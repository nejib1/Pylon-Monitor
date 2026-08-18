# Node-RED integration — Pylontech battery monitoring

## Option A — polling the JSON API

1. Drop an **http request** node onto the flow.
2. Method: `GET`
3. URL: `http://<DEVICE-IP>/api.json`
4. Return: *a parsed JSON object*
5. Feed it with an **inject** node on a repeat timer (e.g. every 30s) to poll periodically.
6. Downstream, read fields like:
   - `msg.payload.summary.soc`
   - `msg.payload.summary.voltage`
   - `msg.payload.summary.current`
   - `msg.payload.summary.power`
   - `msg.payload.summary.state`
   - `msg.payload.health.soh`
   - `msg.payload.net.rssi`

Minimal example flow (import via Node-RED's *Import* menu):

```json
[
    {"id":"pm-inject","type":"inject","z":"","name":"every 30s","props":[{"p":"payload"}],"repeat":"30","crontab":"","once":true,"onceDelay":0.1,"topic":"","payload":"","payloadType":"date","x":150,"y":120,"wires":[["pm-http"]]},
    {"id":"pm-http","type":"http request","z":"","name":"GET /api.json","method":"GET","ret":"obj","paytoqs":"ignore","url":"http://<DEVICE-IP>/api.json","tls":"","persist":false,"proxy":"","insecureHTTPParser":false,"authType":"","x":360,"y":120,"wires":[["pm-debug"]]},
    {"id":"pm-debug","type":"debug","z":"","name":"battery state","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","x":580,"y":120,"wires":[]}
]
```

## Option B — subscribing to MQTT (no polling)

If MQTT is configured on the device (see the Home Assistant MQTT auto-discovery section of the
main README), use an **mqtt in** node subscribed to the device's state topic:

```
pylon-monitor/state
```

This pushes updates as they happen instead of polling on a timer, and also lets you subscribe
to the retained availability topic (`pylon-monitor/status`, `online`/`offline`) to detect if the
device goes offline.
