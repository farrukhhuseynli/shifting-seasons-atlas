# Shifting Seasons Atlas

Interactive demo that measures whether the hottest day of the year is moving, using harmonic fitting and trend regression on climate time series.

> **Note:** All data in this repository is synthetic. Each city carries a known, hidden seasonal shift so the method can be validated by checking whether it recovers that shift. No result is a real climate measurement. The same pipeline is designed to run on reanalysis data such as ERA5.

## What it does

1. Fits an annual cycle to each year of daily temperature (least squares, first harmonic).
2. Extracts the peak day for every year (1950–2020).
3. Regresses peak day on year to estimate the total shift, with a 95% confidence interval.
4. Compares the recovered shift with the hidden true shift for six cities.

## Run it

Open `index.html` in any browser. No build step, no dependencies.

## Methodology

- Seasonal fit: T(d) = c + a·cos(2πd/365) + b·sin(2πd/365); peak day = atan2(b, a)·365/2π.
- Trend: ordinary least squares on yearly peak days; robust alternative is Theil–Sen with a Mann–Kendall test.
- Validation: synthetic recovery test (known shift + noise).

## Tools

- This demo: vanilla JavaScript and SVG.
- Planned production stack: Python (xarray, NumPy, pandas, SciPy, statsmodels), cdsapi for ERA5, Cartopy or QGIS for maps, Tableau or Power BI for stakeholder dashboards.

## Roadmap

- Replace synthetic series with ERA5 for 50+ cities
- Global gridded map of seasonal shift
- Vegetation indicator (NDVI) as a second measure of seasonal timing

## References

- Hersbach, H. et al. (2020). The ERA5 global reanalysis. *Q. J. R. Meteorol. Soc.*, 146, 1999–2049.
- Stine, A. R., Huybers, P., & Fung, I. Y. (2009). Changes in the phase of the annual cycle of surface temperature. *Nature*, 457, 435–440.
- Thomson, D. J. (1995). The seasons, global temperature, and precession. *Science*, 268, 59–68.
- Sen, P. K. (1968). Estimates of the regression coefficient based on Kendall's tau. *JASA*, 63, 1379–1389.
- Mann, H. B. (1945). Nonparametric tests against trend. *Econometrica*, 13, 245–259.

Verify citations before using them in formal work.

## License

MIT
