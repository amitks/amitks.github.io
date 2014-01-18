---
layout: post
title: "A Demo facebook app for extracting user details"
date: 2013-02-04 12:26
comments: true
categories: 
---
I have been thinking of extracting user details of a facebook profile(if we have user's permission) and found this php script.you can create a facebook demo app to see the result.you 'll need to dump this script as `index.php` along with `facebook.php` and `base_facebook.php` to your hosting server.these files are available at [github.com/facebook/php-sdk](https://github.com/facebook/php-sdk).

currently i am hosting my app at [heroku.com](https://heroku.com) you can also consider this for your need.heroku's service is cool and most of them are free.

Now you will need to register a facebook app at [developers.facebook.com](https://developers.facebook.com).you will get a unique 'appId' and 'Secret'. put the exact values in the index.php and now your heroku app address(something like myapp.herokuapp.com once you have created it) while registering for the app at developers.facebook.com.

My Demo App is available at [Demo App](https://facebook-demo.herokuapp.com)
below is the code for index.php. have Fun while creating your first Facebook App :) 
{% include_code user-details.php lang:php %}
