# Küche – Smart-Home-Planung

## Ziel

Die Küche soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Philips-Hue-Beleuchtung
- helligkeitsabhängige Automationen
- Präsenz- und Bewegungserkennung
- Raumklima
- Fensterüberwachung
- Wasserschutz
- spätere Heizungs- und Rollladensteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Spot Wand links | Akzentbeleuchtung |
| Spot rechts | Akzentbeleuchtung |
| Lightstrip Küchenzeile | Arbeits- / indirekte Beleuchtung |
| Lampe Esstisch | Haupt- und Stimmungsbeleuchtung |

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
Küchen-Szene aktivieren
```

Dadurch kann die Beleuchtung beispielsweise an einem dunklen Regentag früher eingeschaltet werden als an einem hellen Sommertag.

Der genaue Lux-Grenzwert wird später im laufenden Betrieb festgelegt.

Um häufiges Ein- und Ausschalten zu vermeiden, soll eine Verzögerung bzw. Hysterese eingebaut werden.

---

## Arbeitslicht

Das Licht an der Küchenzeile soll unabhängig von der allgemeinen Ambientebeleuchtung steuerbar sein.

Ziel ist eine eigene Logik für das Arbeitslicht.

Mögliche Automation:

```text
Präsenz in der Küche
        +
Raumhelligkeit niedrig
        │
        ▼
Grundbeleuchtung aktivieren
```

Optional zusätzlich:

```text
Arbeitslicht aktiviert
        │
        ▼
Lightstrip Küchenzeile heller
        │
        └── übrige Ambientebeleuchtung bleibt unabhängig
```

Dadurch kann beim Kochen gezielt eine höhere Helligkeit an der Arbeitsfläche genutzt werden, ohne die komplette Küchenbeleuchtung verändern zu müssen.

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
- Arbeitslicht

Eine manuell gewählte Lichtstimmung soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Sensorik und Raumklima

Im Küchenbereich sollen folgende Werte und Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Temperatur | ✅ |
| Luftfeuchtigkeit | ✅ |
| Helligkeit | ✅ |
| Präsenz | ✅ |
| Bewegung | ✅ |
| Fensterstatus | ✅ |
| Wasserleck | ✅ |

Wenn möglich, sollen mehrere Messwerte durch geeignete Kombisensoren abgedeckt werden.

---

## Präsenz

Eine echte Präsenzmessung ist gegenüber einem reinen Bewegungsmelder bevorzugt.

Das ist besonders wichtig bei:

- Kochen
- Vorbereiten von Speisen
- Hausarbeiten
- Sitzen am Esstisch
- längerem Aufenthalt ohne große Bewegung

Da sich der Esstisch in der Nähe der Küche befindet, soll das System möglichst erkennen können, dass sich weiterhin Personen im Küchen-/Essbereich aufhalten, auch wenn diese sich nur wenig bewegen.

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
Heizung Küche pausieren
```

---

## Wasserschutz

Für die Küche soll mindestens ein Wassersensor vorgesehen werden.

Mögliche Positionen:

- unter der Spüle
- im Bereich der Spülmaschine

Ziel:

```text
Wasser erkannt
        │
        ▼
Home Assistant
        │
        ├── sofortige Benachrichtigung
        ├── Warnung auf dem Tablet
        └── optional spätere weitere Sicherheitsaktion
```

Die konkrete Position und Hardware werden später festgelegt.

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

### Küchen-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Helligkeit
- Präsenz
- Fensterstatus
- Lichtstatus
- Hue-Szenen
- Wassersensorstatus
- später Rollläden und Heizung

Steuerung:

- Licht
- Farben
- Helligkeit
- Szenen
- Arbeitslicht
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
→ Küchen-Szene aktivieren
```

### Arbeitslicht

```text
Küche in Benutzung
+
Helligkeit zu niedrig
→ Arbeitslicht aktivieren
```

### Abwesenheit

```text
Niemand zuhause
→ Küchenbeleuchtung aus
→ später Heizung reduzieren
→ später Sicherheitsmodus aktivieren
```

### Fenster geöffnet

```text
Fenster geöffnet
→ später Heizung Küche pausieren
```

### Wasser erkannt

```text
Wasserleck erkannt
→ sofortige Benachrichtigung
→ Warnung auf Tablet
```

### Gute Nacht

```text
Gute Nacht
→ Küchenbeleuchtung aus
→ Fensterstatus prüfen
→ Wassersensor prüfen
→ später Rollläden schließen
→ später Heizung auf Nachtbetrieb
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
- [ ] Wassersensor integrieren

### Phase 2 – Komfort

- [ ] helligkeitsabhängige Lichtautomation
- [ ] separate Arbeitslicht-Automation
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung
- [ ] Küchen-Szene
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
- [ ] Wassersensor auswählen
- [ ] Position des Wassersensors festlegen
- [ ] elektrische Rollladenlösung auswählen
- [ ] Sprachsteuerung festlegen
- [ ] Lux-Grenzwert bestimmen
- [ ] Verhalten bei manueller Lichtsteuerung definieren
- [ ] Arbeitslicht-Logik im realen Betrieb testen