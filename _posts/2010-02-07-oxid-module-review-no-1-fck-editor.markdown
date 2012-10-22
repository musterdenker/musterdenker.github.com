--- 
layout: post
title: "OXID Module Review - No.1: fck editor"
wordpress_id: 193
wordpress_url: http://www.musterdenker.de/?p=193
date: 2010-02-07 18:48:50 +01:00
---
Together with the last year release of the OXID eShop open source (GPL V3) version, the<a href="http://www.oxid-esales.com/de/exchange" target="_blank"> OXID eXchange</a> open its doors to the public. The OXID eXchange is similar to the Apple App Store or the Magento connect a central place where developers can put their applications or in terms of OXID eShop extensions (modules, language packs and themes) in order to distribute and sell them. In the eXchange we find a description by the creator of the extension as well as reviews written by customers. But as most of the reviews are more like comments and tend to be quite short it may be hard to determine the quality of the extensions. That's why we'll start a series of objective reviews in order to help people in the jungle of OXID extensions. For the start we'll mainly cover open source extensions but we plan to cover paid extensions as well.

Number one in our series will be the "fck editor" (<a href="http://www.oxid-esales.com/en/exchange/extensions/fckeditor-lauffaehig-mit-oxid-eepece" target="_self">link to eXchange</a>) extension by <a title="Top Concepts" href="http://www.topconcepts.de" target="_blank">top concepts</a> a german OXID partner located in Hambug.

All testing take place with the newest version of the OXID eShop CE (4.2) in UTF-8 mode, installed on my local Mac OSX 10.5.7 with an old PHP 5.2.5.

Description:
This extension adds the open source fck editor, which is today known as the <a href="http://ckeditor.com/" target="_blank">CKEditor</a>, as default WYSIWYG editor in the eShop. Remark: The OXID eShop CE ships without an WYSIWYG editor so you'll need to install this or the TinyMCE editor in order to use full WYSIWYG features.

Documentation:
There is a small install.txt file in english and german. All you need to know about installing can be found there, but don't expect any additional information. A new user might have a problem with the term "add the following lines to the 'Modules' section". It would be better to describe where to find the text box in admin area (Master Settings -&gt; Core Settings -&gt; System -&gt; Modules), especially as WYSIWYG usually is the first think installed when someone tries the eShop for the first time.

Installation:
Following the instructions it takes me 20 seconds and FCK Editor is installed an working. No problems at all.

Good:
<ul>
	<li>Easy and fast installation and applies to all OXID eShop text boxes that are capable of html text.</li>
	<li>The FCK Editor is a very good editor including adding / uploading of pictures.</li>
</ul>
Bad:
<ul>
	<li>The FCK Editor interface switches language according to the text language and not based on the admin interface language. So if an english admin edits the german translation of an article the FCK editor's interface is in german too.</li>
	<li>Maximizing the editor can't be used as the OXID "save" button disappears, although this is mostly a problem of the admin templates.</li>
</ul>
Conclusion:
Use it! You might also think about replacing the build in editor of PE and EE versions by the FCK editor if you like it more.

Please feel free to comment or recomment other extensions...
