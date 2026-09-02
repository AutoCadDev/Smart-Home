# Flur – Smart-Home-Planung

## Ziel

Der Flur soll umfassend in Home Assistant integriert werden.

Der Schwerpunkt liegt auf einer weitgehend automatischen Beleuchtung.

Das Licht soll abhängig von:

- Bewegung
- Raumhelligkeit
- Tageszeit
- Anwesenheitsstatus
- Nachtmodus

automatisch gesteuert werden.

Zusätzlich soll jederzeit eine manuelle Bedienung möglich bleiben.

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Deckenlampe | Hauptbeleuchtung |
| Spots an den Wänden | Akzent- / Ambientebeleuchtung |

Die Beleuchtung soll in Philips Hue integriert und zusätzlich über Home Assistant gesteuert werden.

---

## Grundprinzip der Lichtautomation

### Aktueller Zustand

Aktuell ist noch keine Hardware für die automatische Lichtsteuerung implementiert.

Die Umsetzung erfolgt nach Bezug der neuen Wohnung.

### Ziel

Beim Betreten des Flurs soll Home Assistant anhand von Bewegung, Helligkeit und Tageszeit entscheiden, welche Beleuchtung benötigt wird.

Grundprinzip:

```text
Bewegung im Flur erkannt
        +
Raumhelligkeit unter Grenzwert
        │
        ▼
passende Flurbeleuchtung aktivieren
        │
        ▼
keine Bewegung mehr
        │
        ▼
nach definierter Zeit ausschalten
```

Als erster Richtwert kann beispielsweise eine Nachlaufzeit von etwa 2 Minuten verwendet werden.

Die genaue Zeit wird später im realen Betrieb angepasst.

---

## Deckenlicht

Das Deckenlicht dient als helle Hauptbeleuchtung des Flurs.

Es soll insbesondere tagsüber bzw. am frühen Abend verwendet werden, wenn eine stärkere Beleuchtung benötigt wird.

Mögliche Automation:

```text
Bewegung erkannt
        +
Raumhelligkeit niedrig
        +
Tag / Abend
        │
        ▼
Deckenlicht einschalten
```

Wenn keine Bewegung mehr erkannt wird:

```text
keine Bewegung
        +
Nachlaufzeit abgelaufen
        │
        ▼
Deckenlicht ausschalten
```

---

## Spots an den Wänden

Die Spots sollen unabhängig vom Deckenlicht steuerbar sein.

Sie dienen hauptsächlich als:

- Ambientebeleuchtung
- Abendbeleuchtung
- Nachtbeleuchtung
- Orientierungslicht

Mögliche Abendautomation:

```text
Bewohner zuhause
        +
Abendzeit
        +
Raumhelligkeit niedrig
        │
        ▼
Spots gedimmt aktivieren
```

Dadurch kann im Flur eine dezente Grundbeleuchtung vorhanden sein, ohne dauerhaft das helle Deckenlicht einzuschalten.

---

## Nachtmodus

Für den Flur soll eine eigene Nachtlogik eingerichtet werden.

Nachts soll bei Bewegung nicht automatisch die volle Deckenbeleuchtung eingeschaltet werden.

Stattdessen sollen die Spots als schwaches Orientierungslicht verwendet werden.

Mögliche Automation:

```text
Nachtmodus aktiv
        +
Bewegung im Flur erkannt
        +
Raumhelligkeit niedrig
        │
        ▼
Spots sehr gedimmt einschalten
        │
        ▼
nach kurzer Zeit wieder ausschalten
```

Das Deckenlicht bleibt dabei ausgeschaltet.

Die genaue:

- Helligkeit
- Lichtfarbe
- Einschaltdauer
- Zeitspanne des Nachtmodus

wird später im realen Betrieb festgelegt.

---

## Bewegungserkennung

Der Flur ist hauptsächlich ein Durchgangsbereich.

Deshalb ist zunächst ein Bewegungs- und Helligkeitssensor ausreichend.

Er soll erkennen:

- Betreten des Flurs
- Bewegung im Flur
- aktuelle Raumhelligkeit

Eine dauerhafte Präsenzmessung ist zunächst nicht zwingend erforderlich.

Sollte sich später zeigen, dass die Bewegungserkennung nicht zuverlässig genug funktioniert, kann eine echte Präsenzmessung ergänzt werden.

---

## Sensorik

Im Flur sollen folgende Werte bzw. Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Helligkeit | ✅ |
| Bewegung | ✅ |
| Präsenz | optional |
| Temperatur | optional |
| Luftfeuchtigkeit | optional |

Wenn möglich, sollen Bewegung und Helligkeit durch einen geeigneten Kombisensor erfasst werden.

---

## Manuelle Bedienung

Die Beleuchtung soll trotz der Automationen jederzeit manuell steuerbar bleiben.

Mögliche Bedienwege:

- Home-Assistant-App
- Philips-Hue-App
- Tablet-Dashboard
- Sprachsteuerung
- physische Schalter / Taster

Manuell steuerbar bleiben sollen:

- Deckenlicht
- Spots
- Helligkeit
- Farben
- Hue-Szenen

