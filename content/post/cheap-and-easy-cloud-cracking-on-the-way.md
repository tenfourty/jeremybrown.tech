+++
author = "Jeremy Brown"
categories = ["Blog Posts", "Technology"]
date = "2010-11-27"
dsq_thread_id = [2028125631]
type = "post"
short-url = ["http://bit.ly/fAhLFx"]
tags = ["Amazon", "Cracking", "EC2", "GPU", "Hacker", "Wifi", "WPA"]
title = "Cheap And Easy Cloud Cracking On The Way"
aliases = "/2010/11/27/cheap-and-easy-cloud-cracking-on-the-way/"

+++

Ama­zon recently announced a new instance type for their [EC2 cloud ser­vice][1] that they call the [Clus­ter GPU][2] which has an impres­sive spec:

> 22 GB of mem­ory

> 33.5 EC2 Com­pute Units (2 x Intel Xeon X5570, quad-core â€œNehalemâ€ archi­tec­ture)

> 2 x NVIDIA Tesla â€œFer­miâ€ M2050 GPUs

> 1690 GB of instance stor­age

> 64-bit plat­form

> I/O Per­for­mance: Very High (10 Giga­bit Ethernet)

The really inter­est­ing part that has got a lot of peo­ple inter­ested is the fact that it has two high-powered graph­ics cards which can be used to do mas­sively pow­er­ful par­al­lel com­put­ing. Now there are many poten­tial appli­ca­tions for these GPUs — image and video pro­cess­ing, com­pu­ta­tional biol­ogy and chem­istry, fluid dynam­ics sim­u­la­tion, CT image recon­struc­tion, seis­mic analy­sis, ray trac­ing and so on. <span class="pullquote">But what really inter­ests me is the pos­si­bil­ity of using these GPU instances for pass­word cracking.</span>

It’s now well-known that using a GPU to crack pass­words can reduce the time required from some­thing like 2 months to 3 days, but what hap­pens when you throw one of these new Ama­zon instances at the prob­lem? And what if it’s not just one instance but a clus­ter of them that is used to do the mas­sively par­al­lel com­pu­ta­tion? TheÂ sheerÂ com­put­ing power that even a small clus­ter of these machines has avail­able would make short work of crack­ing all sorts of pass­words. Some that come to mind are:

  * Sys­tem Pass­word files which use the MD4, MD5, NTLM or SHA1 algorithms.
  * WPA-PSK or WPA2-PSK net­work pass­words (WEP is already triv­ial to crack).
  * Pass­word pro­tected RAR or ZIP files.
  * Pass­word pro­tected Microsoft Office or Open Office files.
  * Pass­word pro­tected PDFs.
  * Encrypted disks

Some peo­ple have already tested these GPU instances to [crack pass­word hashes][3] and [Pyrit has been tested on it][4] (could be used to crack WPA/WPA2). The per­for­mance of a sin­gle instance is impres­sive, [the cost is equally impres­sive][5] ($2.10 for an hour). Just a few years ago this kind of com­put­ing power was only avail­able to organ­i­sa­tions that had a large amount of resources such as gov­ern­ments, large cor­po­ra­tions and a few uni­ver­si­ties and research organ­i­sa­tions. Now any­one with a bit of tech­ni­cal knowl­edge and a credit card has access to it.

It’s only a mat­ter of time before some­one uses a clus­ter of these instances in anger to start crack­ing pass­words, in fact I’m sure some­one already is. How long will it be before some­one releases a com­mer­cial ser­vice based on this platform?

The only com­mer­cial ser­vice for pass­word crack­ing that I’ve found so far is [WPA Cracker][6] who claim to have a 400 CPU clus­ter, how­ever a ser­vice that uses a few EC2 GPU instances could blow away the per­for­mance of WPA Cracker. We could soon start to see pass­words being cracked in just a few min­utes with a large enough clus­ter. I wouldn’t be sur­prised if it wasn’t long before some­one sets up a ser­vice like this which inte­grates nicely into [back­track][7] or some other wi-fi sniff­ing soft­ware that grabs the required wi-fi pack­ets and uploads it to an EC2 clus­ter that cracks the pass­word in a few minutes.

All of this is a very strong argu­ment for using longer and more com­plex pass­words that are less vul­ner­a­ble to dic­tio­nary and brute force attacks, and one more rea­son not to assume that your wi-fi net­work is secure because you are using WPA or WPA2 instead of WEP.

 [1]: https://aws.amazon.com/ec2/
 [2]: https://aws.amazon.com/ec2/hpc-applications/
 [3]: http://stacksmashing.net/2010/11/15/cracking-in-the-cloud-amazons-new-ec2-gpu-instances/
 [4]: https://groups.google.com/group/pyrit/browse_thread/thread/6fb00f6c41e6ee0c
 [5]: http://aws.amazon.com/ec2/pricing/
 [6]: http://www.wpacracker.com/
 [7]: http://www.backtrack-linux.org/
