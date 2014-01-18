---
layout: post
title: "sound problem in DELL vostro 1088"
date: 2012-11-23 15:32
comments: true
categories: 
---

I own a DELL-vostro-1088 Laptop.i have switched over linux in year 2009,every thing was ok with the installation of drivers except for one.Laptop's audio jack was not working so no fun with any headfones or external Sound-Box.That time current version of alsa was 1.0.21 or 1.0.22  something like that.i tried upgrading with alsa 1.0.25 still no luck at all with sound output.
Googled a lot then i got some where close.i created a alsa.conf file inside `/etc/modprobe.d/` directory.then i did this:
```sh
echo "options snd-hda-intel model=dell-vostro position_fix=0 enable=yes" > /etc/modprobe.d/alsa.conf
```
it took some time because i was trying with `model=dell-vostro-1088` while above line was sufficient.anyway i rebooted the machine and was really surprised to see that my audio jack was working.Now i am enjoying my Creative Sound-Box.
Right now Fedora, ubuntu and some other distro has upgraded the version of alsa so no problem with audio drivers.
but Redhat-6/Centos-6 are still using alsa-1.0.21 so, i need to do above modifications in order to stay pain free.

