# Balkon – Hardwareplanung

## Planungsstatus

📐 Exakte Positionen und Abmessungen werden nach dem Wohnungsaufmaß
und der späteren Möblierung festgelegt.

---

## Beleuchtung

Ziel ist eine sehr gemütliche und indirekte Balkonbeleuchtung.

Die Beleuchtung wird in zwei Ebenen aufgebaut:

### 1. Grundbeleuchtung

| Bereich | Beleuchtung | Anzahl | Status |
|---|---|---:|---|
| Wand | vorhandene Wandleuchten | 2 | 🔵 Vorhanden |
| Wand | Hue White & Color Ambiance Leuchtmittel | 2 | 🟡 Fassung prüfen |

Die vorhandenen Wandleuchten dienen als Grundbeleuchtung.

Wenn technisch möglich, werden passende Hue White & Color Ambiance
Leuchtmittel eingesetzt.

### 2. Ambientebeleuchtung

| Bereich | Beleuchtung | Anzahl | Status |
|---|---|---:|---|
| indirekte Balkonbeleuchtung | Philips Hue Outdoor Lightstrip | 1 | 🟢 Geplant |
| zusätzliche Akzentbeleuchtung | Hue Outdoor | 0–2 | ⚪ Nach Möblierung prüfen |

Der Outdoor Lightstrip soll möglichst indirekt montiert werden,
sodass die Lichtquelle selbst nicht unmittelbar sichtbar ist.

Mögliche Positionen:

- hinter oder unter einer Sitzbank
- entlang einer Wand
- hinter Pflanzgefäßen
- entlang eines geeigneten Möbelstücks

Die benötigte Länge wird nach dem Wohnungsaufmaß festgelegt.

### Geplante Szenen

- 🌅 Abenddämmerung – warmes Orange / Amber
- 🕯️ Gemütlich – sehr warm und stark gedimmt
- 🌙 Später Abend – nur indirekte Beleuchtung
- 🎨 Sommerabend – dezente Farbakzente
- 💡 Hell – Wandleuchten als funktionale Grundbeleuchtung
---

## Sensorik

| Gerät | Anzahl | Funktion | Status |
|---|---:|---|---|
| Aqara Door and Window Sensor P2 | 1 | Status Balkontür | 🟢 Geplant |
| Philips Hue Outdoor Sensor | 1 | Bewegung + Umgebungshelligkeit | 🟢 Geplant |
| Aqara FP300 | 0 | Präsenz-/Raumklima | ⚪ Für Außenbereich nicht vorgesehen |

### Balkontür

An der Balkontür ist ein Aqara Door and Window Sensor P2 vorgesehen.

Mögliche Funktionen:

- Balkontür offen / geschlossen erkennen
- Status am Echo Hub anzeigen
- spätere Heizungsautomation
- Einbindung in Sicherheitsfunktionen
- Nutzung in Alexa-Routinen

### Bewegung und Helligkeit

Für den Balkon ist ein Philips Hue Outdoor Sensor vorgesehen.

Aufgaben:

- Bewegung auf dem Balkon erkennen
- Umgebungshelligkeit erfassen
- Balkonbeleuchtung nur bei Dunkelheit automatisch einschalten
- unterschiedliche Beleuchtung abhängig von Tageszeit
- Steuerung über Hue Bridge Pro

Die endgültige Position wird nach dem Wohnungsaufmaß festgelegt.

### Geplante Lichtautomation

Beispiel:

**Tagsüber**
Bewegung → kein Licht

**Abends**
Bewegung + dunkel → gemütliche Balkonbeleuchtung

**Nachts**
Bewegung → stark gedimmtes, warmes Licht

**Keine Bewegung**
→ Beleuchtung nach definierter Zeit wieder ausschalten

Manuelle Bedienung bleibt jederzeit möglich.ntür

---

## Bedienung

Die Balkonbeleuchtung soll überwiegend automatisch über den
Hue Outdoor Sensor gesteuert werden.

Eine manuelle Bedienung bleibt jederzeit möglich.

| Position | Funktion | Lösung | Status |
|---|---|---|---|
| Innen bei Balkontür | Licht Ein/Aus, Dimmen, Szenen | Philips Hue Dimmer Switch | 🟢 Geplant |
| Balkon | automatische Lichtsteuerung | Philips Hue Outdoor Sensor | 🟢 Geplant |
| Wohnung | Sprachsteuerung | Alexa | 🟢 Über vorhandene Echo-Geräte |
| Zentral | Smart-Home-Bedienung | Amazon Echo Hub | 🟢 Geplant |

### Hue Dimmer Switch

Der Hue Dimmer Switch wird innen in der Nähe der Balkontür
positioniert.

Geplante Funktionen:

- Balkonbeleuchtung ein-/ausschalten
- Helligkeit ändern
- Balkon-Szenen auswählen
- Automatik bei Bedarf manuell übersteuern

Ein Schalter im Außenbereich ist aktuell nicht vorgesehen.

### Geplante Bedienung

Normalbetrieb:
Hue Outdoor Sensor übernimmt die automatische Beleuchtung.

Manuell:
Hue Dimmer Switch an der Balkontür.

Sprache:
Alexa kann die Balkonbeleuchtung und Szenen zusätzlich steuern.

Zentral:
Steuerung und Status über den Echo Hub.


---

## Steckdosen / Aktoren

Aktuell sind keine smarten Steckdosen oder zusätzlichen Aktoren
für den Balkon vorgesehen.

---

## Sonstige Hardware

Aktuell ist keine zusätzliche Smart-Home-Hardware fest vorgesehen.

### Später prüfen

- wetterfeste Bewegungs-/Helligkeitserkennung
- automatische Aktivierung der Balkonbeleuchtung bei Dunkelheit
- Einbindung der Balkontür über einen Fenster-/Türkontakt