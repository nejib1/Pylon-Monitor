<p align="center">
  <a href="https://pylon-monitor.com/es"><img src="assets/pylon-monitor-banner.png" alt="Pylon-Monitor — monitorización y diagnóstico remoto para su batería Pylontech" width="800"></a>
</p>

# Pylon-Monitor — Monitorización, Diagnóstico Pylontech e Integración con Home Assistant

[🇬🇧 English](README.md) | [🇫🇷 Français](README.fr.md) | [🇩🇪 Deutsch](README.de.md) | 🇪🇸 Español | [🇮🇹 Italiano](README.it.md) | [🇳🇱 Nederlands](README.nl.md)

**Last updated:** 2026-08-23 09:01:23 UTC

[![Sitio oficial](https://img.shields.io/badge/sitio%20oficial-pylon--monitor.com-D8571C)](https://pylon-monitor.com) [![Licencia docs](https://img.shields.io/badge/licencia%20docs-CC--BY--4.0-blue)](LICENSE) [![Idiomas](https://img.shields.io/badge/idiomas-6-green)](#idiomas-disponibles)

> **Pylon-Monitor** es un pequeño dispositivo autónomo para la **monitorización de baterías Pylontech**: un aparato WiFi plug & play que lee el puerto Console (RS-232) de una batería de litio Pylontech y convierte cada valor —Estado de Carga, Estado de Salud, voltaje, corriente, potencia, voltajes por celda, temperaturas y alarmas— en una **API REST JSON** clara, un panel web en directo y una pantalla TFT integrada. Es la forma más rápida de hacer **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics** y **monitorización de Pylontech inalámbrica / a distancia** —con integración nativa con **Home Assistant**, **MQTT**, **Jeedom**, **Node-RED**, **Domoticz** y **openHAB**, configurable en menos de 2 minutos.

Este repositorio es el centro de documentación pública, referencia de integración y recursos comunitarios del dispositivo **[Pylon-Monitor](https://pylon-monitor.com)**. **No** es el firmware ni el diseño de hardware del dispositivo — vea [Qué contiene (y qué no) este repositorio](#qué-contiene-y-qué-no-este-repositorio) más abajo.

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/product/pylon-monitor-pylontech-battery-monitor.jpg" alt="Dispositivo Pylon-Monitor conectado al puerto Console de una batería Pylontech" width="600">
</p>

---

## Índice

- [¿Qué es Pylon-Monitor?](#qué-es-pylon-monitor)
- [Por qué Pylon-Monitor — la monitorización Pylontech simplificada](#por-qué-pylon-monitor--la-monitorización-pylontech-simplificada)
- [Características clave](#características-clave)
- [Baterías Pylontech compatibles](#baterías-pylontech-compatibles)
- [Bajo el capó — diseñado para las variaciones reales de firmware Pylontech](#bajo-el-capó--diseñado-para-las-variaciones-reales-de-firmware-pylontech)
- [Inicio rápido — plug & play en menos de 2 minutos](#inicio-rápido--plug--play-en-menos-de-2-minutos)
- [API JSON — recuperar los datos de sus baterías Pylontech](#api-json--recuperar-los-datos-de-sus-baterías-pylontech)
- [Integración con Home Assistant (auto-descubrimiento MQTT y REST)](#integración-con-home-assistant-auto-descubrimiento-mqtt-y-rest)
- [Integración con Jeedom](#integración-con-jeedom)
- [Integración con Node-RED](#integración-con-node-red)
- [Domoticz, openHAB y cualquier plataforma HTTP/JSON](#domoticz-openhab-y-cualquier-plataforma-httpjson)
- [Privacidad y seguridad — 100 % local, sin nube](#privacidad-y-seguridad--100--local-sin-nube)
- [Actualizaciones de firmware](#actualizaciones-de-firmware)
- [Preguntas frecuentes](#preguntas-frecuentes)
- [Qué contiene (y qué no) este repositorio](#qué-contiene-y-qué-no-este-repositorio)
- [Idiomas disponibles](#idiomas-disponibles)
- [Enlaces oficiales](#enlaces-oficiales)
- [Licencia](#licencia)

---

## ¿Qué es Pylon-Monitor?

**Pylon-Monitor** es una herramienta dedicada de **monitorización y diagnóstico Pylontech** —no un gadget IoT genérico, no un sistema de gestión de baterías, y no afiliado ni respaldado por Pylontech. Se conecta al **puerto Console (RS-232) de baja tensión** de una batería Pylontech, lee en tiempo real la telemetría interna de la batería, y la expone de tres formas a la vez:

1. Una **API REST JSON** (`GET /api.json`) — una sola llamada HTTP, todo el estado de la batería, lista para cualquier script, panel o plataforma domótica.
2. Un **panel web en directo**, accesible desde cualquier navegador de la red local — sin ninguna app que instalar.
3. Una **pantalla TFT de 1,8" integrada** en el propio dispositivo, para una lectura de un vistazo sin siquiera abrir un portátil.

Si buscaba **Pylontech Monitor**, **Pylontech Monitoring**, **Pylontech Diagnostics**, **cómo monitorizar una batería Pylontech a distancia**, **Pylontech Home Assistant**, **Pylontech MQTT**, **Pylontech Jeedom**, **recuperar las informaciones de las baterías Pylontech**, **seguimiento SOC SOH Pylontech**, o **monitorización de Pylontech inalámbrica / a distancia**, esto es exactamente lo que hace Pylon-Monitor.

## Por qué Pylon-Monitor — la monitorización Pylontech simplificada

La mayoría de las formas de leer el estado interno de una batería Pylontech requieren un portátil conectado al puerto Console con el software del fabricante (PYLON Console / BatteryView) en marcha cada vez que se quiere consultar un dato. **Pylon-Monitor convierte eso en un servicio permanente, remoto e inalámbrico**:

- **Plug & play en menos de 2 minutos.** Conecte el cable Console, alimente el dispositivo, únase a su portal WiFi de configuración (`PylonMonitor-Setup`), elija su red WiFi doméstica. Listo. Sin app, sin cuenta, sin línea de comandos, sin soldadura.
- **Monitorización Pylontech remota y permanente.** Una vez configurado, el SOC, SOH, voltaje, corriente, potencia, temperatura y estado de alarma de la batería están disponibles desde cualquier lugar de su red local (o remotamente, a través de su propia VPN / proxy inverso — el dispositivo en sí no depende de ninguna nube, vea [Privacidad y seguridad](#privacidad-y-seguridad--100--local-sin-nube)).
- **Diseñado para la integración, no solo para mirar una pantalla.** La API JSON y el soporte nativo de Home Assistant / MQTT hacen que los datos fluyan directamente a su solución domótica, de monitorización energética o de registro existente — Home Assistant, Jeedom, Node-RED, Domoticz, openHAB, Grafana, una tarea cron, un script de shell, cualquier cosa capaz de hacer un HTTP GET.
- **Hasta 16 baterías, modelos mezclados gestionados correctamente.** Los sistemas Pylontech encadenados — hasta 16 baterías, p. ej. 16&times; US5000 (&asymp;76,8 kWh) o una mezcla como US2000 + US3000 + US5000 — se detectan y reportan individualmente, con el SOC combinado ponderado por capacidad entre modelos en lugar de una media simple, siempre que el cable RJ45 esté conectado al puerto Console de la unidad maestra. El detalle de voltaje por celda está limitado a 64 lecturas (las primeras ~4 baterías); cada batería conserva igualmente todas sus lecturas de SOC/voltaje/corriente/potencia/SOH/ciclos.

## Características clave

| Característica | Descripción |
|---|---|
| **API REST JSON** | `GET /api.json` devuelve SOC, SOH, voltaje, corriente, potencia, estado, voltajes por celda, detalle por batería, temperaturas, estado WiFi/MQTT y más en JSON estructurado — sin autenticación necesaria en la red local, listo para Home Assistant, Node-RED, Jeedom, Domoticz, openHAB o sus propios scripts. |
| **Home Assistant, auto-descubrimiento MQTT** | Introduzca la IP y las credenciales de su broker MQTT y aparecen automáticamente 10 sensores — SOC, SOH, voltaje, corriente, potencia, temperatura de batería y MOSFET, ciclos, estado y desequilibrio de celdas — agrupados bajo una única tarjeta de dispositivo, más una señal de disponibilidad en línea/fuera de línea. **Cero YAML.** |
| **Panel web** | Las tarjetas en vivo se actualizan cada pocos segundos sin recargar nunca la página: Carga (SOC, voltaje, corriente, potencia, estado), Salud (SOH, ciclos, desequilibrio de celdas, contadores de carga/descarga), Temperaturas (base y MOSFET), Sistema (IP, señal WiFi, estado MQTT, tiempo de actividad), Celdas e historial de carga de 24 h. |
| **Pantalla TFT integrada, autorreparable** | Una pantalla IPS de 1,8" muestra el Estado de Carga en cifras enormes, con voltaje/corriente al lado y SOH/ciclos/temperatura debajo — totalmente personalizable, y se reinicializa automáticamente para que un fallo de alimentación nunca la deje bloqueada. |
| **Alarmas configurables (notificaciones push)** | Defina sus propios umbrales de SOC y temperatura, con histéresis para que una sola lectura errática no genere spam, y reciba una notificación push vía Pushover en cuanto se cruce cualquiera de los dos. |
| **Soporte multi-batería — hasta 16 baterías** | Hasta 16 baterías encadenadas — p. ej. 16&times; US5000 (&asymp;76,8 kWh combinados) o una mezcla de modelos como US2000 + US3000 + US5000 — detectadas y mostradas individualmente (SOC, voltaje, corriente, potencia, estado, SOH, ciclos, temperaturas), con el SOC combinado ponderado por capacidad entre modelos. Un selector alterna entre "todas las baterías combinadas" y cada batería por separado. Conectar solo al puerto Console de la unidad maestra. Detalle de voltaje por celda limitado a 64 lecturas (~primeras 4 baterías). |
| **Personalización de la pantalla** | Elija exactamente qué elementos muestra la pantalla TFT física, con una vista previa en vivo antes de guardar. |
| **Dos niveles de reinicio** | Una doble pulsación del botón de reinicio reabre solo la configuración WiFi (nada más se toca); el reinicio de fábrica desde el panel borra todo (WiFi, MQTT, alarmas, inicio de sesión). |

Lista completa e ilustrada: **[pylon-monitor.com/es/features](https://pylon-monitor.com/es/features)**

<p align="center">
  <img src="https://pylon-monitor.com/assets/img/screenshots/dashboard-pylontech-monitor.png" alt="Panel web en directo de Pylon-Monitor mostrando carga, salud, temperaturas, celdas e historial de 24h de la batería Pylontech" width="480">
  <br><sub>El panel web en directo — sin pantalla de inicio de sesión por defecto, se actualiza cada pocos segundos.</sub>
</p>

## Baterías Pylontech compatibles

Pylon-Monitor funciona con cualquier **batería Pylontech que tenga un puerto Console/RS-232 de baja tensión**:

- Pylontech US5000 / US5000C (también vendida como US5000-1C)
- Pylontech US3000C
- Pylontech US3000
- Pylontech US2000C
- Pylontech US2000B+
- Pylontech UP2500
- Familia Pylontech Force-L1

**No compatible** con sistemas Pylontech de alta tensión (Force-H, H48050) ni con otras marcas de baterías (BYD, Dyness, Seplos, etc.) — el protocolo y el conector son específicos de Pylontech.

**Hasta 16 baterías, modelos mezclados incluidos.** Un solo Pylon-Monitor admite hasta 16 baterías encadenadas en total — por ejemplo 16&times; US5000 (&asymp;76,8 kWh combinados), 16&times; US2000 (&asymp;38,4 kWh), o cualquier mezcla como 2&times; US2000 + 2&times; US3000 + 1&times; US5000 en la misma cadena. Cada batería física se consulta y reporta individualmente; el SOC combinado se pondera por la capacidad propia de cada unidad (leída en vivo de la batería, nunca fija por modelo), de modo que un pack de capacidades mezcladas da un número combinado fiel en lugar de una media ingenua entre unidades — vea [Bajo el capó](#bajo-el-capó--diseñado-para-las-variaciones-reales-de-firmware-pylontech) más abajo.

## Bajo el capó — diseñado para las variaciones reales de firmware Pylontech

La salida de la consola del BMS de Pylontech no es perfectamente estable entre versiones de firmware y modelos — el diseño exacto de columnas de las respuestas de consola `pwr`/`bat` puede cambiar con una actualización del firmware del BMS, incluso en el *mismo* modelo de batería. Esto no es hipotético: se ha observado en el mismo modelo US5000 sobre el que se desarrolla este proyecto, donde un firmware de BMS más reciente inserta cuatro columnas de diagnóstico adicionales antes de los campos de estado de carga y Coulomb (SOC).

Un monitor que asuma una posición de columna fija para "SOC" o "cargando/descargando" reportaría, en ese firmware, un número completamente erróneo — sin error, sin aviso, simplemente un SOC incorrecto. El firmware de Pylon-Monitor en cambio analiza la línea de cabecera real que la batería envía en cada consulta y localiza cada valor **por su nombre**, adaptándose automáticamente al diseño que use el firmware del BMS de esa unidad concreta. Verificado tanto contra el formato de respuesta exacto usado en desarrollo como contra una respuesta con un diseño distinto reportada desde el campo.

Dos detalles de fiabilidad más, útiles si desarrolla contra este dispositivo:

- **SOC combinado ponderado por capacidad.** En un pack que mezcla modelos/capacidades de batería (p. ej. US2000 + US3000 + US5000), el porcentaje de carga combinado se pondera según la capacidad nominal propia de cada unidad — leída en vivo de la respuesta `info` de la batería, nunca fija por modelo — en lugar de una media simple, que subrepresentaría a las unidades más grandes.
- **Diagnóstico en flujo, no en búfer.** La vista de diagnóstico `/raw` (respuestas de consola exactas, sin procesar) se transmite al navegador poco a poco en lugar de montarse antes en RAM. En un ESP8266 (&asymp;80 KB de RAM total), construir una página de varios kilobytes en un único búfer antes de enviarla es un riesgo real de fallo bajo presión de memoria, sobre todo a medida que crece el número de baterías encadenadas. Transmitir mantiene constante la huella de memoria de esa página, sin importar la longitud de la cadena.

Nada de esto afecta solo a la precisión de `/api.json` en un banco de pruebas pequeño — es precisamente lo que permite que el mismo firmware funcione correctamente tanto con 1 batería como con una cadena completa de 16 unidades, y sea o no el mismo modelo en cada una.

## Inicio rápido — plug & play en menos de 2 minutos

Pylon-Monitor está diseñado para que **cualquiera pueda configurarlo en menos de dos minutos**, sin app, sin cuenta y sin línea de comandos:

1. **Conecte** el cable Console incluido entre el Pylon-Monitor y el puerto Console (RS-232) de su batería Pylontech.
2. **Alimente** el dispositivo — la pantalla TFT se enciende y el dispositivo arranca en modo de configuración WiFi.
3. **Únase** a la red WiFi temporal que difunde (`PylonMonitor-Setup`) desde su teléfono u ordenador.
4. **Elija** su red WiFi doméstica e introduzca su contraseña en el portal cautivo que se abre automáticamente.
5. **Listo.** El dispositivo se reinicia en su red, la pantalla TFT muestra su nueva dirección IP, y el panel está disponible en `http://<ip-del-dispositivo>` o `http://pylon-monitor.local`.

No se necesita flasheo de firmware, ni controladores, ni ninguna app de terceros para este paso. Guía condensada: **[pylon-monitor.com/es/quickstart](https://pylon-monitor.com/es/quickstart)** — guía completa paso a paso y solución de problemas: **[pylon-monitor.com/es/installation](https://pylon-monitor.com/es/installation)**.

## API JSON — recuperar los datos de sus baterías Pylontech

El núcleo de toda integración es un único endpoint:

```
GET http://<ip-del-dispositivo>/api.json
```

- No requiere autenticación en la red local — diseñado para ser consultado por plataformas domóticas y scripts.
- Sin ida y vuelta a la nube — la respuesta viene directamente del dispositivo, que la leyó directamente del puerto Console de la batería.
- Devuelve el estado completo de la batería como JSON estructurado: resumen de carga, salud, voltajes por celda, detalle por batería (para sistemas encadenados), temperaturas, señal WiFi, estado de conexión MQTT y más.

Extracto ilustrativo (vea [`examples/api-response-example.json`](examples/api-response-example.json)):

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

Cualquier herramienta capaz de hacer un HTTP GET y analizar JSON puede usarlo — una tarea cron con `curl` + `jq`, un script Python/Node, Grafana mediante la fuente de datos JSON API, o cualquier plataforma domótica. Vea la respuesta completa y todos los campos en el propio panel del dispositivo, o las capturas de pantalla anotadas en **[pylon-monitor.com/es/tour](https://pylon-monitor.com/es/tour)**.

## Integración con Home Assistant (auto-descubrimiento MQTT y REST)

Pylon-Monitor está construido para la **integración Home Assistant Pylontech** de fábrica — ambos métodos están integrados en el propio firmware: **sin HACS, sin componente personalizado, sin complemento que instalar en el lado de Home Assistant.**

### Opción 1 — Auto-descubrimiento MQTT (recomendado)

Si ya utiliza el complemento *Mosquitto / MQTT broker* en Home Assistant: introduzca su IP, puerto, usuario y contraseña en la página Settings del dispositivo. El dispositivo publica entonces configuraciones de descubrimiento estándar de Home Assistant, y **10 sensores aparecen automáticamente** en **Ajustes → Dispositivos y servicios → MQTT**, agrupados bajo una única tarjeta de dispositivo llamada *Pylon-Monitor*:

| Sensor | Topic de descubrimiento |
|---|---|
| SOC de la batería | `homeassistant/sensor/pylon-monitor/soc/config` |
| SOH de la batería | `homeassistant/sensor/pylon-monitor/soh/config` |
| Voltaje de la batería | `homeassistant/sensor/pylon-monitor/voltage/config` |
| Corriente de la batería | `homeassistant/sensor/pylon-monitor/current/config` |
| Potencia de la batería | `homeassistant/sensor/pylon-monitor/power/config` |
| Temperatura de la batería | `homeassistant/sensor/pylon-monitor/temp/config` |
| Temperatura MOSFET | `homeassistant/sensor/pylon-monitor/mostemp/config` |
| Ciclos de carga | `homeassistant/sensor/pylon-monitor/cycles/config` |
| Estado de la batería | `homeassistant/sensor/pylon-monitor/state/config` |
| Desequilibrio de celdas | `homeassistant/sensor/pylon-monitor/celldelta/config` |

Los diez sensores comparten un único topic de estado (`pylon-monitor/state`, con prefijo del nombre de host), y el dispositivo publica un topic de **disponibilidad** retenido (`pylon-monitor/status` → `online` / `offline`) con un auténtico Last-Will-and-Testament, para que cada sensor se atenúe correctamente en Home Assistant si el dispositivo pierde alimentación o WiFi, en lugar de quedarse congelado silenciosamente en su último valor.

### Opción 2 — REST (sin broker MQTT)

La plataforma `rest` integrada de Home Assistant consulta `/api.json` directamente cada 30 segundos y crea 6 sensores. El YAML se genera para usted (con la IP actual de su dispositivo ya rellenada) en la página Settings del dispositivo — vea [`examples/home-assistant-rest-sensor.yaml`](examples/home-assistant-rest-sensor.yaml) para la forma genérica.

<img src="assets/home-assistant-configuration.yaml-pylontech-monitor.png" alt="Editor configuration.yaml de Home Assistant mostrando el bloque de sensores REST de Pylon-Monitor pegado" width="420"><br>
*Pegado tal cual en `configuration.yaml` — el bloque exacto de la página Settings, sin modificar nada.*

<img src="assets/home-assistant-pylontech-monitor.png" alt="Configuración de una tarjeta Gauge de Home Assistant con la entidad Pylontech SOC seleccionada, mostrando un 50% en vivo" width="520"><br>
*Uno de los sensores resultantes (Pylontech SOC) añadido a una tarjeta Gauge — en vivo al 50% aquí.*

> No mezcle la opción 1 y la opción 2 para el mismo sensor — obtendrá entidades duplicadas. MQTT ya cubre todo lo que hace REST, y más (10 sensores frente a 6), así que rara vez hay motivo para usar ambos.

Guía completa con capturas de pantalla: **[pylon-monitor.com/es/home-assistant](https://pylon-monitor.com/es/home-assistant)**

## Integración con Jeedom

**Monitorización Pylontech Jeedom** en tres pasos:

1. Instale el plugin **JSON** desde la tienda de plugins de Jeedom.
2. Apunte un equipo a `http://<ip-del-dispositivo>/api.json`.
3. Asocie rutas JSON a comandos de Jeedom — p. ej. `summary>soc`, `summary>voltage`, `summary>state`, `net>rssi`.

Vea [`examples/jeedom-json-plugin.md`](examples/jeedom-json-plugin.md) para un ejemplo detallado.

## Integración con Node-RED

Use un nodo **http request** — método `GET`, URL `http://<ip-del-dispositivo>/api.json`, tipo de retorno *a parsed JSON object* — y luego lea `msg.payload.summary.soc` (o cualquier otro campo) más adelante en el flujo. Si MQTT está configurado en el dispositivo, también puede suscribirse directamente a `pylon-monitor/state` con un nodo MQTT-in — sin necesidad de sondeo. Vea [`examples/node-red-http-request.md`](examples/node-red-http-request.md).

## Domoticz, openHAB y cualquier plataforma HTTP/JSON

Dado que los datos son JSON simple y sin autenticar sobre HTTP local, **cualquier plataforma capaz de consultar una URL y analizar JSON puede integrar Pylon-Monitor** — los sensores Dummy/Virtual de Domoticz con un script, el binding HTTP de openHAB, un panel de Grafana con fuente de datos JSON, un script Python con `requests`, una línea de shell con `curl | jq`, etc. Ningún SDK propietario que instalar, ninguna clave API que solicitar.

## Privacidad y seguridad — 100 % local, sin nube

- **Sin servicio en la nube.** El dispositivo no "llama a casa", no requiere ninguna cuenta, y funciona completamente sin conexión en su red local.
- **Sin telemetría, sin suscripción.** Compra única; el dispositivo no reporta datos de uso a ningún sitio.
- **El puerto Console es de solo lectura.** Pylon-Monitor solo *lee* la telemetría de la batería — nunca envía comandos de control o de carga, por lo que no afecta a la garantía del fabricante Pylontech y no puede alterar el comportamiento de la batería. Es una herramienta de monitorización y diagnóstico, no un sistema de gestión de baterías (BMS) ni un regulador de carga.
- **Inicio de sesión del panel opcional.** El panel web no tiene pantalla de inicio de sesión por defecto (cómodo en una LAN doméstica de confianza); se puede activar una contraseña en Settings para redes compartidas o menos fiables.
- **OTA de firmware local.** Las actualizaciones se aplican desde el propio panel del dispositivo, no se envían silenciosamente desde una nube del fabricante.

## Actualizaciones de firmware

Pylon-Monitor recibe **actualizaciones de firmware gratuitas de por vida**: descargue el `.bin` e instálelo desde el propio panel web del dispositivo — sin cables, sin herramientas de reflasheo. Changelog e instrucciones: **[pylon-monitor.com/es/firmware](https://pylon-monitor.com/es/firmware)**.

**Última versión: v2.2** — una revisión de fiabilidad multi-firmware/multi-modelo. El análisis de respuestas de consola ahora localiza los valores por nombre de columna en lugar de una posición fija (vea [Bajo el capó](#bajo-el-capó--diseñado-para-las-variaciones-reales-de-firmware-pylontech) arriba), el SOC combinado en packs de modelos mezclados ahora está ponderado por capacidad, y la página de diagnóstico `/raw` ahora es segura en memoria en cadenas de baterías grandes. Changelog completo: **[pylon-monitor.com/es/firmware#changelog](https://pylon-monitor.com/es/firmware#changelog)**.

## Preguntas frecuentes

**¿Pylon-Monitor está fabricado o respaldado por Pylontech?**
No. Pylon-Monitor es un accesorio de monitorización independiente, de terceros. "Pylontech" se refiere al fabricante de baterías; Pylon-Monitor no está afiliado a este.

**¿Anula mi garantía Pylontech?**
No — el puerto Console se usa estrictamente en modo lectura para la monitorización, por lo que no afecta a la garantía del fabricante de la batería.

**¿Puede controlar o cargar mi batería?**
No. Pylon-Monitor es únicamente una herramienta de **monitorización y diagnóstico**. Nunca envía comandos de control o de carga — considérelo un medidor de solo lectura muy completo, no un BMS.

**¿Necesita la nube o una app?**
No. La configuración, el panel y la API son 100 % locales. Sin cuenta, sin app, sin suscripción.

**¿Qué idiomas admite el sitio oficial?**
Inglés, francés, alemán, neerlandés, español e italiano — vea [Idiomas disponibles](#idiomas-disponibles).

Más preguntas respondidas en **[pylon-monitor.com/es/faq](https://pylon-monitor.com/es/faq)**.

## Qué contiene (y qué no) este repositorio

Este repositorio es el **centro público de documentación, SEO/descubrimiento y referencia de integración** del dispositivo Pylon-Monitor — resúmenes de instalación, notas de integración JSON/MQTT/Home Assistant/Jeedom/Node-RED, y enlaces al sitio oficial.

**Deliberadamente no incluye** el código fuente del firmware del dispositivo, el diseño interno de la placa/microcontrolador, esquemas, ni ningún otro detalle propietario de hardware/firmware. Si busca eso, no está publicado ni aquí ni en ningún otro sitio — solo se cubren las interfaces públicas documentadas y estables (`/api.json`, topics MQTT, panel web), que es todo lo que una integración necesita.

## Idiomas disponibles

El [sitio oficial](https://pylon-monitor.com) y este repositorio están completamente disponibles en:

| Idioma | Sitio | README del repositorio |
|---|---|---|
| 🇬🇧 English | [pylon-monitor.com](https://pylon-monitor.com) | [README.md](README.md) |
| 🇫🇷 Français | [pylon-monitor.com/fr](https://pylon-monitor.com/fr) | [README.fr.md](README.fr.md) |
| 🇩🇪 Deutsch | [pylon-monitor.com/de](https://pylon-monitor.com/de) | [README.de.md](README.de.md) |
| 🇪🇸 Español | [pylon-monitor.com/es](https://pylon-monitor.com/es) | [README.es.md](README.es.md) |
| 🇮🇹 Italiano | [pylon-monitor.com/it](https://pylon-monitor.com/it) | [README.it.md](README.it.md) |
| 🇳🇱 Nederlands | [pylon-monitor.com/nl](https://pylon-monitor.com/nl) | [README.nl.md](README.nl.md) |

## Enlaces oficiales

- [Página de inicio](https://pylon-monitor.com/es) — descripción del producto, precio, compra
- [Características](https://pylon-monitor.com/es/features) — lista completa de funciones
- [Recorrido visual](https://pylon-monitor.com/es/tour) — capturas de pantalla reales de cada pantalla, incluida la respuesta de la API JSON
- [Inicio rápido](https://pylon-monitor.com/es/quickstart) — guía condensada de 5 pasos
- [Guía de instalación](https://pylon-monitor.com/es/installation) — configuración completa y solución de problemas
- [Integración con Home Assistant](https://pylon-monitor.com/es/home-assistant) — configuración detallada MQTT/REST, referencia de topics, ejemplos de payloads
- [Firmware](https://pylon-monitor.com/es/firmware) — changelog e instrucciones de actualización
- [FAQ](https://pylon-monitor.com/es/faq)
- [Contacto](https://pylon-monitor.com/es/contact)

## Licencia

Los textos y ejemplos de este repositorio se publican bajo [CC BY 4.0](LICENSE) — reutilización, adaptación y difusión libres con atribución. "Pylon-Monitor" y "Pylontech" son marcas de sus respectivos propietarios; este repositorio es un recurso de documentación independiente y no está afiliado a Pylontech.
