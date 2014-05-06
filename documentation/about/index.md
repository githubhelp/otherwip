---
title: About EmonHub
tags: 
categories: 
published: True
layout: default
js: index
---

Emonhub was previously known as the OEM gateway and originally written by Jérôme Lafréchoux. 

It has been used by the OpenEnergyMonitor project for sometime, mainly but not exclusively as a standalone data forwarding solution, It became better known as the "Rock-solid Gateway" as when installed on a read-only sdcard it offered a simple and very reliable alternative to a self hosted emonCMS server, faithfully forwarding data to emoncms.org.




RFM2Pi Gateway

What and why

The gateway is the software running on the Raspberry Pi that reads from the COM port (serial port) of the RFM2Pi board and sends data to a local, and optionally a remote, emonCMS instance.

The historical implementation is a php script: raspberry_run.php that was called once every minute through crontab to make sure it was started again in case of crash. There was a discussion about how to improve this (see here). From emonCMS v5, a script is included to make it run as a daemon.

In the meantime, I wrote an alternative python script. It aims at being more robust, easier to extend, and it features better logging.

Installation and troubleshooting

Since this is still work in progress, you should use the latest version of emonCMS and its raspberrypi module (at least v5). For installation and usage, follow instructions in readme file.

To try it, make sure you've got the parameters right in the Raspberry Pi config tab of your local emonCMS installation. If you are using legacy crontab-launched php script (raspberry_run.php), first remove the crontab line that launches it and terminate any running instance (or reboot if you don't know how to kill a process). We don't want the two gateways to work at the same time.

If anything goes wrong, launch the script manually and see what happens (I would do that even before setting it to run on startup):


/var/www/emoncms/Modules/raspberrypi/rfm2pigateway.py

All the logging is output to the console and you can check everything works as expected.

In case of failure, it is possible to check the settings with the dedicated command line option:


/var/www/emoncms/Modules/raspberrypi/rfm2pigateway.py --show-settings

Note that since the standalone OEM Gateway, we may question the pertinence of maintaining the python gateway in the Raspberry Pi module. I advise to use the OEM Gateway instead.

OEM Gateway

The RFM2Pi gateway python script was designed as a copy of the php script. It has a few limitations :
• It is parametered via emonCMS GUI, which is nice, but takes a whole emonCMS installation on the Pi
• It is limited to RFM2Pi inputs

Starting from this, I wrote a standalone gateway : OEM Gateway.
• It can be configured through the GUI or through a configuration file, in which case there is no need for a database, and it is easier to extend (no need for a GUI modification).
• It can listen not only to a RFM2Pi board, but to anything on the serial port or on a socket, which allows easy communication with any local or remote program.
• It can repeat on the RF link the frames that are received on a socket.
• The samples are stored when the network is down (work in progress).
• Its object oriented design makes it relatively easy to extend (add support for different sources of data, or different storage and display servers).
• It allows the use of the base for forwarding only, which may preserve the SD cards: ? http://openenergymonitor.org/emon/node/2292
? http://openenergymonitor.org/emon/node/2312


The OEM Gateway is now included in the so-called "Rock solid" SD card. This ready-made card allows the RPi to act as a base, but it is read-only to preserve the SD card from wearing off, and therefore it does not embed the emoncms installation. It only acts as a repeater.

There are limits to this object oriented approach. For instance, while being able to send to different types of display servers sounds nice, in practice, most of them don't expect the same kind of data. For instance, they don't do post-processing like in emoncms. Currently, no other display backend is implemented.
