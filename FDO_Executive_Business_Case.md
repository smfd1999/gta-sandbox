# Fermaca Digital Origins (FDO)
## Executive Business Case — Board & Investment Committee

**Prepared:** March 13, 2026
**Entity:** Fermaca Domes, S.A. de C.V. (RFC: FSC141124IGA)
**Confidential — For Internal Use Only**

---

## 1. Executive Summary

Fermaca Digital Origins (FDO) is a $46.2M USD, 1 MW purpose-built AI data center at Fermaca's Mexico City headquarters — the first NVIDIA B300 GPU deployment in Latin America. The project deploys 576 NVIDIA B300 GPUs across 72 compute nodes, monetized from day one through a strategic distribution agreement with Hydra Host's Brokkr GPU marketplace.

**Why now:** Global GPU compute demand is outpacing supply at an unprecedented rate. Mexico sits at the intersection of this supply gap and a geographic opportunity: direct US fiber connectivity, competitive energy costs ($0.109 USD/kWh), USMCA trade advantages, and near-zero local GPU supply serving a rapidly growing Latin American market. B300 GPUs — the most advanced accelerator available — have only 3 recorded spot contracts globally on the Brokkr marketplace, indicating extreme scarcity.

**The investment case in four numbers:**

| Metric | Value |
|--------|-------|
| Total Project Cost | $46.2M USD |
| Bull Case Annual Revenue (90% util.) | $24.7M USD |
| Breakeven GPU Utilization | 38% |
| Expected Payback | 1.9 — 2.2 years |

FDO also serves as the operational proof-of-concept for Fermaca's longer-term vision: a 250 MW Fermaca Digital City that would position Mexico as a sovereign AI compute hub.

---

## 2. The Market Opportunity

### 2.1 Global GPU Supply-Demand Imbalance

Hyperscalers, AI labs, and enterprise adopters are locked in a race to secure accelerated computing capacity. Infrastructure buildout cannot keep pace — particularly outside the United States. This creates a pricing premium for GPU compute and a window of opportunity for new entrants with the right hardware and distribution channels.

### 2.2 Mexico's Structural Advantages

| Advantage | Detail |
|-----------|--------|
| Geographic proximity | Direct fiber to US markets, <10ms latency to major US data center hubs |
| Energy cost | $0.109 USD/kWh (Iberdrola pass-through IBD tariff) vs $0.08-0.15 in US Tier 1 markets |
| USMCA framework | Favorable trade treatment for cross-border AI services |
| Government alignment | Plan Mexico federal strategy, SEDECO backing, CFE utility partnership |
| Tax efficiency | 88-89% accelerated depreciation on fixed assets, 25% R&D deduction |
| LATAM demand | Near-zero local GPU supply against rapidly growing enterprise AI adoption |

### 2.3 NVIDIA Sovereign AI Enrollment

FDO is enrolled in NVIDIA's AI Nations / Sovereign AI program and is positioned to become a Preferred NVIDIA Cloud Partner (NCP) — the first in Mexico. This provides priority GPU access, reference architecture support, and a powerful market credential.

---

## 3. Project Description

### 3.1 Facility Overview

| Parameter | Specification |
|-----------|---------------|
| Location | Fermaca HQ, Alvaro Obregon, CDMX (19.32°N, 99.22°W) |
| Elevation | 2,395m ASL |
| Seismic Zone | Zone D (high) — structural design compliant |
| Data Center Area | 333 m² (Ground Floor) |
| IT Capacity | 1 MW |
| Tier Level | II (N Electrical / N+1 Mechanical) |
| Target PUE | 1.34 (per EPC design, BCYSA validated) |
| Construction | 27 weeks (ATN Ingenieria, fixed-price EPC) |
| COD Target | Q2 2026 |

### 3.2 Compute Infrastructure

| Component | Specification |
|-----------|---------------|
| GPUs | 576x NVIDIA B300 HGX (latest generation) |
| Nodes | 72x Dell PowerEdge XE9780 (8 GPU/node) |
| Cabinets | 17x DDC S-Series v4 NEMA 3R (14 Type-A @ 5 nodes, 1 Type-B @ 2 nodes, 2 Network) |
| Per-Cabinet Load | 68.7 kW (57.9 kW IT + 10.8 kW HVAC) |
| GPU Fabric | 12x NVIDIA Q3400-X800 InfiniBand NDR (400 Gbps/port, full fat-tree) |
| Ethernet | 8x NVIDIA SN5610 Spectrum-4 (800G) |
| Uplinks | 4x 100Gb QSFP28 via Hydra Edge Routers |

### 3.3 Power Architecture

