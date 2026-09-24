# 04 — Feature Landscape: Drill-Down (click an entity)

---

## 🧷 1. Every entity

| Field | Notes |
|---|---|
| 🕒 **Last status update** | Date and time |
| 📍 **Last known location** | With the date and time it was last updated |
| 🎯 **Track quality** | Uncertainty ellipse, originating sensor(s), track number. No confidence score (P1, `08`). |
| 🗺️ **Position history** | **Mini map** of past positions, marked over time |
| 🔗 **Related entities** | Parent unit, sub-units, co-located items |
| 📎 **Linked intel reports & media** | The evidence behind the symbol |
| 📝 **Timestamped notes** | Anyone can add comments to any item over time |

---

## 🔵 2. Friendly assets

| Field | Notes |
|---|---|
| 🪪 **Identity** | Callsign, unit, parent in the order of battle, commander |
| 🎥 **What it sees** | Its intelligence and video feeds |
| 📦 **Inventory** | What it *should* be carrying, e.g. weapons. Hard to keep accurate: data degrades on its way up the chain of command. |
| 🛢️ **Readiness** (logistics) | Personnel, fuel, ammo, serviceability (green / amber / red) |
| 🎯 **Status** (tasking) | Current task / mission, weapons control status, comms link health, last contact |
| ⏳ **Endurance / time on station** | Air and UAV assets |
| 🛡️ **Highlight coverage** | Show its sensor coverage and WEZ on the map (`03` §3) |

---

## 🔴 3. Hostile / unknown / suspect

| Field | Notes |
|---|---|
| 🧐 **ID basis** | Sensor observations behind the classification (deterministic) |
| 💣 **Type & capabilities** | **Reference data** looked up by type: weapons, max range, altitude, speed. **Staff can edit in the UI.** Max range = default threat-ring radius (`03` §3). |
| 👁️ **Custody** | Which of our sensors hold it now |
| 🎯 **Targeting status** | On the target list? No-strike? Previously engaged, and BDA |

---

## 🏗️ 4. Installations & infrastructure

| Field | Notes |
|---|---|
| 🏭 **Function, owner, operational status** | Working / damaged / destroyed |
| 🚫 **Protected / no-strike status** | See no-strike overlay (`03` §3) |
| 🛰️ **Imagery history** | Before and after comparison. **If able.** |

---

## 📱 5. OSINT items

| Field | Notes |
|---|---|
| 🎞️ **Original media** | Plus the post link and account |
