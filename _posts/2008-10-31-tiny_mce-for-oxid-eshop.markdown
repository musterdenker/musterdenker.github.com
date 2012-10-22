--- 
layout: post
title: tiny_mce for OXID eShop
wordpress_id: 16
wordpress_url: http://www.musterdenker.de/?p=16
date: 2008-10-31 17:45:10 +01:00
---
Using the new open source CE version of <a href="http://www.oxid-esales.com">OXID</a> eShop I realised that there is no nice WYSIWYG shipped with it. So I had a look into code and wrote a simple module that makes the admin area use<a href="http://tinymce.moxiecode.com/"> tiny_mce.</a>

Of course this module is GPL and not yet finished :)

Known restrictions:
- by now only article long text, category long text and CMS use tiny_mce
- not all features of tiny_mce tested
- tiny_mce is not able to deal with smarty tags afaik ...

So please feel free to extend, enhance and modify it ...

V0.1 <a href="http://www.musterdenker.de/wp-content/uploads/2008/10/tiny_mce_for_eshop.zip">download</a>

EDIT:
So first bug has been found: IE 7 ( and others) didn't work, so here version 0.1.1(<a href="http://www.musterdenker.de/wp-content/uploads/2008/11/tiny_mce_for_eshop-v0_1_11.zip">iny_mce_for_eshop-v0_1_11</a>)  with IE7 fix
The reason and the solution I found <a href="http://tinymce.moxiecode.com/punbb/viewtopic.php?id=12940">here</a>

UPDATE: download <a href="http://www.musterdenker.de/wp-content/uploads/2008/10/oxid_tiny_mce.zip">oxid_tiny_mce V0.2</a> Version 0.2

UPDATE: neue Version für Shop &gt; 4.1.5 gibts <a href="http://www.musterdenker.de/wp-content/uploads/2008/10/oxid_tiny_mce_03.zip">hier</a>.
