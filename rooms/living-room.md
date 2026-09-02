# Wohnzimmer – Smart-Home-Planung

## Ziel

Das Wohnzimmer soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Philips-Hue-Beleuchtung
- helligkeitsabhängige Automationen
- Raumklima und Präsenz
- Multimedia
- Fenster- und Balkontürüberwachung
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

Die Beleuchtung soll zukünftig zusätzlich von der tatsächlichen Raumhelligkeit, Tageszeit und Nutzung des Wohnzimmers abhängen.

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
- Multimedia-Szenen

Eine manuell gewählte Lichtstimmung soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Multimedia

Vorhandene Geräte:

- TV
- Heimkino
- PlayStation

Die Geräte sollen später auf ihre Integrationsmöglichkeiten mit Home Assistant geprüft werden.

Ziel ist, Multimedia und Beleuchtung sinnvoll miteinander zu verknüpfen.

---

## Fernsehen

Beim Einschalten des Fernsehers soll optional eine passende TV-Szene aktiviert werden.

Mögliche spätere Automation:

```text
TV eingeschaltet
        +
Raumhelligkeit niedrig
        │
        ▼
TV-Szene aktivieren
        │
        ├── Hue Play einschalten
        ├── Lightstrip TV einschalten
        ├── Lightstrip Lowboard anpassen
        ├── restliches Licht reduzieren
        └── Decken-/Hauptbeleuchtung vermeiden
```

Wird der Fernseher ausgeschaltet, soll die vorherige oder eine passende normale Wohnzimmerbeleuchtung wiederhergestellt werden können.

---

## Gaming

Beim Starten der PlayStation soll optional eine eigene Gaming-Szene aktiviert werden.

Mögliche spätere Automation:

```text
PlayStation aktiv
        +
Raumhelligkeit niedrig
        │
        ▼
Gaming-Szene aktivieren
        │
        ├── Hue Play
        ├── Lightstrip TV
        ├── Lightstrip Lowboard
        └── Gaming-Farbschema
```

Die Gaming-Szene soll unabhängig von der normalen Abendbeleuchtung steuerbar bleiben.

---

## Heimkino

Das vorhandene Heimkino soll später ebenfalls auf Integrationsmöglichkeiten geprüft werden.

Mögliche Nutzung:

- automatisches Einschalten zusammen mit dem TV
- Lautstärke- oder Eingangssteuerung
- Statusanzeige im Dashboard
- Kombination mit TV- und Gaming-Szenen

Die konkrete Umsetzung hängt von den verfügbaren Schnittstellen des Heimkinosystems ab.

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

---

## Präsenz

Eine echte Präsenzmessung ist gegenüber einem reinen Bewegungsmelder bevorzugt.

Das ist besonders wichtig bei:

- Fernsehen
- Gaming
- Lesen
- Sitzen auf dem Sofa
- längeren ruhigen Aufenthalten

Das System soll erkennen können, dass sich weiterhin Personen im Wohnzimmer befinden, auch wenn nur wenig Bewegung stattfindet.

Zusätzlich können später weitere Zustände als Hinweis auf eine aktive Nutzung des Wohnzimmers dienen.

Beispiele:

- TV eingeschaltet
- PlayStation aktiv
- Heimkino aktiv

Dadurch soll verhindert werden, dass Beleuchtung oder andere Automationen während der Nutzung unbeabsichtigt deaktiviert werden.

---

## Fenster und Balkontür

### Fenster

Aktuell ist ein Fenster vorhanden.

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
Heizung Wohnzimmer pausieren
```

### Balkontür

Zusätzlich soll später die große Balkontür überwacht werden.

Für die Balkontür ist ebenfalls ein Kontaktsensor vorgesehen.

Mögliche Nutzung:

- Balkontürstatus im Dashboard
- Heizungssteuerung
- Sicherheitsprüfung
- Abwesenheitsprüfung
- Gute-Nacht-Prüfung

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
- Verhalten bei geöffnetem Fenster oder geöffneter Balkontür

### Rollläden / Beschattung

Aktuell erfolgt die Bedienung manuell.

Langfristig ist eine elektrische Lösung vorgesehen.

Mögliche spätere Automationen:

- Beschattung bei starker Sonneneinstrahlung
- Beschattung abhängig von Raumtemperatur
- automatisches Öffnen am Morgen
- automatisches Schließen am Abend
- TV-Modus mit angepasster Beschattung
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
- Balkontürstatus
- Lichtstatus
- Hue-Szenen
- TV-Status
- PlayStation-Status
- Heimkino-Status
- später Rollläden und Heizung

Steuerung:

- Licht
- Farben
- Helligkeit
- Szenen
- TV-Szene
- Gaming-Szene
- Multimedia
- später Heizung
- später Beschattung

Zusätzlich sollen zentrale Funktionen per Sprache steuerbar sein.

---

## Geplante Automationen

### Abendlicht

```text
Bewohner zuhause
+
Abendzeit
+
Helligkeit unter Grenzwert
+
keine spezielle Multimedia-Szene aktiv
→ Wohnzimmer-Szene aktivieren
```

---

### TV-Szene

```text
TV eingeschaltet
+
Helligkeit unter Grenzwert
→ TV-Szene aktivieren
```

---

### Gaming-Szene

```text
PlayStation aktiv
+
Helligkeit unter Grenzwert
→ Gaming-Szene aktivieren
```

---

### Multimedia beendet

```text
TV / PlayStation ausgeschaltet
+
Bewohner weiterhin im Wohnzimmer
        │
        ▼
passende normale Wohnzimmer-Szene aktivieren
```

---

### Abwesenheit

```text
Niemand zuhause
        │
        ├── Wohnzimmerbeleuchtung aus
        ├── Multimedia prüfen / ausschalten
        ├── später Heizung reduzieren
        └── später Sicherheitsmodus aktivieren
```

---

### Fenster oder Balkontür geöffnet

```text
Fenster oder Balkontür geöffnet
→ später Heizung Wohnzimmer pausieren
```

---

### Gute Nacht

```text
Gute Nacht
        │
        ├── Wohnzimmerbeleuchtung aus
        ├── TV-Status prüfen
        ├── PlayStation-Status prüfen
        ├── Heimkino-Status prüfen
        ├── Fensterstatus prüfen
        ├── Balkontürstatus prüfen
        ├── später Rollläden schließen
        └── später Heizung auf Nachtbetrieb
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
- [ ] Multimedia-Status erfassen
- [ ] Anwesenheitslogik
- [ ] Rückkehr zur normalen Wohnzimmer-Szene nach Multimedia-Nutzung

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] elektrische Rollläden
- [ ] Balkontürsensor
- [ ] automatische Beschattung
- [ ] Heimkino vollständig integrieren
- [ ] erweiterte Multimedia-Automationen
- [ ] TV-abhängige Beschattung

---

## Offene Punkte

- [ ] Heizsystem klären
- [ ] Tablet-Standort festlegen
- [ ] Helligkeitssensor auswählen
- [ ] Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Fenstersensor auswählen
- [ ] Balkontürsensor auswählen
- [ ] elektrische Rollladenlösung auswählen
- [ ] Sprachsteuerung festlegen
- [ ] TV-Integration prüfen
- [ ] Heimkino-Integration prüfen
- [ ] PlayStation-Integration prüfen
- [ ] Lux-Grenzwert bestimmen
- [ ] Verhalten bei manueller Lichtsteuerung definieren
- [ ] Verhalten beim Beenden einer Multimedia-Szene definieren
- [ ] Wohnzimmer-Logik im realen Betrieb testen