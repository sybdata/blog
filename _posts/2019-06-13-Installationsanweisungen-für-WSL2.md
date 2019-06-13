---
title: "Installieren von WSL 2"
date: 2019-06-13T15:37:30-04:00
categories:
  - Windows Subsystem for Linux
tags:
  - WLS
  - Linux kernel
---
Führen Sie zum Installieren und nutzen Sie WSL 2 die folgenden Schritte aus:

   * Aktivieren Sie die "VM-Plattform" optionale Komponente
   * Legen Sie eine Distribution, die durch die WSL-2, die über die Befehlszeile unterstützt werden
   * Überprüfen Sie, welche Versionen von WSL Ihre Distributionen verwenden

Aktivieren Sie die "VM-Plattform" optionale Komponente

Öffnen Sie PowerShell als Administrator, und führen Sie aus:

Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform

Nachdem diese Änderungen aktiviert sind, müssen Sie den Computer neu starten.
Legen Sie eine Distribution, die durch die WSL-2, die über die Befehlszeile unterstützt werden

In PowerShell ausführen:

wsl --set-version <Distro> 2

und achten Sie darauf, ersetzen Sie dies <Distro> durch den tatsächlichen Namen von Ihrer Distribution. (Sie finden diese mit dem Befehl: wsl -l). Sie können an WSL 1 auf jederzeit ändern, indem den gleichen Befehl wie oben ausführen, aber ersetzen die "2" mit "1".

Darüber hinaus sollten Sie WSL 2 Stellen Sie die Standardarchitektur können Sie mit diesem Befehl dafür:

wsl --set-default-version 2

Dies veranlasst alle neuen-Distribution, die Sie installieren, als eine Distribution WSL 2 initialisiert.
Beim Überprüfen, welche Versionen von WSL Ihre Distribution verwenden, sind abgeschlossen

So überprüfen, welche Versionen von WSL jede Distribution verwendet den folgenden Befehl verwenden:

wsl --list --verbose oder wsl -l -v

Die Distribution, der Sie oben ausgewählt haben, sollte nun eine "2" in der Spalte "Version" anzeigen. Nun, da Sie danach können Sie beim Einstieg in Ihre WSL-2-Distribution!
