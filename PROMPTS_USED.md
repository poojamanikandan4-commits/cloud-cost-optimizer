# Prompts Used During Development

**Project:** Cloud Cost Optimizer AI Agent

---

## Prompt 1 — Project Scaffold
```
Generate a Python project structure for a cloud cost optimizer tool using Streamlit,
SQLite, and Pandas. Include an agent loop that runs: Analyze → Evaluate → Recommend
→ Verify → Final Report. Use only free/open-source tools.
```
**Result:** Got the folder structure, file list, and initial config.py.

---

## Prompt 2 — Detection Logic
```
Write a Python function that takes a pandas DataFrame of cloud resources and detects:
1. Idle resources (CPU < 5%)
2. Oversized instances (CPU between 5% and 20%)
3. Storage waste (storage utilization < 20%)
Each function should return a filtered DataFrame.
```
**Result:** Generated cost_analyzer.py with detect_idle_resources(), detect_oversized_instances(), detect_storage_waste().

---

## Prompt 3 — Agent Loop
```
Implement a Python class CloudCostAgent with a run() method that loops through
5 steps: analyze, evaluate, recommend, verify, final_report. Loop should repeat
until confidence >= 0.75 or max 5 iterations. Add logging at each step.
```
**Result:** Generated agent.py with iteration tracking and confidence scoring.

---

## Prompt 4 — Streamlit Dashboard
```
Create a Streamlit app with:
- Dark theme with IBM Plex fonts
- File upload for CSV
- 5 KPI metric cards (total cost, resources, idle, oversized, storage waste)
- A savings banner in green
- Donut chart for cost by resource type
- Bar chart for cost by region
- Recommendation cards with priority color coding (red/orange/green)
- Agent log trace expander
- PDF download button
```
**Result:** Generated app.py with CSS, layout, and all components.

---

## Prompt 5 — External API Integration
```
Write a Python module that fetches live USD exchange rates from a free API
(no API key required). Include a fallback dictionary if the API is unreachable.
Add a convert_cost(amount_usd, target_currency, rates) function.
```
**Result:** Generated api_client.py using exchangerate.host.

---

## Prompt 6 — SQLite Schema
```
Design a SQLite schema for storing cloud cost analysis runs. I need:
1. A table for analysis runs (metadata: file, date, totals)
2. A table for individual recommendations linked to runs
3. A table for agent step logs linked to runs
Write Python functions to insert and query each table.
```
**Result:** Generated database.py with three tables and CRUD functions.

---

## Prompt 7 — PDF Report
```
Using fpdf2, generate a PDF report that includes:
- Executive summary with key metrics
- Issues detected section
- Cost by region table
- Recommendations list with color-coded priority labels
Include a header and footer on each page.
```
**Result:** Generated report_generator.py with CostReport class extending FPDF.

---

## Prompt 8 — Unit Tests
```
Write pytest unit tests for the cost_analyzer.py module covering:
- load_and_clean handles missing values and strips whitespace
- detect_idle_resources returns correct rows
- detect_oversized_instances excludes idle and active resources
- detect_storage_waste only flags storage resource types
- compute_summary returns correct totals and counts
- Edge case: empty DataFrame
- Edge case: DataFrame with None values
```
**Result:** Generated tests/test_analyzer.py with 11 test cases.

---

## Prompt 9 — Debugging fpdf2
```
I'm getting TypeError: ln() got an unexpected keyword argument 'h' when using fpdf2.
I'm calling self.cell(..., ln=1). How do I fix this for fpdf2?
```
**Result:** AI explained the new fpdf2 API using new_x and new_y parameters.

---

## Prompt 10 — README
```
Write a GitHub README for a cloud cost optimizer Streamlit app. Include:
badges, features list, architecture diagram in ASCII, installation steps,
CSV format table, screenshots section (placeholder), and external API section.
```
**Result:** Generated README.md with full documentation.
