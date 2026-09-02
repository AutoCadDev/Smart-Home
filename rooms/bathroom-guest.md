# Gästebad – Smart-Home-Planung

## Ziel

Das Gästebad soll mit einer einfachen und zuverlässigen Smart-Home-Automation in Home Assistant integriert werden.

Vorhanden sind:

- WC
- Dusche

Schwerpunkte:

- automatische Beleuchtung
- Nachtbeleuchtung
- Präsenz- / Bewegungserkennung
- Temperatur und Luftfeuchtigkeit
- Feuchtigkeitsüberwachung beim Duschen
- Wasserschutz
- spätere Heizungssteuerung

> **Grundsatz:** Im Gästebad steht eine einfache und zuverlässige Automation vor möglichst vielen Funktionen.

---

## Beleuchtung

### Vorhandene / geplante Lichtbereiche

| Licht | Typ / Verwendung |
|---|---|
| Deckenbeleuchtung | Hauptbeleuchtung |
| Spiegelbeleuchtung | Funktionsbeleuchtung |
| Nachtlicht | optional / gedimmte Beleuchtung |

Die genaue vorhandene Beleuchtung wird nach Bezug der Wohnung dokumentiert.

---

## Automatische Beleuchtung

Im Gästebad soll die Beleuchtung weitgehend automatisch funktionieren.

```text
Person betritt Gästebad
        +
Raumhelligkeit niedrig
        │
        ▼
Beleuchtung einschalten
```

Nach Verlassen des Raumes:

```text
keine Präsenz mehr
        │
        ▼
definierte Nachlaufzeit
        │
        ▼
Beleuchtung ausschalten
```

Die genaue Nachlaufzeit wird später im realen Betrieb bestimmt.

---

## Nachtmodus

Nachts soll das Gästebad nur schwach beleuchtet werden.

```text
Nachtmodus aktiv
        +
Präsenz / Bewegung erkannt
        │
        ▼
gedimmte Beleuchtung aktivieren
        │
        └── volle Hauptbeleuchtung bleibt aus
```

Damit kann das WC nachts genutzt werden, ohne dass eine helle Beleuchtung eingeschaltet wird.

---

## Manuelle Bedienung

Trotz automatischer Lichtsteuerung soll die Beleuchtung jederzeit manuell bedienbar bleiben.

Mögliche Bedienwege:

- physischer Schalter / Taster
- Home-Assistant-App
- Tablet
- Sprachsteuerung

Eine manuelle Änderung soll nicht unmittelbar von einer Automation überschrieben werden.

---

## Sensorik und Raumklima

Im Gästebad sollen folgende Werte und Zustände erfasst werden:

| Sensorik | Geplant |
|---|:---:|
| Temperatur | ✅ |
| Luftfeuchtigkeit | ✅ |
| Helligkeit | ✅ |
| Präsenz / Bewegung | ✅ |
| Wasserleck | ✅ |
| Fensterstatus | falls vorhanden |

---

## Luftfeuchtigkeit

Durch die Dusche soll die Luftfeuchtigkeit überwacht werden.

```text
Luftfeuchtigkeit steigt deutlich
        │
        ▼
Duschvorgang / hohe Feuchtigkeit erkannt
        │
        ├── optional Lüfter aktivieren
        └── alternativ Lüftungshinweis
```

Nach dem Duschen soll geprüft werden, wann sich die Luftfeuchtigkeit wieder normalisiert hat.

---

## Lüftung

Die vorhandene Lüftungssituation wird nach Bezug der Wohnung geprüft.

Falls ein steuerbarer Lüfter vorhanden ist:

```text
Luftfeuchtigkeit erhöht
→ Lüfter aktivieren

Luftfeuchtigkeit wieder normal
→ Lüfter nach Nachlauf ausschalten
```

---

## Wasserschutz

Ein Wassersensor soll insbesondere im Bereich von:

- Dusche
- Waschbecken
- wasserführenden Anschlüssen

geprüft werden.

```text
Wasserleck erkannt
→ sofortige Benachrichtigung
→ Warnung auf Tablet
```

---

## Heizung

Die konkrete Heizungssteuerung ist aktuell noch offen.

Zu klären:

- vorhandenes Heizsystem
- Home-Assistant-Integration
- gewünschte Temperatur
- Abwesenheitsabsenkung
- Nachtabsenkung

---

## Tablet und Sprachsteuerung

### Gästebad-Dashboard

Anzeigen:

- Temperatur
- Luftfeuchtigkeit
- Lichtstatus
- Präsenzstatus
- Wasserleckstatus
- optional Fensterstatus
- später Heizungsstatus

Steuerung:

- Licht
- später Heizung

Das Gästebad benötigt keinen umfangreichen eigenen Dashboard-Bereich.

Die wichtigsten Informationen können in das zentrale Wohnungs-Dashboard integriert werden.

---

## Geplante Automationen

### Licht

```text
Präsenz erkannt
+
Helligkeit niedrig
+
kein Nachtmodus
→ Beleuchtung einschalten
```

### Licht ausschalten

```text
keine Präsenz
+
Nachlaufzeit abgelaufen
→ Beleuchtung ausschalten
```

### Nachtlicht

```text
Nachtmodus aktiv
+
Präsenz erkannt
→ gedimmte Beleuchtung aktivieren
```

### Duschen / Luftfeuchtigkeit

```text
Luftfeuchtigkeit steigt deutlich
→ Lüftungsbedarf erkennen
→ optional Lüfter aktivieren
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
→ Beleuchtung aus
→ Nachtmodus aktivieren
→ Wasserstatus prüfen
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Beleuchtung integrieren
- [ ] Bewegung / Präsenz erfassen
- [ ] Helligkeit erfassen
- [ ] Temperatur erfassen
- [ ] Luftfeuchtigkeit erfassen
- [ ] Wassersensor integrieren

### Phase 2 – Komfort

- [ ] automatische Lichtsteuerung
- [ ] Nachtmodus
- [ ] Feuchtigkeitsautomation
- [ ] Tablet-Integration
- [ ] Sprachsteuerung

### Phase 3 – Erweiterung

- [ ] Heizungsautomation
- [ ] Lüftungsautomation
- [ ] automatische Wasserabsperrung prüfen
- [ ] erweiterte Sicherheitsfunktionen

---

## Offene Punkte

- [ ] vorhandene Beleuchtung dokumentieren
- [ ] Fenster prüfen
- [ ] Lüftungssystem prüfen
- [ ] Heizsystem klären
- [ ] Bewegungs-/Präsenzsensor auswählen
- [ ] Temperatur-/Luftfeuchtigkeitssensor auswählen
- [ ] Wassersensor auswählen
- [ ] Position des Wassersensors bestimmen
- [ ] Nachtbeleuchtung festlegen
- [ ] Nachlaufzeit bestimmen
- [ ] Feuchtigkeitslogik definieren
- [ ] Sprachsteuerung festlegen
- [ ] Gästebad-Automationen im realen Betrieb testen