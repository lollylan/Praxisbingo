---
name: Gemini - Projektverfassung Praxisbingo
version: 1.0
status: Aktiv
---

# Gemini: Projektverfassung Praxisbingo

## North Star
Ein lustiges, tägliches Bingo-Spiel für das MFA-Team einer Hausarztpraxis. Niemand braucht einen Server. Alles läuft im Browser. Wer zuerst eine Reihe voll hat, ruft "Bingo!" in der Gruppe.

## Architektur-Invarianten
- **Kein Server** – reine client-side App (HTML + CSS + JS)
- **Hosting:** GitHub Pages (https://github.com/lollylan/Praxisbingo)
- **Einstiegsdatei:** `index.html`
- **Keine Datenbank** – alles im LocalStorage (optional, für Felder-Persistenz)
- Keine externen Bibliotheken die einen CDN-Aufruf brauchen (offline-fähig)

## Datenschema

### Board-State (im Speicher / LocalStorage)
```json
{
  "mode": "5x5" | "4x4",
  "cells": [
    {
      "id": 0,
      "text": "Patient hat vorher gegoogelt 🔍",
      "marked": false,
      "isCenter": false
    }
  ],
  "bingoAchieved": false
}
```

### Bingo-Pool-Eintrag
```json
{
  "id": "unique_slug",
  "text": "Anzeigetext (max ~50 Zeichen)",
  "emoji": "🔍",
  "category": "patient | telefon | technik | team | papier"
}
```

## Spielregeln
- 5x5: 25 Felder, mittleres Feld = FREI (automatisch markiert)
- 4x4: 16 Felder, kein Freifeld
- Bingo = eine vollständige Reihe (horizontal, vertikal oder diagonal)
- Felder werden durch Anklicken markiert/abgehakt
- "Neues Spiel" = neues zufälliges Board aus dem Pool

## Content-Regeln
- Nur Ereignisse, die täglich in einer Hausarztpraxis vorkommen können
- Kein Quartalsbezug (kein KV-Abrechnung etc.)
- Deutsch, leicht humorvoll, nicht verletzend
- Emojis erlaubt, aber sparsam

## Features
1. Board-Größe wählen: 4x4 oder 5x5
2. Zufälliges Board aus Pool generieren
3. Felder anklicken (markiert / nicht markiert)
4. Bingo-Erkennung: Zeilen, Spalten, Diagonalen
5. Bingo-Feier-Animation
6. Edit-Modus: Einzelne Felder anpassen
7. Export: Felder-Liste als Text kopieren
8. Drucken
9. Responsive (Mobile + Desktop)
10. LocalStorage: angepasste Felder bleiben erhalten

## Verhaltensregeln
- Ton: Locker, lustig, kollegial – wie ein Insider-Witz im Team
- Keine Patienten-Namen oder sensible Daten
- Alle Texte auf Deutsch
- App darf niemals abstürzen (kein Server = kein Ausfall)