| Component | Specification |
|-----------|---------------|
| Utility Feed | CFE 23kV Medium Voltage (Oficio 0659/2026 approved) |
| Transformer | 2 MVA Driescher dry-type (23kV → 480V) |
| Generators | 3x 800 kW diesel (N+1 redundancy, 2,400 kW total) |
| UPS | 2x 1,250 kVA Schneider Li-ion (N+1, 10-min runtime) |
| ATS | Generac 2000A, dual redundancy, <10s transfer |
| CFE Connection Cost | $7.69M MXN (~$447K USD) including IVA |

### 3.4 Cooling System

| Component | Specification |
|-----------|---------------|
| Chillers | 2x Schneider XRAC1812A, 134.4 TR each (N+1) |
| Total Capacity | 268.8 TR |
| HVAC Power | 246.6 kW (lowest of all EPC bids) |
| Cooling Type | Chilled water, closed-loop, 14°C supply |
| Water Flow | 36.4 GPM per cabinet (618.8 GPM total) |
| CRAC Units | 4x 3-Ton precision units |
| Noise | 63.7 dB (near-silent for urban HQ location) |

---

## 4. Revenue Model — GPU-as-a-Service

### 4.1 Distribution Strategy

FDO's 576 B300 GPUs are pre-connected to enterprise demand through **Hydra Host's Brokkr marketplace** — a GPU-as-a-Service platform managing 30,000+ GPUs across 50+ data centers globally with >90% historical utilization. This eliminates the cold-start problem: FDO has access to a global buyer pool from day one.

The commission-based model means Fermaca does not need to build sales infrastructure. Hydra Host handles customer acquisition, billing, SLA enforcement, and workload orchestration. Fermaca earns supplier rates on deployed compute hours.

### 4.2 B300 Pricing & Market Position

Based on Hydra Host's contract decay dataset (1,817 contracts, Nov 2024 — Feb 2026):

| GPU Type | Buyer Rate | Supplier Rate | Spread | Deals |
|----------|-----------|---------------|--------|-------|
| **B300 (FDO)** | **$5.50/hr** | **$4.76/hr** | **$0.74** | 3 (spot only) |
| B200 | $3.98/hr | $3.55/hr | $0.43 | 280 |
| H200 | $2.11/hr | $1.82/hr | $0.29 | 325 |
| H100 | $1.42/hr | $1.25/hr | $0.17 | 477 |

B300 commands a **2.8x premium** over B200 and **3.9x premium** over H100. Only 3 spot contracts have been recorded globally — supply is extremely limited, and FDO would be the first LATAM B300 deployment.

### 4.3 Revenue Projections

| Scenario | Rate | Utilization | Monthly Revenue | Annual Revenue |
|----------|------|-------------|-----------------|----------------|
| **Bull** | $5.50 | 95% | $2.17M | $26.0M |
| **Base** | $4.50 | 90% | $1.60M | $19.2M |
| **Bear** | $3.50 | 80% | $1.16M | $13.9M |

**Key assumption:** Revenue is denominated in USD through the Brokkr platform, providing a natural hedge against MXN/USD volatility.

### 4.4 GPU Price Decay Risk

The single largest risk to the revenue model is GPU price decay. H100 prices declined ~39% over 13 months (from $2.34 to $1.42/GPU/hr). If B300 follows a similar trajectory:

| Timeline | Optimistic | H100-Mirrored | Aggressive |
|----------|-----------|---------------|-----------|
| COD (Jul 2026) | $5.50 | $5.50 | $5.50 |
| +6 months | $4.69 | $4.29 | $3.85 |
| +12 months | $4.07 | $3.19 | $2.20 |
| +18 months | $3.96 | $3.19 | $2.09 |

**Critical insight:** Even in the aggressive decay scenario, the breakeven rate is $1.06/GPU/hr at 90% utilization — well below all projected price floors. The asset generates positive cash flow in every modeled scenario.

---

## 5. Financial Structure

### 5.1 Total Sources & Uses

| Source | Amount (USD) | % of Total |
|--------|-------------|-----------|
| GPU Debt (USD.AI, 15%, 3yr) | ~$30.0M | 65% |
| DC Infrastructure Debt (USD.AI, 8%, 10yr) | ~$9.3M | 20% |
| Equity | ~$6.9M | 15% |
| **Total** | **$46.2M** | **100%** |

| Use | Amount (USD) | % of Total |
|-----|-------------|-----------|
| GPU Hardware (576x B300) | $37.3M | 80.6% |
| Auxiliary CAPEX | $5.0M | 10.8% |
| EPC Construction (ATN) | $2.5M | 5.5% |
| Engineering & Commissioning | $0.8M | 1.8% |
| CFE + Permits + Contingency | $0.6M | 1.3% |
| **Total** | **$46.2M** | **100%** |

### 5.2 Debt Financing

