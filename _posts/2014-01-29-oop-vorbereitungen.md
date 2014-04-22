---
layout: post
title: "Continuous Delivery Workshop Vorbereitungen"
date: 2014-01-30 9:30
comments: false
published: true
tags:
  - workshops
  - howtos
---

## Überblick

Diese Anleitung führt Sie durch die Installation für das Beispielprojekt zum 'Continuous Delivery' Workshop.

Während des Workshops deployen Sie eine Website über folgende Stages:

    dev -> ci -> qa -> prod


## Anforderungen

Für den Praxisteil des Workshops benötigen Sie einen Laptop und folgende Software:

* VirtualBox installieren: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
* Vagrant installieren: [http://www.vagrantup.com/downloads.html](http://www.vagrantup.com/downloads.html)
* Sorgen Sie für ausreichend Platz auf Ihrer Festplatte.
Wir empfehlen für den Workshop mindestens 2.5GB freien Festplattenspeicher.
* Stellen Sie sicher, dass Ihr USB-Port funktioniert.
Wir bieten das VM-Image auf einem USB-Stick an.
* Stellen Sie sicher, dass die Ports `8181` und `8153` frei sind.
  Wir benötigen diese Ports zum Aufrufen der Beispiel-Applikation auf der Virtuellen Maschine

### Dateistruktur

<pre>
    .
    ├── README.md                     Allgemeine Anleitungen
    ├── Vagrantfile                   Konfiguration zum Starten der VM
    ├── app                           Beispiel-Applikation für den Workshop
    └── vendor                        Externe Dateien von Drittherstellern
        ├── Vagrant-1.4.3.dmg
        ├── Vagrant_1.4.3.msi
        ├── vagrant_1.4.3_i686.deb
        ├── vagrant_1.4.3_i686.rpm
        ├── vagrant_1.4.3_x86_64.deb
        ├── vagrant_1.4.3_x86_64.rpm
        ├── VirtualBox-4.3.2-90405-Win.exe
        ├── VirtualBox-4.3.2-90405-OSX.dmg
        └── ubuntu-12.04.2-amd64.box
</pre>


## Das Beispielprojekt verwenden

* Verzeichnis `cd_workshop` vom USB Stick auf die lokale Festplatte kopieren
* USB Stick auswerfen und an den nächsten Teilnehmer geben
* VirtualBox und Vagrant installieren (falls noch nicht vorhanden)
* Terminal öffnen und in den Workshop Ordner wechseln
* Den Befehl `vagrant up` auf dem Terminal ausführen<br>
  Nun startet die Virtuelle Maschine.
* Öffnen Sie [http://localhost:8153/](http://localhost:8153/) im Browser um den CI-Server zu sehen
* Öffnen Sie [http://localhost:8181/](http://localhost:8181/), um eine Übersicht des Beispiel-Projektes zu sehen:
<pre>
http://localhost:8181/workshop-dev  - Current status in `app`
http://localhost:8181/workshop-ci   - Stage after build
http://localhost:8181/workshop-qa   - Stage after tests
http://localhost:8181/workshop-prod - Production
</pre>
* Verbinden Sie sich per SSH auf die Virtuelle Maschine mit `vagrant ssh`.<br>
  Sie sind nun mit dem Benutzer `vagrant` angemeldet und sollten sämtliche für den Workshop relevanten Befehle ausführen können.<br>
  Falls Sie `sudo` benötigen, können Sie ohne Passwort `root` Benutzer werden.
* Für den Fall, dass Sie einmal nach dem Passwort gefragt werden:
<pre>
Benutzer: vagrant
Passwort: vagrant
</pre>
* Wechseln Sie in das Verzeichnis `/vagrant/app`, führen Sie die Änderungen aus und pushen Sie diese in das Git-Repository:
<pre>
cd /vagrant/app

git add .
git commit -m "Update content"
git push origin master
</pre>
* Ihre Änderungen aktivieren den CI-Server. Wechseln Sie auf die Web-Oberfläche und schauen Sie dabei zu, wie das erste Paket gebaut wird: [http://localhost:8153/view/CD-Pipeline/](http://localhost:8153/view/CD-Pipeline/)
* Bauen Sie die Applikation weiter aus und wiederholen Sie den Schritt, wenn Sie mit den Änderungen zufrieden sind.<br>
  Sie können die Applikation über Ihren gewohnten Editor oder Ihre IDE auf dem Host bearbeiten und die Änderungen dann auf der Maschine pushen.
* Sobald Sie mit dem Ergebnis zufrieden sind, stoßen Sie das Deployment auf die weiteren Stages an.


## Häufige Fragen

F: Ist die VirtualBox zwingend notwendig oder kann man das auch mit VMWare Workstation arbeiten?<br>
A: Wir benutzen für den Workshop das kostenfreie VirtualBox. VMWare Workstation unterstützen wir nicht.
