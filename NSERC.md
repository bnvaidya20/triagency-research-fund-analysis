# NSERC Research Funding Analysis

## Overview
Analysis of Natural Sciences and Engineering Research Council (NSERC) funding data from 2005-2021 for Ontario universities, examining award counts and funding amounts.

## Key Findings
- **Total Funding**: $3.48 billion distributed across Ontario institutions
- **Top Institutions**:
  - University of Toronto
  - University of Waterloo
  - Queen's University
- **Award Growth**: 15% increase in average awards per institution since 2005

## Methodology

### I. Time-Series Funding Trend Analysis

```python 
plot_annual_trends(df, agency="NSERC")
```

#### Outcomes

![Annual NSERC Funding and Awards Trends for Ontario Universities (2005-2021)](images\nserc_trends.png)

![Top & Bottom 5 Universities by Funding CAGR(%)](images\nserc_cagr.png)

### II. Comparative Analysis Between Institutions

```python
top_bottom_universities(df, agency="NSERC")
```    

#### Outcomes

![Top & Bottom 8 Universities by Total NSERC Funding](images\nserc_top_bot_funding.png)

**NSERC Funding Concentration Analysis:**
- Top 3 universities account for 48.2% of total funding
- Top 5 universities account for 65.0% of total funding
- Top 10 universities account for 91.5% of total funding

### III. Agency-Specific Trend Breakdown 

```python
agency_specific_analysis(df, agency="NSERC")
```
#### Outcomes

![NSERC Funding by University](images\nserc_univ.png)


### IV. Statistical Modeling & Forecasting

```python
funding_forecasting(df, agency="NSERC")
```
#### Outcomes

![NSERC Funding Trends and Forecasts](images\nserc_forecasts.png)

### V. Statistical and Advanced Analysis

```python
advanced_analysis(df, agency="NSERC")
```

#### Outcomes

![University Clusters by NSERC Funding](images\nserc_clusters.png)

### VI. Benchmarking and Efficiency Metrics
```python
efficiency_metrics(df, agency="NSERC")
```

#### Outcomes

![Number of Universities Receiving >10M Annually from NSERC](images\nserc_10m.png)
