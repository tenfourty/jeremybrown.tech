+++
aktt_notify_twitter = [true]
aktt_tweeted = [1]
author = "Jeremy Brown"
categories = ["Africa", "Blog Posts", "Cameroon", "Technology"]
date = "2010-11-19"
dsq_thread_id = [2019673048]
layout = "post"
short-url = ["http://bit.ly/ctNYRd"]
tags = ["Camtel", "CDMA", "Creolink", "GPRS", "Internet", "ISP", "Low Bandwidth", "Matrix", "MTN", "Orange", "performance", "Ringo", "SCDMA", "Wifi", "Wimax"]
title = "Do Cameroonian ISPs care about their customers?"
aliases = "/2010/11/19/do-cameroonian-isps-care-about-their-customers/"

+++

I wanted to inves­ti­gate the typ­i­cal expe­ri­ence of a Cameroon­ian Inter­net user while vis­it­ing the web­sites of the major Inter­net Ser­vice Providers (ISPs). <span class="pullquote">I fig­ured that the time and energy a com­pany puts into opti­mis­ing their web­site for slow con­nec­tions might indi­cate how focused they are as a com­pany on their cus­tomers.</span> After all, if ISPs know what band­width they are giv­ing their cus­tomers then surely they will have opti­mised their sites to work well on those connections?

In addi­tion I hope that this post will high­light the fact that you must opti­mise your site for low-bandwidth users, espe­cially if you oper­ate in coun­tries with poor Inter­net con­nec­tiv­ity. In fact it’s not too hard to do these days if you take a few sim­ple steps, but first you need to be aware of the issue.

Hav­ing lived in Cameroon for the last two years I’m more than famil­iar with surf­ing on a poor unre­li­able con­nec­tion and it stag­gers me that so few Cameroon­ian com­pa­nies have made an effort to improve the user expe­ri­ence for the major­ity of peo­ple who visit their web­sites over these slow con­nec­tions. Inter­net users in Cameroon either have their own 128 kbps “broad­band” con­nec­tion or they are at an Inter­net cafÃ© that shares a slow con­nec­tion between their users (who are all on Face­book and YouTube com­pet­ing for the band­width avail­able). Some are using USBÂ don­gles to access mobile data net­works, but as none of the oper­a­tors have a 3G license users are stuck at slower GPRS speeds with patchy coverage.

* * *

**The ISPs**

The major ISPs in Cameroon today are:

  * <a href="http://www.camtel.cm/" target="_blank"><strong>Cam­tel</strong></a> — the state-owned incum­bent who has a monop­oly on all the fibre in the coun­try and the <a href="http://en.wikipedia.org/wiki/SAT-3/WASC_(cable_system)" target="_blank">SAT3 cable</a>, all other ISPs must buy band­width from Cam­tel. Cam­tel pro­vides Inter­net access via ADSL or over Wire­less using CDMA.
  * <a href="http://www.mtn.cm/" target="_blank"><strong>MTN</strong></a> — the mobile oper­a­tor with the largest mar­ket share, pro­vid­ing Inter­net through GPRS, wire­less hotspots and WiMax.
  * <a href="http://www.orange.cm/" target="_blank"><strong>Orange</strong></a> — the sec­ond largest mobile oper­a­tor, pro­vid­ing Inter­net through GPRS and WiMax.
  * <a href="http://www.ringo.cm/" target="_blank"><strong>Ringo</strong></a> — they claim to have more band­width avail­able than their com­peti­tors (apart from Cam­tel). Ringo is using pro­pri­etary SCDMA based McWill tech­nol­ogy from Xin­Wei in China and have also started to pro­vide wire­less hotspots in the major cities.
  * <a href="http://www.matrixtelecoms.com/" target="_blank"><strong>Matrix Tele­coms</strong></a> — ISP using wire­less tech­nol­ogy to pro­vide access.
  * <a href="http://www.creolink.cm/" target="_blank"><strong>Cre­olink</strong></a> — uses cable to pro­vide access to their customers.

I’ve tried to sum­marise the cheap­est options for con­sumers from each of these ISPs in the table below.

**This table was lost somewhere between upgrades between wordpress versions and moving to a static website!**

