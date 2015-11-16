+++
author = "Jeremy Brown"
categories = ["CTO", "Developer"]
date = "2013-08-28"
dsq_thread_id = [2490005863]
layout = "post"
tags = ["PaaS"]
title = "The Evolution of Paas and how this site was setup"
aliases = "/2013/08/28/evolution-paas-site-setup/"

+++

![The evolution of PaaS and Guybrush Threepwood](/uploads/evolution_of_guybrush_threepwood.png)

As I’m a bit of a geek at heart and because I’m a major fan of open source I really wanted to host this web­site on an open source PaaS using as much open source soft­ware so I decided to use my favourite blog­ging soft­ware [Word­Press][1] and host it on [Open­Shift Online][2]. While I was putting this blog together I realised just how far things have come when it comes to set­ting up your own web­site, but before I dive into the evo­lu­tion of host­ing that has got­ten us to PaaS let me show you exactly why I think PaaS is so magic by tak­ing you through the three sim­ple steps it took to set up a Word­Press blog on the domain www.themiddlewareman.org.

**Step 1.** Reg­is­ter the domain (I use [Gandi][3]). This took just a cou­ple of min­utes includ­ing pay­ing by credit card.

**Step 2.** Setup an Open­Shift “app”. I used a[ word­press quick­start][4] which only required the fol­low­ing steps and took a cou­ple of min­utes in total:

> Cre­ate an account at <http://openshift.redhat.com/> and install the client tools (run ‘rhc setup’ first)
>
> Cre­ate a php-5.3 appli­ca­tion (you can call your appli­ca­tion what­ever you want)
>
>     rhc app create wordpress php-5 mysql-5 --from-code=https://github.com/openshift/wordpress-example
>     
>
> That’s it, you can now check­out your appli­ca­tion at:
>
>     http://wordpress-$yournamespace.rhcloud.com
>     
>
> You’ll be prompted to set an admin pass­word and name your Word­Press site the first time you visit this page.

**Step 3.** All that was left was to [reg­is­ter an alias][5] in Open­Shift for www.themiddlewareman.org and update my dns set­tings (I use DNS Made Easy) to point to my new appli­ca­tion url. Again this took only a few min­utes to do and as I’m using a really great DNS provider my changes prop­a­gated super fast!

Fun­nily enough tweak­ing the theme and con­fig­ur­ing plu­g­ins took WAY more time than instal­la­tion, but again the sim­ple steps above just illus­trate how easy it is to set up a web­site with a PaaS — and of course with Open­Shift I still have ssh access to the site and every­thing is in a git repos­i­tory that I con­trol and I can even [do my own back­ups of my site][6] if I don’t trust the Word­Press backup plu­gin I’m run­ning which backs up this site to my Drop­box account once a week.

