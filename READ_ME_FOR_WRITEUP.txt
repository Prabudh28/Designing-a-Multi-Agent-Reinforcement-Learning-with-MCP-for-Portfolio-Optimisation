
Design notes:

- Data: Bloomberg EDU, 5-min OHLCV, Jan-2024 to Jun-2025, assets per provided sheets.
- Split: Train < 2025-01-01, Test = 2025-01-01..2025-06-30.
- Constraints: per-asset cap = 0.30; Σw ≤ 1 with cash.
- Costs: main 5.0 bps (sens 3.0 bps). Bootstrap block=78 bars (~1 day).
- Baselines: EW (static), MinVar (static from train cov), InvVol (monthly rebalanced, targets from train vol). All capped at rebalance targets; weights drift between rebalances.
- RL: PPO with GAE; Actor (256,128), Critic (256,256,128), clip=0.2, entropy=0.01, minibatch=1024, 10 epochs/update.
- CTDE MARL: central critic over joint obs; per-asset actors.
- MCP: binary context alerts with TTL≈30 min — Turnover Alert=1 if prior-hour turnover>50%; Drawdown Alert=1 if running drawdown>5%.
- Trading frictions mitigation: HOLD_N=3 (15 min), action smoothing α=0.2, turnover penalty λ=0.5.
- Diagnostics saved: equity, drawdown, exposure heatmaps, MARL exposure-corr, turnover, training curves; summary metrics; Table 4.1 with CumReturn/AnnVol/Sharpe/Sortino/MaxDD/PSR/DSR/bootstrap-p/Turnover/CumulativeCost.
