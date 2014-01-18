---
layout: post
title: "changing theme for octopress"
date: 2013-01-26 23:46
comments: true
categories: 
---
**oo..yeah! it's an octopress theme.**

I did a lot of customization for octopress default theme any way i wasn't satisfied with the look.so thought of changing the default theme and i came to know about this one.it's a cool theme designed for octopress/jekyll blogging.

installation steps:
```sh
cd octopress
git clone https://github.com/wallace/justin-kelly-theme.git .themes/jk
rake install['jk']
rake generate
rake deploy
``` 
That's it your New Theme is installed.But your existing customization will be deleted.if you want to add something in navigation menu try editing the file `_include/custom/navigation.html`.
 
