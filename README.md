# **Employee Layoffs Since COVID-19: Industry Impact & Federal Reserve Interest Rate Analysis (2020–2026)**

**Author:** S Rohith  
**Repository:** [Employee-Layoffs-Analysis](https://github.com)

## Problem Statement
The purpose of this project is to analyze the impact of employee layoffs globally since the onset of COVID-19. The project aims to identify which industries experienced the highest number of layoffs, which countries were most affected, and to explore whether there is a correlation between U.S. federal interest rates and layoffs in companies. 

We have two datasets:
- **Global employee layoffs** across different industries and companies.
- **U.S. federal interest rates (`FEDFUNDS`)** over the same time period.

The analysis focuses first on identifying trends in layoffs by industry and company, and then moves to investigate potential relationships between federal interest rates and layoffs.


## Objectives
- Identify the industries and companies most affected by employee layoffs since COVID-19.
- Determine which countries experienced the most significant workforce reductions.
- Quantify and statistically test the relationship between U.S. Federal Reserve interest rates and U.S. company layoffs from 2020 to 2026.

## Challenges & Solutions
  - **Missing Values & Mixed Date Formats:** The raw layoffs dataset contained missing categorical and numerical entries alongside inconsistent date strings (`MM/DD/YYYY` and `MM-DD-YYYY`).
      * *Solution:* Audited null values with `missingno`, imputed missing categorical fields with `'Unknown'`, **retained missing numerical fields as `NaN` to avoid distorting aggregate layoff totals**, and standardized all dates to monthly periods (`YYYY-MM-01`).
- **Mismatch in Data Granularity:** Layoff events were recorded on specific days, whereas Federal Reserve interest rates were reported monthly.  
  * *Solution:* Aggregated layoff dates to the month level, merged both datasets via a left join, and forward-filled the latest available interest rate values.
- **Global vs. National Scope:** Comparing global layoffs against U.S.-specific Federal Reserve interest rates risked skewing economic insights, and 8 non-U.S. cities (e.g., `Tel Aviv, Non-U.S.`, `New Delhi`, `Brisbane`) were mislabeled under the United States.  
  * *Solution:* Filtered the macroeconomic and statistical analysis strictly to U.S. companies and removed the 8 mislabeled non-U.S. city entries.

## Key Results & Statistical Findings
- **Oracle's June 2026 Layoff:** Oracle laid off **21,000 employees (13% of its workforce)** in June 2026 while U.S. Federal Reserve interest rates stood at **3.63%**—well above the 0.05% COVID-era low—driven by elevated borrowing costs and strategic restructuring toward AI infrastructure.
- **Statistical Hypothesis Testing (SciPy):**
  - **Two-Sample Welch's t-test:** Comparing low-rate months (< 2.5%) against high-rate months (≥ 2.5%) confirms that average monthly U.S. layoffs nearly tripled from **3,704** to **11,094** (**t = 3.758, p = 0.0003**).
  - **Pearson Correlation Test:** The results show a statistically significant moderate positive correlation between Federal Funds rates and monthly layoffs (**r = 0.309, t = 2.851, p = 0.0056**), suggesting that higher interest rates were associated with increased layoffs. However, correlation does not establish causation.

- **Geographic Concentration:** Among the top 5 affected countries, the **United States accounted for 81.9%** of laid-off employees, followed by **India (8.4%)**, **Germany (4.0%)**, the **United Kingdom (3.0%)**, and the **Netherlands (2.7%)**.
- **Hardest-Hit U.S. Industries:** **Hardware** (100,762), **Other** (85,729, including Oracle), **Retail** (83,937), and **Consumer** (81,409) recorded the highest cumulative U.S. layoffs.
- **Top Affected U.S. Companies:** **Amazon** (~60k), **Intel** (~43k), **Meta** (~36k), and **Microsoft** (~35k) led total reductions, with **Oracle** ranking 6th (~22k).

## Tools & Technologies Used
- **Data Cleaning & Manipulation:** Python, Pandas, NumPy, Missingno
- **Statistical Analysis:** SciPy (`scipy.stats`)
- **Data Visualization:** Matplotlib, Seaborn, Plotly
- **Environment:** Jupyter Notebook (VS Code)

## Repository Contents
- `Employee Layoff Analysis since covid - 19.ipynb` — Complete Jupyter Notebook with data cleaning, EDA, visualizations, and statistical hypothesis testing.
- `layoffs.csv` — Global layoffs dataset (2020–2026).
- `FEDFUNDS.csv` — Historical U.S. Federal Reserve interest rate dataset.

- ## Conclusion
This project provides a comprehensive analysis of employee layoffs since COVID-19 across different industries and countries, while statistically evaluating the relationship between U.S. Federal Reserve interest rates and U.S. layoffs. The findings demonstrate that elevated borrowing costs significantly coincided with higher monthly layoffs—nearly tripling during high-rate periods (≥ 2.5%)—and explain how macroeconomic pressures alongside AI restructuring contributed to major workforce reductions such as Oracle's 21,000-employee layoff in June 2026. Together, the visualizations and statistical tests offer actionable insights into how monetary policy and sector shifts shape corporate employment decisions.

