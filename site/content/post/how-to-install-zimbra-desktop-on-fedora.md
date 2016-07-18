+++
author = "Jeremy Brown"
categories = ["Blog Posts"]
date = "2014-10-09"
dsq_thread_id = [3100452983]
type = "post"
title = "How To Install Zimbra Desktop on Fedora"
aliases = "/2014/10/09/how-to-install-zimbra-desktop-on-fedora/"

+++

As we use Zim­bra at work I decided to install Zim­bra Desk­top for offline email, how­ever I ran into a bit of a snag because after [down­load­ing](http://www.zimbra.com/downloads/zimbra-desktop) it and fol­low­ing the [instal­la­tion instruc­tions](http://www.zimbra.com/documentation/zimbra-desktop) I had the fol­low­ing error mes­sage when I ran Zim­bra Desk­top for the first time:

```Couldn't load XPCOM.```

After a bit of googling around I found this arti­cle [Installing Zim­bra Desk­top on 64bit Linux](http://wiki.zimbra.com/wiki/Installing_Zimbra_Desktop_on_64bit_Linux) which has the fol­low­ing fix to install the 32-bit libraries that are (nat­u­rally) miss­ing in my 64-bit Fedora install:

```yum install -y alsa-lib.i686 libstdc++.i686 xulrunner.i686 gtk2-engines.i686<```

Once I had these libs installed I could hap­pily run Zim­bra Desk­top or zdesktop.

 
