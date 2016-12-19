+++
categories = ["Blog Posts", "Technology", "Mac",]
date = "2016-12-19T10:03:00Z"
description = "How to stop the BlueJeans App for Mac using all of your CPU and Battery with the AppPolice app"
draft = "false"
keywords = []
slug = ""
title = "How to stop the BlueJeans App for Mac using all of your CPU and Battery"
type = "post"

+++



**TL;DR** Use [AppPolice for the Mac](https://github.com/fuyu/AppPolice) to control how much CPU the BlueJeans for Mac app can use (100% or 1 core seems to work) so that your computer is usable while using video and your battery won't be zeroed by a one hour call.

I'm a big fan of using video for calls instead of just voice - participants are often far more engaged when you can all see each other, and you can give thumbs ups, raise your hand and give other visual cues as part of the conversation that avoids the [usual voice conference call](https://www.youtube.com/watch?v=DYu_bGbZiiQ).

At Red Hat we encourage remote work, and one of the ways we make it work is to have a lot of video calls using [BlueJeans](https://www.bluejeans.com/), which works great for me on my Mac except for one horrible problem that tends to completely kill my experience - if I enable my camera (kind of important for a video call) when I'm using the BlueJeans desktop app (seems to happen with Chrome and browsers as well) the BlueJeans app seems to try to hog **ALL** of my CPU that it can use and when it has all the cores of my processor spinning away at maximum I will lose HALF of my Mac's battery life after a one hour call!

<!--more-->

I looked into running the BlueJeans app on Linux in a docker container with X11, but apps run this way on my Mac lose their native feel and end up being a bit laggy, though this approach might work for Linux users.

In the end I found a cool app for the Mac called [AppPolice](https://github.com/fuyu/AppPolice) that allows you to control how much CPU an application can consume on your Mac, it has a simple GUI, runs in the background and can remember what you set for apps, so you don't have to use it every time BlueJeans (or other apps) are misbehaving.

Getting it up and running is easy, just download and install the app from the Disk image on [the AppPolice releases page](https://github.com/fuyu/AppPolice/releases) and once it's running launch BlueJeans and set its CPU to max 100% or 1 processor core which seems to work well for me - I might experiment and reduce this further but so far this hack works quite well.

![Screenshot of AppPolice and BlueJeans](/img/BlueJeans_AppPolice_Screenshot.jpeg)

With all of that, I can have much better [video conference calls instead!](https://youtu.be/JMOOG7rWTPg)

{{< youtube JMOOG7rWTPg >}}