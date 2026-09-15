# Smart Home – Einkaufsliste

Diese Datei enthält die zentrale Hardware- und Einkaufsliste für das
Smart-Home-Projekt.

Die Raumdateien enthalten die detaillierte Zuordnung der Hardware.
Diese Einkaufsliste fasst den tatsächlichen bzw. möglichen Kaufbedarf
zentral nach Hardware-Kategorien zusammen.

## Status

- 🟢 Ausgewählt / Kauf geplant
- 🟡 In Prüfung / Aufmaß erforderlich
- ⚪ Optional / später geplant
- 🔵 Bereits vorhanden / kein Kauf erforderlich

---

# 1. Zentrale & Bridges

| Komponente | Anzahl | Hersteller / Modell | Aufgabe | Status | Richtpreis |
|---|---:|---|---|---|---:|
| Smart-Home-Zentrale / Display | 1 | Amazon Echo Hub | Zentrale Bedienung, Alexa, Matter, Thread und Zigbee | 🟢 Ausgewählt | ca. 199,99 € |
| Lichtsteuerung | 1 | Philips Hue Bridge Pro | Zentrale Steuerung der Hue-Beleuchtung und des Hue-Zubehörs | 🟢 Ausgewählt | Preis vor Kauf prüfen / Starterset prüfen |
| Wandhalterung Echo Hub | 1 | Amazon Original | Wandmontage Echo Hub | 🔵 Lieferumfang | 0 € |
| Netzteil Echo Hub | 1 | Amazon Original | Stromversorgung Echo Hub | 🔵 Lieferumfang | 0 € |

## Hinweise

- Keine zusätzliche Zigbee-Bridge vorgesehen.
- Kein Aqara Hub für die aktuell geplanten Matter-over-Thread-Geräte vorgesehen.
- Kein zusätzlicher Thread Border Router vorgesehen.
- Kein Home-Assistant-Rechner vorgesehen.
- Hue Bridge Pro möglichst nicht vorschnell einzeln kaufen.
- Vor dem Kauf Hue Startersets und Bundles mit den noch benötigten
  Hue-Leuchten und Sensoren vergleichen.

---

# 2. Sensoren

| Komponente | Anzahl | Hersteller / Modell | Aufgabe | Status | Richtpreis |
|---|---:|---|---|---|---:|
| Präsenz-/Raumklimasensor | offen | Aqara FP300 | Präsenz, Bewegung, Temperatur und Luftfeuchtigkeit | 🟢 Ausgewählt – Anzahl nach Aufmaß | ca. 49,99 €/Stk. |
| Zonen-Präsenzsensor | offen | Aqara FP2 | Zonenerkennung im offenen Wohn-/Ess-/Koch-/Flurbereich | 🟡 Nach Aufmaß prüfen | ca. 82,99 €/Stk. |
| Fenster-/Türkontakt | offen | Aqara Door and Window Sensor P2 | Fenster-/Türstatus, Sicherheit und spätere Heizungsautomation | 🟢 Ausgewählt – Anzahl nach Aufmaß | ca. 32,99 €/Stk. |
| Bewegungs-/Helligkeitssensor Innen | offen | Philips Hue Motion Sensor | Bewegungs- und helligkeitsabhängige Lichtsteuerung | 🟡 Bedarf nach Aufmaß prüfen | Preis prüfen |
| Virtuelle Bewegungserkennung | – | Philips Hue MotionAware | Bewegungserkennung über geeignete Hue-Leuchten | 🟡 Einsatzbereiche prüfen | 0 € zusätzliche Sensorhardware |
| Outdoor Bewegungs-/Helligkeitssensor | 1 | Philips Hue Outdoor Sensor | Bewegung und Helligkeit auf dem Balkon | 🟢 Kauf geplant | Preis prüfen |
| Wassersensor | ca. 3 | Modell noch offen | Wasserschutz Küche, Hauptbad und Gästebad | 🟡 Modell auswählen | Preis offen |

## Sensorstrategie

### Aqara FP300

Vorgesehener Standard-Sensor für Räume.

Bereits grundsätzlich vorgesehen für:

- Schlafzimmer
- Kinderzimmer Lilly
- Kinderzimmer Luca
- Hauptbad
- Gästebad

Weitere Positionen werden nach dem Wohnungsaufmaß festgelegt.

### Aqara FP2

