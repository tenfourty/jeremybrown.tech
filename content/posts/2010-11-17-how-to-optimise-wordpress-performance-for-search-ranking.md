+++
aktt_notify_twitter = [true]
aktt_tweeted = [1]
author = "Jeremy Brown"
categories = ["Blog Posts", "Technology"]
date = "2010-11-17"
dsq_thread_id = [2019673042]
layout = "post"
short-url = ["http://bit.ly/cn3cY1"]
tags = ["Google", "How To", "Search", "Search Ranking", "Speed", "W3 Total Cache", "WordPress", "WP Super Cache"]
title = "How to Optimise WordPress Performance for Search Ranking"
url = "/2010/11/17/how-to-optimise-wordpress-performance-for-search-ranking/"

+++

Google says that <a href="http://googlewebmastercentral.blogspot.com/2010/04/using-site-speed-in-web-search-ranking.html" target="_blank">they use the per­for­mance of your web­site</a> as part of your search ranking:

> You may have heard that here at Google we’re obsessed with speed, in our prod­ucts and on the web. As part of that effort, today we’re includ­ing a new sig­nal in our search rank­ing algo­rithms: web­site speed. Site speed reflects how quickly a web­site responds to web requests.
>
> Speed­ing up web­sites is impor­tant ” not just to site own­ers, but to all Inter­net users. Faster sites cre­ate happy users and we’ve seen in our <a href="http://googleresearch.blogspot.com/2009/06/speed-matters.html" target="_blank">inter­nal stud­ies</a> that when a site responds slowly, vis­i­tors spend less time there. But faster sites don’t just improve user expe­ri­ence; recent data shows that improv­ing site speed also <a href="http://radar.oreilly.com/2009/07/velocity-making-your-site-fast.html" target="_blank">reduces oper­at­ing costs</a>. Like us, our users place a lot of value in speed ” that’s why we’ve decided to take site speed into account in our search rank­ings. We use a vari­ety of sources to deter­mine the speed of a site rel­a­tive to other sites.

<a href="http://wordpress.org/extend/plugins/w3-total-cache/faq/" target="_blank">Here</a> are more good rea­sons why speed matters:

> Speed is among the most sig­nif­i­cant suc­cess fac­tors web sites face. In fact, your site’s speed directly affects your income (rev­enue) ” it’s a fact. Some high traf­fic sites con­ducted research and uncov­ered the following:
>
>   * Google.com: **+500 ms** (speed decrease) -> **–20% traf­fic loss** [[1][1]]
>   * Yahoo.com: **+400 ms** (speed decrease) -> **–5–9% full-page traf­fic loss**(vis­i­tor left before the page fin­ished load­ing) [[2][2]]
>   * Amazon.com: **+100 ms** (speed decrease) -> **–1% sales loss** [[1][1]]
>
> A thou­sandth of a sec­ond is not a long time, yet the impact is quite sig­nif­i­cant. Even if you’re not a large com­pany (or just hope to become one), a loss is still a loss.

So how do you speed up your Word­Press web­site to get that extra edge in search rank­ings and give a bet­ter expe­ri­ence to your users? Well you install a caching plu­gin of course! How­ever not all caching plu­g­ins are cre­ated equal. For years <a href="http://wordpress.org/extend/plugins/wp-super-cache/" target="_blank">WP Super Cache</a> has been my weapon of choice because it is sim­ple to install, very fast and is being con­stantly devel­oped and improved.

One thing always annoyed me though, when I ran any of the per­for­mance analy­sis plu­g­ins like <a href="http://code.google.com/speed/page-speed/docs/extension.html" target="_blank">Page Speed</a> and <a href="http://developer.yahoo.com/yslow/" target="_blank">YSlow</a> in Fire­fox or the built in Webkit devel­oper tools in Chrome and Safari, my sites still weren’t scor­ing top marks even though caching was fully on. This really bugged me as I’m such a per­fec­tion­ist! I just hated to see those red results in the Page Speed report.

