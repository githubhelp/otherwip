#### Set-up a Raspbian hard drive image for Raspberry Pi using SD card.

{% include link/rasp-img.md %}

The quick and easy method is to put the image on **BOTH** the SD card and the HDD, boot up the RaspberryPi on the SD card and from there, connect and prepare the HDD for the RaspberryPi to boot to.

Since the HDD image is a duplicate, the partition's uuid should be changed so that it is unique, at the same time the partitions label can be set. The harddisk's filesystem must then be mounted in order to access it, so create a directory  called hdd in the existing media directory and then mount the new hdd image to that directory.

    sudo tune2fs -U random -L hdd  /dev/sda2
    sudo mkdir /media/hdd
    sudo mount /dev/sda2 /media/hdd
    sudo nano /media/hdd/etc/fstab

This last line opens the hdd's fstab for editing, change the default root location from " **/dev/mmcblk0p2** " to " **/dev/sda2** " then save and exit using `ctrl-X` -> `Y` -> `enter`,

