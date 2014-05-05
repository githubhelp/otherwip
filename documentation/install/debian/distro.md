---
title: Debian Packages
tags: 
categories: 
published: True
layout: default
js: index
---

### Currently the following distro's are supported

The correct "distro" must be specified in the sources list to ensure the correct package is installed by the debian installer.

##### Raspbian wheezy

    wheezy

##### Ubuntu quantal

    quantal
    
------------------------------------------------------------
    

These details only need to be added one time and can be checked by opening the sources list with an editor

    sudo nano /etc/apt/sources.list
    
There needs to be a line that specifies the distro and repository url, it should look like this line but with <DISTRO> replaced with the distro name

    deb http://archive.emonhub.org <DISTRO> unstable


    
