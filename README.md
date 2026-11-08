# Biodiversity Data Analysis (R)

An ecological data-analysis project using five Environmental Change Network (ECN) datasets to investigate vegetation, woodland structure, butterflies and moths. The supplied data contains **612,005 records** in total.

## Project contents

| File | Records | Description |
|---|---:|---|
| `ECN_VB1.csv` | 52,033 | Baseline vegetation monitoring |
| `ECN_VF1.csv` | 261,888 | Fine-grain vegetation monitoring |
| `ECN_VW1.csv` | 14,075 | Woodland vegetation and tree measurements |
| `ECN_IB1.csv` | 79,410 | Butterfly observations |
| `ECN_IM1.csv` | 204,599 | Moth observations |

The CSV files contain site identifiers and measurements recorded at different spatial and temporal scales. Their schemas differ: for example, the woodland file includes plot, cell, tree and stem identifiers, while the invertebrate files include observation dates and recorded values.

The `WR_INDIV_DRAFT_*.pdf` files are draft coursework reports documenting parts of the analysis. They are useful as a record of the questions, code fragments, plots and interpretations explored during the project.

## Analysis covered

The accompanying report drafts document several complementary investigations:

- **Exploratory data analysis:** examining the structure, sampling effort, distributions and limitations of the five datasets.
- **Moth flight windows:** converting observation dates into week-of-year values, aggregating counts by site and week, and comparing seasonal activity patterns between sites.
- **Woodland tree measurements:** reshaping the woodland data so measurements such as diameter, height, number of stems and distance can be considered together; investigating the relationship between tree diameter and height.
- **Woodland and invertebrate comparisons:** aggregating butterfly and moth counts by site and year, then comparing them with the number of recorded woodland tree species.
- **Fine-grain vegetation and butterflies:** comparing annual butterfly totals with the number of unique fine-grain vegetation species recorded at each site.

## Methods

The analyses use data preparation and reshaping, grouped aggregation, exploratory plots, correlation, simple linear regression and residual diagnostics. Model assessment considers the strength and form of relationships, influential or anomalous observations, missing values, sample sizes and whether a straight-line model is appropriate. The reports also explore subsets of the data where site-level patterns differ from the pooled relationship.

For example, the woodland tree analysis fits `HEIGHT ~ DIAMETER` to the combined observations and separately to selected sites. The draft reports a positive pooled association, but also shows that the relationship and its strength vary by site. The fine-grain vegetation analysis finds only a weak positive linear association between unique vegetation-species counts and butterfly totals in the analysed site-year records; this should not be interpreted as evidence of causation.

## Tools and packages

- **R** — data handling and statistical analysis
- **R Markdown** — combining code, output, plots and written interpretation in reports
- **ggplot2** — statistical graphics
- **dplyr / tidyr** — data manipulation and reshaping

## Reproducing the work

The archive includes the five source CSV files and PDF report drafts, but **does not include standalone `.R` or `.Rmd` source files**. Code excerpts are embedded in the reports. To reproduce or extend the analyses, create an R or R Markdown file in this directory and read the relevant CSV files, for example:

```r
woodland <- read.csv("ECN_VW1.csv")
butterflies <- read.csv("ECN_IB1.csv")
moths <- read.csv("ECN_IM1.csv")
fine_grain <- read.csv("ECN_VF1.csv")
baseline <- read.csv("ECN_VB1.csv")
```

Install the packages used by the relevant analysis before running code that calls them:

```r
install.packages(c("ggplot2", "dplyr", "tidyr"))
```

## Interpretation and limitations

These are observational monitoring datasets, not controlled experiments. Sampling designs and frequencies differ between datasets and sites, and observations may be nested within plots or repeated over time. Aggregating to site-year totals can hide within-site variation and differences in sampling effort. Missing values, special field codes and unusual identifiers also require care; exclusions should be justified and recorded rather than treated as automatic data errors.

The PDF files are explicitly draft reports. Their code and conclusions are a record of the work undertaken, not a packaged, automated analysis pipeline.
