# Hauptbad – Smart-Home-Planung

## Ziel

Das Hauptbad soll umfassend in Home Assistant integriert werden.

Schwerpunkte:

- intelligente Beleuchtung
- automatische Lichtsteuerung
- Präsenz- und Bewegungserkennung
- Temperatur und Luftfeuchtigkeit
- Feuchtigkeitsüberwachung nach Duschen und Baden
- Wasserschutz
- Fensterüberwachung
- spätere Heizungssteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Raumausstattung

Das Hauptbad verfügt über:

- WC
- Dusche
- Badewanne

Die genaue Position und Anzahl von Fenstern sowie die vorhandene Lüftung werden nach Bezug der Wohnung dokumentiert.

---

## Beleuchtung

### Vorhandene / geplante Lichtbereiche

| Licht | Typ / Verwendung |
|---|---|
| Deckenbeleuchtung | Hauptbeleuchtung |
| Spiegelbeleuchtung | Funktionsbeleuchtung |
| Dusche / Badewanne | optionale Akzentbeleuchtung |
| indirekte Beleuchtung | optionale Ambientebeleuchtung / Nachtlicht |

Die genaue Beleuchtung wird nach Einrichtung des Badezimmers festgelegt.

---

## Lichtautomation

Die Beleuchtung soll abhängig von:

- Präsenz
- Bewegung
- Raumhelligkeit
- Tageszeit
- Nachtmodus

gesteuert werden können.

Mögliche Grundlogik:

```text
Präsenz im Badezimmer
        +
Raumhelligkeit niedrig
        +
kein Nachtmodus
        │
        ▼
Badbeleuchtung aktivieren
```

Eine automatische Abschaltung soll erst erfolgen, wenn sicher keine Person mehr im Badezimmer erkannt wird.

---

## Nachtmodus

Nachts soll beim Betreten des Badezimmers nicht automatisch die volle Beleuchtung eingeschaltet werden.

Stattdessen soll eine stark gedimmte Beleuchtung zur Orientierung verwendet werden.

```text
Nachtmodus aktiv
        +
Präsenz erkannt
        +
Raum dunkel
        │
        ▼
Nachtbeleuchtung gedimmt aktivieren
        │
        └── Hauptbeleuchtung bleibt aus
```

Die genaue:

- Helligkeit
- Lichtfarbe
- Einschaltdauer
- Zeitspanne

wird später im realen Betrieb festgelegt.

---

## Spiegelbeleuchtung

Die Spiegelbeleuchtung soll unabhängig von der normalen Badezimmerbeleuchtung steuerbar sein.

Sie kann beispielsweise für:

- Zähneputzen
- Rasieren
- Styling
- Pflege

genutzt werden.

Die Steuerung soll manuell über Schalter sowie optional über Home Assistant erfolgen.

---

## Baden / Wellness

Für die Badewanne kann später eine eigene Szene eingerichtet werden.

```text
Baden-Szene aktiviert
        │
        ├── Hauptbeleuchtung reduzieren
        ├── indirekte Beleuchtung aktivieren
        ├── Akzentbeleuchtung aktivieren
        └── gewünschte Lichtfarbe einstellen
```

Diese Szene soll bewusst manuell gestartet werden können.

---

## Sensorik und Raumklima

Im Hauptbad sollen folgende Werte und Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Temperatur | ✅ |
| Luftfeuchtigkeit | ✅ |
| Helligkeit | ✅ |
| Präsenz | ✅ |
| Bewegung | ✅ |
| Wasserleck | ✅ |
| Fensterstatus | falls Fenster vorhanden |

Wenn möglich, sollen mehrere Messwerte durch geeignete Kombisensoren abgedeckt werden.

---

## Luftfeuchtigkeit

Die Luftfeuchtigkeit ist im Badezimmer besonders wichtig.

Home Assistant soll erkennen können, wenn die Luftfeuchtigkeit durch Duschen oder Baden deutlich ansteigt.

```text
Luftfeuchtigkeit steigt deutlich
        │
        ▼
erhöhte Feuchtigkeit erkannt
        │
        ├── Status im Dashboard anzeigen
        ├── optional Lüftung steuern
        └── bei Bedarf Lüftungshinweis senden
```

Dabei soll später möglichst nicht nur ein fester Grenzwert verwendet werden.

Auch ein deutlicher Anstieg gegenüber der normalen Raumfeuchtigkeit kann berücksichtigt werden.

---

## Lüftung

Die vorhandene Lüftungssituation muss nach Bezug der Wohnung geprüft werden.

Mögliche Varianten:

- Fensterlüftung
- vorhandener elektrischer Lüfter
- später nachrüstbare Lüftung

Falls ein steuerbarer Lüfter vorhanden ist, kann dieser später abhängig von der Luftfeuchtigkeit automatisiert werden.

