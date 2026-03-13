# FDO Dashboard — User Guide

**Fermaca Digital Origins** | Pre-Construction Digital Twin Dashboard
**File:** `fdo-dashboard.html` | **Version:** March 2026

---

## Getting Started

Open `fdo-dashboard.html` in any modern browser (Chrome, Edge, or Firefox recommended). No installation or internet connection is required — the entire dashboard is a single self-contained HTML file.

For the best experience, use a screen width of 1200px or wider. All charts automatically resize when you resize the browser window.

To serve it locally (e.g., for team access on the same network):

```bash
npx -y http-server . -p 8000 -c-1
```

Then open `http://localhost:8000/fdo-dashboard.html`.

---

## Navigation

The **tab bar** at the top contains 15 sections. Click any tab to switch views. The active tab is highlighted in NVIDIA green. Tabs scroll horizontally on smaller screens.

| # | Tab | What It Shows |
|---|-----|---------------|
| 1 | **Overview** | Executive summary: KPI cards (IT capacity, GPUs, PUE, tier level, S&U, COD), business case narrative, project overview, and a Risk Matrix with 4 analytical charts |
| 2 | **Power & Energy** | Complete power chain from CFE 23kV feed through transformer, UPS, generators, and PDUs to cabinets. Includes KPI cards and power distribution charts |
| 3 | **Cooling** | Chiller specifications (3x Schneider XRAC1812A, 134.4 TR each), CRAC units, chilled water loop diagram with flow rates and temperatures |
| 4 | **Rack Layout** | Interactive 18-cabinet grid (Row A + Row B). Hover over any cabinet to see its type, GPU count, power load, and inlet temperature |
| 5 | **Network** | Full network topology: InfiniBand fabric (12x Q3400-X800), Ethernet switches (4x SN5610), Hydra Edge Routers, and 4x 100Gb uplinks. Includes OPEX chart |
| 6 | **Facility** | Site details: location (CDMX, 2,395m elevation), seismic zone D, building specs, floor plan parameters |
| 7 | **Timeline** | 24-week construction Gantt chart showing all phases from site prep through commissioning. EPC contractor: ATN Ingenieria |
| 8 | **Financial** | Sources & Uses waterfall chart and summary — $46.2M total project funding structure |
| 9 | **CAPEX** | Capital expenditure deep dive with waterfall and donut charts. Total CAPEX: $51.6M across IT, electrical, mechanical, and civil categories |
| 10 | **OPEX** | Annual operating expenses ($2.7M USD) with pie chart, treemap, energy cost breakdown, and network OPEX analysis |
| 11 | **EPC Eval** | BCYSA technical & economic evaluation of EPC bids — bubble chart comparison, PUE/load analysis, bid evolution timeline, and HVAC breakdown |
| 12 | **OEM** | Dell equipment quotes and cost analysis |
| 13 | **GPUaaS** | GPU-as-a-Service market analysis: Hydra Host overview, pricing evolution, deal volume trends, contract term distribution, spread analysis, and B300 revenue projections |
| 14 | **Legal** | Corporate structure org chart, escritura details, entity information, shareholder table, and NDA register |
| 15 | **Digital Twin** | Interactive 3D isometric facility view with real-time simulation — PUE, temperatures, power load, and heatmap visualization |

---

## Interacting with Charts

All charts are rendered using HTML5 Canvas. They are **not static images** — they redraw automatically when:

- You **switch tabs** (charts render on tab activation)
- You **resize the browser window** (all charts scale to fit)

### Hover Interactions

- **Rack Layout (tab 4):** Hover over any cabinet to see a tooltip with cabinet ID, type (GPU-A, GPU-B, or Network), node count, GPU count, power draw, and inlet temperature.
- **Charts with labels:** Most bar charts and donuts display values directly on the chart face — no hover needed.

---

## Digital Twin Tab (Interactive Simulation)

The Digital Twin tab is the most interactive section. It contains:

### 3D Isometric Facility View
A real-time rendered isometric view of the data center showing:
- **17 cabinets** — color-coded by type (14 GPU-A in green, 1 GPU-B in lighter green, 2 Network in blue)
- **3 chillers** along the top (Schneider XRAC1812A)
- **3 diesel generators** (600kW each, N+1)
- **InfiniBand spine switches** and **Ethernet switches** with animated fiber runs
- **Uplink fiber** to the MMR (Meet-Me Room) with animated pulse dots

A **component legend** in the bottom-right identifies each element type.

### Simulation Controls
The simulation runs automatically on tab activation. The status panel in the top-left shows live-updating values:
- **PUE** — oscillates around the design target of 1.33
- **IT Load** — fluctuates around 1,000 kW
- **Supply/Return temperatures** — chilled water loop readings
- **Alert status** — shows current cooling configuration

### Heatmap
Below the 3D view, a **thermal heatmap** shows temperature distribution across all cabinets with a color gradient from blue (cool) to red (hot).

### Power Distribution
A real-time **power distribution chart** shows how facility load is split across IT, cooling, lighting, and other subsystems.

---

## Risk Matrix (Overview Tab)

Scroll down in the Overview tab to find the **Risk Matrix & Sensitivity Analysis** section with four charts:

1. **Risk Heat Map** — 5x5 probability vs. impact grid with positioned risk items
2. **Monte Carlo Sensitivity** — Contour-style visualization of financial sensitivity
3. **Risk Decay Timeline** — Shows how risk exposure decreases over the construction timeline
4. **Cash-Flow-at-Risk** — Probability distribution of project cash flows

Below the charts, a **Risk Register** table lists all identified risks with their category, probability, impact, risk score, mitigation strategy, and responsible owner.

---

## Data Sources

All data in the dashboard is sourced from project documents in the `docs/` folder:

| Folder | Content |
|--------|---------|
| `docs/ATN/` | EPC construction proposals and budgets |
| `docs/BCYSA/` | Owner's engineer assessments, load lists, transmittals |
| `docs/Energy/` | CFE/Iberdrola tariffs, PPA contracts, load diagrams |
| `docs/Financing/` | Sources & Uses, debt structure, equity prospects |
| `docs/Legal/` | Corporate structure, escrituras, NDAs |
| `docs/MDCs/` | MDC (modular data center) equipment quotes |
| `docs/SITE/` | Rack and power layout specifications |
| `docs/Dashboard/` | Dashboard commentary and review notes |
| `docs/Gobierno/` | Government permits and regulatory documents |

The dashboard hardcodes all values — it does not read files at runtime. To update the dashboard when new documents arrive, use the `/update-dashboard` command in Claude Code.

---

## Updating the Dashboard

When new or updated documents are added to `docs/`, use Claude Code to sync changes:

```
/update-dashboard              # Scan only docs changed since last dashboard commit
/update-dashboard --full       # Re-scan all documents in docs/
/update-dashboard Energy       # Scan only docs/Energy/ folder
```

This will extract data from the new documents, compare against current dashboard values, and present a change plan for your approval before modifying anything.

---

## Tips

- **Full-screen mode** (F11) gives the best chart readability on smaller monitors.
- **Print / PDF export:** Use your browser's print function (Ctrl+P) — the dark theme will print as-is. For a light background, consider browser print settings.
- **Sharing:** Since it's a single HTML file, just send `fdo-dashboard.html` via email or file share. Recipients need no special software.
- **Financial figures** are in USD unless explicitly labeled MXN. The FX rate used throughout is **17.2 MXN/USD**.
- **Color coding:** Green = NVIDIA/positive, Blue = informational, Amber = warning/attention, Red = critical/risk.
