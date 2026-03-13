---
name: update-dashboard
description: Scan project documents in docs/ for new or changed data and update fdo-dashboard.html accordingly. Use when docs have been added or modified and the dashboard needs to reflect the latest project information — cabinets, power, cooling, financials, energy, construction timeline, network, or any other facility parameter.
argument-hint: [--full | --changed | subfolder]
disable-model-invocation: true
allowed-tools: Read, Glob, Grep, Bash, Edit, Write, Agent, AskUserQuestion
---

# Dashboard Update Skill

You are updating the FDO pre-construction digital twin dashboard (`fdo-dashboard.html`) based on project documents in `docs/`. This is a **single-file HTML dashboard** with inline JS and Canvas 2D charts — no frameworks.

## Step 0 — Determine Scan Scope

Parse `$ARGUMENTS` to decide what to scan:

| Argument | Behavior |
|----------|----------|
| `--changed` (or no argument) | Scan only docs changed since the last dashboard commit. Use: `git log -1 --format=%H -- fdo-dashboard.html` to get the last dashboard commit, then `git diff --name-only <hash> HEAD -- docs/` plus any untracked files in docs/ via `git ls-files --others --exclude-standard docs/`. |
| `--full` | Scan ALL files in `docs/` regardless of git status. |
| A subfolder name (e.g., `Energy`, `BCYSA`, `Financing`) | Scan only `docs/<subfolder>/` — all files in it. |

If no new or modified documents are found, report that to the user and stop.

## Step 1 — Inventory & Extract

For each document in scope:

1. **List** all files with their modification dates and sizes.
2. **Extract content** based on file type:
   - **PDF**: Use `pdftotext` (available via Git for Windows mingw64) to extract text. For multi-page PDFs, extract all pages. If `pdftotext` fails, use `node` with a pdf-parse approach or report the file as unreadable.
   - **Excel (.xlsx/.xls/.XLSX)**: Use `node -e "const XLSX=require('xlsx'); ..."` to read sheets and dump cell data. The `xlsx` npm package is installed.
   - **Word (.docx/.doc)**: Use `node` to unzip and extract document.xml text, or use available CLI tools.
   - **Images (.jpeg/.jpg/.png)**: Read them directly with the Read tool (Claude is multimodal) and describe relevant content.
   - **HTML**: Read directly with the Read tool.
3. **Summarize** each document's key data points in a structured list — focus on quantitative values: kW, TR, USD, MXN, counts, dimensions, dates, equipment models, capacities.

## Step 2 — Read Current Dashboard State

Read `fdo-dashboard.html` and extract the current values for all key parameters. Focus on:

- **Facility**: cabinet count, rack layout (Row A / Row B), floor area, elevation, seismic zone
- **Power**: IT load (kW), total facility load (kW), PUE, transformer (MVA), UPS (kVA), generators (kW), PDU specs
- **Cooling**: chiller model, count, capacity (TR), flow rate (GPM), CRAC units, temperatures
- **GPU/Compute**: GPU model, count, nodes, servers per cabinet, kW per cabinet
- **Network**: switch models, counts, uplink speeds, InfiniBand topology
- **Financial**: CAPEX total, OPEX annual, S&U total, debt terms, equity, energy cost (USD/kWh, MXN/kWh)
- **Energy**: tariff provider, rate structure, monthly consumption, PPA terms
- **Timeline**: construction duration, COD date, EPC contractor, milestones
- **Digital Twin**: simulation parameters (PUE center, chiller count in 3D, facility load multiplier)

## Step 3 — Diff & Classify Changes

Compare extracted document data against current dashboard values. For each discrepancy, classify it:

### AUTO-APPLY (obvious, mechanical updates):
- A numeric value has clearly changed (e.g., PUE 1.33 → 1.28, chiller capacity 268.8 → 300 TR)
- An equipment model name has been updated (e.g., chiller brand change)
- A date or timeline milestone has shifted
- A financial figure has been updated in a newer version of the same spreadsheet
- A count has changed (e.g., cabinets, generators, switches)
- Unit conversions or derived values that follow directly from a primary change (e.g., PUE change → facility load recalculation)

### ASK USER (ambiguous or structural):
- A **new category** of equipment or cost appears that doesn't have a dashboard section yet
- **Conflicting data** — two documents show different values for the same parameter
- **Structural changes** — e.g., adding a new tab, new chart, or new KPI card
- **Removed items** — a component present in the dashboard is absent from newer docs (might be intentional or might be doc scope)
- **Terminology changes** that could affect multiple labels/references
- **Alternative configurations** — docs show multiple options (e.g., NVIDIA vs Hydrahost) and it's unclear which is active
- **Legal/contractual data** — PPA terms, loan terms, equity structures (these warrant confirmation)

## Step 4 — Present Change Plan

Before making any edits, present a clear summary:

```
## Dashboard Update Summary

### Documents Scanned
- [list of files scanned with dates]

### Auto-Apply Changes (N items)
| # | Parameter | Current Value | New Value | Source Document |
|---|-----------|---------------|-----------|-----------------|
| 1 | PUE       | 1.33          | 1.28      | Lista de Cargas v5.pdf |
| ...

### Questions (M items)
For each ambiguous item, ask the user using AskUserQuestion with clear options.

### No Changes Detected
- [list of parameters reviewed that match current dashboard]
```

Wait for the user to confirm auto-apply items and answer questions before proceeding.

## Step 5 — Apply Changes

When applying changes to `fdo-dashboard.html`:

1. **Use bulk Node.js scripts** for changes affecting 10+ locations (write a temp `.js` file, run it, delete it). This avoids dozens of individual Edit calls.
2. **Use the Edit tool** for targeted changes (< 10 locations).
3. **Recalculate derived values** when a primary value changes:
   - PUE change → facility total load = IT load × PUE
   - Chiller change → cooling section, 3D view chiller count, simulation params
   - Cabinet count change → rack layout, 3D view loops, heatmap dimensions, power distribution
   - Financial changes → S&U totals, CAPEX/OPEX charts, waterfall charts
   - Energy rate change → monthly/annual cost recalculations
4. **Update the Digital Twin simulation** section if physical parameters changed:
   - `dtInit()` / `dtDraw3D()` / `dtDrawHeatmap()` / `dtDrawPower()` functions
   - 3D isometric view: equipment count, row layout
   - Simulation center values: PUE, temperatures, loads
5. **Verify** with Grep that no stale values remain after edits.

## Step 6 — Verify & Report

After all edits:

1. Run `grep` searches for any remaining old values that should have been updated.
2. Present a final summary of all changes made.
3. Commit with a descriptive message following the project's git conventions (per CLAUDE.md).
4. Push to remote.

## Important Rules

- **FX Rate**: 17.2 MXN/USD unless a document explicitly states a different rate.
- **Active config**: The FDO project uses the **Hydrahost** cabinet configuration (57.9 kW/cab) unless documents indicate otherwise. NVIDIA config (71.5 kW/cab) is reference only.
- **Spanish documents**: Many docs are in Spanish. Extract and translate key technical values.
- **File versions**: When multiple versions of the same document exist, use the **most recent** (by filename date or modification date).
- **Never fabricate data**: Only use values explicitly found in documents. If a value can't be extracted, flag it as unreadable.
- **Preserve chart architecture**: All charts use vanilla Canvas 2D with helper functions (`drawHBarChart`, `drawDonut`, `drawWaterfall`). Do not introduce external libraries.
- **Single-file constraint**: All changes go into `fdo-dashboard.html`. No external JS/CSS files.
