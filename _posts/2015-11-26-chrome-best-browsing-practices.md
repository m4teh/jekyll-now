---
author: Mathew Estrada
slug: alertegps-wikango
title: AlerteGPS 700 by Wikango
categories:
- Reviews
images:  /assets/2015-11-26-chrome-best-browsing-practices/
---
Chromium is my browser of choice. I’ve tinkered with settings and obtained the best usability vs privacy trade-off for my liking.

Before I go into detail about specific settings, a couple of pointers..

1. **I browse with JavaScript disabled**. I have an extension that toggles websites on/off. It’s actually quite practical and you should try it. The security gain is worth it. During writing of this, I even saw [an article on WiRED](http://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/) about the same thing.
2. I aim to **clear most settings on browser exit**, somewhat resembling the Firefox ‘never remember history’ permanent private browsing mode.
3. I use an [updater for the open source Chromium](http://chromium.woolyss.com/download/), instead of the Google Chrome software package.
4. **Certain cookies are white listed** so they aren’t cleared on restart (lastpass, duckduckgo etc)
5. My primary search engine is non-tracking **DuckDuckGo**.
6. If you’re doing a fresh install, check and clear your “All cookies and site data” prior to browsing as Google likes to throw in a bunch of cookies and local storage for Google services after installation.

### Settings

##### Privacy

- Un-check all options
- Enable ‘Send a “Do Not track” request’

*Content settings:*

- Keep local data only until you quit your browser
- **[tick]** Block third-party cookies and site data
- Do not allow any site to run JavaScript
- Let me choose when to run plug in content
  Manage individual plug-ins – disable all except ‘Native Client’ (and PDF viewer if you prefer usability over security)
- **[tick]** Do not allow any site to disable the mouse curser
- **[untick]** Allow identifiers for protected content
- Do not allow sites to access your camera

This reduces calls home to Google with all your data, and minimises the attack surface somewhat.



##### Extensions

- [uBlock Origin](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm) – very lightweight and blocks a multitude of online ads, trackers, potential threats and WebRTC local IP reveal. If you don’t use this, you should.
- [HTTPS Everywhere](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp) – automatically connects to websites securely where available
- [JavaScript Toggle](https://chrome.google.com/webstore/detail/quick-javascript-switcher/geddoclleiomckbhadiaipdggiiccfje) – enable/disable websites access to JavaScript on the fly.
- [Cache Killer](https://chrome.google.com/webstore/detail/cache-killer/jpfbieopdmepaolggioebjmedmclkbap) – set to wipe all browser data on exit (cache, other persistent website data)
- [LastPass](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd) – gotta keep those passwords somewhere
- [Xmarks](https://chrome.google.com/webstore/detail/xmarks-bookmark-sync/ajpgkpeckebdhofmmjfgcjjiiejpodla) – bookmarks sync across browsers and devices



What you are left with when [performing an anonymity test](http://ip-check.info/) is a nice clean result. This is in comparison to my Firefox instance which has JavaScript enabled, and is how most browsers will display by default. Almost all of this data can and is used to track your presence online. Locking down the browser by restricting JavaScript, stopping call home features, running uBlock to block tracking companies & malvertising, deleting cache and other website data upon exit all demonstrate a substantial increase in browser security and anonymity. You’re simply reducing your online ‘footprint’ and severely hindering the ways that companies and government can monetise and monitor you.

 

## **Chromium:**

![Chromium Privacy]({{page.images}}Chromium.png)

## **Firefox:**

![Firefox Privacy]({{page.images}}Firefox.png)

 