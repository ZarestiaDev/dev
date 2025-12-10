# 🏰 Die Stämme - Plünder-Tracker

Eine interaktive Webanwendung zum Tracken und Analysieren von Spielerstatistiken aus dem Online-Spiel **"Die Stämme"**.

Perfekt für Stammesführer und Mitglieder, die den Fortschritt ihrer Spieler verfolgen und vergleichen möchten.

## ✨ Features

- 📊 **Globale Statistiken** - Vergleiche Spieler über mehrere Stämme hinweg
- 📈 **Interaktive Charts** - Visualisiere Fortschritt über Zeit
- 🏆 **Top 10 Rankings** - Sieh die besten Plünderer auf einen Blick
- 🎯 **Delta-Tracking** - Zeige tägliche Veränderungen an
- 📱 **Responsive Design** - Funktioniert auf Desktop und Mobile
- ☁️ **GitHub Integration** - Speichere Daten direkt in deinem Repository
- 🚀 **Keine Installation** - Läuft komplett im Browser

## 🚀 Schnellstart

### 1. Repository einrichten

1. **Forke dieses Repository** oder erstelle ein neues:
   ```bash
   git clone https://github.com/DEIN-USERNAME/stamm-tracker.git
   cd stamm-tracker
   ```

2. **GitHub Pages aktivieren**:
   - Gehe zu deinem Repository auf GitHub
   - Settings → Pages
   - Source: `main` Branch
   - Save

3. **Deine App ist jetzt live unter**:
   ```
   https://DEIN-USERNAME.github.io/stamm-tracker/
   ```

### 2. GitHub API Token erstellen (optional, aber empfohlen)

Für die direkte Integration benötigst du einen Personal Access Token:

