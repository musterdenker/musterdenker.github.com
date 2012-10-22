--- 
layout: post
title: Google Product Search aka Froogle with Rails
wordpress_id: 25
wordpress_url: http://www.musterdenker.de/?p=25
date: 2009-02-04 14:10:08 +01:00
---
Yesterday I wanted to put all my articles (from <a href="http://www.deineschokoladen.com" target="_blank">deineschokoladen.com</a>) from my Ruby on Rails application into the google product search formally knows as Froogle and again I was surprised how easy it was! Nevertheless I couldn't find a tutorial about that topic, so I had to look up the facts at different places. So I'll just put everything here at one place:

1. You need to trust big G and get a google account with which you can login into <a href="http://www.google.de/base/" target="_blank">google base</a>, There you can create articles (or nearly anything else like job adds, events, ...) manually, or you can upload a data feed. As I wanted to put more then 1500 products online I choose the data feed.

2. Create the data feed in your rails app: Of course this depends on your application but it should be very easy to adapt the following code to your needs. First you need a controller action like this:
<blockquote>def froogle
@products = Products.find(:all)
xml_string = render_to_string :layout =&gt; false, :content_type =&gt; "application/xml"
send_data xml_string, :filename =&gt; "my.xml"
end</blockquote>
As we use xml builder (build in in Rails) the only thing we need now is a view called <em>froogle.xml.builder</em> which looks like this (this is with german attributes, for oterh countries have a look at google base for correct attribute names):
<blockquote>xml.instruct!( :xml, :version =&gt; "1.0", :encoding =&gt; "UTF-8")
xml &lt;&lt; '&lt;rss version ="2.0" xmlns:g="http://base.google.com/ns/1.0"&gt;'

xml.channel {
xml.title("YOUR TITLE")
xml.Link("LINK TO PRODUCTS")
xml.description("A SHORT DESCRIPTION")
for product in @products do
xml.item{
xml.title(product.title)
xml.description(product.description)
xml.link("http://www.YOURAPP.com/products/" + product.id.to_s)
xml.tag!("g:id", product.id)
xml.tag!("g:preis", product.price)
xml.tag!("g_mpn", product.id)
xml.tag!("g:bild_url", product.image_url)
xml.tag!("g:marke", product.brand)
xml.tag!("g:gewicht", product.weitgh)
xml.tag!("g:preisart", "ab")
xml.tag!("g:hersteller", product.manufacturer)
xml.tag!("g:zustand", "neu")
xml.tag!("g:produktart", "PRODUCT_TYPE")
}
end
}

xml &lt;&lt; '&lt;/rss&gt;'</blockquote>
Thats already all! just open you action like this <em>YOURAPP.com/CONTROLLER/froogle?fromat=xml</em> and you can download the XML file and afterwards upload it to google base.

As you need to renew the product data in google base frequently to be up to date, an automatic upload would be more convenient. So lets add a few more lines to our controller:
<blockquote>def froogle
@products = Product.find(:all)

xml_string = render_to_string :layout =&gt; false, :content_type =&gt; "application/xml"

my_file = File.new("tmp/my.xml", "w")
my_file.puts xml_string

ftp = Net::FTP.new('uploads.google.com')
ftp.login("FTPUSERNAME", "FTPPASSWORD")
ftp.putbinaryfile("tmp/my.xml", "my.xml" )
ftp.quit()

render :text =&gt; "done"

end</blockquote>
Be aware that ftp user/password has to be set up separately at google base and it can take more then 2h till they are working. Now when you invoke the "froogle" action your xml will be automatically transfered to and processed by google base.

Any hints and/or questions? Please leave a comment
