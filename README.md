# Project Metro Transit

This repository contains the code, data, and write-up for an exploratory spatial
analysis of Metro Transit service equity in the Twin Cities metro area. The project
examines whether transit service volume and quality are equitably distributed across
census tracts, with a focus on the relationship between neighborhood income, race,
and access to frequent transit.

**Published website:** https://mac-stat212-s26.github.io/project-metrotransit-rishika-hadley/
[![Watch the video](https://img.youtube.com/vi/5tACRrbhGbU/0.jpg)](https://www.youtube.com/watch?v=5tACRrbhGbU)


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
| Quarto | Bundled with RStudio 2024.12+ | — |

> **macOS note:** Git is bundled with Xcode Command Line Tools. Open Terminal,
> run `git --version`, and follow the prompt to install if needed.
>
> **Windows note:** Always verify the Git installer architecture (x64 vs ARM)
> matches your machine before downloading.

---

## R Package Dependencies

The following R packages are required. Install them from the RStudio **Packages**
pane → **Install**, or run this in the R console:

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
- Choose a local path that is **not** inside a cloud-synced folder (e.g., not
  inside iCloud Drive or Google Drive).
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

Download the shapefile from the Minnesota Geospatial Commons:
<https://gisdata.mn.gov/dataset/us-mn-state-metc-trans-transit-count-headway-sum>

### 6. Render the site locally

In RStudio, open the **Build** pane → click **Render Book**. A local preview of
the website will open in your browser.

### 7. Publish to GitHub Pages

In RStudio, open the **Terminal** (Tools → Terminal → New Terminal) and run:

```bash
quarto publish gh-pages --no-browser
```

Type `Yes` when prompted. If a **File Deleted** dialog appears, click **Yes**. When
the process finishes, the published URL will be printed in the terminal.

> **Authentication note:** If prompted for GitHub credentials, your GitHub password
> will not work — you need a personal access token (PAT). Generate one at
> <https://github.com/settings/tokens/new>: give it a name, set an expiration date,
> check the **repo** scope, and click **Generate token**. Paste the token when
> RStudio prompts for your password (it will not display after pasting — this is
> expected).

---

## Expected Output

After publishing, the site is live at:

> https://mac-stat212-s26.github.io/project-metrotransit-rishika-hadley/

The website has the following structure:

| Page | Description |
|---|---|
| **Main report** (`index.html`) | Full written analysis with folded code chunks, choropleth maps, headway charts, and scatter plots |
| **Hadley W EDA** | Individual exploratory analysis — income vs. transit scatter plots and LOESS regression |
| **Rishika Kundu EDA** | Individual exploratory analysis — linear regression of income and service volume |
| **Laurice J. EDA** | Individual exploratory analysis — temporal patterns across service periods and day types |
| **Project Proposal** | Original project proposal (appendix) |
| **Case Study** | Supporting case study (appendix) |

The main report is organized into: Motivation → Research Question → Background →
Data → Data Insights → Conclusions → Limitations and Future Work.

All code chunks are **folded by default** — readers can expand them via the
"Show code" toggle. A floating table of contents appears on the right side of
each page.

---

## Repository Structure

```
.
├── data/
│   └── raw/
│       └── shp_trans_transit_count_headway_sum/  # Transit shapefile (not tracked by Git)
├── eda/
│   ├── eda-hadley.qmd
│   ├── eda-member2.qmd
│   └── eda-Laurice.qmd
├── appx/
│   ├── proposal.qmd
│   └── case-study.qmd
├── wa/                    # Workspace files
├── index.qmd              # Main report
├── _quarto.yml            # Quarto site configuration
└── *.Rproj                # RStudio project file
```

> The shapefile in `data/raw/` is not tracked by Git due to file size. See
> **Step 5** above for download instructions.

---

## Authors

- Hadley W
- Rishika K
- Laurice J

Macalester College — STAT 212, Spring 2026
