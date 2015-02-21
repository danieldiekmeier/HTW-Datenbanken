# Semesterprojekt im Kurs Datenbanken
# Wintersemester 14/15
# Weißwurst-Datenbank
- Daniel Diekmeier (544835)
- Elias Klemm (546032)
- Robert Koerber (545073)
- Robert Piwonski (544838)

## Zusammenfassung

Da wir an einem Datenbank-Modell arbeiten wollten, dass wir wenigstens ein-, zweimal aus Spaß selbst benutzen können, haben wir uns für eine Datenbank entschieden, in der wir unseren Weißwurstkonsum unserer regelmäßig stattfindenden Weißwurstessen abbilden können.
Dabei sollen Weißwürste, Senfsorten, Unternehmen, wie zum Beispiel Supermärkte oder Fleischer, sowie Nutzerbewertungen der Würste gespeichert werden.
Wir hatten im Zuge der Entwicklung mit einigen Meinungsänderungen und technischen Problemen zu kämpfen, die wir aber zu unserer Zufriedenheit lösen konnten.

## Zugriffsdaten

- Host: 		db.f4.htw-berlin.de
- Username: 	s0544835
- Passwort: 	Bitte bei Daniel erfragen
- Database: 	_s0544835__weisswurst
- Port: 		3306

## Funktionsumfang

Da wir die Datenbank am Ende selbst benutzen wollten, haben sich während der Entwicklungszeit einige Anforderungen unsererseits geändert, sodass der zunächst angedachte grundsätzliche Aufbau nicht vollständig umgesetzt wurde. Allerdings haben wir in allen Fällen, in denen eine Vorgabe von unseren Änderungen betroffen war, einen adäquaten Ersatz überlegt.
Es ist nun möglich …

## Urprünglicher, grundsätzlicher Aufbau

- Eine Tabelle mit Weißwürsten:
	- Die Herkunft der Wurst, also den Schlachter, die Metzgerei, und den Markt, der diese Sorte verkauft, sollen gespeichert werden.
	- Bestimmte Besonderheiten sollen kenntlich gemacht werden: ob die Wurst frisch vom Fleischer stammt, oder im Kühlregal fertig verpackt zu finden ist, oder ob die Wurst in Naturdarm oder in künstlichen Darm gefüllt wurde.
	- Außerdem sollen weitere Bemerkungen als Freitext gespeichert werden. z. B., ob besondere Aromen besonders hervorstechen, oder wo bestimmte Verfügbarkeiten vermerkt werden.
	- Ein Bewertungssystem, das die Wurst in einem einfachen System von 1 bis 5 Sternen bewertet, was unserem subjektiven Geschmacksempfinden entspricht

- Eine Tabelle mit den entsprechenden Händlern, also Fleischereien und Supermärkten und sonstige Geschäfte
	- Adressen und die Öffnungszeiten werden dort vermerkt.

- Eine Tabelle mit Senfsorten:
	- Der vollständige Name
	- Die Art des Senfes, als Auswahl von „Süß“, „Mittelscharf“ und „Scharf“, sowie „Besondere Sorte“, mit der z. B. Frucht-Senf gekennzeichnet werden kann.
	- Wie bei der Weißwurst-Tabelle, soll das Geschäft gespeichert werden.
	- Eine Spalte für sonstige Bemerkungen als Freitext

Die Tabellen der Senfsorten und der Weißwürste sollen derart miteinander verknüpft werden, dass auch eine Bewertung gespeichert wird, die das Zusammenspiel von Senf und Wurst speichert

Zu guter Letzt sollen die Tabellen für Senf und Weißwürste mit den Geschäften verknüpft werden, in denen man sie kaufen kann.

## Beispielanwendungen

- Wir möchten herausfinden, welcher Senf besonders gut zu einer bestimmten Wurstsorte passt.
- Wir möchten uns nur Senfsorten und Würste anzeigen lassen, die beim gleichen Geschäft zu kaufen sind
- Beim Einkauf auf den letzten Drücker wollen wir herausfinden, welche Geschäfte am Samstag nach 19:00 Uhr offen haben.
- Für die wahren Zuzler kommt natürlich nur echter Darm in Frage, also sollen alle Suchen auf Würste nur in Naturdarm beschränkt werden können.

## Durchführung

### Konzeptuelles und physisches Schema

Wir haben haten aus dem bereits vorhandenen Konzept ein Entity-Relationship-Modell entwickelt welches alle Relationen darstellt. Jedoch wurde das Modell immer wieder kleineren und größeren Änderungen unterworfen (Beispiele unter *Änderungen während der Modellierungsphase*), sodass wir uns entschieden haben hier nur das finale Diagram zu zeigen.

![alt tag](img/Weisswurstdatenbank.jpg)

Aus diesem wurde ein Datenbankmodell welches zusätzlich Datentypen definiert. (Dieser Punkt stimmt glaube ich noch nicht ganz.)

### Prozeduren

### Funktionen

### Sicht

### Anwender Oberfläche (sollen wir das machen? Wäre eigentlich z.B. mit PHP recht leicht umsetzbar. Richtig Lust hab ich dazu aber nicht.)

### Änderungen während der Modellierungsphase
- Die Abstufungen bezüglich dem Schärfegrad von Süß, Mittelscharf, Scharf und Besondere Sorte soll zu einer numerischen von 1-100 geändert werden. Somit entsteht die Möglichkeit zwei ähnlich scharfe Senfe miteinander zu vergleichen.
- Wir haben uns dazu entschlossen eine eigene Tabelle für die Weiswurst Typen zu definieren da diese immer wieder vorkommen und die Eindeutigkeit verbessert werden kann.
- Aus Gründen der Ähnlichkeit haben wir die Fleischer und Verkäufer in die Tabelle `Unternehmen` gebündelt. Somit sind diese zentral verwaltbar. Zusätzlich definieren wir eine Tabelle `Unternehmenstyp` um eine Unterscheidung festzuhalten. 

### Probleme
- Wir konnten häufige Verbindungsabbrüche / Probleme mit dem Aufbau feststellen. Dies ist auf die Limitierung von einzelnen Verbindungen auf die Datenbank zu führen. (`Mysql Error 1203`)  

