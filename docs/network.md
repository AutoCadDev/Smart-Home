# Netzwerkplanung – Smart Home

## Ziel

Das Netzwerk bildet die technische Grundlage des Smart Homes.

Ziel ist ein stabiles, zuverlässiges und möglichst lokales System, bei dem Home Assistant, Smartphones, Tablet, Sensoren und weitere Geräte sauber miteinander kommunizieren können.

---

## Grundprinzip

Das Smart Home wird in mehrere Kommunikationsbereiche aufgeteilt:

- LAN
- WLAN
- Zigbee
- Thread
- optional Bluetooth

Nicht jedes Gerät soll direkt per WLAN verbunden werden.

Kleine Sensoren und batteriebetriebene Geräte sollen bevorzugt über Zigbee oder Thread eingebunden werden.

---

## Home-Assistant-Server

Der Home-Assistant-Server soll dauerhaft im Heimnetzwerk erreichbar sein.

Bevorzugte Verbindung:

- LAN statt WLAN

Vorteile:

- stabilere Verbindung
- geringere Latenz
- weniger Störungen
- zuverlässigere Automationen

Der Server erhält möglichst eine feste IP-Adresse beziehungsweise eine DHCP-Reservierung im Router.

Beispiel:

```text
Home Assistant
192.168.178.20