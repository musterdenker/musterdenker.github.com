--- 
layout: post
title: OXID eShop - enable lazy loading for categories
wordpress_id: 169
wordpress_url: http://www.musterdenker.de/?p=169
date: 2009-09-04 13:28:34 +02:00
---
The OXID eShop has a really cool<a href="http://en.wikipedia.org/wiki/Lazy_loading" target="_blank"> lazy loading mechanism</a> implemented in oxBase class. Its mainly used to save memory and avoid overloaded objects. Usually this is not needed for "small" classes like e.g. oxvendor oxcategory. Thats why it is deactivated per default in oxBase class:

$_blUseLazyLoading = false;

But sometimes it makes sense to activate lazy loading. One example are the categories. When a category list (oxCategoryList) is loaded somewhere in the shop only a selection of data fields are loaded into the single oxcategorxy object. This can cause some porblems if u want to access own fields or e.g. the oxthumb of the category within a category list.

In practice I wanted to show the thumb picture in a category list but I could not access the field, cause it was not loaded per default.

One solution would be to extend the field list in the "_getSelectString" method of oxcategory list. But a much simplier and more elegant solution is to activate lazy loading for the categories. Thereby it will be possible to access all fields of oxcategory!

There is s slight disadvantage of this solution: Every (first) access to a not loaded field of each object will fire a SQL query. Accessing a huge amount of not loaded fields on a long category list could thereby kill the performance of your shop ...

I attached a small module activating lazy loading. Just put the file to your modules folder and add a line in admin module entries like this:
"oxcategory =&gt; mude_lazyloading" for each class you want to activate lazy loading.

<a href="http://www.musterdenker.de/wp-content/uploads/2009/09/mude_lazyloading.php_V0_2.zip">Download here</a>

Have fun and pleas give me feedback ...

EDIT: It's always the same, on first version there is always a bug ;) The first version only works without caching. The new Version 0.2  has one more line:

"self::$_blDisableFieldCaching[get_class($this)] = true;" to disable field caching for our class in order to make lazy loading work also with caching.
