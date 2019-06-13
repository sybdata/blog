---
title: "User Experience Changes from WSL 1 to WSL 2"
date: 2019-06-13T15:34:30-04:00
categories:
  - Windows Subsystem for Linux
tags:
  - WLS
  - Linux kernel
---
Auf dieser Seite verläuft über die Unterschiede hinsichtlich der benutzerfreundlichkeit zwischen WSL 1 und der WSL-2-Vorschau. Die wichtigsten Änderungen, zu berücksichtigen sind:

   * Speichern Sie Dateien, die Ihre Linux-apps in Ihrem Linux-Root-Dateisystem für schnellere Leistung, Geschwindigkeit Datei zugegriffen wird
   * In ersten die WSL-2-Vorschau-Builds müssen Sie den Zugriff auf netzwerkanwendungen mithilfe einer IP-Adresse und nicht "localhost"

Und unten ist die vollständige Liste der anderen Änderungen, die Sie ggf. bemerken:

   * WSL 2 verwendet eine virtuelle Festplatte zum Speichern der Dateien, und wenn Sie die maximale Größe erreichen müssen Sie möglicherweise um ihn zu erweitern
   * Beim Start wird WSL 2 einen kleinen Anteil des Speichers jetzt verwenden.
   * Cross-Betriebssystem wird zugriffsgeschwindigkeit der Datei in der ersten Vorschau-Builds langsamer sein.

## Speichern Sie die Linux-Dateien in Ihrem Linux-Root-Dateisystem

Stellen Sie sicher, dass die Dateien, die Sie häufig mit Linux zugreifen, stellen Anwendungen innerhalb Ihrer Linux-root-Dateisystem, um die Datei Leistungsvorteile nutzen zu können. Diese Dateien müssen in das Stammdateisystem für Linux, damit schnellere Dateisystemzugriff sein. Wir haben auch möglich, dass Windows-apps, die Linux-Root-Dateisystem (z. B. Datei-Explorer! den Zugriff auf die vereinfacht Versuchen Sie es ausgeführt wird: ```explorer.exe /``` in Ihrem Bash-Shell und was geschieht, finden Sie unter) dem erleichtert diesen Übergang erheblich.

## Zugriff auf netzwerkanwendungen

In der ersten die WSL-2-Vorschau-Builds müssen Sie die IP-Adresse Ihrer Linux-Distribution und einem beliebigen Windows-Server unter Linux, die die IP-Adresse des Host-Computers mit Windows auf einem Linux-Server. Dies ist etwas, das temporäre, und auf unserer Prioritätenliste beheben sehr hoch ist.

### Zugreifen auf Linux-Anwendungen aus Windows

Wenn Sie einen Server in einer Distribution WSL verfügen, müssen Sie die IP-Adresse des virtuellen Computers verbessern der Leistung von Ihrer Distribution zu finden und mit dieser IP-Adresse herstellen. Sie können dazu folgende Schritte:

   * Erhalten Sie durch Ausführen des Befehls die IP-Adresse Ihrer Distribution ```ip addr``` innerhalb Ihrer Distribution WSL und finden sie unter den ```inet``` Wert der ```eth0``` Schnittstelle.
        * Sie finden diese leichter durch Filtern der Ausgabe des Befehls mit Grep folgendermaßen: 
        ```ruby
        ip addr | grep eth0.
        ```
   * Verbinden Sie mit dem Linux-Server mit der IP-Adresse, dem Sie weiter oben wurde gefunden.

Die folgende Abbildung zeigt ein Beispiel dafür durch Herstellen einer Verbindung mit einem Node.js-Server mit Microsoft Edge-Browser.
{% include figure image_path="https://docs.microsoft.com/de-de/windows/wsl/media/wsl2-network-w2l.jpg" alt="this is a placeholder image" caption="" %}

### Zugriff auf Windows-Anwendungen unter Linux

