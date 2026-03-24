# Global Conflict & Economic Stability Analysis
### A Data-Driven Study of Armed Conflict and GDP Growth (1946–2024)

---

## Overview

This project investigates the relationship between armed conflict and national economic performance using two globally recognised datasets. It answers two core research questions:

> **Q1. Which time period saw the biggest spikes in global instability?**
>
> **Q2. Does conflict affect a country's wealth (GDP)?**

---

## Key Findings

**On Global Instability:**
- The **1990s was the most unstable decade in modern history** — 116 minor conflicts, driven by the collapse of the Soviet Union simultaneously destabilising Eastern Europe, Central Asia, and Africa
- Major wars have **declined significantly** since the 1970s (18 wars) to just 1 in the 2020s — but minor conflicts remain persistently high, meaning violence has fragmented rather than disappeared
- **2020 was the worst single year for GDP crashes** — COVID-19 caused 159 of 196 countries to contract simultaneously, more than any conflict-driven year ever recorded
- **Conflict regions are shifting over time** — Asia was the most involved region in the previous century, but recent decades show Africa emerging as the new hotspot for armed conflicts.

**On Conflict and GDP:**
- **Mean vs Median paradox** — Conflict years average **3.06% GDP growth** vs **3.46% in stable years**, yet the median is *higher* during conflict. Most countries maintain moderate growth while a few extreme collapses drag the mean down.

- **Weak global correlation** — r = **−0.020** (p = 0.103). Fast-growing conflict-affected economies (India, Myanmar, Philippines) dilute the signal, making the relationship statistically insignificant at the aggregate level.

- **Intensity is what matters** — Minor conflicts average **+3.45% GDP**. Full-scale wars average **−2.56%**. A **6 percentage point gap** shows that conflict severity determines economic outcome far more than the binary conflict flag alone.

- **Damage is concentrated, not universal** — Moldova **−30.6pp**, Georgia **−22.4pp**, Libya **−16.8pp**, Yemen **−11.5pp**. Conflict creates heavy downside risk for specific countries rather than a uniform global decline.

- **Biggest crash was non-conflict** — Macao SAR fell **−54.2% in 2020** due to COVID-19 — the worst single-year collapse in the dataset. Non-conflict shocks can be equally or more destructive than war.

- **Conflict increases volatility** — The primary economic effect of conflict is not consistent growth suppression but increased variance, making catastrophic collapses far more likely in affected countries.

---

## Datasets

| Dataset | Source | Coverage | Rows |
|---------|--------|----------|------|
| GDP Growth Rate | IMF / Kaggle | 196 countries, 1980–2024 | 6,509 (long format) |
| Armed Conflict | UCDP v25.1 | 303 conflicts, 1946–2024 | 2,752 episodes |

- **GDP dataset** tracks annual GDP growth % per country in wide format (years as columns)
- **UCDP dataset** records each armed conflict episode with government, opponent, region, intensity level (1 = minor, 2 = war), and start/end dates

---

## Project Structure

```
├── Geopolitical_analysis.ipynb   ← Main notebook
├── data
       └──dataset 1.csv   ← GDP growth dataset
       └──dataset 2.csv   ← UCDP conflict dataset
└── README.md
```

---

## Notebook Structure

| Section | Description |
|---------|-------------|
| 1. Data Understanding | Dataset overview, structure, missing value analysis |
| 2. Data Cleaning | Wide-to-long reshape, zero-to-NaN fix, feature engineering |
| 3. EDA — Regional Analysis | Conflict distribution by region, pre/post-2000 shift |
| 4. EDA — Global Instability | Decade-by-decade conflict trends, GDP crash analysis |
| 5. Merged Analysis | Country name crosswalk, conflict flagging, GDP comparison |
| 6. Final Report | Full findings, tables, limitations, methodology |

---

## Methodology

**Data Merging:**
UCDP uses different country names than the GDP dataset (e.g. `"Myanmar (Burma)"` vs `"Myanmar"`). A 21-entry manual crosswalk was built to align names before joining on `[country_name, year]`.

**Conflict Flagging:**
Each conflict episode was expanded across all active years (`start_year → end_year`) to correctly flag every year a country was in conflict — not just the end year.

**Intensity Split:**
Conflicts are separated into Minor (intensity = 1, 25–999 deaths/yr) and War (intensity = 2, ≥1,000 deaths/yr) to isolate the distinct economic impact of each.

---

## Tools & Libraries

```python
pandas      # data manipulation, merging, groupby
numpy       # numerical operations
matplotlib  # all visualisations
scipy.stats # t-test, point-biserial correlation
```

---

## How to Run

1. Clone the repository
2. Place 'data' folder in the same folder as the notebook
3. Open `Geopolitical_analysis.ipynb` in Jupyter or VS Code
4. Run all cells from top to bottom

---

## Limitations

- GDP data starts from 1990 after cleaning — pre-1990 conflict economic impact is unanalysed
- GDP growth % is nominal and affected by exchange rates (Euro adoption in 1999 creates artificial jumps for several European countries)
- Multi-country conflict episodes cannot be cleanly attributed to a single country
- The `in_conflict` flag is binary — it does not capture conflict severity within intensity levels

---

## Author

Built as a geopolitical data analysis portfolio project using Python.

**Datasets:**
- [UCDP Armed Conflict Dataset](https://ucdp.uu.se/downloads/)
- [World GDP Growth Rate — Kaggle](https://www.kaggle.com/)
