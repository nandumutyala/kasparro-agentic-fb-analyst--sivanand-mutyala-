# Kasparro — Agentic Facebook Performance Analyst

## Overview
This project implements a **self-directed agentic system** to analyze Facebook Ads performance data, diagnose changes in ROAS over time, identify key performance drivers, and propose data-grounded creative recommendations.

The system is designed with an **LLM-first, production-style mindset**, focusing on reasoning clarity, modular execution, and traceable outputs rather than complex model training or visual dashboards.

The pipeline follows a **Planner → Analyzer → Diagnostic → Generator** workflow.

---

## Quick Start
This project was developed and executed using **Google Colab**.

### Requirements
- Python **>= 3.10**
- pandas

(Optional) LLM APIs such as Gemini or OpenAI can be integrated in production.

### How to Run
1. Open `analysis_notebook.ipynb` in Google Colab.
2. Upload `synthetic_fb_ads_undergarments.csv`.
3. Run the notebook from top to bottom.

All outputs will be generated automatically.

---

## Dataset
**File:** `synthetic_fb_ads_undergarments.csv`

The dataset contains synthetic Facebook Ads performance data, including:
- Engagement metrics (impressions, clicks, CTR)
- Conversion metrics (purchases, conversion rate, ROAS)
- Spend information
- Creative attributes (creative type, creative messaging)
- Audience segmentation (Broad, Lookalike, Retargeting)
- Platform and country metadata

Minimal preprocessing is applied to preserve analytical interpretability.

---

## Agentic Pipeline Design

### 1. Planner
Identifies high-impact analytical dimensions:
- Creative Type
- Audience Type
- Time (ROAS trends)

### 2. Analyzer
Performs deterministic aggregation using pandas:
- Average CTR
- Average Conversion Rate
- Average ROAS
- ROAS trends over time

This ensures numerical calculations remain transparent and reproducible.

### 3. Diagnostic Layer
Analyzes ROAS changes over time and connects them to:
- Creative underperformance (Video vs UGC/Image)
- Audience efficiency differences (Broad vs Retargeting)

### 4. Insight Generator
Transforms numerical summaries into structured, business-ready insights stored in `insights.json`.

### 5. Creative Generator
Generates new ad creative ideas for low-performing segments, stored in `creatives.json`, including:
- Audience targeting
- Creative format
- Hooks, messaging, and CTAs
- Clear rationale grounded in observed performance

---

## Repository Structure

├── synthetic_fb_ads_undergarments.csv
├── analysis_notebook.ipynb
├── insights.json
├── creatives.json
├── report.md
└── README.md



---

## Outputs
- **insights.json** — Performance insights and ROAS drivers
- **creatives.json** — New creative recommendations
- **report.md** — Detailed explanation of analysis and findings

---

## LLM Integration Note
The system is designed to support live LLM-based reasoning (e.g., Gemini or OpenAI).  
Due to external API constraints during execution, this submission uses **deterministic outputs** while preserving the same modular structure expected in a production LLM-powered workflow.

---

## Version
**v1.0**

---

## Self-Review
- ✅ Agentic reasoning flow implemented
- ✅ ROAS diagnosis tied to creative and audience drivers
- ✅ Deterministic and reproducible analysis
- ✅ Actionable creative recommendations generated

