# AI Usage Note

**Project:** Cloud Cost Optimizer AI Agent  
**Challenge:** AI Prototype Challenge — VSB Group  

---

## What AI Helped With

1. **Boilerplate generation** — AI generated the initial project scaffold including file structure, `requirements.txt`, and base Streamlit layout.
2. **Agent loop design** — AI suggested the Analyze → Evaluate → Recommend → Verify → Final Report loop pattern and helped implement the confidence scoring mechanism.
3. **Detection logic** — AI helped write the threshold-based rules in `cost_analyzer.py` for idle, oversized, and storage waste detection.
4. **SQL schema design** — AI suggested the three-table schema (analysis_runs, recommendations, agent_logs) for SQLite persistence.
5. **PDF generation** — AI helped implement `fpdf2` layout with colored priority rows and page headers/footers.
6. **CSS styling** — AI generated the dark-theme Streamlit CSS with IBM Plex fonts and metric card components.
7. **Unit test structure** — AI wrote the pytest fixtures and test cases covering happy path, edge cases (empty data, null values), and boundary conditions.
8. **Plotly charts** — AI provided the donut and bar chart configurations with dark transparent backgrounds.
9. **README structure** — AI generated the markdown README with architecture diagram, badge shields, and installation steps.

---

## What AI Got Wrong

1. **fpdf2 API** — AI initially used the `fpdf` (v1) API style (`ln=1` parameter), which is not compatible with `fpdf2`. Required manual correction to use `new_x="LMARGIN", new_y="NEXT"`.
2. **Streamlit session state** — AI forgot to check `st.session_state` keys before accessing them, causing `KeyError` on first load. Required adding `.get()` with defaults.
3. **Exchange rate API URL** — AI suggested `openexchangerates.org` which requires an API key on the free tier. Switched to `exchangerate.host` which is truly free.
4. **SQLite thread safety** — AI initially suggested a global connection object, which fails with Streamlit's multi-thread model. Corrected to create a new connection per function call.
5. **Confidence calculation** — AI's first version could produce division-by-zero when the recommendations list was empty. Required an explicit guard clause.
6. **Test isolation** — AI-generated tests initially shared a database file, causing interference between test runs. Fixed by using in-memory or temp databases.

---

## Best Prompts Used

See `PROMPTS_USED.md` for the full list of prompts used during development.

---

## Time Spent Using AI

| Task | Estimated AI Contribution |
|------|--------------------------|
| Architecture design | 60% |
| Writing code | 70% |
| Debugging | 50% |
| Documentation | 80% |
| Testing | 65% |
