--- 
layout: post
title: OXID eShop module for developers
wordpress_id: 111
wordpress_url: http://www.musterdenker.de/?p=111
date: 2009-04-23 18:07:39 +02:00
---
I just wrote a small module for OXID eShop that automatically deletes the "tmp/" folder at the beginning of each call. The module does nothing when shop is in productive mode.

Background: The OXID eShop does its smarty and its object caching in the folder "tmp/". Even when productive mode ist off some caching mechanism still work which sometimes causes funny behaviour during development: "Why can't I see a change, I just changed the whole function/database/template ..." In the past you had to delete all files from"tmp/" manually, now you have this small module doing the work :)

Of course this module is open Source (GPL V3) and can be downloaded directly here(<a href="http://www.musterdenker.de/wp-content/uploads/2009/04/mude_dev.zip">mude_dev</a>) or you can have a look at<a href="http://www.oxid-esales.com/en/exchange/extensions/delete-tmp/version/delete-tmp" target="_blank"> OXID exchange </a>and don't forget to vote for us ;)
