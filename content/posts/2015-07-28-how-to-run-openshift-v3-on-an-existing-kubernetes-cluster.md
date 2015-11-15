+++
author = "Jeremy Brown"
categories = ["Blog Posts", "Platform", "Technology"]
date = "2015-07-27"
dsq_thread_id = [3978516980]
layout = "post"
tags = ["Docker", "kubernetes", "openshift"]
title = "How to run OpenShift V3 on an existing Kubernetes Cluster"
url = "/2015/07/28/how-to-run-openshift-v3-on-an-existing-kubernetes-cluster/"

+++

I’m a big fan of [Kuber­netes][1] and the ideas it brings to enable run­ning Docker con­tain­ers at scale. How­ever if you’ve used Kuber­netes you’ll know that right now the tool­ing around it is pretty basic from a devel­oper and appli­ca­tion life­cy­cle per­spec­tive. [Open­Shift V3][2] builds on the con­cepts of Docker and Kuber­netes to add some much needed higher level tool­ing and a Web UI that is really nice.

Here are just a few of the fea­tures that Open­Shift Ori­gin pro­vides out of the box on top of a Kuber­netes cluster:

  * A rich set of role based poli­cies out of the box
  * Quota’s and resource limits
  * Source to Image — no need to know Docker, just build an image very effi­ciently from source
  * Auto­mated builds using on webhooks
  * Appli­ca­tion focused CLI, including:
      * Get logs for any of your run­ning containers
      * Clever port for­ward­ing for remote debugging

One of the things I wanted to do was to run a Kuber­netes clus­ter in [Google Con­tainer Engine][3] but run Open­Shift on top of it. This is because Con­tainer Engine does a great job of run­ning my Kuber­netes clus­ter — includ­ing han­dling autoscal­ing based on demand, net­work­ing and per­sis­tent vol­umes inside the clus­ter etc. All the plumb­ing stuff I don’t want to have to care about when run­ning a cluster.

When I looked into it I found this [exam­ple of run­ning OpenShift-Origin as a pod in an exist­ing Kuber­netes clus­ter][4] in the Kuber­netes GitHub project, how­ever it didn’t work! So this is my basic guide in how to setup Open­Shift V3 Ori­gin to run on top of an exist­ing Kuber­netes cluster.

Like all things we do I’m stand­ing on the shoul­ders of giant’s and this tuto­r­ial was of course orig­i­nally writ­ten by [Derek Carr][5] in the [Kuber­netes exam­ples folder][4] I’ve just tarted it up a bit.

### Step 0: Prerequisites

This exam­ple assumes that you have an under­stand­ing of Kuber­netes and that you have forked [my exam­ple repos­i­tory][6].

The [Kuber­netes Get­ting Started Guide][7] lists a few options, how­ever for sim­plic­ity and robust­ness I’d rec­c­om­mend using [Google Con­tainer Engine][3] to run your Kuber­netes Cluster.

Open­Shift Ori­gin cre­ates priv­i­leged con­tain­ers when run­ning Docker builds dur­ing the [source-to-image][8] process.

If you are fol­low­ing the get­ting started guide above and using a Salt based KUBERNETES_PROVIDER (**gce**, **vagrant**, **aws**), you should enable the abil­ity to cre­ate priv­i­leged con­tain­ers via the API.

```
$ cd kubernetes
$ vi cluster/saltbase/pillar/privilege.sls

# If true, allow privileged containers to be created by API
allow_privileged: true
```

Now spin up a clus­ter using your pre­ferred KUBERNETES_PROVIDER

```
$ export KUBERNETES_PROVIDER=gce
$ cluster/kube-up.sh
```

Per­son­ally I setup my own clus­ter in Google Con­tainer Engine, if you take this approach you will need to fol­low these two guides:

  * <https://cloud.google.com/container-engine/docs/before-you-begin>
  * <https://cloud.google.com/container-engine/docs/clusters/operations>

Just one note about this approach — I haven’t tried source-to-image but it may well fail in a vanila Google Con­tainer Engine clus­ter as [Google cur­rently doesn’t sup­port cre­at­ing priv­i­leged con­tain­ers via the API][9].

**Whichever way you choose to setup your clus­ter, make sure that kubectl and your ~/.kube/config is setup and can talk to your cluster.**

Lets test that our kubectl can talk to the cluster:

```
$ kubectl get nodes
NAME                               LABELS                                                    STATUS
gke-cluster-1-01678227-node-79jo   kubernetes.io/hostname=gke-cluster-1-01678227-node-79jo   Ready
```

Next, let’s setup some vari­ables, and cre­ate a local folder that will hold gen­er­ated con­fig­u­ra­tion files.

```
$ cd openshift-origin-kubernetes-example
$ export BASE=${PWD}
$ export BASE_CONFIG=${BASE}/config
$ mkdir ${BASE_CONFIG}
```

### Step 1: Cre­ate an Exter­nal Load Bal­ancer to Route Traf­fic to OpenShift

An exter­nal load bal­ancer is needed to route traf­fic to our Open­Shift mas­ter ser­vice that will run as a pod on your

Kuber­netes cluster.

```
$ kubectl create -f $BASE/openshift-service.yaml
```

### Step 2: Gen­er­ate con­fig­u­ra­tion file for your Open­Shift mas­ter pod

The Open­Shift mas­ter requires a con­fig­u­ra­tion file as input to know how to boot­strap the system.

