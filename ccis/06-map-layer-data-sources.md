# 06 — Map Layer: Data Sources

## 🎯 Question being answered

> What **sources of information** have to feed the map layer (`03`) for every feature to work?

> ⚠️ Access, cost and licence details are **unverified** (from memory). Check before committing to a source.

> ❓ Open: **area of operations** (decides what real data exists) and **sea domain in or out** (decides whether 🚢 rows are needed).

**Priority:** 🔴 needed for the minimal end-to-end demo · 🟡 important · 🟢 nice to have

**Kind:** 🌐 live feed · 📦 static / periodic import · 🧪 simulated (no public source)

---

## 🗺️ 1. Base maps & imagery (`03` §1)

|    | Need                      | Source                                                                      | Kind | Access                                |
| -- | ------------------------- | --------------------------------------------------------------------------- | ---- | ------------------------------------- |
| 🔴 | Simplified street map     | **OpenStreetMap** tiles (e.g. OpenFreeMap)                            | 📦   | Free                                  |
| 🔴 | Satellite imagery         | **Sentinel-2 cloudless mosaic** (EOX) or **Esri World Imagery** | 📦   | Free / terms of use                   |
| 🟡 | SAR imagery               | **Sentinel-1** (Copernicus); **Umbra / Capella open data**      | 📦   | Free; open data is sample scenes only |
| 🟡 | Terrain contours, 3D view | **Copernicus DEM GLO-30**                                             | 📦   | Free, 30 m                            |
| 🟢 | Army topographic maps     | **OpenTopoMap** (stand-in)                                            | 📦   | Free; real military sheets not public |

---

## 🎖️ 2. Symbology & entities (`03` §2)

|    | Need                                                      | Source                                                                                                 | Kind | Access                               |
| -- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ---- | ------------------------------------ |
| 🔴 | NATO symbol rendering (APP-6 / MIL-STD-2525)              | **milsymbol.js** (library, not data)                                                             | —   | Open source                          |
| 🔴 | Air tracks                                                | **ADS-B Exchange<br />**Have to find online dataset to replicate air tracks                            | 🌐   | Paid API; unfiltered, shows military |
| 🟡 | 🚢 Sea tracks                                             | **aisstream.io**, or one of **MarineTraffic** / **VesselFinder**                     | 🌐   | aisstream free; others paid          |
|    |                                                           |                                                                                                        |      |                                      |
| 🔴 | Blue-force units (all domains, all UAV classes)           | **Scenario generator**                                                                           | 🧪   | —                                   |
| 🔴 | OPFOR units and order of battle                           | **Scenario generator**                                                                           | 🧪   | —                                   |
| 🟡 | UAV tracks (scenario A)                                   | **Scenario generator**                                                                           | 🧪   | —                                   |
| 🔴 | Strategic points: bridges, ports, C2 nodes                | **OpenStreetMap** (Overpass); **NGA World Port Index**; **OurAirports**; C2 nodes 🧪 | 📦   | Free                                 |
| 🔴 | Critical infrastructure: comms towers, fuel depots, power | **OpenStreetMap**, **OpenInfraMap**                                                        | 📦   | Free                                 |
| 🟡 | Undersea cables                                           | **Submarine Cable Map** (TeleGeography)                                                          | 📦   | Free, licence to check               |
| 🔴 | Installations                                             | **OpenStreetMap** (`military=*`); own installations 🧪                                         | 📦   | Free                                 |

---

## 🧩 3. Overlays (`03` §3)

|    | Need                                                                                      | Source                                                                                                                     | Kind    | Access                                             |
| -- | ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------- | -------------------------------------------------- |
| 🔴 | Threat rings (default radius)                                                             | **US Army ODIN Worldwide Equipment Guide**, hand-curated subset                                                      | 📦      | Public; PDF / web, no API                          |
| 🔴 | Own WEZ                                                                                   | **Scenario generator** (own weapon reference data)                                                                   | 🧪      | —                                                 |
| 🟡 | Own sensor coverage                                                                       | **Scenario generator** (ground / air sensors)                                                                        | 🧪      | —                                                 |
| 🟡 | Satellite overpass windows                                                                | **CelesTrak** TLEs + `skyfield`                                                                                    | 📦      | Free                                               |
| 🟡 | !!GPS jamming (sensor / comms gaps)                                                       | **GPSJam**, or derive from ADS-B Exchange                                                                            | 📦      | Free; daily                                        |
| 🔴 | Operational graphics: boundaries, PLs, FSCL, kill boxes, NFA / RFA / RFL, ROZs, corridors | **Drawn by users** + **scenario generator**                                                                    | 🧪      | —                                                 |
| 🟡 | FLOT (real front line)                                                                    | **DeepStateMap** or **ISW** control-of-terrain                                                                 | 🌐      | Ukraine only; unofficial access                    |
| 🟡 | NAIs / TAIs                                                                               | **Drawn by users** + **scenario generator**                                                                    | 🧪      | —                                                 |
| 🔴 | No-strike sites                                                                           | **OpenStreetMap** (hospitals, schools, places of worship); **healthsites.io**; **UNESCO World Heritage** | 📦      | Free                                               |
| 🔴 | Population density                                                                        | **WorldPop** or **GHSL**                                                                                       | 📦      | Free                                               |
| 🟡 | !!International / state borders                                                           | **Natural Earth**                                                                                                    | 📦      | Free                                               |
| 🟡 | !! Territorial waters, EEZs                                                               | **Marine Regions**                                                                                                   | 📦      | Free                                               |
| 🟢 | International airspace, FIRs                                                              | **OpenAIP**; FIRs from **VATSpy** (community, accuracy unverified)                                             | 📦      | Free with key / open                               |
| 🟢 | Maritime sea lanes                                                                        | ❓ No source identified yet                                                                                                | —      | —                                                 |
| 🟡 | !!Live weather: winds, temperature, cloud                                                 | **Open-Meteo**                                                                                                       | 🌐      | Free                                               |
| 🟢 | !!Weather radar                                                                           | **RainViewer** tiles                                                                                                 | 🌐      | Free                                               |
| 🔴 | Strike history (last 1 h, own positions)                                                  | **Scenario generator**; real-world context from **ACLED** (weekly) and **NASA FIRMS** (hours)            | 🧪 / 📦 | ACLED free with registration; FIRMS free with key  |
| 🔴 | Engagement lines (in-flight munitions)                                                    | **Scenario generator** / mission execution (`05`)                                                                  | 🧪      | —                                                 |
| 🟡 | Under-fire alert                                                                          | **Scenario generator**                                                                                               | 🧪      | —                                                 |
| 🟡 | OSINT media pinned by location                                                            | **GeoConfirmed**; raw **Telegram** scraping                                                                    | 📦 / 🌐 | Community data; Telegram has legal / ToS questions |
| 🟢 | Cyber / network indicators                                                                | **Cloudflare Radar**                                                                                                 | 🌐      | Free API; country / network level only             |

---

## ⏱️ 4. Time (`03` §4)

No extra sources. Live refresh, trails, stale tracks and replay come from **storing** the 🌐 feeds and 🧪 scenario above at ≤ 5 s resolution for ≥ 1 h.

---

## 🖼️ 5. Reference dashboards (UI ideas, not data)

- **World Monitor**
- **SENTINEL** — ❓ which one; link needed

---

## 🔵 6. Summary: what we must build ourselves

The 🧪 rows share one source: a **scenario generator** that produces blue force, OPFOR, UAV tracks, own WEZ / sensor coverage, operational graphics, strikes and engagements. Public data only provides the backdrop.
