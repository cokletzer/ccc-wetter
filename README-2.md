# 🚴❄️ Cold Collective Crew – Wetter-Bot

Schickt der Crew das Wetter für die Ausfahrt (Di + Do, 6:30–8:30) als Push-Nachricht aufs Handy, über die App **ntfy**:

| Wann | Was |
|---|---|
| **Mo + Mi, 16:30** | Prognose für die Ausfahrt am nächsten Morgen |
| **Di + Do, 5:45** | Update kurz vor dem Losfahren |

**Orte:** Wien, Heiligenstadt (Treffpunkt) · Weidling, St. Andrä (Wienerwald) · Stammersdorf, Bisamberg, Manhartsbrunn (Weinviertel). Von November bis März steht die Weinviertel-Runde oben.

**So sieht es aus:** In der Benachrichtigung seht ihr sofort den Titel und die Warnungen. Antippen zeigt alle Orte.

```
🚴❄️ Cold Collective Crew · Update heute, Do 15.10.
🌅 Sonnenaufgang 7:14 – Licht mitnehmen!
🌧 Regen wahrscheinlich: Weidling, St. Andrä
🌫 Nebel: Wien, Heiligenstadt – Licht an

━━ TREFFPUNKT ━━
📍 Heiligenstadt – 🌫 Nebel · jetzt 6°
🌡 6–7° (gefühlt 3°) · 🌧 25 % / 0,1 mm
💨 aus W 14 km/h, Böen 34
…
```

Dazu gibt es eine **Live-Wetter-Seite**, auf der alle jederzeit selbst die aktuellen Daten abrufen können, für jeden Tag der nächsten Woche. Unter jeder Push-Nachricht ist ein Knopf **Live-Wetter**, der sie öffnet.

Kosten: **keine**. Bot und Seite laufen auf GitHub, ihr braucht keinen eigenen Computer und kein Konto bei ntfy.

---

## Einrichtung durch eine Person (einmalig, ca. 15 Minuten)

### 1. GitHub-Konto und privates Repository

1. Auf **github.com** ein kostenloses Konto anlegen.
2. Oben rechts auf **+** → **New repository** klicken.
   - Name: `cold-collective-wetter`
   - **Private** auswählen. Bei öffentlichen Repositories schaltet GitHub Zeitpläne nach 60 Tagen ohne Änderung automatisch ab.
   - Auf **Create repository** klicken.
3. **uploading an existing file** anklicken, die Dateien `cold_collective_wetter.py` und `README.md` hineinziehen und auf **Commit changes** klicken.
4. Den Zeitplan anlegen: **Add file** → **Create new file**.
   - Als Dateinamen genau `.github/workflows/wetter.yml` eintippen. Die Schrägstriche legen die Ordner an.
   - Den Inhalt der Datei `wetter.yml` hineinkopieren und auf **Commit changes** klicken.

### 2. Das ntfy-Thema hinterlegen

Das Thema ist der „Kanal“, den alle in der App abonnieren. Wer den Namen kennt, kann mitlesen. Er sollte deshalb schwer zu erraten sein, zum Beispiel `ccc-wetter-376c2ef4`.

Im Repository: **Settings** → **Secrets and variables** → **Actions** → **New repository secret**
- Name: `NTFY_TOPIC`
- Secret: euer Thema, z. B. `ccc-wetter-376c2ef4`
- Auf **Add secret** klicken.

### 3. Selbst abonnieren und testen

1. Die App **ntfy** installieren (App Store bzw. Google Play) und das Thema abonnieren (siehe unten).
2. Auf GitHub den Reiter **Actions** öffnen. Falls GitHub fragt, die Workflows aktivieren.
3. Links **Cold Collective Crew – Wetter** wählen, dann **Run workflow** → **Run workflow** klicken.
4. Nach etwa 30 Sekunden kommt die Prognose für die nächste Ausfahrt aufs Handy. ✅

Ab dann läuft alles automatisch.

### 4. Live-Wetter-Seite veröffentlichen (ca. 5 Minuten)

