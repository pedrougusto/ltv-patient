# Cohort Retention Heatmaps

## Context
Month-over-month retention analysis for a healthcare diagnostics company, covering acquisition cohorts by digital channel and by subchannel (e.g., paid search).

## Business question
How long does a patient acquired through a specific channel keep coming back? Does retention vary by acquisition channel?

## Methodology
- BigQuery query that builds the acquisition cohort, computes months since acquisition, and the month-over-month retention rate.
- Heatmap (cohort × month matrix) to quickly visualize where retention drops off — split by Digital channel and by Paid Search subchannel.
- All downstream transformations done in pandas from a single data load (no redundant queries).

## Stack
`Python` · `pandas` · `matplotlib` (heatmap) · `SQL (BigQuery)`

## So What?
The heatmap visually exposes the exact month where most of the cohort stops returning — information that guides when in the lifecycle (e.g., month 2 or 3) it's worth investing in reactivation campaigns.
