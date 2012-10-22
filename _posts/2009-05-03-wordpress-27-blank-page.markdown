--- 
layout: post
title: Wordpress 2.7 blank page
wordpress_id: 116
wordpress_url: http://www.musterdenker.de/?p=116
date: 2009-05-03 03:44:09 +02:00
---
We updated this blog several weeks ago, but suddenly the nothing was working. The whole frontend of this blog was blank, only admin was still working. Playing around with php installation, checking different templates and updating all plugins I tried everything without any success. Finally I deactivated all plugins and ..... the blog waws working again. So I hunted down the "black sheep" and it was:

cforms V 10.5

For now I removed this plugin, maybe I'll later investigate a bit more what happend ...

If you also have a blank screen but removing cforms does not help try these useful links:

http://wordpress.org/support/topic/225819/page/1
http://www.blogsdna.com/1669/fix-wordpress-27-upgrade-white-blank-page-issue-updatephp.htm
http://nslog.com/2008/12/13/wordpress_27_bug_blank_home_page_high_number_of_posts
