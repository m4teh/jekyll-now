---
author: Mathew Estrada
slug: stream-netflix-chromecast-pfsense
title: How to stream Netflix to Chromecast using pfSense
categories:
- Tutorial
images:  /assets/2014-08-31-stream-netflix-to-chromecast-using-pfsense/
---

In this guide I will teach you how to stream US Netflix using a smart DNS service in pfSense WITHOUT setting your entire network to use the smart DNS servers.
There are many ‘security’ implications of sending all your DNS traffic over a rogue/less trusted network, and quite frankly, you don’t know if they’re logging and or selling your lookups or similar.

Chromecast by default uses Google DNS instead of your router for DNS lookups and bypasses your router entirely. This is a problem because we cannot manipulate the DNS lookups without first tricking Chromecast into using our routers DNS.

This guide assumes:

- You have a Netflix account

- You are using pfSense

- You have a Smart DNS provider (e.g. [getflix.com.au](http://getflix.com.au/))

  ​



### Step 1 – Setting up DNS Overrides

1. **Navigate to Services > DNS Forwarder.**
2. **Ensure your DNS Forwarder is enabled.**
3. **Scroll down to “Domain Overrides” and add a new entry.**
   ​

The domains that we need to override are:

> netflix.com
> movies.netflix.com

*You will need to obtain the Smart DNS IP address from your DNS provider. For example, Getflix operates the servers listed on this page. You should pick the closest server and use this as the override IP. Mine is 54.252.183.4.*

![pfSense Domain Overrides]({{page.images}}domainoverride.png)

This is enough to access Netflix on other services such as your PC or Mac. However, because Chromecast is hard wired to use Google DNS instead of your router DNS, we need to perform one extra step.



### Step 2 – Redirecting Chromecast DNS requests to pfSense

1. **Navigate to Firewall > NAT > Port Forward.**
2. **Add a new entry with the following details:**

> **Interface:** LAN  
> **Protocol:** TCP/UDP  
> **Source:** any (or enter Chromecast LAN IP in ‘Single host or alias’)  
> **Source Port:** any  
> **Destination:** any  
> **Destination port:** DNS  
> **Redirect Target IP**: IP address of your pfSense router/gateway  
> **Redirect Target Port:** DNS  
> **Filter Rule Association:** None

 

![pfSense NAT Redirection]({{page.images}}nat.png)

 

# All done!

What step 2 does is redirect all DNS requests within your network to your router. This means that any manually set servers on a device will always forward to the router. In my case, I have only redirected the Chromecast IP to pfSense. If I manually set my DNS on another computer, this will not be re-routed to pfSense.