Die Seite kommt in ein **zweites, öffentliches** Repository. GitHub Pages ist nur für öffentliche Repositories kostenlos. Das ist unbedenklich, denn die Seite enthält nur die Orte und kein ntfy-Thema.

1. Auf GitHub **+** → **New repository** klicken.
   - Name: `ccc-wetter`
   - **Public** auswählen und auf **Create repository** klicken.
2. **uploading an existing file** anklicken, die Datei `index.html` hineinziehen und auf **Commit changes** klicken.
3. **Settings** → links **Pages** öffnen.
   - Bei **Source**: „Deploy from a branch“ wählen.
   - Bei **Branch**: `main` und `/ (root)` wählen, dann **Save** klicken.
4. Nach 1–2 Minuten steht oben auf derselben Seite die Adresse, z. B. `https://euer-name.github.io/ccc-wetter/`. Die Adresse auf dem Handy öffnen und prüfen.
5. Damit der Knopf unter den Push-Nachrichten erscheint: im **Bot-Repository** `cold-collective-wetter` unter **Settings** → **Secrets and variables** → **Actions** → **New repository secret** anlegen.
   - Name: `WETTER_SEITE_URL`
   - Secret: die Adresse aus Schritt 4

Ohne dieses Secret funktioniert alles wie bisher, nur ohne den Knopf.

---

## Wetter manuell abrufen

| Wer | Wie | Was passiert |
|---|---|---|
| **Alle** | Live-Wetter-Seite öffnen (oder in einer Push auf **Live-Wetter** tippen), dann den Tag wählen und auf **Aktualisieren** tippen | Die aktuellen Daten erscheinen sofort auf dem eigenen Handy. Niemand sonst bekommt eine Nachricht |
| **Admin** | GitHub → **Actions** → **Cold Collective Crew – Wetter** → **Run workflow** | Alle aus der Crew bekommen sofort eine Push-Nachricht mit der Prognose für die nächste Ausfahrt, z. B. wenn sich das Wetter kurzfristig ändert |

Die Seite zeigt dieselben Werte und Warnungen wie die Push-Nachricht. Zusätzlich lässt sich jeder Tag der nächsten Woche wählen, die Ausfahrtstage sind markiert. Lag die Seite länger als 10 Minuten im Hintergrund, lädt sie beim Zurückkehren automatisch neu.

---

## Für alle aus der Crew (2 Minuten)

1. Die App **ntfy** installieren:
   - iPhone: App Store, „ntfy“ suchen
   - Android: Google Play, „ntfy“ suchen
2. App öffnen und auf **+** tippen.
3. Das Thema eintragen (z. B. `ccc-wetter-376c2ef4`). Den Server auf **ntfy.sh** lassen.
4. Auf **Abonnieren** bzw. **Subscribe** tippen. Fertig.
5. Wichtig: Benachrichtigungen für die App erlauben, wenn das Handy fragt.
6. Die Live-Wetter-Seite als App-Symbol auf den Startbildschirm legen:
   - iPhone: Seite in Safari öffnen → Teilen-Symbol → **Zum Home-Bildschirm**
   - Android: Seite in Chrome öffnen → **⋮** → **Zum Startbildschirm hinzufügen**

Tipp: Wer die 5:45-Nachricht leiser haben will, ändert in den Mitteilungs- bzw. Benachrichtigungseinstellungen des Handys den Ton für die App ntfy oder schaltet ihn aus.

---

## Gut zu wissen

