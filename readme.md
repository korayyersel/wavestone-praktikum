# Praktikum Bewerbungsaufgabe "Aufgaben-Tracker"

## Fachliche Anforderungen 

- **Funktion:** Eine Web-App, in der Benutzer ihre Aufgaben erstellen, bearbeiten und als "erledigt" markieren können.
- **Anforderungen:**
  - Aufgaben haben Felder wie Titel, Beschreibung, Priorität und Fälligkeitsdatum.
  - Das Backend verwaltet die Aufgaben in MongoDB und bietet APIs für CRUD-Operationen.
  - (optional) Benutzer können sich anmelden und nur ihre eigenen Aufgaben verwalten.  
    → Siehe "Optionale Zusatz-Anforderung 'Google Login'".

## Technische Anforderungen

### **Frontend**
- **Technologien:** React, Angular oder Vue.js (freie Wahl)
- **Environment:** Läuft in einem Docker-Container gemeinsam mit dem Backend. Der Docker-Container wird auf **Cloud Run** gehostet (https://cloud.google.com/run?hl=en).
- **Aufgabe:**
  - Eine Benutzeroberfläche erstellen, um Aufgaben anzuzeigen und hinzuzufügen.
  - Über REST-Aufrufe mit dem Backend kommunizieren.

### **Backend**
- **Technologien:** Node.js (Express.js) oder Java (Spring)
- **Environment:** Läuft in demselben Docker-Container wie das Frontend, ebenfalls auf Cloud Run.
- **Aufgabe:**
  - Eine RESTful API mit mindestens zwei Endpunkten bereitstellen:
    1. **GET /tasks:** Gibt eine Liste aller Aufgaben aus der MongoDB zurück.
    2. **POST /tasks:** Speichert eine neue Aufgabe in der MongoDB.

### **Datenbank**
- **Technologien:** MongoDB
- **Environment:** Bereitgestellt über MongoDB Atlas (https://cloud.mongodb.com/)
- **Aufgabe:**
  - Eine Collection (z. B. `tasks`) erstellen, in der die Aufgaben gespeichert werden.

## Docker

Wie oben beschrieben, müssen Frontend und Backend gemeinsam in einem Docker-Container laufen.  
Beispiel-Projektstruktur (Backend in Node.js):

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
---

### **Optionale Zusatz-Anforderung "Google Login":**
Mit dieser optionalen Aufgabe könnt ihr ausprobieren, eine einfache Authentifizierung zu implementieren.  
Die Applikation erkennt den eingeloggten Benutzer und ermöglicht es, dass jeder Benutzer nur seine eigenen Aufgaben sehen und verwalten kann.

Funktionsfähiges Beispiel (Demo Login):  
**https://login-demo-bewerbung.web.app/**

Was benötigt wird?

- Ein Firebase-Projekt: https://console.firebase.google.com/  
  **Wichtiger Hinweis:** Kein neues Projekt anlegen – verwendet das bestehende Google-Cloud-Projekt, das ihr später für das Cloud-Run-Deployment nutzt.  
    > „Already have a Google Cloud project? Add Firebase to Google Cloud project“

- Im bestehenden Projekt eine **Web-Applikation hinzufügen**:  
  Links im Menü **Project Overview** → **App hinzufügen** → **Web** auswählen.  
  Danach die App **registrieren** (App-Name frei wählbar).  
  **Wichtig:** Beim Registrieren **kein Haken bei „Firebase Hosting einrichten“** setzen.

- Nach der Registrierung erhaltet ihr den **Firebase SDK Konfigurationsblock** (firebaseConfig).  
  Dieser Block enthält `apiKey`, `authDomain`, `projectId` usw. und muss im Frontend eingebunden werden.

- Unter **Authentication → Sign-in method** den Provider **Google** auswählen und aktivieren.

- Zusätzlich sicherstellen, dass die verwendeten Domains unter  
  **Authentication → Settings → Authorized domains** eingetragen sind  
  (z. B. `localhost`, Cloud-Run-Domain, später die produktive Domain).

---

## Vorbereitung

- **Google-Konto erstellen:**  
  Es ist nicht notwendig, eine Gmail-Adresse zu verwenden. Ein Google-Konto kann mit jeder bestehenden E-Mail-Adresse erstellt werden.  
  Anleitung: accounts.google.com → „Konto erstellen“ → „Eigene E-Mail-Adresse verwenden“.

- **Google Cloud Console:**  
  Anmeldung unter https://console.cloud.google.com/  
  Für die Registrierung wird eine Kreditkarte zur Verifizierung verlangt.  
  Die oben genannten Aufgaben liegen jedoch vollständig im Free Tier und verursachen keine Kosten.

- **MongoDB Atlas:**  
  Anmeldung unter https://cloud.mongodb.com/  
  Keine Kreditkarte erforderlich.
