# Schlafzimmer – Smart-Home-Planung

## Ziel

Das Schlafzimmer soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Philips-Hue-Beleuchtung
- helligkeits- und tageszeitabhängige Automationen
- dezente Ambientebeleuchtung
- Präsenz- und Bewegungserkennung
- Raumklima
- Fensterüberwachung
- Schlaf- und Nachtmodus
- spätere Heizungs- und Rollladensteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Deckenlampe | Haupt- und Stimmungsbeleuchtung |
| Spots | Akzentbeleuchtung |
| Lightstrip | indirekte Ambientebeleuchtung |
| 2 × Nachttischlampe | Stimmungs- und Nachtbeleuchtung |

Die vorhandene Philips-Hue-Installation soll weiterhin über die Hue-App nutzbar bleiben und zusätzlich in Home Assistant integriert werden.

---

## Lichtautomation

### Aktueller Zustand

Aktuell sind für das Schlafzimmer vorhanden:

- Lightstrip
- 2 × Nachttischlampe

Weitere Lampen und Spots sollen nach dem Bezug der neuen Wohnung und der endgültigen Einrichtung des Schlafzimmers ergänzt werden.

### Ziel

Die Beleuchtung soll eine dezente Ambientebeleuchtung bereitstellen, die sich an:

- Tageszeit
- Raumhelligkeit
- Anwesenheit
- Schlaf-/Nachtmodus

orientiert.

Die Beleuchtung soll zusätzlich jederzeit manuell über Schalter, Sprache oder App steuerbar bleiben.

Mögliche Grundlogik:

```text
Bewohner zuhause
        +
passender Tageszeitraum
        +
Raumhelligkeit unter Grenzwert
        +
kein Schlafmodus
        │
        ▼
Ambientebeleuchtung aktivieren
```

Der genaue Lux-Grenzwert wird später im laufenden Betrieb festgelegt.

Um häufiges Ein- und Ausschalten zu vermeiden, soll eine Verzögerung bzw. Hysterese eingebaut werden.

---

## Deckenlicht

Das Deckenlicht soll unabhängig von der Ambientebeleuchtung steuerbar sein.

Es dient als helle Grundbeleuchtung, wenn im Schlafzimmer mehr Licht benötigt wird.

Mögliche Automation:

```text
Präsenz im Schlafzimmer
        +
Raumhelligkeit niedrig
        +
kein Nacht-/Schlafmodus
        │
        ▼
Grundbeleuchtung verfügbar
```

Das Deckenlicht soll nicht automatisch eingeschaltet werden, wenn der Schlaf- oder Nachtmodus aktiv ist.

---

## Ambientebeleuchtung

Lightstrip, Nachttischlampen und spätere Spots sollen gemeinsam eine dezente Ambientebeleuchtung ermöglichen.

Mögliche Automation:

```text
Präsenz im Schlafzimmer
        +
Raumhelligkeit niedrig
        +
Abendzeit
        │
        ▼
Ambientebeleuchtung aktivieren
```

Dabei können:

- Lightstrip
- Nachttischlampen
- Spots

abhängig von der gewählten Szene unterschiedlich gesteuert werden.

---

## Nachttischlampen

Die beiden Nachttischlampen sollen unabhängig voneinander steuerbar bleiben.

Dadurch kann beispielsweise nur eine Bettseite beleuchtet werden, ohne die andere Person unnötig zu stören.

Mögliche Bedienung:

- physischer Schalter / Taster
- Sprache
- Home-Assistant-App
- Philips-Hue-App
- Tablet
- spätere Automationen

---

## Manuelle Bedienung

Die Beleuchtung soll jederzeit manuell steuerbar bleiben.

Mögliche Bedienwege:

- Home-Assistant-App
- Philips-Hue-App
- Tablet-Dashboard
- Sprachsteuerung
- physische Schalter / Taster

Manuell steuerbar bleiben sollen:

- Licht ein / aus
- Helligkeit
- Farben
- Hue-Szenen
- einzelne Lampen
- Deckenlicht
- Ambientebeleuchtung
- Nachttischlampen

Eine manuell gewählte Lichtstimmung soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Sensorik und Raumklima

Im Schlafzimmer sollen folgende Werte und Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Temperatur | ✅ |
| Luftfeuchtigkeit | ✅ |
| Helligkeit | ✅ |
| Präsenz | ✅ |
| Bewegung | ✅ |
| Fensterstatus | ✅ |

Wenn möglich, sollen mehrere Messwerte durch geeignete Kombisensoren abgedeckt werden.

---

## Präsenz

Eine echte Präsenzmessung ist gegenüber einem reinen Bewegungsmelder bevorzugt.

Im Schlafzimmer muss jedoch berücksichtigt werden, dass über längere Zeit kaum oder keine Bewegung stattfinden kann.

Das gilt insbesondere beim:

- Schlafen
- Lesen
- Liegen im Bett
- Fernsehen / Medienkonsum
- ruhigen Aufenthalt

Deshalb darf eine fehlende Bewegung nicht automatisch bedeuten, dass das Schlafzimmer nicht mehr belegt ist.

Die Präsenzlogik soll später mit dem Schlaf-/Nachtmodus kombiniert werden.

---

## Fenster

Für das Schlafzimmer soll der Fensterstatus erfasst werden.

Geplant ist ein Kontaktsensor.

Mögliche Nutzung:

- Fensterstatus im Dashboard
- Heizungssteuerung
- Gute-Nacht-Prüfung
- Sicherheitsprüfung
- Benachrichtigung bei Abwesenheit

Beispiel:

