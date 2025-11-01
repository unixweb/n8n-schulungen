# n8n Schulung - Workflow-Beispiele

Diese Workflows gehoeren zum 6-woechigen n8n-Schulungsprogramm. Jede Woche enthaelt praxisnahe Beispiele, die aufeinander aufbauen.

## Uebersicht

| Woche | Thema | Anzahl Workflows | Schwierigkeit |
|-------|-------|------------------|---------------|
| 1 | Grundlagen & Erste Schritte | 4 | * Anfaenger |
| 2 | Datenverarbeitung & Transformation | 4 | ** Anfaenger+ |
| 3 | API-Integrationen & Authentifizierung | 3 | ** Fortgeschritten |
| 4 | Datenbanken & Persistenz | 3 | *** Fortgeschritten |
| 5 | Fortgeschrittene Workflows | 3 | *** Fortgeschritten+ |
| 6 | Praxisprojekte | 2 | **** Experte |

---

## Woche 1: Grundlagen & Erste Schritte

### 1.1 Erste Schritte
**Datei:** `woche1/woche1-1-erste-schritte.json`

**Beschreibung:** Ihr erster n8n-Workflow mit Manual Trigger und Set Node.

**Lernziele:**
- Manual Trigger verwenden
- Set Node zum Erstellen von Daten
- Workflow ausfuehren und Ergebnisse pruefen

**Nodes:** Manual Trigger, Set

---

### 1.2 Schedule Trigger
**Datei:** `woche1/woche1-2-schedule-trigger.json`

**Beschreibung:** Automatischer Workflow, der taeglich um 9 Uhr ausgefuehrt wird.

**Lernziele:**
- Schedule Trigger mit Cron-Expression
- Zeitstempel generieren mit Expressions
- Automatisierung verstehen

**Nodes:** Schedule Trigger, Set

---

### 1.3 Webhook Beispiel
**Datei:** `woche1/woche1-2-webhook-beispiel.json`

**Beschreibung:** Webhook, der Namen als Parameter empfaengt und personalisierte Begruessung zurueckgibt.

**Lernziele:**
- Webhook Trigger einrichten
- Query-Parameter auslesen
- Response zurueckgeben

**Nodes:** Webhook, Set, Respond to Webhook

**Test:** `GET http://localhost:5678/webhook/begruessen?name=Max`

---

### 1.4 HTTP Request Wetter
**Datei:** `woche1/woche1-3-http-request-wetter.json`

**Beschreibung:** Wetterdaten von Open-Meteo API abrufen und verarbeiten.

**Lernziele:**
- HTTP Request Node mit GET
- Query-Parameter an API senden
- Response-Daten extrahieren

**Nodes:** Manual Trigger, HTTP Request, Set

**API:** Open-Meteo (keine Auth erforderlich)

---

### 1.5 Email Wettervorhersage
**Datei:** `woche1/woche1-4-email-wettervorhersage.json`

**Beschreibung:** Taegliche Wettervorhersage per E-Mail.

**Lernziele:**
- Email Node konfigurieren
- Credentials einrichten
- Kompletter End-to-End Workflow

**Nodes:** Schedule Trigger, HTTP Request, Set, Email Send

**Voraussetzung:** SMTP-Credentials konfiguriert

---

## Woche 2: Datenverarbeitung & Transformation

### 2.1 Set Node Transformation
**Datei:** `woche2/woche2-1-set-node-transformation.json`

**Beschreibung:** Daten von API abrufen und mit Set Node transformieren.

**Lernziele:**
- Nested JSON-Daten zugreifen
- String-Operationen (toUpperCase, split)
- Neue Felder berechnen
- Boolean-Logik

**Nodes:** Manual Trigger, HTTP Request, Set

**API:** JSONPlaceholder Users

---

### 2.2 Filter und IF Node
**Datei:** `woche2/woche2-2-filter-if-beispiel.json`

