+++
Categories = []
Description = ""
Tags = []
date = "2016-06-08T16:06:49+02:00"
title = "Building the Ultimate Home Media Center with the new AppleTV 4, Plex/Kodi and a QNAP NAS"

+++

*TL;DR; The Apple TV 4 can run Kodi (XBMC) directly and play all my Movies, TV Shows and Music from my QNAP NAS. It's quite a sweet setup.*

I've finally had a bit of time to work on a project I've had on my back burner for quite some time, building a home entertainment system to play all of my movies and TV series that I've got on my NAS.

I already have a QNAP NAS and it supports running Plex or Kodi (formerly XBMC) as well as it's own Media Center, however as I started to research the project a bit I realised that really the NAS on it's own wasn't going to be enough, most home media setups have a media server that can do transcoding from one format to another for the various devices that can connect to it. As the model of NAS I have ([TS-239 Pro](http://www.cnet.com/products/qnap-ts-239-pro-dual-bay-nas-server/specs/)) only has an Intel Atom 1.6 GHz processor and 1GB of RAM so it wasn't going to cut it.

My research lead me to a bunch of mini-PCs that could run Linux and in the end I drew up the following shortlist.

- The [Kangaroo +](http://www.kangaroo.cc/kangaroo-2/) - I love the form factor and portability. It runs Linux but I was dubious it's processor was capable of heavy duty transcoding with a CPU PassMark of only 1706 (normally you need 2000+).
- The form factor of the [Intel Compute Sticks](http://www.intel.com/buy/us/en/catalog/desktop/computesticks) were also pretty cool! Only the top of the range model has a sufficient PassMark and it is quite pricey. Also I wasn't sure how well Fedora would run on it (Ubuntu does apparently but I still prefer Fedora).
- The [System76 Meerkat](https://system76.com/desktops/meerkat) and the [Zareason Zini](https://zareason.com/shop/Zini-1550.html) are similarly priced higher end options with more horsepower (Intel i3/5 CPUs) and storage/expansion options. These were the most flexible and expensive options.

During all of this I stumbled across some articles about running [Plex](https://plex.tv) and [Kodi](https://plex.tv) as apps on the new [Apple TV 4](http://www.apple.com/uk/tv/). After I did a bit more research I realised that this might actually be the most cost effective solution of the bunch AND offer me a whole lot of flexibility in what I could run on it.

So off I went down to my local Apple store to get one and I've set it up like this:
```
            ┌──────────────────┐                
            │                  │                
            │        TV        │                
            │                  │                
            └──────────────────┘                
                      ▲                         
                      │                         
            ┌───────────────────┐               
        ┌──▶│HDMI Auto Switcher │◀──┐           
        │   └───────────────────┘   │           
┌──────────────┐            ┌───────────────┐   
│ TV Receiver  │            │  Apple TV 4   │   
└──────────────┘            └───────────────┘   
                                    │           
                                    ▼           
                        ┌──────────────────────┐
                        │       QNAP NAS       │
                        └──────────────────────┘
```

I've been running this setup for a couple weeks and I have to say that I'm really pleased with the setup I've evolved to.

I've not settled on Plex or Kodi for playback of my media (Music, TV Shows, Movies) - both have their pros and cons and I'm currently running both side by side, I will follow up with a sequel to this blog post with more in depth analysis.

Not only am I using the NAS for storing my Movies and TV Shows but I'm also using it to collect new ones.

To get TV Shows I'm using [SickRage](https://sickrage.github.io) and for Movies I'm using [CouchPotato](https://couchpota.to) and both of these are driving [Transmission](https://www.transmissionbt.com) (a BitTorrent Client) that is also running on the QNAP NAS.

I found that the interface for both SickRage and CouchPotato was a bit too technical for some people at home so I've got both of them setup to sync with [Trakt](https://trakt.tv), so whenever I add something to my Watch List on Trakt it is automatically downloaded to the NAS and available for playback on my Apple TV.

My setup looks like this:
```
  ╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳   
 ╳                                            ╳  
 ╳                   Trakt                    ╳  
 ╳                                            ╳  
  ╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳╳   
                        │                        
                        │                        
            ┌───────────┴───────────┐            
┏━━━━━━━━━━━╋━━━━━━━━━━━━━━━━━━━━━━━╋━━━━━━━━━━━┓
┃QNAP NAS   │                       │           ┃
┃           ▼                       ▼           ┃
┃ ┌───────────────────┐  ┌────────────────────┐ ┃
┃ │SickRage - TV Shows│  │CouchPotato - Movies│ ┃
┃ └───────────────────┘  └────────────────────┘ ┃
┃           │                       │           ┃
┃           └───────────┬───────────┘           ┃
┃                       │                       ┃
┃                       ▼                       ┃
┃        ┌─────────────────────────────┐        ┃
┃        │Transmission - Torrent Client│        ┃
┃        └─────────────────────────────┘        ┃
┃                                               ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
```

I have to say this is a pretty sweet setup and is working really well for me so far. Compared to the other options out there this was the most cost effective AND I have access to all the other cool Apple TV Apps that are appearing.
