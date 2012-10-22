--- 
layout: post
title: Pitfalls with postfix smpt and db auth
wordpress_id: 13
wordpress_url: http://www.musterdenker.de/?p=13
date: 2008-08-13 15:26:05 +02:00
---
Now its running! a postfix with courier and sasl on my ubunto server having virtual users stored in a mysql. Regarding the tutorials you can find (e.g. this is a good <a href="http://www.howtoforge.de/howto/virtuelle-benutzer-und-domains-mit-postfix-courier-und-mysql-ubuntu-610-edgy-eft/">one in german</a>) it doesn't seem to be complicated, but just a lot of work. But I had two BIG problems during configuration. Happily I managed to solve them both:

1. After setting up everything I got the error: "pam_mysql - required option "db" is not set"  when trying to send mails. This was very strange as this parameter is not needed and was also not mentioned in any tutorial. After longer research using my big friend (brother?!) google, I realized that my mysql user had a password that contained a "#" which is a illigeal character! Nice error message I have to say :( Somehow the "#" is a character that stops the evaluation of password string. I don't know if other special chars are also a problem, my password it now only "normal" charecters.

2. My users all had a username like user@domain unfortunately courier does NOT support that type of username. Whenever I tried smpt from my mail client he cut of the "@domain" part and looked up the "user" in my db. One possibility would have been to switch to dovecot which "seems" to support this type of names (<a href="http://www.howtoforge.com/forums/showthread.php?t=12308">howto</a>), but I didn't want to. Also changin all my users for some different login name was not a solution as I allready had the whole structure of my mail dir like "/domain/user". So I decided to map the "@" in my usernames to a "#". Now my user names are like user#domain and still all the mapping to the folders "domain/user" is done. All I had to do was changing

"authmysqlrc" (for outgoing) :
<blockquote>MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'#',-1),'/',SUBSTRING_INDEX(email,'#',1),'/')</blockquote>
and "mysql-virtual-mailboxes.cf (which contains the mapping on my machine) (for incoming)
<blockquote>query = SELECT CONCAT(SUBSTRING_INDEX(email,'#',-1),'/',SUBSTRING_INDEX(email,'#',1),'/') FROM users WHERE email=REPLACE('%s','@','#')</blockquote>
Now it works ... if all I did was bullshit and could have been done in a nicer way, please leave a comment.
