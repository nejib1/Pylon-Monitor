<p align="center">
  <a href="https://pylon-monitor.com/de"><img src="assets/pylon-monitor-banner.png" alt="Pylon-Monitor — Fernüberwachung und Diagnose für Ihre Pylontech-Batterie" width="800"></a>
</p>

# Pylon-Monitor — Pylontech Monitoring, Diagnose & Home-Assistant-Integration

[🇬🇧 English](README.md) | [🇫🇷 Français](README.fr.md) | 🇩🇪 Deutsch | [🇪🇸 Español](README.es.md) | [🇮🇹 Italiano](README.it.md) | [🇳🇱 Nederlands](README.nl.md)

**Last updated:** 2026-08-31 23:51:01 UTC

[![Offizielle Website](https://img.shields.io/badge/offizielle%20website-pylon--monitor.com-D8571C)](https://pylon-monitor.com) [![Docs-Lizenz](https://img.shields.io/badge/docs%20lizenz-CC--BY--4.0-blue)](LICENSE) [![Sprachen](https://img.shields.io/badge/sprachen-6-green)](#verfügbare-sprachen)

> **Pylon-Monitor** ist ein kleines, eigenständiges Gerät für **Pylontech-Monitoring**: ein Plug-&-Play-WLAN-Gerät, das den Console-Port (RS-232) einer Pylontech-Lithiumbatterie ausliest und jeden Wert — Ladezustand (SOC), Gesundheitszustand (SOH), Spannung, Strom, Leistung, Zellspannungen, Temperaturen und Alarme — in eine saubere **JSON-REST-API**, ein Live-Web-Dashboard und ein eingebautes TFT-Display umwandelt. Es ist der schnellste Weg für **Pylontech-Monitoring**, **Pylontech-Diagnose** und **kabelloses / Fernüberwachung von Pylontech-Batterien** — mit nativer Integration in **Home Assistant**, **MQTT**, **Jeedom**, **Node-RED**, **Domoticz** und **openHAB**, eingerichtet in unter 2 Minuten.

Dieses Repository ist die öffentliche Dokumentation, Integrationsreferenz und Community-Ressource für das Hardware-Gerät **[Pylon-Monitor](https://pylon-monitor.com)**. Es ist **nicht** die Firmware oder das Hardwaredesign des Geräts — siehe [Was dieses Repository enthält (und was nicht)](#was-dieses-repository-enthält-und-was-nicht) weiter unten.

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/product/pylon-monitor-pylontech-battery-monitor.jpg" alt="Pylon-Monitor-Gerät am Console-Port einer Pylontech-Batterie angeschlossen" width="600">
</p>

---

## Inhaltsverzeichnis

- [Was ist Pylon-Monitor?](#was-ist-pylon-monitor)
- [Warum Pylon-Monitor — Pylontech-Monitoring einfach gemacht](#warum-pylon-monitor--pylontech-monitoring-einfach-gemacht)
- [Hauptfunktionen](#hauptfunktionen)
- [Kompatible Pylontech-Batterien](#kompatible-pylontech-batterien)
- [Unter der Haube — gebaut für reale Pylontech-Firmware-Varianz](#unter-der-haube--gebaut-für-reale-pylontech-firmware-varianz)
- [Schnellstart — Plug & Play in unter 2 Minuten](#schnellstart--plug--play-in-unter-2-minuten)
- [JSON-REST-API — Pylontech-Batteriedaten auslesen](#json-rest-api--pylontech-batteriedaten-auslesen)
- [Home-Assistant-Integration (MQTT-Auto-Discovery & REST)](#home-assistant-integration-mqtt-auto-discovery--rest)
- [Jeedom-Integration](#jeedom-integration)
- [Node-RED-Integration](#node-red-integration)
- [Domoticz, openHAB & jede HTTP/JSON-Plattform](#domoticz-openhab--jede-httpjson-plattform)
- [Datenschutz & Sicherheit — 100 % lokal, keine Cloud](#datenschutz--sicherheit--100--lokal-keine-cloud)
- [Firmware-Updates](#firmware-updates)
- [Häufig gestellte Fragen](#häufig-gestellte-fragen)
- [Was dieses Repository enthält (und was nicht)](#was-dieses-repository-enthält-und-was-nicht)
- [Verfügbare Sprachen](#verfügbare-sprachen)
- [Offizielle Links](#offizielle-links)
- [Lizenz](#lizenz)

---

## Was ist Pylon-Monitor?

**Pylon-Monitor** ist ein dediziertes Werkzeug für **Pylontech-Monitoring und -Diagnose** — kein generisches IoT-Gadget, kein Batteriemanagementsystem, und nicht mit Pylontech verbunden oder von Pylontech unterstützt. Es verbindet sich mit dem Niederspannungs-**Console-Port (RS-232)** einer Pylontech-Batterie, liest deren interne Telemetrie in Echtzeit und stellt sie auf drei Arten gleichzeitig bereit:

1. Eine **JSON-REST-API** (`GET /api.json`) — ein einziger HTTP-Aufruf, der komplette Batteriestatus, startklar für jedes Skript, Dashboard oder jede Smart-Home-Plattform.
2. Ein **Live-Web-Dashboard**, erreichbar von jedem Browser im lokalen Netzwerk — keine App zu installieren.
3. Ein **eingebautes 1,8"-TFT-Display** direkt am Gerät, für einen Blick auf den Status ohne überhaupt einen Laptop zu öffnen.

Wenn Sie nach **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics**, **Pylontech-Batterie aus der Ferne überwachen**, **Pylontech Home Assistant**, **Pylontech MQTT**, **Pylontech Jeedom**, **Pylontech-Batteriedaten auslesen**, **Pylontech SOC-SOH-Überwachung** oder **kabellose / Fernüberwachung von Pylontech-Batterien** gesucht haben — genau das leistet Pylon-Monitor.

## Warum Pylon-Monitor — Pylontech-Monitoring einfach gemacht

Die meisten Wege, den internen Zustand einer Pylontech-Batterie auszulesen, erfordern einen Laptop, der am Console-Port angeschlossen ist, mit Herstellersoftware (PYLON Console / BatteryView), die bei jedem Blick auf einen Wert manuell gestartet wird. **Pylon-Monitor macht daraus einen dauerhaften, entfernten, kabellosen Dienst**:

- **Plug & Play in unter 2 Minuten.** Console-Kabel anschließen, Gerät mit Strom versorgen, dem WLAN-Einrichtungsportal beitreten (`PylonMonitor-Setup`), Heim-WLAN auswählen. Fertig. Keine App, kein Konto, keine Kommandozeile, kein Löten.
- **Dauerhaftes, entferntes Pylontech-Monitoring.** Nach der Einrichtung sind SOC, SOH, Spannung, Strom, Leistung, Temperatur und Alarmstatus der Batterie von überall im lokalen Netzwerk verfügbar (oder aus der Ferne über Ihren eigenen VPN/Reverse-Proxy — das Gerät selbst hat keine Cloud-Abhängigkeit, siehe [Datenschutz & Sicherheit](#datenschutz--sicherheit--100--lokal-keine-cloud)).
- **Für Integration gebaut, nicht nur zum Ablesen.** Die JSON-API und native Home-Assistant-/MQTT-Unterstützung sorgen dafür, dass die Daten direkt in Ihre bestehende Smart-Home-, Energiemonitoring- oder Logging-Lösung fließen — Home Assistant, Jeedom, Node-RED, Domoticz, openHAB, Grafana, ein Cronjob, ein Shell-Skript, alles, was einen HTTP-GET machen kann.
- **Bis zu 16 Batterien, gemischte Modelle korrekt gehandhabt.** Verkettete Pylontech-Systeme — bis zu 16 Batterien, z. B. 16&times; US5000 (&asymp;76,8 kWh) oder eine Mischung wie US2000 + US3000 + US5000 — werden einzeln erkannt und gemeldet, mit modellübergreifend kapazitätsgewichtetem statt naiv gemitteltem kombiniertem SOC — vorausgesetzt, das RJ45-Kabel steckt am Console-Anschluss der Master-Einheit. Das Detail der Zellspannungen ist auf 64 Messwerte begrenzt (die ersten ~4 Batterien); jede Batterie erhält trotzdem vollständige SOC-/Spannungs-/Strom-/Leistungs-/SOH-/Zyklenwerte.

## Hauptfunktionen

| Funktion | Beschreibung |
|---|---|
| **JSON-REST-API** | `GET /api.json` liefert SOC, SOH, Spannung, Strom, Leistung, Status, Zellspannungen, Details je Batterie, Temperaturen, WLAN-/MQTT-Status u. v. m. als strukturiertes JSON — keine Authentifizierung im lokalen Netzwerk nötig, startklar für Home Assistant, Node-RED, Jeedom, Domoticz, openHAB oder eigene Skripte. |
| **Home Assistant, MQTT-Auto-Discovery** | IP und Zugangsdaten Ihres MQTT-Brokers eintragen, und 10 Sensoren erscheinen automatisch — SOC, SOH, Spannung, Strom, Leistung, Batterie- & MOSFET-Temperatur, Zyklen, Status und Zellungleichgewicht — gruppiert unter einer Gerätekarte, plus ein Online-/Offline-Verfügbarkeitssignal. **Kein YAML.** |
| **Web-Dashboard** | Live-Karten aktualisieren sich alle paar Sekunden, ohne die Seite neu zu laden: Ladung (SOC, Spannung, Strom, Leistung, Status), Zustand (SOH, Zyklen, Zellungleichgewicht, Lade-/Entladezähler), Temperaturen (Basis & MOSFET), System (IP, WLAN-Signal, MQTT-Status, Laufzeit), Zellen & 24-Stunden-Ladeverlaufsgrafik. |
| **Eingebautes TFT-Display, selbstheilend** | Ein 1,8"-IPS-Display zeigt den Ladezustand in großen Ziffern mit Spannung/Strom daneben und SOH/Zyklen/Temperatur darunter — vollständig anpassbar und wird automatisch neu initialisiert, sodass ein Stromausfall es nie einfriert. |
| **Konfigurierbare Alarme (Push-Benachrichtigungen)** | Eigene SOC- und Temperaturschwellen mit Hysterese festlegen, damit ein einzelner Ausreißer keine Spam-Benachrichtigung auslöst, und eine Push-Benachrichtigung via Pushover erhalten, sobald ein Schwellwert überschritten wird. |
| **Mehrbatterien-Unterstützung — bis zu 16 Batterien** | Bis zu 16 verkettete Batterien — z. B. 16&times; US5000 (&asymp;76,8 kWh kombiniert) oder eine Mischung wie US2000 + US3000 + US5000 — werden erkannt und einzeln angezeigt (SOC, Spannung, Strom, Leistung, Status, SOH, Zyklen, Temperaturen), mit modellübergreifend kapazitätsgewichtetem kombiniertem SOC. Eine Auswahl wechselt zwischen „alle Batterien kombiniert" und jeder einzelnen Batterie. Anschluss nur am Console-Port der Master-Einheit. Detail der Zellspannungen auf 64 Messwerte begrenzt (~4 erste Batterien). |
| **Anpassung der Bildschirmanzeige** | Wählen Sie genau, welche Elemente das physische TFT-Display zeigt, mit Live-Vorschau vor dem Speichern. |
| **Zwei Reset-Stufen** | Doppelklick auf die Reset-Taste öffnet nur die WLAN-Einrichtung erneut (nichts anderes wird berührt); Factory Reset im Dashboard löscht alles (WLAN, MQTT, Alarme, Login). |

Vollständige, bebilderte Funktionsliste: **[pylon-monitor.com/de/features](https://pylon-monitor.com/de/features)**

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/dashboard-pylontech-monitor.png" alt="Pylon-Monitor Live-Web-Dashboard mit Ladung, Zustand, Temperaturen, Zellen und 24h-Verlauf der Pylontech-Batterie" width="480">
  <br><sub>Das Live-Web-Dashboard — standardmäßig kein Login-Bildschirm, aktualisiert sich alle paar Sekunden.</sub>
</p>

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/pylon-monitor-battery-alarms-pushover-notifications.webp" alt="Pylon-Monitor Einstellungen — Alarme-Karte mit SOC- und Temperaturschwellen, Pushover-Zugangsdaten und Test-Benachrichtigungsschaltfläche" width="480">
  <br><sub>Konfigurierbare SOC-/Temperaturalarme — Schwellen festlegen, Pushover-Zugangsdaten hinzufügen, mit einem Klick testen.</sub>
</p>

## Kompatible Pylontech-Batterien

Pylon-Monitor funktioniert mit jeder **Pylontech-Batterie mit Niederspannungs-Console-/RS-232-Port**:

- Pylontech US5000 / US5000C (auch als US5000-1C verkauft)
- Pylontech US3000C
- Pylontech US3000
- Pylontech US2000C
- Pylontech US2000B+
- Pylontech UP2500
- Pylontech-Force-L1-Familie

**Nicht kompatibel** mit Hochspannungs-Pylontech-Systemen (Force-H, H48050) oder anderen Batteriemarken (BYD, Dyness, Seplos usw.) — Protokoll und Steckverbinder sind Pylontech-spezifisch.

**Bis zu 16 Batterien, auch gemischte Modelle.** Ein einzelner Pylon-Monitor unterstützt bis zu 16 verkettete Batterien insgesamt — zum Beispiel 16&times; US5000 (&asymp;76,8 kWh kombiniert), 16&times; US2000 (&asymp;38,4 kWh), oder jede Mischung wie 2&times; US2000 + 2&times; US3000 + 1&times; US5000 in derselben Kette. Jede physische Batterie wird einzeln abgefragt und gemeldet; der kombinierte Ladezustand wird nach der eigenen Kapazität jeder Einheit gewichtet (live von der Batterie gelesen, nicht fest codiert), sodass ein Pack mit gemischten Kapazitäten eine genaue kombinierte Zahl liefert statt eines naiven Durchschnitts über alle Einheiten — siehe [Unter der Haube](#unter-der-haube--gebaut-für-reale-pylontech-firmware-varianz) unten.

## Unter der Haube — gebaut für reale Pylontech-Firmware-Varianz

Die BMS-Console-Ausgabe von Pylontech ist nicht über alle Firmware-Versionen und Modelle hinweg perfekt stabil — das genaue Spaltenlayout der `pwr`/`bat`-Console-Antworten kann sich mit einem BMS-Firmware-Update ändern, sogar beim *selben* Batteriemodell. Das ist nicht hypothetisch: Es wurde am selben US5000-Modell beobachtet, für das dieses Projekt entwickelt wird — dort fügt eine neuere BMS-Firmware vier zusätzliche Diagnosespalten vor den Feldern für Ladezustand und Coulomb (SOC) ein.

Ein Monitor, der eine feste Spaltenposition für „State of Charge" oder „Laden/Entladen" annimmt, würde bei dieser Firmware stillschweigend eine komplett falsche Zahl melden — kein Fehler, keine Warnung, einfach ein falscher SOC. Die Firmware von Pylon-Monitor liest stattdessen die tatsächliche Kopfzeile aus, die die Batterie bei jeder Abfrage wirklich sendet, und findet jeden Wert **anhand seines Namens** — sie passt sich also selbst an das Layout an, das die BMS-Firmware dieser konkreten Einheit verwendet. Geprüft sowohl gegen das während der Entwicklung verwendete exakte Antwortformat als auch gegen ein anders aufgebautes, aus dem Feld gemeldetes Antwortformat.

Zwei weitere Zuverlässigkeitsdetails, die nützlich sind, wenn Sie gegen dieses Gerät entwickeln:

- **Kapazitätsgewichteter kombinierter SOC.** Bei einem Pack mit gemischten Batteriemodellen/-kapazitäten (z. B. US2000 + US3000 + US5000) wird der kombinierte Ladeprozentsatz nach der eigenen Nennkapazität jeder Einheit gewichtet — live aus der `info`-Antwort der Batterie gelesen, nicht pro Modell fest codiert — statt eines einfachen Durchschnitts, der die größeren Einheiten unterrepräsentieren würde.
- **Gestreamte Diagnose, nicht gepuffert.** Die Diagnoseansicht `/raw` (exakte, unverarbeitete Console-Antworten) wird Stück für Stück an den Browser gestreamt, statt vorher komplett im RAM zusammengesetzt zu werden. Auf einem ESP8266 (&asymp;80 KB RAM insgesamt) ist der Aufbau einer mehrere Kilobyte großen Seite in einem einzigen Puffer vor dem Senden ein reales Fehlerrisiko unter Speicherdruck, besonders wenn die Anzahl der verketteten Batterien wächst. Streaming hält den Speicherbedarf dieser Seite unabhängig von der Kettenlänge konstant.

Nichts davon betrifft nur die Genauigkeit von `/api.json` auf einem kleinen Testaufbau — es ist genau der Grund, warum dieselbe Firmware korrekt funktioniert, egal ob Sie 1 Batterie oder eine volle Kette aus 16 Einheiten haben, und egal ob jede Einheit dasselbe Modell ist oder nicht.

## Schnellstart — Plug & Play in unter 2 Minuten

Pylon-Monitor ist so konzipiert, dass **jeder es in unter zwei Minuten einrichten kann**, ohne App, ohne Konto und ohne Kommandozeile:

1. **Anschließen** des mitgelieferten Console-Kabels zwischen Pylon-Monitor und dem Console-Port (RS-232) Ihrer Pylontech-Batterie.
2. **Strom** anlegen — das TFT-Display leuchtet auf und das Gerät startet im WLAN-Einrichtungsmodus.
3. **Beitreten** zum temporären WLAN-Netzwerk, das es ausstrahlt (`PylonMonitor-Setup`), von Ihrem Smartphone oder Laptop aus.
4. **Auswählen** Ihres Heim-WLAN-Netzwerks und Eingabe des Passworts im automatisch erscheinenden Captive-Portal.
5. **Fertig.** Das Gerät startet neu in Ihrem Netzwerk, das TFT-Display zeigt die neue IP-Adresse, und das Dashboard ist live unter `http://<geräte-ip>` oder `http://pylon-monitor.local`.

Kein Firmware-Flashen, keine Treiber, keine App eines Drittanbieters für diesen Schritt nötig. Kompakte Anleitung: **[pylon-monitor.com/de/quickstart](https://pylon-monitor.com/de/quickstart)** — vollständige Schritt-für-Schritt-Anleitung mit Fehlerbehebung: **[pylon-monitor.com/de/installation](https://pylon-monitor.com/de/installation)**.

## JSON-REST-API — Pylontech-Batteriedaten auslesen

Der Kern jeder Integration ist ein einziger Endpunkt:

```
GET http://<geräte-ip>/api.json
```

- Keine Authentifizierung im lokalen Netzwerk nötig — konzipiert für die Abfrage durch Smart-Home-Plattformen und Skripte.
- Kein Cloud-Umweg — die Antwort kommt direkt vom Gerät, das sie direkt vom Console-Port der Batterie gelesen hat.
- Liefert den vollständigen Batteriestatus als strukturiertes JSON: Ladeübersicht, Gesundheit, Zellspannungen, Details je Batterie (bei verketteten Systemen), Temperaturen, WLAN-Signal, MQTT-Verbindungsstatus u. v. m.

Veranschaulichender Auszug (siehe [`examples/api-response-example.json`](examples/api-response-example.json)):

```json
{
  "summary": {
    "soc": 87,
    "voltage": 52.3,
    "current": -4.1,
    "power": -214,
    "state": "discharging"
  },
  "health": {
    "soh": 98
  },
  "net": {
    "rssi": -52
  }
}
```

Jedes Tool, das einen HTTP-GET machen und JSON parsen kann, kann dies nutzen — ein Cronjob mit `curl` + `jq`, ein Python-/Node-Skript, Grafana über die JSON-API-Datenquelle, oder jede Smart-Home-Plattform. Die vollständige Antwort und alle Felder finden Sie im Dashboard des Geräts oder in den kommentierten Screenshots unter **[pylon-monitor.com/de/tour](https://pylon-monitor.com/de/tour)**.

## Home-Assistant-Integration (MQTT-Auto-Discovery & REST)

Pylon-Monitor ist von Haus aus für die **Home-Assistant-Pylontech-Integration** gebaut — beide Methoden sind fest in der Firmware verankert: **kein HACS, keine eigene Komponente, kein auf Home-Assistant-Seite zu installierendes Add-on.**

### Option 1 — MQTT-Auto-Discovery (empfohlen)

Wenn Sie bereits das Add-on *Mosquitto / MQTT broker* in Home Assistant nutzen: Tragen Sie dessen IP, Port, Benutzername und Passwort auf der Settings-Seite des Geräts ein. Das Gerät veröffentlicht dann Standard-Home-Assistant-Discovery-Konfigurationen, und **10 Sensoren erscheinen automatisch** unter **Einstellungen → Geräte & Dienste → MQTT**, gruppiert unter einer Gerätekarte namens *Pylon-Monitor*:

| Sensor | Discovery-Topic |
|---|---|
| Batterie-SOC | `homeassistant/sensor/pylon-monitor/soc/config` |
| Batterie-SOH | `homeassistant/sensor/pylon-monitor/soh/config` |
| Batteriespannung | `homeassistant/sensor/pylon-monitor/voltage/config` |
| Batteriestrom | `homeassistant/sensor/pylon-monitor/current/config` |
| Batterieleistung | `homeassistant/sensor/pylon-monitor/power/config` |
| Batterietemperatur | `homeassistant/sensor/pylon-monitor/temp/config` |
| MOSFET-Temperatur | `homeassistant/sensor/pylon-monitor/mostemp/config` |
| Ladezyklen | `homeassistant/sensor/pylon-monitor/cycles/config` |
| Batteriestatus | `homeassistant/sensor/pylon-monitor/state/config` |
| Zellungleichgewicht | `homeassistant/sensor/pylon-monitor/celldelta/config` |

Alle zehn Sensoren teilen sich ein State-Topic (`pylon-monitor/state`, mit Hostname-Präfix), und das Gerät veröffentlicht ein retained **Verfügbarkeits**-Topic (`pylon-monitor/status` → `online` / `offline`) mit einem echten Last-Will-and-Testament, sodass jeder Sensor in Home Assistant korrekt ausgegraut wird, wenn das Gerät Strom oder WLAN verliert, statt stillschweigend auf seinem letzten Wert einzufrieren.

### Option 2 — REST (kein MQTT-Broker nötig)

Die eingebaute `rest`-Plattform von Home Assistant fragt `/api.json` direkt alle 30 Sekunden ab und erstellt 6 Sensoren. Das YAML wird für Sie generiert (mit der aktuellen IP Ihres Geräts bereits eingetragen) auf der Settings-Seite des Geräts — siehe [`examples/home-assistant-rest-sensor.yaml`](examples/home-assistant-rest-sensor.yaml) für die generische Form.

<img src="assets/home-assistant-configuration.yaml-pylontech-monitor.png" alt="Home Assistant configuration.yaml-Editor mit dem eingefügten Pylon-Monitor REST-Sensorblock" width="420"><br>
*Direkt in `configuration.yaml` eingefügt — genau der Block von der Settings-Seite, ohne Anpassungen.*

<img src="assets/home-assistant-pylontech-monitor.png" alt="Home Assistant Gauge-Karten-Konfiguration mit ausgewählter Pylontech-SOC-Entität, live bei 50 %" width="520"><br>
*Einer der daraus entstandenen Sensoren (Pylontech SOC) auf einer Gauge-Karte — hier live bei 50 %.*

> Mischen Sie Option 1 und Option 2 nicht für denselben Sensor — Sie erhalten doppelte Entitäten. MQTT deckt bereits alles ab, was REST kann, und mehr (10 Sensoren gegenüber 6), daher gibt es selten einen Grund, beide zu nutzen.

Vollständige Anleitung mit Screenshots: **[pylon-monitor.com/de/home-assistant](https://pylon-monitor.com/de/home-assistant)**

## Jeedom-Integration

**Pylontech-Jeedom-Monitoring** in drei Schritten:

1. Installieren Sie das **JSON**-Plugin aus dem Jeedom-Plugin-Store.
2. Richten Sie ein Gerät auf `http://<geräte-ip>/api.json` aus.
3. Ordnen Sie JSON-Pfade Jeedom-Befehlen zu — z. B. `summary>soc`, `summary>voltage`, `summary>state`, `net>rssi`.

Siehe [`examples/jeedom-json-plugin.md`](examples/jeedom-json-plugin.md) für ein ausgearbeitetes Beispiel.

## Node-RED-Integration

Verwenden Sie einen **http request**-Node — Methode `GET`, URL `http://<geräte-ip>/api.json`, Rückgabetyp *a parsed JSON object* — und lesen Sie anschließend `msg.payload.summary.soc` (oder ein beliebiges anderes Feld) weiter im Flow. Falls MQTT auf dem Gerät konfiguriert ist, können Sie auch direkt mit einem MQTT-in-Node `pylon-monitor/state` abonnieren — kein Polling nötig. Siehe [`examples/node-red-http-request.md`](examples/node-red-http-request.md).

## Domoticz, openHAB & jede HTTP/JSON-Plattform

Da die Daten reines, unauthentifiziertes JSON über lokales HTTP sind, kann **jede Plattform, die eine URL abfragen und JSON parsen kann, Pylon-Monitor integrieren** — Domoticz-Dummy-/Virtual-Sensoren mit einem Skript, das HTTP-Binding von openHAB, ein Grafana-Panel mit JSON-Datenquelle, ein Python-Skript mit `requests`, eine Shell-Zeile mit `curl | jq` und so weiter. Kein Hersteller-SDK zu installieren, kein API-Schlüssel zu beantragen.

## Datenschutz & Sicherheit — 100 % lokal, keine Cloud

- **Kein Cloud-Dienst.** Das Gerät „telefoniert nicht nach Hause", benötigt kein Konto und funktioniert vollständig offline in Ihrem lokalen Netzwerk.
- **Keine Telemetrie, kein Abo.** Einmaliger Kauf; das Gerät meldet keine Nutzungsdaten irgendwohin.
- **Console-Port ist nur lesend.** Pylon-Monitor *liest* nur die Batterietelemetrie — es sendet niemals Steuer- oder Ladebefehle, beeinträchtigt also nicht die Herstellergarantie von Pylontech und kann das Batterieverhalten nicht verändern. Es ist ein Monitoring- und Diagnosewerkzeug, kein Batteriemanagementsystem (BMS) und kein Laderegler.
- **Optionaler Dashboard-Login.** Das Web-Dashboard hat standardmäßig keinen Login-Bildschirm (praktisch im vertrauenswürdigen Heimnetz); ein Passwort kann in den Einstellungen für gemeinsam genutzte oder weniger vertrauenswürdige Netzwerke aktiviert werden.
- **Lokales Firmware-OTA.** Updates werden vom Dashboard des Geräts selbst aus angewendet, nicht still aus einer Hersteller-Cloud gepusht.

## Firmware-Updates

Pylon-Monitor erhält **kostenlose lebenslange Firmware-Updates**: die `.bin` herunterladen und über das eigene Web-Dashboard des Geräts installieren — keine Kabel, keine Reflash-Tools. Changelog und Update-Anleitung: **[pylon-monitor.com/de/firmware](https://pylon-monitor.com/de/firmware)**.

**Neueste Version: v2.2** — eine Zuverlässigkeitsüberarbeitung für mehrere Firmware-Versionen/Modelle. Das Parsen der Console-Antworten findet Werte jetzt anhand des Spaltennamens statt einer festen Position (siehe [Unter der Haube](#unter-der-haube--gebaut-für-reale-pylontech-firmware-varianz) oben), der kombinierte SOC bei Packs mit gemischten Modellen ist jetzt kapazitätsgewichtet, und die Diagnoseseite `/raw` ist jetzt speichersicher bei großen Batterieketten. Vollständiges Changelog: **[pylon-monitor.com/de/firmware#changelog](https://pylon-monitor.com/de/firmware#changelog)**.

## Häufig gestellte Fragen

**Wird Pylon-Monitor von Pylontech hergestellt oder unterstützt?**
Nein. Pylon-Monitor ist ein unabhängiges Monitoring-Zubehör eines Drittanbieters. „Pylontech" bezeichnet den Batteriehersteller; Pylon-Monitor ist damit nicht verbunden.

**Erlischt dadurch meine Pylontech-Garantie?**
Nein — der Console-Port wird ausschließlich lesend zum Monitoring genutzt, was die Garantie des Batterieherstellers nicht beeinträchtigt.

**Kann es meine Batterie steuern oder laden?**
Nein. Pylon-Monitor ist ausschließlich ein **Monitoring- und Diagnose**-Werkzeug. Es sendet niemals Steuer- oder Ladebefehle — sehen Sie es als sehr fähigen, nur lesenden Zähler, nicht als BMS.

**Braucht es die Cloud oder eine App?**
Nein. Einrichtung, Dashboard und API sind zu 100 % lokal. Kein Konto, keine App, kein Abo.

**Welche Sprachen unterstützt die offizielle Website?**
Englisch, Französisch, Deutsch, Niederländisch, Spanisch und Italienisch — siehe [Verfügbare Sprachen](#verfügbare-sprachen).

Weitere Fragen beantwortet: **[pylon-monitor.com/de/faq](https://pylon-monitor.com/de/faq)**.

## Was dieses Repository enthält (und was nicht)

Dieses Repository ist der **öffentliche Dokumentations-, SEO-/Discovery-Hub und die Integrationsreferenz** für das Pylon-Monitor-Gerät — Installationszusammenfassungen, JSON-/MQTT-/Home-Assistant-/Jeedom-/Node-RED-Integrationshinweise und Links zur offiziellen Website.

Es enthält **absichtlich nicht** den Firmware-Quellcode des Geräts, das interne Platinen-/Mikrocontroller-Design, Schaltpläne oder andere proprietäre Hardware-/Firmware-Details. Wer danach sucht, findet es weder hier noch anderswo — nur die dokumentierten, stabilen, öffentlichen Schnittstellen (`/api.json`, MQTT-Topics, Web-Dashboard) werden behandelt, was alles ist, was eine Integration benötigt.

## Verfügbare Sprachen

Die [offizielle Website](https://pylon-monitor.com) und dieses Repository sind vollständig verfügbar in:

| Sprache | Website | Repo-README |
|---|---|---|
| 🇬🇧 English | [pylon-monitor.com](https://pylon-monitor.com) | [README.md](README.md) |
| 🇫🇷 Français | [pylon-monitor.com/fr](https://pylon-monitor.com/fr) | [README.fr.md](README.fr.md) |
| 🇩🇪 Deutsch | [pylon-monitor.com/de](https://pylon-monitor.com/de) | [README.de.md](README.de.md) |
| 🇪🇸 Español | [pylon-monitor.com/es](https://pylon-monitor.com/es) | [README.es.md](README.es.md) |
| 🇮🇹 Italiano | [pylon-monitor.com/it](https://pylon-monitor.com/it) | [README.it.md](README.it.md) |
| 🇳🇱 Nederlands | [pylon-monitor.com/nl](https://pylon-monitor.com/nl) | [README.nl.md](README.nl.md) |

## Offizielle Links

- [Startseite](https://pylon-monitor.com/de) — Produktübersicht, Preise, Kauf
- [Funktionen](https://pylon-monitor.com/de/features) — vollständige Funktionsliste
- [Rundgang](https://pylon-monitor.com/de/tour) — echte Screenshots jedes Bildschirms, einschließlich der JSON-API-Antwort
- [Schnellstart](https://pylon-monitor.com/de/quickstart) — kompakte 5-Schritt-Anleitung
- [Installationsanleitung](https://pylon-monitor.com/de/installation) — vollständige Einrichtung & Fehlerbehebung
- [Home-Assistant-Integration](https://pylon-monitor.com/de/home-assistant) — detaillierte MQTT-/REST-Einrichtung, Topic-Referenz, Payload-Beispiele
- [Firmware](https://pylon-monitor.com/de/firmware) — Changelog & Update-Anleitung
- [FAQ](https://pylon-monitor.com/de/faq)
- [Kontakt](https://pylon-monitor.com/de/contact)

## Lizenz

Texte und Beispiele in diesem Repository stehen unter [CC BY 4.0](LICENSE) — freie Nutzung, Anpassung und Weitergabe mit Namensnennung. „Pylon-Monitor" und „Pylontech" sind Marken ihrer jeweiligen Inhaber; dieses Repository ist eine unabhängige Dokumentationsressource und nicht mit Pylontech verbunden.