Nur einsetzen, wenn die Zonenerkennung im offenen
Wohn-/Ess-/Koch-/Flurbereich einen tatsächlichen Mehrwert bietet.

Position und Anzahl erst nach Aufmaß festlegen.

### Aqara P2

Geplant für relevante Fenster und Türen.

Mindestens vorgesehen:

- Balkontür
- relevante Fenster der Wohnräume
- Schlafzimmer
- Kinderzimmer
- Badezimmer, sofern Fenster vorhanden

Die endgültige Stückzahl wird beim Aufmaß ermittelt.

---

# 3. Beleuchtung

| Bereich | Komponente | Anzahl | Hersteller / Modell | Status | Richtpreis |
|---|---|---:|---|---|---:|
| Wohnzimmer | zusätzlicher Color Wandspot | 1 | Philips Hue White & Color Ambiance | 🟢 Kauf geplant | Preis prüfen |
| Küche | GU10 Leuchtmittel | offen | Philips Hue White & Color Ambiance GU10 | 🟢 Kauf geplant – Anzahl nach Aufmaß | Preis prüfen |
| Küche | Wandleuchte | 2 | Modell noch offen | 🟡 Leuchte auswählen | Preis offen |
| Küche | Leuchtmittel für Wandleuchten | 2 | Philips Hue White & Color Ambiance E14/E27 | 🟡 Fassung prüfen | Preis prüfen |
| Schlafzimmer | Haupt-/Deckenbeleuchtung | 1 | Modell noch offen | 🟡 Auswahl nach Einrichtung | Preis offen |
| Schlafzimmer | Nacht-/Orientierungslicht | 1 | Modell noch offen | 🟡 Lösung auswählen | Preis offen |
| Schlafzimmer | zusätzliche Akzentleuchten | 1–2 | Modell noch offen | ⚪ Optional | Preis offen |
| Kinderzimmer Lilly | Haupt-/Deckenbeleuchtung | 1 | Philips Hue White & Color Ambiance / Modell offen | 🟢 Kauf geplant | Preis offen |
| Kinderzimmer Lilly | Schreibtischleuchte | 1 | Modell noch offen | 🟢 Kauf geplant | Preis offen |
| Kinderzimmer Lilly | indirekte Beleuchtung Kuschelecke | 1 | Philips Hue / Lösung offen | 🟢 Kauf geplant | Preis offen |
| Kinderzimmer Luca | Haupt-/Deckenbeleuchtung | 1 | Philips Hue White & Color Ambiance / Modell offen | 🟢 Kauf geplant | Preis offen |
| Kinderzimmer Luca | Wickeltischbeleuchtung | 1 | Philips Hue / Lösung offen | 🟢 Kauf geplant | Preis offen |
| Kinderzimmer Luca | Nacht-/Orientierungslicht | 1 | Philips Hue / Lösung offen | 🟢 Kauf geplant | Preis offen |
| Flur | GU10 Leuchtmittel | offen | Philips Hue White & Color Ambiance GU10 | 🟢 Kauf geplant – Anzahl nach Aufmaß | Preis prüfen |
| Flur | Wandleuchten | 2 | Modell noch offen | 🟡 Anschluss und Auswahl prüfen | Preis offen |
| Flur | Leuchtmittel Wandleuchten | 2 | Philips Hue White & Color Ambiance E14/E27 | 🟡 Fassung prüfen | Preis prüfen |
| Hauptbad | GU10 Leuchtmittel | offen | Philips Hue White & Color Ambiance GU10 | 🟢 Kauf geplant – Anzahl nach Aufmaß | Preis prüfen |
| Hauptbad | Spiegelleuchte | 1 | Philips Hue / Modell offen | 🟢 Kauf geplant | Preis prüfen |
| Hauptbad | Ambientebeleuchtung Badewanne | 1 | Philips Hue / Lösung offen | 🟢 Kauf geplant | Preis offen |
| Gästebad | GU10 Leuchtmittel | offen | Philips Hue White & Color Ambiance GU10 | 🟢 Kauf geplant – Anzahl nach Aufmaß | Preis prüfen |
| Gästebad | Spiegelleuchte | 1 | Philips Hue / Modell offen | 🟢 Kauf geplant | Preis prüfen |
| Balkon | Outdoor Lightstrip | 1 | Philips Hue Outdoor Lightstrip | 🟢 Kauf geplant – Länge nach Aufmaß | Preis prüfen |
| Balkon | Color Leuchtmittel Wandleuchten | 2 | Philips Hue White & Color Ambiance E14/E27 | 🟡 Fassung prüfen | Preis prüfen |

