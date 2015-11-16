+++
author = "Jeremy Brown"
categories = ["Architect", "Platform"]
date = "2013-09-27"
dsq_thread_id = [2489813011]
layout = "post"
tags = ["Docker", "open", "PaaS"]
title = "Docker + Red Hat OpenShift = The Tipping Point for Open PaaS?"
aliases = "/2013/09/27/docker-red-hat-openshift-tiping-point-open-paas/"

+++


![Sumo tipping point](/uploads/sumo-tipping-point.jpg)

_What if you could wrap up your appli­ca­tion in a light­weight con­tainer and then move it to any Linux server and have it per­form in a pre­dictable way with no changes? bare metal? vir­tu­al­ized? in a multi ten­ant envi­ron­ment? securely?_

_What if you could choose your  lan­guage and run­time envi­ron­ment (Ruby, Python, JEE, JavaScript, etc) and have it pro­vi­sioned with your appli­ca­tion code? with full life-cycle man­age­ment? with auto scal­ing? sup­ported by the ven­dor behind the tech­nol­ogy? on any PaaS?_

**TL;DR ver­sion** — Docker is an awe­some way to con­tainer­ise any appli­ca­tion run­ning on Linux, but it has some short­falls. Red Hat’s col­lab­o­ra­tion with dot­Cloud the com­pany behind Docker will fix these and allow Docker run on almost any dis­tri­b­u­tion of Linux (includ­ing RHEL and it’s deriv­a­tives). They will also inte­grate the tech­nol­ogy that under­pins the Open­Shift PaaS (car­tridges) so that the life­cy­cle of an appli­ca­tion run­time can be man­aged. Mean­ing your appli­ca­tion will even­tu­ally be able to run any­where on your infra­struc­ture or on the cloud with no changes — cool eh?

I believe that the announced part­ner­ship last week by Red Hat and dot­Cloud to get Docker work­ing on Fedora/RHEL and into Open­Shift may actu­ally make some of the what if’s above a real­ity. Though the news hasn’t hit the major tech news head­lines this really is the tip­ping point for Open PaaS to even­tu­ally win against the future that is being pushed on us by the proprietary/closed source ven­dors with their siloed approach to the world.

**Docker is awe­some… but what is it?**

[Docker][1] is a super cool way of con­tainer­is­ing your appli­ca­tion on Linux so that rather than hav­ing a full vir­tual machine with an Oper­at­ing Sys­tem and all of its files in a large image file you instead store just the files that are dif­fer­ent for your appli­ca­tion and the Docker con­tainer makes sure that your appli­ca­tion only sees its view of the world. Appli­ca­tions run­ning in Docker con­tain­ers are kept sep­a­rate due to the power of Linux con­tain­ers (LXC).

The power of this approach is that basi­cally you can have an extremely light­weight, super fast VM like run­time envi­ron­ment for your appli­ca­tion that are highly portable, for a quick 5 minute intro [watch this video][2] and come back.

Docker and Open­Shift cur­rently lever­age the same build­ing blocks to imple­ment con­tain­ers, such as Linux ker­nel name­spaces and resource man­age­ment with Con­trol Groups (cGroups).

Docker has some draw­backs though because it doesn’t work in dis­tri­b­u­tions of Linux built for the enter­prise use such as RHEL and it doesn’t use Security-Enhanced Linux (SELinux) which allows the OS to pro­vide secure multi-tenancy and reduce the risk of mali­cious appli­ca­tions or ker­nel exploits. This is because Docker uses AuFS (Advanced Multi Layer Uni­fi­ca­tion Filesys­tem)  is not com­pat­i­ble with SELinux due to labelling lim­i­ta­tions so Docker can­not run on Fedora, RHEL or Cen­tOS. Soon this lim­i­ta­tion will be removed and the secu­rity and porta­bil­ity of Docker con­tain­ers will take a major leap forward.

**So what have Docker and Red Hat announced?**