| Tranche | Lender | Amount | Rate | Term | Status |
|---------|--------|--------|------|------|--------|
| GPU Permanent | USD.AI | ~$30M | 15% fixed | 3 years | **Term Sheet Fully Executed** |
| DC Infrastructure | USD.AI | ~$9.3M | 8% fixed | 10 years | **Term Sheet Fully Executed** |
| Bridge (Construction) | Metaversal Ventures | $27.3M | 10% | 6 months | NDA Signed (Mar 6, 2026) |

The bridge financing from Metaversal covers the construction period. Upon COD, the permanent USD.AI facility (70-80% LTV, USDC-denominated) takes out the bridge.

### 5.3 Equity Requirement

The project requires approximately **$6.9M — $9.1M in equity**. Active prospects:

| Prospect | Type | Status |
|----------|------|--------|
| Olayan Group | Family Office | In discussions |
| ERA Funds | Infrastructure Fund | In discussions |
| Philippe Sourofim | Private Investor | In discussions |
| Macquarie | Infrastructure Bank | In discussions |

**Financial advisor:** Moelis & Company (NDA executed March 11, 2026).

### 5.4 Key Financial Metrics

| Metric | Bull Case | Base Case | Bear Case |
|--------|-----------|-----------|-----------|
| Annual Revenue | $26.0M | $19.2M | $13.9M |
| Annual OPEX | $2.7M | $2.7M | $2.7M |
| Annual Debt Service | ~$13.2M | ~$13.2M | ~$13.2M |
| Net Cash Flow (Year 1) | $10.1M | $3.3M | ($2.0M) |
| DSCR | 1.87x | 1.59x | 1.05x |
| Payback Period | 1.9 years | 2.8 years | N/A (requires restructuring) |
| Breakeven Utilization | 38% | — | — |
| Breakeven GPU Rate | $1.06/hr | — | — |

---

## 6. Annual Operating Expenditure (OPEX)

| Category | Annual USD | % of Total |
|----------|-----------|-----------|
| Energy (Iberdrola IBD) | $1,207K | 46.2% |
| Telecom (2x 100Gb transit) | $457K | 17.5% |
| O&M Infrastructure | $317K | 12.1% |
| Personnel (IT + Ops) | $286K | 11.0% |
| Insurance | $244K | 9.3% |
| OEM/DDC Support | $101K | 3.9% |
| **Total Annual OPEX** | **$2,736K** | **100%** |

**Energy detail:** Iberdrola qualified supply (MEM) at an all-in rate of $1.87 MXN/kWh ($0.109 USD/kWh), representing approximately $11.2M MXN/year in savings versus CFE's basic commercial tariff.

---

## 7. EPC Selection & Construction

### 7.1 Competitive Bidding Process

