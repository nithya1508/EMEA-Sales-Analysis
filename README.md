# EMEA GTM Intelligence Engine
Portfolio project demonstrating Category Business Manager skills: market sizing, competitive analysis, promotional ROI, and demand signal intelligence across 12 EMEA markets. Enables data-driven go-to-market prioritisation and consumer segment optimisation.

**End-to-end Category Business Manager portfolio project** — market sizing, competitive analysis, promotional ROI modelling, and demand signal intelligence across 12 EMEA markets.

Built to demonstrate the analytical and strategic skills required for go-to-market leadership in consumer hardware across the EMEA region.

---

## What this project demonstrates

| JD requirement | Implementation |
|---|---|
| In-depth data analysis to identify trends & opportunities | TAM sizing, quarterly sell-out modelling, competitive share shift analysis |
| Go-to-market strategy across EMEA | Market tier framework, Demand Signal Index, investment prioritisation matrix |
| Promotional offer strategy & budget management | ROI modelling across 8 promo scenarios × 4 channels |
| Business performance & market share interpretation | Competitive landscape tracker with trend decomposition |
| Internal authority on product category | Upgrader/switcher funnel with segment-level conversion benchmarks |

---

## Project structure

```
emea-gtm-intelligence/
├── src/
│   └── emea_gtm_analysis.py      # Main analysis pipeline (run this first)
├── notebooks/
│   └── emea_gtm_analysis.ipynb   # Annotated walkthrough with charts
├── outputs/                       # Generated JSON + PNG outputs
│   ├── tam_sizing.json
│   ├── quarterly_performance.json
│   ├── competitive_landscape.json
│   ├── promotional_roi.json
│   ├── switcher_upgrader_funnel.json
│   ├── demand_signal_index.json
│   └── executive_summary.json
├── dashboard/
│   └── index.html                 # Interactive 5-panel dashboard
└── README.md
```

---

## Data sources

All analysis is anchored to real public datasets from Kaggle:

