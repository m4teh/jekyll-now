---
author: Mathew Estrada
title: Build an awesome APU based pfSense Router
categories:
- Tutorial
images:  /assets/2014-09-19-build-an-awesome-apu-based-pfsense-router/
redirect_from: "/2014/09/build-awesome-apu-based-pfsense-router"
---
![pfSense logo]({{page.images}}pfsense.png)

I have been running pfSense under VirtualBox for many years now. Whilst I like it, I prefer to run a standalone instance because I have a 100mbit internet connection and this pulls a lot of resources. It’s neater, tidier can perform a touch better and quite frankly I wanted a non-windows dependent firewall router that didn’t have to be rebooted for Windows Updates or VirtualBox instability.

There are many options for pfSense hardware available, two common ones being [pfSense store APU](http://store.pfsense.org/VK-T40E/) and [Netgate APU](http://store.netgate.com/APU4.aspx), both which run off the [PC Engines](http://www.pcengines.ch/apu.htm) designed hardware.

We will be building this unit based off the hardware sold directly from the originating manufacturer, PC Engines. As you can see, it is far cheaper with the exact same end product. The only difference is the 20 minute set up time you will need to self assemble.

The APU is a cheap little fan less (passively cooled) device that incorporates a 1Ghz dual core 64-bit architecture AMD G-T40E, 3 x gigabit LAN ports, 2 x USB 2.0, 2 x miniPCI express inc. SIM slot and mSATA slot. Perfect for a router, PBX or similar.

Things you will need:

<!--more-->

- \$127 – \$155 – PC Engines [APU1C](http://www.pcengines.ch/apu1c.htm) or [APU1D4](http://www.pcengines.ch/apu1c4.htm) (2GB vs 4GB RAM)

- \$5.00 – [EU](http://www.pcengines.ch/ac12veur2.htm),  [UK](http://www.pcengines.ch/ac12vuk.htm), [US](http://www.pcengines.ch/ac12vus.htm) or [AU ](http://www.jaycar.com.au/productView.asp?ID=MP3490)power adapter

- \$9.30 – [Silver case](http://www.pcengines.ch/case1d2u.htm), [Black case](http://www.pcengines.ch/case1d2blku.htm) (disperses heat best), [Red case](http://www.pcengines.ch/case1d2redu.htm) or [Blue case](http://www.pcengines.ch/case1d2bluu.htm)

- \$1.30 – [Null modem serial cable](http://www.pcengines.ch/db9cab1.htm)

- \$5.00 – USB to serial cable

- \$20 – [16GB mSATA SSD](http://www.pcengines.ch/msata16d.htm)

- USB drive for pfSense installation




**APPROX TOTAL – $195 USD**

### [Purchase here](http://www.pcengines.ch/order1.php?c=4)

 

Your order will usually be sent via UPS express and arrive quite quickly. Mine arrived in Australia a few days after shipping, which is fantastic.

*Please read http://www.pcengines.ch/pdf/apu1.pdf in conjunction with the below guide.*

#### Step 1 – Assembly

1. Unscrew the hex nuts located on the serial port. You won’t be able to fit the board into the casing otherwise.
2. Install the CPU heat spreader onto your board by following [these easy instructions](http://pcengines.ch/apucool.htm).
3. Install mSATA SSD by slotting it into a socket in the centre of the board.
4. Carefully insert the board into the case and secure. Close casing and screw hex nuts back on.



#### Step 2 – Pre-install

1. Download a copy of [AMD64 pfSense](https://www.pfsense.org/download/mirror.php?section=downloads) “Live CD with Installer on USB memstick” with serial.
2. Download [physdiskwrite + gui](http://m0n0.ch/wall/physdiskwrite.php) to write the pfSense image to USB. Tick the 2GB restriction removal in the software.
3. Download [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe) to access the serial interface.
4. Ensure your USB serial cable is plugged in and configure the COM port with Bits per second 115200, Data bits 8, Parity None and Stop bits 1. Configure this for PuTTY also.
5. Ensure cables are connected to the APU -before- powering on the unit. Plug the power cord into the device before the power socket to avoid sparking.



#### Step 3 – Installation

1. Plug the pfSense install USB into the APU for boot. If you wish to run a memtest before installation, you can do that. Power on the APU.
2. The serial console should start to populate and automatically boot from USB. There will be garbabe text displayed due to baud inconsistencies but this will dissipate.
3. Install pfSense as you would normally. If you have never done this before, follow a [guide](https://doc.pfsense.org/index.php/Installing_pfSense). I personally booted the live version, configured my LAN parameters and then used command “99” to install to the hard drive so that I could disconnect the serial cable and use the web interface.
4. Port configuration is from left to right; re0, re1 and re2 respectively.




That’s pretty much it. From here you can import your settings from existing pfSense installations or configure it fresh. Let me know what your experiences are with the APU.