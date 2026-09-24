# 02 — Kill-Chain Stage Map (the lay of the land)

## 🎯 Question being answered

> Across the US kill chain, what **data** has to be ingested at each stage, and what **processing and decisions** happen there?

---

## 🧭 Frame: sense → make sense → act

JADC2 sums up C2 in three verbs:

| JADC2 verb | Our platform |
|---|---|
| **Sense** | Raw signals in |
| **Make sense** | Picture a commander can read |
| **Act** | Compose → authorise → task |

### 🔁 Two loops, one platform

| Loop | Echelon | Tempo | Doctrine | Outputs |
|---|---|---|---|---|
| **Deliberate** | Strategic / operational | Hours to days | Joint planning process (JPP) + joint targeting cycle → joint air tasking cycle | Target lists, ATO (air tasking order), orders |
| **Dynamic** | Operational / tactical | Minutes to seconds | F2T2EA, which runs inside phase 5 of the targeting cycle | Engagements |

> 💡 **Key design point:** the deliberate loop is what makes the dynamic loop fast. It settles **authorities, ROE and target categories in advance**. JADC2 calls for *"pre-determined, pre-approved, event-driven, bundled authorities."* So the strategic user's main job is to **set the conditions under which the tactical loop may run**.

---

## 🗺️ Stage-by-stage map

| # | Stage | 📥 Data ingested | ⚙️ Processing / decisions | 📤 Output |
|---|---|---|---|---|
| 0 | **Guidance & objectives** (JPP: initiation, mission analysis) | Strategic direction, commander's intent, political constraints, ROE, LOAC, intel estimates of adversary centres of gravity, own-force readiness | Turn intent into objectives and effects; set TST (time-sensitive target) criteria and pre-approved authorities; set priorities and risk tolerance | Commander's guidance, objectives and effects list, ROE matrix, TST categories, PIRs (priority intelligence requirements) |
| 1 | **Target development & COA** (JPP: COA dev, wargame, compare, approve) | Intel databases (orders of battle, facilities), geospatial and terrain data, pattern-of-life history, no-strike and restricted lists, own capabilities and basing | Target systems analysis; vetting and validation; generate and wargame COAs; collateral damage estimation (CDE) | Joint integrated prioritised target list, approved COA, collection plan, pre-planned engagement options |
| 2 | **Find** | Wide-area sensors: space EO/SAR/IR, over-the-horizon and ground radar, AWACS/AEW, SIGINT/ELINT, AIS, ADS-B and civil radar, HUMINT/OSINT, cyber indicators | Detect and cue; flag anomalies against the expected picture; correlate against the target list and PIRs; first-pass classification | Detections and cues with confidence levels; nominated possible targets of interest |
| 3 | **Fix** | Cross-cues from Find; narrow-field sensors (UAV full-motion video, high-res SAR, ELINT geolocation); friendly positions | Multi-sensor fusion; combat ID (friend, foe or neutral); retask sensors | Positively identified target at target-quality location, with error ellipse |
| 4 | **Track** | Continuous feeds: radar tracks, FMV, data links (Link 16 style), ESM | Track fusion and custody management; predict movement to weapon arrival; hand over between sensors; watch for triggers | Maintained track, custody plan, predicted windows of vulnerability |
| 5 | **Target** | Available shooters (status, position, weapons, fuel, time on station), weaponeering data, ROE, CDE inputs, airspace and fires coordination measures, priority list | Decide to engage and choose the means: pair weapon to target, check CDE, deconflict, check authority, escalate to the right approver | Recommended engagement options, then an **authorised engagement order** |
| 6 | **Engage** | The order, platform and unit status, comms state, live track updates | Turn the order into unit-specific tasking (ATO change, fire mission, drone plan, EW or cyber tasking); time and synchronise; monitor; abort or retarget | Tasking messages to manned, unmanned and other units; execution status |
| 7 | **Assess** | Post-strike ISR, weapon telemetry, crew reports, SIGINT changes, adversary behaviour | Battle damage assessment (BDA); munitions effectiveness; combat assessment against objectives; re-attack decision | Re-attack recommendation, updated target list, **feedback into stages 0 and 1** |

### 🕸️ Kill web, not kill chain

- Mitchell Institute: the more interconnected the nodes, the **more paths there are to close the chain**.
- 🏗️ Architecture implication: each stage is a **service** that takes any qualifying input and hands off to any qualifying next node, not a fixed pipe from sensor A to shooter B.
- 🇺🇦 Real example: Ukraine's **Delta**, linked with **GIS Arta** and **Kropyva**, works as a federated integration layer across echelons.

---

## 🧱 Cross-cutting layers (every scenario needs these)

| Layer | What it means for us |
|---|---|
| 🗃️ **Data fabric & standards** | One common **track / entity / task schema** that every stage speaks |
| ⚖️ **Authority & ROE engine** | A machine-readable record of *who can approve what, under which conditions*. This turns strategic intent into tactical speed. |
| 🚦 **Deconfliction** | Airspace, fires, EW spectrum and friendly positions, checked at Target **and** again at Engage |
| 📡 **Degraded ops** | Mission-type tasking, so units can execute on intent when the link drops |
| 🤝 **Human-machine teaming** | For each verb (detect, process, decide, communicate, act, assess), decide whether the machine **does**, **recommends** or **stays out** (CSIS, Hudson) |

---

## 🎬 Candidate scenarios (not yet reviewed)

| | Scenario | Hot stages | Loop | Hard part |
|---|---|---|---|---|
| **A** | Drone raid on a base (air defence / C-UAS) | 2–6 | Dynamic, seconds to minutes | Fusing small, low, slow tracks; combat ID; pairing mixed effectors with cost-exchange in mind |
| **B** | Time-sensitive mobile launcher | 1–4 | Dynamic, fed by deliberate | Find and Fix; pattern of life; predicting the next hide site; CDE escalation |
| **C** | All-domain joint effects to take a land objective | 0, 1, 6 | Deliberate | Sequencing and deconflicting cross-domain effects; assessing against the objective. **Best fit for the theatre-commander persona and compose → authorise → task.** |
