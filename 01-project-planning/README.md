# Project Planning

## Ziel der Planungsphase

Ziel dieser Phase war es, die technischen und organisatorischen Grundlagen für den Aufbau einer Windows-Domäneninfrastruktur zu definieren.  
Dabei wurde bewusst vor der technischen Umsetzung geplant, um spätere Fehlkonfigurationen zu vermeiden und ein strukturiertes Vorgehen sicherzustellen.

---

## Ausgangslage

Es bestand keine bestehende Infrastruktur.  
Das Projekt wurde vollständig neu in einer **virtuellen Umgebung** aufgebaut.

Rahmenbedingungen:
- Keine physische Hardware
- Keine bestehenden Netzwerke
- Fokus auf Lern- und Testumgebung
- Reproduzierbarkeit aller Schritte

---

## Projektumfang

Das Projekt umfasst folgende Kernkomponenten:

- Eine **pfSense-Firewall** als zentrales Gateway
- Einen **Windows Server** als Domain Controller
- Einen **Windows 11 Client** als Domänenmitglied
- Zentrale Benutzer- und Richtlinienverwaltung

Nicht Teil des Projekts:
- Hochverfügbarkeit
- Backup-Strategien
- Produktivbetrieb

---

## Architektur- und Designentscheidungen

### Virtualisierung

Alle Systeme werden mittels **VirtualBox** betrieben.  
Dies ermöglicht:
- Schnelles Erstellen und Zurücksetzen von Systemen
- Isolierte Testumgebung
- Plattformunabhängiges Arbeiten

---

### Netzwerkdesign

Die Netzwerkinfrastruktur basiert auf einer klaren Trennung der Rollen:

- **pfSense**
  - Routing zwischen Netzwerken
  - NAT-Konfiguration
  - Standard-Gateway für Server und Clients

- **Windows Server**
  - Feste IP-Adresse
  - DNS-Server für die Domäne
  - Active Directory Domain Services

- **Windows Client**
  - Dynamische IP-Adresse
  - DNS-Auflösung über Domain Controller

Diese Trennung orientiert sich an realen Unternehmensnetzwerken.

---

## Namens- und Adressierungskonzept

### Domänenname

- Interne Domäne: corp.local

Der Name wurde bewusst als interne Testdomäne gewählt und ist nicht öffentlich auflösbar.

---

### Namenskonventionen

Beispiele:
- Domain Controller: `DC01`
- Windows Client: `W11-CLIENT01`
- Benutzerkonten: `vorname.nachname`

Klare Namenskonventionen erleichtern die Administration und Fehlersuche.

---

## Zieldefinition

Am Ende des Projekts sollen folgende Ziele erreicht sein:

- Eine funktionierende Windows-Domäne
- Erfolgreicher Domänenbeitritt eines Clients
- Anmeldung mit Domänenbenutzer
- Zentrale Verwaltung mittels Gruppenrichtlinien
- Nachvollziehbare technische Dokumentation

---

## Ergebnis der Planungsphase

Nach Abschluss dieser Phase lag ein vollständiges Konzept vor, welches als Grundlage für alle weiteren Umsetzungsschritte diente.  
Durch die strukturierte Planung konnten spätere Probleme schneller analysiert und behoben werden.

---

## Übergang zur nächsten Phase

Auf Basis der Planungsphase konnte mit der **Installation der Systeme** begonnen werden.  
Die nächste Phase behandelt die Installation und Grundkonfiguration von Windows Server, Windows Client und pfSense.