# Kinderzimmer Luca – Smart-Home-Planung

## Ziel

Das Zimmer von Luca soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Philips-Hue-Beleuchtung
- helligkeitsabhängige Automationen
- Präsenz- und Bewegungserkennung
- Raumklima
- Fensterüberwachung
- kindgerechte Nachtbeleuchtung
- spätere Heizungs- und Rollladensteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Deckenlampe | Haupt- und Stimmungsbeleuchtung |
| 2 × Spot | Akzentbeleuchtung |
| Lightstrip | Akzent- / indirekte Beleuchtung |

Die vorhandene Philips-Hue-Installation soll weiterhin über die Hue-App nutzbar bleiben und zusätzlich in Home Assistant integriert werden.

---

## Lichtautomation

### Aktueller Zustand

Aktuell werden bereits verschiedene Philips-Hue-Szenen verwendet.

Diese werden zu festen Uhrzeiten:

- eingeschaltet
- ausgeschaltet

### Ziel

Die Beleuchtung soll zukünftig zusätzlich von der tatsächlichen Raumhelligkeit und der Tageszeit abhängen.

```text
Bewohner zuhause
        +
passender Tageszeitraum
        +
Raumhelligkeit unter Grenzwert
        │
        ▼
Kinderzimmer-Luca-Szene aktivieren
```

Dadurch kann die Beleuchtung beispielsweise an einem dunklen Regentag früher eingeschaltet werden als an einem hellen Sommertag.

Der genaue Lux-Grenzwert wird später im laufenden Betrieb festgelegt.

Um häufiges Ein- und Ausschalten zu vermeiden, soll eine Verzögerung bzw. Hysterese eingebaut werden.

---

## Deckenlicht

Das Deckenlicht soll unabhängig von der allgemeinen Ambientebeleuchtung steuerbar sein.

Es dient als helle Grundbeleuchtung, wenn im Zimmer mehr Licht benötigt wird.

Mögliche Automation:

```text
Präsenz im Kinderzimmer
        +
Raumhelligkeit niedrig
        +
kein Nachtmodus
        │
        ▼
Grundbeleuchtung aktivieren
```

Das Deckenlicht soll insbesondere nachts nicht automatisch eingeschaltet werden.

---

## Ambientebeleuchtung

Der Lightstrip und die Spots sollen für eine dezente Ambientebeleuchtung genutzt werden.

Mögliche Automation:

```text
Präsenz im Kinderzimmer
        +
Raumhelligkeit niedrig
        +
Abendzeit
        │
        ▼
Ambientebeleuchtung aktivieren
```

Dadurch kann im Zimmer eine angenehme Beleuchtung bereitgestellt werden, ohne automatisch das helle Deckenlicht einzuschalten.

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

Eine manuell gewählte Lichtstimmung soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Sensorik und Raumklima

Im Zimmer von Luca sollen folgende Werte und Zustände erfasst werden:

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

Das ist besonders wichtig bei:

- Spielen
- Schlafen
- ruhigem Aufenthalt
- Versorgung des Babys
- längeren Phasen mit wenig Bewegung

Da Luca noch ein Baby ist, darf eine fehlende Bewegung nicht automatisch bedeuten, dass das Zimmer nicht mehr belegt ist.

Die Präsenzlogik soll deshalb später mit dem Nacht- und Schlafmodus kombiniert werden.

---

## Fenster

### Aktuell

- 1 Fenster
- manuelle Beschattung

### Später

- elektrische Beschattung vorgesehen

Für das Fenster ist ein Kontaktsensor vorgesehen.

Mögliche Nutzung:

- Fensterstatus im Dashboard
- Heizungssteuerung
- Sicherheitsprüfung
- Gute-Nacht-Prüfung
- Benachrichtigung bei Abwesenheit

Beispiel:

```text
Fenster geöffnet
        │
        ▼
Heizung Kinderzimmer Luca pausieren
```

---

## Heizung und Beschattung

### Heizung

Die konkrete Heizungssteuerung ist aktuell noch offen.

Zu klären:

- vorhandenes Heizsystem
- Art der Regelung
- Home-Assistant-Integration
- gewünschte Raumtemperatur
- Nachtabsenkung
- Abwesenheitsabsenkung
- Verhalten bei geöffnetem Fenster

### Rollläden / Beschattung

Aktuell erfolgt die Bedienung manuell.

Langfristig ist eine elektrische Lösung vorgesehen.

Mögliche spätere Automationen:

