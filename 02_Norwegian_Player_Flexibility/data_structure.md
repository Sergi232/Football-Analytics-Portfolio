# 📘 Data Structure (Aligned with FIS, Player, and Club Flex Summary)

This document provides a transparent schema of the datasets powering the **Norwegian Player Flow Analysis**.  
It covers the **FIS (Flexibility Index System)**, **Club Flex Summary**, and **Player Block data**, keeping proprietary calculations abstracted but preserving structure and analytical intent.

---

## 🧾 FIS Weekly Sheet (Core Match-Level Data)

| Variable | Description |
|-----------|-------------|
| **Fecha** | Match date (YYYY-MM-DD). Used as the temporal key. |
| **Liga** | Competition name or division (e.g. “Norwegian Div. 2 – Avd. 3”). |
| **Partido** | Fixture label: concatenation of home and away clubs. |
| **Equipo_filial** | Reserve or “B” team in the fixture. |
| **Equipo_rival** | Opponent team name. |
| **Clasificación_mejor_equipo** | Relative league position of the stronger side in the pair. |
| **Club_1r_equipo** | First-team club associated with the reserve team. Relational key linking to other tables. |
| **S1_Stake_1r (0–3)** | Internal scoring of first-team match importance (0 = irrelevant; 3 = key). |
| **S2_Stake_filial (0–3)** | Internal scoring of reserve-team match importance. |
| **Alt_flex** | Alternative flexibility measure derived from alignment frequency. |
| **Mitja_flex** | Mean flexibility over recent observation window. |
| **Kickoff_1r** | Kick-off time of the first-team match (24 h format). |
| **Kickoff_filial** | Kick-off time of the reserve match. |
| **Δt_h** | Hour difference between both kick-offs; key for overlap detection. |
| **Dir** | Direction of player flow (encoded: `1st→B`, `B→1st`, or `Both`). |
| **F_idx** | Normalized flexibility index (0–1) — captures magnitude and direction. |
| **g (ventana)** | Rolling-window parameter defining aggregation depth (matches). |
| **FIS** | Composite flexibility signal combining multiple indicators (proprietary weighting). |
| **Semáforo** | Qualitative gating system (“Red”, “Amber”, “Green”) defining model confidence zone. |
| **Ángulo** | Tag describing actionable angle or market condition (e.g. “Fade”, “Buy”, “Neutral”). |
| **Notas** | Operator or analyst notes for contextual observations. |
| **Unnamed: 20–21** | Empty placeholder columns ignored in processing. |

---

## 🏟️ Club-Level Flexibility Summary  

| Variable | Description |
|-----------|-------------|
| **Club_1r_equipo** | Unique identifier of the first-team club. |
| **FLEX_sum** | Total cumulative flexibility load for the observation period. |
| **FLEX_mean** | Average flexibility per match entry. |
| **n_players** | Total players considered within the dataset window. |
| **n_bridge_players** | Count of players featuring in both first and reserve squads (bridge players). |
| **FLEX_ratio** | Proportion of bridge players relative to squad size — proxy of squad elasticity. |
| **Last_update** | Last data refresh timestamp (used in Power BI). |

---

## 👤 Player Block Structure  

| Variable | Description |
|-----------|-------------|
| **Player_ID** | Unique internal identifier. |
| **Player_name** | Player full name (standardized). |
| **Club_current** | Current club association at data time. |
| **Club_origin** | Club of origin (if loaned or transferred). |
| **Appearances_B** | Number of appearances in the reserve squad. |
| **Appearances_1st** | Number of appearances in the first team. |
| **Bridge_flag** | Boolean flag if the player has appeared in both squads. |
| **Flex_score** | Player-level normalized flexibility score. |
| **Minutes_total** | Total minutes accumulated (all competitions). |
| **Last_seen** | Last appearance date. |
| **Season_period** | Data window (e.g. “2025-Q3”). |

---

## 🔗 Relational Structure  

- `Club_1r_equipo` → primary key linking across **FIS**, **Club Summary**, and **Player Blocks**.  
- `Fecha` + `Equipo_filial` → composite key for temporal alignment.  
- Aggregations cascade upward: **Player → Match → Club**.  

---

## 🧠 Analytical Use  

| Layer | Use case |
|-------|-----------|
| **Match-level (FIS)** | Detect intra-week flexibility shocks and predict betting market inefficiencies. |
| **Club-level summary** | Quantify organizational flexibility and risk exposure. |
| **Player-level block** | Measure rotational dynamics and player volatility across squads. |

---

## 🗒️ Notes  

- All values are **anonymized** or **synthetic replicas** mirroring the real model’s architecture.  
- Proprietary coefficients and weights are excluded for confidentiality.  
- The schema aligns fully with the internal FIS pipeline used for predictive modeling, feature engineering, and Power BI visualization.

---

**Author:** [Sergi Ferrer Juanola](https://github.com/Sergi232)  
*Sports Data Scientist | Predictive Modeling & Football Analytics*
232)  
*Sports Data Scientist | Predictive Modeling & Football Analytics*