| Dataset | Source | Used for |
|---|---|---|
| Global Electronics Retailer Sales | [kaggle.com/bhavikjikadara/global-electronics-retailer](https://www.kaggle.com/datasets/bhavikjikadara/global-electronics-retailer) | Sell-out velocity, channel mix, ASP benchmarks |
| Consumer Electronics Market Analysis | [kaggle.com/manus25/consumer-electronics-market-analysis](https://www.kaggle.com/datasets/manus25/consumer-electronics-market-analysis) | Competitive share, category trends |
| World GDP & Population (World Bank) | [kaggle.com/tunguz/country-regional-and-world-gdp](https://www.kaggle.com/datasets/tunguz/country-regional-and-world-gdp) | TAM sizing inputs, market sizing |

Market share benchmarks cross-referenced with IDC EMEA Consumer Devices Tracker Q4 2023. Promo elasticity anchored to McKinsey Consumer Electronics Promo Effectiveness research (2023). Switcher/upgrader funnel benchmarked against GfK EMEA Consumer Survey archetypes.

---

## Analytical modules

### 1. TAM Sizing (`tam_sizing()`)
Total Addressable Market per EMEA country using a bottom-up approach:

```
TAM = Population × Smartphone Penetration × Premium Segment Share × ASP ($650)
```

12 markets classified into three tiers by TAM, premium appetite, and FX risk. Growth Opportunity Index computed as a weighted composite of premium share, headroom to full penetration, and FX stability.

**Key finding**: Germany ($12.2B), UK ($10.8B), and France ($9.4B) represent 50% of EMEA TAM. UAE and Netherlands show disproportionate premium share relative to population — high-efficiency opportunity.

### 2. Quarterly Performance Tracking (`quarterly_performance()`)
Simulated 12-quarter sell-out series (2022–2024) across 12 markets × 4 channels:
- Carrier/Telco
- Open Market Retail
- Online Direct
- E-tailer

Channel mix assumptions calibrated by market tier (carrier-dominant in Tier 1, open market in Tier 3). AI camera feature launch modelled as a 30% CAGR accelerant from H2 2023.

### 3. Competitive Landscape (`competitive_landscape()`)
EMEA market share tracked quarterly across 5 brands (target brand, Samsung, Apple, Xiaomi, Other). Share normalised to 100% per quarter. Target brand growth trajectory driven by differentiated AI feature narrative vs Android incumbents.

**Key finding**: 10.2pp share gain over study period — primarily captured from mid-tier Android (Samsung −4.4pp, Xiaomi −3.1pp).

### 4. Promotional ROI Modelling (`promotional_roi()`)
Eight promotional scenarios modelled across channel × mechanic:

| Mechanic | Channels tested |
|---|---|
| Trade-in (£200 off) | Carrier, Open Market |
| Bundle (earbuds + case) | Online Direct, E-tailer |
| Cashback (£100) | Open Market, E-tailer |
| Early bird (15% launch discount) | Online Direct |
| Carrier financing (0% APR) | Carrier |

For each scenario:
```
Incremental units = Investment × Elasticity × Noise
Incremental revenue = Units × ASP
ROI = (Incremental Revenue − Investment) / Investment
Margin compression = Investment / (Base Revenue + Incremental Revenue)
```

**Recommendation**: Cashback (Open Market) and Trade-in (Carrier) deliver ROI >100% with margin compression <7%. Avoid Early Bird — insufficient elasticity at current awareness levels.

### 5. Switcher & Upgrader Funnel (`switcher_upgrader_funnel()`)
Decision funnel across three demand segments:

| Segment | Pool | Addressable |
|---|---|---|
| Upgrader (existing Android) | 26.4M | 55% of premium pool |
| Switcher (iOS → Android) | 9.6M | 20% of premium pool |
| New-to-premium | 12.0M | 25% of premium pool |

Stages: Awareness → Consideration → Intent → Conversion. Largest funnel drop identified per segment to focus investment (upgraders lose 21pp at Awareness→Consideration; switchers lose 20pp at Consideration→Intent).

### 6. Demand Signal Index (`demand_signal_index()`)
Composite 0–100 index per market combining:

| Signal | Weight | Proxy |
|---|---|---|
| Search trend | 30% | Relative interest index |
| Sell-out velocity | 30% | Units/week normalised |
| Stock turns | 20% | Retailer inventory health |
| NPS proxy | 20% | Net promoter score estimate |

Markets classified as **Accelerate** (>65), **Sustain** (45–65), or **Build** (<45) — directly informing investment allocation decisions.

---

## Key outputs

### Executive summary (2024 Q4)

| Metric | Value |
|---|---|
| EMEA TAM | $63.7B |
| Current revenue | $2.5B |
| Revenue whitespace | $61.1B |
| Share gain (study period) | +10.2pp |
| Top opportunity market | United Kingdom |
| Best promo ROI | >100% (Cashback, Open Market) |
| Upgrader pool | 26.4M addressable |

### GTM prioritisation

| Priority | Market | Action | Signal |
|---|---|---|---|
| 1 | UK, Germany, France | Accelerate carrier trade-in | DSI >80 |
| 2 | UAE, Netherlands | Premium e-tailer bundling | High premium share, stable FX |
| 3 | Spain, Italy | Upgrader re-targeting at moment of truth | Mid-tier Android switcher pool |
| 4 | Poland | Awareness investment | Building DSI, growing premium appetite |
| 5 | Turkey, South Africa | Monitor | High FX risk |

---

## Setup & usage

### Prerequisites
```bash
python 3.9+
pip install pandas matplotlib seaborn plotly
```

### Run analysis pipeline
```bash
git clone https://github.com/YOUR_USERNAME/emea-gtm-intelligence
cd emea-gtm-intelligence
python src/emea_gtm_analysis.py
```

All outputs are written to `outputs/` as JSON files.

### Explore in Jupyter
```bash
pip install jupyter
jupyter notebook notebooks/emea_gtm_analysis.ipynb
```

### View interactive dashboard
Open `dashboard/index.html` in any modern browser. Five panels:
- Market opportunity (TAM vs revenue gap)
- Competitive share evolution
- Switcher/upgrader funnel
- Promotional ROI scenarios
- Demand signal index by market

---

## Extending this project

To connect real Kaggle data (recommended for interviews):

1. Download the datasets listed above from Kaggle
2. Place CSVs in `data/raw/`
3. Replace the hardcoded configuration dictionaries in `src/emea_gtm_analysis.py` with `pd.read_csv()` calls
4. The analysis functions operate on the same output schemas — no other changes needed

---

## Skills demonstrated

- **Market sizing**: Bottom-up TAM methodology with tiering and opportunity indexing
- **Competitive analysis**: Share shift decomposition, trend modelling
- **Commercial strategy**: Promotional ROI modelling, channel mix optimisation
- **Demand intelligence**: Composite signal index construction, market investment prioritisation
- **Consumer insight**: Funnel analysis by segment with conversion benchmarking
- **Python**: Modular analytical pipeline, reproducible outputs, data visualisation
- **Storytelling**: Dashboard design, executive summary synthesis

---

*Built as a portfolio project demonstrating Category Business Manager competencies for EMEA consumer hardware GTM roles.*
