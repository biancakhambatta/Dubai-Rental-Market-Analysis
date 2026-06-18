# Dubai Rental Market Analysis (2020–2026)
### What's driving rental growth across Dubai's key districts?

---

## Overview

This project analyses Dubai's residential rental market using a comprehensive 
dataset spanning January 2020 to April 2026, covering secondary sales, off-plan 
listings, and rental contracts across 84 communities and 52 zones.

The analysis investigates the macroeconomic forces behind Dubai's rental growth 
cycle — from the COVID-era dip through the Expo 2020 rally, the Russian/CIS 
capital influx of 2022, the Golden Visa expansion, the 2023 market peak, and the 
subsequent rate-driven cooling. It is built entirely in Python and structured to 
mirror a professional analytics workflow: raw data through cleaning and feature 
engineering to business-ready findings.

---

## Business Question

**How have Dubai rental prices trended since 2020, and what's driving growth?**

Secondary questions explored:

- Does Dubai's rental growth correlate with macroeconomic indicators —
  mortgage rate cycles, capital inflows, and demand shocks post-2020?
- Which districts are experiencing demand-supply imbalances, and are rental
  prices in those areas outpacing broader market growth?
- Can we identify leading vs lagging districts — communities where price
  signals appear early and predict broader market movement?
- What is the price elasticity pattern across bedroom categories — do larger
  units absorb price shocks differently than studios and 1-beds?
- Is there evidence of a K-shaped recovery post-COVID in Dubai's rental
  market, where luxury and budget segments diverged significantly?
- How does Metro proximity and freehold designation influence rental premiums,
  and have those premiums shifted as infrastructure and policy evolved?

---

## Dataset

- **Source:** [Kaggle — Dubai Real Estate: Sales, Off-Plan & Rentals 2020–2026](https://www.kaggle.com/datasets/sergionefedov/dubai-real-estate-sales-and-rentals-20202026)
- **License:** Apache 2.0 — open for public use and publication
- **Coverage:** January 2020 to April 2026 | 84 communities | 52 zones
- **Total records:** ~93,000 rows across 5 files (~17 MB)

**A note on methodology:** Listing-level records are generated via a hedonic 
pricing model anchored to real DLD/Property Finder base prices per zone, real 
CBUAE mortgage rate timelines, and real Dubai Metro coordinates. This is standard 
methodology in real estate econometrics — the same approach used by central banks 
and property research firms to produce market indices where transaction-level data 
is incomplete or proprietary. Aggregate trends and community-level patterns 
reflect real market dynamics.

### Files used

| File | Rows | Description |
|---|---|---|
| `rentals.csv` | 25,000 | Annual rental contracts: primary analysis file |
| `area_prices_monthly.csv` | 6,384 | Monthly time series: 84 communities × 76 months |
| `secondary_sales.csv` | 50,000 | Secondary market sales: used for K-shaped recovery comparison |
| `metro_stations.csv` | 55 | Dubai Metro stations (Red + Green Line) with coordinates |
| `off_plan.csv` | 12,000 | Off-plan listings: used for market context |

---

## Tools & Libraries

| Tool | Purpose |
|---|---|
| Python 3.11 | Core analysis language |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations and outlier detection |
| Matplotlib / Seaborn | Visualisation |
| Scipy | Pearson correlation, OLS regression, z-score |
| Jupyter Notebook | Development environment |

---

## Project Structure
dubai-rental-market-analysis/

│

├── dataraw/

│   ├── rentals.csv

│   ├── area_prices_monthly.csv

│   ├── secondary_sales.csv

│   ├── metro_stations.csv

│   └── off_plan.csv

│

├── rental_analysis.ipynb     # Main analysis notebook

└── README.md                 # You're here

## Key Findings

1. **Market growth:** Dubai's rental market grew from a median of ~$29,000/yr
   in 2021 to a peak of ~$55,000/yr in mid-2023, an ~90% increase over
   two years, before cooling to ~$47,000/yr by 2026 as mortgage rates rose.

2. **Barbell market structure:** Rather than a classic K-shaped recovery,
   the data revealed a barbell pattern; luxury (peak index: 158.9) and
   budget (peak index: 161.1) segments both significantly outperformed
   mid-market (peak index: 135.4), suggesting two distinct demand drivers
   operating simultaneously: capital inflow at the top, population-driven
   undersupply at the bottom.

3. **Mortgage rate correlation:** Pearson r = 0.518 (p < 0.0001) between
   UAE mortgage rate and median rental prices; statistically significant
   positive correlation, consistent with demand shifting from purchase to
   rental as borrowing costs rose from ~1.5% in 2021 to ~5% in 2023.

4. **Leading communities:** Dubai Islands (~28% avg YoY growth), Jumeirah
   Beach Residence (~26%), and Jumeirah 1 (~25%) consistently outperformed
   the market. Dubailand showed the lowest average growth at under 1%,
   reflecting oversupply in that corridor.

5. **Bedroom elasticity:** 1BR units showed the highest appreciation
   (peak index: 198.2), nearly doubling from the 2021 baseline. 4+ BR
   units showed the lowest growth (peak: 179.9) — suggesting the demand
   surge was driven by single professionals and young couples rather
   than families.

6. **Metro proximity discount:** Contrary to conventional real estate
   wisdom, Metro walkability correlated with a consistent ~53% rental
   discount — reflecting Dubai's unique urban structure where premium
   communities are car-dependent and Metro-served areas skew toward
   affordable mid-density housing.

7. **View premium:** Sea view commanded the highest rental premium at
   +30% over community-facing units ($53,800 vs $41,400/yr), narrowly
   outperforming Burj Khalifa view (+20%) and Marina view (+25%).

8. **Structural price drivers:** Property size (r=0.782) and bedroom
   count (r=0.735) are by far the strongest predictors of rental price.
   Distance to Burj Khalifa showed a negligible negative correlation
   (r=-0.040), and Metro distance showed almost no linear relationship
   (r=0.048) — consistent with Dubai's car-centric premium market geography.
