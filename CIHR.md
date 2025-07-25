# CIHR Research Fund Analysis

## Overview
Analysis of Canadian Institutes of Health Research (CIHR) funding data from 2005-2021 for Ontario universities, examining award counts and funding amounts.

## Key Findings
- **Total Funding**: $1.15 billion distributed across Ontario institutions
- **Top Institutions**:
  - University of Toronto
  - McMaster University
  - University of Ottawa
- **COVID Impact**: 22% funding increase in 2020-2021

## Methodology

### I. Time-Series Funding Trend Analysis

```python 
plot_annual_trends(df, agency="CIHR")
```

#### Outcomes

![Annual CIHR Funding and Awards Trends for Ontario Universities (2005-2021)](images\cihr_trends.png)

![University-Specific CIHR Funding Trends (2005-2021)](images\cihr_univ_trends.png)

### II. Comparative Analysis Between Institutions

```python
top_bottom_universities(df, agency="CIHR")
```    

#### Outcomes

![Top & Bottom 8 Universities by Total CIHR Funding](images\cihr_top_bot_funding.png)

**CIHR Funding Concentration Analysis:**
- Top 3 universities account for 79.4% of total funding
- Top 5 universities account for 93.2% of total funding
- Top 10 universities account for 98.7% of total funding

### III. Agency-Specific Trend Breakdown 

```python
agency_specific_analysis(df, agency="CIHR")
```

#### Outcomes

![CIHR Funding by University](images\cihr_univ.png)


### IV. Statistical Modeling & Forecasting

```python
funding_forecasting(df, agency="CIHR")
```

#### Outcomes

![CIHR Funding Trends and Forecasts](images\cihr_forecasts.png)

### V. Statistical and Advanced Analysis

```python
advanced_analysis(df, agency="CIHR")
```

#### Outcomes

![University Clusters by CIHR Funding](images\cihr_clusters.png)

### VI. Benchmarking and Efficiency Metrics

```python
efficiency_metrics(df, agency="CIHR")
```

#### Outcomes

![Number of Universities Receiving >10M Annually from CIHR](images\cihr_10m.png)
