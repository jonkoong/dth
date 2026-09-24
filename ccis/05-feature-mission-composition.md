# 05 — Feature Landscape: Mission Composition & Tasking

> ❓ *"I have **X assets** and **Y threats**. How can I optimise my resources to strike efficiently, given the constraints of X, Y and the campaign objectives / restrictions?"*

---

## 📥 1. Board intake

| Source | Enters |
|---|---|
| 🪖 Ground unit **strike request** | DYNAMIC |
| 🎖️ Commander **designation** (right-click track → move to board) | DELIBERATE or DYNAMIC, commander's choice |

---

## 🗂️ 2. Targeting Kanban board (Maven-style)

### 🔀 Flow

```
[DELIBERATE] / [DYNAMIC] --> [PENDING PAIRING] --> [PAIRED] --> [PENDING APPROVAL] --> [IN EXECUTION] --> [PENDING BDA] --> [COMPLETE]
                                    |
                                    v
                    AI generates top 3 COAs from available assets
                    Human adjusts the metrics
```

### 📋 Columns

| Column | Meaning | Kill-chain stage (`02`) |
|---|---|---|
| **DELIBERATE** | Pre-planned target (§3) | 1 Target development |
| **DYNAMIC** | Short-term reaction target (§3) | 2–4 Find / Fix / Track |
| **PENDING PAIRING** | Validated; waiting for weapon–target pairing | 5 Target |
| **PAIRED** | Asset(s) matched; tasking generated | 5 Target |
| 🆕 **PENDING APPROVAL** | Waiting for approval (not in Maven) | 5 Target (authorise) |
| **IN EXECUTION** | Tasked and under way | 6 Engage |
| **PENDING BDA** | Struck; waiting for battle damage assessment | 7 Assess |
| **COMPLETE** | Done | — |

### 🃏 Card anatomy (from Maven)

- NATO symbol, **track ID** (e.g. `NY2182`), title (e.g. *SAM Site 0018*, *TEL*, *C2 Node*)
- Titles often name the **detection source**: *Computer Vision Detection*, *AIS Alert*, *Reported Sighting*
- **Last edited** time; ⚠️ warning icon; tags (e.g. *Kinetic layer 2*)
- Board toolbar: Add, Search, Filter, Sort by, Group by, Guidance, Map, Board Hierarchy, View, Share

### 🤖 AI tasking recommendation

| Aspect | Decision |
|---|---|
| **Trigger** | **Automatic** when a card enters PENDING PAIRING |
| **Presentation** | **Top 3 COAs side by side**: assets, time on target, risk, munitions used |
| **Adjustable metrics** | ⏱️ Speed / time on target · 🏘️ Collateral damage risk · 🛡️ Risk to own assets · 💰 Munition cost / scarcity |
| **Adjusting** | **Presets + sliders** (e.g. "Speed first", "Minimise collateral", then fine-tune) |
| **Approver** | **Depends on target type**: pre-set authority rules, e.g. staff approve low-risk targets, commander approves high collateral-damage ones (`02`) |

### 🗺️ Board status on the map

- A track on the board looks different on the map **at a glance**: colour, extra symbology, or both. ⏳ Method TBD.

---

## ⏱️ 3. Mission types

Most open-source C2 systems don't separate these; we support both.

| | ⚡ Short-term reaction | 🗓️ Long-term pre-planned |
|---|---|---|
| **Board column** | DYNAMIC | DELIBERATE |
| **Shape** | **One threat**, joint effects on it | **Strategic strike**, many coordinated parts |
| **Example 1** | Cyber denies the C2 node controlling it → EW denies its sensor → a jet does the kinetic strike | A four-ship of F-16s goes deep, coordinated with Navy strikes, EW and cyber |
| **Example 2** | CAS: a flight of Apaches supports troops on the ground | |

The commander runs the **whole flow end to end**: assets + targets → approved tasking.

---

## 🎛️ 4. Level of control

Both modes, for any mission type:

- 🎯 **Effect-based (preferred):** commander states the **desired effect** and constraints (e.g. *"neutralise SAM site by H-hour, no collateral damage over X"*); system / staff build the joint package; commander **approves**.
- 🧰 **Asset-level:** commander picks assets per target directly.

---

## 🔍 5. Lessons: common gaps in baseline CCIS tasking

### ✅ Worth doing

- **Explainable scoring**: every score shows its inputs (e.g. ETA, munition chosen, sensor modifier).
- **Adjustable weights, exposed in the UI.**
- **Timestamped status log** per mission (cf. timestamped notes, `04` §1).

### ⚠️ Common gaps (where we can differ)

| Gap | Why it matters |
|---|---|
| **1 target ↔ 1 platform** | No joint packages (cyber + EW + kinetic) |
| **No deliberate vs dynamic split** | Every request goes through the same flow |
| **Strike only** | No CAS, EW, cyber or ISR tasking |
| **No ROE / CDE / deconfliction / threat routing** | The constraints the commander's question is about |
| **"Completed" = destroyed** | No BDA step; finishing ≠ achieving the effect |
| **Requestor picks assets** | Asset-level micromanagement, not effect-level intent (§4) |
| **Straight-line ETA** | Ignores routes, threats and airspace |

---

## ❓ 6. Open question

- 🔑 **How does the AI agent recommend COAs, and how does that fit with P1 (`08`)?** Key area; to be worked through in depth.