- **Pünktlichkeit:** GitHub startet geplante Läufe oft ein paar Minuten später, die Nachricht kommt also z. B. zwischen 5:47 und 5:55. In seltenen Fällen kann ein Lauf auch ausfallen. Kommt der Morgenlauf erst nach 6:30, wird nichts mehr geschickt.
- **Sommer-/Winterzeit:** Die Umstellung passiert automatisch. Im Zeitplan steht jeder Termin zweimal, weil GitHub nur Weltzeit (UTC) kennt. Eine der beiden Varianten beendet sich mit „Nichts zu tun“. Das ist normal.
- **Kosten:** Private Repositories haben 2.000 Freiminuten pro Monat. Der Bot braucht rund 35.
- **Was die Werte bedeuten:**
  - Temperatur und Wind kommen aus den Stundenwerten um 6, 7 und 8 Uhr.
  - Regen ist die Summe von 6 bis 9 Uhr, die Regenwahrscheinlichkeit der höchste Stundenwert.
  - Das Wettersymbol zeigt das „schlechteste“ Wetter im Zeitfenster.
  - „jetzt“ ist der aktuelle Modellwert von Open-Meteo. Er wird alle 15 Minuten aktualisiert, ist aber keine Messstation.
- **Wenn etwas schiefgeht:** Bei einem fehlgeschlagenen Lauf schickt GitHub dem Kontoinhaber automatisch eine E-Mail. Sind die Wetterdaten nicht abrufbar, bekommt die Crew eine kurze Ersatznachricht.
- **Neues Thema:** Gerät der Themenname in falsche Hände, einfach ein neues Thema ausdenken, das Secret `NTFY_TOPIC` überschreiben und der Crew den neuen Namen schicken.

## Anpassen

Alles Wichtige steht ganz oben im Skript unter **„Einstellungen“**: Ausfahrtstage, Uhrzeiten, Orte mit Koordinaten, Wintermonate, Warnschwellen und die Lautstärke der Benachrichtigung (`NTFY_PRIORITAET`: 4 = Pop-up mit Ton, 3 = normal).
Die Live-Seite hat dieselben Einstellungen im Abschnitt **„Einstellungen“** im Skriptteil von `index.html`. Wenn ihr Orte oder Schwellen ändert, ändert sie an beiden Stellen, damit Push und Seite dasselbe zeigen.
Zum Bearbeiten auf GitHub die Datei anklicken, auf das Stift-Symbol klicken und dann **Commit changes** wählen.

Wenn ihr **Versandzeiten oder Wochentage** ändert, müsst ihr auch `wetter.yml` anpassen:
- Die Sommer-Zeile ist die Wiener Zeit minus 2 Stunden, die Winter-Zeile die Wiener Zeit minus 1 Stunde.
- Bei den Wochentagen steht 1 = Montag … 5 = Freitag.

## Fehlersuche

| Problem | Lösung |
|---|---|
| Keine Nachricht | **Actions** → letzten Lauf anklicken → Protokoll lesen |
| `NTFY_TOPIC fehlt` | Secret-Name genau so schreiben, in Großbuchstaben |
| Lauf grün, aber nichts am Handy | Ist das Thema in der App exakt gleich geschrieben? Sind Benachrichtigungen für ntfy erlaubt? |
| Testen ohne GitHub | Im Browser `https://ntfy.sh/<euer-thema>` öffnen: Dort seht ihr alle Nachrichten der letzten Stunden |
| Live-Seite zeigt 404 | Nach dem Speichern bei **Pages** 1–2 Minuten warten. Liegt die Datei als `index.html` im Hauptordner? Ist das Repository **Public**? |
| Neue `index.html` hochgeladen, Handy zeigt noch die alte Seite | GitHub stellt Änderungen nach 1–2 Minuten bereit. Das Handy kann die alte Seite bis zu 10 Minuten zwischenspeichern: Seite neu laden bzw. die Startbildschirm-App ganz schließen und neu öffnen. Unten auf der Seite steht die **Seitenversion** |
| „Nicht aktualisiert“ auf der Live-Seite | Darunter steht der Grund (z. B. keine Verbindung, Wetterdienst gestört). Die Seite versucht es vorher selbst bis zu dreimal |
| Kein Knopf „Live-Wetter“ in der Push | Secret `WETTER_SEITE_URL` im Bot-Repository angelegt, mit `https://` am Anfang? |

---
Wetterdaten: [Open-Meteo.com](https://open-meteo.com) (CC BY 4.0, kostenlos für nicht-kommerzielle Nutzung) · Push: [ntfy.sh](https://ntfy.sh)
