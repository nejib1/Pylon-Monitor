<p align="center">
  <a href="https://pylon-monitor.com/fr"><img src="assets/pylon-monitor-banner.png" alt="Pylon-Monitor — monitoring et diagnostic à distance pour votre batterie Pylontech" width="800"></a>
</p>

# Pylon-Monitor — Monitoring, Diagnostic Pylontech & Intégration Home Assistant

[🇬🇧 English](README.md) | 🇫🇷 Français | [🇩🇪 Deutsch](README.de.md) | [🇪🇸 Español](README.es.md) | [🇮🇹 Italiano](README.it.md) | [🇳🇱 Nederlands](README.nl.md)

**Last updated:** 2026-08-29 03:49:01 UTC

[![Site officiel](https://img.shields.io/badge/site%20officiel-pylon--monitor.com-D8571C)](https://pylon-monitor.com) [![Licence docs](https://img.shields.io/badge/licence%20docs-CC--BY--4.0-blue)](LICENSE) [![Langues](https://img.shields.io/badge/langues-6-green)](#langues-disponibles)

> **Pylon-Monitor** est un petit boîtier autonome de **monitoring Pylontech** : un appareil WiFi plug & play qui lit le port Console (RS-232) d'une batterie lithium Pylontech et transforme chaque donnée — État de Charge, État de Santé, tension, courant, puissance, tensions par cellule, températures et alarmes — en une **API JSON** propre, un tableau de bord web en direct, et un écran TFT intégré. C'est la solution la plus simple pour faire du **Pylontech Monitor**, du **Pylontech Monitoring**, du **Pylontech Diagnostics**, et du **monitoring Pylontech sans fil / à distance** — avec une intégration native **Home Assistant**, **MQTT**, **Jeedom**, **Node-RED**, **Domoticz** et **openHAB**, configurable en moins de 2 minutes.

Ce dépôt est le hub de documentation publique, de référence d'intégration et de ressources communautaires pour l'appareil **[Pylon-Monitor](https://pylon-monitor.com)**. Ce **n'est pas** le firmware ni la conception matérielle de l'appareil — voir [Ce que contient (et ne contient pas) ce dépôt](#ce-que-contient-et-ne-contient-pas-ce-dépôt) plus bas.

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/product/pylon-monitor-pylontech-battery-monitor.jpg" alt="Appareil Pylon-Monitor connecté au port Console d'une batterie Pylontech" width="600">
</p>

---

## Sommaire

- [Qu'est-ce que Pylon-Monitor ?](#quest-ce-que-pylon-monitor-)
- [Pourquoi Pylon-Monitor — le monitoring Pylontech simplifié](#pourquoi-pylon-monitor--le-monitoring-pylontech-simplifié)
- [Fonctionnalités clés](#fonctionnalités-clés)
- [Batteries Pylontech compatibles](#batteries-pylontech-compatibles)
- [Dans les coulisses — conçu pour les vraies variations de firmware Pylontech](#dans-les-coulisses--conçu-pour-les-vraies-variations-de-firmware-pylontech)
- [Démarrage rapide — plug & play en moins de 2 minutes](#démarrage-rapide--plug--play-en-moins-de-2-minutes)
- [API JSON — récupérer les informations de vos batteries Pylontech](#api-json--récupérer-les-informations-de-vos-batteries-pylontech)
- [Intégration Home Assistant (auto-découverte MQTT & REST)](#intégration-home-assistant-auto-découverte-mqtt--rest)
- [Intégration Jeedom](#intégration-jeedom)
- [Intégration Node-RED](#intégration-node-red)
- [Domoticz, openHAB & toute plateforme HTTP/JSON](#domoticz-openhab--toute-plateforme-httpjson)
- [Confidentialité & sécurité — 100 % local, sans cloud](#confidentialité--sécurité--100--local-sans-cloud)
- [Mises à jour firmware](#mises-à-jour-firmware)
- [Questions fréquentes](#questions-fréquentes)
- [Ce que contient (et ne contient pas) ce dépôt](#ce-que-contient-et-ne-contient-pas-ce-dépôt)
- [Langues disponibles](#langues-disponibles)
- [Liens officiels](#liens-officiels)
- [Licence](#licence)

---

## Qu'est-ce que Pylon-Monitor ?

**Pylon-Monitor** est un outil dédié de **monitoring et de diagnostic Pylontech** — pas un gadget IoT générique, pas un système de gestion de batterie, et non affilié à Pylontech ni approuvé par la marque. Il se connecte au port **Console (RS-232) basse tension** d'une batterie Pylontech, lit en temps réel la télémétrie interne de la batterie, et l'expose de trois façons simultanément :

1. Une **API REST JSON** (`GET /api.json`) — un seul appel HTTP, tout l'état de la batterie, prêt pour n'importe quel script, tableau de bord ou plateforme domotique.
2. Un **tableau de bord web en direct**, accessible depuis n'importe quel navigateur du réseau local — aucune application à installer.
3. Un **écran TFT 1.8" intégré** sur l'appareil lui-même, pour une lecture en un coup d'œil sans même ouvrir un ordinateur.

Si vous cherchiez **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics**, **comment surveiller une batterie Pylontech à distance**, **Pylontech Home Assistant**, **Pylontech MQTT**, **Pylontech Jeedom**, **récupérer les informations des batteries Pylontech**, **suivi SOC SOH Pylontech**, ou **monitoring Pylontech sans fil / à distance**, c'est exactement ce que fait Pylon-Monitor.

## Pourquoi Pylon-Monitor — le monitoring Pylontech simplifié

La plupart des méthodes pour lire l'état interne d'une batterie Pylontech nécessitent un ordinateur portable branché sur le port Console, avec un logiciel du fabricant (PYLON Console / BatteryView) lancé manuellement à chaque consultation. **Pylon-Monitor transforme cela en un service permanent, à distance et sans fil** :

- **Plug & play en moins de 2 minutes.** Branchez le câble Console, alimentez l'appareil, rejoignez son portail WiFi de configuration (`PylonMonitor-Setup`), choisissez votre réseau WiFi domestique. C'est terminé. Aucune application, aucun compte, aucune ligne de commande, aucune soudure.
- **Monitoring Pylontech à distance, en permanence.** Une fois configuré, le SOC, le SOH, la tension, le courant, la puissance, la température et l'état des alarmes de la batterie sont accessibles depuis n'importe où sur votre réseau local (ou à distance via votre propre VPN / reverse proxy — l'appareil lui-même ne dépend d'aucun cloud, voir [Confidentialité & sécurité](#confidentialité--sécurité--100--local-sans-cloud)).
- **Pensé pour l'intégration, pas seulement pour regarder un écran.** L'API JSON et le support natif Home Assistant / MQTT font que les données circulent directement vers votre solution domotique, de suivi énergétique ou de journalisation existante — Home Assistant, Jeedom, Node-RED, Domoticz, openHAB, Grafana, un script cron, un script shell, tout ce qui peut faire une requête HTTP GET.
- **Jusqu'à 16 batteries, modèles mélangés gérés correctement.** Les installations Pylontech chaînées — jusqu'à 16 batteries, ex. 16&times; US5000 (&asymp;76,8 kWh) ou un mélange comme US2000 + US3000 + US5000 — sont détectées et rapportées individuellement, avec le SOC combiné pondéré par capacité entre modèles plutôt qu'une simple moyenne, à condition de brancher le câble RJ45 sur le port Console de l'unité maître. Le détail des tensions par cellule est limité à 64 lectures (les ~4 premières batteries) ; chaque batterie conserve néanmoins toutes ses valeurs SOC/tension/courant/puissance/SOH/cycles.

## Fonctionnalités clés

| Fonctionnalité | Description |
|---|---|
| **API REST JSON** | `GET /api.json` renvoie SOC, SOH, tension, courant, puissance, état, tensions par cellule, détail par batterie, températures, statut WiFi/MQTT et plus, en JSON structuré — aucune authentification requise sur le réseau local, prêt pour Home Assistant, Node-RED, Jeedom, Domoticz, openHAB ou vos propres scripts. |
| **Home Assistant, auto-découverte MQTT** | Renseignez l'IP et les identifiants de votre broker MQTT et 10 capteurs apparaissent automatiquement — SOC, SOH, tension, courant, puissance, température batterie & MOSFET, cycles, état et déséquilibre des cellules — regroupés sous une seule carte appareil, plus un signal de disponibilité en ligne/hors ligne. **Zéro YAML.** |
| **Tableau de bord web** | Des cartes en direct se rafraîchissent toutes les quelques secondes sans jamais recharger la page : Charge (SOC, tension, courant, puissance, état), Santé (SOH, cycles, déséquilibre cellules, compteurs de charge/décharge), Températures (base & MOSFET), Système (IP, signal WiFi, statut MQTT, uptime), Cellules & graphique d'historique de charge sur 24h. |
| **Écran TFT intégré, auto-réparant** | Un écran IPS 1.8" affiche l'État de Charge en gros chiffres, avec tension/courant à côté et SOH/cycles/température en dessous — entièrement personnalisable, et réinitialisé automatiquement pour qu'un incident d'alimentation ne le bloque jamais. |
| **Alarmes configurables (notifications push)** | Définissez vos propres seuils de SOC et de température, avec hystérésis pour qu'une seule mesure erratique ne déclenche pas de spam, et recevez une notification push via Pushover dès qu'un seuil est franchi. |
| **Support multi-batteries — jusqu'à 16 batteries** | Jusqu'à 16 batteries chaînées ensemble — ex. 16&times; US5000 (&asymp;76,8 kWh combinés) ou un mélange de modèles comme US2000 + US3000 + US5000 — chacune détectée et affichée individuellement (SOC, tension, courant, puissance, état, SOH, cycles, températures), avec le SOC combiné pondéré par capacité entre modèles. Un sélecteur bascule entre « toutes les batteries combinées » et chaque batterie séparément. Branchement uniquement sur le port Console de l'unité maître. Détail des tensions par cellule limité à 64 lectures (~4 premières batteries). |
| **Personnalisation de l'affichage écran** | Choisissez exactement quels éléments l'écran TFT physique affiche, avec un aperçu en direct avant d'enregistrer. |
| **Deux niveaux de réinitialisation** | Un double appui sur le bouton reset rouvre uniquement la configuration WiFi (rien d'autre n'est touché) ; le Factory reset depuis le tableau de bord efface tout (WiFi, MQTT, alarmes, connexion). |

Liste complète et illustrée : **[pylon-monitor.com/fr/features](https://pylon-monitor.com/fr/features)**

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/dashboard-pylontech-monitor.png" alt="Tableau de bord web en direct Pylon-Monitor affichant charge, santé, températures, cellules et historique 24h de la batterie Pylontech" width="480">
  <br><sub>Le tableau de bord web en direct — pas d'écran de connexion par défaut, rafraîchi toutes les quelques secondes.</sub>
</p>

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/pylon-monitor-battery-alarms-pushover-notifications.webp" alt="Réglages Pylon-Monitor — carte Alarms avec seuils SOC et température, identifiants Pushover et bouton de notification de test" width="480">
  <br><sub>Alarmes SOC/température configurables — définissez les seuils, ajoutez vos identifiants Pushover, testez en un clic.</sub>
</p>

## Batteries Pylontech compatibles

Pylon-Monitor fonctionne avec toute **batterie Pylontech disposant d'un port Console / RS-232 basse tension** :

- Pylontech US5000 / US5000C (aussi vendue sous le nom US5000-1C)
- Pylontech US3000C
- Pylontech US3000
- Pylontech US2000C
- Pylontech US2000B+
- Pylontech UP2500
- Famille Pylontech Force-L1

**Non compatible** avec les systèmes Pylontech haute tension (Force-H, H48050) ni avec les autres marques de batteries (BYD, Dyness, Seplos, etc.) — le protocole et le connecteur sont spécifiques à Pylontech.

**Jusqu'à 16 batteries, modèles mélangés inclus.** Un seul Pylon-Monitor prend en charge jusqu'à 16 batteries chaînées au total — par exemple 16&times; US5000 (&asymp;76,8 kWh combinés), 16&times; US2000 (&asymp;38,4 kWh), ou n'importe quel mélange comme 2&times; US2000 + 2&times; US3000 + 1&times; US5000 sur la même chaîne. Chaque batterie physique est interrogée et remontée individuellement ; le SOC combiné est pondéré par la capacité propre de chaque unité (lue en direct sur la batterie, jamais codée en dur), pour un chiffre combiné fidèle plutôt qu'une simple moyenne entre unités — voir [Dans les coulisses](#dans-les-coulisses--conçu-pour-les-vraies-variations-de-firmware-pylontech) ci-dessous.

## Dans les coulisses — conçu pour les vraies variations de firmware Pylontech

La sortie console du BMS Pylontech n'est pas parfaitement stable d'une version de firmware à l'autre, ni d'un modèle à l'autre — la disposition exacte des colonnes des réponses console `pwr`/`bat` peut changer avec une mise à jour du firmware BMS, même sur le *même* modèle de batterie. Ce n'est pas hypothétique : c'est constaté sur ce même modèle US5000 utilisé pour développer ce projet, où un firmware BMS plus récent insère quatre colonnes de diagnostic supplémentaires avant les champs d'état de charge et de Coulomb (SOC).

Un moniteur qui suppose une position de colonne fixe pour le « SOC » ou « charge/décharge » afficherait, sur ce firmware, un chiffre complètement faux — silencieusement, sans erreur ni avertissement. Le firmware de Pylon-Monitor analyse à la place la vraie ligne d'en-tête réellement envoyée par la batterie à chaque interrogation, et retrouve chaque valeur **par son nom**, s'adaptant automatiquement à la disposition utilisée par le firmware BMS de cette unité précise. Vérifié à la fois sur le format de réponse exact utilisé en développement et sur une réponse à la disposition différente signalée sur le terrain.

Deux autres détails de fiabilité utiles si vous développez autour de cet appareil :

- **SOC combiné pondéré par capacité.** Sur un pack mélangeant plusieurs modèles/capacités de batteries (ex. US2000 + US3000 + US5000), le pourcentage de charge combiné est pondéré par la capacité nominale propre de chaque unité — lue en direct sur la réponse `info` de la batterie, jamais codée en dur par modèle — plutôt qu'une simple moyenne, qui sous-représenterait les unités les plus grandes.
- **Diagnostics envoyés en flux, jamais mis en tampon.** La vue de diagnostic `/raw` (réponses console brutes, non analysées) est envoyée au navigateur morceau par morceau plutôt qu'assemblée en RAM au préalable. Sur un ESP8266 (&asymp;80 Ko de RAM au total), construire une page de plusieurs kilo-octets dans un seul tampon avant l'envoi est un vrai risque de défaillance sous pression mémoire, d'autant plus que le nombre de batteries chaînées augmente. Le flux garde l'empreinte mémoire de cette page constante, quelle que soit la longueur de la chaîne.

Rien de tout cela ne concerne uniquement la précision de `/api.json` sur un petit banc de test — c'est précisément ce qui permet au même firmware de fonctionner correctement, que vous ayez 1 batterie ou une chaîne complète de 16 unités, et que chaque unité soit du même modèle ou non.

## Démarrage rapide — plug & play en moins de 2 minutes

Pylon-Monitor est conçu pour que **n'importe qui puisse le configurer en moins de deux minutes**, sans application, sans compte et sans ligne de commande :

1. **Connectez** le câble Console fourni entre le Pylon-Monitor et le port Console (RS-232) de votre batterie Pylontech.
2. **Alimentez** l'appareil — l'écran TFT s'allume et l'appareil démarre en mode configuration WiFi.
3. **Rejoignez** le réseau WiFi temporaire qu'il diffuse (`PylonMonitor-Setup`) depuis votre téléphone ou ordinateur.
4. **Choisissez** votre réseau WiFi domestique et saisissez son mot de passe dans le portail captif qui s'ouvre automatiquement.
5. **C'est fait.** L'appareil redémarre sur votre réseau, l'écran TFT affiche sa nouvelle adresse IP, et le tableau de bord est accessible sur `http://<ip-appareil>` ou `http://pylon-monitor.local`.

Aucun flashage de firmware, aucun pilote, aucune application tierce nécessaire pour cette étape. Guide condensé : **[pylon-monitor.com/fr/quickstart](https://pylon-monitor.com/fr/quickstart)** — guide complet pas-à-pas et dépannage : **[pylon-monitor.com/fr/installation](https://pylon-monitor.com/fr/installation)**.

## API JSON — récupérer les informations de vos batteries Pylontech

Le cœur de toute intégration est un seul point d'accès :

```
GET http://<ip-appareil>/api.json
```

- Aucune authentification requise sur le réseau local — pensé pour être interrogé par des plateformes domotiques et des scripts.
- Aucun aller-retour vers le cloud — la réponse vient directement de l'appareil, qui l'a lue directement sur le port Console de la batterie.
- Renvoie l'état complet de la batterie en JSON structuré : résumé de charge, santé, tensions par cellule, détail par batterie (pour les systèmes chaînés), températures, signal WiFi, statut de connexion MQTT, et plus.

Extrait illustratif (voir [`examples/api-response-example.json`](examples/api-response-example.json)) :

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

Tout outil capable de faire une requête HTTP GET et de parser du JSON peut l'utiliser — une tâche cron avec `curl` + `jq`, un script Python/Node, Grafana via une source de données JSON API, ou n'importe quelle plateforme domotique. Voir la réponse complète et chaque champ sur le tableau de bord de l'appareil, ou les captures d'écran annotées sur **[pylon-monitor.com/fr/tour](https://pylon-monitor.com/fr/tour)**.

## Intégration Home Assistant (auto-découverte MQTT & REST)

Pylon-Monitor est conçu pour l'**intégration Home Assistant Pylontech** dès la sortie de la boîte — les deux méthodes sont intégrées directement au firmware : **pas de HACS, pas de composant personnalisé, aucun add-on à installer côté Home Assistant.**

### Option 1 — Auto-découverte MQTT (recommandé)

Si vous utilisez déjà l'add-on *Mosquitto / MQTT broker* dans Home Assistant : renseignez son IP, port, identifiant et mot de passe dans la page Settings de l'appareil. L'appareil publie alors des configurations de découverte Home Assistant standard, et **10 capteurs apparaissent automatiquement** dans **Paramètres → Appareils et services → MQTT**, regroupés sous une seule carte appareil nommée *Pylon-Monitor* :

| Capteur | Topic de découverte |
|---|---|
| SOC batterie | `homeassistant/sensor/pylon-monitor/soc/config` |
| SOH batterie | `homeassistant/sensor/pylon-monitor/soh/config` |
| Tension batterie | `homeassistant/sensor/pylon-monitor/voltage/config` |
| Courant batterie | `homeassistant/sensor/pylon-monitor/current/config` |
| Puissance batterie | `homeassistant/sensor/pylon-monitor/power/config` |
| Température batterie | `homeassistant/sensor/pylon-monitor/temp/config` |
| Température MOSFET | `homeassistant/sensor/pylon-monitor/mostemp/config` |
| Cycles de charge | `homeassistant/sensor/pylon-monitor/cycles/config` |
| État de la batterie | `homeassistant/sensor/pylon-monitor/state/config` |
| Déséquilibre cellules | `homeassistant/sensor/pylon-monitor/celldelta/config` |

Les dix capteurs partagent un unique topic d'état (`pylon-monitor/state`, préfixé par le nom d'hôte) et l'appareil publie un topic de **disponibilité** retenu (`pylon-monitor/status` → `online` / `offline`) avec un vrai Last-Will-and-Testament, afin que chaque capteur grise correctement dans Home Assistant si l'appareil perd l'alimentation ou le WiFi, au lieu de rester figé silencieusement sur sa dernière valeur.

### Option 2 — REST (sans broker MQTT)

La plateforme `rest` intégrée à Home Assistant interroge `/api.json` directement toutes les 30 secondes et crée 6 capteurs. Le YAML est généré pour vous (avec l'IP actuelle de votre appareil déjà renseignée) sur la page Settings de l'appareil — voir [`examples/home-assistant-rest-sensor.yaml`](examples/home-assistant-rest-sensor.yaml) pour la forme générique.

<img src="assets/home-assistant-configuration.yaml-pylontech-monitor.png" alt="Éditeur configuration.yaml de Home Assistant montrant le bloc de capteurs REST Pylon-Monitor collé" width="420"><br>
*Collé tel quel dans `configuration.yaml` — le bloc exact généré par la page Settings, sans rien modifier.*

<img src="assets/home-assistant-pylontech-monitor.png" alt="Configuration d'une carte Jauge Home Assistant avec l'entité Pylontech SOC sélectionnée, affichant 50 % en direct" width="520"><br>
*Un des capteurs obtenus (Pylontech SOC) ajouté à une carte Jauge — 50 % en direct ici.*

> Ne mélangez pas les options 1 et 2 pour le même capteur — vous obtiendrez des entités en double. MQTT couvre déjà tout ce que fait REST, et plus (10 capteurs contre 6), donc il y a rarement une raison d'utiliser les deux.

Guide complet avec captures d'écran : **[pylon-monitor.com/fr/home-assistant](https://pylon-monitor.com/fr/home-assistant)**

## Intégration Jeedom

**Monitoring Pylontech Jeedom** en trois étapes :

1. Installez le plugin **JSON** depuis le market Jeedom.
2. Pointez un équipement vers `http://<ip-appareil>/api.json`.
3. Associez les chemins JSON à des commandes Jeedom — par ex. `summary>soc`, `summary>voltage`, `summary>state`, `net>rssi`.

Voir [`examples/jeedom-json-plugin.md`](examples/jeedom-json-plugin.md) pour un exemple détaillé.

## Intégration Node-RED

Utilisez un nœud **http request** — méthode `GET`, URL `http://<ip-appareil>/api.json`, type de retour *a parsed JSON object* — puis lisez `msg.payload.summary.soc` (ou tout autre champ) en aval. Si MQTT est configuré sur l'appareil, vous pouvez aussi vous abonner directement à `pylon-monitor/state` avec un nœud MQTT-in — aucune interrogation nécessaire. Voir [`examples/node-red-http-request.md`](examples/node-red-http-request.md).

## Domoticz, openHAB & toute plateforme HTTP/JSON

Les données étant du JSON simple, non authentifié, sur HTTP local, **toute plateforme capable d'interroger une URL et de parser du JSON peut intégrer Pylon-Monitor** — les capteurs Dummy/Virtual de Domoticz avec un script, le binding HTTP d'openHAB, un panneau Grafana avec source de données JSON, un script Python avec `requests`, une ligne de commande shell avec `curl | jq`, etc. Aucun SDK propriétaire à installer, aucune clé API à demander.

## Confidentialité & sécurité — 100 % local, sans cloud

- **Aucun service cloud.** L'appareil ne « rentre pas à la maison », ne nécessite aucun compte, et fonctionne entièrement hors ligne sur votre réseau local.
- **Aucune télémétrie, aucun abonnement.** Achat unique ; l'appareil ne remonte aucune donnée d'usage nulle part.
- **Le port Console est en lecture seule.** Pylon-Monitor ne fait que *lire* la télémétrie de la batterie — il n'envoie jamais de commande de contrôle ou de charge, ce qui n'affecte donc pas la garantie du fabricant Pylontech et ne peut pas modifier le comportement de la batterie. C'est un outil de monitoring et de diagnostic, pas un système de gestion de batterie (BMS) ni un régulateur de charge.
- **Connexion au tableau de bord optionnelle.** Le tableau de bord web n'a pas d'écran de connexion par défaut (pratique sur un réseau domestique de confiance) ; un mot de passe peut être activé dans Settings pour les réseaux partagés ou moins fiables.
- **Mise à jour firmware locale.** Les mises à jour s'appliquent depuis le tableau de bord de l'appareil lui-même, pas poussées silencieusement depuis un cloud fournisseur.

## Mises à jour firmware

Pylon-Monitor bénéficie de **mises à jour firmware gratuites à vie** : téléchargez le `.bin` et installez-le depuis le tableau de bord web de l'appareil — aucun câble, aucun outil de reflashage. Changelog et instructions : **[pylon-monitor.com/fr/firmware](https://pylon-monitor.com/fr/firmware)**.

**Dernière version : v2.2** — une passe de fiabilité multi-firmware/multi-modèles. L'analyse des réponses console retrouve désormais les valeurs par nom de colonne plutôt que par position fixe (voir [Dans les coulisses](#dans-les-coulisses--conçu-pour-les-vraies-variations-de-firmware-pylontech) ci-dessus), le SOC combiné sur les packs à modèles mélangés est désormais pondéré par capacité, et la page de diagnostic `/raw` est désormais sûre en mémoire sur les grandes chaînes de batteries. Changelog complet : **[pylon-monitor.com/fr/firmware#changelog](https://pylon-monitor.com/fr/firmware#changelog)**.

## Questions fréquentes

**Pylon-Monitor est-il fabriqué ou approuvé par Pylontech ?**
Non. Pylon-Monitor est un accessoire de monitoring indépendant, tiers. « Pylontech » désigne le fabricant de batteries ; Pylon-Monitor n'y est pas affilié.

**Cela annule-t-il ma garantie Pylontech ?**
Non — le port Console est utilisé strictement en lecture seule pour le monitoring, ce qui n'affecte pas la garantie du fabricant de la batterie.

**Peut-il contrôler ou charger ma batterie ?**
Non. Pylon-Monitor est uniquement un outil de **monitoring et de diagnostic**. Il n'envoie jamais de commande de contrôle ou de charge — voyez-le comme un compteur en lecture seule très complet, pas comme un BMS.

**A-t-il besoin du cloud ou d'une application ?**
Non. La configuration, le tableau de bord et l'API sont 100 % locaux. Aucun compte, aucune application, aucun abonnement.

**Quelles langues le site officiel prend-il en charge ?**
Anglais, français, allemand, néerlandais, espagnol et italien — voir [Langues disponibles](#langues-disponibles).

Plus de questions traitées sur **[pylon-monitor.com/fr/faq](https://pylon-monitor.com/fr/faq)**.

## Ce que contient (et ne contient pas) ce dépôt

Ce dépôt est le **hub public de documentation, de référencement/découverte et de référence d'intégration** de l'appareil Pylon-Monitor — résumés d'installation, notes d'intégration JSON/MQTT/Home Assistant/Jeedom/Node-RED, et liens vers le site officiel.

Il ne contient **volontairement pas** le code source du firmware, la conception interne de la carte/microcontrôleur, les schémas, ni aucun autre détail matériel/firmware propriétaire. Si vous cherchez cela, ce n'est publié ni ici ni ailleurs — seules les interfaces publiques documentées et stables (`/api.json`, topics MQTT, tableau de bord web) sont couvertes, ce qui est tout ce dont une intégration a besoin.

## Langues disponibles

Le [site officiel](https://pylon-monitor.com) et ce dépôt sont entièrement disponibles en :

| Langue | Site | README du dépôt |
|---|---|---|
| 🇬🇧 English | [pylon-monitor.com](https://pylon-monitor.com) | [README.md](README.md) |
| 🇫🇷 Français | [pylon-monitor.com/fr](https://pylon-monitor.com/fr) | [README.fr.md](README.fr.md) |
| 🇩🇪 Deutsch | [pylon-monitor.com/de](https://pylon-monitor.com/de) | [README.de.md](README.de.md) |
| 🇪🇸 Español | [pylon-monitor.com/es](https://pylon-monitor.com/es) | [README.es.md](README.es.md) |
| 🇮🇹 Italiano | [pylon-monitor.com/it](https://pylon-monitor.com/it) | [README.it.md](README.it.md) |
| 🇳🇱 Nederlands | [pylon-monitor.com/nl](https://pylon-monitor.com/nl) | [README.nl.md](README.nl.md) |

## Liens officiels

- [Page d'accueil](https://pylon-monitor.com/fr) — présentation, tarif, achat
- [Fonctionnalités](https://pylon-monitor.com/fr/features) — liste complète
- [Visite guidée](https://pylon-monitor.com/fr/tour) — vraies captures d'écran de chaque écran, y compris la réponse de l'API JSON
- [Démarrage rapide](https://pylon-monitor.com/fr/quickstart) — guide condensé en 5 étapes
- [Guide d'installation](https://pylon-monitor.com/fr/installation) — configuration complète & dépannage
- [Intégration Home Assistant](https://pylon-monitor.com/fr/home-assistant) — configuration détaillée MQTT/REST, référence des topics, exemples de payloads
- [Firmware](https://pylon-monitor.com/fr/firmware) — changelog & instructions de mise à jour
- [FAQ](https://pylon-monitor.com/fr/faq)
- [Contact](https://pylon-monitor.com/fr/contact)

## Licence

Les textes et exemples de ce dépôt sont publiés sous licence [CC BY 4.0](LICENSE) — réutilisation, adaptation et partage libres avec attribution. « Pylon-Monitor » et « Pylontech » sont des marques de leurs propriétaires respectifs ; ce dépôt est une ressource de documentation indépendante et n'est pas affilié à Pylontech.
