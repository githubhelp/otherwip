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



If you want/need to expand the partition on the hdd see Br1an's notes here http://openenergymonitor.org/emon/node/3889. 


