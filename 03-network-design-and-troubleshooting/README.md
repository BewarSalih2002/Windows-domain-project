# Network Design and Troubleshooting

## Ziel dieser Phase

Ziel dieser Phase war die Konzeption, Umsetzung und Analyse der Netzwerkinfrastruktur, welche die Grundlage für eine funktionierende Windows-Domäne bildet.  
Ein besonderer Fokus lag auf der Integration der **pfSense-Firewall**, der korrekten IP-Adressierung sowie der systematischen Fehleranalyse bei auftretenden Netzwerkproblemen.

---

## Ausgangslage

Nach der Installation aller Systeme bestand noch keine funktionierende Netzwerkkommunikation zwischen:

- pfSense
- Windows Server
- Windows 11 Client

Insbesondere Internetzugang, DNS-Auflösung und Erreichbarkeit des Domain Controllers mussten zuerst korrekt eingerichtet werden.

---

## Netzwerkarchitektur

### Rollenverteilung

- **pfSense**
  - Zentrales Gateway
  - NAT und Routing
  - Trennung von WAN und LAN

- **Windows Server**
  - Feste IP-Adresse
  - DNS-Server für die Domäne
  - Späterer Domain Controller

- **Windows 11 Client**
  - Dynamische IP-Adresse
  - Nutzung des Domain Controllers als DNS

---

## IP-Adressierung

### pfSense

- **WAN**
  - IP-Adresse: dynamisch (NAT / Internetzugang)

- **LAN**
  - IP-Adresse:     `192.168.10.1 /24`

---

### Windows Server

- IP-Adresse:       `192.168.10.10 /24`
- Standard-Gateway: `192.168.10.1`
- DNS-Server:       `192.168.10.10`

Der Server nutzt sich selbst als DNS-Server, was für Active Directory zwingend erforderlich ist.

---

### Windows 11 Client

- IP-Adresse: dynamisch (DHCP)
- Standard-Gateway: `192.168.10.1`
- DNS-Server:       `192.168.10.10`

---

## Typische Netzwerkprobleme und Analyse

### Kein Internetzugang

**Ursache:**
- Falsche Netzwerkschnittstelle (NAT statt internes Netzwerk)
- Fehlende Gateway-Konfiguration

**Lösung:**
- Korrekte Zuweisung der Netzwerkschnittstellen in VirtualBox
- Überprüfung der pfSense-WAN/LAN-Zuordnung

---

### DNS-Auflösung funktioniert nicht

**Symptom:**
- `ping google.com` schlägt fehl
- Namensauflösung nicht möglich

**Analyse:**
- DNS-Anfragen wurden nicht korrekt weitergeleitet
- Client verwendete falschen DNS-Server

**Lösung:**
- DNS-Server auf den Windows Server setzen
- DNS-Forwarder in pfSense prüfen

---

### Domain Controller nicht erreichbar

**Symptom:**
- Domänenbeitritt schlägt fehl
- Client findet die Domäne nicht

**Ursache:**
- Falscher DNS-Eintrag
- Server temporär im falschen Netzwerkmodus (NAT)

**Lösung:**
- Umstellung auf internes Netzwerk
- DNS-Konfiguration korrigiert
- Netzwerkverbindung erneut getestet

---

## Werkzeuge zur Fehleranalyse

Während dieser Phase wurden folgende Werkzeuge eingesetzt:

- `ipconfig`
- `ping`
- `nslookup`
- pfSense Webinterface
- VirtualBox Netzwerkübersicht

Diese Tools ermöglichten eine strukturierte und nachvollziehbare Analyse der Netzwerkprobleme.

---

## Ergebnis dieser Phase

Nach Abschluss dieser Phase:

- Funktionierte die Kommunikation zwischen allen Systemen
- War Internetzugang über pfSense verfügbar
- War die DNS-Auflösung korrekt eingerichtet
- Konnte der Windows Server zuverlässig erreicht werden

Damit war die Basis für den Aufbau der Active Directory Infrastruktur geschaffen.

---

## Übergang zur nächsten Phase

Nach erfolgreicher Netzwerkkonfiguration konnte mit der **Installation und Konfiguration von Active Directory und DNS** begonnen werden.  
Die nächste Phase behandelt den Aufbau der Domäne sowie die Strukturierung von Benutzern und Computern.
