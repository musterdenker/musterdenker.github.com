--- 
layout: post
title: Update OXID eShop from PE 3.X to PE 4.1.5 SQL issues
wordpress_id: 176
wordpress_url: http://www.musterdenker.de/?p=176
date: 2009-09-13 19:27:00 +02:00
---
I recently did an update from an old <a href="http://www.oxid-esales.com" target="_blank">OXID eShop Version</a> PE 3.0.4 to the newest Version of PE 4.1.5.

Although most of the things went well I ran into several problems. Sharing the solutions here might help you and will for sure help me for the next update :)

<strong>1. no cumulative updates:</strong> As there are no cumulative updates you are forced to do each update step separately from Version 4.0.0.0 to 4.1.5. As there is only an updatescript from 3.0.4. to 4.0.0.0 you are forced to do all 9! updates afterwards. OXID promised that there will be cumulative updates in the future so you'll be able to say "give me a patch from 4.0.0.0 to 4.1.X and you'll get a single file. But as we are not living in the future (yet) here is a simple list of 9 SQL scripts you have to execute to come from freshly updated 4.0.0.0 to version 4.1.5. Be aware that there are also 2 PHP files you have to copy to doc root and execute after the according SQL has been executed.
<a href="http://www.musterdenker.de/wp-content/uploads/2009/09/sql.zip">Download all OXID update SQLs at once.</a>

<strong>2. OXACTIVE &gt; 1 in oxarticles table:</strong> The oxactive field in oxarticle table is responsible to activate/deactivate an article. Allowed values are 0 and 1. But after update it may happen that you have a lot of "2"s as values, leading to "half active" articles. I can tell you, thats quite confusing ;). <a href="https://bugs.oxid-esales.com/view.php?id=938" target="_blank">Here is the accorind note by OXID</a> and with the following SQL you can fix it:

<address>UPDATE oxarticles SET oxactive = 0 WHERE oxactive &gt; 1</address><strong>3. Old orders have sum of 0 and all articles of an old order have thr price of 0</strong>. Nearly all entries in the order overview in admin might become "0" after an update. The reasons are new fields in oxorder and oxorderarticles tables. These fields might not be filled. Thats why you'll need the following SQL:

<address>update oxorderarticles set oxbprice = oxprice where oxbprice = 0 and oxprice &lt;&gt; 0

update oxorderarticles set oxnprice = ((oxprice*100) / (100 + oxvat)) where oxnprice = 0 and oxprice &lt;&gt; 0

UPDATE `oxorder` AS _main SET _main.oxtotalordersum = _main.oxdelcost + _main.oxpaycost + _main.oxwrapcost - _main.oxdiscount + ( SELECT SUM( oxbrutprice ) FROM `oxorderarticles` WHERE oxorderid = _main.oxid ), _main.oxtotalbrutsum = ( SELECT SUM( oxbrutprice ) FROM `oxorderarticles` WHERE oxorderid = _main.oxid ), _main.oxtotalnetsum = ( SELECT SUM( oxnetprice ) FROM `oxorderarticles` WHERE oxorderid = _main.oxid ) WHERE _main.oxtotalnetsum = 0 AND _main.oxtotalbrutsum = 0 AND _main.oxtotalordersum = 0;

</address><a href="https://bugs.oxid-esales.com/view.php?id=691" target="_blank">An according note by OXID about the third of these SQLs</a>. The first two I build myself.

Of course all the files and SQLs are without ANY warranty and you use them at your own risk! Don't forget a backup before you do anything!

Please leave feedback :)
