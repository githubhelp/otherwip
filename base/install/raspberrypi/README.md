while we are here just edit the inittab (this step is only required if you're intending to use rfm2pi or serial port)

sudo nano /media/hdd/etc/inittab

edit the very last line by adding a hash so it reads " # T0:23:respawn:/sbin/getty -L ttyAMA0 115200 vt100 "




edit the cmdline.txt and reboot (the next 2 lines are 1 line wrapped, be sure it is entered as 1 line "sudo" to "txt'")

sudo sh -c 'echo "dwc_otg.lpm_enable=0 console=tty1 root=/dev/sda2 rootfstype=ext4 elevator=deadline rootwait" > /boot/cmdline.txt'

sudo shutdown -r now

should now boot up to the hdd so add the repo to sources list, update and install (next 2 lines as one line again)

sudo sh -c "echo 'deb http://emon-repo.s3.amazonaws.com wheezy unstable' >> /etc/apt/sources.list"

sudo apt-get update

sudo apt-get -y --force-yes install emoncms emoncms-module-event emoncms-module-rfm12pi

(if you do not need or want the event module or rfm2pi module delete them from that last line to suit)

you will get asked a series of questions about mysql and emoncms passwords

The first 2 questions are to set the root password for the mySQL database root user, it's most important you set this password correctly, The rest are questions about setting up the emoncms database and email. You can accept all the default values except the second emoncms question (4th overall) this password gives emoncms access to mySQL so It should be set to the MySQL root password you just entered for questions 1 & 2. If you make a mistake with the emoncms settings it's not a problem as you can go through the questions again by using sudo dpkg-reconfigure emoncms --force.

Once these settings are entered the databases and server will be created, this will take a while, once there done run 

sudo a2ensite emoncms

sudo a2enmod rewrite

sudo /etc/init.d/apache2 restart

and if you have an rfm2pi installed also run

sudo service rfm12piphp start

go to http;//IP.ADD.OF.PI/emoncms and register a user and with any luck you're in.

 

In future when you use sudo apt-get update && sudo apt-get upgrade emoncms will get updated along with everything else.and as more modules become available in apt packaging you can install them with apt-get install as well but there maybe other steps also and that will be documented with each module.

The second partition of your sdcard still holds a redundant copy of raspbian, you could copy just the boot partition to a smaller sdcard if you wanted to free up this sdcard or if not just leave it there and if ever you have an issue with your "hdd" version you can whip out the sdcard edit the /boot/cmdline.txt file on windows by changing "/dev/sda2" to "/sda/mmcblk0p2" and pop it back it the pi to boot into the sdcard image and explore / fix your hdd image.

There are tidier methods to do this but this is by far the easiest way without another linux machine.

Also as you mentioned xstart I thought I would mention that I also like to use windows remote desktop to raspberrypi's xrdp so I can have a remote "xstart" screen open on my windows PC. but I could never get it to work with any emonCMS image until I used this method. It is now fully functional.

If you want/need to expand the partition on the hdd see Br1an's notes here http://openenergymonitor.org/emon/node/3889. 


