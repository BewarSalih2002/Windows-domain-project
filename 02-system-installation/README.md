# System Installation

## Ziel der Installationsphase

Ziel dieser Phase war die Installation und Grundkonfiguration aller benötigten Systeme, welche als Basis für die spätere Domäneninfrastruktur dienen.  
Dabei wurde sichergestellt, dass alle Systeme stabil laufen und korrekt für den weiteren Ausbau vorbereitet sind.

---

## Übersicht der installierten Systeme

In dieser Phase wurden folgende Systeme installiert:

- **pfSense Firewall**
- **Windows Server**
- **Windows 11 Client**

Alle Systeme wurden in einer virtualisierten Umgebung betrieben.

---

## Virtualisierungsumgebung

### VirtualBox

Als Virtualisierungsplattform wurde **VirtualBox** eingesetzt.

Gründe für diese Wahl:
- Kostenlose Nutzung
- Unterstützung mehrerer Betriebssysteme
- Einfache Netzwerkverwaltung

---

## Installation der pfSense Firewall

### Vorbereitung

- Download der pfSense ISO-Datei
- Erstellung einer neuen virtuellen Maschine
- Zuweisung von zwei Netzwerkadaptern:
  - WAN
  - LAN

### Installation

- Start der VM mit pfSense ISO
- Standard-Installation mit Voreinstellungen
- Auswahl des Dateisystems
- Abschluss der Installation und Neustart

### Ergebnis

- pfSense erfolgreich installiert
- Konsolenmenü verfügbar
- Netzwerkinterfaces initial konfiguriert

---

## Installation des Windows Servers

### Vorbereitung

- Download der Windows Server ISO
- Erstellung einer virtuellen Maschine
- Aktivierung von UEFI
- Zuweisung von ausreichend RAM und CPU

### Installation

- Start der VM mit Windows Server ISO
- Auswahl der Server-Edition
- Installation im Core-Modus
- Vergabe eines Administrator-Passworts

### Grundkonfiguration

- Anmeldung über Konsole
- Nutzung von `sconfig` zur:
  - Umbenennung des Servers
  - Konfiguration der Netzwerkeinstellungen
  - Aktivierung von Remote Desktop

### Ergebnis

- Windows Server erfolgreich installiert
- Server bereit für weitere Rollen

---

## Installation des Windows 11 Clients

### Vorbereitung

- Download der Windows 11 ISO
- Erstellung einer virtuellen Maschine
- Aktivierung von UEFI
- Deaktivierung von Secure Boot
- Anpassung der Systemanforderungen (TPM)

### Installation

- Start der VM mit Windows 11 ISO
- Auswahl der Edition **Windows 11 Pro**
- Abschluss der Installation

### Grundkonfiguration

- Lokale Benutzeranmeldung
- Netzwerkverbindung überprüfen
- Vorbereitung für Domänenbeitritt

### Ergebnis

- Windows 11 Client erfolgreich installiert
- System bereit für Integration in die Domäne

---

## Herausforderungen während der Installation

Während dieser Phase traten folgende Herausforderungen auf:

- Probleme mit UEFI- und Secure-Boot-Einstellungen
- Netzwerkadapter falsch zugewiesen
- Windows 11 Installationsanforderungen in virtueller Umgebung

Alle Probleme konnten durch Anpassung der VM-Konfiguration und gezielte Fehleranalyse behoben werden.

---

## Ergebnis der Installationsphase

Nach Abschluss dieser Phase standen drei lauffähige Systeme zur Verfügung, welche als Grundlage für die weitere Netzwerkkonfiguration und den Aufbau der Domäneninfrastruktur dienten.

---

## Übergang zur nächsten Phase

Nach erfolgreicher Installation aller Systeme wurde mit der **Netzwerkkonfiguration und Fehleranalyse** begonnen.  
Die nächste Phase behandelt das Netzwerkdesign, die IP-Adressierung sowie das Troubleshooting von Verbindungsproblemen.