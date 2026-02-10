# Client Integration (Windows 11)

## Ziel dieser Phase

Ziel dieser Phase war die Integration eines **Windows 11 Clients** in die bestehende **Active Directory Domäne**.  
Der Client sollte sich korrekt im internen Netzwerk befinden, den Domain Controller erreichen und eine erfolgreiche Domänenanmeldung ermöglichen.

---

## Voraussetzungen

Vor dem Domänenbeitritt mussten folgende Punkte erfüllt sein:

- Funktionierende pfSense Firewall
- Aktive Windows-Domäne (`lab.local`)
- Windows Server als Domain Controller erreichbar
- DNS des Clients zeigt **ausschliesslich** auf den Domain Controller
- Windows 11 **Pro** (Home ist nicht domänenfähig)

---

## Installation des Windows 11 Clients

### Auswahl der Edition

Für den Domänenbeitritt wurde **Windows 11 Pro** verwendet.

**Begründung:**
- Nur Pro / Education / Enterprise unterstützen Active Directory
- Windows 11 Home ist ungeeignet

---

### Umgehung der Hardwareprüfung (Lab-Umgebung)

Da es sich um eine virtuelle Lernumgebung handelt, wurde die Hardwareprüfung umgangen:

- Anpassung über `regedit` während der Installation
- Aktivierung von:
  - TPM Bypass
  - Secure Boot Bypass

---

## Netzwerkkonfiguration des Clients

### IP-Konfiguration

Der Client erhielt seine IP-Adresse über DHCP von pfSense.

Beispiel:
IP-Adresse:     `192.168.10.100`
Subnetz:        `255.255.255.0`
Gateway:        `192.168.10.1`
DNS:            `192.168.10.10` (Domain Controller)

⚠️ **Wichtig:**  
Der DNS darf **nicht** auf pfSense oder öffentliche Server zeigen.

---

## Domänenbeitritt

### Beitritt zur Domäne

Pfad:
Einstellungen → System → Info → Domäne oder Arbeitsgruppe

Domänenname:    `lab.local`

---

### Anmeldeinformationen

Verwendeter Benutzer: LAB\Administrator
Nach erfolgreichem Beitritt wurde der Client neu gestartet.

---

## Anmeldung an der Domäne

### Domänenanmeldung vs. lokale Anmeldung

- **Domänenanmeldung:**
LAB\user01

- **Lokale Anmeldung:**
CLIENT-PC\user

⚠️ Häufige Fehlerquelle:
- Falscher Kontext bei der Anmeldung

---

## Überprüfung der Integration

Erfolgreiche Integration wurde geprüft durch:

- Client erscheint in Active Directory
- Anmeldung mit Domänenbenutzer möglich
- DNS-Auflösung funktioniert
- Internetzugang vorhanden

---

## Typische Probleme und Lösungen

### Client kann Domain Controller nicht finden

**Ursache:**
- Falscher DNS-Server

**Lösung:**
- DNS manuell auf Domain Controller setzen

---

### Domänenbeitritt schlägt fehl

**Ursache:**
- Windows 11 Home
- Zeitabweichung
- DNS falsch

**Lösung:**
- Edition prüfen
- Uhrzeit synchronisieren
- DNS prüfen

---

### Anmeldung schlägt fehl

**Ursache:**
- Benutzer nicht berechtigt
- Falsche OU
- Tippfehler bei Domäne

**Lösung:**
- Benutzer prüfen
- Gruppenmitgliedschaften kontrollieren

---

## Ergebnis dieser Phase

Nach Abschluss dieser Phase:

- Ist der Windows 11 Client Mitglied der Domäne
- Können Domänenbenutzer sich anmelden
- Funktioniert die Kommunikation zwischen Client und Server stabil

---

## Übergang zur nächsten Phase

In der nächsten Phase werden **Gruppenrichtlinien (GPOs)** eingesetzt, um Clients zentral zu verwalten.

