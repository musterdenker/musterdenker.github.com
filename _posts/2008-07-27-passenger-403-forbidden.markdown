--- 
layout: post
title: Passenger - 403 Forbidden
wordpress_id: 12
wordpress_url: http://www.musterdenker.de/?p=12
date: 2008-07-27 13:08:15 +02:00
---
Running Passenger on an apache machine to deploy a RoR application I suddenly encountered a default
<blockquote>403 Forbidden - You don't have permission to access / on this server.</blockquote>
page generated from apache, although it was working before and I didn't made a single change to my apache server. No real help from the log files:
<blockquote>Directory index forbidden by rule: XYZ</blockquote>
After some time of searching and banging my head against the wall I realized what I did wrong:
I'm using capistrano for "easy" deployment and I added a symlink linking always to the same server "environment.rb". Of course I had a misstyping there and the symlink and thus the environment.rb was empty. So check your environment.rb file if you get such a 403 page, it may be empty....
