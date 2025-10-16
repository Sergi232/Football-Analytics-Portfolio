# 🇳🇴 Regional Leagues – Dynamic Player Flow Analysis  

This project explores **player flexibility** across regional football leagues and its measurable relationship with **match outcomes** and **betting market dynamics**.

---

## 🎯 Objective  
To quantify the influence of players rotating between **first teams** and **reserve squads**, identifying tactical asymmetries, flexibility-driven volatility, and potential inefficiencies in market pricing.

---

## ⚙️ Approach (Public Overview)  

Weekly ingestion from an operator-facing **FIS (Flexibility Index System)** sheet, including key contextual and model variables:

`Fecha`, `Liga`, `Partido`, `Equipo_filial`, `Equipo_rival`, `Club_1r_equipo`,  
`S1_Stake_1r (0–3)`, `S2_Stake_filial (0–3)`, `Alt_flex`, `Mitja_flex`,  
`Kickoff_1r`, `Kickoff_filial`, `Δt_h`, `Dir`, `F_idx`, `g (ventana)`,  
`FIS`, `Semáforo`, `Ángulo`, `Notas`.

### 🔹 Club-level aggregation  
`Club_1r_equipo`, `FLEX_sum`, `FLEX_mean`, `n_players`, `n_bridge_players`.

Proprietary transformations derive the **Player Flexibility Index (PFI)** and related **team risk indicators**, without exposing internal weight structures or calibration thresholds.

Weekly diagnostics and visual outputs are generated to support interpretability, early-signal monitoring, and betting decision-making.

---

## 🧩 Outputs  

| Visualization | Description |
|---------------|-------------|
| `visuals/player_flow_network.png` | Network of player movements between first and reserve squads. |
| `visuals/team_risk_index.png` | Volatility and flexibility risk by team. |
| `visuals/division_heatmap.png` | Regional heatmap of flexibility intensity across divisions. |

---

## 🧠 Tools & Environment  

**Python** (pandas, NumPy, scikit-learn, matplotlib)  
**Google Colab** – pipeline prototyping & model iteration  
**Power BI** – exploratory dashboards & dynamic visual summaries  

---

## 🧮 Model Validation – Norwegian 2025 Sample  

A validation pilot was conducted on **13 Norwegian regional league matches (Sept–Oct 2025)** to benchmark the **Filial Index Score (FIS)** model against actual outcomes.

| Metric | Value | Description |
|--------|--------|-------------|
| Matches evaluated | 13 | Divisions 2–3 (Reserve team context) |
| Correct signals | 8 / 13 (61.5 %) | Alignment with FIS “Fade / Buy” indicators |
| Net profit | **+4.16 units** | Flat staking (1 unit per match) |
| ROI | **+32.0 %** | Profit / Total Stake × 100 |
| Yield | **+32.0 %** | Equivalent to ROI for fixed staking |
| Period | Sept–Oct 2025 | Initial validation window |

> *Even within a limited dataset, the model consistently captured asymmetries caused by first-team integration, suggesting predictive structure rather than randomness.*

---

## 📈 Interpretation & Ongoing Validation  

A preliminary yield of **+32 %** on a small validation sample indicates that the model successfully identifies **market inefficiencies** linked to lineup fluidity and tactical depth differences between first and reserve teams.  

However, the sample remains non-significant for statistical confirmation.  
Continuous tracking and recalibration are therefore essential.

### Next validation phase:
- Adjustment of **flexibility coefficients** (player & club level)  
- Variance analysis vs. **closing lines** and odds movement  
- Cross-validation with **alternative betting angles** (Asian Handicap / Totals)  
- Transition from qualitative FIS triggers → **quantitative PFI weighting**  
- Automated monitoring of **model drift** and recalibration over time  

These steps will determine whether the model’s edge is **structural** (linked to under-modeled squad behavior) or **transitory**, as the market adapts.

---

## 🗒️ Note  

All datasets are **anonymized** or **synthetic reconstructions** based on the structure of the working FIS and flexibility models.  
The public version reflects **methodology and structure**, not proprietary calculations or parameters.

---

**Author:** [Sergi Ferrer Juanola](https://github.com/Sergi232)  
*Sports Data Scientist | Predictive Modeling & Football Analytics*
