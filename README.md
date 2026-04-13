# SAPM Monte Carlo — Cybercrime & Ransomware / Attribution Impossibility

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Cybercrime & Ransomware (Attribution Impossibility).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.22** |
| β_W mean | 6.43 |
| β_W std | 1.58 |
| **90% CI** | **[4.2, 9.3]** |
| 99% CI | [3.6, 11.1] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$6,221.4B/yr** |
| Π (revenue) | $1,000.0B/yr |

**β_W = 6.22** means the cybercrime & ransomware industry destroys **$6.22 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-cybercrime.git
cd sapm-mc-cybercrime
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.22` and `ΔW median : $6,221.4B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_financial_extraction | $59.9B | [$29.9B, $119.7B] | Lognormal |
| C2_business_downtime | $1,499.1B | [$1,021.4B, $2,206.2B] | Lognormal |
| C3_ip_theft | $2,398.5B | [$1,280.5B, $4,496.4B] | Lognormal |
| C4_infrastructure | $1,001.1B | [$554.5B, $1,796.9B] | Lognormal |
| C5_consumer_harm | $897.8B | [$507.2B, $1,593.0B] | Lognormal |
| C6_governance | $199.7B | [$100.1B, $399.9B] | Lognormal |
| **Total ΔW** | **$6,221.4B** | **[$4,227.7B, $9,316.9B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.1 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Cybercrime & Ransomware (Attribution Impossibility)*.
> GitHub: epostnieks/sapm-mc-cybercrime.
> https://github.com/epostnieks/sapm-mc-cybercrime
