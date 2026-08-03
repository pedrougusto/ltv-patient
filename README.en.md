# Patient Return/Churn Analysis Across Multiple Cuts

## Context
Churn analysis for a healthcare diagnostics company, answering which channel, campaign, product, payer type, and age group retains vs. loses the most patients.

## Business question
Where is churn concentrated? Which campaigns/products/payers deserve priority retention attention?

## Methodology
- Classifies patients into return categories (e.g., returned quickly, returned late, no return).
- Percentage distribution by acquisition channel, campaign (Top 20 + "Other"), product group, payer type, and age group.
- 100% stacked bar charts sorted by "no return" rate for immediate visual prioritization.

## Stack
`Python` · `pandas` · `matplotlib`

## So What?
Sorting each cut by churn rate quickly surfaces the "worst offenders" (e.g., a specific campaign or product group with churn far above average) for targeted action — rather than treating retention as a generic problem.
