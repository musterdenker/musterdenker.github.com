--- 
layout: post
title: Changing scope in PHP for unit testing
wordpress_id: 189
wordpress_url: http://www.musterdenker.de/?p=189
date: 2009-10-13 14:54:24 +02:00
---
Mathias Krieck recently publish an easy way to change scope of methods and variables.

The main use is for unit testing (e.g <a href="http://www.phpunit.de/" target="_self">PHPUnit</a>) when you need to access protected or private variables / methods. With his "<a href="http://phpclasses.waaf.net/browse/package/5659.html" target="_self">Super Proxy</a>" you do:
<pre>$oInstance = SuperProxy::getInstance("CLASSNAME", $aParams);</pre>
Whereas "$aParams" is an optional parameter. The return value "$oInstance" is an instance of the given class where everything is public. So you can access everything from outside.

<strong>Stop!!!</strong>
Do you want to post a comment like "bad coding style" or something similar? First you should be aware that this helper is intended to be only used for unit testing or other meta programming, but NEVER in productive code.

I myself think that's fine ;) And of course it's open source!

So please help Matze to win the "Innovation Award" by <a href="http://phpclasses.waaf.net/browse/package/5659.html" target="_blank">voting for him here.</a>
