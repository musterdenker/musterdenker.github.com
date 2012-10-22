--- 
layout: post
title: OXID trifft CMS Part 2
wordpress_id: 211
wordpress_url: http://www.musterdenker.de/?p=211
date: 2010-01-11 13:37:23 +01:00
---
Nach dem positiven Feedback auf meinen ersten <a href="http://www.musterdenker.de/2010/01/oxid-eshop-trifft-cms/" target="_blank">Artikel über CMS Erweiterungen für den OXID eShop</a>, möchte ich den Artikel nun vervollständigen. Erfreulicherweise gibt es nämlich noch mehr :)

<strong>OXID2CON</strong>
Das Offenbacher Unternehmen <a href="http://www.4fb.de/" target="_blank">four for business</a> wird in naher Zukunft eine Schnittstelle (<a href="http://www.4fb.de/Loesungen/Shopsystem-OXID-eShop/OXID2CON/OXID2CON-Portal/" target="_blank">OXID2CON</a>) veröffentlichen zwischen dem OXID eShop und dem <a href="http://www.contenido.org/" target="_blank">CMS Contentido</a>. Letzteres war mir bisher leider unbekannt. Ich habe es aber etwas unter die Lupe genommen und bin positiv überrascht. Contentido ist ein kleines aber feines CMS veröffentlicht unter der GPL Lizenz mit sehr einfach zu erweiterten HTML Templates. Die aktuelle Versionsnummer 4.8 , ein aktives Communityforum und sehr viele Referenzen im Web lassen auf ein ausgereiftes und vielgenutztes CMS schließen. Schlimm genug das ich es bisher nicht kannte ... In einem zukünftigen Projekt werde ich es mal ausprobieren und mir dann noch ein genaueres Bild machen.
Aber zurück zu der OXID Schnittstelle. Da ich freundlicherweise einen Testzugang zu dem Entwicklungssystem bekommen hatte konnte ich OXID2CON testen. Das erste das auffällt ist das der eShop der "Master" ist. Also die gesamte Webseite wird durch den Shop gesteuert und CMS Inhalte werden aus Contentido geladen. Die Lösung ist elegant und einfach. Wie schon im letzten Artikel erwähnt werden die eShop Kategorien genutzt und um den CMS Inhalt erweitert. Dazu kann man im Admin aus einer normalen Kategorie eine "Contentido-Kategorie" machen und den Inhalt auswählen der dynamisch aus Contentido geladen werden soll. Das bedeutet die Inhaltspflege findet im Contentido Backend statt und im Shop Backend wird dann festgelegt wo der entsprechende Inhalt auftauchen soll. Links zwischen CMS Inhalten machen keine Probleme und auch dynamische Inhalte aus dem Shop (wie Artikellisten) sollen sich darstellen lassen. Ein kleiner Wermutstropfen: Momentan wird nur eine Sprache unterstützt. Aber da CMS wie auch eShop mehrsprachig sind,  wäre eine entsprechende Erweiterung, so wurde mir versichert, kein größeres Problem. Den angezielten Preis kenne ich noch nicht, werde ich aber nachreichen.

<strong>TOXID</strong>
Beim Thema Preis noch eine kleine Ergänzung zu TOXID aus dem letzten Artikel. Die Version für den OXID CE und soll auf jeden Fall Open Source veröffentlicht werden. Daumen hoch dafür!

<strong>DIY (Do it yourself)</strong>
Abschließend möchte ich noch auf ein Tutorial von Andreas Ziehten (<a href="http://www.anzido.com/" target="_blank">Anzido GmbH</a>) zum Thema "<a href="http://phpbuilder.com/columns/Andreas_Ziethen010710.php3" target="_blank">PHP Modul Programming with OXID eShop C</a>E" verweisen. Denn das gewählte Beispiel ist eine Erweiterung des eingebauten CMS um die Möglichkeit CMS Artikel zu verschachteln. Sofern man den Shop also selbst erweitern möchte ist dieses Tutorial ein perfekter Startpunkt.