As you can see 128 kbps is pretty typ­i­cal, even if some providers claim to have faster speeds the actual speed is closer to 128 kbps in real world con­di­tions. Price wise they are all pretty sim­i­lar, though it’s quite a dif­fer­ence from the prices we are used to pay­ing in Europe! For exam­ple, from <a href="http://shop.virginmedia.com/broadband.html" target="_blank">Vir­gin</a> in the UK you can pay â‚¬15 a month forÂ a claimed 10 Mbps.

* * *

**Analy­sis and Results**

So given all of this I thought I would do a com­par­a­tive analy­sis of the major Cameroon­ian ISP’s web­sites to see how they actu­ally fared on a typ­i­cal 128 kbps con­nec­tion. I used a com­bi­na­tion of <a href="http://forums.macrumors.com/showthread.php?t=333657" target="_blank">pipes and the ipfw com­mand on my mac</a> (for band­width sim­u­la­tion), <a href="http://code.google.com/speed/page-speed/docs/extension.html" target="_blank">Page Speed</a>/<a href="http://developer.yahoo.com/yslow/" target="_blank">YSlow</a> plu­g­ins for <a href="http://www.mozilla.com/firefox/" target="_blank">Fire­fox</a> and the devel­oper tools in <a href="http://www.google.com/chrome" target="_blank">Google Chrome</a> to mea­sure the page load results. The tools used and approach wasn’t totally sci­en­tific but they give a pretty good indi­ca­tion of real per­for­mance. If you are inter­ested in run­ning this test your­self <a href="http://www.aptivate.org/" target="_blank">Apti­vate</a> have a great <a href="http://blog.aptivate.org/2010/01/23/make-sure-your-apps-work-in-the-field/" target="_blank">blog post of how to do this</a>. The met­rics I mea­sured were:

  * Page load time, empty cache and primed cache
  * Page size, empty cache and primed cache
  * Num­ber of HTTP Requests, empty cache and primed cache
  * Page Speed Score
  * YSlow Grade

The table below details the results.

**This table was lost somewhere between upgrades between wordpress versions and moving to a static website!**

On the whole the results are pretty dis­ap­point­ing and show just how out of touch with their users the ISPs really are, Matrix does best with a page load time of 15 sec­onds, not too bad but they still have room for improve­ment, in com­par­i­son it takes 10 sec­onds to load <a href="http://www.google.cm/" target="_blank">www.google.cm</a>’s 174K page when the cache is empty and 1 sec­ond when primed. The results for the other web­sites go from bad to worse to incredible!

What is really fright­en­ing about these results is that the slow­est load­ing sites took nearly a minute or more, surely none of their cus­tomers spend that long wait­ing for the sites to load or much time brows­ing on their pages. The big cul­prit in all of this is of course Flash! As far as I’m con­cerned it just isn’t a tech­nol­ogy that should be used on web­sites, espe­cially in low-bandwidth sit­u­a­tions. Usu­ally coun­tries where band­width is very low the PCs being used to the access the Inter­net are old and slow and Flash causes even more prob­lems as it hogs CPU, a dou­ble whammy of user pain.

Flash used on these sites to pro­mote the ISP’s prod­ucts, how­ever because they take so long to dis­play the user has usu­ally moved on by the time they load so they don’t even achieve the aim that jus­ti­fied Flash in the fist place.

One inter­est­ing point to note is that though MTN’s site has a rel­a­tively small size in com­par­i­son to some of the other sites, with very few HTTP requests, they still take a long time to load because they redi­rect the browser sev­eral times, this sig­nif­i­cantly increases the total time it takes to load the page.

All the sites tested could improve their page load times by tak­ing the rec­om­mended steps in the Page Speed and YSlow plu­g­ins, remov­ing errors and bro­ken HTML and mostly by remov­ing Flash.

* * *

**Con­clu­sion**

In con­clu­sion we can see that most Inter­net Ser­vice Providers in Cameroon seem to be out of touch with their cus­tomers and pay lit­tle atten­tion to the user expe­ri­ence on their web­sites AND Flash is very bad in low-bandwidth situations!

_Does a web­site reflect a company’s treat­ment of their cus­tomers in real life? I’m curi­ous to hear what your expe­ri­ence is, please leave a com­ment below._
