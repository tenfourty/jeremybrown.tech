+++
author = "Jeremy Brown"
categories = ["Blog Posts", "Technology"]
date = "2011-07-09"
dsq_thread_id = [2050870394]
type = "post"
short-url = ["http://bit.ly/qs7OYY"]
tags = ["CentOS", "How To", "Linux", "RHEL", "Scientific Linux"]
title = "How-to Switch from CentOS 5.6 to Scientific Linux 5.6"
aliases = "/2011/07/09/how-to-switch-from-centos-5-6-to-scientific-linux-5-6/"

+++

I have recently switched my [Lin­ode][1] VPS from [Cen­tOS][2] 5.6 to [Sci­en­tific Linux][3] 5.6 because I got a bit sick of all of the delays that the Cen­tOS team have been expe­ri­enc­ing, to be hon­est I don’t care what their rea­sons are, I just want a dis­tro that fol­lows [RHEL][4] a bit faster!

I think I can sum­marise my rea­sons based on this email:

  * Faster updates
  * Pro­fes­sional
  * Secu­rity and bug­fix updates separate
  * Secu­rity updates also for older ver­sions of SL
  * More reli­able than CentOS

>The Cen­tOS guys seem more focused on infight­ing rather than focussing on get­ting Cen­tOS 6 out the door, con­sid­er­ing how long RHEL 6 has been avail­able this has turned into a bit of a joke!

When I googled around I couldn’t find a con­cise arti­cle that explained how to do this, so here is a my sim­ple guide to switch­ing from Cen­tOS 5.6 to Sci­en­tific Linux (SL) 5.6, it was rel­a­tively straight­for­ward and my rock solid VPS has stayed up and reli­able through­out the process. These instruc­tions are based on the fol­low­ing articles:

  * [Cen­tOS Migra­tion Guide][5]
  * [This thread][6] on the SL user mail­ing list.

If you want to tell what ver­sion of Cen­tOS you are cur­rently run­ning you can use the fol­low­ing command:

```
cat /etc/redhat-release
```

Now to “upgrade” to SL. All com­mands should obvi­ously be run as root.

You might also want to back up your release file, you can do that with the fol­low­ing command:

```
cp /etc/redhat-release /etc/redhat-release-saved
```

Then just use the fol­low­ing com­mands to remove Cen­tOS and install SL:

```
yum clean all
rpm -e --nodeps centos-release-notes centos-release yum-3.2.22-33.el5.centos.noarch redhat-logos redhat-artwork redhat-menus
rpm -e --nodeps yum-3.2.22-33.el5.centos.noarch
rpm -ivh http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/sl-release-5.6-1.i386.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/sl-release-notes-5.6-1.noarch.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/redhat-artwork-5.0.9-2.SL.4.i386.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/redhat-logos-4.9.16-2.sl5.6.noarch.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/redhat-menus-6.7.8-3.el5.noarch.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/yum-3.2.22-33.sl.noarch.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/yum-autoupdate-1.1-1.SL.noarch.rpm http://ftp.scientificlinux.org/linux/scientific/56/i386/SL/yum-conf-56-1.SL.noarch.rpm
yum update all
```

If you now check what release ver­sion you are on you should see some­thing like the following:

```
[root@wahala ~]# cat /etc/redhat-release
Scientific Linux SL release 5.6 (Boron)
[root@wahala ~]#
```

Next I think I’ll attempt to upgrade or rebuild my VPS to run Sci­en­tific Linux 6… the sub­ject of a future blog post!

 [1]: http://www.linode.com/
 [2]: http://www.centos.org/
 [3]: http://www.scientificlinux.org/
 [4]: http://www.redhat.com/rhel/
 [5]: http://wiki.centos.org/HowTos/MigrationGuide
 [6]: http://listserv.fnal.gov/scripts/wa.exe?A2=ind1101&L=scientific-linux-users&T=0&P=7477
