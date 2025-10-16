# 🇳🇴 Norwegian Regional Leagues – Dynamic Player Flow Analysis

This project analyzes **player flexibility** across Norway’s regional football leagues and its relationship with match outcomes and betting dynamics.

## 🎯 Objective
To quantify the influence of players moving between **first teams** and **reserve squads**, identifying tactical patterns, flexibility effects, and potential betting inefficiencies.

## ⚙️ Approach (public view)
- Weekly ingestion from an operator-facing **FIS** sheet including fields:  
  `Fecha, Liga, Partido, Equipo_filial, Equipo_rival, Club_1r_equipo, S1_Stake_1r (0-3), S2_Stake_filial (0-3), Alt_flex, Mitja_flex, Kickoff_1r, Kickoff_filial, Δt_h, Dir, F_idx, g (ventana), FIS, Semaforo, Angulo, Notas`.
- Club-level summary table:  
  `Club_1r_equipo, FLEX_sum, FLEX_mean, n_players, n_bridge_players`.
- Proprietary transformations produce the **Player Flexibility Index (PFI)** and **team risk indicators**, without disclosing internal weights or thresholds.
- Weekly visual diagnostics are created for interpretability and decision support.

## 📊 Outputs
- `visuals/player_flow_network.png` — network of player connections between first and reserve squads.  
- `visuals/team_risk_index.png` — team-level volatility and flexibility risk.  
- `visuals/division_heatmap.png` — regional/divisional flexibility intensity.

## 🧠 Tools
Python (pandas, NumPy, scikit-learn, matplotlib), Google Colab, Power BI.

## 🔐 Note
All datasets are anonymized and/or synthetic replicas based on the structure of the working FIS and flexibility files.  
The public version reflects **structure and methodology**, not the proprietary calculations.