In order to build this con­fig­u­ra­tion file, we need to know the pub­lic IP address of our exter­nal load bal­ancer in order to

build default certificates.

Grab the pub­lic IP address of the ser­vice we pre­vi­ously created.

```
$ export PUBLIC_IP=$(kubectl get services openshift --template="{{ index .status.loadBalancer.ingress 0 \"ip\" }}")
$ echo "PUBLIC IP: ${PUBLIC_IP}"
```

Ensure you have a valid PUBLIC_IP address before con­tin­u­ing in the exam­ple, you might need to wait 60 sec­onds in order for it to be setup.

We now need to run a com­mand on your host to gen­er­ate a proper Open­Shift con­fig­u­ra­tion. To do this, we will vol­ume mount our con­fig­u­ra­tion direc­tory and the direc­tory (~/.kube/config) that holds your Kuber­netes con­fig file.

```
$ docker run --privileged -e KUBECONFIG=/kubeconfig -v ${HOME}/.kube/config:/kubeconfig -v ${BASE_CONFIG}:/config openshift/origin:v1.0.3 start master --write-config=/config --master=https://localhost:8443 --public-master=https://${PUBLIC_IP}:8443
```

You should now see a num­ber of cer­tifi­cates minted in your con­fig­u­ra­tion direc­tory, as well as a master-config.yaml file that tells the Open­Shift mas­ter how to exe­cute. In the next step, we will bun­dle this into a Kuber­netes Secret that our Open­Shift mas­ter pod will consume.

### Step 4: Bun­dle the con­fig­u­ra­tion into a Secret

We now need to bun­dle the con­tents of our con­fig­u­ra­tion into a secret for use by our Open­Shift mas­ter pod.

Open­Shift includes an exper­i­men­tal com­mand to make this easier.

First, update the own­er­ship for the files pre­vi­ously generated:

```
$ sudo -E chown ${USER} -R ${BASE_CONFIG}
```

Then run the fol­low­ing com­mand to col­lapse them into a Kuber­netes secret.

```
$ docker run -i -t --privileged -e KUBECONFIG=/kubeconfig -v ${HOME}/.kube/config:/kubeconfig -v ${BASE_CONFIG}:/config openshift/origin:v1.0.3 cli secrets new openshift-config /config -o json &&gt; ${BASE}/secret.json
```

Now, lets cre­ate the secret in your Kuber­netes cluster.

```
$ kubectl create -f ${BASE}/secret.json
```

**NOTE: This secret is secret and should not be shared with untrusted parties.**

### Step 5: Deploy Open­Shift Master

We are now ready to deploy OpenShift.

We will deploy a pod that runs the Open­Shift mas­ter. The Open­Shift mas­ter will del­e­gate to the under­ly­ing Kuber­netes

sys­tem to man­age Kuber­netes spe­cific resources. For the sake of sim­plic­ity, the Open­Shift mas­ter will run with an embed­ded etcd to hold Open­Shift spe­cific con­tent. **Note if the Open­Shift mas­ter fails the etcd con­tent will be lost, this is because etcd is using an ephemeral vol­ume for now.**

```
$ kubectl create -f ${BASE}/openshift-controller.yaml
```

You should now get a pod pro­vi­sioned whose name begins with openshift.

```
$ kubectl get pods | grep openshift
$ kubectl logs openshift-3a1dt origin
I0727 22:11:44.720769       1 start_master.go:307] Starting an OpenShift master, reachable at 0.0.0.0:8443 (etcd: [https://localhost:4001])
I0727 22:11:44.720884       1 start_master.go:308] OpenShift master public address is https://130.211.171.209:8443
```

Depend­ing upon your cloud provider, you may need to open up an exter­nal fire­wall rule for tcp:8443. For GCE, you can run the fol­low­ing (if you are using Google Con­tainer Engine this should already be done for you):

```
gcloud compute --project "your-project" firewall-rules create "origin" --allow tcp:8443 --network "your-network" --source-ranges "0.0.0.0/0"
```

Con­sult your cloud provider’s doc­u­men­ta­tion for more information.

### Step 6: Test it out

Open a browser and visit the Open­Shift mas­ter pub­lic address reported in your log, any user­name and pass­word will work as we haven’t con­fig­ured authen­ti­ca­tion yet.

You can use the CLI com­mands by run­ning the following:

```
$ docker run --privileged --entrypoint="/usr/bin/bash" -it -e KUBECONFIG=/kubeconfig -v ${HOME}/.kube/config:/kubeconfig openshift/origin:v1.0.3
$ oc help
$ oc get pods
```

Or if you have the Open­Shift CLI installed on your local machine you can can skip the docker run com­mand above and just do:

```
$ oc help
$ oc get pods
```


 [1]: http://kubernetes.io/
 [2]: http://www.openshift.org/
 [3]: https://cloud.google.com/container-engine/
 [4]: https://github.com/GoogleCloudPlatform/kubernetes/tree/master/examples/openshift-origin
 [5]: https://github.com/derekwaynecarr
 [6]: https://github.com/tenfourty/openshift-origin-kubernetes-example
 [7]: http://kubernetes.io/gettingstarted/
 [8]: https://github.com/openshift/source-to-image
 [9]: https://stackoverflow.com/questions/31124368/allow-privileged-containers-in-kubernetes-on-google-container-gke
