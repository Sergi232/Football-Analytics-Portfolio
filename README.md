#Regional Leagues – Dynamic Player Flow Analysis

This project analyzes **player flexibility** across regional football leagues and its relationship with match outcomes and betting dynamics.

## Objective
To quantify the influence of players moving between **first teams** and **reserve squads**, identifying tactical patterns, flexibility effects, and potential betting inefficiencies.

## Approach (public view)
- Weekly ingestion from an operator-facing **FIS** sheet including fields:  
  `Fecha, Liga, Partido, Equipo_filial, Equipo_rival, Club_1r_equipo, S1_Stake_1r (0-3), S2_Stake_filial (0-3), Alt_flex, Mitja_flex, Kickoff_1r, Kickoff_filial, Δt_h, Dir, F_idx, g (ventana), FIS, Semaforo, Angulo, Notas`.
- Club-level summary table:  
  `Club_1r_equipo, FLEX_sum, FLEX_mean, n_players, n_bridge_players`.
- Proprietary transformations produce the **Player Flexibility Index (PFI)** and **team risk indicators**, without disclosing internal weights or thresholds.
- Weekly visual diagnostics are created for interpretability and decision support.

## Outputs
- `visuals/player_flow_network.png` — network of player connections between first and reserve squads.  
- `visuals/team_risk_index.png` — team-level volatility and flexibility risk.  
- `visuals/division_heatmap.png` — regional/divisional flexibility intensity.

## Tools
Python (pandas, NumPy, scikit-learn, matplotlib), Google Colab, Power BI.

## Note
All datasets are anonymized and/or synthetic replicas based on the structure of the working FIS and flexibility files.  
The public version reflects **structure and methodology**, not the proprietary calculations.

## Model Validation – Norwegian 2025 Sample

A validation sample of 13 Norwegian regional league matches (Sep–Oct 2025) was used to benchmark the Filial Index Score (FIS) model against real betting outcomes.

| Metric | Value | Description |
|---------|-------|-------------|
| Matches evaluated | 13 | Division 2–3 (Reserve team context) |
| Correct signals | 8 / 13 (61.5 %) | Consistent with FIS “Fade/Buy” indicators |
| Net Profit | **+4.16 units** | Flat staking (1u per match) |
| ROI | **+32.0 %** | (Profit / Total Stake) × 100 |
| Yield | **+32.0 %** | Equivalent to ROI for fixed staking |
| Period | Sep–Oct 2025 | Model validation window |

---

### Interpretation and Ongoing Validation

A **+32% yield** over 13 matches indicates that the model consistently captures **market inefficiencies** driven by player flexibility and lineup asymmetries between first and reserve teams.  
Even within a small sample size, this performance suggests **structural predictive power** rather than short-term randomness.

Continuous validation will track the model’s evolution week by week, integrating:
- Adjusted flexibility coefficients (per player and per club)
- Variance analysis between predicted and actual closing lines
- Cross-validation against alternative betting angles (e.g., Asian Handicap vs Over/Under)
- Progressive scaling from qualitative (FIS) to quantitative (PFI-weighted) triggers

This monitoring process will determine whether the current predictive edge remains **statistically significant** or regresses toward market equilibrium, forming the foundation for automated model calibration in subsequent versions.

