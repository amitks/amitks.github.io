---
layout: post
title: "packing an rpm without source code"
date: 2013-01-18 10:33
comments: true
categories: 
---
Here we are creating an demo rpm for heroku-client.
To build an RPM, you must:

- Set up a directory hierarchy per the rpmbuild specifications.
- Place your source code and or supplemental files in the proper locations in the hierarchy.
- Create your spec file.
- Build the RPM.

You can optionally build a source RPM to share your source code with others.
To begin, build the hierarchy. In a directory in your home directory—say,
$HOME/rpmbuild.now create six subdirectories:
```sh
$mkdir -p /home/amit/rpmbuild/BUILD BUILDROOT RPMS SOURCES SPECS SRPMS
```
now create a directory `heroku-client-1.0-el6.i386` inside BUILDROOT.
This directroy name should follow this format %{name}-%{version}-%{release}.{archiecture}
Now copy your scripts or files what ever your want to put inside the rpm like this:
/home/amit/rpmbuild/BUILDROOT/heroku-client-1.6-el6.i386/usr/local/heroku-client/
it means all the files and directory in side heroku directory will be added to the rpm.when you will install this rpm your installing location will be /usr/local/heroku-client/.
if you want the installed location inside /bin then directory structure will be look like this:
/home/amit/rpmbuild/BUILDROOT/heroku-client-1.6-el6.i386/bin/heroku-client/


Next, create the spec file. A spec file is nothing more than a text file with a special syntax.below is a sample spec file.
{% include_code heroku-client.spec lang:cpp %}

Now let's walk through spec file.
The %prep, %build, and %install sections are next, consecutively. Each section
generates a shell script that is embedded into the RPM and run subsequently as part
of the installation. %prep readies the source code, such as unpacking the tarball.
Here, %setup -q is a %prep macro to automatically unpack the tarball named in
Source.
The instructions in the %build section should look familiar. They are identical to the
steps you used to configure and launch the build manually. The %install section
is identical, too. However, while the target of the manual build was the actual
/usr/local directory of your system, the target of the %install instruction is
~/rpmbuild/BUILDROOT.
%files lists the files that should be bundled into the RPM and optionally sets
permissions and other information. Within %files, you can use the %defattr
macro to define the default permissions, owner, and group of files in the RPM; in this
example, %defattr(-,root,root) installs all the files owned by root, using
whatever permissions found when RPM bundled them up from the build system.
You can include multiple files per line in %files.
%post is a hook which will executes the codes after the installation of rpm.

We are not including few section of spec file because we are not building an rpm from source tar ball file.see the spec file.


now run below command as a non root user(avoid root preferably)

```sh
$rpmbuild -v -ba SPECS/heroku-client.spec
```

-ba is for build all.Now your binary as well as source rpms are created inside RPMS and SOURCES directory.if only want to build binary then use -bb instead.

source:  [http://www.ibm.com/developerworks/library/l-rpm1/](http://www.ibm.com/developerworks/library/l-rpm1/)
