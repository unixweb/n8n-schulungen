# n8n Schulungsprogramm - 6 Wochen (48 Stunden)

## Programm-Uebersicht
Dieses Schulungsprogramm fuehrt absolute Beginner in 6 Wochen zur eigenstaendigen Entwicklung von n8n-Workflows.
**Format:** 4 Einheiten a 2 Stunden pro Woche = 8 Stunden/Woche

---

## Woche 1: Grundlagen & Erste Schritte

### Lernziele
- n8n-Oberflaeche verstehen und navigieren
- Erste einfache Workflows erstellen
- Grundlegende Nodes kennenlernen
- Konzept von Triggers und Actions verstehen

---

### Einheit 1.1: Einfuehrung & Setup (2 Stunden)

**Theorie (45 Min):**
- Was ist n8n? Workflow-Automation und Low-Code Konzept
- Anwendungsfaelle: E-Mail-Automation, API-Integration, Daten-Synchronisation
- n8n Cloud vs. Self-Hosted
- Oberflaeche: Canvas, Nodes, Connections, Execution

**Praxis (75 Min):**
- n8n-Account einrichten und erste Anmeldung
- Canvas erkunden: Zoom, Navigation, Ansichten
- Node hinzufuegen (+ Button), verbinden, loeschen, duplizieren
- Erster Workflow: Manual Trigger  Set Node  grundlegende Ausgabe
- Workflow ausfuehren (Execute) und Ergebnisse im Output pruefen
- Workflow speichern und umbenennen

**Hausaufgabe:**
Erstellen Sie einen Workflow mit Manual Trigger und Set Node, der Ihre persoenlichen Daten (Name, Stadt, Hobbies) als JSON ausgibt.

---

### Einheit 1.2: Trigger-Konzepte (2 Stunden)

**Theorie (30 Min):**
- Trigger-Typen: Manual, Schedule, Webhook, App-Trigger
- Datenfluss: Wie Daten von Node zu Node fliessen
- JSON-Datenstruktur verstehen
- Execution-Log lesen und interpretieren

**Praxis (90 Min):**
- **Workflow 1:** Schedule Trigger (taeglich 9 Uhr)  Set Node  Daten vorbereiten
- **Workflow 2:** Webhook Trigger  Set Node  Webhook Response Node
- Webhook testen mit Browser oder Postman/curl
- Execution History ansehen und verstehen

**Hausaufgabe:**
Erstellen Sie einen Webhook, der einen Namen als Parameter empfaengt und "Hallo [Name]!" zurueckgibt.

---

### Einheit 1.3: HTTP Requests & externe Daten (2 Stunden)

**Theorie (30 Min):**
- HTTP Request Node Grundlagen
- GET-Requests: Daten von APIs abrufen
- Oeffentliche APIs ohne Authentifizierung
- Response-Daten verstehen

**Praxis (90 Min):**
- **Workflow 1:** HTTP Request zu oeffentlicher API (z.B. JSONPlaceholder, OpenMeteo)
- Daten inspizieren und verstehen
- **Workflow 2:** Schedule  HTTP Request (Wetter-API)  Set Node (Daten extrahieren)
- Mehrere HTTP Requests verketten
- Fehlerfaelle beobachten (404, 500)

**Hausaufgabe:**
Erstellen Sie einen Workflow, der Wetterdaten fuer Ihre Stadt abruft und die Temperatur extrahiert.

---

### Einheit 1.4: Email-Integration & erster kompletter Workflow (2 Stunden)

**Theorie (20 Min):**
- Email Node (SMTP, Gmail, Outlook)
- Credentials einrichten
- Email-Felder: To, Subject, Body, HTML

**Praxis (100 Min):**
- Email-Credentials konfigurieren (Gmail App-Passwort oder SMTP)
- **Workflow 1:** Manual Trigger  Email senden
- **Workflow 2:** Schedule  HTTP Request (Quote API)  Email mit Quote
- HTML-Formatierung in E-Mails
- Kompletter Workflow: Taegliche Wettervorhersage per E-Mail

**Hausaufgabe:**
Erstellen Sie einen Workflow, der taeglich um 8 Uhr eine motivierende Quote von einer API abruft und Ihnen per E-Mail sendet.

---

## Woche 2: Datenverarbeitung & Transformation