- Beschattung bei starker Sonneneinstrahlung
- Beschattung abhängig von Raumtemperatur
- automatisches Öffnen am Morgen
- automatisches Schließen am Abend
- Gute-Nacht-Automation
- Urlaubsmodus
- Abwesenheitsmodus

---

## Tablet und Sprachsteuerung

Ein zentrales Smart-Home-Tablet ist vorgesehen.

Der endgültige Standort ist noch offen:

- Wohnzimmer
- Eingangsbereich

### Luca-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Helligkeit
- Präsenz
- Fensterstatus
- Lichtstatus
- Hue-Szenen
- später Rollläden und Heizung

Steuerung:

- Licht
- Farben
- Helligkeit
- Szenen
- Deckenlicht
- Ambientebeleuchtung
- später Heizung
- später Beschattung

Zusätzlich sollen zentrale Funktionen per Sprache steuerbar sein.

---

## Geplante Automationen

### Spielen-Szene

```text
Bewohner zuhause
+
passender Tageszeitraum
+
Helligkeit unter Grenzwert
→ Spielen-Szene aktivieren
```

---

### Abendlicht

```text
Bewohner zuhause
+
Abendzeit
+
Helligkeit unter Grenzwert
→ Kinderzimmer-Luca-Abendszene aktivieren
```

---

### Automatische Grundbeleuchtung

```text
Präsenz im Kinderzimmer
+
Helligkeit zu niedrig
+
kein Nachtmodus
→ Grundbeleuchtung aktivieren
```

---

## Nachtmodus

Für das Kinderzimmer soll eine eigene Nachtlogik eingerichtet werden.

Nachts soll bei Bewegung oder Präsenz nicht automatisch das helle Deckenlicht eingeschaltet werden.

Stattdessen soll bei Bedarf eine sehr schwache Ambientebeleuchtung genutzt werden.

Mögliche Automation:

```text
Nachtzeit
        +
Präsenz oder Bewegung erkannt
        +
Raum dunkel
        │
        ▼
Lightstrip sehr gedimmt einschalten
        │
        └── Deckenlicht bleibt aus
```

Das kann insbesondere hilfreich sein bei:

- nächtlicher Versorgung
- Wickeln
- Füttern
- kurzem Betreten des Zimmers
- Orientierung in der Nacht

Die genaue:

- Helligkeit
- Farbe
- Zeitspanne
- Einschaltdauer

wird später im realen Betrieb festgelegt.

---

### Abwesenheit

```text
Niemand zuhause
→ Kinderzimmer-Luca-Beleuchtung aus
→ später Heizung reduzieren
→ später Sicherheitsmodus aktivieren
```

---

### Fenster geöffnet

```text
Fenster geöffnet
→ später Heizung Kinderzimmer Luca pausieren
```

---

### Gute Nacht

Die Gute-Nacht-Szene soll das Zimmer in einen ruhigen Nachtzustand versetzen.

```text
Gute Nacht
        │
        ├── Deckenlicht aus
        ├── Spots aus oder stark dimmen
        ├── Lightstrip als dezentes Nachtlicht
        ├── Fensterstatus prüfen
        ├── Nachtmodus aktivieren
        ├── später Rollläden schließen
        └── später Heizung auf Nachtbetrieb
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Hue-Beleuchtung integrieren
- [ ] vorhandene Hue-Szenen integrieren
- [ ] Helligkeit erfassen
- [ ] Temperatur erfassen
- [ ] Luftfeuchtigkeit erfassen
- [ ] Präsenz erkennen
- [ ] Fensterstatus erfassen

### Phase 2 – Komfort

- [ ] helligkeitsabhängige Lichtautomation
- [ ] Spielen-Szene
- [ ] separate Deckenlicht-Automation
- [ ] Nachtmodus
- [ ] Gute-Nacht-Szene
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung
- [ ] Anwesenheitslogik

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] elektrische Rollläden
- [ ] automatische Beschattung
- [ ] erweiterte Sicherheitsfunktionen

---

## Offene Punkte

- [ ] Heizsystem klären
- [ ] Tablet-Standort festlegen
- [ ] Helligkeitssensor auswählen
- [ ] Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Fenstersensor auswählen
- [ ] elektrische Rollladenlösung auswählen
- [ ] Sprachsteuerung festlegen
- [ ] Lux-Grenzwert bestimmen
- [ ] Verhalten bei manueller Lichtsteuerung definieren
- [ ] Helligkeit des Nachtlichts bestimmen
- [ ] Farbe des Nachtlichts bestimmen
- [ ] Zeitraum für Nachtmodus definieren
- [ ] Lichtlogik im realen Betrieb testen