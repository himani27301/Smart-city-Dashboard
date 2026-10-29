# Smart City Dashboard — Native R Shiny

## Quick RStudio demonstration
Open `Smart_City_India.Rproj`, then run:

```r
source("demo_in_RStudio.R")
```

This demonstration requires base R only. It reads the real Indian city dataset, filters Hyderabad 2018, prints summary statistics, displays two R plots, and saves tables and a PDF under `outputs/`.

Expected results: **8,539 total records, eight cities; Hyderabad 2018 has 365 records, mean PM2.5 43.1, mean source AQI 98.**

## Full dashboard in RStudio

```r
source("setup.R")  # install Shiny and jsonlite if missing
shiny::runApp()
```

Or open `app.R` and click **Run App** after setup.

## Architecture
RStudio is the development environment, R is the analysis language, and Shiny hosts the web application. The native R process loads the CSV and performs all filtering, means, monthly aggregation, category percentages, custom CSV parsing, numerical-series preparation and CSV exports. Shiny sessions isolate uploaded data. HTML/CSS preserves the approved appearance; JavaScript draws the R-computed series and sends UI events to Shiny. The native dashboard has no webR or JavaScript analysis fallback.

The data and features match the prior project. Health/education data and Liquid Galaxy remain unavailable. Historical air quality covers 2017–2019; weather is separate model output. Google Maps and weather require internet.

## External hosting
The included Dockerfile runs a persistent native R Shiny process and respects the host's PORT variable. This package is ready for a Docker web service on Render. External publication requires a connected Git repository and selected Render workspace. No external URL is claimed until deployment succeeds.

## Review script
1. Open the .Rproj file and show the project folders.
2. Run source("demo_in_RStudio.R"). Show the console results, Environment data frames and Plots pane.
3. Show `R/analytics.R`: read.csv, row filtering, mean, vapply and write.csv.
4. Run shiny::runApp(). Choose Hyderabad and 2018; verify the same 365 / 43.1 / 98 results.
5. Change year, switch city and export CSV to show R reacting to inputs.

## Sources and licence
Layout/assets: Prayag Biswas, https://github.com/Prayag-X/Smart-City-Dashboard (MIT, preserved in dist/LICENSE.txt).
Air data: https://github.com/prathibha13/Air-Quality-Index-in-India-R-shiny (upstream preprocessed values retained).
Weather: Open-Meteo; maps: Google Maps; photos: Wikipedia/Wikimedia with per-city provenance links.
