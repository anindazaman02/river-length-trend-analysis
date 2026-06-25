# OLS Linear Regression and Statistical Diagnostics of River Length Trends

[![Language](https://img.shields.io/badge/Language-R%20%2F%20RStudio-blue?logo=r&logoColor=white)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview
This repository contains an advanced statistical processing pipeline written in R to investigate river channel morphodynamics and long-term hydrological changes. The script models historical timeline data of river channel lengths using Ordinary Least Squares (OLS) linear regression. Beyond fitting a standard trend line, the framework computes 95% confidence intervals, extracts prediction matrices, and automatically exports vital structural diagnostic plots to validate core regression assumptions.

---

## 📊 Methodological Framework & Pipeline

The script automates an end-to-end data analysis workflow divided into five distinct stages:

### 1. Data Cleaning and Type Integrity
* Ingests chronological spreadsheet datasets using the `readxl` engine.
* Forces explicit numerical formatting for `Year` and `Length` columns, discarding incomplete pairs (`NA`) to safeguard against model calculation bias.

### 2. OLS Mathematical Modeling
* Fits a simple linear regression model via the `lm()` architecture:
  $$\text{Length} = \beta_1(\text{Year}) + \beta_0 + \epsilon$$
* Computes complex diagnostic parameters including Adjusted $R^2$, the Standard Error of Estimate (SEE), and two-tailed $p$-values to evaluate slope significance.
* Derives the **95% Confidence Interval** limits for the temporal slope coefficient ($\beta_1$).

### 3. Automated Excel Accounting
Generates a multi-sheet Microsoft Excel workbook via `writexl` containing:
* **Summary:** Core model constants, observations count ($N$), and quality fit metrics.
* **Coefficients:** Detailed intercept, slope values, and standard errors.
* **Fitted_Residuals:** Logged residuals and fitted metrics for individual observations.
* **Predictions_95CI:** A single-year interval matrix mapping projected channel lengths bound with standard error prediction limits.

### 4. Publication-Ready Visualizations
All figures are compiled at a crisp **300 DPI resolution** using a standard `ggplot2` theme explicitly formatted to strict academic submission requirements (**Times New Roman** typography):
* **Trend Plot:** A scatter matrix overlayed with a linear fit line, standard error bands, and an explicit formula text annotation block.
* **Residuals vs. Fitted Plot:** Used to visually inspect the data for homoscedasticity and non-linear patterns.
* **Normal Q–Q Plot:** Evaluates the normal distribution assumption of model residuals.

---

## 💻 Repository Structure & Usage

### File Directory
* `river_length_regression.R` — Main script containing the structural data processing code.

### Prerequisites & Dependencies
To run this pipeline locally, you will need R/RStudio and the following CRAN packages installed:
```r
install.packages(c("readxl", "writexl", "ggplot2", "broom", "dplyr", "extrafont"))
