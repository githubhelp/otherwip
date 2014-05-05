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

To add the distro and repository url to the sources list use this line replacing <DISTRO> with the distro required.

    sudo sh -c "echo 'deb http://archive.emonhub.org <DISTRO> unstable' >> /etc/apt/sources.list"

##### Raspbian wheezy

    wheezy

##### Ubuntu quantal

    quantal


    