So this prompted me to think back to just how far we’ve come in the last 20 or so years that the inter­net as we know it has been around. Here are the dif­fer­ent phases that we’ve been through so far.

  * Inter­net Con­nec­tion — yep, you got an inter­net con­nec­tion (rang­ing from a dial-up to a T3 line) and a sta­tic IP and you hosted your own site on your own hard­ware. This was pretty expen­sive and totally man­ual because you paid for Inter­net, Hard­ware and you looked after every­thing from hard­ware, soft­ware, net­work­ing and every­thing in between.
  * Servers at the ISP — either col­lo­cated or access to the ISP’s own servers. At this point you needed less net­work­ing smarts and your con­nec­tion got both faster and cheaper but you still needed expen­sive hard­ware and it was all still very expensive.
  * [Geoc­i­ties][7] arrived on the scene — It’s really worth men­tion­ing these guys because what they did was setup some of those big expen­sive servers and paid for the inter­net con­nec­tion but they carved it up into lit­tle chunks (1MB seemed huge at the time) and allowed you to host very sim­ple web­sites for free, they even gen­er­ated the HTML for you so you didn’t have to hand craft it your­self. This then spawned a whole host­ing indus­try where you could get a very small slice of a big­ger machine with vary­ing lev­els of priv­i­lege from what was usu­ally FTP and flat HTML files to SSH and the abil­ity to run [CGI][8] scripts.
  * Vir­tu­al­iza­tion and the arrival of the Vir­tual Pri­vate Server (VPS) — With the increas­ing usage of vir­tu­al­iza­tion by host­ing providers and as Linux started to infil­trate the host­ing mar­ket it became pos­si­ble to have your own vir­tual server that you had root access to and com­plete con­trol of. At this point peo­ple were really still build­ing tra­di­tional appli­ca­tions and man­ag­ing their servers by hand or with elab­o­rate man­age­ment tool­ing but the. Most of my own per­sonal web­site and projects are now hosted on a VPS that I’ve had for the last few years from [Lin­ode][9] (arguably they are an IaaS provider too) but with the evo­lu­tion of PaaS it’s start­ing to make more sense for me to move all these sites onto a PaaS.
  * Infra­struc­ture as a Ser­vice (IaaS) — The rev­o­lu­tion of IaaS was not that you could get a vm really quickly though that is part of it, for me the really sig­nif­i­cant change was that you started to archi­tect your appli­ca­tions dif­fer­ently, this is where appli­ca­tion nodes started to become state­less, we started to move away from clus­ter­ing to share appli­ca­tion state and move to using things like data­bases more for state (ini­tially, because that’s what we knew) and ulti­mately to using data grids for appli­ca­tion state. As appli­ca­tions get adapted or new ones writ­ten for this new approach they will become more resilient and scal­able with the main idea being that you can [kill any server in your infra­struc­ture][10] and ser­vice will con­tinue as nor­mal auto­mat­i­cally. With this approach you still do care about things like the oper­at­ing sys­tem and how to scale and all the magic that goes along with it. There are some steps being taken to ease this pain already in the IaaS world such as [Amazon’s Cloud­For­ma­tion][11] or the open source equiv­a­lent for Open­Stack called [Heat][12] which look promising.
  * Plat­form as a Ser­vice (PaaS) — this is really an evo­lu­tion of IaaS where instead of me (the appli­ca­tion devel­oper) main­tain­ing the under­ly­ing infra­struc­ture and tak­ing care of the oper­at­ing sys­tem, fail­ures and scal­ing etc. I now let the PaaS do that so that I can focus on my code and my appli­ca­tion alone. The steps to setup this blog are a pretty good exam­ple of how PaaS works.
  * Soft­ware as a Ser­vice (SaaS) — basi­cally hosted appli­ca­tions such as SalesForce.com or ser­vices pro­vided by Google such as Google Mail. I could have even gone with the SaaS approach by using a ser­vice like [WPEngine][13] to host this site and they would have taken care of all the has­sle or run­ning it and keep­ing it secure (at a cost). SaaS style appli­ca­tions are sort of what I expect most appli­ca­tion devel­op­ers to develop going for­ward and the smart ones will start build­ing their apps on a PaaS — like the [Cloud9 IDE][14] which is entirely run on the Open­Shift PaaS.

You may have more thoughts and ideas on these phases (com­ments wel­come) but for me as a lazy devel­oper who still likes to have con­trol I think it’s fan­tas­tic that I can now have an appli­ca­tion up and run­ning with a few key presses or clicks and what’s even more amaz­ing is that it’s com­pletely repeat­able and doesn’t depend on a huge IT depart­ment to run, any­one can host their own Open­Shift instance using either the [Ori­gin][15] com­mu­nity ver­sion or the fully sup­ported and tested [Enter­prise][16] ver­sion or just use the [Online][17] ver­sion if you are like me and don’t want to think about man­ag­ing servers anymore.

 [1]: http://wordpress.org/
 [2]: https://www.openshift.com/
 [3]: https://www.gandi.net/domain
 [4]: https://github.com/openshift/wordpress-example
 [5]: https://www.openshift.com/blogs/custom-url-names-for-your-paas-applications-host-forwarding-and-cnames-the-openshift-way
 [6]: https://www.openshift.com/kb/kb-e1047-how-do-i-backup-and-restore-my-openshift-data
 [7]: http://en.wikipedia.org/wiki/GeoCities
 [8]: http://en.wikipedia.org/wiki/Common_Gateway_Interface
 [9]: https://www.linode.com/
 [10]: http://www.codinghorror.com/blog/2011/04/working-with-the-chaos-monkey.html
 [11]: http://aws.amazon.com/cloudformation/
 [12]: https://wiki.openstack.org/wiki/Heat
 [13]: http://wpengine.com/
 [14]: https://c9.io/
 [15]: https://www.openshift.com/products/origin
 [16]: https://www.openshift.com/products/enterprise
 [17]: https://www.openshift.com/products/online
