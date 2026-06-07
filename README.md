# ☁️ Cloud Cost Optimizer AI Agent

> An AI-powered cloud spend analysis tool that automatically detects idle resources, oversized instances, and storage waste — and recommends actionable savings.

!\[Python](https://img.shields.io/badge/Python-3.11+-blue)
!\[Streamlit](https://img.shields.io/badge/Streamlit-1.35-red)
!\[SQLite](https://img.shields.io/badge/SQLite-3-green)
!\[License](https://img.shields.io/badge/License-MIT-yellow)

\---

## Demo Video

Watch the demo here:
[Click for Demo Video](https://drive.google.com/file/d/1uvLa-uPIwEOAAzcxdQagUePUukZvRpvT/view?usp=drivesdk)

## 🚀 Features

* **Agent Loop**: Analyze → Evaluate → Recommend → Verify → Final Report
* **Idle Resource Detection**: Flags compute instances with <5% CPU utilization
* **Oversized Instance Detection**: Identifies under-utilized compute (5–20% CPU)
* **Storage Waste Detection**: Highlights storage resources below 20% utilization
* **External API Integration**: Live currency exchange rates via exchangerate.host
* **Multi-Currency Support**: USD, INR, EUR, GBP, CAD, AUD, JPY, SGD
* **SQLite History**: Every analysis run stored persistently
* **PDF Reports**: Downloadable PDF with full recommendations
* **Streamlit Dashboard**: Interactive charts and filterable recommendations

\---

## 🗂️ Architecture

```
cloud-cost-optimizer/
├── app.py                  ← Streamlit dashboard (UI)
├── agent.py                ← Agent loop orchestrator
├── cost\_analyzer.py        ← Detection logic (idle, oversized, waste)
├── recommendation\_engine.py← Recommendation generation
├── database.py             ← SQLite persistence layer
├── api\_client.py           ← External API (exchange rates)
├── report\_generator.py     ← PDF report generation
├── utils.py                ← Validation \& helpers
├── config.py               ← All thresholds and settings
├── sample\_data/
│   └── cloud\_costs.csv     ← Demo billing data (30 resources)
├── tests/
│   ├── test\_analyzer.py    ← Unit tests for analysis logic
│   └── test\_agent.py       ← Unit tests for agent loop
├── reports/                ← Auto-created PDF output folder
├── requirements.txt
├── README.md
├── AI\_USAGE\_NOTE.md
├── PROMPTS\_USED.md
└── TEST\_CASES.md
```

### Agent Loop Detail

```
┌──────────┐    ┌──────────┐    ┌───────────┐    ┌────────┐    ┌──────────────┐
│  ANALYZE │───▶│ EVALUATE │───▶│ RECOMMEND │───▶│ VERIFY │───▶│ FINAL\_REPORT │
└──────────┘    └──────────┘    └───────────┘    └────────┘    └──────────────┘
     ▲                                                                  │
     │          confidence < 75%? loop back                             │
     └──────────────────────────────────────────────────────────────────┘
```

\---

## 🛠️ Installation

### Prerequisites

* Python 3.11 or higher
* pip

### Step-by-step

```bash
# 1. Clone or create the project folder
git clone https://github.com/YOUR\_USERNAME/cloud-cost-optimizer.git
cd cloud-cost-optimizer

# 2. Create virtual environment
python -m venv venv

# 3. Activate virtual environment
# Windows:
venv\\Scripts\\activate
# Mac/Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Run the app
streamlit run app.py
```

The app opens at **http://localhost:8501**

\---

## 🧪 Running Tests

```bash
# Make sure venv is activated
pytest tests/ -v
```

\---

## 📋 CSV Format

Your billing CSV must have these columns:

|Column|Type|Description|
|-|-|-|
|`resource\_id`|string|Unique resource identifier|
|`resource\_type`|string|`ec2`, `s3`, `ebs`, `rds`, etc.|
|`region`|string|Cloud region|
|`monthly\_cost\_usd`|float|Monthly cost in USD|
|`cpu\_utilization\_pct`|float|CPU usage percentage (0–100)|
|`storage\_utilization\_pct`|float|Storage usage percentage (0–100)|

\---

## 📸 Screenshots

> \*See demo video for full walkthrough\*

1. **Dashboard with Upload** — File uploader and sample data loader
2. **Agent Running** — Step-by-step progress with live log trace
3. **Summary Metrics** — 5 KPI cards + savings banner
4. **Cost Charts** — Donut chart by type, bar chart by region
5. **Recommendations** — Priority-filtered cards with savings per resource
6. **Agent Log Trace** — Full iteration log per step
7. **History Page** — All past runs from SQLite
8. **PDF Report** — Downloaded PDF with executive summary

\---

## 🔑 External API

\## 🔗 External Integrations



\### 1. Exchange Rate API

Used for real-time currency conversion and multi-currency cloud cost reporting.



\*\*Features\*\*

\- USD to INR conversion

\- USD to EUR conversion

\- USD to GBP conversion

\- Live exchange rate fetching



\### 2. GitHub REST API

Used to fetch repository analytics from public GitHub repositories.



\*\*GitHub API Features\*\*

\- ⭐ Repository Stars

\- 🍴 Fork Count

\- 🐞 Open Issues

\- 🕒 Last Updated Date



\*\*Example Repository\*\*

streamlit/streamlit




\---

## 📬 Contact

Pooja M M - poojavsb074@gmail.com
Sandhya K - sandhyakannan61@gmail.com
Shijitha Jenifer J - shijithajenifer2005@gmail.com

