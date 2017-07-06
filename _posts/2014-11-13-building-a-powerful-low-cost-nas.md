---
author: Mathew Estrada
slug: powerful-low-cost-nas
title: Building a powerful, low cost NAS
categories:
- Technology
images:  /assets/2014-11-13-building-a-powerful-low-cost-nas/
---

I have been in need of a NAS refresh for some time now. I was using a 4 bay [Synology DS411j](http://www.engadget.com/products/synology/ds411j/specs/) acquired in 2011. It featured an underpowered CPU and only 128mb RAM. How I used to run the NAS + SickBeard + SABnzbd + Transmission + media streamer on it…. I don’t know.

I decided on a FreeNAS build. I do not regret it. I went with a UFS file system. Although ZFS was preferable, proper operating procedures requires ECC RAM which then requires a server motherboard compatible with all the features that I want, including CPUs. I decided I couldn’t be bothered and I just settled for a desktop based machine utilising UFS, which is also quite a bit cheaper.

<!--more-->

Newegg listings are just for reference. Use staticice.com(.au, .nz, .co.uk) to find the lowest local pricing.



- $84 – [ASRock B85M Pro4 Micro ATX LGA1150 Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157388)

- $79 – [Intel Pentium G3420](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116949)

- $88 – [Kingston 8G 1600MHZ DDR3 CL11 1.35V Single Memory – KVR16LN11/8](http://www.newegg.com/Product/Product.aspx?Item=054-00X6-00002&cm_re=KVR16LN11%2f8-_-054-00X6-00002-_-Product)

- $45 – [Corsair VS350 ATX Power Supply](http://www.pccasegear.com/index.php?main_page=product_info&products_id=22269)

- \$45 – [Silverstone Precision PS08 Black USB3.0 Micro ATX Case](http://www.newegg.com/Product/Product.aspx?Item=N82E16811163247)
  **$341 AUD**

-  \$924 – *4x* [HGST Deskstar NAS 4TB SATA3 7200RPM](http://www.amazon.com/HGST-Deskstar-3-5-Inch-Internal-0S03664/dp/B00HHAJRU0)

   **TOTAL $1265 AUD** (minus shipping and PayPal fees)



When deciding on components, I had a few things in mind that I wanted:

1. motherboard capable of SATA 6GB/s with a minimum of 4x SATA ports
2. mini ITX case with at least 4 3.5″ HDD bays
3. 7200RPM NAS drives and not 5400RPM NAS drives
4. Integrated Ethernet and video



I am using a USB drive with FreeNAS installed. This will boot the OS into RAM on startup. I also memtested the RAM and error checked the hard drives before letting this go operational.

I used PC Part Picker to help pick the motherboard. They have an excellent search refine tool that lets you search with your requirements. This spat out the cheapest compatible motherboard with local pricing. **Perfect!**

I opted for Hitachi 7200RPM NAS drives because I wanted the crazy awesome reliability that Hitachi/HGST is known for, but also in a NAS optimised configuration with the beefier 7200RPM performance. It was worth it because the slower Western Digital Red 4TB 5400RPM drives were only $20ea less.

This price is pretty nice considering you can pay that much just for a retail NAS solution without hard drives.

The upside of this is I get to decommission a Windows Server machine which was acting as my download station. There is now lots less internal bandwidth being consumed because all data is written to the local hard drive (after it’s downloaded from SABnzbd for example) as opposed to over the network shares. I have absolutely no bottle necking now and I love it! Worthwhile upgrade which will hopefully last me a long time.




![NAS Memory Stats]({{page.images}}mem.png)

![NAS CPU Stats]({{page.images}}cpu.png)

![NAS Jails]({{page.images}}jails.png)