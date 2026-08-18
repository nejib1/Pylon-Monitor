# Jeedom integration — Pylontech battery monitoring via the JSON plugin

Pylon-Monitor needs no custom Jeedom plugin. The standard **JSON** plugin (available in the
Jeedom plugin store) can poll the device's built-in `/api.json` endpoint directly.

## Setup

1. Install the **JSON** plugin from the Jeedom plugin store, if not already installed.
2. Create a new equipment ("équipement") in the JSON plugin.
3. Set its URL to:
   ```
   http://<DEVICE-IP>/api.json
   ```
4. Set the polling interval (30–60 seconds is plenty for battery telemetry; it does not change fast enough to need sub-second polling).
5. Add commands ("commandes") and map each one to a JSON path in the response, for example:

| Jeedom command | JSON path | Type |
|---|---|---|
| SOC | `summary>soc` | numeric (%) |
| Voltage | `summary>voltage` | numeric (V) |
| Current | `summary>current` | numeric (A) |
| Power | `summary>power` | numeric (W) |
| State | `summary>state` | string |
| SOH | `health>soh` | numeric (%) |
| WiFi signal (RSSI) | `net>rssi` | numeric (dBm) |

6. Save and refresh — the commands should populate with live values from your Pylontech battery on the next poll.

No authentication, no API key and no additional network configuration is required as long as
Jeedom and the Pylon-Monitor device are on the same local network.
