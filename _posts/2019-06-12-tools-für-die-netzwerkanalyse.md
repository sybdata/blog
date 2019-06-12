---
title: "Die 10 wichtigsten Tools für die Netzwerkanalyse mit der Kommandozeile cmd"
date: 2019-06-12T15:34:30-04:00
categories:
  - Netzwerk
tags:
  - IP
  - ipconfig
  - DHCP
  - DNS
---

1. Zeigt die IP-Konfiguration des lokalen Systems an:
```ruby
C:\Windows\System32> ipconfig
[/all] Detaillierte Ausgabe aller Parameter
[/renew] IP-Adresse vom DHCP-Server
[/release] IP-Adresse freigeben
[/displaydns] Inhalt des DNS-Caches anzeigen
[/flushdns] DNS-Cache löschen
[/registerdns] DNS-Record registrieren 
```
2. Zeigt die Zuordnung von MAC-Adressen zu IP-Adressen an:
```ruby
c:\Windows\System32> arp
[-a] Zeigt alle Zuordnungen an.
```
3. Zeigt den DNS-Hostnamen des lokalen Systems an:
```ruby
c:\Windows\System32> hostname
```
4. Löst den DNS-Namen bzw. die IP-Adresse auf dem primären DNS-Server auf:
```ruby
c:\Windows\System32> nslookup
```
5. Zeigt TCP / IP Statistiken an:
```ruby
c:\Windows\System32> netstat
Standardmäßig werden die momentan offenen Verbindungen angezeigt
[-a] Zeigt auch serverseitige Verbindungen an.
[-n] Zeit IP-Adressen und Portnummern an.
[-p] Hiermit kann ein bestimmtes Protokoll gewählt werden.
[-o] Zeigt zu jeder Verbindung die Prozess PID an
```
6. Zeigt die Route zum Ziel und berechnet für jeden Abschnitt Statistiken:
```ruby
c:\Windows\System32> pathping
[-h] Setzt einen Maximalwert für die Hops Anzahl
[-4] Erzwingt die Verwendung von IPv4
```
7. Es wird ein Ping an einen Rechnernamen oder IP-Adresse ausgeführt:
```ruby
c:\Windows\System32> ping
[-t] Der ping läuft so lange bis er per Tastenkombination abgebrochen wird.
[-l] Setzt die Länge der Pakete in Byte
```
8. Zeigt die Routingtabelle an und lässt Konfigurationen zu:
```ruby
c:\Windows\System32> route
[print] Zeigt alle Routingeinträge an
[add] Fügt einen Routingeintrag hinzu.
[delete] löschen einen Routingeintrag
```
9. Zeigt die Namenstabelle und aktuelle Verbindungen von NetBIOS über TCP an:
```ruby
c:\Windows\System32> nbtstat
[-c] Zeigt den Inhalt des Cache an.
[-n] Zeigt lokale NetBIOS Namenszuordnungen an.
[-R] Löst den Cache
```
10. Zeigt die Route zum Ziel an:
```ruby
c:\Windows\System32> tracert
[-h] Setzt die maximale Anzahl von Hops, welche zur Zielsuche verwendet werden dürfen.
```



[Quelle:](https://it-learner.de/)
