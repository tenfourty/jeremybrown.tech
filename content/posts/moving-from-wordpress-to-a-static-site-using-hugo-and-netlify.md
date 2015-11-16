+++
Categories = []
Description = ""
Tags = []
date = "2015-11-16T21:04:09Z"
title = "Moving from WordPress to a static site using Hugo and Netlify"

+++

I've had it in the back of my mind for a while to move this site to be a statically generated site to escape the constant admin and update cycles of wordpress and over the weekend I finally managed to get around to it.

In the end it was remarkably painless, probably because I didn't have that many blog posts!

I chose to use the excellent and blisteringly fast [Hugo](http://gohugo.io) for the site itself and [Netlify](https://www.netlify.com) to actually host it. Everything is publicly available (of course) on [GitHub](https://github.com/tenfourty/tenfourty.com).

The steps to do this were pretty easy:

* [WordPress to Hugo Exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter)
* Some hand crafting of my Hugo theme to get something I liked (I really liked Hugo's local server and live reload)
* setting up Netlify from my github account (super easy)
* letting it all run (for free) on Netlify completely reliably.

In the end I'm really happy with the result, my site is faster and doesn't require as much maintenance as my previous setup.

Previously I was running this site using [Wordpress on OpenShift](/2013/08/28/the-evolution-of-paas-and-how-this-site-wassetup/) and I found that the pain of WordPress requiring constant updates, plus OpenShift regularly restarting the node my code was on (meaning that my monitoring setup was sending me alerts all the time) meant I spent far more time maintaining and checking this website than I ever wanted to. The other pain I had with OpenShift 2.0 was that their WordPress cartridge didn't really work very well for content that was uploaded and I suspect they moved my app/gear from one node to another at some point and I lost some files from my uploads directory - annoying. I think that a lot of this has been fixed in OpenShift 3 but for this wee site I'd prefer to just have it statically generated and hosted in Netlify's CMS.

In the future I might investigate running this in Docker in OpenShift 3/Kubernetes but for now Netlify is hard to beat as a new home.
