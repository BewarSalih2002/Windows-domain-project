# Windows Domain Infrastructure Project

## Projektübersicht

Dieses Projekt dokumentiert den vollständigen Aufbau einer **Windows-Domäneninfrastruktur** in einer virtualisierten Umgebung.  
Die Umgebung besteht aus einem **Windows Server als Domain Controller**, einem **Windows 11 Client** sowie einer **pfSense-Firewall** zur Netzwerksegmentierung, zum Routing und für den Internetzugang.

Der Fokus liegt auf einer **realitätsnahen Unternehmensumgebung**, wie sie in der Praxis von Systemadministratoren aufgebaut und betrieben wird.

---

## Projektziele

- Planung und Umsetzung einer strukturierten Windows-Domäne
- Einsatz von **pfSense** als zentrale Firewall und Router
- Aufbau eines **Domain Controllers mit Active Directory und DNS**
- Integration eines **Windows 11 Clients in die Domäne**
- Verständnis von **Netzwerkdesign, NAT, DNS und Routing**
- Zentrale Verwaltung mittels **Group Policies**
- Vollständige und nachvollziehbare **technische Dokumentation**

---

## Infrastruktur-Übersicht

Die Umgebung besteht aus folgenden Komponenten:

- **pfSense Firewall**
  - Routing zwischen internen Netzwerken
  - NAT-Konfiguration
  - Gateway für Server und Clients
  - Zentrales Netzwerk-Troubleshooting

- **Windows Server**
  - Active Directory Domain Services (AD DS)
  - DNS-Server
  - Domain Controller
  - Verwaltung von Benutzern, Gruppen und Computern

- **Windows 11 Client**
  - Domänenbeitritt
  - Anmeldung mit Domänenbenutzer
  - Anwendung von Gruppenrichtlinien

Alle Systeme laufen in einer **virtuellen Testumgebung**.

---

## Verwendete Technologien

- **VirtualBox** (Virtualisierung)
- **pfSense**
  - Firewall
  - NAT
  - Routing
  - Netzwerk-Gateway
- **Windows Server**
  - Active Directory Domain Services (AD DS)
  - DNS
  - Group Policy Management
- **Windows 11**
- **Remote Desktop (RDP)**
- **PowerShell**
- **sconfig**

---

## Projektstruktur

Die Dokumentation ist in logisch aufgebaute Kapitel unterteilt.  
Jeder Ordner enthält eine eigene `README.md` mit Erklärungen, Konfigurationsschritten und Problemlösungen.


windows-domain-project/
│
├── README.md
│
├── project-planning/
│   └── README.md
│
├── system-installation/
│   └── README.md
│
├── network-design-and-troubleshooting/
│   └── README.md
│
├── active-directory-infrastructure/
│   └── README.md
│
├── client-domain-integration/
│   └── README.md
│
└── group-policy-and-administration/
    └── README.md

---

## Inhaltliche Schwerpunkte

- Planung der Gesamtarchitektur (Server, Client, Firewall)
- Installation und Grundkonfiguration von pfSense
- Netzwerkdesign (NAT vs. internes Netzwerk)
- Fehleranalyse bei Netzwerkproblemen
- Installation und Konfiguration von Windows Server
- Aufbau von Active Directory und DNS
- Domänenbeitritt eines Windows-Clients
- Verwaltung von Benutzern, Gruppen und Computern
- Einsatz von Gruppenrichtlinien zur zentralen Administration

---

## Typische Herausforderungen und Lösungen

- NAT-Fehlkonfigurationen zwischen pfSense und Windows Server
- DNS-Probleme beim Domänenbeitritt
- Client kann Domain Controller nicht erreichen
- Anmeldung an der Domäne schlägt fehl
- Unterschied zwischen lokaler Anmeldung und Domänenanmeldung

Alle Probleme wurden analysiert, dokumentiert und nachhaltig gelöst.

---

## Lernresultat

Durch dieses Projekt wurden praxisnahe Kenntnisse in folgenden Bereichen aufgebaut:

- Windows-Domäneninfrastrukturen
- Netzwerkdesign mit pfSense
- DNS und Active Directory Abhängigkeiten
- Systematisches Troubleshooting
- Strukturierte Projektdokumentation
- Arbeiten nach Best Practices aus der IT-Systemadministration

---

## Hinweise

- Die Umgebung wurde ausschliesslich zu Lern- und Testzwecken erstellt
- Alle Konfigurationen sind reproduzierbar
- Das Projekt eignet sich als Referenz für Einsteiger und Junior System Engineers

---

## Autor

**Bewar Salih**  
Windows & Netzwerk Infrastruktur Projekt
