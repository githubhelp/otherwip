---
title: Raspberry Pi SD-card
tags: 
categories: 
published: True
layout: default
js: index
---

### The Raspberry Pi SD-card

[trystans ro image](http://openenergymonitor.org/emon/node/4283)
http://www.raspberrypi.org/forums/viewtopic.php?f=29&t=22596
https://wiki.debian.org/ReadonlyRoot


Configure Raspbian to run in read-only mode for increased stability (optional but recommended)

Steps from: http://www.raspberrypi.org/forum/viewtopic.php?f=29&t=22596

    sudo nano /etc/default/rcS

add line 

    RAMTMP=yes

    sudo nano /etc/fstab

    tmpfs           /tmp            tmpfs   nodev,nosuid,size=30M,mode=1777    0    0
    tmpfs           /var/log        tmpfs   nodev,nosuid,size=30M,mode=1777    0    0
    proc            /proc           proc    defaults          0       0
    /dev/mmcblk0p1  /boot           vfat    defaults          0       2
    /dev/mmcblk0p2  /               ext4    defaults,ro,noatime,errors=remount-ro  0       1
    # /dev/mmcblk0p3  /home           ext4    defaults,noatime

c) fix mtab: 

    sudo rm /etc/mtab
    sudo ln -s /proc/self/mounts /etc/mtab

Change mount mode:

    sudo mount -o remount,ro /dev/mmcblk0p2  /
    sudo mount -o remount,rw /dev/mmcblk0p2  /