### Lernziele
- Daten filtern, transformieren und strukturieren
- Expressions und Variablen verstehen
- Bedingte Logik implementieren
- Fehlerbehandlung kennenlernen

---

### Einheit 2.1: Set Node & Daten-Manipulation (2 Stunden)

**Theorie (30 Min):**
- Set Node im Detail: Felder hinzufuegen, aendern, entfernen
- JSON-Struktur: Objekte und Arrays
- Expressions: `{{ $json.fieldname }}`
- Auf vorherige Node-Daten zugreifen

**Praxis (90 Min):**
- Set Node: Neue Felder hinzufuegen
- Felder umbenennen und kombinieren
- Nested Data: Auf verschachtelte Felder zugreifen (`{{ $json.user.name }}`)
- **Workflow:** HTTP Request  Set Node (Daten bereinigen und neu strukturieren)
- String-Operationen: `.toUpperCase()`, `.toLowerCase()`, String-Concatenation

**Hausaufgabe:**
API-Daten abrufen und mit Set Node umstrukturieren: Nur relevante Felder behalten und neue berechnete Felder hinzufuegen.

---

### Einheit 2.2: Filter & IF Node (2 Stunden)

**Theorie (25 Min):**
- Filter Node: Bedingungen definieren
- IF Node: Workflow-Verzweigungen
- Vergleichsoperatoren: equals, contains, groesser/kleiner
- Boolean-Logik: AND, OR

**Praxis (95 Min):**
- **Workflow 1:** HTTP Request  Filter Node (nur bestimmte Eintraege)
- **Workflow 2:** Webhook  IF Node  zwei verschiedene Actions
- Bedingungen kombinieren (AND/OR)
- **Workflow 3:** Daten abrufen  Filter  IF  Email oder Log

**Hausaufgabe:**
Erstellen Sie einen Workflow, der Nachrichten von einer API abruft, nach Prioritaet filtert und nur dringende Meldungen per E-Mail versendet.

---

### Einheit 2.3: Code Node & JavaScript Basics (2 Stunden)

**Theorie (35 Min):**
- Code Node: Wann verwenden?
- JavaScript Grundlagen: Variablen, Schleifen, Funktionen
- Zugriff auf Input-Daten: `items`
- Output formatieren: `return items`

**Praxis (85 Min):**
- Einfache Code Node: Daten transformieren
- Array-Operationen: `.map()`, `.filter()`, `.reduce()`
- **Workflow 1:** HTTP Request  Code Node (Daten berechnen)  Output
- **Workflow 2:** Datum/Zeit-Berechnungen mit JavaScript Date
- Debugging: `console.log()` nutzen

**Hausaufgabe:**
Verwenden Sie Code Node, um aus einer Liste von Zahlen den Durchschnitt zu berechnen und zu formatieren.

---

### Einheit 2.4: Fehlerbehandlung & Merge (2 Stunden)

**Theorie (30 Min):**
- Error Workflow: Fehler abfangen
- Try-Catch Konzept
- Merge Node: Daten zusammenfuehren
- Split In Batches: Grosse Datenmengen verarbeiten

**Praxis (90 Min):**
- Error Trigger erstellen und verknuepfen
- **Workflow mit Fehlerbehandlung:** API-Call  bei Fehler Alternative
- Merge Node: Zwei Datenquellen kombinieren
- Split In Batches fuer Loop-Simulation
- **Praxis-Workflow:** Multi-Source Daten  Merge  Einheitliche Verarbeitung

**Hausaufgabe:**
Workflow mit zwei API-Calls, deren Ergebnisse gemerged und dann gemeinsam verarbeitet werden. Fehlerbehandlung implementieren.

---

## Woche 3: API-Integrationen & Authentifizierung

### Lernziele
- REST-APIs verstehen und einbinden
- Credentials & OAuth konfigurieren
- Gaengige Dienste integrieren (Google, Slack, etc.)
- POST/PUT Requests mit Daten senden

---

### Einheit 3.1: REST-API Grundlagen (2 Stunden)

**Theorie (40 Min):**
- REST-Prinzipien: GET, POST, PUT, DELETE
- API-Authentifizierung: API-Key, Bearer Token
- Headers setzen: Content-Type, Authorization
- Request Body: JSON-Daten senden