**Beschreibung:** Posts filtern und nach Laenge des Titels in Kategorien einteilen.

**Lernziele:**
- Filter Node mit Bedingungen
- IF Node fuer Verzweigungen
- Zwei Output-Pfade
- String-Laenge pruefen

**Nodes:** Manual Trigger, HTTP Request, Filter, IF, Set (2x)

**API:** JSONPlaceholder Posts

---

### 2.3 Code Node Beispiel
**Datei:** `woche2/woche2-3-code-node-beispiel.json`

**Beschreibung:** Verkaufszahlen mit JavaScript analysieren und Statistiken berechnen.

**Lernziele:**
- Code Node fuer komplexe Berechnungen
- Array-Operationen (reduce, map)
- Math-Funktionen (max, min)
- Custom Logic in JavaScript

**Nodes:** Manual Trigger, Set, Code

---

### 2.4 Fehlerbehandlung & Merge
**Datei:** `woche2/woche2-4-fehlerbehandlung-merge.json`

**Beschreibung:** Zwei APIs parallel abrufen, Daten mergen und kombinieren.

**Lernziele:**
- Parallele API-Calls
- Merge Node verwenden
- Daten nach ID matchen
- Error-Handling einrichten

**Nodes:** Manual Trigger, HTTP Request (2x), Merge, Filter, Set, Stop and Error

**APIs:** JSONPlaceholder Users & Posts

---

## Woche 3: API-Integrationen & Authentifizierung

### 3.1 REST API POST Request
**Datei:** `woche3/woche3-1-rest-api-post-request.json`

**Beschreibung:** Daten mit POST-Request an API senden.

**Lernziele:**
- POST-Request mit JSON-Body
- HTTP-Methoden verstehen
- Response verarbeiten
- Request-Body formatieren

**Nodes:** Manual Trigger, Set, HTTP Request, Set

**API:** JSONPlaceholder Posts (POST)

---

### 3.2 Google Sheets Integration
**Datei:** `woche3/woche3-3-google-sheets-integration.json`

**Beschreibung:** Taegliche Wetterdaten in Google Sheets schreiben.

**Lernziele:**
- Google Sheets Credentials
- OAuth 2.0 konfigurieren
- Append/Update Operation
- Column Mapping

**Nodes:** Schedule Trigger, HTTP Request, Set, Google Sheets

**Voraussetzung:** Google OAuth Credentials

---

### 3.3 Slack Alert System
**Datei:** `woche3/woche3-4-slack-alert-system.json`

**Beschreibung:** Webhook empfangen und basierend auf Severity Slack-Alert senden.

**Lernziele:**
- Slack Bot Token
- Markdown-Formatierung
- Conditional Messaging
- Alert-Kategorisierung

**Nodes:** Webhook, IF, Set (2x), Slack, Respond to Webhook

**Voraussetzung:** Slack App & Bot Token

**Test:**
```bash
curl -X POST http://localhost:5678/webhook/alert \
  -H "Content-Type: application/json" \
  -d '{"system": "API", "message": "Server down", "severity": "high"}'
```

---

## Woche 4: Datenbanken & Persistenz

### 4.1 PostgreSQL Grundlagen
**Datei:** `woche4/woche4-1-postgres-grundlagen.json`

**Beschreibung:** Daten aus PostgreSQL-Datenbank auslesen.

**Lernziele:**
- PostgreSQL Credentials
- SELECT Query ausfuehren
- ORDER BY und LIMIT
- Daten formatieren

**Nodes:** Manual Trigger, Postgres, Set

**Voraussetzung:** PostgreSQL-Datenbank mit `kunden`-Tabelle

**Schema:**
```sql
CREATE TABLE kunden (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  status VARCHAR(50),
  erstellt_am TIMESTAMP DEFAULT NOW()
);
```

---

### 4.2 CRUD Operationen
**Datei:** `woche4/woche4-2-crud-operationen.json`

