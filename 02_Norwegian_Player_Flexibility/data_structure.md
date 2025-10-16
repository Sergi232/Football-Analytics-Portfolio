# Data Structure (Aligned with FIS and Club Flex Summary)

## FIS weekly sheet (public schema)
- `Fecha` — match date (YYYY-MM-DD)
- `Liga` — competition name / division
- `Partido` — fixture label
- `Equipo_filial` — reserve/second team
- `Equipo_rival` — opponent team
- `Club_1r_equipo` — related first team (linked entity)
- `S1_Stake_1r (0-3)` — discretionary stake score for 1st team (0–3)
- `S2_Stake_filial (0-3)` — discretionary stake score for reserve (0–3)
- `Alt_flex` — alternative flexibility signal (derived)
- `Mitja_flex` — averaged flexibility signal (derived)
- `Kickoff_1r` — kickoff time (first team)
- `Kickoff_filial` — kickoff time (reserve team)
- `Δt_h` — hours difference between kickoffs (first vs reserve)
- `Dir` — direction of player flow (1st→B / B→1st) [encoded]
- `F_idx` — proprietary flexibility index (scaled)
- `g (ventana)` — rolling window parameter (aggregations)
- `FIS` — consolidated signal (composite) [proprietary]
- `Semaforo` — operational traffic-light (entry gating)
- `Angulo` — angle/tag for actionable setups
- `Notas` — operator notes / qualifiers

> Columns `Unnamed: 20`, `Unnamed: 21` are blank placeholders in the working file and are ignored in the public schema.

## Club-level flexibility summary
- `Club_1r_equipo` — first team club key
- `FLEX_sum` — total flexibility load (season-to-date/period)
- `FLEX_mean` — average flexibility per observation
- `n_players` — players observed in sample
- `n_bridge_players` — players connecting first team and reserve