**Praxis (80 Min):**
- HTTP Request Node: POST Request mit JSON-Body
- Custom Headers konfigurieren
- API-Key Authentifizierung
- **Workflow:** Daten von einer API abrufen (GET) und zu anderer API senden (POST)
- Response-Codes interpretieren (200, 400, 401, 500)

**Hausaufgabe:**
Erstellen Sie einen Workflow, der Daten von JSONPlaceholder abruft und an webhook.site weiterleitet.

---

### Einheit 3.2: Credentials & OAuth (2 Stunden)

**Theorie (35 Min):**
- Credentials in n8n verwalten
- API-Key vs. OAuth 2.0
- OAuth-Flow verstehen
- Sicherheit: Credentials niemals im Workflow hartcoden

**Praxis (85 Min):**
- API-Key Credential erstellen
- OAuth2 Credential konfigurieren (z.B. Google)
- **Workflow:** HTTP Request mit verschiedenen Auth-Methoden
- Credentials wiederverwenden
- Troubleshooting: Auth-Fehler diagnostizieren

**Hausaufgabe:**
Richten Sie OAuth fuer einen Google-Service ein und erstellen Sie einen Test-Workflow.

---

### Einheit 3.3: Google Sheets Integration (2 Stunden)

**Theorie (20 Min):**
- Google Sheets Node Overview
- Operationen: Read, Append, Update, Lookup
- Sheet ID und Range verstehen

**Praxis (100 Min):**
- Google Sheets Credentials einrichten
- **Workflow 1:** Daten aus Sheet lesen
- **Workflow 2:** Neue Zeile zu Sheet hinzufuegen (Append)
- **Workflow 3:** Bestehende Zeile updaten (Lookup + Update)
- **Praxis-Projekt:** Formular-Webhook  Daten validieren  Google Sheets schreiben

**Hausaufgabe:**
Erstellen Sie einen Workflow, der taeglich Daten von einer API in ein Google Sheet schreibt.

---

### Einheit 3.4: Slack Integration (2 Stunden)

**Theorie (25 Min):**
- Slack Node: Messages, Channels, Users
- Slack App erstellen und Bot Token
- Webhooks vs. Bot Token
- Formatting: Markdown, Mentions, Emojis

**Praxis (95 Min):**
- Slack App erstellen und in Workspace installieren
- Credentials in n8n konfigurieren
- **Workflow 1:** Message in Channel posten
- **Workflow 2:** Schedule  Daten aggregieren  Slack Report
- **Workflow 3:** Webhook empfangen  Bedingung pruefen  Slack Alert
- Interactive Messages (Buttons) ausprobieren

**Hausaufgabe:**
Erstellen Sie ein Alert-System, das bei bestimmten Bedingungen (z.B. Wert ueber Schwelle) eine Slack-Nachricht sendet.

---

## Woche 4: Datenbanken & Persistenz

### Lernziele
- Mit SQL-Datenbanken arbeiten (PostgreSQL/MySQL)
- CRUD-Operationen implementieren
- Daten-Synchronisation zwischen Services
- Duplikate vermeiden und Datenintegritaet sichern

---

### Einheit 4.1: SQL-Datenbanken Grundlagen (2 Stunden)

**Theorie (45 Min):**
- SQL Basics: SELECT, INSERT, UPDATE, DELETE
- WHERE, ORDER BY, LIMIT
- n8n Postgres/MySQL Node
- Datenbankverbindung konfigurieren
- Sicherheit: SQL-Injection vermeiden

**Praxis (75 Min):**
- Testdatenbank einrichten (z.B. PostgreSQL auf Cloud)
- Credentials in n8n konfigurieren
- **Workflow 1:** SELECT Query - Daten auslesen
- **Workflow 2:** INSERT - Neue Zeile einfuegen
- WHERE-Bedingungen in Queries
- Parametrisierte Queries mit Expressions

**Hausaufgabe:**
Erstellen Sie eine Datenbank-Tabelle und einen Workflow zum Auslesen und Einfuegen von Testdaten.

---

### Einheit 4.2: CRUD-Operationen (2 Stunden)

**Theorie (25 Min):**
- UPDATE und DELETE Queries
- JOIN-Operationen (Basic)
- Transactions und Atomicity
- Error-Handling bei DB-Operationen

