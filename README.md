# Project Metro Transit

This repository contains the code, data, and write-up for an exploratory spatial
analysis of Metro Transit service equity in the Twin Cities metro area. The project
examines whether transit service volume and quality are equitably distributed across
census tracts, with a focus on the relationship between neighborhood income, race,
and access to frequent transit.

The final deliverable is a **knitted HTML or PDF report** produced from an R Markdown
/ Quarto source file.

---

## Required Software

Install the following before attempting to run or render anything in this repository.
Older versions may work but are not guaranteed.

| Software | Minimum Version | Download |
|---|---|---|
| Git | Latest | https://git-scm.com/downloads |
| R | 4.5.2 (2025-10-31) | https://cran.rstudio.com/ |
| RStudio | 2024.12.1 Build 563 | https://posit.co/download/rstudio-desktop/ |
| GitHub Desktop | Latest | https://desktop.github.com/ |

> **macOS note:** Git is bundled with Xcode Command Line Tools. Open Terminal,
> run `git --version`, and follow the prompt to install if needed.
>
> **Windows note:** Always verify the Git installer architecture (x64 vs ARM)
> matches your machine before downloading.

---

## R Package Dependencies

The following R packages are required. Install them from the RStudio **Packages**
pane → **Install**, or run this in the console:

```r
install.packages(c("tidyverse", "dplyr", "sf", "tidycensus",
                   "patchwork", "scales", "rmarkdown", "downlit", "xml2"))
```

`tidycensus` requires a free Census API key. Register at
<https://api.census.gov/data/key_signup.html>, then run:

```r
tidycensus::census_api_key("YOUR_KEY_HERE", install = TRUE)
```

---

## Setup Steps

### 1. Clone the repository

- Open the GitHub Classroom assignment link and accept it.
- Click the **Code** dropdown → **Open with GitHub Desktop**.
- Choose a local path that is **not** inside a cloud-synced folder (e.g., not inside
  iCloud Drive or Google Drive).
- Click **Clone** → select **For my own purposes** → click **Continue**.

### 2. Open the project in RStudio

- In GitHub Desktop: **Repository** menu → **Show in Explorer / Finder**.
- Double-click the `.Rproj` file to open the project in RStudio.

### 3. Configure RStudio global settings

To prevent session state from interfering with reproducibility:

- **Tools** → **Global Options** → **General** → **Basic** tab
- Uncheck **"Restore .RData into workspace at startup"**
- Set **"Save workspace to .RData on exit"** → **Never**
- Click **Apply** → **OK**

### 4. Install required packages

In the RStudio **Packages** pane → **Install**, type:

```
rmarkdown, downlit, xml2
```

Make sure **Install dependencies** is checked, then click **Install**.

### 5. Add your data

Place the raw transit shapefile in the following location relative to the project
root (create the folders if they don't exist):

```
data/raw/shp_trans_transit_count_headway_sum/
```

The shapefile can be downloaded from the Minnesota Geospatial Commons:
<https://gisdata.mn.gov/dataset/us-mn-state-metc-trans-transit-count-headway-sum>

### 6. Render the report

Open `index.qmd` (or `index.Rmd`) in RStudio and click the **Knit** button at the
top of the editor. Choose **Knit to HTML** or **Knit to PDF** from the dropdown.

Alternatively, run from the R console:

```r
# HTML
rmarkdown::render("index.qmd", output_format = "html_document")

# PDF (requires a LaTeX installation — see note below)
rmarkdown::render("index.qmd", output_format = "pdf_document")
```

> **PDF note:** Rendering to PDF requires a LaTeX distribution. The easiest option
> is to install the `tinytex` R package:
> ```r
> install.packages("tinytex")
> tinytex::install_tinytex()
> ```

---

## Expected Output

After knitting, a rendered report file will appear in the project root:

- **`index.html`** — opens directly in any web browser; contains all prose,
  folded code chunks, choropleth maps, and charts rendered inline.
- **`index.pdf`** — a print-ready version of the same report.

The report is organized into the following sections:

1. Motivation
2. Research Question
3. Background
4. Data (collection, acquisition, and understanding)
5. Data Insights (choropleth maps, headway charts, scatter plots)
6. Conclusions
7. Limitations and Future Work

---

## Repository Structure

```
.
├── data/
│   └── raw/
│       └── shp_trans_transit_count_headway_sum/   # Transit shapefile (not tracked by Git)
├── index.qmd          # Main report source file
├── eda/               # Individual EDA notebooks
├── _quarto.yml        # Quarto configuration (if applicable)
└── *.Rproj            # RStudio project file
```

---

## Authors

- Hadley W
- Rishika K
- Laurice J

Macalester College — STAT 212, Spring 2026
