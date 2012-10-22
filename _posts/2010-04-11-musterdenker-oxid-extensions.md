--- 
layout: post
title: Musterdenker Oxid Extensions
wordpress_id: 217
wordpress_url: http://www.musterdenker.de/?p=217
date: 2010-04-11 20:06:46 +02:00
---

{% include JB/setup %}

Im Zuge des <a href="http://wiki.oxidforge.org/Downloads/4.3.0" target="_blank">4.3 er Updates</a> habe ich heute mal alle unsere veröffentlichten Module angefasst und geprüft ob sie auch mit der aktuellen eShop Version laufen. Dabei ist mir aufgefallen das ich auch gleich einen kleine Überblick geben könnte welche <a href="http://www.oxid-esales.com/de/exchange/eshop/tags/musterdenker" target="_blank">Erweiterungen der Musterdenker zur Zeit im eXchange</a> zu finden sind. In eckiger Klammer noch eine kurze Notiz ob und was geändert werden musste um die Erweiterung 4.3 kompatibel zu machen:
<ol>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/delete-tmp" target="_blank">Delete_tmp</a> (Open Source) [kein Änderung für 4.3 notwendig]
Diese winzige Modul mach das Entwickeln mit dem eShop ein bisschen einfacher. Das Problem das nach Änderungen an der Datenbank, der Übersetzungsdateien oder anderer Elemente die gecached werden der "tmp" Ordner geleert werden muss kostet viel zu oft Nerven. Dieses Modul übernimmt das für uns, bei jedem Request auf den Shop wird der gesamte cache geleert. Aber bloß nicht vergessen das Modul vorm Going-Live zu entfernen.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/user-avatar-pictures-0" target="_blank">Mude_Avatar</a> (Open Source) [kein Änderung für 4.3 notwendig - jedoch habe ich die Tempaltes auf den neusten Stand gebracht]
Erweitert das Nutzerkonto um die Möglichkeit ein Avatarbild hoch zu laden oder sein Gravatar Icon zu hinterlegen. Dieses Avatarbild wird dann neben den Kommentaren des Benutzers angezeigt. Sieht nett aus und gibt den Benutzerbewertung noch mehr Glaubwürdigkeit.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/prepayment-reminder" target="_blank">Prepayment Reminder </a>(Open Source) [Admin Templates mussten angepasst werden]
Dieses Admin Modul hilft dem Shopbetreiber einen schnellen Überblick über offene Vorkassebestellungen zu erhalten. In der neuen Liste im Admin werden alle offenen Vorkassebestellungen angezeigt und gleichzeitig besteht die Möglichkeit den einzelen Kunden direkt eine Mail zu schicken um sie ans Bezahlen zu erinnern.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/tiny-mce-admin" target="_blank">TinyMCE für Admin </a>(Open Source) [keine Änderungen notwendig, jedoch habe ich die neuste TinyMCE Version (3.3.2) eingebaut ]
Die OXID Community Edition (CE) kommt ja ohne einen WYSIWYG Editor. Wer den Tiny MCE Editor nutznen möchte für Artikellangtext, Kategoriebeschreibung, CSM, etc. sollte dieses Modul installieren.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/reorder-preorder" target="_blank">Preorder / Reorder </a>(90,00€) [Admin Templates mussten angepasst werden - neuste Version kommt in wenigen Tagen]
Wenn ein Artikel ausverkauft ist kann er nicht bestellt werden und es gehen Umsätze verloren. Auch braucht der Shopbetreiber eine Möglichkeit Informationen zu sammeln um zu entscheiden ob es sich noch lohnt ein bereits ausverkauftes Produkt nach zu bestellen. Beide Probleme löst dieses Extension. Der Shopbetreiber kann einzelne Produkte nachbestellbar machen wodurch der Kunde bei einem ausverkauften Artikel angeben können ob und wieviel dieses Artikels er vorbestellen möchte. Diese Information wird im Shopbackend zusammengefasst und aus dieser Liste herraus können die Kunden auch per Mail informiert werden sobald die Artikel wieder auf Lager sind.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/saferpay-ecommere" target="_blank">Saferpay eCommerce</a> (290,00€) [keine Änderungen notwendig - neuste Version kommt in  wenigen Tagen]
Mit diesem Modul bindet man das <a href="http://saferpay.six-card-solutions.com/de/offers/e-payment/products/Pages/eCommerce.aspx" target="_blank">Saferpay eCommerce Packet </a>an seinen OXID eShop an. Die Zahlung wird entweder direkt auf der Seite von Saferpay vorgenommen wohin der Kunde im Schritt 3 geleitet wird oder in einem iFrame ohne das der Kunde den Shop verlassen muss. Abgebucht wird der Betrag natürlich erst nach einer erfolgten Bestellung.</li>
	<li><a href="http://www.oxid-esales.com/de/exchange/extensions/mude-translate" target="_blank">Mude Translate</a> (Open Source) [funktioniert noch nicht mit Version 4.3. aufgrund <a href="https://bugs.oxid-esales.com/view.php?id=1756" target="_blank">dieses Bugs</a>]
Der jüngste Nachwuchs unter den Musterdenker OXID Modulen wurde bereits <a href="http://www.musterdenker.de/2010/03/translation-modul-for-oxid-eshop/" target="_blank">hier</a> auführlich beschrieben. Kurz zusammengefasst ermöglicht diese Erweiterung eine Editieren aller Sprachkonstanten innerhalb des Shop Frontends. Egal ob neue Sprache oder nur Anpassung des Wordings, werden dabei alle Änderungen in eine *.po Datei geschrieben. Diese Modul ermöglicht also auch die Verwendung von *.po Dateien. Dieser Standart kann genutzt werden um mit externen Übersetzungsagenturen Dateien aus zu tauschen.</li>
</ol>
Das Update der Module auf 4.3 wurde nur durch 2 Dinge getrübt. Zum einen die notwendigen Änderungen in den Admintemplates :
<blockquote><em>in the new eShop version 4.3.0, the internal links in admin tool are  changed from [{$shop-&gt;selflink}]<strong><span style="color: #ff0000;">?</span></strong>[{ $editurl }] to [{$shop-&gt;selflink}]<strong><span style="color: #ff0000;">&amp;</span></strong>[{ $editurl }]. This  allows to add parameters to the selflink not only in templates, but also  in the admin php classes. Also, this may affect some modules, which  uses admin interface templates with custom [{$shop-&gt;selflink}]<strong><span style="color: #ff0000;">?</span></strong>[{ $editurl }] urls for e.g.  frameset definitions. The '<strong><span style="color: #ff0000;">?</span>'</strong> character in these urls should be replaced by the '<strong><span style="color: #ff0000;">&amp;</span>'</strong>.</em></blockquote>
Sowie durch den <a href="https://bugs.oxid-esales.com/view.php?id=1756" target="_blank">Bug beim Erweitern der Klasse "oxlang"</a> welches auch andere Module betreffen dürfte.