**Praxis (95 Min):**
- **Workflow 1:** Daten auslesen  Modifizieren  UPDATE
- **Workflow 2:** Daten loeschen (DELETE mit WHERE)
- **Workflow 3:** Komplexer Flow: Webhook  Validierung  INSERT/UPDATE  Response
- Error-Handling bei DB-Fehlern
- Duplicate Key Errors behandeln

**Hausaufgabe:**
Workflow, der prueft, ob Eintrag existiert (SELECT), dann UPDATE oder INSERT durchfuehrt (Upsert-Logik).

---

### Einheit 4.3: Daten-Synchronisation (2 Stunden)

**Theorie (30 Min):**
- Sync-Strategien: Full vs. Incremental
- Timestamps fuer Change Detection
- Deduplizierung: Eindeutige IDs verwenden
- Konfliktaufloesung

**Praxis (90 Min):**
- **Workflow:** Google Sheets  Datenbank Sync
- Timestamps nutzen: `last_modified` checken
- Nur geaenderte Daten synchronisieren
- **Workflow:** API  DB (Duplikat-Check vor INSERT)
- Batch-Processing fuer grosse Datenmengen

**Hausaufgabe:**
Erstellen Sie einen inkrementellen Sync von Google Sheets zu PostgreSQL (nur neue/geaenderte Zeilen).

---

### Einheit 4.4: NoSQL & Praxis-Projekt (2 Stunden)

**Theorie (20 Min):**
- NoSQL Konzepte (MongoDB)
- Wann SQL vs. NoSQL?
- MongoDB Node in n8n

**Praxis (100 Min):**
- MongoDB Atlas Setup (kostenlos)
- MongoDB Credentials in n8n
- Basic Operations: Insert, Find, Update
- **Praxis-Projekt:** Kompletter Data-Pipeline
  - Webhook empfangen (Formular-Submit)
  - Daten validieren
  - In Datenbank speichern
  - Bestaetigungs-Email senden
  - Slack-Benachrichtigung

**Hausaufgabe:**
Erweitern Sie das Praxis-Projekt um Error-Handling und Logging in separate DB-Tabelle.

---

## Woche 5: Fortgeschrittene Workflows & Best Practices

### Lernziele
- Komplexe Workflows strukturieren
- Sub-Workflows nutzen
- Performance optimieren
- Testing und Debugging-Strategien

---

### Einheit 5.1: Workflow-Architektur (2 Stunden)

**Theorie (40 Min):**
- Design Patterns fuer Workflows
- Modularitaet: Ein Workflow = Eine Aufgabe
- Execute Workflow Node
- Wiederverwendbarkeit und Wartbarkeit
- Dokumentation mit Sticky Notes

**Praxis (80 Min):**
- Sub-Workflows erstellen (z.B. "Validate Data", "Send Notification")
- Execute Workflow Node verwenden
- **Workflow:** Master-Workflow ruft 3 Sub-Workflows auf
- Parameter an Sub-Workflows uebergeben
- Return-Werte von Sub-Workflows verarbeiten

**Hausaufgabe:**
Refactoren Sie einen bestehenden komplexen Workflow in mehrere Sub-Workflows.

---

### Einheit 5.2: Loops & Batch-Processing (2 Stunden)

**Theorie (30 Min):**
- Split In Batches Node im Detail
- Loop-Konzepte in n8n
- Wann Batching nutzen?
- Rate-Limiting und API-Beschraenkungen

**Praxis (90 Min):**
- **Workflow:** 1000 Eintraege in Batches a 50 verarbeiten
- Loop-Node mit Split In Batches
- Wait-Time zwischen Batches (Rate Limiting)
- **Workflow:** CSV Import  Split In Batches  API Calls  Ergebnisse sammeln
- Progress-Tracking mit Variablen

**Hausaufgabe:**
Verarbeiten Sie eine grosse Datenmenge (100+ Eintraege) mit Batch-Processing und Error-Handling.

---

### Einheit 5.3: Error-Handling & Monitoring (2 Stunden)

**Theorie (35 Min):**
- Error Workflow Advanced
- Retry-Strategien
- Logging Best Practices
- Monitoring und Alerting
- Execution-Limits verstehen

**Praxis (85 Min):**
- Error Workflow mit detailliertem Logging
- **Workflow:** Try-Catch Pattern mit Retry-Logik
- Error-Daten in Datenbank loggen
- **Monitoring-Workflow:** Schedule  Status-Checks  Alert bei Problemen
- Execution History analysieren

