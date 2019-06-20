---
title: "MMC(.msc) & Control Panel(.cpl)"
date: 2019-06-20T15:34:30-04:00
categories:
  - Windows 10 - Server
tags:
  - Windows 10
  - Windows Server
  - MMC Consoles
  - Control Panel
  - .msc
  - .cpl
---
Öffnen Sie PowerShell und führen Sie den folgenden Befehl aus, um eine Liste aller mmc- und cpl-Dateien abzurufen:
```ruby
Get-ChildItem -Path C:\Windows\system32\* -Include *.msc, *.cpl | Sort-Object -Property Extension | Select-Object -Property Name | Format-Wide -Column 4
```

{% include figure image_path="/assets/images/mmscpl.png" alt="this is a placeholder image" caption="" %}

## 1. compmgmt.msc
Um sich einen Überblick über Ihren Computer zu verschaffen und Ihr System zu verwalten, öffnen Sie die Suche oder drücken Sie ALT + R und geben Sie compmgmt.msc ein.
{% include figure image_path="/assets/images/mmscpl02.png" alt="this is a placeholder image" caption="" %}
## 2. eventvwr.msc
Führen Sie zum Öffnen der Windows-Ereignisanzeige eventvwr.msc aus.
{% include figure image_path="/assets/images/mmscpl03.png" alt="this is a placeholder image" caption="" %}
