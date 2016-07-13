+++
author = "Jeremy Brown"
categories = ["Blog Posts"]
date = "2015-05-26"
dsq_thread_id = [3795765956]
type = "post"
title = "Fixing the fonts on my new MacBook Pro 13″ Retina on external displays"
aliases = "/2015/05/26/fixing-the-fonts-on-my-new-macbook-pro-13-retina-on-external-displays/"

+++

I have a new Mac­Book Pro 13″ Retina (early 2015) that is pretty amaz­ing, how­ever when I plugged it into my large exter­nal dis­play at the office fonts became really blurry and ugly, so bad that I could barely look at the display!

After a lot of mess­ing around I’ve found a cheaper solu­tion than buy­ing an awe­some Apple display!

Basi­cally it’s a com­bi­na­tion of this arti­cle on the prob­lem [Fonts Look Blurry in OS X Yosemite? Change Font Smooth­ing Set­tings](http://osxdaily.com/2014/10/27/change-font-smoothing-text-os-x-yosemite/) but I found that though the arti­cle rec­om­mends a set­ting of “2” or Medium I found (after much repet­i­tive reboot­ing and chang­ing one vari­able at a time) that a set­ting of “4” or Strong actu­ally worked best for my display.

The actual com­mand to type at the ter­mi­nal is:

```defaults -currentHost write -globalDomain AppleFontSmoothing -int 4```

This set­ting wasn’t doc­u­mented in the orig­i­nal arti­cle but it can be found in this one [Change Font Smooth­ing](https://software.com/mac/tweaks/change-font-smoothing) how­ever the com­mand line syn­tax in the first arti­cle had an effect while this didn’t work.

```defaults write NSGlobalDomain AppleFontSmoothing -integer 4```

Com­ment and link to this if this help you as a ran­dom Googler, it’s always great to know I’ve saved some­one a bit of time!
