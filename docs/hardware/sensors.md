# Sensorplanung

Planung und Auswahl der Sensorik für das Echo-Hub-Smart-Home.

> Die endgültigen Stückzahlen und Positionen werden nach dem Aufmaß der Wohnung festgelegt.

---

## Aktueller Planungsstand

- 🟢 Aqara FP300 als Standard-Präsenzsensor vorgesehen
- 🟢 Aqara Door and Window Sensor P2 als Standard-Fensterkontakt vorgesehen
- 🟡 Aqara FP2 für offenen Wohn-/Ess-/Kochbereich prüfen
- 🟡 Philips Hue Motion Sensor für bewegungs- und helligkeitsabhängige Lichtsteuerung prüfen
- 🟡 Hue MotionAware zur Reduzierung zusätzlicher Bewegungsmelder prüfen
- ⚪ Hue Secure Contact Sensor nur als mögliche Bundle-Alternative
- 📐 Stückzahlen und Sensorpositionen erst nach Wohnungsaufmaß

---

## Präsenzsensoren

### Aqara Presence Multi-Sensor FP300

**Status:** 🟢 Grundsätzlich ausgewählt

Geplanter Einsatz als Standardsensor für Räume, in denen eine zuverlässige
Präsenzerkennung benötigt wird.

Funktionen:

- mmWave-Präsenzerkennung
- PIR-Bewegungserkennung
- Helligkeitssensor vorhanden
- Helligkeitswert bei direkter Alexa-/Matter-Einbindung derzeit nicht nutzbar
- Temperatur
- Luftfeuchtigkeit
- Matter over Thread
- batteriebetrieben
- direkte Einbindung über Echo Hub vorgesehen
- keine zusätzliche Aqara Bridge vorgesehen

**Stückzahl:** Noch offen – Festlegung nach Wohnungsaufmaß.

### Einschränkung Alexa

Der integrierte Helligkeitssensor des FP300 wird bei direkter
Matter-over-Thread-Einbindung derzeit nicht von Alexa unterstützt.

Präsenz, Temperatur und Luftfeuchtigkeit können weiterhin genutzt werden.

Für helligkeitsabhängige Lichtautomationen wird eine separate Lösung geprüft.

---

### Aqara Presence Sensor FP2

**Status:** 🟢 Grundsätzlich ausgewählt

Der FP2 soll insbesondere für größere oder offene Bereiche geprüft werden,
bei denen eine Aufteilung in unterschiedliche Erkennungszonen sinnvoll ist.

Möglicher Einsatz:

- Wohnbereich
- Essbereich
- Küche
- Übergang zum Flur

Der Wohn-, Ess- und Kochbereich ist offen und mit dem Flur verbunden.
Die endgültige Sensoranzahl und Positionierung kann deshalb erst nach
dem Aufmaß der Wohnung festgelegt werden.

**Stückzahl:** Noch offen.

Für reine Lichtautomationen wird bevorzugt geprüft,
ob Philips Hue Motion Sensor oder Hue MotionAware verwendet werden können.

Dadurch kann die Helligkeitslogik direkt innerhalb des Hue-Systems
ausgeführt werden, ohne auf die Alexa-Unterstützung von Lux-Werten
angewiesen zu sein.

### Alternative: Philips Hue Secure Contact Sensor

**Status:** ⚪ Alternative bei wirtschaftlich interessantem Hue-Bundle

Der Hue Secure Contact Sensor wird nicht als Standard-Fensterkontakt
bevorzugt.

Grund:
Fenster- und Türzustände sollen möglichst direkt über Matter/Thread
im Echo-Hub-System zur Verfügung stehen und später insbesondere für
Heizungsautomationen verwendet werden.

Der Hue Secure Contact Sensor bleibt als Alternative bestehen, falls
ein Hue Bridge Pro Bundle mit Kontakt- und Bewegungssensoren bei der
finalen Beschaffung einen deutlichen Preisvorteil bietet.

**Entscheidung über Bundle:** Nach Abschluss der gesamten Hardwareplanung.

---

### Philips Hue Motion Sensor

**Status:** 🟡 Bevorzugt für bewegungsabhängige Lichtsteuerung

