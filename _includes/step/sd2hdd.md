#### Set-up a Raspbian hard drive image for Raspberry Pi using SD card.

{% include link/ext/rasp-img.md %}

The quick and easy method is to put the image on **BOTH** the SD card and the HDD, boot up the Pi on the SD card and from there, connect and prepare the HDD to boot to.

Since the HDD image is a duplicate, the partition's uuid should be changed so that it is unique, at the same time the partitions label can be set. The harddisk's filesystem must then be mounted in order to access it, so create a directory  called hdd in the existing media directory and then mount the new hdd image to that directory.

    sudo tune2fs -U random -L hdd  /dev/sda2
    sudo mkdir /media/hdd
    sudo mount /dev/sda2 /media/hdd
    sudo nano /media/hdd/etc/fstab

This last line opens the hdd's fstab for editing, change the default root location from " **/dev/mmcblk0p2** " to " **/dev/sda2** " then save and exit using `ctrl-X` -> `Y` -> `enter`,

Next edit the cmdline.txt to point to the HDD at boot time.

    sudo sh -c 'echo "dwc_otg.lpm_enable=0 console=tty1 root=/dev/sda2 rootfstype=ext4 elevator=deadline rootwait" > /boot/cmdline.txt'

*note - this command also removes text from cmdline.txt that effects the {% include link/int/rpi-uart %}, check before re-starting Pi*    
    
    sudo shutdown -r now

The Pi should now boot up to the HDD, now is a good time to perform an update and upgrade the Raspbian image.

    sudo apt-get update
    sudo apt-get upgrade -y

The Pi and it's harddrive are now fully usable, although the downloaded Raspbian image's root partition is quite small and therefore the resulting partition on the HDD will possibly require re-sizing.

    ADD LINK ?


