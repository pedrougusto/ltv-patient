# Retention × LTV Matrix and CRM Impact Simulator

## Context
The most advanced project in the series: beyond a Retention × LTV matrix by channel, subchannel, brand, and product group, it adds a decision layer for choosing between CRM (retention) and paid media (acquisition) investment.

## Business question
Is it more worthwhile to invest in retaining existing patients (CRM) or acquiring new ones (paid media)? At which point in the lifecycle does a CRM intervention have the most impact?

## Methodology
- **Retention × LTV Matrix**: positions each segment (channel, subchannel, brand, product group) on two axes — retention rate and patient value — to flag high-priority quadrants.
- **LTV Decomposition**: LTV = Average Ticket × Annual Frequency × Retention (years), isolating which component is dragging LTV down in each segment.
- **Early Drop-off**: classifies cohorts into "returned" vs. "lost" within the first 4 months and computes the LTV gap between the two groups — quantifying the cost of not retaining early.
- **CRM Impact Simulator**: uses the actual early drop-off numbers to estimate the revenue gain from converting a fraction of "lost" patients into "returned" ones.
- **Optimal Reactivation Window**: identifies which month patients naturally tend to come back, by subchannel — used to time reactivation campaigns.
- **Slope Analysis**: compares the marginal speed of LTV gain between CRM and paid media over time — paid media captures value immediately (peak at M0), while CRM has a delayed but more sustainable effect (peak at M3), providing numerical evidence to justify mid-term retention investment.

## Stack
`Python` · `pandas` · `matplotlib` · `numpy` · `SQL (BigQuery)`

## So What?
This project turns retention from a descriptive KPI into an investment-decision lever: it quantifies, in revenue terms, the expected gain from a CRM initiative versus the cost of paid-media acquisition — enabling budget prioritization between "retain" and "acquire" based on evidence rather than intuition.