Funktionen:

- PIR-Bewegungserkennung
- integrierter Tageslichtsensor
- Tageslichtempfindlichkeit einstellbar
- unterschiedliche Szenen abhängig von der Tageszeit
- direkte Steuerung der Hue-Beleuchtung über Hue Bridge Pro
- batteriebetrieben

Mögliche Einsatzbereiche:

- Flur
- Durchgangsbereiche
- Bereiche ohne notwendige dauerhafte Präsenzerkennung

Vorteil:

Die Kombination aus Bewegung und Umgebungshelligkeit kann direkt
innerhalb des Hue-Systems verarbeitet werden.

**Stückzahl:** Noch offen – Festlegung nach Wohnungsaufmaß.

---

### Philips Hue MotionAware

**Status:** 🟡 Einsatz wird geprüft

Hue MotionAware nutzt kompatible Hue-Leuchten zur Bewegungserkennung,
ohne dass ein zusätzlicher physischer Bewegungssensor erforderlich ist.

Voraussetzungen:

- Hue Bridge Pro
- mindestens drei kompatible Hue-Leuchten für eine Motion Area

Möglicher Vorteil:

In geeigneten Bereichen kann auf zusätzliche Bewegungsmelder verzichtet werden.

Die endgültige Nutzung wird nach der Raum- und Lichtplanung festgelegt.

---

## Bewegungsmelder

### Aqara Motion and Light Sensor P2

**Status:** 🟡 Einsatz wird geprüft

Vorgesehen als kostengünstiger Bewegungssensor für Bereiche,
in denen keine dauerhafte Präsenzerkennung erforderlich ist.

Funktionen:

- PIR-Bewegungserkennung
- Helligkeitssensor
- Matter over Thread
- batteriebetrieben
- direkte Einbindung über Echo Hub vorgesehen
- keine zusätzliche Aqara Bridge vorgesehen

Mögliche Einsatzbereiche:

- Flur
- Durchgangsbereiche
- eventuell Nebenräume

Der offene Übergang zwischen Wohn-/Ess-/Kochbereich und Flur muss
nach dem Wohnungsaufmaß berücksichtigt werden. Möglicherweise kann
dort auf einen zusätzlichen Bewegungsmelder verzichtet werden.

**Stückzahl:** Noch offen – Festlegung nach Wohnungsaufmaß.

Für reine Durchgangsbereiche kann möglicherweise ein klassischer
PIR-Bewegungsmelder anstelle eines Präsenzsensors verwendet werden.

---

## Fenster- und Türkontakte

### Aqara Door and Window Sensor P2

**Status:** 🟢 Grundsätzlich ausgewählt

Geplanter Einsatz zur Überwachung von Fenstern und ausgewählten Türen.

Funktionen:

- Öffnen-/Geschlossen-Status
- Matter over Thread
- batteriebetrieben
- direkte Einbindung über Echo Hub vorgesehen
- keine zusätzliche Aqara Bridge vorgesehen
- nutzbar für Alexa-Automationen
- später für Heizungssteuerung vorgesehen

Geplante Automationen:

- Fenster offen → Heizung im Raum reduzieren/ausschalten
- Fenster geschlossen → Heizungsregelung wieder aktivieren
- Status offener Fenster anzeigen
- optional Benachrichtigung bei geöffneten Fenstern/Türen

**Stückzahl:** Noch offen – Festlegung nach Wohnungsaufmaß.

**Richtpreis:** 32,99 € pro Sensor (Stand September 2026)

Geplanter späterer Einsatzzweck:

- Fensterstatus erkennen
- Heizungsautomation
- Statusanzeige am Echo Hub
- mögliche Sicherheitsfunktionen

---

## Offene Punkte

- [ ] Wohnung aufmessen
- [ ] Grundriss erstellen
- [ ] Sensorpositionen festlegen
- [ ] FP2 für offenen Wohnbereich bewerten
- [ ] Anzahl FP300 bestimmen
- [ ] Bewegungsmelder auswählen
- [ ] Fenster-/Türkontakte auswählen
- [ ] Preise vergleichen
- [ ] finale Komponenten in Einkaufsliste übernehmen