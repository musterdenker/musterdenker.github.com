--- 
layout: post
title: OXID eShop trifft CMS
wordpress_id: 205
wordpress_url: http://www.musterdenker.de/?p=205
date: 2010-01-05 13:11:08 +01:00
---
Gerade finde ich in meinem Postfach eine Mail die mich informiert das <a href="http://www.topconcepts.de" target="_blank">top concepts</a> ihre Integration vom OXID eShop in das hauseigene CMS abgeschlossen ist. Für mich anlass genug ein bisschen etwas über das Thema OXID und CMS zu schreiben.

<strong>OXID CMS - Status quo:
</strong>
<ul>
	<li>Der eShopbesitzt CMS Seiten die an beliebiger Stelle eingebunden werden können: als Link oder im Kategoriebaum</li>
	<li>Jede CMS Seite besteht aus einem großen Textblock der per WYSIWYG Editor befüllt wird, einen Titel und außerdem kann die SEO-Url angepasst werden.</li>
	<li>Natürlich unterstützen die CMS Seiten genauso wie der Rest des eShops beliebig viele Sprachen</li>
</ul>
Mit dieser Basisausstattung kommt man, wie ich aus eigener Erfahrung weiss recht weit. So gibt es sogar "nicht"-Shops die mit mit eShop umgesetzt wurden und den Shop als CMS nutzen (<a href="http://www.anzido-akademie.de/" target="_blank">z.b. Anzido Akademie</a>). Dennoch stößt man natürlich bei sehr inhaltslastigen Angeboten schnell an die Grenzen. So z.B.:

<strong>OXID CMS - das fehlt...</strong>
<ul>
	<li>CMS Seiten sind nicht durchsuchbar</li>
	<li>alle CMS Seiten haben das gleiche Template</li>
	<li>CMS Seite können nicht beliebig verschachtelt werden (so wie z.B. Artikel in Kategorien)</li>
	<li>das Rechte &amp; Rollen System der EE (OXID eShop Enterprise) greift nicht auf einzelnen CMS Bereiche / CMS Seiten</li>
	<li>es gibt nur eine Textbox pro Seite</li>
	<li>...</li>
</ul>
<strong>top concepts CMS</strong>

Schon seit dem 4er Release gab es immer mal wieder Bemühungen diesem Problem Abhilfe zu schaffen und jetzt scheint eine weitere Lösung fertig zu sein. Was top concepts in ihrem <a href="http://topconcepts.wordpress.com/2010/01/04/top-concepts-cms-oxid-eshop/" target="_blank">Blog</a> schreiben klingt vielversprechend. So wurde der eShop in das bestehende CMS eingebunden wobei das CMS der Master ist und jede benötigte eShop Funktionalität einzeln lädt/aufruft. Da das CMS eine SaaS Lösung ist kann man den Code leider nicht begutachten, muss sich als Nutzer bzw. Reseller aber auch keine Gedanken darüber machen ;) gut zu hören ist das der Shop weiterhin getrennt vom CMS läuft und auch voll updatefähig bleibt. Auch wenn ich das top concepts CMS nicht bis ins Detail kenne scheint es mir ein erwachsener Vertreter seiner Zunft zu sein. Um als externen Entwickler / Agentur in den Genuss dieser CMS eShop Kombi zu kommen wird es ein Resellerprogramm geben. Ich bin schon jetzt sehr gespannt darauf.

<strong>TOXID</strong>

Doch top concepts sind nicht allein. Ein weiterer Ansatz an dem auch schon lange gearbeitet wird scheint sich auch der Fertigstellung zu nähern:
"TOXID" Was sich giftig anhört ist das Projekt von Joscha Krug (aka. <a href="http://www.marmalade.de/" target="_blank">Marmalade.de</a>) mit dem Ziel Typo3 mit dem OXID eShop zu verheiraten. In dem letzten <a href="http://blog.marmalade.de/2009/12/aktueller-stand-von-toxid/" target="_blank">Blogpost zu dem Thema</a> hört es sich so an als ob die Fertigstellung in nicht all zu weiter Ferne liegt. Anders als bim voherigen Beispiel soll hier der OXID Shop der Master sein und Typo3 dem Shop also seine CMS Features zur Verfügung stellt. Vergleicht man den Umfang beider Programme so scheint es als ob David hier über Goliath befiehlt. Mir gefällt dieser Ansatz jedoch sehr gut, denn bei einem eCommerce Projekt sollte der eShop im Vordergrund stehen. Auch soll es vielleicht eine Open Source Version geben, was angesichts der Tatsache das Typo3 wie auch OXID Open Source sind natürlich wunderbar wäre. Leider gibt es noch keinenkonkreten Veröffentlichungstermin. Aber ich schließe mich dem Kommentar von "TypoTom" auf o.g. Blogbeitrag an und biete gerne meine Hilfe an sofern es sich um ein Open Source Projekt handelt.

<strong>Fatchip OXID CMD Modul</strong>

Neben diesen beiden "Verschmelzungen" gibt es auch noch eine eigenständige Extension zum OXID eShop welche die bestehenden CMS Funktionen aufbohren soll. Das von <a href="http://shop.fatchip.de/OXID-eShop-Module/OXID-CMS-Modul.html" target="_blank">Fatchip angebotenen Modul</a>. Leider ist die Beschreibung recht mager aber es scheint so als ob viele von meinen oben aufgeführten Problemen gelöst werden. Es gibt eine Rechteverwaltung, seperates Tempaltes und ein dynamisches Menü (was genau das auch immer ist). Ich werde mal schauen ob ich eine Version bekommen kann um sie ausführlich zu testen und dann hier an dieser Stelle mehr Details zu berichten.

<strong>DIY - Do it yourself</strong>

Zu guterletzt kann man auch selbst Hand an legen und mit ein paar einfachen Tricks das bordeigene CMS aufbohren. So kann man auch Artikel und Kategorien als CMS Seiten nutzen. Beiden kann man eigene Tempaltes zuweisen und beide besitzen ein WYSIWYG Textfeld. Damit haben wir dann die Möglichkeit CMS Seiten beliebig zu verschachteln (mit Hilfe der Kategorien) und können für jede CMS Seite eigene Templates vergeben (mit Hilfe des Template Feldes für Artikel und Kategorien). Auch werden dies CMS "Artikel" ohne weiteres durch die Suche gefunden. Ein bisschen sollte man den eShop jedoch durch eine Extension anpassen um z.B.
<ul>
	<li>zu verhindern das diese "Artikel" gekauft werden können</li>
	<li>die CMS Artikel in der Suche gesondert dar zu stellen</li>
	<li>ein gesonderte Darstellung im Admin um die Pflege zu erleichtern</li>
	<li>...</li>
</ul>
Also auch hier kann man viel Zeit investieren, aber wem die bestehenden Lösungen nicht gefallen hat hiermit einen guten Ansatz es selbst zu machen.

Ich hoffe ich konnte den ein oder anderen Einblick hinterlassen und wer noch weitere OXID - CMS kennt möge doch bitte einen Kommentar hinterlassen.
