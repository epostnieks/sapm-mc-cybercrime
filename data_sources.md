# Data Sources — Cybercrime & Ransomware Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Cybercrime & Ransomware: Attribution Impossibility) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_financial_extraction`

$60B/yr deadweight loss from direct financial extraction (Anderson et al. 2013 DWL fraction 15-25% of gross; excludes wealth transfers). Paper §4 C1: δ_C1=60B [30,90].

*Full citations: paper §4 (available SSRN).*

### `C2_business_downtime`

$1,500B/yr business disruption, remediation, recovery costs. Paper §4 C2.

*Full citations: paper §4 (available SSRN).*

### `C3_ip_theft`

$2,400B/yr IP theft + innovation disincentive multiplier (Commission on Theft of American IP range scaled globally). Paper §4 C3: δ_C3=2,400B [1,000-4,000]. Largest channel.

*Full citations: paper §4 (available SSRN).*

### `C4_infrastructure`

$1,000B/yr critical infrastructure risk, national security costs. Paper §4 C4.

*Full citations: paper §4 (available SSRN).*

### `C5_consumer_harm`

$900B/yr consumer + psychological harm: direct fraud ($150-250B), remediation ($50-100B), QALY-monetized psych harm ($125B), digital participation chilling effect ($100-300B). Paper §4 C5: δ_C5=900B [400-1,500].

*Full citations: paper §4 (available SSRN).*

### `C6_governance`

$200B/yr attribution impossibility, regulatory failure, cross-jurisdictional enforcement costs. Paper §4 C6: δ_C6≈140-260B.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $1,000.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Cybercrime & Ransomware (Attribution Impossibility)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
