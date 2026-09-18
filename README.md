# Three-Level Linear Mixed Models: Mathematics Achievement Predictors from 72 Countries

## Overview

This repository provides the analysis code and rendered analytical report associated with the manuscript:

**Three-Level Linear Mixed Models: Mathematics Achievement Predictors from 72 Countries**

The study used data from the **OECD Programme for International Student Assessment (PISA) 2022, Version 1** to investigate predictors of mathematics achievement while accounting for the hierarchical structure of students nested within schools and schools nested within countries.

The final analytical sample included:

* 459,413 students
* 19,535 schools
* 72 countries and participating education systems

This repository was prepared to support transparent reporting, reproducibility, and peer review.

## Repository contents

| File                        | Description                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `Final_Analysis_Clean.Rmd`  | R Markdown source containing the data-processing, statistical-analysis, diagnostic, and output-generation code |
| `Final_Analysis_Clean.html` | Rendered HTML report containing the complete analysis, tables, figures, model results, and diagnostic outputs  |
| `README.md`                 | Project description, data-access instructions, analytical overview, and reproducibility guidance               |
| `.gitignore`                | Prevents operating-system files, temporary R files, and nonpublic datasets from being committed                |
| `CITATION.cff`              | Citation metadata for the repository                                                                           |
| `LICENSE`                   | License governing reuse of the original code in this repository                                                |

## Data source

The study used the **PISA 2022 Database** published by the Organisation for Economic Co-operation and Development (OECD).

The official database, Public Use Files, questionnaires, codebooks, and supporting documentation are available from:

**OECD PISA 2022 Database:**
https://www.oecd.org/en/data/datasets/pisa-2022-database.html

The OECD database includes student-questionnaire data, estimates of student performance, school-questionnaire data, cognitive-item data, questionnaire-timing data, and other supporting resources.

## Data availability and redistribution

The original PISA 2022 files and the processed analytical dataset are **not included in this repository**.

Users should obtain the PISA 2022 Public Use Files directly from the OECD and review the applicable OECD terms, documentation, and conditions of use. This repository does not grant a license to any OECD data.

The source data were processed to retain the variables required for the analysis. The resulting analytical dataset was used to fit the models documented in `Final_Analysis_Clean.Rmd`.

Because the data are not redistributed, users who wish to reproduce the analysis must:

1. Download the appropriate PISA 2022 Public Use Files from the OECD.
2. Review the PISA 2022 codebook and technical documentation.
3. Store the source data locally.
4. Update the input-data path in `Final_Analysis_Clean.Rmd`, if necessary.
5. Run the R Markdown file in RStudio or another compatible R environment.

## Study design and analytical approach

The analysis evaluated mathematics achievement using a three-level hierarchical structure:

* Level 1: students
* Level 2: schools
* Level 3: countries or participating education systems

The analytical workflow included:

1. Importing and preparing the PISA 2022 student-level data.
2. Selecting and recoding the variables required for analysis.
3. Evaluating missingness and conducting descriptive analyses.
4. Examining the distribution of mathematics achievement and study covariates.
5. Fitting unconditional and adjusted three-level linear mixed models.
6. Estimating variance components at the student, school, and country levels.
7. Calculating intraclass correlation coefficients.
8. Comparing candidate models using likelihood-based statistics and information criteria.
9. Evaluating model assumptions and diagnostic results.
10. Producing the tables and figures reported in the analytical output.

## Plausible values

PISA reports mathematics performance using multiple plausible values rather than a single observed score.

All ten mathematics plausible values—`PV1MATH` through `PV10MATH`—were analyzed separately. Fixed-effect estimates and their uncertainty were subsequently combined using Rubin’s combining rules.

This approach was used to incorporate the uncertainty associated with the plausible-value methodology.

## Sampling weights

The PISA final student weight, `W_FSTUWT`, was normalized to have a mean of one and supplied to the fitted mixed models.

In this implementation, the normalized values function as prior weights within `lme4::lmer()`. They should not be interpreted as a complete implementation of the PISA complex survey design or replicate-weight variance estimation. This distinction is documented to ensure that the analytical approach is represented transparently.

## Multilevel models

The models included random intercepts for schools and countries to account for clustering at both levels.

The analysis considered increasingly adjusted models and compared their fit using relevant statistical criteria. The final workflow reports:

* Fixed-effect estimates
* Standard errors and confidence intervals
* School- and country-level variance components
* Intraclass correlation coefficients
* Marginal and conditional measures of explained variance
* Model-comparison statistics
* Residual and model-diagnostic results
* Sensitivity analyses

## Software

The analysis was conducted in **R** using R Markdown.

Principal R packages included:

* `lme4`
* `lmerTest`
* `MuMIn`
* `dplyr`
* `tidyr`
* `readr`
* `haven`

Additional packages used by the analysis are identified in `Final_Analysis_Clean.Rmd`.

## Viewing the analysis

The completed analytical report is available in:

[`Final_Analysis_Clean.html`](Final_Analysis_Clean.html)

GitHub may display the HTML source instead of rendering the report as an interactive webpage. If that occurs:

1. Download `Final_Analysis_Clean.html`.
2. Open the downloaded file in a web browser such as Chrome, Safari, or Firefox.

The underlying R Markdown source is available in:

[`Final_Analysis_Clean.Rmd`](Final_Analysis_Clean.Rmd)

## Reproducing the analysis

To reproduce the analysis:

1. Install a recent version of R and RStudio.
2. Download the required PISA 2022 Public Use Files from the OECD.
3. Clone or download this repository.
4. Open `Final_Analysis_Clean.Rmd`.
5. Install any required R packages that are not already installed.
6. Update the local data-file path in the R Markdown file.
7. Render the document by selecting **Knit** in RStudio or by running:

```r
rmarkdown::render("Final_Analysis_Clean.Rmd")
```

The analysis cannot run without a locally available copy of the required PISA 2022 data.

## Ethical considerations

This research used publicly available, de-identified secondary data released by the OECD. The investigators did not recruit participants, interact with participants, or receive directly identifiable information.

Users of the PISA data remain responsible for following the OECD’s applicable terms, documentation, and data-use requirements.

## Authors

* Md Saiful Hasan
* Ridwanul Mosrur
* Abdul Awal
* Asif Aziz

**Corresponding author:** Md Saiful Hasan
**ORCID:** https://orcid.org/0009-0004-2122-6583

## Citation

Citation information for this repository will be provided through `CITATION.cff`. A permanent DOI will be added after the repository is archived through Zenodo.

Until a DOI is available, please cite the GitHub repository using its title, authors, year, and URL:

https://github.com/saifulanalyst/three-level-lmm-math-achievement

## License

The original analysis code in this repository is provided under the license identified in the `LICENSE` file.

The license applies only to the original repository code and documentation. It does not apply to the PISA 2022 data, which remain subject to the OECD’s applicable terms and conditions.

## Contact

For questions concerning the analysis or repository, please contact:

**Md Saiful Hasan**
ORCID: https://orcid.org/0009-0004-2122-6583
