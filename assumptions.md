# Monte Carlo Assumptions — Cybercrime & Ransomware / Attribution Impossibility

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $1,000.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 6.22 | Confirmed by N=100,000 draws |
| ΔW median (result) | $6,221.4B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_financial_extraction` | lognormal | $30B | $60B | $120B | $60B/yr deadweight loss from direct financial extraction (Anderson et al. 2013 D |
| `C2_business_downtime` | lognormal | $1,000B | $1,500B | $2,200B | $1,500B/yr business disruption, remediation, recovery costs. Paper §4 C2. |
| `C3_ip_theft` | lognormal | $1,200B | $2,400B | $4,500B | $2,400B/yr IP theft + innovation disincentive multiplier (Commission on Theft of |
| `C4_infrastructure` | lognormal | $500B | $1,000B | $1,800B | $1,000B/yr critical infrastructure risk, national security costs. Paper §4 C4. |
| `C5_consumer_harm` | lognormal | $450B | $900B | $1,600B | $900B/yr consumer + psychological harm: direct fraud ($150-250B), remediation ($ |
| `C6_governance` | lognormal | $80B | $200B | $400B | $200B/yr attribution impossibility, regulatory failure, cross-jurisdictional enf |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.1 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.1) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 6.06 | 20% DC adj = 4.85 | 40% DC adj = 3.64

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $6,221B = 5.9% of world GDP ($106T) ✓
- **β_W range**: 6.22 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