**Hausaufgabe:**
Implementieren Sie ein Monitoring-System, das kritische Workflows ueberwacht und bei Fehlern benachrichtigt.

---

### Einheit 5.4: Performance & Best Practices (2 Stunden)

**Theorie (40 Min):**
- Performance-Optimierung
- Queue-Mode vs. Regular Mode
- Memory-Management
- Best Practices Zusammenfassung:
  - Naming Conventions
  - Dokumentation
  - Credentials-Management
  - Testing-Strategien

**Praxis (80 Min):**
- Performance-Vergleich: Mit/ohne Batching
- Workflow-Review: Bestehende Workflows optimieren
- **Praxis:** Refactoring-Session
- Code-Review simulieren
- Workflows dokumentieren mit Sticky Notes

**Hausaufgabe:**
Reviewen und optimieren Sie Ihre bisherigen Workflows nach Best Practices.

---

## Woche 6: Praxisprojekte & Eigenstaendige Entwicklung

### Lernziele
- Eigenstaendige Workflow-Planung von Anforderung bis Implementierung
- Vollstaendige Use-Case Umsetzung
- Troubleshooting ohne Hilfe
- Praesentation und Dokumentation

---

### Einheit 6.1: Projektplanung (2 Stunden)

**Theorie (45 Min):**
- Von Anforderung zu Workflow: Systematischer Ansatz
- User Stories in n8n uebersetzen
- Workflow-Diagramme skizzieren (Papier/Whiteboard)
- Projekt-Checkliste:
  - Inputs/Outputs definieren
  - Benoetigte Integrationen
  - Error-Szenarien
  - Testing-Plan

**Praxis (75 Min):**
- Projektauswahl aus vorbereiteten Use-Cases (siehe unten)
- Anforderungsanalyse durchfuehren
- Workflow-Architektur planen und skizzieren
- Benoetigte Credentials und APIs identifizieren
- Meilensteine festlegen

**Projekt-Optionen:**
1. **E-Commerce Automation:** Bestellung  Lagerpruefung  Rechnung  Multi-Channel Benachrichtigung
2. **Content-Aggregation:** RSS/APIs  Filterung  Kategorisierung  Newsletter
3. **Onboarding-System:** Formular  User-Anlage (DB)  Task-Generierung  Welcome-Flow
4. **Data-Pipeline:** Multi-Source  ETL  Data Warehouse  Reporting

---

### Einheit 6.2: Implementierung Teil 1 (2 Stunden)

**Praxis (120 Min):**
- Projekt-Implementierung starten
- Core-Workflow aufbauen
- Integrationen konfigurieren
- Erste Tests durchfuehren
- Probleme identifizieren und dokumentieren
- Peer-Review: Kurzes Feedback von anderen Teilnehmern

**Trainer-Unterstuetzung:**
- Individuelle Hilfe bei Blockern
- Code-Review auf Anfrage
- Best-Practice Hinweise

---

### Einheit 6.3: Implementierung Teil 2 & Testing (2 Stunden)

**Praxis (120 Min):**
- Projekt fertigstellen
- Error-Handling implementieren
- Sub-Workflows erstellen (falls sinnvoll)
- Umfassendes Testing:
  - Happy Path
  - Error Cases
  - Edge Cases
- Performance-Check
- Dokumentation erstellen:
  - Sticky Notes im Workflow
  - README mit Setup-Anleitung
  - Workflow-Beschreibung

---

### Einheit 6.4: Praesentation & Review (2 Stunden)

**Praesentationen (90 Min):**
- Jeder Teilnehmer praesentiert sein Projekt (10-15 Min):
  - Problem/Use-Case
  - Loesungsansatz
  - Workflow-Demo (Live!)
  - Herausforderungen & Learnings
  - Q&A

**Abschluss (30 Min):**
- Feedback-Runde
- Key Learnings zusammenfassen
- Naechste Schritte & Ressourcen
- Community & Weiterbildung
- Zertifikat-Uebergabe (optional)

---

## Abschlussprojekt-Anforderungen

**Minimum-Kriterien:**
- Mindestens 7 verschiedene Nodes
- Minimum 2 externe Integrationen (API/Service)
- Error-Handling implementiert
- Daten-Transformation/Filterung
- Mindestens 1 Sub-Workflow ODER komplexe Logik (IF/Loop)
- Dokumentation (Sticky Notes, README)
- Funktionsfaehiger Demo

