# Geräteliste – Smart Home

## Ziel

Diese Datei dient als zentrale Übersicht über alle geplanten und später tatsächlich eingesetzten Smart-Home-Geräte.

Jedes Gerät soll möglichst eindeutig einem Raum, einer Funktion und einem Kommunikationsstandard zugeordnet werden.

---

## Statuswerte

Für Geräte verwenden wir folgende Statuswerte:

- Geplant
- In Auswahl
- Bestellt
- Vorhanden
- Installiert
- Getestet
- Ersetzt

---

## Gerätetabelle

| Raum | Gerät | Funktion | Hersteller / Modell | Standard | Stromversorgung | Status | Notizen |
|---|---|---|---|---|---|---|---|
| Wohnzimmer | Tablet | Zentrale Bedienung | offen | WLAN | Netzteil | Geplant | Wand-/Standmontage |
| Wohnzimmer | Lampe | Beleuchtung | offen | Zigbee / Matter | Netz | Geplant |  |
| Wohnzimmer | Bewegungsmelder | Präsenz | offen | Zigbee / Thread | Batterie | Geplant |  |
| Wohnzimmer | Temperatursensor | Raumklima | offen | Zigbee / Thread | Batterie | Geplant |  |
| Küche | Fenstersensor | Fensterstatus | offen | Zigbee / Thread | Batterie | Geplant |  |
| Schlafzimmer | Heizkörperthermostat | Heizung | offen | Zigbee / Matter | Batterie | Geplant |  |
| Kinderzimmer | Temperatursensor | Raumklima | offen | Zigbee / Thread | Batterie | Geplant |  |
| Babyzimmer | Temperatursensor | Raumklima | offen | Zigbee / Thread | Batterie | Geplant |  |
| Badezimmer | Wassersensor | Sicherheit | offen | Zigbee / Thread | Batterie | Geplant |  |
| Flur | Bewegungsmelder | Nachtlicht | offen | Zigbee / Thread | Batterie | Geplant |  |
| Balkon | Temperatursensor | Außenklima | offen | Zigbee / Thread | Batterie | Geplant | wetterfest |
| Wohnung | Home-Assistant-Server | Zentrale Steuerung | offen | LAN | Netz | Geplant |  |
| Wohnung | Zigbee-Koordinator | Zigbee-Netzwerk | offen | USB / LAN | Server / PoE | Geplant |  |

---

## Auswahlkriterien

Geräte sollen nach Möglichkeit folgende Kriterien erfüllen:

- lokale Steuerung möglich
- Home-Assistant-kompatibel
- keine zwingende Cloud-Abhängigkeit
- gute Community-Unterstützung
- stabiles Funkprotokoll
- vernünftige Batterielaufzeit
- gute Ersatzteil- und Geräteverfügbarkeit
- möglichst herstellerunabhängig

---

## Bevorzugte Standards

### Priorität 1

Zigbee

Geeignet für:

- Sensoren
- Schalter
- Steckdosen
- Lampen
- Bewegungsmelder
- Fensterkontakte

### Priorität 2

Matter / Thread

Geeignet für:

- neue Gerätegenerationen
- zukünftige Erweiterungen
- herstellerübergreifende Integration

### Priorität 3

WLAN mit lokaler API

Geeignet für:

- Kameras
- Displays
- Tablets
- Multimedia-Geräte

---

## Gerätebewertung

Für konkrete Produkte soll später jeweils bewertet werden:

- Preis
- Home-Assistant-Kompatibilität
- lokale Steuerung
- Funkstandard
- Reichweite
- Batterielaufzeit
- Qualität
- Verfügbarkeit
- Datenschutz
- Zukunftssicherheit

---

## Offene Geräteentscheidungen

- Home-Assistant-Hardware
- Zigbee-Koordinator
- Thread Border Router
- Tablet
- Thermostate
- Fensterkontakte
- Bewegungsmelder
- Temperatursensoren
- smarte Lampen
- smarte Schalter
- Steckdosen
- Wassersensoren
- Rauchmelder
- Türklingel
- Kameras