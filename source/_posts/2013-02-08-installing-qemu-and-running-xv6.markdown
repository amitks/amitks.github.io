---
layout: post
title: "installing qemu and running xv6 on Centos/Redhat 6"
date: 2013-02-08 23:14
comments: true
categories: 
---
##QEMU Emulator
QEMU is a generic and open source machine emulator and virtualizer.

When used as a machine emulator, QEMU can run OSes and programs made for one machine (e.g. an ARM board) on a different machine (e.g. your own PC). By using dynamic translation, it achieves very good performance.

When used as a virtualizer, QEMU achieves near native performances by executing the guest code directly on the host CPU. QEMU supports virtualization when executing under the Xen hypervisor or using the KVM kernel module in Linux. When using KVM, QEMU can virtualize x86, server and embedded PowerPC, and S390 guests. 

##xv6
xv6 is a re-implementation of Dennis Ritchie's and Ken Thompson's Unix
Version 6 (v6).  xv6 loosely follows the structure and style of v6,
but is implemented for a modern x86-based multiprocessor using ANSI C.

##Installing QEMU
get the current version of QEMU at [http://wiki.qemu.org/Download](http://wiki.qemu.org/Download) or clone the git repository `git clone git://git.qemu-project.org/qemu.git`.if downloaded the tarball archieve then untar it.either way you have qemu on your system.Now before further proceeding we should check the requirements for installing QEMU.make sure these packages are installed if not you can't proceed for the installation.

- SDL (This comes with installation DVD if not u may google it)
- SDL-devel (This too comes with installation DVD)
- [glib](http://hammurabi.acc.umu.se/pub/gnome/sources/glib/2.12/glib-2.12.12.tar.bz2)
- [pkg-config](http://pkgconfig.freedesktop.org/releases/pkg-config-0.22.tar.gz)

```sh installation steps for QEMU
cd qemu
./configure
make
make install
```
##Running xv6
Fetch xv6 source.The latest xv6 source is available via `git clone git://pdos.csail.mit.edu/xv6/xv6.git`.
```sh check the path for qemu executables
which qemu-system-i386
```
Change the line containing `#QEMU` in xv6/Makefile to: `QEMU=/usr/local/bin/qemu-system-i386` (or ensure that qemu is in your path).
Go to the xv6 directory. Run following command to run xv6 inside Qemu.
```sh Running xv6
cd xv6
make qemu
```
That's it now enjoy xv6 inside QEMU emulator and learn the core of unix operating system.

