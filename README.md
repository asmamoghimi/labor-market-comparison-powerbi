# SDG 8 Labor Market & Living Standards Dashboard (Power BI)

A Power BI dashboard comparing labor market health and living standards across three economies — the Netherlands, Brazil, and Bangladesh — through the lens of UN Sustainable Development Goal 8 (Decent Work and Economic Growth).

> My first-ever data science project. Built solo during Block A, Year 1 at Breda University of Applied Sciences (September–November 2024).

## Business Case

SDG 8 calls for economic growth that creates safe, fair, accessible jobs for everyone, regardless of gender, age, or background. This dashboard tracks progress toward that goal by comparing one high-income country (Netherlands), one middle-income country (Brazil), and one low-income country (Bangladesh) against two of SDG 8's official indicators:

- **8.5.1** — average hourly earnings, used to assess whether people are fairly paid for their work and to surface income gaps between groups (e.g. men vs. women)
- **8.5.2** — unemployment rate, the share of the workforce without a job but actively looking for one

The goal was to turn these indicators into a comparative narrative — not just "what are the numbers," but "what do they reveal about inclusive growth at different income levels."

## Data

Sourced from the International Labour Organization (ILO), World Bank Group, and United Nations. Variables used: unemployment rate (by country, sex, age, disability status), average hourly earnings, purchasing power parity (PPP), inflation rate, GDP growth rate, and labor force participation rate.

Data preparation included deduplication, missing-value handling (imputed with country averages where possible, dropped where not), and outlier capping on earnings and unemployment figures — plus two derived variables: unemployment rate by urban/rural region, and a year-over-year wage growth rate.

## Dashboard Pages

Six pages, each built around one comparison:

1. **Introduction** — explains SDG 8 and the two indicators (8.5.1, 8.5.2), and classifies the three countries by income level (Netherlands: high-income, Brazil: middle-income, Bangladesh: low-income).
2. **Income Level** — GDP per capita trend (1989–2029) across all three countries, with a GDP Growth (2024–2029) KPI card and a year slicer.
3. **Annual Earning** — a pivot table of annual earnings in USD plus a clustered column chart comparing earnings between genders.
4. **Purchasing Power** — an area chart of PPP-adjusted GDP trends from 1990–2020, to compare real living standards rather than raw income.
5. **Unemployment Rate** — a combo chart (line + clustered column) of unemployment rate from 1990–2025.
6. **Inflation & Unemployment** — two line charts side by side (unemployment rate over time, inflation rate over time), set up to visually probe the relationship between the two.

## Analysis

Beyond the visual comparison, the underlying analysis included correlation analysis between unemployment and macro factors (GDP growth, inflation) and a simple linear regression to predict unemployment trends from those factors, evaluated with R² and Mean Absolute Error and checked with cross-validation. Linear regression was chosen deliberately for interpretability over accuracy — the goal was a model stakeholders could reason about, not a black box.

**Key findings:**

- Bangladesh shows a significantly higher unemployment rate than the Netherlands, pointing to deeper labor-market challenges.
- The Netherlands has a much higher PPP-adjusted standard of living than Brazil or Bangladesh — a gap that raw income figures alone understate.
- GDP growth correlates negatively with unemployment, consistent with the idea that economic growth tends to come with job creation.

## Tech Stack

`Power BI` (Power BI Desktop/Service) · DAX & Power Query for data modeling and transformation · simple linear regression and correlation analysis for the predictive layer · data sourced from ILO, World Bank, and UN.

## Limitations

- Demographic breakdowns (age, sex) are incomplete for some years, which limits how far the cross-demographic comparisons can be trusted.
- Data collection methodology differs across countries (e.g. how unemployment is measured), which affects strict comparability.
- The linear regression model is intentionally simple — it captures general trend direction, not the full complexity of labor markets.
- Several custom Power BI visuals (dumbbell chart, heatmap, radar chart, waffle chart, and others) were imported into the file while exploring chart options but aren't actually used on the final report pages — the six pages above use only standard Power BI visuals (line, area, combo, clustered column, pivot table, KPI, slicer).

## Repository Structure

Kept deliberately minimal, since this was a first project built to learn the tool rather than ship production work:

```
.
├── README.md
└── Asmamoghimi-Dashboard-240791-SDG8.pbix
```

## Skills Demonstrated

Power BI dashboard design across multiple linked pages, DAX/Power Query data modeling, translating a UN SDG framework into concrete, measurable indicators, comparative cross-country analysis, and a first pass at predictive modeling (linear regression, correlation analysis) alongside descriptive visualization.

## Acknowledgments

Completed as part of the Block A curriculum (Year 1) at Breda University of Applied Sciences. Data sourced from public ILO, World Bank, and UN datasets.