**Bewertungskriterien:**
- Funktionalitaet (40%)
- Code-Qualitaet & Struktur (25%)
- Error-Handling (20%)
- Dokumentation (15%)

---

## Zusaetzliche Ressourcen

### Fuer jeden Teilnehmer
- n8n Cloud Trial oder Self-Hosted Zugang
- Zugang zu Test-APIs und Dummy-Daten
- Dokumentations-Template
- Workflow-Cheat-Sheet
- Best-Practices Checklist

### Online-Ressourcen
- n8n Dokumentation: https://docs.n8n.io
- n8n Community Forum: https://community.n8n.io
- n8n YouTube Channel
- Beispiel-Workflows: https://n8n.io/workflows

### Test-Services & APIs
- JSONPlaceholder (Test-API)
- Webhook.site (Testing)
- OpenMeteo (Wetter-API)
- PokeAPI (Lern-API)
- RequestBin (Request-Testing)

---

## Technische Voraussetzungen

### Teilnehmer
- Laptop/PC mit Internetzugang (stabil!)
- Browser: Chrome/Firefox (aktuell)
- E-Mail-Account fuer n8n
- Optional: Smartphone fuer 2FA

### Accounts (vor Kurs-Start einrichten)
- n8n Cloud Account
- Gmail (fuer E-Mail-Tests)
- Slack Workspace (kann Test-Workspace sein)
- Google Account (fuer Sheets/Drive)

### Optional (fuer Fortgeschrittene)
- GitHub Account
- PostgreSQL Cloud-DB (z.B. ElephantSQL)
- MongoDB Atlas Account

---

## Trainer-Hinweise

### Didaktischer Ansatz
- **30% Theorie / 70% Praxis** in jeder Einheit
- Learning-by-Doing: Sofort anwenden
- Fehlerkultur: Fehler sind Lernchancen
- Peer-Learning foerdern
- Live-Coding mit Erklaerung

### Zeitmanagement pro 2h-Einheit
- 0:00-0:30 - Theorie & Demo
- 0:30-1:45 - Praktische Uebungen
- 1:45-2:00 - Q&A, Hausaufgabe, Wrap-Up

### Gruppengroesse
- **Optimal:** 4-6 Teilnehmer
- **Maximum:** 10 Teilnehmer (dann mit Co-Trainer)

### Hausaufgaben
- Review zu Beginn der naechsten Einheit (10-15 Min)
- Best Solutions zeigen
- Haeufige Fehler besprechen

---

## Erfolgs-Metriken

### Wochenweise Checkpoints
- **Woche 1:** Einfache 3-Node-Workflows erstellen
- **Woche 2:** Daten transformieren und filtern
- **Woche 3:** Mindestens 2 externe Services integrieren
- **Woche 4:** Datenbank CRUD-Operationen
- **Woche 5:** Komplexen Workflow strukturieren
- **Woche 6:** Eigenstaendiges Projekt umsetzen

### Erfolgskriterien am Ende
- Teilnehmer koennen Use-Case in Workflow uebersetzen
- Selbststaendiges Debugging
- Verstaendnis fuer Best Practices
- Abgeschlossenes, funktionsfaehiges Projekt

---

## Nach dem Kurs

### Weiterfuehrende Themen
- n8n AI Nodes (OpenAI, LLM-Integration)
- Custom Node Development
- Self-Hosting & Deployment
- Advanced Security
- Workflow-Templates erstellen

### Community-Einbindung
- n8n Community Forum beitreten
- Workflows teilen
- Templates veroeffentlichen
- Fragen stellen & beantworten

### Praxis-Projekte
- Eigene Use-Cases im Unternehmen
- Prozess-Automatisierung
- Integration bestehender Tools
- Kontinuierliche Optimierung

### Zertifizierung
- Teilnahme-Zertifikat (nach Abschlussprojekt)
- Optional: n8n Expert Certification (falls verfuegbar)

---

## Kontakt & Support

**Waehrend des Kurses:**
- Slack/Discord Channel fuer Fragen
- Office Hours (z.B. 1x/Woche 30 Min)
- E-Mail Support

**Nach dem Kurs:**
- Alumni-Gruppe (optional)
- Regelmaessige Follow-Up Sessions
- n8n Community als Hauptanlaufstelle
