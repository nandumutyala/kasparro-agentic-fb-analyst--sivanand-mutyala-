# Facebook Ads Performance Analysis Report

## Objective
The objective of this assignment is to build an agentic system that can diagnose changes in Return on Ad Spend (ROAS), identify the underlying drivers of those changes, and generate actionable creative recommendations grounded in historical ad performance data.

The focus is on clarity of reasoning, modular design, and production-style applied AI thinking.

---

## Dataset Overview
The dataset (`synthetic_fb_ads_undergarments.csv`) contains synthetic Facebook Ads performance data for an undergarments brand, including:
- Engagement metrics (impressions, clicks, CTR)
- Conversion metrics (purchases, conversion rate, ROAS)
- Spend information
- Creative attributes (creative type and messaging)
- Audience segmentation (Broad, Lookalike, Retargeting)
- Platform and country context

The dataset is treated as a historical snapshot for analysis.

---

## Methodology

### Agentic Workflow
The solution is structured as a modular, agent-inspired pipeline:

#### 1. Planner
The planner identifies high-impact analytical dimensions:
- Creative Type
- Audience Type
- Time (ROAS trends)

#### 2. Analyzer
Deterministic aggregation is performed using pandas to compute:
- Average CTR
- Average Conversion Rate
- Average ROAS
- ROAS trends over time using the date dimension

This ensures transparency and reproducibility while avoiding LLM usage for numerical computation.

#### 3. Diagnostic Layer
ROAS is analyzed over time by comparing early and later periods.
Performance shifts are linked to:
- Increased presence of underperforming video creatives
- Differences in audience efficiency, particularly between broad and retargeting segments

#### 4. Insight Generator
Numerical summaries are translated into structured insights describing:
- Overall account performance
- Creative-level strengths and weaknesses
- Audience-level performance drivers

Insights are stored in `insights.json`.

#### 5. Creative Generator
Based on identified weaknesses, new creative recommendations are generated to address:
- Low-performing video formats
- Inefficient broad audience targeting
- Opportunities to scale high-performing UGC and Image creatives

These recommendations are stored in `creatives.json`.

---

## Key Findings

### Creative Performance
- **UGC creatives** deliver the strongest performance, combining high ROAS with strong CTR.
- **Image creatives** perform efficiently and provide clarity of value.
- **Video creatives** underperform relative to other formats, showing lower CTR and ROAS.

### Audience Performance
- **Retargeting audiences** are the primary profitability drivers due to higher conversion rates.
- **Lookalike audiences** offer a balance of scale and efficiency.
- **Broad audiences** exhibit weaker performance and require stronger messaging and hooks.

### ROAS Trends
ROAS trends over time indicate that performance changes are driven primarily by:
- Creative underperformance in video formats
- Audience saturation in broader targeting segments

---

## Strategic Recommendations
- Scale UGC and Image creatives for retargeting and lookalike audiences.
- Treat retargeting as the primary ROAS engine.
- Redesign video creatives with shorter, benefit-focused messaging.
- Apply learnings from top-performing creatives to guide prospecting experiments.

---

## Limitations & Future Improvements
- The dataset is synthetic and may not capture all real-world dynamics.
- Live LLM calls were omitted due to execution constraints.
- Future enhancements could include automated A/B testing feedback, live LLM-driven reasoning, and budget optimization agents.

---

## Conclusion
This project demonstrates a practical agentic approach to marketing performance analysis. By separating planning, analysis, diagnosis, and generation, the system clearly explains ROAS changes and produces actionable, data-grounded recommendations aligned with real-world decision-making.