1. Gehe zu [GitHub Token Settings](https://github.com/settings/tokens/new)
2. **Token name**: `Stamm Tracker`
3. **Expiration**: `No expiration` oder nach Wunsch
4. **Scopes**: Wähle `repo` (Full control of private repositories)
5. Klicke auf "Generate token"
6. **Kopiere den Token** - du siehst ihn nur einmal!

### 3. App konfigurieren

1. Öffne deine App im Browser
2. Klicke auf "⚙️ GitHub Einstellungen"
3. Trage ein:
   - **GitHub Username**: Dein GitHub-Benutzername
   - **Repository Name**: Name deines Repos (z.B. `stamm-tracker`)
   - **Personal Access Token**: Der Token aus Schritt 2
4. Klicke "✅ Speichern"
5. Teste mit "🔍 Verbindung testen"

## 📖 Anleitung

### Ersten Stamm hinzufügen

1. Klicke auf "➕ Neuen Stamm hinzufügen"
2. Gib einen Namen ein (z.B. "Die Barbaren")
3. Der Stamm wird lokal erstellt

### Daten hochladen

1. **Wähle einen Stamm** durch Anklicken
2. Klicke auf "📤 Daten für aktuellen Stamm hochladen"
3. **Kopiere die Spielerliste aus "Die Stämme"**:
   - Gehe zu deinem Stamm → Mitglieder
   - Markiere die komplette Tabelle (inkl. Header-Zeile)
   - Kopiere mit `Strg+C` / `Cmd+C`
4. **Füge die Daten ein** in das Textfeld
5. Klicke "✅ Daten verarbeiten"
6. Die App zeigt dir die verarbeiteten Daten an

### Änderungen speichern

**Wichtig**: Daten werden erst nach dem Pushen dauerhaft gespeichert!

1. Nachdem du Daten hochgeladen hast, siehst du einen grünen Button:
   ```
   ☁️ X Änderungen pushen
   ```
2. Klicke darauf
3. Die App speichert alle Änderungen direkt in dein GitHub Repository
4. Fertig! ✅

## 🎯 Features im Detail

### Stamm-Übersicht
- Sieh alle deine Stämme auf einen Blick
- Zeigt Anzahl der Spieler und letztes Update
- Wähle einen Stamm zum Anzeigen der Details

### Globale Statistik
- **Top 10 Spieler**: Die besten Plünderer über alle Stämme
- **Stamm-Statistiken**: Vergleiche verschiedene Stämme
  - Anzahl Spieler
  - Gesamt geplündert
  - Durchschnitt geplündert/Spieler
  - Durchschnittliche Punkte

### Stamm-Details (nach Auswahl)
- **Übersicht-Tab**:
  - Tabelle mit allen Spielern
  - Sortierbar nach Rang, Name, Punkte, Geplündert
  - Delta-Anzeige (Veränderung zum Vortag)

- **Verlaufs-Tab**:
  - Charts: Geplünderte Rohstoffe über Zeit
  - Charts: Punkteentwicklung über Zeit
  - Alle Spieler in einer Ansicht

## 📊 Datenformat

### Rohdaten aus "Die Stämme"
```
Name;Rang;Punkte;Globaler Rang;Dörfer;Features;Geplündert
Herr von Ribbeck;7;1,501;956;1;  ;61,140
Radio Pyongyang;1;2,642;80;1;  ;54,522
```

### Gespeichert als CSV
```csv
Datum;Name;Punkte;Geplündert
2025-12-08;Herr von Ribbeck;1501;61140
2025-12-08;Radio Pyongyang;2642;54522
```

Die App:
- ✅ Entfernt unnötige Spalten
- ✅ Normalisiert Zahlen (entfernt Kommas/Leerzeichen)
- ✅ Fügt automatisch das heutige Datum hinzu
- ✅ Merged mit existierenden Daten

## 🗂️ Repository-Struktur

```
stamm-tracker/
├── index.html              # Haupt-Anwendung (Single Page App)
├── stamm-list.json         # Liste aller Stämme
├── README.md               # Diese Anleitung
└── data/
    ├── die-barbaren.csv    # Daten für "Die Barbaren"
    ├── wikinger.csv        # Daten für "Wikinger"
    └── friendzone.csv      # etc.
```

### stamm-list.json Format
```json
[
  "die-barbaren",
  "wikinger",
  "friendzone"
]
```

**Hinweis**: Stammesnamen werden automatisch in Dateinamen konvertiert:
- `Die Barbaren` → `die-barbaren.csv`
- `Wikinger 2.0` → `wikinger-20.csv`

## 🔧 Technische Details

- **Rein Client-seitig** - Keine Server-Komponente nötig
- **Chart.js 4.4.0** - Für Visualisierungen
- **GitHub API** - Für direktes Speichern
- **Cache-Busting** - Verhindert veraltete Daten im Browser
- **Responsive CSS Grid** - Mobile-freundlich

## ⚠️ Wichtige Hinweise

- **Tausendertrennzeichen**: Die App unterstützt beide Formate (1.234 und 1,234)
- **Tägliche Updates**: Wenn du Daten für denselben Tag nochmal hochlädst, werden die alten überschrieben
- **Historische Daten**: Werden nie gelöscht - perfekt für Langzeit-Tracking
- **Browser-Cache**: Die App lädt immer die neuesten Daten von GitHub (kein Cache-Problem)
- **GitHub Token Sicherheit**: Wird nur lokal im Browser gespeichert (localStorage), nie auf einem Server

## 🐛 Troubleshooting

### Alte Daten werden angezeigt
- **Lösung**: Hard Refresh im Browser (`Strg+Shift+R` / `Cmd+Shift+R`)
- Die App lädt automatisch die neuesten Daten - sollte normalerweise nicht passieren

### "Keine stamm-list.json gefunden"
- **Lösung**: Erstelle die Datei im Repository Root:
  ```json
  []
  ```
- Dann füge Stämme über die App hinzu

### Push-Button funktioniert nicht
- **Prüfe**:
  1. GitHub Token ist korrekt eingetragen
  2. Token hat `repo` Berechtigung
  3. Username und Repository-Name stimmen
- **Test**: Klicke "🔍 Verbindung testen" in den Einstellungen

### Charts werden nicht angezeigt
- **Ursache**: Du benötigst mindestens 2 verschiedene Tage mit Daten
- **Lösung**: Lade an mehreren Tagen Daten hoch

### Tausendertrennzeichen-Probleme
- **Hinweis**: Die App unterstützt beide Formate automatisch
- Bei Problemen: Prüfe, ob die Rohdaten korrekt kopiert wurden

## 🔐 Datenschutz & Sicherheit

- **Alle Daten bleiben in deinem GitHub Repository**
- **Kein externer Server** - alles läuft lokal im Browser
- **GitHub Token** wird nur im Browser gespeichert (localStorage)
- **Öffentliche Repos**: Bedenke, dass Daten öffentlich sichtbar sind
- **Private Repos**: Nutze ein Private Repository für vertrauliche Daten

## 🤝 Für andere freigeben

1. **Teile den Link**: `https://DEIN-USERNAME.github.io/stamm-tracker/`
2. Andere können die Daten **lesen**, aber nicht ändern (ohne Token)
3. Für **Bearbeitungsrechte**: Teile deinen GitHub Token (NICHT empfohlen)
4. **Besser**: Gib anderen Collaborator-Rechte im Repository

## 📝 Workflow-Beispiel

```bash
# Täglicher Workflow
1. Öffne die App
2. Wähle deinen Stamm
3. Kopiere aktuelle Daten aus "Die Stämme"
4. Lade hoch und verarbeite
5. Klicke "Alle Änderungen pushen"
6. Fertig! ✅

# Die App aktualisiert automatisch:
- Globale Top 10
- Stamm-Statistiken
- Verlaufs-Charts
- Delta-Werte
```

## 🚀 Erweiterte Nutzung

### Mehrere Stämme verwalten
- Füge beliebig viele Stämme hinzu
- Jeder Stamm hat seine eigene CSV-Datei
- Globale Statistik zeigt Vergleich über alle Stämme

### Daten manuell bearbeiten
- CSV-Dateien können direkt in GitHub bearbeitet werden
- Format beachten: `Datum;Name;Punkte;Geplündert`
- Änderungen werden beim nächsten Laden der App übernommen

### Backup & Export
- Alle Daten liegen in deinem Git-Repository
- Automatisches Backup durch Git-Historie
- CSV-Download für lokale Backups möglich

## 📄 Lizenz

MIT License - Frei verwendbar für deine Stammeskollegen!

## 🙋 Support

Bei Fragen oder Problemen:
1. Prüfe dieses README
2. Schau in den Browser Console (F12) nach Fehlermeldungen
3. Erstelle ein Issue im GitHub Repository

---

**Viel Erfolg beim Tracken! 🎮**
