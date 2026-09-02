# Balkon – Smart-Home-Planung

## Ziel

Der Balkon soll als gemütlicher Outdoor-Bereich sinnvoll in Home Assistant integriert werden.

Der Schwerpunkt liegt auf:

- stimmungsvoller Außenbeleuchtung
- helligkeitsabhängigen Automationen
- wetterabhängigen Funktionen
- Balkontürüberwachung
- optionaler Temperatur- und Wettermessung
- späterer Beschattungssteuerung
- Bedienung per App, Sprache und Tablet

> **Grundsatz:** Automationen sollen Komfort schaffen, aber die manuelle Bedienung niemals verhindern.

---

## Beleuchtung

### Vorhandene / geplante Lichtquellen

| Licht | Typ / Verwendung |
|---|---|
| Lichterkette | Ambientebeleuchtung |
| Außenleuchte | Grundbeleuchtung |
| indirekte Beleuchtung | Lounge- / Stimmungsbeleuchtung |
| Grillbereich-Beleuchtung | Arbeitsbeleuchtung |
| Pflanzenbeleuchtung | optional |

Alle eingesetzten Komponenten müssen für den Außenbereich geeignet sein.

Besonders zu beachten:

- geeignete IP-Schutzklasse
- wettergeschützte Steckverbindungen
- sichere Kabelführung
- möglichst lokale Smart-Home-Integration

---

## Lichtautomation

### Ziel

Die Balkonbeleuchtung soll sich abhängig von:

- Tageszeit
- Außenhelligkeit
- Anwesenheit
- gewählter Szene

steuern lassen.

Mögliche Grundlogik:

```text
Bewohner zuhause
        +
Abendzeit
        +
Außenhelligkeit unter Grenzwert
        │
        ▼
Balkon-Ambientebeleuchtung aktivieren
```

Die Beleuchtung soll nicht zwangsläufig automatisch eingeschaltet werden, sondern abhängig von der später festgelegten Nutzung.

---

## Balkon-Abend

Für entspannte Abende soll eine eigene Szene eingerichtet werden.

```text
Balkonabend aktiviert
        │
        ├── Lichterkette einschalten
        ├── indirekte Beleuchtung einschalten
        ├── Außenleuchte gedimmt
        └── Grillbeleuchtung aus
```

Die Szene soll per:

- Sprache
- Home-Assistant-App
- Tablet
- physischem Taster

aktivierbar sein.

---

## Grillen

Für den Grillbereich soll eine eigene Beleuchtungslogik vorgesehen werden.

```text
Grill-Szene aktiviert
        │
        ├── Grillbereich hell beleuchten
        ├── Ambientebeleuchtung aktivieren
        └── übrige Außenbeleuchtung passend dimmen
```

Der Grill bzw. Pizzaofen selbst soll nicht automatisch eingeschaltet werden.

Home Assistant kann später optional zur:

- Statusanzeige
- Leistungsüberwachung
- Laufzeitüberwachung

genutzt werden.

Eine automatische Stromschaltung darf nur erfolgen, wenn verwendete Geräte, Steckdose und Smart-Plug für die entsprechende Leistung ausdrücklich geeignet sind.

---

## Manuelle Bedienung

Die Balkonbeleuchtung soll jederzeit manuell steuerbar bleiben.

Mögliche Bedienwege:

- Home-Assistant-App
- Tablet-Dashboard
- Sprachsteuerung
- physische Schalter / Taster

Manuell steuerbar bleiben sollen:

- Lichterkette
- Außenleuchte
- indirekte Beleuchtung
- Grillbeleuchtung
- Helligkeit
- Szenen

Eine manuell aktivierte Balkonszene soll nicht unmittelbar von einer Automation überschrieben werden.

Die genaue Override-Logik wird später festgelegt.

---

## Sensorik

Für den Balkon sollen folgende Werte und Zustände berücksichtigt werden:

| Sensorik | Geplant |
|---|:---:|
| Außenhelligkeit | ✅ |
| Außentemperatur | optional |
| Balkontürstatus | ✅ |
| Regen | später optional |
| Wind | später optional |
| Bewegung | optional |

Die Sensorik soll möglichst nur dort eingesetzt werden, wo sie einen echten Mehrwert bietet.

---

## Balkontür

Der Status der Balkontür soll in Home Assistant verfügbar sein.

Mögliche Nutzung:

- Sicherheitsprüfung
- Gute-Nacht-Prüfung
- Heizungssteuerung
- Abwesenheitsprüfung
- Anzeige im Dashboard

Beispiel:

```text
Balkontür geöffnet
        │
        ▼
Heizung Wohnzimmer pausieren
```

