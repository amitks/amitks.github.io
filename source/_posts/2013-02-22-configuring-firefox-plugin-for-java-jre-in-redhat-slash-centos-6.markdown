---
layout: post
title: "Configuring java jre plugin for Firefox in Redhat/Centos 6"
date: 2013-02-22 15:05
comments: true
categories: 
---
Download the latest Linux RPM (self-extracting file), currently jre-7u15-linux-i586.rpm, from [java.com](java.com) then as root install and configure the alternatives system and plugins:

```sh
rpm -Uvh jre-7u15-linux-i586.rpm
alternatives --config java
```
There are 2 programs which provide 'java'.
```sh "alternatives --config java" output
  Selection    Command

*+ 1           /usr/lib/jvm/jre-1.6.0-openjdk/bin/java     
   2           /usr/lib/jvm/jre-1.5.0-gcj/bin/java
```   
Enter to keep the current selection[+], or type selection number:

Note use number of versions, N, For example, if 2 versions were installed then:
```sh
alternatives --install /usr/bin/java java /usr/java/latest/bin/java 3
alternatives --config java
```
There are 3 programs which provide 'java'.
```sh "alternatives --config java" output
  Selection    Command
  
*+ 1           /usr/lib/jvm/jre-1.6.0-openjdk/bin/java  
   2           /usr/lib/jvm/jre-1.5.0-gcj/bin/java
   3           /usr/java/latest/bin/java
```
Enter to keep the current selection[+], or type selection number: 3
```sh
java -version
```
java version "1.7.0_15"
Java(TM) SE Runtime Environment (build 1.7.0_15-b03)
Java HotSpot(TM) Server VM (build 23.7-b01, mixed mode)

Create links in the Mozilla Plugins directory so Java jre will show in firefox plugin option.
```sh
cd /usr/lib/mozilla/plugins/
ln -fs /usr/java/latest/lib/i386/libnpjp2.so
```
Now Restart your browser and then click on Enable button to enable this plugin.Thats it you are all set.