Eine manuelle Bedienung soll nicht unmittelbar von der Bewegungsautomation überschrieben werden.

Die genaue Override-Logik wird später definiert.

---

## Zentrales Smart-Home-Tablet

Der Flur bzw. Eingangsbereich ist einer der möglichen Standorte für das zentrale Smart-Home-Tablet.

Der endgültige Standort ist noch offen.

Mögliche Positionen:

- Eingangsbereich / Flur
- Wohnzimmer

Sollte das Tablet im Flur montiert werden, dient es als zentrale Bedienstation für die gesamte Wohnung.

### Dashboard

Das Tablet soll nicht nur den Flur, sondern den Gesamtzustand der Wohnung darstellen.

Mögliche Anzeigen:

- Anwesenheitsstatus
- Temperaturen der Räume
- Luftfeuchtigkeit
- offene Fenster / Türen
- Lichtstatus
- aktive Szenen
- später Heizungsstatus
- später Rollladenstatus
- Sicherheitsstatus

Mögliche Steuerung:

- Räume
- Beleuchtung
- Szenen
- Gute-Nacht-Modus
- Abwesenheitsmodus
- später Heizung
- später Beschattung

---

## Sprachsteuerung

Auch im Flur sollen zentrale Funktionen per Sprache steuerbar sein.

Beispiele:

- Flurlicht ein / aus
- Spots ein / aus
- Gute Nacht
- alle Lichter ausschalten
- Abwesenheitsmodus aktivieren

Der konkrete Sprachassistent bzw. die Integration wird später festgelegt.

---

## Geplante Automationen

### Durchgangsbeleuchtung

```text
Bewegung erkannt
+
Helligkeit unter Grenzwert
+
Tag / Abend
→ Flurbeleuchtung einschalten
→ nach definierter Nachlaufzeit ausschalten
```

---

### Abendbeleuchtung

```text
Bewohner zuhause
+
Abendzeit
+
Helligkeit unter Grenzwert
→ Spots gedimmt aktivieren
```

---

### Nachtbeleuchtung

```text
Nachtmodus aktiv
+
Bewegung erkannt
+
Helligkeit unter Grenzwert
→ Spots sehr gedimmt einschalten
→ Deckenlicht bleibt aus
→ nach kurzer Zeit Spots ausschalten
```

---

### Abwesenheit

```text
Niemand zuhause
→ Flurbeleuchtung aus
→ Ambientebeleuchtung aus
→ später Sicherheitsmodus aktivieren
```

---

### Nach Hause kommen

Langfristig kann der Flur Teil einer zentralen Ankunftsautomation werden.

```text
Bewohner kommt nach Hause
        +
Wohnung war zuvor abwesend
        +
Raumhelligkeit niedrig
        │
        ▼
Flurbeleuchtung aktivieren
        │
        └── Zuhause-Modus aktivieren
```

---

### Wohnung verlassen

```text
letzter Bewohner verlässt Wohnung
        │
        ▼
Abwesenheitsmodus
        │
        ├── Flurbeleuchtung aus
        ├── übrige Beleuchtung prüfen
        └── später Sicherheitsmodus aktivieren
```

---

### Gute Nacht

```text
Gute Nacht aktiviert
        │
        ├── Deckenlicht aus
        ├── normale Flurbeleuchtung aus
        ├── Nachtmodus aktivieren
        └── Nacht-Orientierungslicht freigeben
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Hue-Beleuchtung integrieren
- [ ] Deckenlicht integrieren
- [ ] Spots integrieren
- [ ] Bewegung erfassen
- [ ] Helligkeit erfassen
- [ ] automatische Durchgangsbeleuchtung einrichten

### Phase 2 – Komfort

- [ ] helligkeitsabhängige Lichtautomation
- [ ] Abendbeleuchtung
- [ ] Nachtmodus
- [ ] gedimmtes Orientierungslicht
- [ ] Sprachsteuerung
- [ ] Tablet-Steuerung
- [ ] Anwesenheitslogik
- [ ] Ankunftsautomation
- [ ] Abwesenheitsautomation

### Phase 3 – Erweiterung

- [ ] endgültigen Tablet-Standort festlegen
- [ ] zentrales Wohnungs-Dashboard
- [ ] Präsenzsensor bei Bedarf ergänzen
- [ ] erweiterte Sicherheitsfunktionen

---

## Offene Punkte

- [ ] Bewegungs-/Helligkeitssensor auswählen
- [ ] Position des Sensors festlegen
- [ ] Lux-Grenzwert bestimmen
- [ ] Nachlaufzeit für das Flurlicht bestimmen
- [ ] Helligkeit der Abendbeleuchtung bestimmen
- [ ] Helligkeit und Farbe des Nachtlichts bestimmen
- [ ] Zeitraum für Nachtmodus definieren
- [ ] Tablet-Standort festlegen
- [ ] Sprachsteuerung festlegen
- [ ] Verhalten bei manueller Lichtsteuerung definieren
- [ ] Flurbeleuchtungs-Logik im realen Betrieb testen