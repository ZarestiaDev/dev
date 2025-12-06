# Die Stämme - Plünder-Tracker

Interaktive Webanwendung zum Tracken von Spielerstatistiken aus "Die Stämme".

## 🚀 Setup

### 1. GitHub Pages einrichten

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/DEIN-USERNAME/stamm-tracker.git
git push -u origin main
```

Dann in GitHub:
- Settings → Pages
- Source: "main" Branch
- Save

Deine Seite ist dann unter: `https://DEIN-USERNAME.github.io/stamm-tracker/`

### 2. Repo-Struktur

```
stamm-tracker/
  ├── index.html           # Haupt-Anwendung
  ├── stamm-list.json      # Liste aller Stämme
  ├── README.md            # Diese Datei
  └── data/
      ├── die-barbaren.csv
      ├── wikinger.csv
      └── ...
```

## 📝 Workflow

### Neuen Stamm hinzufügen

1. In der App auf "➕ Neuen Stamm hinzufügen" klicken
2. Stammname eingeben (z.B. "Die Barbaren")
3. App erstellt automatisch den Eintrag
4. **Wichtig:** `stamm-list.json` manuell im Repo aktualisieren:

```json
[
  "die-barbaren",
  "wikinger",
  "dein-neuer-stamm"
]
```

Stammname wird automatisch in Dateinamen umgewandelt:
- `Die Barbaren` → `die-barbaren.csv`
- `Wikinger 2.0` → `wikinger-20.csv`

### Tägliches Update

1. Stamm auswählen
2. "📤 Daten für aktuellen Stamm hochladen" klicken
3. Rohdaten aus Die Stämme kopieren (inkl. Header):

```
Name;Rang;Punkte;Globaler Rang;Dörfer;Features;Geplündert
Herr von Ribbeck;7;501 ;956;1;  ;61,140
Radio Pyongyang;1;642 ;80;1;  ;54,522
...
```

4. "✅ Daten verarbeiten" klicken
5. App zeigt aktualisierte Statistiken
6. "💾 CSV herunterladen" klicken
7. Datei im Repo unter `data/stammname.csv` ersetzen
8. Git commit + push:

```bash
git add data/stammname.csv
git commit -m "Update stammname - $(date +%Y-%m-%d)"
git push
```

## 🎯 Features

### Übersicht-Tab
- Tabelle mit allen Spielern
- Sortierbar nach allen Spalten
- Delta-Anzeige (Veränderung zu gestern)

### Top 10 Tab
- Charts: Geplünderte Rohstoffe über Zeit
- Charts: Punkte über Zeit
- Automatisch die 10 besten Spieler basierend auf heutigem Stand

### Bottom 10 Tab
- Chart: Die 10 Spieler mit den wenigsten geplünderten Rohstoffen

### Spielersuche
- Sucht über alle Stämme
- Zeigt Stamm-Zugehörigkeit an

## 📊 CSV-Format

Nach Verarbeitung:
```csv
Datum;Name;Punkte;Geplündert
2024-12-05;Spieler1;1234;56789
2024-12-05;Spieler2;2345;67890
```

- Automatische Bereinigung (nur relevante Spalten)
- Datum wird automatisch gesetzt (heute)
- Zahlen werden normalisiert (Leerzeichen + Kommas entfernt)

## 🔧 Technisches

- **Keine Backend-Anforderungen** - rein HTML/JS
- **Chart.js** für Visualisierungen
- **LocalStorage** wird NICHT verwendet (alles in CSV)
- **Responsive Design**

## ⚠️ Wichtig

- CSV-Dateien müssen UTF-8 kodiert sein
- Pro Stamm max. 25 Spieler (Die Stämme Limit)
- Historische Daten werden nie gelöscht
- Wenn du Daten für denselben Tag nochmal hochlädst, werden die alten überschrieben

## 🐛 Troubleshooting

### "Keine stamm-list.json gefunden"
→ Erstelle die Datei im Root mit:
```json
["stamm1", "stamm2"]
```

### Charts werden nicht angezeigt
→ Stelle sicher, dass du mindestens 2 verschiedene Tage mit Daten hast

### Download funktioniert nicht
→ Browser-Popup-Blocker deaktivieren

## 📄 Lizenz

MIT - Frei verwendbar für deine Stammeskollegen!
