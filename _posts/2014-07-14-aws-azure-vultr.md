---
author: Mathew Estrada
slug: aws-azure-vultr
title: Cloud comparison – Amazon AWS vs Microsoft Azure vs Vultr
categories:
- Technology
- Review
images:  /assets/2014-07-14-aws-azure-vultr/
---
I have been playing around with cloud based virtual server applications for a few months now and I thought I’d share a non-technical summary of each.
The ability to spin up virtual servers for deployment within seconds is extremely handy and provides endless possibilities. Web servers, game servers, file servers, VPN servers, VoIP servers, dummy test servers, almost anything really. This is just a very quick recap on what I find most appealing (or not) about each service.



> If you can’t be bothered reading: I give a clear victory to Vultr for their innovation, uniqueness and very low-cost affordability. See below for details.

 

![amazon-aws-logo]({{page.images}}aws.jpg)



Amazon AWS EC2 was my second cloud adventure and is a lot of fun to mess around with. One of the best things about AWS is the one year [free tier](https://aws.amazon.com/free/). This allows you to operate free virtual servers in certain circumstances (low-cost *t2.micro* instance) for one year, before you start being charged standard instance rates. You also get 15gb of data transfer before you start getting charged (going over your 15gb free data threshold doesn’t cancel the free instance tier, you simply pay for the extra data you use).

This is perfect for anybody wanting to run a small/small-medium website.


**The good:**

- Free tier for one year (750 hrs/month) on selected instances.
- Data centres available in places like Australia (albeit at a higher price).
- Very simple web based firewall so you don’t have to muck around with individual server firewalls.
- Clear billing view that clearly states where every cent of your running costs is derived from.
- Integrate with an array of other Amazon AWS entities (such as Route 55 DNS or Elastic IPs among many others).
- Spot Instances which allows you to run instances cheaper than the on-demand cost, however your server will terminate if somebody out bids your spot price.
  ​

**The bad:**

- Need a credit card to utilize free tier, common practice but just a note.
- Could do with better explanation of how free tier works and if you go over the 15gb limit. I assumed this would cancel free tier and start billing data + instance costs, but no, you are simply billed the additional data costs as described above (which is a good thing).
- U.S. IP block despite cloud services being operated in other countries. This creates issues for geo IP-based services if you’re using it for VPN purposes.
- The online ssh/console view never seemed to work properly




![windows-azure]({{page.images}}azure.png)


Windows Azure was my first trial of cloud based computing. It gave me an insight into what the cloud could offer and how it works. Unfortunately I wasn’t very happy with Azure and that’s when I decided to move on to Amazon AWS to see if it picks up the slack. Disclaimer: I used Azure very little in comparison to these other cloud services. It certainly wasn’t an extensive experience, so take this information (or lack thereof) with a grain of salt.


**The good:**

- Free $200 credit valid for 30 days on sign up
  ​

**The bad:**

- Data centres not available in countries like Australia yet.
- Couldn’t accurately ascertain servers location using ping/speed testing.
- Very poor data speeds even when speed testing in the same region I assigned to the instance (South East Asia).
- Also uses U.S. IP blocks which creates geo issues for some websites or services.
- Web firewall blocks ICMP and you cannot disable it. This is inconvenient for VPN (and other) users as you can’t ping or be pinged properly.
- Web UI seems very laggy and somewhat confusing to navigate.
- Trial requires a credit card like Amazon, however this is just a side note.







[![vultrlogo]({{page.images}}vultr.png)](http://www.vultr.com/?ref=6806586)


Vultr was brought to my attention by a thread on Whirlpool discussing low-cost VPS solutions. Upon initial observations, I was impressed at how clearly and simply the information was presented on their website. The fact you can run a VPS for \$5 a month is exciting. I immediately signed up and added credit to my account.

Vultr has a limited time offer that sees them double your first credit deposit.  I committed \$25 which was doubled to \$50. I then Googled and found a [$10 coupon code](http://vultrcoupons.com/). This gave me a FULL year of VPS credit for \$25. The process was very quick and painless. Funds were added to my account immediately without manual review, and I was able to spin up instances within seconds.


**The good:**

- Extremely cheap instance and bandwidth costs (\$0.007/hr or \$5/month).
- Generous sign up bonuses and publicly available coupons.
- Ability to freely set the servers reverse DNS within web console (something most cloud platforms subject to approval and authorisation).
- Unlimited free snapshots even while server is running (for a limited time).
- Ability to create a VPS from an uploaded .ISO.
- All web console features worked flawlessly (ssh console, reinstall, stop/start, destroy, restoring snapshots, etc).
- Geo specific IP addresses, not just U.S. block ranges (at least in Australia anyway).
- SSD only arrays
- Automatic backups (at a cost)
  ​

**The bad:**

- Unclear/No SLA (uptime guarantee).
- 1/10th data restriction for Australian servers (1000gb reduced to 100gb). This is common due to outrageous bandwidth prices in Australia. However, 100GB is still generous down under.
- Due to common abuse of cloud/gaming cloud IP block ranges, some websites appear to block or restrict access in mass. [Whirlpool is a contender](http://cl.ly/image/3F0k1b470729/Image%202014-07-14%20at%204.50.54%20AM.png) here, and they won’t remove the CAPTCHA. All providers seem to have this issue though.
- No web-based firewall. You must configure firewalls on your server.
- Less peace of mind and/or brand trust due to being new?
- No trials.





#### **Conclusion**

I could go on all day about all the awesome features that each of these providers has, but the fact is I would be here all night. These are just some main pointers that I find most prevalent in everyday use. Vultr is a new cloud solution and will continue to develop their brand and trust over many years to come, but from my experience, there isn’t a reason to not give them a go. 
They seem to be ticking all the right boxes thus far. As with any provider, good practice means you should be regularly backing up your data just in case.

You can read a more technical comparison of Vultr vs Digital Ocean and Linode [here](http://blog.due.io/2014/linode-digitalocean-and-vultr-comparison/).