Für den Zugriff auf eine Windows-Netzwerk-Anwendung müssen Sie die IP-Adresse des Host-Computers zu verwenden. Mit diesen Schritten können Sie tun:

   * Abrufen die IP-Adresse des Host-Computers mithilfe des Befehls ```cat /etc/resolv.conf``` und kopieren die IP-Adresse, die nach dem Begriff ```nameserver```.
   * Verbinden Sie mit einem beliebigen Windows-Server, der die kopierten IP-Adresse.

Die folgende Abbildung zeigt ein Beispiel dafür durch das Verbinden mit einem Python-Server unter Windows über Curl.
{% include figure image_path="https://docs.microsoft.com/de-de/windows/wsl/media/wsl2-network-l2w.png" alt="this is a placeholder image" caption="" %}

## Grundlegendes zu WSL 2 verwendet, eine virtuelle Festplatte, und was Sie tun, wenn Sie die maximale Größe erreicht

WSL-2 speichert alle Linux-Dateien in eine VHD, die das ext4-Dateisystem verwendet. Diese virtuelle Festplatte wird automatisch um die speicheranforderungen zu erfüllen. Diese virtuelle Festplatte verfügt auch über eine maximale anfängliche Größe von 256GB. Wenn Ihre Distribution in Größe größer sein als 256 GB vergrößert wird, sehen Sie Fehler, die besagt, dass Sie, nicht genügend Speicherplatz vorhanden ausgeführt haben. Sie können diese durch Erweitern der VHD-Größe beheben. Anweisungen dazu finden Sie unten:

   1. Beenden Sie alle WSL-Instanzen, die mit der die ```wsl --shutdown Befehl```
   2. Ändern der Größe der virtuellen Festplatte WSL-2 dazu die folgenden Befehle
    
      * Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten, und führen Sie die folgenden Befehle aus:
       * ```Select vdisk file="<pathToVHD>"```
       * ```expand vdisk maximum="<sizeInMegaBytes>"```
            
   3. Starten Sie Ihre Distribution WSL
   4. Stellen Sie die WSL Beachten Sie, dass das Dateisystem Größe erweitert werden kann
        
      * Führen Sie diese Befehle in Ihrer Distribution WSL:
       * ```sudo mount -t devtmpfs none /dev```
       * ```mount | grep ext4```
        * Kopieren Sie den Namen dieses Eintrags, der aussieht: / Dev/SdXX (mit dem X, die alle anderen Zeichen darstellt.)
       * ```sudo resize2fs /dev/sdXX```
        * Stellen Sie sicher, den Wert Sie zuvor kopiert haben, und Sie verwenden möchten: 
                 ```apt install resize2fs.```

## WSL 2 wird Arbeitsspeicher beim Start verwenden.

WSL 2 verwendet ein einfaches Hilfsprogramm-VM auf einem echten Linux-Kernel, um zur Verfügung zu stellen hervorragende Leistung des Dateisystems und vollständige Kompatibilität und dennoch wird ebenso wie Licht, schnelle, integrierte und reaktionsfähig wie WSL 1 aufrufen. Dieses Hilfsprogramm-VM einen kleinen Speicherbedarf aufweist und belegt Arbeitsspeicher beim Start virtuelle Adresse, die gesichert. Starten Sie einen kleinen Anteil des Ihrer gesamten Arbeitsspeichers konfiguriert ist.

## Cross-Betriebssystem wird Datei Geschwindigkeit in der ersten Vorschau-Builds langsamer sein.

Sie werden feststellen, langsameren Datei WSL 1 verglichen wird, wenn der Zugriff auf Windows-Dateien auf einer Linux-Anwendung und den Zugriff auf Linux-Dateien aus einer Windows-Anwendung. Dies ist das Ergebnis der Änderungen an der Architektur in WSL 2 und etwas, das die WSL-Team aktiv wird untersucht, wie wir diese Erfahrung verbessern können.
