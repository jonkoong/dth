# 03 — Feature Landscape: Map Layer

---

## 🗺️ 1. Base maps & imagery

| Feature | Notes |
|---|---|
| Simplified street map | Plain "Google Maps" look |
| Satellite imagery | |
| SAR imagery | Synthetic aperture radar |
| Terrain contours | Top-down |
| Army topographic maps | Military-style topo sheets |
| 3D battlespace view | Click, pan, rotate; **accurate 3D terrain and texture** |

---

## 🎖️ 2. Symbology & entities

**Symbology standard:** NATO (APP-6 / MIL-STD-2525).

| Category | What to show |
|---|---|
| **Identity** | **NATO standard identity set**: pending, unknown, assumed friend, friend, neutral, suspect, hostile |
| **Domains** | Air, land, sea. Space TBD |
| **UAV classes** | Small FPV → medium → high-end, for **both** blue force and OPFOR |
| **Installations** | Marked on the map |
| **Strategic points** | Bridges, ports, enemy C2 nodes |
| **Critical infrastructure** | Civilian communication towers, fuel depots, munition bunkers, general infrastructure |

---

## 🧩 3. Overlays

| Overlay | Notes |
|---|---|
| 🎯 **Threat rings** | Adversary weapon ranges; move with the threat in real time. Default radius = max range from the type's reference data (`04` §3); **commanders or staff can change it in the UI**. |
| 🛡️ **Own WEZ** | Own weapon engagement zones |
| 👁️ **Own sensor coverage & gaps** | Radar footprints, satellite overpass windows |
| 🧭 **Operational graphics** | Boundaries, phase lines, FLOT, FSCL, kill boxes, NFA / RFA / RFL, ROZs, air corridors (§7). **Can be drawn**, and **update automatically as forces move** (e.g. FLOT follows the forward friendly positions). |
| 🗂️ **NAIs / TAIs** | Named and target areas of interest |
| 🚫 **No-strike sites & population density** | Collateral damage and LOAC inputs |
| 🌐 **Boundaries & demarcation** | International and state borders, territorial lines, international airspace, FIRs, maritime sea lanes |
| 🌦️ **Live weather** | Satellite picture, cloud cover, weather radar, winds, temperature (reference: windy.com) |
| 💥 **Strike history** | Where artillery and bombs have hit **own positions** in the **last 1 h** |
| ➖ **Engagement lines** | Dotted line from shooter to target while munitions are in flight |
| 🚨 **Under-fire alert** | Own unit **flashes** when taking fire |
| 📱 **OSINT** | Scraped internet / social media photos and videos, **pinned by location only**. Location from the post (geotag, text, metadata) where available, else from image content; the pin **shows which method**. No AI description of content (P1, `08`). Research: `06`. |

---

## ⏱️ 4. Time

| Feature | Notes |
|---|---|
| Live refresh | Every **~5 s or faster** |
| Movement trails | Past positions **progressively faded** |
| Stale / lost tracks | Greyed out after dropping out of detection, based on **last seen** time |
| Replay | Pause, rewind, **skip to live**; look back **up to ~1 h** |
| Persistent clock | **Local time and UTC**, side by side, clearly labelled |

---

## 🖱️ 5. Interaction

| Feature | Notes |
|---|---|
| Click anything | Every symbol, icon or pin opens its drill-down (`04`) |
| Global search | Hotkey (e.g. **Ctrl+O**) to search for anything |
| Toggleable layers | **Every** layer can be switched on and off |
| Declutter presets | Preset **and customisable** levels, per commander |
| ✏️ Draw & pin | Excalidraw-style, as easy as a pen tablet. **Shared live with everyone.** |
| 🧽 Clear | As easy as drawing |
| 📏 Measure tools | Range and bearing, area, line of sight / viewshed |
| 🔔 Geofence alerts | Entity enters or leaves a drawn area. **Low priority.** |
| 🫧 Clustering by zoom | Level of detail changes with zoom. **Low priority.** |

---

## 🧭 6. Map furniture

- Scale bar
- North arrow
- Cursor coordinate readout: MGRS + lat/long, **toggleable**

---

## 📖 7. Operational graphics glossary

> ⚠️ Unverified except **kill box** (checked against FM 3-09.34, `09`).

| Graphic | Shape | Meaning |
|---|---|---|
| **Boundary** | Line | Separates adjacent units' areas of responsibility. No firing or moving across without coordinating with the owner. |
| **Phase line (PL)** | Line, usually a road or river | Named line to control movement, e.g. "report crossing PL Blue". |
| **FLOT** | Line | Forward line of own troops: where the most forward friendly forces are now. |
| **FSCL** | Line | Fire support coordination line. **Short of it**, fires need coordination with the land commander; **beyond it**, they don't. |
| **Kill box** | 3D area | Joint fires may attack inside it without further coordination. **Blue** = air-to-surface only; **purple** = air-to-surface + surface-to-surface. |
| **No-fire area (NFA)** | Area | No fires, with narrow exceptions (e.g. hospitals, friendly SOF). |
| **Restrictive fire area (RFA)** | Area | Fires only within stated restrictions. |
| **Restrictive fire line (RFL)** | Line | Between converging friendly forces; no firing across without coordination. |
| **ROZ** | 3D airspace | Restricted operations zone, reserved for one activity (e.g. UAV orbit, tanker track). |
| **Air corridor / minimum-risk route** | 3D route | Safe path for friendly aircraft through own air defences. |