**Beschreibung:** Kompletter CRUD-Workflow: Formular  Validierung  Duplikat-Check  Insert

**Lernziele:**
- INSERT mit RETURNING
- Duplikat-Pruefung
- Upsert-Logik
- Error-Responses

**Nodes:** Webhook, IF (2x), Postgres (2x), Set (3x), Respond to Webhook

**Test:**
```bash
curl -X POST http://localhost:5678/webhook/kunde-anlegen \
  -H "Content-Type: application/json" \
  -d '{"name": "Max Mustermann", "email": "max@beispiel.de", "telefon": "0123456789"}'
```

---

### 4.3 Daten-Sync Sheets  DB
**Datei:** `woche4/woche4-3-daten-sync-sheets-db.json`

**Beschreibung:** Inkrementeller Sync von Google Sheets zu PostgreSQL (nur neue/geaenderte Daten).

**Lernziele:**
- Timestamp-basierter Sync
- ON CONFLICT (Upsert)
- Sync-Log fuehren
- Inkrementelle Updates

**Nodes:** Schedule Trigger, Postgres, Google Sheets, Code, Postgres (2x)

**Schema:**
```sql
CREATE TABLE sync_log (
  id SERIAL PRIMARY KEY,
  sync_name VARCHAR(100),
  last_sync TIMESTAMP,
  eintraege_verarbeitet INT,
  erstellt_am TIMESTAMP DEFAULT NOW()
);
```

---

## Woche 5: Fortgeschrittene Workflows & Best Practices

### 5.1 Sub-Workflow Architektur
**Datei:** `woche5/woche5-1-sub-workflow-architektur.json`

**Beschreibung:** Master-Workflow mit mehreren Sub-Workflows fuer modulare Bestellverarbeitung.

**Lernziele:**
- Execute Workflow Node
- Modulare Architektur
- Workflow-Verkettung
- Parameter-Uebergabe

**Nodes:** Webhook, Set, Execute Workflow (4x), IF (2x), Set (3x), Respond to Webhook

**Hinweis:** Benoetigt separate Sub-Workflows fuer:
- Validierung
- Lagerbestand-Check
- Bestellung verarbeiten
- Benachrichtigung

---

### 5.2 Batch Processing
**Datei:** `woche5/woche5-2-batch-processing.json`

**Beschreibung:** Grosse Datenmengen (1000+ Eintraege) in Batches verarbeiten.

**Lernziele:**
- Split In Batches Node
- Loop-Konzept
- Rate Limiting
- Progress-Tracking

**Nodes:** Manual Trigger, Postgres, Split In Batches, Code, Wait, Postgres, Set, Code

**Batch-Size:** 50 Eintraege pro Batch
**Wait-Time:** 2 Sekunden zwischen Batches

---

### 5.3 Error Handling & Monitoring
**Datei:** `woche5/woche5-3-error-handling-monitoring.json`

**Beschreibung:** Error Workflow mit Logging, Severity-Check und Multi-Channel Alerts.

**Lernziele:**
- Error Trigger
- Error-Details extrahieren
- Severity-basiertes Alerting
- Multi-Channel Notification

**Nodes:** Error Trigger, Code, Postgres, IF, Slack, Email Send, Set

**Verwendung:** Als Error Workflow fuer andere Workflows konfigurieren

**Schema:**
```sql
CREATE TABLE error_log (
  id SERIAL PRIMARY KEY,
  workflow_id VARCHAR(255),
  workflow_name VARCHAR(255),
  execution_id VARCHAR(255),
  error_message TEXT,
  error_node VARCHAR(255),
  error_type VARCHAR(100),
  stack_trace TEXT,
  severity VARCHAR(50),
  created_at TIMESTAMP DEFAULT NOW()
);
```

---

## Woche 6: Praxisprojekte

### 6.1 E-Commerce Automation
**Datei:** `woche6/woche6-praxisprojekt-ecommerce.json`

