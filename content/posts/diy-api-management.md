+++
author = "Jeremy Brown"
Categories = ["Blog Posts"]
Description = ""
Tags = []
date = "2015-11-29T21:13:13+01:00"
title = "DIY API Management, Seriously?"
draft = true

+++

When was the last time you thought that one of the myriad Databases out there wasn't good enough for your purposes so you were going to write your own? Or a message broker or even an Operating System?[^1]

Most folks aren't building their own databases these days but I'm constantly surprised at the number of companies that are attempting to build their own DIY API Management software.

Honestly, I can understand if you are a software vendor and you felt the need to enter this space for whatever reason, however this post is focused more at those who's core business is not software as such but providing support for a real business where APIs are core for the business but the software is not a core competitive advantage.

My thesis is that if you are not in the software business, don't build software - buy it!

#### "Unless you are operating a software company, software should not be central to the way you view your business. It’s just a means to an end. And to be classed as truly successful, the means should be quietly efficient and as close to invisible as you can get.” - Robert X. Cringely in Inc Magazine, February 2003

### Not Invented Here Syndrome

Engineers always want to build everything from scratch themselves, theres always a reason why what's currently available off the shelf needs to be re-written. Here are a couple of the top reasons why people want to build their own API Platform (though you could apply this argument to most software):

1. "APIs are too important to the future of our business to rely on another party to build it for us"
1. The cost of buying the software vs build (Yes really!).
1. Speed in responding to market/business changes.

### Cost of Build vs Buy

Lets start with the easiest argument to tackle, cost. Repeat after me, "building custom software is more expensive than off-the-shelf software".

Initially writing a piece of software to do a set of basic features seems tempting... but the true cost of software is not how many man days it took to write it.

Software is like an iceberg, everything above the water is the initial implementation and the vast majority under the water is the cost of maintaining it. Without this basic principle there wouldn't be any commercial software vendors.

A software vendor makes money by making the cost of an amazing piece of software affordable by spreading it across many customers.

Secondly the way we buy software is changing, we are moving to a SaaS model where you pay for what you use

cloud pricing only goes one way - AWS will never increase their pricing the trend is always down

### Your APIs make you a unique snowflake, not how they managed



### Ending up in your own dead end cul-de-sac

network effect with a vendor

*Full Disclosure - I work for [Apigee](http://apigee.com/) (a leader in the API Management space), nonetheless opinions are my own.*

[^1]: there are of course valid reasons some people will write a whole new Database, Message Broker or Operating System but I just don't think this applies to the majority of companies.
