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


Starting with a fresh raspbian image
    
    sudo apt-get update
    sudo apt-get -y upgrade
    sudo cp /etc/default/rcS /etc/default/rcS.orig
    sudo sh -c "echo 'RAMTMP=yes' >> /etc/default/rcS"
    sudo mv /etc/fstab /etc/fstab.orig
    sudo sh -c "echo 'tmpfs           /tmp            tmpfs   nodev,nosuid,size=30M,mode=1777       0    0' >> /etc/fstab"
    sudo sh -c "echo 'tmpfs           /var/log        tmpfs   nodev,nosuid,size=30M,mode=1777       0    0' >> /etc/fstab"
    sudo sh -c "echo 'proc            /proc           proc    defaults                              0    0' >> /etc/fstab"
    sudo sh -c "echo '/dev/mmcblk0p1  /boot           vfat    defaults,ro,errors=remount-ro         0    2' >> /etc/fstab"
    sudo sh -c "echo '/dev/mmcblk0p2  /               ext4    defaults,ro,noatime,errors=remount-ro 0    1' >> /etc/fstab"
    sudo sh -c "echo ' ' >> /tmp/fstab"
    sudo mv /etc/mtab /etc/mtab.orig
    sudo ln -s /proc/self/mounts /etc/mtab
    sudo shutdown -r now
    
    
    
    sudo mount -o remount,ro /dev/mmcblk0p2  /
    
    sudo mount -o remount,rw /dev/mmcblk0p2  /

    

    
