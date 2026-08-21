# DexCom, Inc. (NASDAQ: DXCM) — DCF Valuation Model

A driver-based discounted cash flow model built from scratch, using DexCom's public 10-K filings, as a portfolio project for FP&A roles.

**Implied share price: $45.49** | Current market price: ~$89.75 | Implied downside: ~(49%)

---

## Why DexCom

I wanted a project that would demonstrate operational, driver-based forecasting - something closer to what FP&A teams build, rather than a pure Wall Street-style valuation. DexCom is a medtech/consumables business (continuous glucose monitors) with:

- Clean, disclosed geographic revenue segmentation (US vs. International)
- Real, quantifiable operating drivers (R&D and SG&A as distinct cost lines, working capital tied to insurance/DME billing cycles)
- A live, current tension between strong recent growth and disclosed structural risk (Medicare reimbursement changes starting 2028), giving the model a real point of view to defend, not just a mechanical exercise

---

## Model structure

Built as a 9 tab Excel workbook, fully linked end to end. Every output flows from the assumptions tab - there are no hardcoded numbers downstream.

Tabs are as follows:

- Assumptions - Every driver and input, single source of truth for the model
- Revenue Build - US + International revenue, driven by geographic growth assumptions
- Opex & EBITDA - Gross margin, R&D, SG&A → EBITDA/EBIT 
- Capex & D&A - Capital spending and depreciation schedule, incl. gross PP&E roll-forward 
- Working Capital - Inventory, receivables, payables → change in NWC
- Unlevered FCF - EBIT, tax, D&A, capex, and NWC combine into free cash flow
- WACC - CAPM cost of equity + after-tax cost of debt, weighted 
- DCF & Valuation - Discounts explicit FCF + terminal value to an implied share price 
- Sensitivity - Two data tables: WACC × Terminal Growth, and Revenue Growth × Exit Multiple 

Historical years (FY2023A-FY2025A) are hardcoded from DexCom's 10-K filings. Forecast years (FY2026E–FY2030E) are formula-driven off the Assumptions tab.

---

## Key judgment calls

A DCF is only as good as the assumptions behind it. These are the calls that most shaped the output, in order of impact:

- **Reimbursement risk.** DexCom's own 10-K discloses upcoming Medicare competitive bidding changes (effective 2028) expected to pressure CGM(continuous glucose monitoring) reimbursement - a real headwind acknowledged by the company. This informed a more conservative growth deceleration in the back half of the forecast, rather than assuming current growth rates persist indefinitely.

- **Terminal value cross-check.** The Gordon Growth method implies a terminal EV/EBITDA multiple of ~8x, well below DexCom's current trading multiple of ~16.5x. Rather than reverse-engineering assumptions to close that gap, I built a second sensitivity table using an exit multiple terminal value method (yielding ~$78 at DexCom's current multiple) to make the disagreement between methods explicit rather than hidden. This is arguably the most important finding in the model: **the two standard terminal value approaches disagree by nearly 2x**, and the gap is driven almost entirely by how conservative or a WACC/growth spread you're willing to assume.

- **Beta.** Estimates for DexCom's beta varied significantly by source (0.75–1.56). I used 1.45, the consensus/average across most data providers(Yahoo/Google/etc.) rather than the low outlier. A notably lower beta would compress WACC and close much of the valuation gap versus current market pricing, so this is a genuinely consequential and debatable choice.

- **Cost of debt.** DexCom's disclosed convertible note effective rates (0.5–0.7%) reflect embedded equity-conversion value, not the cost of straight borrowing. I used a market-based proxy (risk-free rate + credit spread, ~5.75%) instead.

- **Working capital data limitation.** DexCom discloses "Accounts payable and accrued liabilities" as a single combined balance sheet line so there is no standalone trade payables figure. The working capital schedule reflects this combined balance rather than an assumed split of accounts payable.

---

## Why the model lands below the current market price

At $45.49, this model's output sits meaningfully below where DexCom actually trades (~$89.75). I chose not to adjust assumptions to close that gap artificially. A few honest reasons the gap exists:

- My WACC (~10.29%) is higher than several other published DCF estimates I benchmarked against (e.g., one automated model uses ~8.2%), largely a function of the beta and terminal-value methodology choices above.
- My revenue growth deceleration is more conservative than current sell-side consensus, which appears to price in durable, elevated growth for longer than a standard mature-company fade would assume.
- The market is likely pricing in other drivers - particularly Stelo's ramp and continued international expansion - that a single base-case DCF cannot capture succinctly.

The Sensitivity tab quantifies exactly how much each of these levers moves the output, rather than providing just one "correct" answer.

---

## Files

- `Dexcom DCF Project.xlsx` — full model
- Sensitivity heat maps and Summary Dashboard tab give a one-page view of the model without needing to open every tab

---

## What I'd do differently with more time

- Fully re-derive the exit-multiple sensitivity table off the live revenue build, rather than treating it as an illustrative EBITDA-scenario flex
- Pull a cleaner multi-year AP figure if DexCom ever discloses it separately from accrued liabilities
- Build out a light 3-statement linkage (a full PP&E roll-forward is already in the model; a full balance sheet/debt schedule is the natural next step)

