# 📘 Data Structure (Aligned with FIS and Club Flex Summary)

This document describes the core dataset structures used in the **Norwegian Player Flow Analysis**.  
It aligns with the working architecture of the **FIS (Flexibility Index System)** and **Club Flex Summary** tables, keeping proprietary components abstracted but maintaining structural transparency.

---

## 🧾 FIS Weekly Sheet (Public Schema)

| Variable | Description |
|-----------|-------------|
| **Fecha** | Match date (YYYY-MM-DD). Used as primary time reference. |
| **Liga** | Competition name or division (e.g., Division 2 – Group 1). |
| **Partido** | Fixture label – concatenation of home and away teams. |
| **Equipo_filial** | Reserve or “B” team involved in the match. |
| **Equipo_rival** | Opponent team name. |
| **Club_1r_equipo** | Related first-team entity linked to the reserve. |
| **S1_Stake_1r (0–3)** | Discretionary stake score for first-team influence (0–3 scale). |
| **S2_Stake_filial (0–3)** | Discretionary stake score for reserve side (0–3 scale). |
| **Alt_flex** | Alternative flexibility signal derived from lineup differentials. |
| **Mitja_flex** | Averaged flexibility signal (multi-match smoothing). |
| **Kickoff_1r** | Scheduled kickoff time of the first-team fixture. |
| **Kickoff_filial** | Scheduled kickoff time of the reserve fixture. |
| **Δt_h** | Time delta (in hours) between first-team and reserve kickoffs. |
| **Dir** | Encoded direction of player flow (`1st→B` or `B→1st`). |
| **F_idx** | Proprietary flexibility index (scaled 0–1). |
| **g (ventana)** | Rolling window parameter controlling aggregation scope. |
| **FIS** | Consolidated flexibility signal (composite score). |
| **Semáforo** | Operational traffic-light system for model gating (`red / amber / green`). |
| **Ángulo** | Category tag for specific model setups (“angles”). |
| **Notas** | Operator comments or qualitative notes for context. |
| **Unnamed: 20–21** | Empty placeholder columns in the working Excel — ignored in the public schema. |

---

## 🏟️ Club-Level Flexibility Summary

| Variable | Description |
|-----------|-------------|
| **Club_1r_equipo** | Unique key representing the first-team club. |
| **FLEX_sum** | Cumulative flexibility load (sum of flexibility instances across the period). |
| **FLEX_mean** | Mean flexibility score per observation or match. |
| **n_players** | Total players observed within the sample window. |
| **n_bridge_players** | Count of players appearing in both first and reserve teams within the same period. |

---

## 🔄 Relationships Between Tables

- **1st-team link** → `Club_1r_equipo` serves as relational key across the FIS sheet, player register, and club summary.
- **Temporal alignment** → `Fecha` and `Δt_h` synchronize events between both squads.
- **Aggregations** → Club-level summaries are derived from match-level records, feeding into higher-order metrics (PFI, team risk).

---

## 🧠 Analytical Use

- **Exploratory** – Identify structural imbalances in squad deployment.  
- **Modeling** – Input features for PFI computation and FIS calibration.  
- **Validation** – Compare expected vs. observed flexibility impact across matches.  

---

> All variable names and ranges are kept identical to the working files to preserve schema integrity.  
> Sensitive scoring methods and weights remain proprietary.

---

**Author:** [Sergi Ferrer Juanola](https://github.com/Sergi232)  
*Sports Data Scientist | Predictive Modeling & Football Analytics*
