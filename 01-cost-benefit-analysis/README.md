# WT64 Fleet — Replacement vs. Repair Cost-Benefit Analysis Model

**Author:** Jackson Kerins  
**Date:** August 2026  
**Tools:** Microsoft Excel  

---

## Overview

This model evaluates four strategic options for a customer whose 2,500 unit Zebra WT64 fleet has passed the end of its original OneCare warranty coverage. 15% of devices have failed and cannot be repaired without reinstating an active contract. The model compares total 5-year cost across all options, incorporating direct repair costs, contract pricing, trade-in recovery, and most critically -- the productivity loss associated with device downtime under each scenario.

This is a portfolio project built to demonstrate financial modeling skills relevant to FP&A and corporate finance roles.

---

## The Business Problem

- **Fleet size:** 2,500 WT64 units purchased 5 years ago
- **Contract status:** Zebra OneCare expired 2024 - all devices currently unprotected
- **Devices lost:** 375 units (15%) have failed and cannot be repaired without a retroactive contract
- **Surviving units:** 2,125 units still operating but unprotected, aging at a 10% annual failure rate accelerating 2% per year
- **Key constraint:** Dead units can only be repaired if the customer retroactively re-enrolls in OneCare, but this comes at a premium rate and leaves limited coverage remaining

---

## The Four Options

| Option | Description |
|---|---|
| **A** | Retroactive OneCare 3-Year enrollment on all units + warranty repair dead devices. 1 year of coverage remaining after enrollment. |
| **B** | Retroactive OneCare 5-Year enrollment on all units + warranty repair dead devices. 3 years of coverage remaining after enrollment. |
| **C** | Replace dead units only with new WT64s + OneCare on replacements. Surviving units receive no coverage. |
| **D** | Replace full fleet with new WT64s + new 5-year OneCare on all units. Full reset of device lifecycle. |

---

## Model Structure

### Tab 1 — Executive Summary
One page decision brief. Includes situation overview, options at a glance, recommendation with rationale, and a side by side risk comparison of Option C vs Option D. Written as a deliverable for a nontechnical decision maker.

### Tab 2 — Cost-Benefit Model
Full 5-year year-by-year cost build for all four options across three cost categories:

**Section 1 — Key Assumptions & Inputs**
All 14 input variables in yellow-highlighted cells. Everything else in the model flows from these inputs. No hardcoded values in the formula rows.

**Section 2 — Year-by-Year Cost Build**
Each option models:
- Contract or purchase costs (Year 1)
- Out-of-pocket repair exposure by year
- Productivity loss from device downtime, modeled separately for units under contract vs. unprotected units
- Trade-in recovery where applicable

**Section 3 — Summary Scorecard**
Ranks all four options by 5 year total cost with year 1 cash outlay, coverage window, failure risk rating, and cost delta vs. lowest option.

---

## Key Modeling Decisions

**Productivity loss inclusion**  
Most fleet cost models stop at direct repair costs. This model adds a productivity loss layer based on the real world difference in repair turnaround time between OneCare (advance exchange, ~1.5 days) and out-of-contract repairs (ship-in process, ~10 days). At $26/hr × 8 hrs/day, this difference is material at fleet scale.

**Split productivity modeling in Option C**  
Option C replaces dead units (covered under new OneCare, modeled at new-device failure rates ~50% of aging rate) and leaves surviving units unprotected (full aging failure rate, 10 day turnaround). These two populations are modeled separately to accurately reflect their different risk profiles.

**Aging failure rate acceleration**  
Rather than using a flat failure rate, the model applies a 2% annual step-up to the surviving fleet's failure rate. This reflects the real-world pattern of increasing failures as devices age beyond their design lifecycle.

**IFERROR throughout**  
All formula cells are wrapped in IFERROR to return $0 instead of errors when input cells are blank, keeping the blank template clean and readable before inputs are entered.

---

## Key Outputs (Reference Model Inputs)

| Option | Yr-1 Cash Outlay | 5-Year Total Cost | Productivity Loss (5-yr) | Rank |
|---|---|---|---|---|
| A — Retro OneCare 3-Yr | $1,566,300 | $3,791,074 | $1,970,633 | 3 |
| B — Retro OneCare 5-Yr | $2,441,300 | $3,680,949 | $1,148,301 | 2 |
| C — Replace Dead Only | $1,232,850 | $3,487,425 | $2,382,000 | 1 |
| D — Replace Full Fleet | $4,351,500 | $4,550,177 | $237,677 | 4 |

**Recommended option: Option D -- Replace Full Fleet + New OneCare**

Option C has the lowest nominal 5 year cost $3,487,4525. However, $2,381,985 of that total (68% of the entire cost) is uncontrolled productivity loss from 2,125 unprotected devices sitting broken for an average of 10 days per failure. Option D's productivity loss is only $237,677 (5% of its total cost) because new devices under OneCare average just 1.5 days to replace. The nominal $1,062,752 premium of Option D over Option C is almost entirely offset by $2,108,656 in avoided downtime costs.							


---

## Assumptions

| Input | Value | Notes |
|---|---|---|
| Fleet size | 2,500 units | |
| % failed | 15% | 375 dead units |
| WT64 replacement price | $1,420/unit | Confirm with Zebra or distributor |
| Trade-in value | $200/unit | Dead devices cannot be traded in |
| OneCare retro rate — 3-yr | $200/unit/yr | Higher than standard; confirm with Zebra rep |
| OneCare retro rate — 5-yr | $190/unit/yr | Confirm with Zebra rep |
| OneCare new rate — 5-yr | $95/unit/yr | Standard new-device rate |
| OOP repair cost | $350/unit | Full depot rate without coverage |
| Base failure rate | 10% (Yr 1) | Typical for 5-yr-old mobile devices; 8-12% range |
| Failure rate step-up | +2%/yr | Conservative aging acceleration |
| Hourly wage | $26/hr | Fully-loaded operator cost |
| Work hours/day | 8 hours | |
| Downtime — under OneCare | 1.5 days | Advance exchange program |
| Downtime — out of contract | 10 days | Ship-in repair cycle |

---

## Skills Demonstrated

- Multiscenario financial modeling in Excel
- 5-year horizon cost build with year-by-year granularity
- Aging/decay modeling using chained survival formulas
- Productivity loss quantification and integration into total cost
- IFERROR error handling for robust template design
- Absolute cell referencing (`$D$20`) for formula consistency across periods
- Executive summary writing; translating model output into a business recommendation

---

## How to Use the Blank Template

1. Open the **Cost-Benefit Model** tab
2. Fill in only the **yellow cells** in Section 1 (rows 9-26)
3. All other cells calculate automatically

Only edit the yellow cells column D of tab 2, as other cells contain formulas that drive the entire model.
