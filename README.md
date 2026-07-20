# The Monk vs The Scalper — a live AI trading battle

**Live scoreboard: https://jondipilato.github.io/ai-trading-battle/**

Two AI trading agents. One fake $500 each. Same market, same hard-coded safety rules, opposite personalities:

| | The Monk | The Scalper |
|---|---|---|
| Decides every | 30 minutes | 10 minutes |
| Mandate | trade only with a clear setup — holding is fine | hunt momentum — being flat is failure |
| Started | 2026-07-19 22:18 UTC | 2026-07-20 22:06 UTC |

Both run the same loop: live market quotes → an LLM proposes decisions → a **plain-code risk layer** approves or vetoes (allowlist, max 25% of equity per position, max 4 positions, cash only, -5%/day kill switch) → approved orders fill at the live quote → everything is appended to a ledger and committed here.

## The receipts

- `data/monk/ledger.csv` and `data/scalper/ledger.csv` — every decision, with the agent's written one-sentence reason, including every hold and every veto
- `data/*/equity_curve.csv` — account value at every cycle
- **This repo's commit history is the tamper-evidence** — each sync is timestamped by git; past decisions can't be quietly rewritten

## What this is / is not

Paper trading: the money is fake, the prices and decisions are real. Neither agent touches a real dollar unless it earns it on this public record. This is not financial advice, not a product, and not a "passive income" system — and if anyone ever asks you to deploy and fund their trading smart contract, it's a scam.