**Beschreibung:** Komplette Bestellverarbeitung mit Lagercheck, Rechnungserstellung und Multi-Channel Benachrichtigung.

**Features:**
- Bestellvalidierung
- Lagerbestand-Pruefung
- Automatische Rechnungsgenerierung
- E-Mail-Benachrichtigung
- Slack-Integration
- Error-Handling fuer nicht-verfuegbare Produkte

**Nodes:** 17 Nodes
**Komplexitaet:** **** Experte

**Workflow-Schritte:**
1. Webhook empfaengt Bestellung
2. Daten validieren
3. Bestellung in DB speichern
4. Lagerbestand fuer alle Produkte pruefen
5. Status aggregieren
6. **Wenn verfuegbar:** Rechnung generieren  E-Mail + Slack
7. **Wenn nicht verfuegbar:** Wartestatus  Verzoegerungs-Email
8. Response zurueckgeben

**Test:**
```bash
curl -X POST http://localhost:5678/webhook/bestellung \
  -H "Content-Type: application/json" \
  -d '{
    "bestellung_id": "ORD-2025-001",
    "kunde_id": 123,
    "kunde_email": "kunde@beispiel.de",
    "produkte": [
      {"id": 1, "name": "Laptop", "menge": 1, "preis": 899},
      {"id": 2, "name": "Maus", "menge": 2, "preis": 29}
    ],
    "gesamtbetrag": 957
  }'
```

**Schema:**
```sql
CREATE TABLE bestellungen (
  id SERIAL PRIMARY KEY,
  bestellung_id VARCHAR(100) UNIQUE,
  kunde_id INT,
  kunde_email VARCHAR(255),
  gesamtbetrag DECIMAL(10,2),
  status VARCHAR(50),
  erstellt_am TIMESTAMP DEFAULT NOW(),
  bestaetigt_am TIMESTAMP,
  notizen TEXT
);

CREATE TABLE produkte (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  lagerbestand INT,
  preis DECIMAL(10,2)
);
```

---

### 6.2 Mitarbeiter-Onboarding System
**Datei:** `woche6/woche6-praxisprojekt-onboarding.json`

**Beschreibung:** Automatisches Onboarding-System mit Task-Generierung und Multi-Department Notifications.

**Features:**
- Mitarbeiter in DB anlegen
- 6 Onboarding-Tasks automatisch generieren
- Tasks nach Abteilung gruppieren
- Google Sheets Integration
- Welcome-Email an Mitarbeiter
- Benachrichtigungen an HR + Abteilungen
- Prioritaets- und Frist-Management

**Nodes:** 13 Nodes
**Komplexitaet:** **** Experte

**Workflow-Schritte:**
1. Webhook empfaengt neue Mitarbeiter-Daten
2. Mitarbeiter in DB anlegen
3. 6 Standard-Tasks generieren (IT, HR, Facility)
4. Tasks in DB speichern
5. Tasks in Google Sheets eintragen
6. Tasks nach Abteilung aggregieren
7. **Parallel:**
   - Welcome-Email an Mitarbeiter
   - Slack-Notification an HR
   - Emails an betroffene Abteilungen
8. Response zurueckgeben

**Generierte Tasks:**
- E-Mail-Account einrichten (IT, 3 Tage)
- Hardware bereitstellen (IT, 5 Tage)
- Arbeitsplatz vorbereiten (Facility, 7 Tage)
- Zugaenge einrichten (IT, 3 Tage)
- Onboarding-Buddy zuweisen (HR, 5 Tage)
- Welcome-Package (HR, 7 Tage)

**Test:**
```bash
curl -X POST http://localhost:5678/webhook/neuer-mitarbeiter \
  -H "Content-Type: application/json" \
  -d '{
    "vorname": "Anna",
    "nachname": "Schmidt",
    "email": "anna.schmidt@firma.de",
    "abteilung": "Engineering",
    "position": "Senior Developer",
    "startdatum": "2025-02-01"
  }'
```

