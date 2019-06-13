---
title: "Informationen zu WSL 2"
date: 2019-06-13T15:34:30-06:00
categories:
  - Windows Subsystem for Linux
tags:
  - WLS
  - Linux kernel
---

WSL 2 ist eine neue Version der Architektur, die dem Windows-Subsystem für Linux zum Ausführen von ELF64 Linux-Binärdateien auf Windows zugrunde liegen. Die Hauptziele sind, um die Leistung des Dateisystems, ebenso wie das Hinzufügen Aufruf vollständige Kompatibilität zu erhöhen. Diese neue Architektur ändert, wie diese Linux-Binärdateien mit Windows und Hardware des Computers zu interagieren, jedoch bietet weiterhin die gleiche benutzerfreundlichkeit wie WSL 1 (die aktuelle allgemein verfügbare Version). Einzelne-Linux auf Distributionen können entweder als eine WSL-1-Distribution oder als eine WSL-2-Distribution ausgeführt werden, aktualisiert oder zu einem beliebigen Zeitpunkt herabgestuft werden kann, und Sie können die WSL-1 und 2 von WSL Distributionen parallel ausführen. WSL 2 wird verwendet, eine ganz neue Architektur, die einen echten Linux-Kernel verwendet wird.
Linux kernel in WSL 2

Der Linux-Kernel in WSL 2 wird intern von der neuesten stabilen Verzweigung auf Grundlage der Quelle unter kernel.org erstellt. Dieser Kernel wurde speziell für WSL 2 abgestimmt. Es für die Größe und Leistung bieten eine hervorragende Benutzeroberfläche für Linux auf Windows optimiert wurde und werden verarbeitet, über Windows-Updates, was bedeutet, dass Sie den neuesten Sicherheitskorrekturen und kernelverbesserungen erhalten werden, ohne es selbst zu verwalten.

Außerdem werden diese Kernel open-Source. Sie finden den vollständigen Quellcode für den Linux-Kernel [hier](https://thirdpartysource.microsoft.com/download/Windows%20Subsystem%20for%20Linux%20v2/May%202019/WSLv2-Linux-Kernel-master.zip). Wenn Sie, um weitere Informationen möchten zu diesen Kernel, Sie sich sehen [in diesem Blogbeitrag](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/) geschrieben, von dem Team, das sie erstellt.
Eine kurze Übersicht über die WSL-2-Architektur

WSL 2 verwendet das neueste und beste in Virtualisierungstechnologie, die Linux-Kernel in einem einfachen Hilfsprogramm-Computer (VM) ausgeführt. WSL 2 werden jedoch nicht über eine herkömmliche VM-Umgebung. Eine herkömmliche VM-Umgebung kann langsam gestartet sein, isoliert ist, viele Ressourcen verbraucht und Ihre Zeit für die Verwaltung erfordert. Diese Attribute keine WSL 2. Sie erhalten weiterhin die bemerkenswerte Vorteile von WSL 1: Hohes Maß an Integration zwischen Windows und Linux, extrem schnelle Startzeiten, kleine Speicherbedarf und das beste ist keine VM-Konfiguration oder Verwaltung erforderlich. Während WSL 2 einer virtuellen Maschine verwendet, wird es verwaltet und hinter den Kulissen, sodass Sie die gleiche benutzerfreundlichkeit wie WSL 1 ausgeführt werden.
Erhöhte-Datei-e/a-Leistung

Datei rechenintensive Vorgänge wie das Git-Klon, Npm installieren, apt-Update, apt-Upgrade usw. alle deutlich schneller. Die Erhöhung der tatsächlichen Geschwindigkeit hängt in der app sind Sie ausgeführt wird und wie sie mit dem Dateisystem interagieren wird. Anfängliche WSL-2-Versionen ausgeführt, bis zu 20 Mal schneller WSL 1 verglichen wird, beim Entpacken einer ZIP-Tarball, und um 2 bis 5 X schneller ausgeführt, wenn Git-Klon "," Npm Install "und" Cmake an verschiedenen Projekten verwenden.
Kompatibilität der vollständigen Aufruf

Linux-Binärdateien verwenden Systemaufrufe für viele Funktionen, z. B. den Zugriff auf Dateien, Arbeitsspeicher anfordern, das Erstellen von Prozessen und vieles mehr. Während WSL 1 eine Übersetzungsschicht, die vom Team WSL erstellt wurde verwendet, bietet WSL 2 einen eigenen Linux-Kernel Kompatibilität der vollständigen Aufruf. Dies führt zu einen komplett neuen Satz von apps, die Sie innerhalb von WSL, wie Docker und vieles mehr ausführen können. Darüber hinaus können keine Updates für den Linux-Kernel sofort auf Ihrem Computer hinzugefügt werden, anstatt die WSL-Team die Änderungen zu implementieren und dann warten, die sie hinzugefügt.