BCYSA (Owner's Engineer) conducted an independent technical-economic evaluation of 6 EPC contractors across 4 negotiation rounds. Three finalists were shortlisted; three were discarded for incomplete proposals.

| Contractor | Final Bid | Timeline | PUE | Total Load | Experience | Verdict |
|-----------|-----------|----------|-----|-----------|-----------|---------|
| **ATN** | **$6.88M** | 27 wks | **1.34** | **1.337 MW** | 8 projects | **Recommended** |
| PRIMA | $7.91M | 13 wks | 1.48 | 1.474 MW | 4 projects | Structural risk |
| MiELECTRIC | $7.76M | 28 wks | 1.57 | 1.568 MW | 1 project | Non-compliant |

### 7.2 Why ATN

ATN delivers the best value across every evaluation criterion except speed (PRIMA is faster at 13 weeks, but with 15% cost premium and significant structural modification risk). Key differentiators:

- **Lowest price** by $880K-$1.03M among finalists
- **Best PUE** (1.34) — saves ~100-230 kW continuously vs competitors
- **Only bidder with full UPS compliance** (2x 1,250 kW Schneider covers full DC load)
- **Precision-grade HVAC** (Schneider chillers vs GREE comfort-grade from MiELECTRIC)
- **Deepest experience** (8 comparable data center builds)
- **Minimal structural impact** (minor facade adjustments only)

### 7.3 Construction Timeline

27-week fixed-price EPC contract with milestone-based payments:
- 25% advance upon signing
- 50% upon equipment arrival
- 15% upon installation progress verification
- 10% upon final acceptance and commissioning

---

## 8. Risk Analysis

### 8.1 Risk Heat Map

| Severity | Risks |
|----------|-------|
| **Critical** | GPU price decay (High probability, High impact) |
| **High** | Construction delay, CFE supply interruption |
| **Medium** | Equity gap closure, FX volatility, low initial utilization, interest rates, cooling failure |
| **Low** | Regulatory change, seismic event, cybersecurity, key person dependency |

### 8.2 Mitigation Framework

**GPU Price Decay (Critical):** Brokkr platform enables long-term contract structures (1-24 month terms comprise 42% of historical deals), providing revenue visibility. B300 scarcity creates a natural price floor above H100 levels. Diversified GPU mix planned for 250MW expansion phase.

**Construction Delay (High):** Fixed-price EPC with ATN eliminates cost overrun risk. Weekly milestone tracking with BCYSA oversight. Long-lead equipment (chillers, UPS, generators) pre-ordered.

**CFE Supply Interruption (High):** Triple-redundant backup: 3x 800kW diesel generators (N+1), 10-minute UPS bridge (Li-ion), ATS auto-transfer in <10 seconds.

**Equity Gap (Medium):** Bridge financing from Metaversal ($27.3M at 10%) covers construction period. Multiple equity prospects in active discussions. Moelis & Company engaged as financial advisor.

**FX Volatility (Medium):** Revenue is USD-denominated through Brokkr. Debt is USD-denominated through USD.AI. Only OPEX (energy, personnel) is MXN-denominated, creating a natural hedge where MXN depreciation actually improves margins.

### 8.3 Breakeven Sensitivity

The project breaks even at remarkably low thresholds:

- **38% GPU utilization** at current B300 spot rate ($5.50/hr) — Brokkr historical platform utilization exceeds 90%
- **$1.06/GPU/hr** at 90% utilization — H100, the oldest tracked GPU, still trades at $1.42/hr after 13 months of decline

---

## 9. Corporate & Legal Structure

### 9.1 Ownership Chain

```
Fernando Calvillo A. (49%)    Manuel Calvillo A. (49%)
        |                              |
  Fermaca Dreams Holding       Cia. Mexicana de Gas Natural
     S.A. de C.V.                  S.A. de C.V.
        |                              |
        | (99.99%)                (0.01%) |
        +-------->  Fermaca Domes  <------+
                    S.A. de C.V.
                   (Project SPV)
                        |
                   FDO Data Center
```

### 9.2 Legal Status

| Item | Status |
|------|--------|
| Escritura Publica | No. 48,247, inscribed at RPP Mexico City |
| Legal Representative | Laura Trejo Chaparro (powers of attorney for administration, litigation, collections) |
| Tax Status | Active (SAT), Regimen General de Ley |
| Bank Account | BBVA Mexico (MXN), opened January 14, 2026 |

### 9.3 Fermaca Dreams Group

The Calvillo family has operated Fermaca Dreams for 60+ years across telecommunications, petrochemical, engineering, energy, and marine sectors. The group has raised $1B+ in equity capital, secured $2B+ in debt, and manages $4B in commercial value. Esentia Energy Systems (ESENTIAII.MX) was successfully listed on the Mexican Stock Exchange — demonstrating capital markets capability.

---

## 10. Strategic Context — Beyond FDO

FDO is Phase 1 of a larger strategy:

| Phase | Capacity | Status | Timeline |
|-------|----------|--------|----------|
| **Phase 1: FDO** | 1 MW | Under construction | COD Q2 2026 |
| **Phase 2: Digital City** | 250 MW | Planning | 2027-2030 |

The 1 MW facility is the operational proof-of-concept: it validates the NVIDIA reference architecture, the Hydra Host distribution model, the ATN construction methodology, and the Fermaca operational capability. Success at FDO de-risks the 250 MW expansion by providing auditable financial performance data, a live NVIDIA Cloud Partner credential, and a demonstrated construction playbook.

---

## 11. Board Resolution Requested

Management requests board approval for:

1. **Execution of the ATN EPC contract** ($6.88M USD, 27-week fixed price) to commence construction
2. **Finalization of the USD.AI permanent debt facility** (~$39.3M total, GPU + DC tranches)
3. **Authorization to close the Metaversal bridge loan** ($27.3M at 10%, 6 months)
4. **Continuation of equity raise discussions** with Olayan Group, ERA Funds, Sourofim, and Macquarie, supported by Moelis & Company
5. **Procurement authorization for Dell GPU hardware** (72x PowerEdge XE9780, $39.7M including IVA)

---

## Appendices

- **Appendix A:** BCYSA Evaluacion Tecnica-Economica (Anexo 1)
- **Appendix B:** BCYSA Recomendacion Tecnica (Anexo 2)
- **Appendix C:** BCYSA Comparativa Tecnica (Anexo 3)
- **Appendix D:** FDO Dashboard (Interactive) — see `fdo-dashboard.html`
- **Appendix E:** Hydra Host Contract Decay Analysis
- **Appendix F:** Dell OEM Quotes (PSP MC & NBD)
- **Appendix G:** USD.AI Fully Executed Term Sheet
- **Appendix H:** CFE Oficio Resolutivo 0659/2026
- **Appendix I:** Iberdrola MEM Qualified Supply Acceptance

---

*This document was prepared from data extracted from the FDO Pre-Construction Digital Twin Dashboard and supporting project documents. All financial projections are estimates and subject to market conditions.*