## Bereits vorhandene Beleuchtung

Die vorhandene Hue-Beleuchtung wird nicht als Kaufbedarf gerechnet.

Dazu gehören unter anderem:

- Hue Play Lightbars
- vorhandene Hue Lightstrips
- vorhandene Hue Color Spots
- Schlafzimmer-Nachttischlampen
- vorhandene weitere Hue-Leuchten

Die genaue Bestandszuordnung befindet sich in den jeweiligen Raumdateien.

---

# 4. Schalter & Bedienung

## Bestand

| Komponente | Anzahl | Hersteller / Modell | Status |
|---|---:|---|---|
| Hue Dimmer Switch | vorhanden | Philips Hue | 🔵 Bereits vorhanden |

## Weiterer Bedarf

Der tatsächliche zusätzliche Schalterbedarf wird erst festgelegt,
wenn die vorhandenen Hue-Schalter den Räumen endgültig zugeordnet wurden.

Geplante Bedienstellen bestehen unter anderem für:

- Küche
- Schlafzimmer
- Kinderzimmer Lilly
- Kinderzimmer Luca
- Flur
- Hauptbad
- Gästebad
- Balkon

Dabei gilt:

- vorhandene Hue Dimmer zuerst verwenden
- zusätzliche Hue Dimmer nur bei tatsächlichem Bedarf kaufen
- Hue Tap Dial optional für Bereiche mit erweitertem Szenenbedarf
- manuelle Bedienung muss grundsätzlich erhalten bleiben

Aktuell kein zusätzlicher Hue-Schalter als fester Kaufbedarf eingetragen.

---

# 5. Heizung

🟡 Planung vorbereitet – Aufmaß erforderlich.

Die vorhandene Fußbodenheizungssteuerung wird zunächst geprüft.

Zu erfassen:

- vorhandene Raumthermostate
- Hersteller und Modell
- Verkabelung
- Heizkreise
- Stellantriebe
- vorhandene Smart-Home-Fähigkeit

## Kaufbedarf

Aktuell kein Kaufbedarf festgelegt.

Smart-Home-Hardware für die Heizung wird erst ausgewählt,
wenn die vorhandene Installation bekannt ist.

Siehe:

`docs/hardware/heating.md`

---

# 6. Rollläden

🟡 Planung vorbereitet – Aufmaß erforderlich.

Zunächst wird geprüft:

- Anzahl der Rollläden
- elektrisch oder manuell
- vorhandene Schalter
- Hersteller / Steuerung
- Verkabelung
- vorhandene Smart-Home-Funktion

## Kaufbedarf

Aktuell kein Kaufbedarf festgelegt.

Rollladenaktoren oder andere Steuerungshardware werden erst
nach Prüfung der vorhandenen Installation ausgewählt.

Siehe:

`docs/hardware/shutters.md`

---

# 7. Sicherheit & Wasserschutz

## Fenster und Türen

Für Fenster und Türen werden bevorzugt die bereits unter
"Sensoren" aufgeführten Aqara Door and Window Sensor P2 verwendet.

Die Geräte werden hier nicht erneut als Kaufposition gezählt.

Geplante Funktionen:

- Fensterstatus
- Balkontürstatus
- Abwesenheitswarnungen
- spätere Heizungsautomation
- Alexa-/Echo-Hub-Statusanzeige

## Wasserschutz

Geplante Einsatzbereiche:

- Küche – Spüle / Geschirrspüler
- Hauptbad
- Gästebad

| Komponente | Anzahl | Hersteller / Modell | Status | Richtpreis |
|---|---:|---|---|---:|
| Wassersensor | ca. 3 | Modell noch auswählen | 🟡 In Prüfung | Preis offen |

## Weitere Sicherheitstechnik

Aktuell keine vollständige Alarmanlage vorgesehen.

Später optional:

- Kameras
- Sirene
- weitere Außensensoren
- Video-Türklingel
- zusätzliche Anwesenheitssimulation

Siehe:

`docs/hardware/security.md`

---

# 8. Netzwerk & Stromversorgung

## Aktueller Kaufbedarf

