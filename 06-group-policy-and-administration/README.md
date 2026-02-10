# Group Policy Management

## Ziel dieser Phase

Ziel dieser Phase war die zentrale Verwaltung von Benutzer- und Computereinstellungen über **Gruppenrichtlinien (Group Policy Objects, GPOs)**.  
Durch den Einsatz von GPOs können Sicherheit, Konfiguration und Benutzererlebnis zentral gesteuert werden.

---

## Voraussetzungen

- Funktionierende Active Directory Domäne
- Mindestens ein erfolgreicher Domänen-Client
- Klare OU-Struktur im Active Directory
- Anmeldung mit Domänen-Administrator

---

## Grundlagen zu Gruppenrichtlinien

### Was sind GPOs?

Gruppenrichtlinien sind Konfigurationsobjekte, die:

- Benutzerkonfigurationen
- Computerkonfigurationen

zentral steuern und automatisch auf Domänenmitglieder angewendet werden.

---

### Verknüpfung von GPOs

GPOs können verknüpft werden mit:

- Domäne
- Organisationseinheiten (OU)

❗ Best Practice:  
GPOs **nicht** direkt auf Domänenebene verknüpfen.

---

## Aufbau der OU-Struktur

Beispielhafte Struktur:

- `Users`
- `Clients`
- `Servers`

Clients und Benutzer wurden in die passenden OUs verschoben.

---

## Erstellen von Gruppenrichtlinien

### Beispiel 1: Passwort-Richtlinie

- Mindestlänge
- Komplexitätsanforderungen
- Ablaufzeit

Konfiguration über:
Computer Configuration → Policies → Windows Settings → Security Settings

---

### Beispiel 3: Desktop-Einstellungen

- Sperrbildschirm
- Hintergrundbild
- Taskleistenoptionen

---

## Anwendung und Überprüfung

### Richtlinien aktualisieren

Auf dem Client:
gpupdate /force

### Resultant Set of Policy (RSOP)

Zur Überprüfung aktiver Richtlinien:
rsop.msc

---

## Typische Fehler und Lösungen

### GPO wird nicht angewendet

**Ursache:**
- Client in falscher OU
- GPO nicht verknüpft

**Lösung:**
- OU prüfen
- Verknüpfung kontrollieren

---

### Verzögerte Anwendung

**Ursache:**
- Replikationsverzögerung
- Client nicht neu gestartet

**Lösung:**
- Neustart
- gpupdate ausführen

---

## Sicherheit und Best Practices

- Eine GPO = ein Zweck
- Klare Namenskonvention
- Test-GPOs zuerst auf Test-OU anwenden
- Dokumentation jeder Richtlinie

---

## Ergebnis dieser Phase

- Zentrale Verwaltung von Clients
- Einheitliche Sicherheitseinstellungen
- Reduzierter administrativer Aufwand

---

## Übergang zur nächsten Phase

In der nächsten Phase folgt **Troubleshooting & Fehleranalyse**, basierend auf real aufgetretenen Problemen.
