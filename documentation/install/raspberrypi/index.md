---
title: RaspberryPi Install
tags: 
categories: 
published: True
layout: default
js: index
---

Installing EmonHub to Raspberry Pi
===================================

-----------------------------------

#####Installing emonHub to the Raspberry Pi using the debian package installer really couldn't be any easier. This first part adds the address of the emonHub repository where the package is, to the Pi's sources list and only needs to be done once, after then any future installs or upgrades of debian packaged emonHub, emonCMS or their modules will use this same address.

{% include step/wheezy2src.md %}

----

{% include step/hub-deb.md %}

---

Follow the set-up screens

-----------------------------

Adding a RFM2Pi

Create a RO image

#### [Set up RaspberryPi hdd]({{site.page}}install/raspberrypi/hdd)

#### [Set up RaspberryPi hdd]({%include page/rpi-hdd%})