Aktuell kein zusätzlicher Netzwerk-Kaufbedarf festgelegt.

Beim Wohnungsaufmaß werden geprüft:

- Routerposition
- LAN-Anschlüsse
- WLAN-Abdeckung
- WLAN-Abdeckung Balkon
- Position Echo Hub
- Position Hue Bridge Pro
- Steckdosen
- mögliche PoE-Versorgung des Echo Hub
- Bedarf für Mesh oder Access Points

| Komponente | Anzahl | Status | Bemerkung |
|---|---:|---|---|
| zusätzlicher Thread Border Router | 0 | Nicht benötigt | Echo Hub übernimmt diese Funktion |
| zusätzlicher Zigbee Hub | 0 | Nicht benötigt | Echo Hub / Hue Bridge Pro vorhanden |
| Aqara Hub | 0 | Aktuell nicht benötigt | geplante P2-Geräte über Matter/Thread |
| Mesh / Access Point | offen | 🟡 Nach Aufmaß prüfen | nur bei unzureichender WLAN-Abdeckung |
| PoE für Echo Hub | offen | ⚪ Optional | nur falls Verkabelung sinnvoll vorhanden |

Siehe:

`docs/hardware/network.md`

---

# 9. Kostenübersicht

Die endgültige Kostenberechnung erfolgt nach dem Wohnungsaufmaß.

Noch offene Hauptfaktoren:

- Anzahl GU10-Leuchtmittel
- Anzahl Aqara FP300
- Anzahl Aqara P2 Fenster-/Türkontakte
- Einsatz und Anzahl FP2
- Anzahl zusätzlicher Hue Motion Sensoren
- Länge Hue Outdoor Lightstrip
- Fassungen der vorhandenen Wandleuchten
- Auswahl der neuen Leuchten
- tatsächlicher zusätzlicher Schalterbedarf
- Wassersensor-Modell
- eventuelle Heizungssteuerung
- eventuelle Rollladensteuerung
- eventueller Netzwerkbedarf

| Bereich | Aktueller Stand |
|---|---:|
| Zentrale & Bridges | teilweise berechenbar |
| Sensoren | Stückzahlen teilweise offen |
| Beleuchtung | Stückzahlen / Modelle teilweise offen |
| Schalter & Bedienung | Bestand zuerst prüfen |
| Heizung | 0 € fest eingeplant |
| Rollläden | 0 € fest eingeplant |
| Sicherheit & Wasserschutz | Modell / Stückzahl teilweise offen |
| Netzwerk & Stromversorgung | 0 € fest eingeplant |
| **Gesamt** | **nach Aufmaß berechnen** |

---

# 10. Offene Punkte beim Wohnungsaufmaß

- [ ] Anzahl GU10 Küche zählen
- [ ] Anzahl GU10 Flur zählen
- [ ] Anzahl GU10 Hauptbad zählen
- [ ] Anzahl GU10 Gästebad zählen
- [ ] Fassungen der Küchen-Wandleuchten prüfen
- [ ] Fassungen der Flur-Wandleuchten prüfen
- [ ] Fassungen der Balkon-Wandleuchten prüfen
- [ ] alle Fenster und Türen zählen
- [ ] FP300-Positionen festlegen
- [ ] FP2 im offenen Wohnbereich prüfen
- [ ] Hue Motion / MotionAware Bedarf prüfen
- [ ] Länge Outdoor Lightstrip bestimmen
- [ ] vorhandene Hue Dimmer Switches zählen
- [ ] Heizungssteuerung fotografieren und erfassen
- [ ] Rollladensteuerung fotografieren und erfassen
- [ ] Router-/LAN-/WLAN-Situation erfassen
- [ ] Echo-Hub-Position festlegen
- [ ] Hue-Bridge-Pro-Position festlegen
- [ ] Steckdosen an relevanten Positionen prüfen

---

# Kaufstrategie

Vor dem endgültigen Einkauf werden alle Mengen nach dem Wohnungsaufmaß
in dieser Datei ergänzt.

Anschließend:

1. exakte Stückzahlen bestimmen
2. vorhandene Hardware abziehen
3. Hue Startersets und Bundles vergleichen
4. Einzelpreise aktualisieren
5. Gesamtkosten berechnen
6. Einkauf in sinnvolle Prioritäten aufteilen

Es soll keine Hardware auf Verdacht gekauft werden.