```text
Luftfeuchtigkeit erhöht
→ Lüfter aktivieren

Luftfeuchtigkeit wieder normal
→ Lüfter mit Nachlauf ausschalten
```

---

## Wasserschutz

Im Hauptbad sollen Wassersensoren geprüft werden.

Sinnvolle mögliche Positionen:

- unter / neben der Badewanne, sofern zugänglich
- im Bereich der Dusche
- unter dem Waschbecken
- in der Nähe von wasserführenden Anschlüssen

Mögliche Automation:

```text
Wasserleck erkannt
        │
        ▼
Home Assistant
        │
        ├── sofortige Benachrichtigung
        ├── Warnung auf Tablet
        ├── optional akustische Warnung
        └── später weitere Sicherheitsaktion
```

Langfristig kann eine zentrale automatische Wasserabsperrung geprüft werden.

---

## Fenster

Falls das Hauptbad über ein Fenster verfügt, soll ein Kontaktsensor vorgesehen werden.

Mögliche Nutzung:

- Fensterstatus
- Heizungssteuerung
- Lüftungslogik
- Gute-Nacht-Prüfung
- Abwesenheitsprüfung

Beispiel:

```text
Fenster geöffnet
→ später Heizung Hauptbad pausieren
```

---

## Heizung

Die konkrete Heizungssteuerung ist aktuell noch offen.

Zu klären:

- vorhandenes Heizsystem
- Fußbodenheizung / Heizkörper
- Art der Regelung
- Home-Assistant-Integration
- gewünschte Badtemperatur
- Nachtabsenkung
- Abwesenheitsabsenkung

Das Badezimmer kann später eine eigene Temperaturstrategie erhalten, da hier zeitweise eine höhere Raumtemperatur gewünscht sein kann.

---

## Manuelle Bedienung

Alle wichtigen Funktionen sollen weiterhin manuell steuerbar bleiben.

Mögliche Bedienwege:

- physische Schalter / Taster
- Home-Assistant-App
- Tablet-Dashboard
- Sprachsteuerung

Manuell steuerbar bleiben sollen:

- Hauptbeleuchtung
- Spiegelbeleuchtung
- Ambientebeleuchtung
- Szenen
- später Heizung

---

## Tablet und Sprachsteuerung

### Hauptbad-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Präsenz
- Lichtstatus
- Wasserleckstatus
- optional Fensterstatus
- später Heizungsstatus

Steuerung:

- Beleuchtung
- Szenen
- später Heizung

---

## Geplante Automationen

### Normale Beleuchtung

```text
Präsenz erkannt
+
Raumhelligkeit niedrig
+
kein Nachtmodus
→ Hauptbeleuchtung aktivieren
```

### Nachtbeleuchtung

```text
Nachtmodus aktiv
+
Präsenz erkannt
→ gedimmtes Orientierungslicht aktivieren
```

### Baden

```text
Baden-Szene aktiviert
→ Hauptlicht reduzieren
→ Ambientebeleuchtung aktivieren
```

### Hohe Luftfeuchtigkeit

```text
Luftfeuchtigkeit steigt deutlich
→ Lüftungsbedarf erkennen
→ optional Lüfter aktivieren
→ alternativ Lüftungshinweis senden
```

### Wasserleck

```text
Wasser erkannt
→ sofortige Benachrichtigung
→ Warnung auf Tablet
```

### Gute Nacht

```text
Gute Nacht
        │
        ├── Hauptbeleuchtung aus
        ├── Spiegelbeleuchtung aus
        ├── Nachtmodus aktivieren
        ├── Wasserstatus prüfen
        └── optional Fensterstatus prüfen
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Beleuchtung integrieren
- [ ] Temperatur erfassen
- [ ] Luftfeuchtigkeit erfassen
- [ ] Präsenz / Bewegung erfassen
- [ ] Helligkeit erfassen
- [ ] Wassersensor integrieren
- [ ] Fensterstatus erfassen, falls vorhanden

### Phase 2 – Komfort

- [ ] automatische Lichtsteuerung
- [ ] Nachtbeleuchtung
- [ ] Feuchtigkeitsautomation
- [ ] Baden-Szene
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] Lüftungsautomation
- [ ] automatische Wasserabsperrung prüfen
- [ ] erweiterte Feuchtigkeitslogik
- [ ] weitere Wassersensoren bei Bedarf

---

## Offene Punkte

- [ ] vorhandene Beleuchtung dokumentieren
- [ ] Fenster prüfen
- [ ] Lüftungssystem prüfen
- [ ] Heizsystem klären
- [ ] Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Wassersensor auswählen
- [ ] Position der Wassersensoren bestimmen
- [ ] Nachtbeleuchtung festlegen
- [ ] Feuchtigkeitslogik definieren
- [ ] Möglichkeit einer Lüftersteuerung prüfen
- [ ] Sprachsteuerung festlegen
- [ ] Bad-Automationen im realen Betrieb testen