# Active Directory Infrastructure

## Ziel dieser Phase

Ziel dieser Phase war der Aufbau einer zentralen Windows-Domäneninfrastruktur basierend auf **Active Directory Domain Services (AD DS)**.  
Der Windows Server wurde dabei als **Domain Controller**, **DNS-Server** und zentrale Verwaltungsinstanz für Benutzer, Computer und Gruppen eingesetzt.

---

## Voraussetzungen

Vor Beginn dieser Phase mussten folgende Bedingungen erfüllt sein:

- Funktionierende Netzwerkverbindung über pfSense
- Statische IP-Adresse auf dem Windows Server
- Korrekte DNS-Konfiguration (Server zeigt auf sich selbst)
- Erreichbarkeit des Servers aus dem internen Netzwerk

---

## Installation der Active Directory Domain Services

### Hinzufügen der Rolle

Auf dem Windows Server wurden folgende Rollen installiert:

- Active Directory Domain Services (AD DS)
- DNS-Server

Die Installation erfolgte über den **Server Manager**.

---

## Promotion zum Domain Controller

Nach der Rolleninstallation wurde der Server zu einem Domain Controller hochgestuft.

### Domänenkonfiguration

- Neue Gesamtstruktur erstellt
- Domänenname:          `lab.local`
- Funktionslevel:
- Windows Server 2019 (oder höher)
- DNS-Integration:
- Aktiviert

Der Server wurde nach Abschluss automatisch neu gestartet.

---

## DNS-Konfiguration

### Interner DNS

- DNS-Zonen wurden automatisch erstellt
- Forward Lookup Zone:  `lab.local`
- SRV-Records für Active Directory wurden korrekt registriert

---

### DNS-Forwarding

Damit Clients auch Internetadressen auflösen können:

- DNS-Forwarder auf öffentliche DNS-Server konfiguriert
- z.B.:
  ```
  8.8.8.8
  1.1.1.1
  ```

---

## Strukturierung von Active Directory

### Organisationseinheiten (OU)

Zur sauberen Verwaltung wurden folgende OUs erstellt:

- `Servers`
- `Clients`
- `Users`
- `Groups`

Diese Struktur bildet die Grundlage für spätere Gruppenrichtlinien.

---

### Benutzer und Gruppen

Beispielhafte Benutzerkonten:

- `admin.lab`
- `user01.lab`

Beispielhafte Gruppen:

- `IT-Admins`
- `Domain-Users`

Benutzer wurden gezielt Gruppen zugewiesen, um Rechte zentral zu steuern.

---

## Sicherheit und Best Practices

- Verwendung eines separaten Domänen-Administrators
- Kein tägliches Arbeiten mit dem eingebauten Administrator
- Klare OU-Struktur für zukünftige Erweiterungen
- DNS ausschliesslich über den Domain Controller

---

## Typische Probleme und Lösungen

### Active Directory Rolle nicht sichtbar

**Ursache:**
- Verbindung über SCONFIG ohne GUI

**Lösung:**
- Installation der Desktop Experience
- Alternativ Verwaltung über Remote Server Administration Tools (RSAT)

---

### DNS-Fehler nach Promotion

**Symptom:**
- Clients können Domäne nicht auflösen

**Lösung:**
- DNS-Serveradresse geprüft
- SRV-Records validiert
- Neustart des DNS-Dienstes

---

## Ergebnis dieser Phase

Nach Abschluss dieser Phase:

- Existiert eine funktionierende Windows-Domäne
- Arbeitet DNS korrekt mit Active Directory zusammen
- Können Benutzer, Gruppen und Computer zentral verwaltet werden

---

## Übergang zur nächsten Phase

In der nächsten Phase wird ein **Windows 11 Client** in die Domäne integriert und die Kommunikation zwischen Client und Domain Controller validiert.
