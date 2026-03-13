# Dashboard Parameter Reference

This file maps dashboard parameters to their document sources, making it easier to identify what needs updating. Keep this file updated as the dashboard evolves.

## Document Source → Dashboard Section Mapping

| docs/ Subfolder | Dashboard Sections Affected |
|-----------------|----------------------------|
| `ATN/` | Construction timeline, CAPEX (EPC costs), OPEX |
| `BCYSA/` | Power budget, cooling, rack layout, PUE, engineering specs |
| `Energy/` | Energy tariffs tab, IBD rates, CFE connection, PPA terms |
| `Financing/` | Sources & Uses, CAPEX deep dive, OPEX, financial charts |
| `MDCs/` | Cabinet specs, GPU config, DDC S-Series details, rack layout |
| `Network/` | Network topology, switch inventory, InfiniBand |
| `NVIDIA/` | GPU specs, DGX/HGX configuration, compute KPIs |
| `OEM/` | Server/hardware specs |
| `Hydra Host/` | Contract terms, decay data, cabinet power profiles |
| `SITE/` | Floor plan, rack and power layout |
| `Gobierno/` | Government financing (NAFIN/Bancomext), regulatory |
| `Legal/` | Corporate structure, NDAs |
| `Teasers/` | Project overview (investor-facing summary data) |
| `Dashboard/` | Dashboard feedback/corrections documents |
| `MDCs/Crusader/` | Alternative MDC vendor quotes |
| `MDCs/EcoBlox/` | Alternative MDC vendor quotes |
| `MDCs/Gas/` | Gas turbine / backup power options |

## Key Parameters & Typical Locations in fdo-dashboard.html

These are searched by the skill when diffing. Format: `parameter → search pattern in HTML/JS`

### Facility
- Cabinet count → `17 cabinets`, `17 DDC`, cabinet loop counters in `dtDraw3D()`
- Row layout → `Row A (9`, `Row B (8`, loop `for(let i=0;i<9` / `for(let i=0;i<8`
- Floor area → search `m²` or `sq ft`
- PUE → `PUE` (KPI cards, energy params, power budget, DT simulation)

### Power
- IT Load → `1,0` followed by `kW` or `MW` near IT context
- Facility total → search `1,460` or `1,524` (total consumption)
- Transformer → `MVA` (e.g., `2 MVA`)
- UPS → `kVA` and `Li-ion`
- Generators → `kW` near `diesel` or `generator` or `N+1`

### Cooling
- Chiller model → `Schneider`, `XRAC`, `HiRef`
- Chiller capacity → `TR` (tons refrigeration)
- Chiller count → `2 chillers` or `3 chillers`, also in 3D view
- Flow rate → `GPM`
- CRAC → `CRAC` count and model

### Compute
- GPU model → `B300`, `B200`, `HGX`
- GPU count → `576` or similar
- Nodes → `72 nodes` or similar
- kW per cabinet → `57.9` (Hydrahost) or `71.5` (NVIDIA)

### Network
- InfiniBand switches → `Q3400`
- Ethernet switches → `SN5610`, `SN2201`, `SN4700`
- Edge routers → `Hydra`
- Uplinks → `100Gb` or `100 Gb`

### Financial (USD unless labeled MXN)
- Total S&U → `$46.2M` or `46,200`
- Total CAPEX → `$51.6M` or `51,600`
- Annual OPEX → `$2.7M` or `2,700`
- Energy rate → `$0.109` or `0.109 USD/kWh`
- GPU debt → `$31.2M`, `15%`, `3yr`
- DC debt → `$3.3M`, `8%`, `10yr`
- Bridge → `$27.3M`, `Metaversal`, `10%`

### Timeline
- Construction duration → `24-week` or `6-month`
- COD → `Q2 2026`
- EPC → `ATN`

### Digital Twin Simulation
- PUE sim center → value in `dtInit()` around `1.30`
- Facility load multiplier → value like `1.33` in DT section
- Chiller count in 3D → loop drawing chillers in `dtDraw3D()`
- Cooling overhead → `315 kW` or similar in DT power draw
