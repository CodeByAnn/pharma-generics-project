# Pharma Market / Generic Medicine Adoption

This is a portfolio-ready starter for a Roche-adjacent data story about generic medicine adoption.

It uses the same interaction pattern as the moving-dot chart: click a country tab, and the dots move to the selected country's positions.

## Main File

Open `index.html` in a browser, or run a local server from this folder:

```bash
python3 -m http.server 8010
```

Then open:

```text
http://localhost:8010/
```

If you open `index.html` directly as a `file://` page, Safari may block loading the external JSON file. The page includes an embedded copy of the same chart-ready OECD data as a fallback, so the chart will still render.

## Story Angle

Generic medicines can improve affordability and efficiency in pharmaceutical spending, but countries differ in how deeply generics penetrate their markets.

The chart compares:

- generic market share by volume
- generic market share by value

When volume share is much higher than value share, it suggests generics are widely used but represent a smaller share of spending, which is common because generics are lower priced than originator medicines.

## Data Sources To Use

The data has been exported from OECD Health Statistics:

- Generic market: `HEALTH_PHMC@DF_GEN_MRKT`
- Measure: share of generics in the respective pharmaceutical market
- Units: percentage of sales volume and percentage of sales value
- Market types in the export: Total, Community pharmacy market, and Third-party-payer market

Generated files:

- `data/oecd_generic_market_long.csv`: all exported OECD observations in long format.
- `data/oecd_generic_market_long.json`: same export as JSON.
- `data/oecd_generic_market_chart_ready.json`: smaller subset used by `index.html`.
- `data/export_summary.json`: row counts and selected countries.

The chart-ready subset chooses Total market when both value and volume are available. If Total is not available for a country, it falls back to Community pharmacy market, then Third-party-payer market.

Useful official links:

- https://data-explorer.oecd.org/
- https://www.oecd.org/en/data/datasets/oecd-health-statistics.html
- https://www.oecd.org/en/publications/health-at-a-glance-2025_8f9e3f98-en/full-report/generics-and-biosimilars_e68f4e94.html

## Important

The OECD generic-market export does not include Poland in this dataflow, so Poland is not shown in the current chart.
