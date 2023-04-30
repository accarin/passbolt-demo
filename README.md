# Gedanken zu PassBolt
Hierbei handelt es sich um eine Endkunden-Demo mit konkreten Empfehlungen für den Produkteinsatz.
## AD/AAD/LDAP Integration ist NICHT in Passbolt CE enthalten
Dafür brauchen wir die Bezahlvariante. D.h. für Abteilungs/Teameinsatz ist die CE KEIN Problem für unternehmensweiten Einsatz wahrscheinlich eine Enterprisevariante sinnvoller für SSO.

## AD vs AAD vs LDAP
Wenn wir rein on-premise bleiben wollen, wäre der Einsatz des DIR-LDAPs wahrscheinlich am sinnvollsten. Grund der Standard-AD Connector unterstützt per Design ein AD und nicht mehrere ADs. Falls nötig, Nachfrage beim Hersteller! Wenn wir die Cloud als Auth-Provider anbinden dürfen, wäre AAD die bevorzugte Variante, weil man dann über B2B AAD oder B2C AAD auch Dritte berechtigen kann. Frage: Wollen wir das?
### tl;dr:
* **AD:** Kommt das Ding mit mehreren ADs zurecht?
* **AAD:** Cloud-Verbindung OK? Brauchen wir die Features?
* **LDAP:** DIR sollte mit dem wenigsten Aufwand funktionieren. Ist der Ansatz auch praktisch genug?

## Secret Expiry
Ist momentan ein [Working-Draft](https://docs.google.com/document/d/1gVpiU5ejVxgSmpWg6Tt0eZ_7s92RI7cfJhfiD_fiiDs/edit#heading=h.snkvmfmtcj2b) und noch in keiner stabilen Variante verfügbar. Ggf. könnte man aber selbst dafür ein [Plugin](https://community.passbolt.com/t/documentation-on-how-to-create-plugins/2913) entwickeln oder direkt in Docker über die API etwas schnitzen. (zB indem man als Übergangslösung das expiry Date ins Kommentarfeld des Secrets schreibt und man mit einem darauf berechtigten Dienst ausliest und ggf. rechtzeitig die Besitzer informiert.)