--- 
layout: post
title: could not find rubygem echoe
wordpress_id: 22
wordpress_url: http://www.musterdenker.de/?p=22
date: 2009-01-16 21:36:11 +01:00
---
After updating all my gem(1.3.1) and rails(2.2.2) to current version my capistrano(2.5.3) stopped working with the error:
<blockquote>/Library/Ruby/Site/1.8/rubygems.rb:636:in `report_activate_error': Could not find RubyGem echoe (&gt;= 0) (Gem::LoadError)</blockquote>
After some seconds of confusion I installed the gem ("gem install echoe") and everything was fine again. Unlike others my application was still running, but only capistrano had problems. So what is echoe ? Its a fork of hoe, so when gem now uses echoe I should be able to remove hoe.... So I did it and it seems to work :)
