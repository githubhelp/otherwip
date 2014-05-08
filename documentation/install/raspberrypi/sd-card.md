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


Start by updating the downloaded Raspbian image
    
    sudo apt-get update
    sudo apt-get -y upgrade
    
Then run these commands to make changes to filesystem  
    
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
    
The Pi will now run in Read-Only mode from the next restart.

Before restarting create two shortcut commands to switch between read-only and write access modes.

Firstly " rpi-rw " will be the command to unlock the filesystem for editing, run

    sudo nano /usr/bin/rpi-rw
    
and add the following to the blank file that opens

    #!/bin/sh
    sudo mount -o remount,rw /dev/mmcblk0p1  /
    sudo mount -o remount,rw /dev/mmcblk0p2  /
    echo "Filesystem is unlocked - Write access"
    echo "type ' rpi-ro ' to lock"
    
save and exit using `ctrl-x` -> `y` -> `enter` and then to make this executable run

    sudo chmod +x  /usr/bin/rpi-rw

Next " rpi-ro " will be the command to lock the filesytem down again, run

    sudo nano /usr/bin/rpi-ro
    
and add the following to the blank file that opens

    #!/bin/sh
    sudo mount -o remount,ro /dev/mmcblk0p1  /
    sudo mount -o remount,ro /dev/mmcblk0p2  /
    echo "Filesystem is locked - Read Only access"
    echo "type ' rpi-rw ' to unlock"
    
save and exit using `ctrl-x` -> `y` -> `enter` and then to make this executable run

    sudo chmod +x  /usr/bin/rpi-ro
    
Lastly reboot for changes to take effect (*note - if  {% include link/int/rpi-uart %} access required make these changes before restarting*)

    sudo shutdown -r now
    
####***Remember to use " rpi-rw " before making any changes and then to use " rpi-ro " afterwards to lock the filesystem down again.***

To undo these changes and revert to the original set up run
    
    sudo mount -o remount,rw /dev/mmcblk0p2  /
    sudo mv /etc/default/rcS.orig /etc/default/rcS
    sudo mv /etc/fstab.orig /etc/fstab
    sudo mv /etc/mtab.orig /etc/mtab
    sudo rm /usr/bin/rpi-ro
    sudo rm /usr/bin/rpi-rw
    sudo shutdown -r now
    
    
    
    
