# GenealogyTree

Link zum Datenbankdesign:
https://dbdiagram.io/d/67832cde6b7fa355c399cc4c

Im System können registrierte Benutzer Änderungen vorschlagen oder neue Verbindungen zwischen Familien anregen. Die Daten entwickeln sich daher dynamisch weiter.

1. Vorschläge für Änderungen

Jede vorgeschlagene Änderung wird als neuer Eintrag in der Tabelle Proposition gespeichert und referenziert die betroffene Person oder Beziehung.

Beim Anlegen einer Proposition werden die Zähler für Genehmigungen und Ablehnungen initialisiert.

2. Antworten auf Vorschläge

Mitglieder der Community können Vorschläge genehmigen oder ablehnen.

Jede Antwort wird als neuer Eintrag in der Tabelle Proposition_Response gespeichert.

3. Validierung und Anwendung der Änderungen

Jede Genehmigungs- oder Ablehnungsaktion führt zu einer Aktualisierung der entsprechenden Zähler.

Genehmigung:
Jede Genehmigung erhöht den Genehmigungszähler der Proposition.
Erreicht der Zähler 3 Genehmigungen, wird das Attribut is_approved auf true gesetzt und die vorgeschlagenen Änderungen werden auf die Tabellen People und Relationships angewendet.

Ablehnung:
Jede Ablehnung erhöht den Ablehnungszähler.
Erreicht der Zähler 3 Ablehnungen, wird die Proposition verworfen und gelöscht.

  
