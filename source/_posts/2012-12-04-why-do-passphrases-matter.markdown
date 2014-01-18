---
layout: post
title: "Why do Passphrases matter"
date: 2012-12-04 08:11
comments: true
categories: 
---
Passwords aren't very secure,we already know this. If you use one that's easy to remember, it's easier to guess or brute-force (try many options until one works). If you use one that's random it's hard to remember, and thus you're more inclined to write the password down. Both of these are Very Bad Things. This is why we're using ssh keys.

But using a key without a passphrase is basically the same as writing down that random password in a file on your computer. Anyone who gains access to your drive has gained access to every system you use that key with. This is also a Very Bad Thing. The solution is obvious: add a passphrase.

But We don't want to enter a long passphrase every time We use the key!

Thankfully, there's a nifty little tool called ssh-agent that can save your passphrase securely so you don't have to re-enter it. Most linux installations will automatically start ssh-agent for you when you log in.
