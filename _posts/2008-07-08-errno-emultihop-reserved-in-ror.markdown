--- 
layout: post
title: "Errno: EMULTIHOP (Reserved) in RoR "
wordpress_id: 6
wordpress_url: http://www.musterdenker.de/?p=6
date: 2008-07-08 00:46:09 +02:00
---
Seit gestern bekomme ich folgenden Error beim Aufruf jeder Seite meines aktuellen Rails-Projektes:
Errno::EMULTIHOP in MyBlaController#index
EMULTIHOP (Reserved)
Da ich im Netz weder direkte Hilfe noch Leidensgenossen mit dem gleichen Problem finden konnte möchte ich meine Erfahrungen hier kurz niederschreiben. Der Stack trace selbst weisst auf den Datenbank connect hin was mir aber von Anfang an seltsam vorkam. Debuggen ergab das die zugehörige Exception tief im Kern von Ruby geschmissen wird (jenseits von .process). Der Urspung des Fehlers liegt irgendwo om System und wird von Ruby nur übersetzt (error.c) leider ohne weiterführende Informationen. EMULTIHOP kommt aus der Linux Welt und steht für:
EMULTIHOP
Components of path require hopping to multiple remote machines and file system type does not allow it.
Da ich unter Ubuntu arbeite passt das ganz gut, bringt mich aber auch nicht näher an die Lösung des Problems. So blieb nur stures Try&amp;Error. Das Ergebniss: Die genutzte Ruby-Platform war auf Version 1.1 gestellt (keine Ahnung wieso...), ein Wechsel auf 1.85 lies den Fehler verschwinden. Das seltsame ist das ich mich nicht erinnern kann auf 1.1 gewechselt zu haben. Vieleicht hat Netbeans sich ja verschluckt?! So oder so, das Problem ist gelöst wenn auch nicht völlig verstanden, ich bitte deshalb um Feedback.
