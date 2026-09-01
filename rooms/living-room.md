# Wohnzimmer – Smart-Home-Planung

## Ziel

Das Wohnzimmer soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Philips-Hue-Beleuchtung
- helligkeitsabhängige Automationen
- Raumklima und Präsenz
- Multimedia
- Fensterüberwachung
- spätere Heizungs- und Rollladensteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Color Spot Aquarium | Akzentbeleuchtung |
| Spot Wandpaneel | Akzentbeleuchtung |
| Hue Play 1 | TV-/Ambientebeleuchtung |
| Hue Play 2 | TV-/Ambientebeleuchtung |
| Hue Play 3 | TV-/Ambientebeleuchtung |
| Lightstrip Lowboard | indirekte Beleuchtung |
| Lightstrip TV | TV-Hintergrundbeleuchtung |
| Color Spot Wand | Akzentbeleuchtung |
| Lampe Ofen | Ambientebeleuchtung |

Die vorhandene Philips-Hue-Installation soll weiterhin über die Hue-App nutzbar bleiben und zusätzlich in Home Assistant integriert werden.

---

## Lichtautomation

### Aktueller Zustand

Aktuell wird bereits eine Philips-Hue-Szene verwendet.

Diese wird zu einer festen Uhrzeit:

- eingeschaltet
- ausgeschaltet

### Ziel

Die Szene soll zukünftig zusätzlich von der tatsächlichen Raumhelligkeit abhängen.

```text
Bewohner zuhause
        +
passender Tageszeitraum
        +
Raumhelligkeit unter Grenzwert
        │
        ▼
Wohnzimmer-Szene aktivieren
```

Dadurch kann die Beleuchtung beispielsweise an einem dunklen Regentag früher eingeschaltet werden als an einem hellen Sommertag.

Der genaue Lux-Grenzwert wird später im laufenden Betrieb festgelegt.

Um häufiges Ein- und Ausschalten zu vermeiden, soll eine Verzögerung bzw. Hysterese eingebaut werden.

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

Eine manuell gewählte Lichtstimmung soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Multimedia

Vorhandene Geräte:

- TV
- Heimkino
- PlayStation

Die Geräte sollen später auf ihre Integrationsmöglichkeiten mit Home Assistant geprüft werden.

### Fernsehen

Mögliche spätere Automation:

```text
TV eingeschaltet
        │
        ▼
TV-Szene aktivieren
        │
        ├── Hue Play einschalten
        ├── Lightstrip TV einschalten
        ├── Lightstrip Lowboard anpassen
        └── restliches Licht reduzieren
```

### Gaming

Mögliche spätere Automation:

```text
PlayStation aktiv
        │
        ▼
Gaming-Szene aktivieren
        │
        ├── Hue Play
        ├── Lightstrip TV
        ├── Lightstrip Lowboard
        └── Gaming-Farbschema
```

---

## Sensorik und Raumklima

Im Wohnzimmer sollen folgende Werte und Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Temperatur | ✅ |
| Luftfeuchtigkeit | ✅ |
| Helligkeit | ✅ |
| Präsenz | ✅ |
| Bewegung | ✅ |
| Fensterstatus | ✅ |
| Balkontürstatus | später |

Wenn möglich, sollen mehrere Messwerte durch geeignete Kombisensoren abgedeckt werden.

### Präsenz

Eine echte Präsenzmessung ist gegenüber einem reinen Bewegungsmelder bevorzugt.

Das ist besonders wichtig bei:

- Fernsehen
- Spielen
- Lesen
- Sitzen auf dem Sofa

Das System soll also erkennen können, dass noch jemand im Wohnzimmer ist, auch wenn sich die Person nur wenig bewegt.

---

## Fenster und Balkontür

### Aktuell

- 1 Fenster
- manuelle Beschattung

### Später

- große Balkontür
- elektrische Beschattung

Für Fenster und Balkontür sind Kontaktsensoren vorgesehen.

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
Heizung Wohnzimmer pausieren
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
- Urlaubsmodus
- Abwesenheitsmodus

---

## Tablet und Sprachsteuerung

Ein zentrales Smart-Home-Tablet ist vorgesehen.

Der endgültige Standort ist noch offen:

- Wohnzimmer
- Eingangsbereich

### Wohnzimmer-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Helligkeit
- Präsenz
- Fensterstatus
- Lichtstatus
- Hue-Szenen
- Multimedia
- später Rollläden und Heizung

Steuerung:

- Licht
- Farben
- Helligkeit
- Szenen
- Multimedia-Szenen
- später Heizung
- später Beschattung

Zusätzlich sollen zentrale Funktionen per Sprache steuerbar sein.

---

## Geplante Automationen

### Abendlicht

```text
Bewohner zuhause
+
passender Tageszeitraum
+
Helligkeit unter Grenzwert
→ Wohnzimmer-Szene aktivieren
```

### Abwesenheit

```text
Niemand zuhause
→ Licht aus
→ später Heizung reduzieren
→ später Sicherheitsmodus aktivieren
```

### Gute Nacht

```text
Gute Nacht
→ Wohnzimmerbeleuchtung aus
→ Multimedia prüfen
→ Fensterstatus prüfen
→ später Rollläden schließen
→ später Heizung auf Nachtbetrieb
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Hue-Beleuchtung integrieren
- [ ] vorhandene Hue-Szene integrieren
- [ ] Helligkeit erfassen
- [ ] Temperatur erfassen
- [ ] Luftfeuchtigkeit erfassen
- [ ] Präsenz erkennen
- [ ] Fensterstatus erfassen

### Phase 2 – Komfort

- [ ] helligkeitsabhängige Lichtautomation
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung
- [ ] TV-Szene
- [ ] Gaming-Szene
- [ ] Anwesenheitslogik

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] elektrische Rollläden
- [ ] Balkontürsensor
- [ ] automatische Beschattung
- [ ] erweiterte Multimedia-Automationen

---

## Offene Punkte

- [ ] Heizsystem klären
- [ ] Tablet-Standort festlegen
- [ ] Helligkeitssensor auswählen
- [ ] Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Fenstersensor auswählen
- [ ] Balkontür berücksichtigen
- [ ] elektrische Rollladenlösung auswählen
- [ ] Sprachsteuerung festlegen
- [ ] TV-Integration prüfen
- [ ] Heimkino-Integration prüfen
- [ ] PlayStation-Integration prüfen
- [ ] Lux-Grenzwert bestimmen
- [ ] Verhalten bei manueller Lichtsteuerung definieren