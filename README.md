# Designing-a-Multi-Agent-Reinforcement-Learning-with-MCP-for-Portfolio-Optimisation
# Developing a Multi-Agent Reinforcement Learning (MARL) framework employing the Model Context Protocol (MCP) for Dynamic Asset Allocation within Algorithmic Trading Environments” 




This repository accompanies my MSc Fintech with Business Analytics, dissertation:  
**“Multi-Agent Reinforcement Learning with Context Sharing for Portfolio Optimisation”**.  

The project develops and evaluates a **context-aware MARL framework** for intraday portfolio management. It integrates **Centralised Training with Decentralised Execution (CTDE)** and a lightweight **Model Context Protocol (MCP)** for risk-aware coordination. Performance is benchmarked against single-agent PPO and classic portfolio heuristics (Equal-Weight, Inverse-Volatility, Minimum-Variance) under realistic **transaction costs and market frictions**.

---

## 📑 Dissertation Context

- **Research Question 1 (RQ1):** Does MCP-enabled MARL outperform single-agent RL and traditional baselines in risk-adjusted terms?  
- **Research Question 2 (RQ2):** How does MCP affect cooperation, information exchange, and portfolio stability?  
- **Research Question 3 (RQ3):** What challenges arise when applying MARL with MCP to high-frequency data?

**Findings:**  
- Risk-based heuristics (InvVol, MinVar, EW) outperformed RL (+7–8% OOS).  
- MARL-MCP and PPO both ended ≈ –5% after costs.  
- MCP stabilised training and prevented pathological turnover but did not generate alpha.  
- Exposure-correlation ≈ 1.0 across agents → evidence of **policy degeneracy** rather than strategic coordination.

---

## 📊 Key Results

| Strategy          | OOS Return (H1 2025) | Sharpe | Sortino | MaxDD   | Turnover | Notes |
|-------------------|----------------------|--------|---------|---------|----------|-------|
| **InvVol**        | +8%                  | ~0.93  | >1      | 12%     | Low      | Best performer |
| **MinVar**        | +7–8%                | ~0.9   | >1      | 10–11%  | Low      | Smooth growth |
| **Equal-Weight**  | +7%                  | ~1.0   | >1      | 13%     | Low      | Balanced |
| **PPO (Single)**  | –5%                  | –0.3   | –0.4    | 5.6%    | ~0       | Under-exposed (retreat to cash) |
| **MARL (MCP ON)** | –5%                  | –0.1   | –0.2    | 14.5%   | Non-zero | Active but symmetric allocations |

**Statistical inference:** PSR/DSR < 0.9, bootstrap p > 0.1 → no evidence of RL skill (Bailey & López de Prado, 2014).

---

## 🖼️ Figures

Key visualisations (in `/figures/`):  

- `eda_*` → Exploratory Data Analysis (returns, correlations, intraday profiles)  
- `eq_*.png` → Baseline equity curves (EW, InvVol, MinVar)  
- `wgt_*.png` → Baseline weights  
- `marl_*.png` → MARL performance (equity, drawdown, turnover, exposure, correlation)  
- `single_*.png` → Single-agent PPO performance  
- `train_*` → Training return/entropy curves  

---

## ⚙️ Repository Structure

