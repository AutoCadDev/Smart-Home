# Systemarchitektur – Smart Home

## Ziel

Die Smart-Home-Architektur soll zentral, stabil, erweiterbar und möglichst unabhängig von einzelnen Herstellern aufgebaut werden.

Home Assistant übernimmt die zentrale Steuerung und verbindet die verschiedenen Geräte und Kommunikationsstandards miteinander.

---

## Zentrale Plattform

### Home Assistant

Home Assistant bildet die zentrale Steuerungsinstanz des Systems.

Aufgaben:

- Geräte verwalten
- Räume und Bereiche strukturieren
- Sensorwerte erfassen
- Automationen ausführen
- Szenen verwalten
- Dashboards bereitstellen
- Benutzer verwalten
- Benachrichtigungen senden
- Schnittstellen zu Apple Home und weiteren Systemen bereitstellen

---

## Grundstruktur

```text
                    Smartphones
                       iPhone
                         │
                         │
                 Home Assistant App
                         │
                         ▼

                   Home Assistant
                  zentrale Steuerung
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼

       Zigbee        Matter/Thread      WLAN
          │              │              │
          ▼              ▼              ▼

      Sensoren         Geräte         Geräte
      Lampen           Sensoren       Kameras
      Schalter         Aktoren        Displays

                         │
                         ▼

                  Automationen
                         │
                         ▼

                     Aktionen