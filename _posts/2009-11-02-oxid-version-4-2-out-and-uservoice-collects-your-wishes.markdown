--- 
layout: post
title: OXID Version 4.2 out and uservoice collects your wishes
wordpress_id: 191
wordpress_url: http://www.musterdenker.de/?p=191
date: 2009-11-02 23:14:34 +01:00
---
Usually I'm not in blogging about a software release, especially if it's not a major release. But this time I'll make an exception.

On 29th of October OXID eSales released the <a href="http://www.oxid-esales.com/de/news/blog/new-major-version-420-oxid-eshop-released" target="_blank">version 4.2 of OXID eShop</a> and as readers of my blog know I'm working a lot with this shop software. Also I was never overpraising the shop, although it's a good piece of software there are still some quite ugly parts in it.

That's why I was surprised twice by the current update:
- First it only contains things I was missing a lot (usually when there are updates of any piece of software there is always some uninteresting new stuff ...)
- Second the way the new things are done is in a nice and even <a href="http://en.wikipedia.org/wiki/Don%27t_repeat_yourself" target="_blank">DRY </a>way

Let me give you an example:
- Adding new languages automatically just feels so much better then having to edit the database yourself :)
- The template overriding system is so neat :) But why can't I choose the template dir from admin? (a config file entry is necessary)
- The new "Help Popups" in admin you can add with just one call:  [{ oxinputhelp ident="HELP_SHOP_MAIN_PRODUCTIVE" }]

Finally the multidimensional variants: YEAH! The way it was implemented is really clean and performant! One small downside: The handling in admin could have been better (it's really not comfortable) . But there are more versions to come and if the quality of further releases will be like the 4.2.  I'm looking forward ....

Ahhh, one more thing: Oxid set up a "uservoice" where you can vote for new features. Have a look <a href="http://oxid.uservoice.com/" target="_blank">here </a>and don't forget to vote for <a href="http://oxid.uservoice.com/pages/31940-feature-requests/suggestions/372353-shorter-method-names-in-templates" target="_blank">my latest wish</a>.
