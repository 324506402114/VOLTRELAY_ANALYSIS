# VoltRelay Energy — Battery Swap Network Analysis

**Gradient Learnings Data Analytics Hackathon**

An end-to-end analysis of a simulated battery-swapping network for electric two- and three-wheelers, operating across six Indian cities (Bengaluru, Delhi NCR, Hyderabad, Pune, Mumbai, Jaipur) between January 2024 and June 2025.

---

## Business Background

VoltRelay Energy runs unmanned battery-swap cabinets serving gig and logistics riders — food delivery, quick commerce, e-commerce logistics, cargo, and bike-taxi — who need a charged battery in minutes rather than hours. Over 18 months, VoltRelay expanded its station network in two waves, changed its base pricing, piloted peak/off-peak pricing in two cities, onboarded a new battery supplier, and renegotiated its largest fleet contract. Completed swaps and revenue both grew, but service failures rose faster, new-rider retention fell, and per-swap profitability eroded.

This project investigates what's actually driving those outcomes, using ~3.9 million swap events plus station, battery, rider, fleet partner, and support ticket data.

## Core Questions Investigated

1. **Network Performance Over Time** — trends in completed swaps, revenue, failure rate, and contribution margin per swap
2. **Service Failures & Customer Experience** — queue wait, failed attempts, and abandonment by station, hour, season, and vehicle class
3. **Station & Geographic Patterns** — charger generation, location type, and commissioning timing vs. service performance
4. **Battery & Equipment Performance** — state of health, charge cycles, supplier, and manufacturing lot vs. delivered range and swap frequency
5. **Pricing & Partner Economics** — base price change, peak/off-peak pilot, and fleet contract terms vs. revenue and margin
6. **Root Cause of Retention** — which factors most strongly associate with new riders not returning

## Repository Structure

```
.
├── README.md
├── VoltRelay_Analysis.ipynb      # Main analysis notebook (Colab-ready)
├── data/                         # Raw CSVs (not committed — see Data section)
├── outputs/
│   └── charts/                   # Exported chart images
└── report/
    └── VoltRelay_Analysis_Report.pdf   # Written findings & recommendations
```

## Dataset

| File | Rows | Grain |
|---|---|---|
| `swap_events.csv.gz` | 3,877,013 | 1 row per swap attempt |
| `station_hourly_status.csv.gz` | 1,487,712 | 1 row per station per hour |
| `riders.csv` | 20,000 | 1 row per registered rider |
| `batteries.csv` | 6,500 | 1 row per battery pack |
| `support_tickets.csv` | 44,000 | 1 row per support ticket |
| `stations.csv` | 152 | 1 row per swap station |
| `city_daily_context.csv` | 3,282 | 1 row per city per day |
| `fleet_partners.csv` | 12 | 1 row per fleet customer |

> **Note:** raw CSVs are excluded from this repo (`swap_events.csv.gz` alone is 500MB+). Download the dataset from the hackathon dataset link and place the files in `data/` locally, or in a Google Drive folder if running in Colab.

**Source & license:** Synthetic dataset generated for the Gradient Learnings Data Analytics Hackathon (seed `59500`). All company names (VoltRelay Energy, ZipDrop, RapidCell, fleet partners) are fictional. Free for use within this hackathon — no real company or personal data is involved.

## How to Run

### Option A — Google Colab (recommended)
1. Upload the 8 dataset files to a folder in Google Drive.
2. Open `VoltRelay_Analysis.ipynb` in [Google Colab](https://colab.research.google.com) (`File → Upload notebook`).
3. Update the `BASE` path in the Setup cell to point at your Drive folder.
4. `Runtime → Run all`.

### Option B — Local Jupyter
```bash
git clone <this-repo-url>
cd voltrelay-analysis
pip install -r requirements.txt
jupyter notebook VoltRelay_Analysis.ipynb
```
Place the dataset CSVs in `data/` and update the `BASE` path at the top of the notebook accordingly. (Note: the notebook's Drive-mount cell only applies in Colab — replace it with a local path when running in Jupyter.)

### Requirements
```
pandas
numpy
matplotlib
seaborn
```

## Data Cleaning Highlights

The notebook explicitly handles several known data-quality issues, documented inline:
- Inconsistent city spellings in `riders.home_city` (standardized to 6 canonical cities)
- A firmware bug (`v3.2.0`, Mar 10–Apr 14 2025) that logged event timestamps ~5h30m early
- Near-duplicate swap records from offline-sync retries
- Out-of-range sensor readings (SoC/SoH > 100%, implausible odometer deltas) — flagged, not silently dropped
- Two internal test stations excluded from network-performance metrics
- Non-random missingness in support ticket CSAT scores, accounted for rather than averaged naively

## Deliverables

- [x] **Analysis Notebook** — `VoltRelay_Analysis.ipynb` (data understanding, cleaning, EDA, analysis, visualizations)
- [ ] **Analysis Report** — problem understanding, approach, key insights, visualizations, recommendations
- [ ] **3-Minute Video** — business problem, approach, key insight(s), recommendations for VoltRelay leadership

## Key Findings

*(Fill in once analysis is complete — see Section 13 of the notebook)*

- **Network performance:**
- **Service quality:**
- **Equipment:**
- **Pricing & partners:**
- **Retention root cause:**

## Recommendations

*(Tie back to VoltRelay's four proposed budget uses — more stations, more batteries, network-wide pricing rollout, or a long-term fleet exclusive)*

1.
2.
3.

## Author

*(Your name / team name here)*

## License

This project uses a synthetic dataset generated for the Gradient Learnings Data Analytics Hackathon. No real company, rider, or personal data is involved.
