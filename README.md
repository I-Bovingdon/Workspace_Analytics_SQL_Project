# Enterprise Sales & Business Performance Analytics with SQL

> Business-oriented SQL analytics project focused on commercial performance and strategic decision-making across regions, industries, and product categories.

---

## Project Overview

This project delivers business performance analysis using SQL over a commercial sales database, simulating real-world BI scenarios found in enterprise environments.

The objective is to extract **actionable business insights** related to revenue, profitability, customer behavior, regional performance, and sales forecasting — supporting strategic decision-making at the commercial and financial leadership level.

---

## Business Questions Solved

- Which customer accounts generate the highest revenue and margin by product category?
- Which regions and countries drive the strongest commercial performance?
- Which industries are closest to closing high-value deals, and where does profitability stand?
- Are sales forecasts for 2022 aligned with 2021 actual performance?
- Which region–industry combinations yield the highest and lowest profit margins?
- Where should the company prioritize future investment and resource allocation?

---

## Technologies Used

- SQL (aggregations, window functions, conditional logic, multi-table joins)
- Relational Databases
- KPI Analysis & Profitability Metrics
- Business Intelligence & Data Visualization
- Sales Forecasting & Variance Analysis

---

## Analysis Portfolio

### 1. Customer Account Performance — Product Category Breakdown

**Business Context:** The commercial leadership team requires a detailed performance breakdown of account **Adabs Entertainment** for FY2020, covering all revenue streams (maintenance, product, parts, and support), units sold, and total profit.

[SQL QUERY → Query01.sql](sql/Query01.sql)

![Revenue and Profit by Product Category — Adabs Entertainment 2020](images/image01.png)

**Business Insight**

Chairs and Electronics both delivered profit margins of approximately **33% and 36%** respectively — a notably similar performance despite the structural differences between product lines. This consistency may reflect standardized pricing or cost structures across categories.

> **Recommended action:** Benchmark these margins against comparable accounts to assess whether current profitability levels are competitive or represent an optimization opportunity.

---

### 2. Regional Sales Performance — APAC vs. EMEA Country Comparison

**Business Context:** The international expansion team requires a cross-country performance comparison across the **APAC and EMEA regions** to identify high-potential markets and establish regional benchmarks for strategic investment decisions.

[SQL QUERY → Query02.sql](sql/Query02.sq2)

![Country Performance — APAC vs EMEA](images/image02.png)
![Regional Performance Chart](images/image02g.png)

**Business Insight**

APAC markets demonstrate significantly stronger revenue and profitability compared to EMEA, with **Australia and Singapore** as the top-performing countries. This suggests higher market maturity, stronger pricing dynamics, or greater operational efficiency in those markets.

Despite fewer countries, APAC's combined average profit contribution reaches parity with EMEA — both regions converge around **$3,390,000** in total average profit, as confirmed below.

[SQL QUERY — Total Average Profit: EMEA + APAC → Query02b.sql](sql/Query02b.sql)

![Combined Region Profit Verification](images/image02b.png)

> **Data quality flag:** The EMEA region holds **9 registered countries** in the ACCOUNTS table, but only 8 appear in the sales analysis. **United Kingdom (UK)** has 4 registered accounts with zero recorded sales — a gap that warrants investigation before any go-to-market strategy for that market.

---

### 3. Industry Profitability Analysis — High-Value Pipeline (Commit Stage)

**Business Context:** The strategic sales team needs to identify which industries generate the highest profit among accounts in the **Commit stage** (near-close deals) with a forecast exceeding **$500,000**. Industries are classified as *High* (profit > $1M) or *Normal*.

[SQL QUERY → Query03.sql](sql/Query03.sql)

![Industry Profitability — Commit Stage Accounts](images/image03.png)
![Industry Profitability Chart](images/image03g.png)

**Business Insight**

The **Financial sector is not meeting the $500K forecast threshold** in the Commit pipeline — a critical flag for the sales team. This underperformance may reflect deal slippage, longer-than-expected sales cycles, or misaligned forecasting at the account level.

> **Recommended action:** Prioritize pipeline review for Financial sector accounts in Commit stage to assess deal health and adjust revenue projections accordingly.

---

### 4. Forecast vs. Actual Revenue Analysis — Category-Level Trajectory

**Business Context:** The finance leadership requires a consolidated view comparing **FY2021 actual profits** against **FY2022 forecasted profits** by product category, along with sales cycle velocity indicators (oldest and most recent open opportunities per category).

[SQL QUERY → Query04.sql](sql/Query04.sql)

![Forecast vs Actual by Category](images/image04.png)
![Forecast vs Actual Chart](images/image04g.png)

**Business Insight**

Across all 4 product categories, the minimum opportunity age is **2–3 days**, indicating healthy short-cycle deal activity. However, **3 out of 4 categories** contain opportunities open for over **365 days** — a significant operational risk.

> **Recommended action:** Conduct a pipeline audit on all opportunities exceeding 12 months. Long-stalled deals distort revenue forecasts and create planning inefficiencies in inventory, spare parts, and technical support resourcing. Each open deal should be either moved to close or formally disqualified.

---

### 5. Strategic Profitability Study — Region × Industry Cross-Analysis

#### Objective

Identify which **region–industry combinations** yield the highest and lowest profit margins, enabling the commercial leadership team to optimize resource allocation, replicate high-performance strategies, and address underperforming segments.

#### Hypothesis

Regions and industries with the strongest margin profiles should be used as benchmarks. Underperforming combinations may reflect pricing inefficiencies, cost structure issues, or underdeveloped market presence — all correctable with the right strategic lever.

---

#### Exploratory Analysis — Regional KPI Summary

The following query extracts total, minimum, maximum, and average profit alongside margin averages and standard deviation across all 4 regions:

[SQL QUERY → Query05.sql](sql/Query05.sql)

![Regional KPI Summary](images/image05.png)
![Regional KPI Chart](images/image05g.png)

**Key Finding:** **NAM and EMEA** generate the highest absolute profit, while **LATAM significantly underperforms** in volume. Notably, average profit margins are relatively homogeneous across regions — suggesting the profitability gap is driven by **deal volume and market size**, not by pricing or cost efficiency differences.

---

#### Deep Dive — Industry Margin Ranking by Region

Industries are classified by margin performance using the following thresholds:

| Margin | Classification |
|---|---|
| > 38% | 🟢 High |
| 33% – 38% | 🟡 Medium |
| < 33% | 🔴 Low |

[SQL QUERY → Query05b.sql](sql/Query05b.sql)

![Industry Margin by Region](images/image05b.png)
![Industry Margin Chart](images/image05bg.png)

---

#### Strategic Recommendations

**a) Scale high-margin industries into emerging regions (LATAM & APAC)**
Replicating the operational model of sectors with consistently high margins (e.g. Technology, Financial Services) in lower-volume regions can accelerate overall profitability without proportional cost increases.

**b) Optimize underperforming industry–region combinations**
For segments with margins below 33%, a structured review of pricing policies, cost structures, and deal qualification criteria is recommended to improve contribution to total profit.

**c) Investment prioritization**
Sustain commercial momentum in **NAM and EMEA** while designing phased expansion strategies for **LATAM** — focusing on high-margin industries with demonstrated demand signals in adjacent markets.

---

*Analysis conducted on enterprise commercial sales data covering FY2020–2022 across 4 global regions (NAM, EMEA, APAC, LATAM).*


d)	Seguimiento con dashboards dinámicos:
Mantener el monitoreo del beneficio total, margen promedio y su desviación por región e industria, utilizando vistas como BENEF_MARGE_REG para detectar rápidamente desviaciones o nuevas oportunidades.


