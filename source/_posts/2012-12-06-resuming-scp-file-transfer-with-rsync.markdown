---
layout: post
title: "resuming scp file transfer with rsync"
date: 2012-12-06 00:58
comments: true
categories: 
---
I always loved using scp tool for file transfer over internet.but faced some draw back of using it while internet connection get disconnected and file download terminated.now problem is unable to resume from current position.so googled it and found a way out.
```sh
rsync -e ssh --partial user@remote-ip:/file-directory /home/myself/Downloads
```
Download will be resumed from that point where it was terminated by any reason.`-e ssh` indicates rsync to use ssh and `--partial` indicates for partial downloaded files.one more cool feature is that you can see the progress while file is being downloaded.it will show current download rate as well as progress of the file downloaded.For that use prefix `--progress`.
```sh
rsync -e ssh --partial --progress user@remote-ip:/filedirectory /home/myself/download
```
if working with a directory use "-r".
example:
```sh dealing with file
rsync -e ssh --partial --progress emacs@63.90.228.44:/home/emacs/goole_appengine.zip /home/redhat/Downloads
```
```sh dealing with directory
rsync -e ssh --partial --progress -r emacs@63.90.228.44:/home/emacs/goole_appengine /home/redhat/Downloads
```
