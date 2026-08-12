# RSIC Kiosk Fleet Status

Live status store for the RSIC Workspace kiosk tablet fleet.

Each tablet periodically writes/updates its own file under `devices/<device-id>.json`.
The dashboard (GitHub Pages, served from this repo) polls those files and renders a
live table of the whole fleet.

Do not edit files under `devices/` manually — each tablet overwrites its own file on
its next check-in.

## Device status JSON shape

```json
{
  "deviceId": "OTSZ2026042002961",
  "model": "TAB17",
  "lastSeenUtc": "2026-08-12T18:30:00Z",
  "currentUrl": "https://portal.saudireliance.com/rsic-workspace/",
  "batteryPercent": 82,
  "wifiSsid": "RSIC OFFICE TOP 5G",
  "appVersionName": "1.0"
}
```

"Online" is inferred by the dashboard, not stored: a device is shown online if
`lastSeenUtc` is within the last ~2 report intervals.
