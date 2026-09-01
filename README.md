# Finance & Analytics Portfolio
**Jackson Kerins**  
MSF Candidate — San Diego State University | B.S. Managerial Economics, UC Davis  
[LinkedIn](https://linkedin.com/in/jacksonkerins) · San Diego, CA

---

## About This Portfolio

This repository contains financial models and analytics projects built to demonstrate FP&A-relevant technical skills. Each project uses real company data or realistic business scenarios and is documented with full methodology, assumptions, and key findings.

---

## Projects

### 1. Fleet Asset Replacement Cost-Benefit Analysis
**[View Project →](./01-cost-benefit-analysis)**

A multiscenario 5 year CBA model evaluating four strategic options for a 2,500 unit enterprise mobile device fleet with an expired warranty contract. Built to support a real customer facing decision in a $27M ARR business unit.

**What it models:**
- Four options across contract reenrollment, repair, and replacement strategies - each with distinct coverage windows, failure risk profiles, and cost structures
- Year-by-year cost build incorporating contract pricing, out of pocket repair exposure, trade-in recovery, and aging device failure rate acceleration modeled as a chained survival formula
- Productivity loss from device downtime - modeled separately for units under warranty (1.5-day OneCare advance exchange) vs. unprotected units (10-day out-of-contract repair cycle), quantifying the real cost of running an unprotected fleet at scale
- Dynamic failure rate step-up (+2%/yr) to simulate EOL device behavior as the aging fleet accelerates toward failure
- Executive Summary tab written as a one page decision brief for a nontechnical stakeholder, including a side by side risk comparison and risk adjusted recommendation

**Key finding:** The lowest cost option on paper (replace dead units only, $3.49M over 5 years) carries $2.38M in uncontrolled productivity loss (68% of its total cost) driven by 2,125 unprotected devices averaging 10 days of downtime per failure. Full fleet replacement costs $1.06M more but reduces productivity loss exposure to $238K and eliminates all out of pocket repair spend for 5 years.

**Key skills demonstrated:** Multiscenario financial modeling · Aging/decay chain formulas · Productivity loss quantification · IFERROR error handling · Absolute cell referencing · Executive summary writing · FP&A decision support

**Tools:** Microsoft Excel

---

### 2. DexCom, Inc. (NASDAQ: DXCM) — DCF Valuation Model
**[View Project →](./02-dcf-model)**

A driver based discounted cash flow model built from scratch using DexCom's public 10-K filings. Structured as a 9 tab Excel workbook, fully linked end to end with no hardcoded numbers downstream of the assumptions tab.

**Implied share price: $45.49** | Market price at time of build: ~$89.75 | Implied downside: ~(49%)

**What it models:**
- Revenue build driven by geographic segmentation (US vs. International) with separate growth assumptions for each segment
- Full operating cost build: gross margin, R&D, SG&A → EBITDA/EBIT across FY2023A–FY2030E
- Capex and depreciation schedule including a gross PP&E roll forward
- Working capital schedule (inventory, receivables, payables --> change in NWC)
- Unlevered free cash flow build combining EBIT, taxes, D&A, capex, and NWC changes
- WACC derived via CAPM cost of equity + after-tax cost of debt, weighted to capital structure
- Terminal value using both Gordon Growth and exit multiple methods — disagreement between approaches made explicit in the model
- Two sensitivity tables: WACC × Terminal Growth Rate, and Revenue Growth × Exit Multiple

**Key judgment calls:** Conservative revenue deceleration in the back half of the forecast reflects DexCom's own disclosed Medicare competitive bidding risk (effective 2028). Beta set at 1.45 (consensus across Yahoo, Google, and major data providers) rather than the low outlier of 0.75. This was a consequential choice that materially compressed the implied price. The Gordon Growth terminal value implies ~8x EV/EBITDA vs. DexCom's current trading multiple of ~16.5x; a second sensitivity table using an exit multiple approach yields ~$78, making the ~2x disagreement between methods explicit and quantified.

**Key skills demonstrated:** Driver-based financial modeling · 3-statement linkage · WACC/CAPM · DCF and terminal value · Sensitivity analysis · Assumption documentation · Analytical judgment on contested inputs

**Tools:** Microsoft Excel

---

### 3. Costco Wholesale (NASDAQ: COST) — Financial Performance Dashboard
**[View Project →](./03-power-bi)** · **[Live Dashboard](https://app.powerbi.com/view?r=eyJrIjoiZjM0ZTQ2NTktOTEwMS00NGQ1LWJiNTYtNThlY2I5Y2U0ZGMzIiwidCI6Ijk2NzNlOWE4LWFhNTctNDQ2MS05MzM2LTVmZDNmMDAzNGUxOCIsImMiOjZ9)**

An interactive 4-page Power BI dashboard analyzing Costco's financial performance from FY2021–FY2025, covering profitability, income statement structure, and balance sheet health. Built on data compiled from Costco's audited 10-K filings via SEC EDGAR.

**Business question:** How has Costco's financial performance evolved over the past five years, and what does that reveal about the sustainability of its growth?

**What it covers:**
- **Executive Summary** — FY2025 KPI snapshot (Revenue, Net Margin, ROE, Current Ratio) with 5-year Revenue vs. Net Income trend
- **Profitability Deep Dive** — Revenue-to-Net-Income waterfall bridge (FY2025) and 5-year margin trend analysis (Gross, Operating, Net)
- **Balance Sheet & Liquidity** — Balance sheet composition (Liabilities vs. Equity) with liquidity and leverage trends (Current Ratio, Total Liabilities-to-Equity)

**Technical build:**
- Power Query used to clean and unpivot wide-format 10-K financials into a long/tall fact table
- Star schema data model with a fact table (`FactFinancials`) and date dimension (`DimDate`)
- 15+ DAX measures covering profitability margins, liquidity ratios, leverage ratios, and a signed waterfall measure for bridge chart logic
- Multi page layout with consistent navigation, dynamic slicers, and filtering

**Key findings:** Revenue grew from $196B to $275B over the period while net margin expanded from 2.6% to 2.9% showing disciplined cost management in an inflationary environment. COGS consistently consumes ~87% of revenue, consistent with Costco's low margin/high volume model. Total D/E declined from 2.3x to 1.7x while the current ratio held above 1.0, indicating balance sheet strengthening alongside continued growth.

**Key skills demonstrated:** Power Query · DAX · Star schema data modeling · Financial statement analysis · Dashboard design · KPI visualization · Bridge/waterfall charts

**Tools:** Power BI, Excel

---

## Skills

| Category | Tools & Skills |
|---|---|
| Financial Modeling | DCF, Cost-Benefit Analysis, Scenario Modeling, Sensitivity Analysis |
| Excel | Advanced formulas, IFERROR, absolute referencing, multi-sheet linked models |
| Data Visualization | Power BI, DAX, Power Query, Excel charts |
| ERP / Systems | NetSuite, Salesforce |
| Currently Building | SQL, Python (pandas) |

---

## Background

I'm transitioning into FP&A from an operations and account management background, currently pursuing a Master of Science in Finance at San Diego State University (expected 2028). My professional experience includes managing operations within a $27M ARR business unit at MTS, where I worked closely with internal finance teams on reporting, vendor management, and cost analysis.

This portfolio reflects the technical skills I'm building to complement that business experience and make the move into an analyst role.

---

*Projects are updated regularly as new work is completed. See individual project folders for full documentation, methodology, and model files.*
