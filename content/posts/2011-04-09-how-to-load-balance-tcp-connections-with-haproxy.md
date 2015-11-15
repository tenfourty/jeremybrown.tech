+++
aktt_notify_twitter = [true]
aktt_tweeted = [1]
author = "Jeremy Brown"
categories = ["Blog Posts", "Technology"]
date = "2011-04-09"
dsq_thread_id = [2019673089]
layout = "post"
short-url = ["http://bit.ly/dWm4QX"]
tags = ["EAP", "EWS", "HAProxy", "JBoss", "JDBC", "load balancer", "load balancing", "ODBC", "TCP", "Teiid"]
title = "How to load balance TCP connections with HAProxy"
url = "/2011/04/09/how-to-load-balance-tcp-connections-with-haproxy/"

+++

This week I was at a client where we were doing some per­for­mance test­ing of the [JBoss Enter­prise Data Ser­vice][1]s prod­uct (EDS for short). EDS is based on the [JBoss.org][2] com­mu­nity project [Teiid][3] which is a data vir­tu­al­iza­tion sys­tem that allows appli­ca­tions to use data from mul­ti­ple, het­eroge­nous data stores. It’s a really cool prod­uct if you have a lot of back­end data sources and you want to expose a sim­pli­fied vir­tual (SQL) data­base to your front end appli­ca­tions — and it runs within the JBoss appli­ca­tion server, in our case the enter­prise ver­sion — [Enter­prise Appli­ca­tion Plat­form][4] or EAP for short.

As we were doing per­for­mance test­ing we wanted to run EDS within a clus­ter of JBoss EAP nodes, now clus­ter­ing EAP nodes is fairly straight­for­ward and you can then setup a front end load bal­ancer with Apache httpd, in my case I used the [Red Hat][5] prod­uct based on the [Apache web server][6] called [Enter­prise Web Server][7] (EWS) and mod_cluster to clus­ter and load bal­ance my appli­ca­tion servers. Now this sort of clus­ter­ing is fine if you want to do repli­ca­tion of your appli­ca­tions and use dis­trib­uted cache repli­ca­tion within the clus­ter, how­ever the ques­tion was how do you do load bal­anc­ing on the [ODBC][8] and [JDBC][9] con­nec­tions that EDS pro­vides for the appli­ca­tion tier? As these types of con­nec­tions can’t be load bal­anced by the Apache Web Server we had to come up with another way to do this.

As we were at a very large enter­prise client their ini­tial sug­ges­tion was that we use a hard­ware TCP load bal­ancer to do this, how­ever I was pretty sure this was a straight­for­ward prob­lem that must have been solved already and that a soft­ware based solu­tion must exist… and low and behold there is one and it is called [HAProxy][10].

HAProxy is a really cool load bal­ancer that is very pow­er­ful and flex­i­ble and also really easy to use and it seems that not too many peo­ple are aware that it can be used to load bal­ance ANY TCP con­nec­tion, [this blog post][11] lead me in the right direc­tion and with the ethos of try­ing to help all of you out there on the web here is my very short how to and sam­ple con­fig­u­ra­tion for how to load bal­ance ODBC and JDBC con­nec­tions — specif­i­cally for Teiid embed­ded in the JBoss Enter­prise Data Ser­vices product.

First you need to get HAProxy, in my case I was run­ning every­thing on RHEL so the eas­i­est thing is to add the [Fedora EPEL repos­i­tory][12] to your machine and then just do a ```yum install haproxy```, you should now have haproxy installed on your machine — now you just need to con­fig­ure and launch it!

So first con­fig­u­ra­tion, I’ve included a sam­ple con­fig­u­ra­tion file for 4 nodes, as I had two phys­i­cal machines with 2 nodes run­ning on each of them. The first node on each machine was run­ning the default JBoss ports and the sec­ond was using ports 100 greater than the default. Here is my file:

{{< gist 911226 >}}

You’ll notice that I also cre­ate a lis­tener for stats on on port 9090 — this means that you can have a nifty web stats page that you can view on ```http://<haproxyIP>:8080/haproxy?stats``` (username/password = admin/admin).

Now that we have HAProxy con­fig­ured we just need to run it, in this case it would be ```haproxy –f <con­fig file> –V```, I used the ver­bose flag so that I could see what was going on but you may not nec­es­sar­ily want this for production.

Now just launch the stats page to see your nodes con­nected and you are up and run­ning — don’t for­get to con­fig­ure the ODBC and JDBC lis­tener sec­tions to put your own ports to lis­ten to depend­ing on the setup you are going to use.

Oh and by the way the per­for­mance test­ing we did showed that Teiid is amaz­ingly performant!

 [1]: http://www.jboss.com/products/platforms/dataservices/
 [2]: http://www.jboss.org/
 [3]: http://www.jboss.org/teiid
 [4]: http://www.jboss.com/products/platforms/application/
 [5]: http://www.redhat.com/
 [6]: http://httpd.apache.org/
 [7]: http://www.jboss.com/products/platforms/webserver/
 [8]: http://en.wikipedia.org/wiki/Open_Database_Connectivity
 [9]: http://en.wikipedia.org/wiki/Java_Database_Connectivity
 [10]: http://haproxy.1wt.eu/
 [11]: http://www.linickx.com/645/load-balance-anything-with-haproxy
 [12]: http://fedoraproject.org/wiki/EPEL
