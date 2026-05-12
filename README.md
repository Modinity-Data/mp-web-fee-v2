# Modinity Fee Simulator — Website vs Marketplace

An interactive single-page tool built by the **Modinity Data & Business Intelligence Team** to simulate and compare platform fees across sales channels (Website vs Marketplace) for multiple brands.

## What it does

Adjust the Website/Marketplace sales split and projected growth to instantly see how platform fees change across all Modinity brands. The simulator computes baseline fees vs projected fees and highlights savings or cost increases — with an Executive Summary, per-brand breakdown, and an interactive waterfall chart.

**Key features:**

- **Channel mix simulation** — slide the global or per-brand Website share slider to model different channel distributions
- **Sales growth modelling** — apply a projected growth % (−100% to +100%, or custom) across all brands
- **Multi-brand support** — Buttonscarves, Buttonscarves Beauty, Nada Puspita, TYGA, Benang Jarum, ZytaDelia, Calla
- **Two baseline datasets** — Ramadan Day 1 (1 Mar 2025) or Full Month (1–31 Mar 2025)
- **Configurable fee assumptions** — MP fee %, TapCart fee %, Midtrans per-transaction cost, free shipping subsidy
- **Export to Excel** — download a two-sheet workbook (Inputs + Projections) with one click
- **Dark / light mode** — theme preference is persisted in localStorage

## Fee model

| Fee type | Applies to |
|---|---|
| Shopify % | Website + App sales |
| TapCart % | App sales only |
| Midtrans (Rp/trx) | Website + App transactions |
| Free shipping subsidy | Website + App transactions (eligible %) |
| Marketplace fee % | MP sales (2025 rate for baseline, 2026 rate for projection) |

## Tech stack

| Layer | Technology |
|---|---|
| UI | Vanilla HTML + JavaScript |
| Styling | Tailwind CSS (CDN) |
| Charts | Chart.js v4 + chartjs-plugin-datalabels |
| Excel export | SheetJS (xlsx) |
| Serving | nginx (Docker) |

## Running locally

**Open directly in browser** (no build step needed):

```bash
open index.html
```

**Run with Docker:**

```bash
docker build -t modinity-fee-sim .
docker run -p 8080:8080 modinity-fee-sim
```

Then open [http://localhost:8080](http://localhost:8080).

## Project structure

```
.
├── index.html          # Entire application — HTML, CSS, and JS in one file
├── ramadan backup.html # Previous version (Ramadan analysis view)
├── Dockerfile          # nginx:alpine, serves on port 8080
└── .dockerignore
```

## Brands & data

Baseline sales data covers **March 2025** (Ramadan period). All figures are in IDR. Transaction counts are used to derive average order value (AOV) per channel, which is then used to estimate projected transaction counts when sales mix changes.

| Code | Brand |
|---|---|
| BS | Buttonscarves |
| BSB | Buttonscarves Beauty |
| NP | Nada Puspita |
| TYGA | TYGA |
| BJ | Benang Jarum |
| ZD | ZytaDelia |
| CL | Calla |

---

*Developed by Modinity Data & Business Intelligence Team*
