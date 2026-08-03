# CAC × LTV — Media Investment Optimization

## Context
Analytics project applied to a large multi-unit healthcare diagnostics company (Brazil). Connects **Customer Acquisition Cost (CAC)** by paid media platform with **patient Lifetime Value (LTV)** to answer: *where should investment increase or decrease?*

## Business problem
Media teams often allocate budget based on CPC/CPL alone — without checking whether the acquired patient generates enough recurring revenue to justify the acquisition cost. This can lead to cutting channels that are profitable long-term (but expensive short-term) while keeping cheap channels that bring low-value patients.

## Methodology
- SQL pipeline (BigQuery) with 5 chained CTEs: media cost by platform/brand → acquisition cohort (deduplicated with `QUALIFY ROW_NUMBER()` to prevent double-counting patients) → CAC → cumulative LTV at 3/6/12/24-month milestones → LTV:CAC Ratio and Payback Period.
- **Data engineering fixes applied:** cohort size computed before joining the brand dimension (prevents over-counting); cumulative LTV computed with `SUM() OVER (... ROWS BETWEEN UNBOUNDED PRECEDING)` correctly partitioned to avoid numerator/denominator inflation.
- Health semaphore: 12-month LTV:CAC Ratio ≥ 3 (healthy) | ≥ 2 (watch) | < 2 (critical).
- Automated investment recommendations by (platform × brand).

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)` · `google-cloud-bigquery` / `bigquery-storage`

## Outputs
- CAC × LTV table across time milestones
- Retention × LTV matrix by platform and brand
- Channel efficiency ranking (LTV:CAC Ratio)
- Payback period diagnostic

## Illustrative example (fictional data)
| Platform | Brand | CAC | 12m LTV | LTV:CAC Ratio | Status |
|---|---|---|---|---|---|
| Paid Search | Brand A | $180 | $620 | 3.4x | 🟢 Healthy |
| Paid Social | Brand B | $145 | $210 | 1.4x | 🔴 Critical |

*Numbers are illustrative only and do not represent real data from any company.*

## So What?
Flagging (platform × brand) combinations below a 2x LTV:CAC Ratio enables reallocating budget toward channels with proven long-term returns, rather than optimizing for immediate acquisition cost alone.
