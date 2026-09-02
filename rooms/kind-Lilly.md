# Kinderzimmer Lilly – Smart-Home-Planung

## Ziel

Das Zimmer von Lilly soll umfassend in Home Assistant integriert werden.

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

Die Beleuchtung soll zukünftig zusätzlich von der tatsächlichen Raumhelligkeit abhängen.

```text
Bewohner zuhause
        +
passender Tageszeitraum
        +
Raumhelligkeit unter Grenzwert
        │
        ▼
Kinderzimmer-Lilly-Szene aktivieren
```

Dadurch kann die Beleuchtung beispielsweise an einem dunklen Regentag früher eingeschaltet werden als an einem hellen Sommertag.

Der genaue Lux-Grenzwert wird später im laufenden Betrieb festgelegt.

Um häufiges Ein- und Ausschalten zu vermeiden, soll eine Verzögerung bzw. Hysterese eingebaut werden.

---

## Deckenlicht

Das Deckenlicht soll unabhängig von der allgemeinen Ambientebeleuchtung steuerbar sein.

Ziel ist eine eigene Logik für das Deckenlicht.

Mögliche Automation:

```text
Präsenz im Kinderzimmer
        +
Raumhelligkeit niedrig
        │
        ▼
Grundbeleuchtung aktivieren
```

Optional zusätzlich:

```text
Deckenlicht aktiviert
        │
        ▼
helle Beleuchtung für Spielen / Lernen
        │
        └── übrige Ambientebeleuchtung bleibt unabhängig
```

Dadurch kann beim Spielen, Lernen oder bei den Hausaufgaben gezielt eine höhere Helligkeit im Kinderzimmer genutzt werden, ohne die komplette Ambientebeleuchtung verändern zu müssen.

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

Im Zimmer von Lilly sollen folgende Werte und Zustände erfasst werden:

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
- Lernen
- Hausaufgaben
- Lesen
- ruhigem Aufenthalt im Zimmer

Der Präsenzsensor soll zuverlässig erkennen können, dass sich Lilly weiterhin im Zimmer befindet, auch wenn sie beispielsweise beim Lesen, Lernen oder Spielen längere Zeit ruhig sitzt.

Dadurch soll verhindert werden, dass Beleuchtung oder andere Automationen unbeabsichtigt ausgeschaltet werden.

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
Heizung Kinderzimmer Lilly pausieren
```

---

## Heizung und Beschattung

### Heizung

Die konkrete Heizungssteuerung ist aktuell noch offen.

Zu klären:

- vorhandenes Heizsystem
- Art der Regelung
- Home-Assistant-Integration
- gewünschte Temperatursteuerung
- Nachtabsenkung
- Abwesenheitsabsenkung

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

### Lilly-Dashboard

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

Für das Spielen soll eine ausreichend helle und angenehme Beleuchtung zur Verfügung stehen.

```text
Bewohner zuhause
+
passender Tageszeitraum
+
Helligkeit unter Grenzwert
→ Spielen-Szene aktivieren
```

---

### Lernen / Hausaufgaben

Beim Lernen oder bei Hausaufgaben soll eine hellere Beleuchtung genutzt werden.

```text
Lernen-Szene aktiviert
        │
        ▼
Deckenlicht hell
        +
geeignete Lichtfarbe
        +
Ambientebeleuchtung optional
```

Die Szene soll zunächst manuell per App, Sprache, Tablet oder Schalter aktiviert werden können.

---

### Abendlicht

Am Abend soll eine ruhigere Lichtstimmung verwendet werden.

```text
Bewohner zuhause
+
Abendzeit
+
Helligkeit unter Grenzwert
→ Kinderzimmer-Lilly-Abendszene aktivieren
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

Für das Kinderzimmer soll eine eigene Nachtlogik vorgesehen werden.

Ziel ist, dass nachts bei erkannter Präsenz nicht automatisch die helle Hauptbeleuchtung eingeschaltet wird.

Stattdessen soll eine sehr schwache Ambientebeleuchtung zur Orientierung verwendet werden.

Mögliche Automation:

```text
Nachtzeit
        +
Präsenz erkannt
        +
Raum dunkel
        │
        ▼
Lightstrip sehr gedimmt einschalten
        │
        └── Deckenlicht bleibt aus
```

Dadurch kann Lilly sich nachts im Zimmer orientieren, ohne dass eine helle Beleuchtung eingeschaltet werden muss.

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
→ Kinderzimmer-Lilly-Beleuchtung aus
→ später Heizung reduzieren
→ später Sicherheitsmodus aktivieren
```

---

### Fenster geöffnet

```text
Fenster geöffnet
→ später Heizung Kinderzimmer Lilly pausieren
```

---

### Gute Nacht

Die Gute-Nacht-Szene soll das Zimmer in einen ruhigen Nachtzustand versetzen.

```text
Gute Nacht
        │
        ├── Deckenlicht aus
        ├── Spots aus
        ├── Lightstrip als gedimmtes Nacht-/Ambientelicht
        ├── Fensterstatus prüfen
        ├── später Rollläden schließen
        └── später Heizung auf Nachtbetrieb
```

Das Nachtlicht soll unabhängig von der normalen Tagesautomation arbeiten.

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
- [ ] Lern-/Hausaufgaben-Szene
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
- [ ] Lichtlogik im realen Betrieb testen
- [ ] Helligkeit des Nachtlichts bestimmen
- [ ] Farbe des Nachtlichts bestimmen
- [ ] Zeitfenster für Nachtmodus festlegen