--- 
layout: post
title: Accordion Content script - ddaccordion / collapse all
wordpress_id: 126
wordpress_url: http://www.musterdenker.de/?p=126
date: 2009-05-31 12:58:50 +02:00
---
To build a @accordion@ like navigfation menu I used the script <a href="http://www.dynamicdrive.com/dynamicindex17/ddaccordion.htm" target="_blank">ddaccordion </a>by DynamicDrive. Alltogether a nice script, but somehow one feature is missing/not working.

My menu is expanding on mouseover and although there is always only one item expaneded thw whole menu will not collapse when I "mouseleave" the last menu entry. As the menu blends over half of my page it has to collapse. As I couldn't find a solution anywhere I added 3 lines of code to the ddacordion.js script. Go to line 166 (app.) directly after:
<pre lang="js">$('.'+config["headerclass"]).bind(config.revealtype, function(){
	if (config.revealtype=="mouseenter"){
		ddaccordion.expandone(config["headerclass"], parseInt($(this).attr("headerindex")))
	}
	else{
		$(this).trigger("evt_accordion")
		return false //cancel default click behavior
	}
})</pre>
Add the following lines:
<pre lang="js">if (config.revealtype=="mouseenter"){
$('.'+config["headerclass"]).bind("mouseleave", function(){
	ddaccordion.collapseone(config["headerclass"], parseInt($(this).attr("headerindex")))
})}</pre>

That's all, please report your experience...