**Schema:**
```sql
CREATE TABLE mitarbeiter (
  id SERIAL PRIMARY KEY,
  vorname VARCHAR(100),
  nachname VARCHAR(100),
  email VARCHAR(255) UNIQUE,
  abteilung VARCHAR(100),
  position VARCHAR(100),
  startdatum DATE,
  status VARCHAR(50),
  erstellt_am TIMESTAMP DEFAULT NOW()
);

CREATE TABLE onboarding_tasks (
  id SERIAL PRIMARY KEY,
  mitarbeiter_id INT REFERENCES mitarbeiter(id),
  titel VARCHAR(255),
  verantwortlich VARCHAR(100),
  prioritaet VARCHAR(50),
  frist DATE,
  status VARCHAR(50),
  erstellt_am TIMESTAMP DEFAULT NOW(),
  erledigt_am TIMESTAMP
);
```

---

## Workflows importieren

### In n8n Cloud:
1. Workflow oeffnen
2. "..." Menue  "Import from File"
3. JSON-Datei auswaehlen

### In n8n Self-Hosted:
1. Workflow-Seite oeffnen
2. "+ Add workflow"
3. "..." Menue  "Import from File"
4. JSON-Datei hochladen

### Via CLI:
```bash
# Alle Workflows importieren
for file in workflows/**/*.json; do
  curl -X POST http://localhost:5678/api/v1/workflows \
    -H "Content-Type: application/json" \
    -d @"$file"
done
```

---

## Voraussetzungen & Setup

### Allgemein:
- n8n installiert (Cloud oder Self-Hosted)
- Basis-Verstaendnis von JSON
- Testumgebung fuer Webhooks

### Credentials benoetigt:

#### Woche 1-2:
- SMTP fuer Email (Gmail, Outlook, etc.)

#### Woche 3:
- Google OAuth (fuer Sheets)
- Slack Bot Token

#### Woche 4-6:
- PostgreSQL Datenbank
- Alle o.g. Credentials

### Datenbank-Setup:

```bash
# PostgreSQL lokal mit Docker
docker run --name n8n-postgres \
  -e POSTGRES_PASSWORD=n8n \
  -e POSTGRES_DB=n8n_schulung \
  -p 5432:5432 \
  -d postgres:15

# Verbindung in n8n:
# Host: localhost
# Port: 5432
# Database: n8n_schulung
# User: postgres
# Password: n8n
```

SQL-Schemas befinden sich in den jeweiligen Workflow-Beschreibungen.

---

## Tipps & Best Practices

### Beim Import:
- WARNUNG: **Credentials muessen neu konfiguriert werden** (werden nicht mitexportiert)
- IDs in Sub-Workflows anpassen (`{{ SUB_WORKFLOW_ID }}`)
- Webhook-Paths bei Bedarf aendern
- Google Sheets IDs ersetzen

### Beim Testen:
- Mit "Test workflow" starten
- Execution-Log pruefen
- Error-Workflows separat testen
- Webhooks mit curl/Postman testen

### Haeufige Fehler:
- [X] Credentials fehlen  Neu anlegen
- [X] Datenbank existiert nicht  Schema ausfuehren
- [X] Webhook-URL falsch  n8n URL pruefen
- [X] Rate Limiting  Batch-Size reduzieren

---

## Weiterfuehrende Ressourcen

-  [n8n Dokumentation](https://docs.n8n.io)
-  [n8n Community Forum](https://community.n8n.io)
-  [n8n YouTube Channel](https://youtube.com/@n8n-io)
-  [Haupt-Schulungsdokument](../n8n-schulungsprogramm-6-wochen.md)

---

## Support

Bei Fragen zu den Workflows:
1. Execution-Log pruefen
2. Error-Message genau lesen
3. Community Forum durchsuchen
4. Issue im Repository erstellen

---

**Viel Erfolg bei der Schulung! **