Zusätzlich kann bei Abwesenheit eine Warnung ausgelöst werden.

```text
Niemand zuhause
+
Balkontür geöffnet
→ Benachrichtigung senden
```

---

## Wetter

Langfristig kann der Balkon mit Wetterdaten erweitert werden.

Mögliche Werte:

- Außentemperatur
- Regen
- Wind
- Helligkeit
- Sonneneinstrahlung

Diese Werte können später beispielsweise für Beschattung oder Hinweise genutzt werden.

Beispiel:

```text
starke Sonneneinstrahlung
+
Außentemperatur hoch
        │
        ▼
Beschattung aktivieren
```

---

## Beschattung

Falls später eine Markise oder elektrische Beschattung installiert wird, soll diese in Home Assistant integriert werden.

Mögliche Automationen:

- Beschattung bei starker Sonneneinstrahlung
- Beschattung abhängig von Außentemperatur
- automatisches Einfahren bei starkem Wind
- automatisches Einfahren bei Regen
- manuelle Steuerung per App oder Sprache

Bei wetterabhängigen Automationen muss die Sicherheit Vorrang haben.

---

## Tablet und Sprachsteuerung

Der Balkon soll über das zentrale Smart-Home-Tablet erreichbar sein.

### Balkon-Dashboard

Anzeigen:

- Balkontürstatus
- Lichtstatus
- aktive Szene
- Außenhelligkeit
- optional Außentemperatur
- später Wetterstatus
- später Beschattungsstatus

Steuerung:

- Balkonbeleuchtung
- Lichterkette
- Grillbeleuchtung
- Balkonszenen
- später Beschattung

Zusätzlich sollen zentrale Funktionen per Sprache steuerbar sein.

---

## Geplante Automationen

### Balkonabend

```text
Balkonabend aktiviert
→ Lichterkette an
→ indirekte Beleuchtung an
→ Außenleuchte gedimmt
```

---

### Grillen

```text
Grill-Szene aktiviert
→ Grillbeleuchtung hell
→ Ambientebeleuchtung aktiv
```

---

### Abendbeleuchtung

```text
Bewohner zuhause
+
Abendzeit
+
Außenhelligkeit unter Grenzwert
+
Balkon-Szene aktiviert
→ Ambientebeleuchtung einschalten
```

---

### Gute Nacht

```text
Gute Nacht
        │
        ├── Balkonbeleuchtung aus
        ├── Lichterkette aus
        ├── Balkontürstatus prüfen
        └── später Beschattung schließen
```

---

### Abwesenheit

```text
Niemand zuhause
        │
        ├── Balkonbeleuchtung aus
        ├── Balkontürstatus prüfen
        └── bei offener Balkontür warnen
```

---

### Wetterwarnung

Spätere Erweiterung:

```text
starker Wind oder Regen erkannt
        │
        ▼
Beschattung einfahren
        │
        └── Benachrichtigung senden
```

---

## Prioritäten

### Phase 1 – Grundfunktionen

- [ ] Balkontürstatus erfassen
- [ ] Lichterkette integrieren
- [ ] Außenbeleuchtung integrieren
- [ ] Balkon-Szene erstellen
- [ ] manuelle Steuerung einrichten

### Phase 2 – Komfort

- [ ] Außenhelligkeit erfassen
- [ ] Balkonabend-Szene
- [ ] Grill-Szene
- [ ] helligkeitsabhängige Beleuchtung
- [ ] Tablet-Steuerung
- [ ] Sprachsteuerung
- [ ] Gute-Nacht-Integration

### Phase 3 – Erweiterung

- [ ] Außentemperatur erfassen
- [ ] Regensensor prüfen
- [ ] Windsensor prüfen
- [ ] elektrische Beschattung integrieren
- [ ] wetterabhängige Automationen
- [ ] Energieüberwachung für Grillbereich prüfen

---

## Offene Punkte

- [ ] genaue Balkonbeleuchtung festlegen
- [ ] wetterfeste Lichterkette auswählen
- [ ] Außenleuchte auswählen
- [ ] geeignete Smart-Home-Anbindung festlegen
- [ ] Balkontürsensor auswählen
- [ ] Helligkeitssensor auswählen
- [ ] IP-Schutzklassen prüfen
- [ ] Steckdosen und Stromversorgung prüfen
- [ ] Grillbereich-Beleuchtung planen
- [ ] Sprachsteuerung festlegen
- [ ] Beschattungslösung festlegen
- [ ] Außenhelligkeits-Grenzwert bestimmen
- [ ] Balkonbeleuchtung im realen Betrieb testen