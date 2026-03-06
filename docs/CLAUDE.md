# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Fermaca Digital Origins (FDO)** — Pre-construction digital twin dashboard and data repository for a 1MW air-cooled AI data center at Fermaca HQ in Mexico City. The project uses NVIDIA B300 HGX GPUs in DDC S-Series v4 cabinets, with the goal of building an NVIDIA Omniverse digital twin.

## Architecture

### Dashboard
- **fdo-dashboard.html** — Interactive single-file HTML dashboard (130KB, vanilla JS, no dependencies). Contains 11 tabs and 22+ canvas-rendered charts covering facility overview, power, cooling, rack layout, network topology, facility floor plan, construction timeline, financials (S&U), CAPEX deep dive, OPEX, energy tariffs, and digital twin readiness status. All data is sourced from the project documents in `docs/`.

### Data Sources (`docs/`)
- 18 PDF documents: NVIDIA deployment specs, DDC cabinet specs/drawings, ATN construction presentation, BCYSA engineering, Iberdrola energy proposals, Dell quotes, network requirements, project teasers
- 2 Excel files: `CAPEX y OPEX FDO 270126.xlsx` (CAPEX, OPEX, energy tariffs across 14 sheets), `Financing FDO 040326.xlsx` (sources & uses, equity, bridge financing across 5 sheets)

### Key Facility Parameters
- **IT Load:** 1 MW across 18 DDC S-Series v4 NEMA 3R cabinets
- **GPUs:** 72 nodes x 8 GPUs/node = 576 NVIDIA B300 GPUs
- **Power:** CFE 23kV feed, 1.5 MVA Driescher transformer, 3x 600kW diesel generators (N+1), 2x 1000kW UPS (Li-ion, 10 min)
- **Cooling:** 3x 145-ton chillers (N+1), 4x CRAC 3T, chilled water 14C, 36.4 GPM/cabinet
- **Network:** 12x Q3400-X800 InfiniBand, 4x SN5610 Ethernet, 4x Hydra Edge Routers, 4x 100Gb uplinks
- **Financial:** $46.2M total S&U, $51.6M CAPEX, $2.7M USD annual OPEX, Iberdrola pass-through energy at ~$0.109 USD/kWh
- **Timeline:** 24-week (6-month) construction by ATN Ingenieria, COD target Q2 2026
- **Location:** CDMX, 2,395m elevation, Seismic Zone D

## Development

No build or install step. Open `fdo-dashboard.html` in a browser. A local HTTP server can be started with:
```
npx -y http-server . -p 8000 -c-1
```
The `xlsx` npm package is installed for reading Excel files during development (not needed at runtime).

## Dashboard Chart Architecture

All charts are rendered on `<canvas>` elements using vanilla JS (no Chart.js or D3). Key patterns:
- Each chart has a `draw*()` function (e.g., `drawCapexWaterfall()`, `drawEnergyStacked()`)
- All draw functions are called in `init()` on load and on window resize
- Helper functions: `drawHBarChart()`, `drawDonut()`, `drawWaterfall()` for reusable chart types
- Navigation uses `data-section` attributes on nav buttons mapped to `id="sec-*"` divs
- Color palette defined in CSS `:root` variables (--accent: NVIDIA green #76b900, --accent2: blue, --warn: amber, --danger: red)

## Git Workflow

- Commit work to Git regularly — after completing a feature, fixing a bug, or reaching any meaningful milestone. Do not let work accumulate uncommitted.
- Write clean, descriptive commit messages that summarize the "why" of the change.
- Push to GitHub after each commit so progress is always backed up remotely and we never lose work.
- Stage specific files by name rather than using `git add -A` or `git add .`.
- Do NOT commit `node_modules/` or `package-lock.json` unless explicitly asked.

## Conventions

- Single `.html` file with all markup, styles, and scripts inline — no external frameworks or build tools.
- Vanilla JS only. Canvas 2D API for all charts and visualizations.
- PDF/Excel data is extracted once and hardcoded into the dashboard — no runtime file reading.
- Financial figures use USD unless labeled MXN. FX rate: 17.2 MXN/USD.
- Energy data comes from the Iberdrola pass-through IBD tariff table (12 monthly data points).

## Next Steps (Digital Twin)

1. **Awaiting:** 3D CAD files / site renders for OpenUSD conversion
2. **Awaiting:** NVIDIA Omniverse API access credentials
3. **Needed:** BMS/DCIM protocol specs (Modbus/BACnet), sensor placement maps, P&ID diagrams
4. **Future:** Live telemetry integration once facility is operational