```text
Fenster geöffnet
        │
        ▼
Heizung Schlafzimmer pausieren
```

Die genaue Fenster- und Beschattungssituation wird nach Bezug der Wohnung dokumentiert.

---

## Heizung und Beschattung

### Heizung

Die konkrete Heizungssteuerung ist aktuell noch offen.

Zu klären:

- vorhandenes Heizsystem
- Art der Regelung
- Home-Assistant-Integration
- gewünschte Schlaftemperatur
- Nachtabsenkung
- Abwesenheitsabsenkung
- Verhalten bei geöffnetem Fenster

### Rollläden / Beschattung

Die konkrete Beschattung wird nach Bezug der Wohnung dokumentiert.

Langfristig soll eine elektrische Lösung nach Möglichkeit in Home Assistant integriert werden.

Mögliche spätere Automationen:

- Rollläden beim Gute-Nacht-Modus schließen
- automatisches Öffnen am Morgen
- Beschattung bei starker Sonneneinstrahlung
- Beschattung abhängig von Raumtemperatur
- Urlaubsmodus
- Abwesenheitsmodus

---

## Tablet und Sprachsteuerung

Ein zentrales Smart-Home-Tablet ist vorgesehen.

Der endgültige Standort ist noch offen:

- Wohnzimmer
- Eingangsbereich

### Schlafzimmer-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Helligkeit
- Präsenz
- Fensterstatus
- Lichtstatus
- Hue-Szenen
- später Heizung
- später Rollläden

Steuerung:

- Licht
- Farben
- Helligkeit
- Szenen
- Ambientebeleuchtung
- Nachttischlampen
- später Heizung
- später Beschattung

Zusätzlich sollen zentrale Funktionen per Sprache steuerbar sein.

---

## Geplante Automationen

### Ambientebeleuchtung

```text
Bewohner zuhause
+
Abendzeit
+
Helligkeit unter Grenzwert
+
kein Schlafmodus
→ Ambientebeleuchtung aktivieren
```

---

### Abendlicht

```text
Abendzeit
+
Helligkeit unter Grenzwert
+
Präsenz im Schlafzimmer
→ Spots / Lightstrip / Nachttischlampen passend dimmen
```

---

## Schlaf- und Nachtmodus

Für das Schlafzimmer soll eine eigene Nachtlogik eingerichtet werden.

Während des Schlafmodus sollen normale Präsenz- und Bewegungsautomationen keine helle Beleuchtung aktivieren.

```text
Schlafmodus aktiv
        +
Bewegung / Präsenz erkannt
        │
        ▼
Deckenlicht bleibt aus
```

Bei Bedarf kann stattdessen eine sehr schwache Orientierungsbeleuchtung verwendet werden.

```text
Nachtzeit
+
Schlafmodus aktiv
+
Bewegung erkannt
→ dezentes Orientierungslicht aktivieren
```

Die genaue:

- Helligkeit
- Farbe
- Einschaltdauer
- Zeitspanne

wird später im realen Betrieb festgelegt.

---

### Gute Nacht

Der Gute-Nacht-Modus soll das Schlafzimmer in einen definierten Schlafzustand versetzen.

```text
Gute Nacht aktiviert
        │
        ├── Deckenlicht aus
        ├── Spots aus
        ├── Ambientebeleuchtung reduzieren / ausschalten
        ├── Nachttischlampen nach Wunsch
        ├── Fensterstatus prüfen
        ├── Schlafmodus aktivieren
        ├── später Rollläden schließen
        └── später Heizung auf Nachtbetrieb
```

---

### Morgen

Langfristig kann eine Morgenautomation ergänzt werden.

```text
Morgen
+
Schlafmodus beendet
        │
        ├── Nachtmodus deaktivieren
        ├── später Rollläden öffnen
        └── normale Lichtautomation freigeben
```

---

### Abwesenheit

```text
Niemand zuhause
→ Schlafzimmerbeleuchtung aus
→ später Heizung reduzieren
→ später Sicherheitsmodus aktivieren
```

---

### Fenster geöffnet

```text
Fenster geöffnet
→ später Heizung Schlafzimmer pausieren
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] vorhandene Hue-Beleuchtung integrieren
- [ ] Helligkeit erfassen
- [ ] Temperatur erfassen
- [ ] Luftfeuchtigkeit erfassen
- [ ] Präsenz erkennen
- [ ] Fensterstatus erfassen
- [ ] Ambientebeleuchtung einrichten

### Phase 2 – Komfort

- [ ] helligkeitsabhängige Lichtautomation
- [ ] Ambientelicht-Szenen
- [ ] getrennte Steuerung der Nachttischlampen
- [ ] Gute-Nacht-Szene
- [ ] Schlaf-/Nachtmodus
- [ ] Orientierungslicht nachts
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung
- [ ] Anwesenheitslogik

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] elektrische Rollläden
- [ ] automatische Beschattung
- [ ] Morgenautomation
- [ ] erweiterte Schlafautomation

---

## Offene Punkte

- [ ] endgültige Beleuchtung nach Einrichtung festlegen
- [ ] Fenster- und Beschattungssituation dokumentieren
- [ ] Heizsystem klären
- [ ] Helligkeitssensor auswählen
- [ ] Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Fenstersensor auswählen
- [ ] Sprachsteuerung festlegen
- [ ] Lux-Grenzwert bestimmen
- [ ] Verhalten bei manueller Lichtsteuerung definieren
- [ ] Helligkeit des nächtlichen Orientierungslichts bestimmen
- [ ] Schlaf-/Nachtmodus definieren
- [ ] Schlafzimmer-Logik im realen Betrieb testen