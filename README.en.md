# Cumulative LTV Curves by Channel, Subchannel, and Payer Type

## Context
A set of notebooks/scripts that generate cumulative LTV curves (accumulated revenue per patient over months since acquisition) for a healthcare diagnostics company, cut by acquisition channel, subchannel, and payer type (insurance vs. self-pay).

## Business question
How does patient value evolve over time, and does that evolution differ depending on where the patient was acquired or how they pay?

## Methodology
- BigQuery query: acquisition cohort (first visit as "new", deduplicated with `QUALIFY ROW_NUMBER()`), monthly revenue per patient, cumulative revenue via window function, and average LTV per patient = cumulative revenue / cohort size.
- Payer-type segmentation captured at the moment of acquisition (methodology explicitly documented in the code to avoid ambiguity: payer type can change over a patient's lifetime, but the cohort is defined by payer type at acquisition).
- Reusable aggregation and plotting functions, with automatic end-value annotation on each curve.

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)`

## So What?
LTV curves by payer type reveal whether insured and self-pay patients follow divergent value trajectories — relevant for pricing, channel prioritization, and segment-level commercial strategy.
