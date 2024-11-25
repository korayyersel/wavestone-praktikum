# Praktikum Bewerbungsaufgabe "Aufgaben-Tracker"

## Fachliche Anforderungen 

-   **Funktion:** Eine Web-App, in der Benutzer ihre Aufgaben erstellen, bearbeiten und als "erledigt" markieren können.
-   **Anforderungen:**
    -   Aufgaben haben Felder wie Titel, Beschreibung, Priorität, und Fälligkeitsdatum.
    -   Backend verwaltet Aufgaben in MongoDB und bietet APIs für CRUD-Operationen.
    -   (optional) Benutzer können sich anmelden und können nur ihre Aufgaben verwalten.
	    - Siehe "Optionale Zusatz-Anforderung "Google Login"

## Technische Anforderungen
### **Frontend:**
-   **Technologien:** React, Angular, Vue.js (up to you)
-   **Environment:** Läuft in einer Docker-Instanz gemeinsam mit Backend. Docker Instanz wird auf "Cloud Run" (https://cloud.google.com/run?hl=en) gehostet.
-   **Aufgabe:**
    -   Eine Benutzeroberfläche erstellen, um Daten anzuzeigen und hinzuzufügen.
    -   Verwenden Sie REST-Aufrufe, um mit dem Backend zu kommunizieren.

### **Backend:**
-   **Technologien:** Node.js (Express.js) oder Java (Spring)
-   **Environment:** Läuft in einer Docker-Instanz gemeinsam mit Frontend. Docker Instanz wird auf "Cloud Run" (https://cloud.google.com/run?hl=en) gehostet.
-   **Aufgabe:**
    -   Eine RESTful API mit mindestens zwei Endpunkten bereitstellen:
        1.  **GET /tasks:** Gibt eine Liste von gespeicherten Daten aus der MongoDB zurück.
        2.  **POST /tasks:** Speichert neue Daten in der MongoDB.

### **Datenbank:**
-   **Technologien:** MongoDB
-   **Environment:** Läuft bei MongoDB Atlas https://cloud.mongodb.com/
-   **Aufgabe:**
    -   Eine Collection (z. B. `tasks`) erstellen, wo die Aufgaben gespeichert werden


### **Docker**
Wie oben steht müssen Frontend and Backend gemeinsam in deiner Docker Instanz laufen. Hier ein Beispiel Projekt-Struktur:
*(Bespiel nimmt an, dass Backend mit Node.js umgesetzt ist.)*
```
project/
├── frontend/
│   ├── build/                # Das gebaute React-Frontend (nach `npm run build`)
│   └── package.json          # React-spezifische Abhängigkeiten
├── backend/
│   ├── server.js             # Node.js-API
│   └── package.json          # Backend-spezifische Abhängigkeiten
├── Dockerfile                # Docker-Build-Anweisungen
└── docker-compose.yml        # Optional für lokale Entwicklung

```

### **Optionale Zusatz-Anforderung "Google Login":**
Mit dieser optionalen Anforderung könnt ihr ausprobieren, eine Authentifizierung für eure App zu implementieren. Hier ein Beispiel, das ich für euch entwickelt habe: https://hello-world-app-848709590175.us-central1.run.app/ (Login nur mit einem Google-Konto möglich. Siehe "Vorbereitung"). Die Applikation erkennt den eingeloggten Benutzer. Mit dieser Zusatzanforderung könnt ihr versuchen, etwas Ähnliches umzusetzen und sicherzustellen, dass jeder angemeldete Benutzer nur seine eigenen Aufgaben sehen und verwalten kann. Was braucht es dazu?
- Ein Firebase Projekt > https://console.firebase.google.com/
    - **Ein wichtiger Tipp**: Kein neues Projekt anlegen, sondern bestehendes Google Projekt verwenden, wo ihr eure App auf "Cloud Run" deployt. 
        > "Already have a Google Cloud project? Add Firebase to Google Cloud project"
- Unter Projekt eine Webapplikation anlegen
- "Add Firebase SDK": Wichtiger Schritt. Ihr müsst rausfinden, was ihr mit dieser Code machen müsst...
- "Sign-in method" > Choose provider Google > "Enable"

## Vorbereitung
- Ein Google-Konto erstellen: Wichtig: Es ist nicht notwendig, eine Gmail-Adresse zu verwenden oder eine neue G-Mail-Adresse zu registrieren. Ein Google-Konto kann mit einer beliebigen bestehenden E-Mail-Adresse erstellt werden.
Anleitung: Besuche accounts.google.com, wähle „Konto erstellen“ > ... > "Eigene E-Mail-Adresse verwenden".
- Login / Registrierung bei https://console.cloud.google.com/
	- Für die Registrierung bei Google Cloud Platform (GCP) ist eine Kreditkarte erforderlich. Hinweis: Die oben beschriebenen Aufgaben verursachen keine Kosten, da alles innerhalb des Free Tiers abgedeckt wird. GCP verlangt jedoch die Angabe einer Kreditkarte zur Verifizierung, selbst wenn ausschliesslich kostenlose Dienste genutzt werden.
- Login / Registrierung bei https://cloud.mongodb.com/. Hier braucht es keine Kreditkarte. 