Some of the things that always came up when I looked at the gen­er­ated reports included:

  * Make fewer HTTP requests
  * Add Expires headers
  * Com­press com­po­nents with gzip
  * Make JavaScript and CSS external
  * Use a Con­tent Deliv­ery Net­work (CDN)
  * Con­fig­ure entity tags (ETags)
  * Use cookie-free domains

When I finally came across <a href="http://wordpress.org/extend/plugins/w3-total-cache/" target="_blank">W3 Total Cache</a> I knew I’d finally found the solu­tion to all of this. After mak­ing the switch from WP Super Cache to W3 Total Cache I know I’ll be doing this for all Word­Press imple­men­ta­tions I do in the future. Don’t get me wrong though, for a sim­ple low traf­fic site WP Super Cache is prob­a­bly the way to go every time for it’s sim­plic­ity and the lack of tech­ni­cal skills required to install and get it up and run­ning. How­ever if your site has a lot of traf­fic or you want to improve your web­sites per­for­mance by an order of mag­ni­tude then I would rec­om­mend switch­ing to W3 Total Cache. It requires a lit­tle bit more tech­ni­cal knowl­edge, but it is well worth it.

We were run­ning WP Super Cache (fully opti­mised) on our site <a href="http://limbelabssolutions.com/" target="_blank">limbelabssolutions.com</a> before switch­ing to W3 Total Cache, the stats below speak for themselves.

**This table was lost somewhere between upgrades between wordpress versions and moving to a static website!**

This could make all the dif­fer­ence to your server if you get a lot of traf­fic or want to be pre­pared for a sud­den spike in traf­fic and of course improve your search rank­ing at the same time.

Here are the steps I rec­om­mend you take before installing W3 Total Cache, includ­ing some gotchas to watch out for.

  * Bench­mark your site before, dur­ing and after to under­stand the impact of your changes. There are many tools out there that you can use. I would rec­om­mend a com­bi­na­tion of the following:
      * Use Google Web­mas­ter Tools, they have some nice stats on crawl­ing your site, page load times and page sizes.
      * Use the Page Speed and YSlow plu­g­ins for Fire­fox to pro­file your site.
      * Safari and Chrome have a great Webkit pro­filer built into the devel­oper menu.
      * There are some online tools that you can use, some I like are <a href="http://www.showslow.com/" target="_blank">www.showslow.com</a>, <a href="http://www.webpagetest.org/" target="_blank">www.webpagetest.org</a>, <a href="http://tools.pingdom.com/" target="_blank">tools.pingdom.com</a>
  * Remove all exist­ing caching plu­g­ins AND delete them. I didn’t do this and it cause me end­less prob­lems until I realised what was going wrong.
  * Install the W3 Total Cache Plu­gin, <a href="http://wordpress.org/extend/plugins/w3-total-cache/installation/" target="_blank">com­pre­hen­sive instruc­tions are here</a>. Read them before you start as there are a few extra essen­tial steps that dif­fer from the norm and they will throw you if you don’t RTFM. <a href="http://nimopress.com/pressed/blog-building-how-to-dramatically-speed-up-your-wordpress-site-with-w3-total-cache/" target="_blank">Here’s a good tuto­r­ial</a> on how to do it.
  * I used our own sim­ple Con­tent Deliv­ery Net­work, which was very easy to setup (see the the tuto­r­ial link above). One com­ment I would have on the CDN is that I wouldn’t host your mini­fied CSS/JS on the CDN as they aren’t gzip com­pressed when served up, if you keep them on your main site then W3 Total Cache will serve them gziped. I’m run­ning all this in a shared host­ing envi­ron­ment, if I had a ded­i­cated server I would have more con­trol. You will also need to <a href="http://codex.wordpress.org/Editing_wp-config.php#Set_Cookie_Domain" target="_blank">set your Word­Press cookie domain</a> in your wp-config.php file if you use this setup.

So there you have it, def­i­nitely use W3 Total Cache over WP Super Cache if you want to get that extra edge. How­ever it is a bit more com­pli­cated to install and keep running.

 [1]: http://home.blarg.net/~glinden/StanfordDataMining.2006-11-29.ppt
 [2]: http://www.slideshare.net/stoyan/yslow-20-presentation
