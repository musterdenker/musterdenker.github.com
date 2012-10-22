--- 
layout: post
title: Paypal Checkout with 3rd party shopping cart and discounts
wordpress_id: 35
wordpress_url: http://www.musterdenker.de/?p=35
date: 2009-02-18 11:29:20 +01:00
---
<div class="post-meta">Ok, for the start a short and simple answer: It’s NOT possible.</div>


	
<p><strong>Problem:</strong><br>
I’m using paypals checkout by submitting a form to paypal that contains
all the articles, prices and quantities from my shopping card to
paypal. In fact thats a really nice and easy way to integrate paypal,
BUT I recently made a mistake. I wanted to add absolute discounts,
which is not possible! With relative discounts like 10% I could reduce
all prices of the articles in the my shopping card by 10% manually, but
when it comes to an absolute discount like 5€ for the whole basket
there is no way to do it. There is no special field for discount nor
could I add an article called “discount” with an negative price.
Another way to reduce the price of the articles one by one till the
discount is “dead” is a very ugly and user unfriendly solution as no
article is allowed to have a price of 0 (0.01 is minimum).</p>
<p><strong>Solution:</strong><br>
The only easy and user friendly solution I could imagine was to build
in a fall back and pass the aggregated cart amount to paypal instead of
all articles. So deineschokoladen.com now shows all card items on
paypal checkout page only when no discount (voucher) is applied. In
case a user cashes a voucher the user only sees the aggregated sum on
paypal checkout page.</p>
