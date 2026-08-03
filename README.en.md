# Most Profitable New-Patient Acquisition Paths

## Context
Analysis for a large healthcare diagnostics company, with three segmentation variants: all channels, with payer/insurance-type breakdown, and a consolidated view.

## Business question
Which path (channel → subchannel → campaign → payer type / product combination) brings in the most profitable new patient? Where should acquisition effort be concentrated?

## Methodology
- Reading and cleaning the visits/encounters dataset, with per-patient deduplication and handling of null values / "unidentified" categories.
- Building full combination paths (channel × subchannel × ... × payer type) and ranking the Top 20 by volume and by revenue.
- Reusable visualization functions for quick inspection and comparison across cuts.

## Stack
`Python` · `pandas` · `matplotlib` · `SQL (BigQuery)`

## So What?
Rather than deciding investment by channel in isolation, ranking full combination paths surfaces high-profitability niches (e.g., a specific subchannel crossed with a payer type) that would stay hidden in channel-level aggregates.
