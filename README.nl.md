# Pylon-Monitor — Pylontech Monitoring, Diagnose & Home Assistant-integratie

[🇬🇧 English](README.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | [🇪🇸 Español](README.es.md) | [🇮🇹 Italiano](README.it.md) | 🇳🇱 Nederlands

**Last updated:** 2026-08-23 10:13:39 UTC

[![Officiële site](https://img.shields.io/badge/officiële%20site-pylon--monitor.com-D8571C)](https://pylon-monitor.com) [![Docs-licentie](https://img.shields.io/badge/docs%20licentie-CC--BY--4.0-blue)](LICENSE) [![Talen](https://img.shields.io/badge/talen-6-green)](#beschikbare-talen)

> **Pylon-Monitor** is een klein, standalone apparaat voor **Pylontech-accubewaking**: een plug-and-play WiFi-apparaat dat de Console-poort (RS-232) van een Pylontech-lithiumaccu uitleest en elke waarde — laadtoestand (SOC), gezondheidstoestand (SOH), spanning, stroom, vermogen, celspanningen, temperaturen en alarmen — omzet in een overzichtelijke **JSON REST-API**, een live webdashboard en een ingebouwd TFT-scherm. Het is de snelste manier om aan **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics** en **draadloze / monitoring op afstand van Pylontech** te doen — met native integratie in **Home Assistant**, **MQTT**, **Jeedom**, **Node-RED**, **Domoticz** en **openHAB**, ingesteld in minder dan 2 minuten.

Deze repository is het publieke documentatiecentrum, de integratiereferentie en de community-bron voor het hardwareapparaat **[Pylon-Monitor](https://pylon-monitor.com)**. Het is **niet** de firmware of het hardwareontwerp van het apparaat — zie [Wat deze repository wel (en niet) bevat](#wat-deze-repository-wel-en-niet-bevat) hieronder.

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/product/pylon-monitor-pylontech-battery-monitor.jpg" alt="Pylon-Monitor apparaat aangesloten op de Console-poort van een Pylontech-accu" width="600">
</p>

---

## Inhoudsopgave

- [Wat is Pylon-Monitor?](#wat-is-pylon-monitor)
- [Waarom Pylon-Monitor — Pylontech-monitoring eenvoudig gemaakt](#waarom-pylon-monitor--pylontech-monitoring-eenvoudig-gemaakt)
- [Belangrijkste functies](#belangrijkste-functies)
- [Compatibele Pylontech-accu's](#compatibele-pylontech-accus)
- [Onder de motorkap — gebouwd voor echte Pylontech-firmwareverschillen](#onder-de-motorkap--gebouwd-voor-echte-pylontech-firmwareverschillen)
- [Snelstart — plug & play in minder dan 2 minuten](#snelstart--plug--play-in-minder-dan-2-minuten)
- [JSON REST-API — accugegevens van uw Pylontech ophalen](#json-rest-api--accugegevens-van-uw-pylontech-ophalen)
- [Home Assistant-integratie (MQTT auto-discovery & REST)](#home-assistant-integratie-mqtt-auto-discovery--rest)
- [Jeedom-integratie](#jeedom-integratie)
- [Node-RED-integratie](#node-red-integratie)
- [Domoticz, openHAB & elk HTTP/JSON-platform](#domoticz-openhab--elk-httpjson-platform)
- [Privacy & beveiliging — 100% lokaal, geen cloud](#privacy--beveiliging--100-lokaal-geen-cloud)
- [Firmware-updates](#firmware-updates)
- [Veelgestelde vragen](#veelgestelde-vragen)
- [Wat deze repository wel (en niet) bevat](#wat-deze-repository-wel-en-niet-bevat)
- [Beschikbare talen](#beschikbare-talen)
- [Officiële links](#officiële-links)
- [Licentie](#licentie)

---

## Wat is Pylon-Monitor?

**Pylon-Monitor** is een speciaal ontwikkeld hulpmiddel voor **Pylontech-monitoring en -diagnose** — geen generiek IoT-gadget, geen batterijmanagementsysteem, en niet verbonden aan of goedgekeurd door Pylontech. Het maakt verbinding met de laagspannings-**Console-poort (RS-232)** van een Pylontech-accu, leest de interne telemetrie van de accu in realtime uit, en stelt deze op drie manieren tegelijk beschikbaar:

1. Een **JSON REST-API** (`GET /api.json`) — één HTTP-aanroep, de volledige accustatus, klaar voor elk script, dashboard of domoticaplatform.
2. Een **live webdashboard**, bereikbaar vanaf elke browser op het lokale netwerk — geen app te installeren.
3. Een **ingebouwd 1,8"-TFT-scherm** op het apparaat zelf, voor een blik op de status zonder ooit een laptop te openen.

Als u zocht op **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics**, **Pylontech-accu op afstand bewaken**, **Pylontech Home Assistant**, **Pylontech MQTT**, **Pylontech Jeedom**, **gegevens van Pylontech-accu's ophalen**, **SOC SOH-bewaking Pylontech**, of **draadloze / monitoring op afstand van Pylontech**, dan is dit precies wat Pylon-Monitor doet.

## Waarom Pylon-Monitor — Pylontech-monitoring eenvoudig gemaakt

De meeste manieren om de interne status van een Pylontech-accu uit te lezen vereisen een laptop die op de Console-poort is aangesloten, met fabrikantensoftware (PYLON Console / BatteryView) die elke keer handmatig wordt gestart om één waarde te bekijken. **Pylon-Monitor maakt daar een permanente, externe, draadloze dienst van**:

- **Plug & play in minder dan 2 minuten.** Sluit de Console-kabel aan, geef het apparaat stroom, sluit aan op het WiFi-instelportaal (`PylonMonitor-Setup`), kies uw thuisnetwerk. Klaar. Geen app, geen account, geen commandoregel, geen soldeerwerk.
- **Permanente Pylontech-bewaking op afstand.** Eenmaal geconfigureerd zijn SOC, SOH, spanning, stroom, vermogen, temperatuur en alarmstatus van de accu overal op uw lokale netwerk beschikbaar (of op afstand via uw eigen VPN/reverse proxy — het apparaat zelf heeft geen cloudafhankelijkheid, zie [Privacy & beveiliging](#privacy--beveiliging--100-lokaal-geen-cloud)).
- **Gebouwd voor integratie, niet alleen om naar een scherm te kijken.** De JSON-API en native Home Assistant-/MQTT-ondersteuning zorgen ervoor dat de data rechtstreeks naar uw bestaande domotica-, energiebewakings- of logging-omgeving stroomt — Home Assistant, Jeedom, Node-RED, Domoticz, openHAB, Grafana, een cronjob, een shellscript, alles wat een HTTP GET kan doen.
- **Tot 16 accu's, gemengde modellen correct verwerkt.** Aan elkaar gekoppelde Pylontech-systemen — tot 16 accu's, bijv. 16&times; US5000 (&asymp;76,8 kWh) of een mix zoals US2000 + US3000 + US5000 — worden individueel gedetecteerd en gerapporteerd, met een over modellen heen capaciteitsgewogen gecombineerd SOC in plaats van een naïef gemiddelde — mits de RJ45-kabel in de Console-poort van de master-eenheid zit. Het detail van de celspanningen is beperkt tot 64 metingen (de eerste ~4 accu's); elke accu behoudt wel al zijn SOC-/spannings-/stroom-/vermogen-/SOH-/cyclusgegevens.

## Belangrijkste functies

| Functie | Beschrijving |
|---|---|
| **JSON REST-API** | `GET /api.json` geeft SOC, SOH, spanning, stroom, vermogen, status, celspanningen, detail per accu, temperaturen, WiFi-/MQTT-status en meer als gestructureerde JSON — geen authenticatie nodig op het lokale netwerk, klaar voor Home Assistant, Node-RED, Jeedom, Domoticz, openHAB of uw eigen scripts. |
| **Home Assistant, MQTT auto-discovery** | Vul de IP en inloggegevens van uw MQTT-broker in en 10 sensoren verschijnen automatisch — SOC, SOH, spanning, stroom, vermogen, accu- & MOSFET-temperatuur, cycli, status en celonbalans — gegroepeerd onder één apparaatkaart, plus een online/offline-beschikbaarheidssignaal. **Geen YAML.** |
| **Webdashboard** | Live kaarten verversen elke paar seconden zonder ooit de pagina te herladen: Lading (SOC, spanning, stroom, vermogen, status), Gezondheid (SOH, cycli, celonbalans, laad-/ontlaadtellers), Temperaturen (basis & MOSFET), Systeem (IP, WiFi-signaal, MQTT-status, uptime), Cellen & 24u-laadgeschiedenisgrafiek. |
| **Ingebouwd TFT-scherm, zelfherstellend** | Een 1,8"-IPS-scherm toont de laadtoestand in grote cijfers, met spanning/stroom ernaast en SOH/cycli/temperatuur eronder — volledig aanpasbaar, en wordt automatisch opnieuw geïnitialiseerd zodat een stroomstoring het nooit laat vastlopen. |
| **Instelbare alarmen (pushmeldingen)** | Stel uw eigen SOC- en temperatuurdrempels in, met hysterese zodat één ruizige meting geen spam veroorzaakt, en ontvang een pushmelding via Pushover zodra een drempel wordt overschreden. |
| **Ondersteuning voor meerdere accu's — tot 16 accu's** | Tot 16 aan elkaar gekoppelde accu's — bijv. 16&times; US5000 (&asymp;76,8 kWh gecombineerd) of een mix van modellen zoals US2000 + US3000 + US5000 — elk gedetecteerd en individueel getoond (SOC, spanning, stroom, vermogen, status, SOH, cycli, temperaturen), met het gecombineerde SOC capaciteitsgewogen over modellen heen. Een keuzeschakelaar wisselt tussen "alle accu's gecombineerd" en elke afzonderlijke accu. Alleen aansluiten op de Console-poort van de master-eenheid. Detail van de celspanningen beperkt tot 64 metingen (~eerste 4 accu's). |
| **Aanpassing schermweergave** | Kies precies welke elementen het fysieke TFT-scherm toont, met een live voorbeeld voordat u opslaat. |
| **Twee reset-niveaus** | Een dubbele druk op de resetknop heropent alleen de WiFi-instelling (verder wordt niets aangeraakt); Factory reset vanaf het dashboard wist alles (WiFi, MQTT, alarmen, login). |

Volledige, geïllustreerde functielijst: **[pylon-monitor.com/nl/features](https://pylon-monitor.com/nl/features)**

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/dashboard-pylontech-monitor.png" alt="Live web-dashboard van Pylon-Monitor met lading, gezondheid, temperaturen, cellen en 24u-geschiedenis van de Pylontech-accu" width="480">
  <br><sub>Het live webdashboard — standaard geen inlogscherm, ververst elke paar seconden.</sub>
</p>

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/pylon-monitor-battery-alarms-pushover-notifications.webp" alt="Pylon-Monitor Instellingen — Alarms-kaart met SOC- en temperatuurdrempels, Pushover-gegevens en een testmeldingsknop" width="480">
  <br><sub>Instelbare SOC-/temperatuuralarmen — stel drempels in, koppel uw Pushover-account, test met één klik.</sub>
</p>

## Compatibele Pylontech-accu's

Pylon-Monitor werkt met elke **Pylontech-accu met een laagspannings-Console-/RS-232-poort**:

- Pylontech US5000 / US5000C (ook verkocht als US5000-1C)
- Pylontech US3000C
- Pylontech US3000
- Pylontech US2000C
- Pylontech US2000B+
- Pylontech UP2500
- Pylontech Force-L1-familie

**Niet compatibel** met hoogspannings-Pylontech-systemen (Force-H, H48050) of andere accumerken (BYD, Dyness, Seplos, enz.) — het protocol en de connector zijn Pylontech-specifiek.

**Tot 16 accu's, gemengde modellen inbegrepen.** Eén enkele Pylon-Monitor ondersteunt tot 16 aan elkaar geschakelde accu's in totaal — bijvoorbeeld 16&times; US5000 (&asymp;76,8 kWh gecombineerd), 16&times; US2000 (&asymp;38,4 kWh), of elke mix zoals 2&times; US2000 + 2&times; US3000 + 1&times; US5000 in dezelfde keten. Elke fysieke accu wordt individueel bevraagd en gerapporteerd; het gecombineerde SOC wordt gewogen naar de eigen capaciteit van elke eenheid (live van de accu gelezen, niet hardgecodeerd), zodat een pack met gemengde capaciteiten een nauwkeurig gecombineerd getal geeft in plaats van een naïef gemiddelde over de eenheden — zie [Onder de motorkap](#onder-de-motorkap--gebouwd-voor-echte-pylontech-firmwareverschillen) hieronder.

## Onder de motorkap — gebouwd voor echte Pylontech-firmwareverschillen

De BMS-console-uitvoer van Pylontech is niet perfect stabiel over firmwareversies en modellen heen — de exacte kolomindeling van de `pwr`/`bat`-consoleantwoorden kan veranderen bij een BMS-firmware-update, zelfs op *hetzelfde* accumodel. Dit is niet hypothetisch: het is waargenomen op precies hetzelfde US5000-model waarvoor dit project wordt ontwikkeld, waar een nieuwere BMS-firmware vier extra diagnostische kolommen invoegt vóór de laadstatus- en Coulomb-velden (SOC).

Een monitor die een vaste kolompositie aanneemt voor "SOC" of "opladen/ontladen" zou op die firmware stilletjes een compleet verkeerd getal rapporteren — geen fout, geen waarschuwing, gewoon een verkeerd SOC. De firmware van Pylon-Monitor leest in plaats daarvan de echte header-regel die de accu bij elke bevraging daadwerkelijk stuurt, en zoekt elke waarde op **via de naam**, en past zich zo automatisch aan wat de BMS-firmware van die specifieke eenheid gebruikt. Geverifieerd tegen zowel het exacte antwoordformaat gebruikt tijdens ontwikkeling als een anders opgebouwd antwoord dat vanuit het veld gemeld werd.

Nog twee betrouwbaarheidsdetails die nuttig zijn als u tegen dit apparaat ontwikkelt:

- **Capaciteitsgewogen gecombineerd SOC.** Op een pack met gemengde accumodellen/-capaciteiten (bijv. US2000 + US3000 + US5000) wordt het gecombineerde laadpercentage gewogen naar de eigen nominale capaciteit van elke eenheid — live gelezen uit het `info`-antwoord van de accu, nooit hardgecodeerd per model — in plaats van een simpel gemiddelde, dat de grotere eenheden zou onderrepresenteren.
- **Gestreamde diagnostiek, niet gebufferd.** De diagnostische weergave `/raw` (exacte, onverwerkte consoleantwoorden) wordt stuk voor stuk naar de browser gestreamd in plaats van eerst volledig in het RAM te worden opgebouwd. Op een ESP8266 (&asymp;80 KB totaal RAM) is het opbouwen van een pagina van meerdere kilobytes in één buffer vóór het verzenden een reëel faalrisico onder geheugendruk, vooral naarmate het aantal aan elkaar geschakelde accu's groeit. Streamen houdt de geheugenvoetafdruk van die pagina constant, ongeacht de ketenlengte.

Niets hiervan gaat alleen over de nauwkeurigheid van `/api.json` op een kleine testopstelling — het is precies de reden waarom dezelfde firmware correct werkt, of u nu 1 accu heeft of een volledige keten van 16 eenheden, en of elke eenheid hetzelfde model is of niet.

## Snelstart — plug & play in minder dan 2 minuten

Pylon-Monitor is zo ontworpen dat **iedereen het in minder dan twee minuten kan instellen**, zonder app, zonder account en zonder commandoregel:

1. **Sluit** de meegeleverde Console-kabel aan tussen de Pylon-Monitor en de Console-poort (RS-232) van uw Pylontech-accu.
2. **Geef stroom** aan het apparaat — het TFT-scherm licht op en het apparaat start op in WiFi-instelmodus.
3. **Sluit aan** op het tijdelijke WiFi-netwerk dat het uitzendt (`PylonMonitor-Setup`) vanaf uw telefoon of laptop.
4. **Kies** uw thuisnetwerk en voer het wachtwoord in op het captive portal dat automatisch opent.
5. **Klaar.** Het apparaat herstart op uw netwerk, het TFT-scherm toont het nieuwe IP-adres, en het dashboard is live op `http://<apparaat-ip>` of `http://pylon-monitor.local`.

Geen firmware flashen, geen drivers, geen app van derden nodig voor deze stap. Beknopte handleiding: **[pylon-monitor.com/nl/quickstart](https://pylon-monitor.com/nl/quickstart)** — volledige stap-voor-stap handleiding met probleemoplossing: **[pylon-monitor.com/nl/installation](https://pylon-monitor.com/nl/installation)**.

## JSON REST-API — accugegevens van uw Pylontech ophalen

De kern van elke integratie is één endpoint:

```
GET http://<apparaat-ip>/api.json
```

- Geen authenticatie nodig op het lokale netwerk — ontworpen om te worden bevraagd door domoticaplatforms en scripts.
- Geen cloud-omweg — het antwoord komt rechtstreeks van het apparaat, dat het rechtstreeks van de Console-poort van de accu heeft gelezen.
- Geeft de volledige accustatus terug als gestructureerde JSON: laadoverzicht, gezondheid, celspanningen, detail per accu (voor gekoppelde systemen), temperaturen, WiFi-signaal, MQTT-verbindingsstatus en meer.

Illustratief fragment (zie [`examples/api-response-example.json`](examples/api-response-example.json)):

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

Elke tool die een HTTP GET kan doen en JSON kan parsen, kan dit gebruiken — een cronjob met `curl` + `jq`, een Python-/Node-script, Grafana via de JSON API-databron, of elk domoticaplatform. Bekijk het volledige antwoord en elk veld op het dashboard van het apparaat zelf, of de geannoteerde screenshots op **[pylon-monitor.com/nl/tour](https://pylon-monitor.com/nl/tour)**.

## Home Assistant-integratie (MQTT auto-discovery & REST)

Pylon-Monitor is standaard gebouwd voor **Home Assistant Pylontech-integratie** — beide methoden zitten rechtstreeks in de firmware ingebakken: **geen HACS, geen aangepaste component, geen add-on te installeren aan de kant van Home Assistant.**

### Optie 1 — MQTT auto-discovery (aanbevolen)

Als u al de add-on *Mosquitto / MQTT broker* in Home Assistant gebruikt: vul IP, poort, gebruikersnaam en wachtwoord in op de Settings-pagina van het apparaat. Het apparaat publiceert dan standaard Home Assistant discovery-configuraties, en **10 sensoren verschijnen automatisch** onder **Instellingen → Apparaten & diensten → MQTT**, gegroepeerd onder één apparaatkaart met de naam *Pylon-Monitor*:

| Sensor | Discovery-topic |
|---|---|
| Accu-SOC | `homeassistant/sensor/pylon-monitor/soc/config` |
| Accu-SOH | `homeassistant/sensor/pylon-monitor/soh/config` |
| Accuspanning | `homeassistant/sensor/pylon-monitor/voltage/config` |
| Accustroom | `homeassistant/sensor/pylon-monitor/current/config` |
| Accuvermogen | `homeassistant/sensor/pylon-monitor/power/config` |
| Accutemperatuur | `homeassistant/sensor/pylon-monitor/temp/config` |
| MOSFET-temperatuur | `homeassistant/sensor/pylon-monitor/mostemp/config` |
| Laadcycli | `homeassistant/sensor/pylon-monitor/cycles/config` |
| Accustatus | `homeassistant/sensor/pylon-monitor/state/config` |
| Celonbalans | `homeassistant/sensor/pylon-monitor/celldelta/config` |

Alle tien sensoren delen één state-topic (`pylon-monitor/state`, met hostnaam-prefix), en het apparaat publiceert een retained **beschikbaarheids**-topic (`pylon-monitor/status` → `online` / `offline`) met een echte Last-Will-and-Testament, zodat elke sensor correct grijs wordt in Home Assistant als het apparaat stroom of WiFi verliest, in plaats van stilzwijgend te bevriezen op de laatste waarde.

### Optie 2 — REST (geen MQTT-broker nodig)

Het ingebouwde `rest`-platform van Home Assistant bevraagt `/api.json` rechtstreeks elke 30 seconden en maakt 6 sensoren aan. De YAML wordt voor u gegenereerd (met de huidige IP van uw apparaat al ingevuld) op de Settings-pagina van het apparaat — zie [`examples/home-assistant-rest-sensor.yaml`](examples/home-assistant-rest-sensor.yaml) voor de generieke vorm.

<img src="assets/home-assistant-configuration.yaml-pylontech-monitor.png" alt="Home Assistant configuration.yaml-editor met het geplakte Pylon-Monitor REST-sensorblok" width="420"><br>
*Rechtstreeks geplakt in `configuration.yaml` — precies het blok van de Settings-pagina, zonder aanpassingen.*

<img src="assets/home-assistant-pylontech-monitor.png" alt="Home Assistant Gauge-kaartconfiguratie met de Pylontech SOC-entiteit geselecteerd, live op 50%" width="520"><br>
*Een van de resulterende sensoren (Pylontech SOC) toegevoegd aan een Gauge-kaart — hier live op 50%.*

> Meng optie 1 en optie 2 niet voor dezelfde sensor — u krijgt dan dubbele entiteiten. MQTT dekt al alles wat REST doet, en meer (10 sensoren tegenover 6), dus er is zelden reden om beide te gebruiken.

Volledige handleiding met screenshots: **[pylon-monitor.com/nl/home-assistant](https://pylon-monitor.com/nl/home-assistant)**

## Jeedom-integratie

**Pylontech Jeedom-bewaking** in drie stappen:

1. Installeer de **JSON**-plugin uit de Jeedom-pluginwinkel.
2. Richt een apparaat op `http://<apparaat-ip>/api.json`.
3. Koppel JSON-paden aan Jeedom-commando's — bijv. `summary>soc`, `summary>voltage`, `summary>state`, `net>rssi`.

Zie [`examples/jeedom-json-plugin.md`](examples/jeedom-json-plugin.md) voor een uitgewerkt voorbeeld.

## Node-RED-integratie

Gebruik een **http request**-node — methode `GET`, URL `http://<apparaat-ip>/api.json`, retourtype *a parsed JSON object* — en lees vervolgens `msg.payload.summary.soc` (of een ander veld) verderop in de flow. Als MQTT op het apparaat is geconfigureerd, kunt u ook rechtstreeks abonneren op `pylon-monitor/state` met een MQTT-in-node — geen polling nodig. Zie [`examples/node-red-http-request.md`](examples/node-red-http-request.md).

## Domoticz, openHAB & elk HTTP/JSON-platform

Omdat de data eenvoudige, ongeauthenticeerde JSON is over lokale HTTP, kan **elk platform dat een URL kan bevragen en JSON kan parsen Pylon-Monitor integreren** — de Dummy/Virtual-sensoren van Domoticz met een script, de HTTP-binding van openHAB, een Grafana-paneel met JSON-databron, een Python-script met `requests`, een shell-regel met `curl | jq`, enzovoort. Geen eigen SDK te installeren, geen API-sleutel aan te vragen.

## Privacy & beveiliging — 100% lokaal, geen cloud

- **Geen clouddienst.** Het apparaat "belt niet naar huis", vereist geen account, en werkt volledig offline op uw lokale netwerk.
- **Geen telemetrie, geen abonnement.** Eenmalige aankoop; het apparaat rapporteert nergens gebruiksgegevens.
- **Console-poort is alleen-lezen.** Pylon-Monitor *leest* alleen accutelemetrie uit — het stuurt nooit besturings- of laadcommando's, dus het heeft geen invloed op de garantie van fabrikant Pylontech en kan het gedrag van de accu niet wijzigen. Het is een bewakings- en diagnosetool, geen batterijmanagementsysteem (BMS) of laadregelaar.
- **Optionele dashboardlogin.** Het webdashboard heeft standaard geen inlogscherm (handig op een vertrouwd thuisnetwerk); een wachtwoord kan worden ingeschakeld in Settings voor gedeelde of minder vertrouwde netwerken.
- **Lokale firmware-OTA.** Updates worden toegepast vanuit het eigen dashboard van het apparaat, niet stilletjes gepusht vanuit een leverancierscloud.

## Firmware-updates

Pylon-Monitor ontvangt **gratis levenslange firmware-updates**: download de `.bin` en installeer deze vanuit het eigen webdashboard van het apparaat — geen kabels, geen reflash-tools. Changelog en update-instructies: **[pylon-monitor.com/nl/firmware](https://pylon-monitor.com/nl/firmware)**.

**Nieuwste versie: v2.2** — een betrouwbaarheidsronde voor meerdere firmwareversies/modellen. Het parsen van consoleantwoorden vindt waarden nu op basis van de kolomnaam in plaats van een vaste positie (zie [Onder de motorkap](#onder-de-motorkap--gebouwd-voor-echte-pylontech-firmwareverschillen) hierboven), het gecombineerde SOC bij packs met gemengde modellen is nu capaciteitsgewogen, en de diagnosepagina `/raw` is nu geheugenveilig bij grote accuketens. Volledig changelog: **[pylon-monitor.com/nl/firmware#changelog](https://pylon-monitor.com/nl/firmware#changelog)**.

## Veelgestelde vragen

**Is Pylon-Monitor gemaakt of goedgekeurd door Pylontech?**
Nee. Pylon-Monitor is een onafhankelijk, extern bewakingsaccessoire. "Pylontech" verwijst naar de accufabrikant; Pylon-Monitor is daaraan niet verbonden.

**Vervalt hierdoor mijn Pylontech-garantie?**
Nee — de Console-poort wordt strikt alleen-lezen gebruikt voor bewaking, wat de garantie van de accufabrikant niet beïnvloedt.

**Kan het mijn accu besturen of opladen?**
Nee. Pylon-Monitor is uitsluitend een **bewakings- en diagnosetool**. Het stuurt nooit besturings- of laadcommando's — zie het als een zeer capabele alleen-lezen meter, geen BMS.

**Heeft het de cloud of een app nodig?**
Nee. Installatie, dashboard en API zijn 100% lokaal. Geen account, geen app, geen abonnement.

**Welke talen ondersteunt de officiële site?**
Engels, Frans, Duits, Nederlands, Spaans en Italiaans — zie [Beschikbare talen](#beschikbare-talen).

Meer vragen beantwoord op **[pylon-monitor.com/nl/faq](https://pylon-monitor.com/nl/faq)**.

## Wat deze repository wel (en niet) bevat

Deze repository is het **publieke documentatie-, SEO/ontdekkings- en integratiereferentiecentrum** voor het Pylon-Monitor-apparaat — installatiesamenvattingen, JSON-/MQTT-/Home Assistant-/Jeedom-/Node-RED-integratienotities, en links naar de officiële site.

Het bevat **opzettelijk niet** de firmware-broncode van het apparaat, het interne board-/microcontrollerontwerp, schema's, of andere eigen hardware-/firmwaredetails. Wie daarnaar zoekt, vindt dat noch hier, noch elders — alleen de gedocumenteerde, stabiele, publieke interfaces (`/api.json`, MQTT-topics, webdashboard) worden behandeld, wat alles is wat een integratie nodig heeft.

## Beschikbare talen

De [officiële site](https://pylon-monitor.com) en deze repository zijn volledig beschikbaar in:

| Taal | Site | Repo-README |
|---|---|---|
| 🇬🇧 English | [pylon-monitor.com](https://pylon-monitor.com) | [README.md](README.md) |
| 🇫🇷 Français | [pylon-monitor.com/fr](https://pylon-monitor.com/fr) | [README.fr.md](README.fr.md) |
| 🇩🇪 Deutsch | [pylon-monitor.com/de](https://pylon-monitor.com/de) | [README.de.md](README.de.md) |
| 🇪🇸 Español | [pylon-monitor.com/es](https://pylon-monitor.com/es) | [README.es.md](README.es.md) |
| 🇮🇹 Italiano | [pylon-monitor.com/it](https://pylon-monitor.com/it) | [README.it.md](README.it.md) |
| 🇳🇱 Nederlands | [pylon-monitor.com/nl](https://pylon-monitor.com/nl) | [README.nl.md](README.nl.md) |

## Officiële links

- [Homepage](https://pylon-monitor.com/nl) — productoverzicht, prijs, aankoop
- [Functies](https://pylon-monitor.com/nl/features) — volledige functielijst
- [Visuele tour](https://pylon-monitor.com/nl/tour) — echte screenshots van elk scherm, inclusief de JSON API-respons
- [Snelstart](https://pylon-monitor.com/nl/quickstart) — beknopte 5-stappen handleiding
- [Installatiehandleiding](https://pylon-monitor.com/nl/installation) — volledige installatie & probleemoplossing
- [Home Assistant-integratie](https://pylon-monitor.com/nl/home-assistant) — gedetailleerde MQTT-/REST-instellingen, topic-referentie, payload-voorbeelden
- [Firmware](https://pylon-monitor.com/nl/firmware) — changelog & update-instructies
- [FAQ](https://pylon-monitor.com/nl/faq)
- [Contact](https://pylon-monitor.com/nl/contact)

## Licentie

De teksten en voorbeelden in deze repository zijn vrijgegeven onder [CC BY 4.0](LICENSE) — vrij te hergebruiken, aan te passen en te delen met naamsvermelding. "Pylon-Monitor" en "Pylontech" zijn merken van hun respectievelijke eigenaars; deze repository is een onafhankelijke documentatiebron en is niet verbonden aan Pylontech.