As announced in the [press release][3] and the [docker blog post][4] the main points of the part­ner­ship are:

  * **Pack­ag­ing Docker for the Fedora Project**, Red Hat and dot­Cloud are col­lab­o­rat­ing to pack­age Docker for Fedora which will ulti­mately enable Docker to build and deploy on Red Hat Enter­prise Linux.
  * **Remov­ing Docker’s depen­dency on AuFS** (Advanced Multi Lay­ered Uni­fi­ca­tion Filesys­tem) to meet mission-critical require­ments from enter­prise cus­tomers. The new approach will be based on the device-mapper thin pro­vi­sion­ing tech­nol­ogy included in Fedora, Red Hat Enter­prise Linux, and other Linux dis­tri­b­u­tions. This approach allows Docker to be more com­pat­i­ble with upstream ker­nel ver­sions and frees it from a depen­dency on Ubuntu.
  * **Enabling lib­virt** within Docker to enable users to take full advan­tage of the robust net­work­ing capa­bil­i­ties of libvirt.
  * **Inte­grate Docker with OpenShift’s car­tridge model** for appli­ca­tion orches­tra­tion. This inte­gra­tion will com­bine the power of Docker con­tain­ers with OpenShift’s abil­ity to describe and man­age multi-container appli­ca­tions, enabling cus­tomers to build more sophis­ti­cated appli­ca­tions with enhanced portability.

**The tip­ping point for Open PaaS?**

There has been quite a few rip­ples from this announce­ment in the Fedora, Docker and PaaS com­mu­nity and [some good analy­sis][5]. Here is my take on why this is such an impor­tant announce­ment for the future of open PaaS, some­thing I care a lot about

Docker has fast become the con­tainer of choice for many on Linux and on many open source PaaS’s that are emerg­ing, how­ever with­out SELinux and the abil­ity to run on Enter­prise Linux it was severely restricted. Docker is super pow­er­ful and the adop­tion and ecosys­tem already build­ing up around it and with Red Hat onboard it means mean that it’s start­ing to emerge as a stan­dard for Linux containers.

**Yes but what has this got to do with PaaS?** Well PaaS has always needed a way to take your appli­ca­tion from one PaaS to another, with Docker as a stan­dard you will have a fully portable appli­ca­tion that behaves exactly the same on one PaaS as it doesn’t on another. This frees up your appli­ca­tion from all of those pro­pri­etary for­mats that each PaaS has come up with in order to give you the PaaS ser­vice in the first place.

OpenShift’s car­tridge model allows “appli­ca­tion con­tain­ers” to be defined in a com­mon man­ner so that for exam­ple a JEE con­tainer can be cre­ated and more impor­tantly orches­trated (scaled up and down) and man­aged by the PaaS. At the moment the for­mat for these “appli­ca­tion con­tain­ers” is fairly spe­cific to each PaaS provider, how­ever with Red Hat com­mit­ting to inte­grate their car­tridge model with Docker it starts to pave the way for Docker con­tain­ers to have a stan­dard­ised way to describe these so called “appli­ca­tion con­tain­ers” as well.

And this is the really excit­ing part, with a stan­dard­ised way to con­tainer­ise not only the files on an oper­at­ing sys­tem but also the appli­ca­tion con­tain­ers as well we could have a truly open ecosys­tem for PaaS. You would be able to build your appli­ca­tion on a local desk­top, vir­tual machine, on-premise PaaS or cloud PaaS and move your appli­ca­tion from one PaaS provider to another while hav­ing an extremely portable con­tainer­ised appli­ca­tion AND a fully sup­ported appli­ca­tion con­tainer con­tain­ing your Java Appli­ca­tion Server of choice. We would rapidly start to see sup­port for almost every sort of appli­ca­tion con­tainer avail­able (Jetty, Tom­cat, JBoss EAP, Ora­cle WebLogic, IBM Web­sphere, vert.x, Ruby on Rails, Django, what­ever) in a stan­dard­ised way.

To have a truly open ecosys­tem in PaaS is what we’ve been wait­ing for and I believe that the deci­sion announced last week has the poten­tial to form the seed of this open ecosystem.

_Update:_ I made it to the home page of [Hacker News][6] so feel free to join the dis­cus­sion there: <https://news.ycombinator.com/item?id=6494527>

 [1]: http://www.docker.io/
 [2]: https://www.youtube.com/watch?v=wW9CAH9nSLs
 [3]: http://gb.redhat.com/about/news/press-archive/2013/9/red-hat-and-dotcloud-collaborate-on-docker-to-bring-next-generation-linux-container-enhancements-to-openshift
 [4]: http://blog.docker.io/2013/09/red-hat-and-docker-collaborate/
 [5]: http://allthingsplatforms.com/platforms/the-importance-of-red-hat-docker-partnership/
 [6]: https://news.ycombinator.com/
