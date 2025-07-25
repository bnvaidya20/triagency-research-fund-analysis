# Tri-Agency Research Funding Analysis for Universities in Ontario (2005-2021)

## Overview
This project analyzes research funding data from the three Canadian Tri-Agencies—Natural Sciences and Engineering Research Council (NSERC), Canadian Institutes of Health Research (CIHR), and Social Sciences and Humanities Research Council (SSHRC) — for universities in Ontario from 2005 to 2021. The analysis explores funding trends, institutional performance, and disparities, providing insights into the distribution and efficiency of research funding across the province.

For detailed findings, explore the agency-specific reports:  
- [NSERC Funding Analysis](NSERC.md)  
- [CIHR Funding Analysis](CIHR.md)  
- [SSHRC Funding Analysis](SSHRC.md)  


## Key Insights  
- **Funding Dominance**: The University of Toronto leads in total funding across all agencies.  
- **Agency Specialization**:  
  - CIHR funding is concentrated in medical-focused institutions (e.g., McMaster, Ottawa).  
  - Smaller universities (e.g., Nipissing, OCAD) rely more on SSHRC and NSERC.  
- **COVID-19 Impact**: CIHR funding surged by 22% in 2020–2021, reflecting pandemic-related research priorities.  
- **Inequality**: Top institutions account for 45–80% of total funding, highlighting significant concentration. 

## Methodology

### I. Time-Series Funding Trend Analysis
- **Objective**: Track annual funding and award trends to identify growth patterns, volatility, and external impacts (e.g., policy changes, pandemics). 

#### Key Steps:  
1. Plot total funding and awards per year (2005–2021) for all agencies combined and separately.  
2. Calculate **Compound Annual Growth Rates (CAGR)** for funding and awards by university.  
3. Analyze average award size (funding per award) over time and across institutions. 

```python 
# Sample Function
def plot_annual_trends(df, agency=None):
    annual_totals = df.groupby('Year').agg({'Funding': 'sum', 'Awards': 'sum'}).reset_index()
    ax1.plot(annual_totals['Year'], annual_totals['Funding'], color=color, marker='o', label='Funding')
    ax2.plot(annual_totals['Year'], annual_totals['Awards'], color=color, marker='s', label='Awards')
    plt.title(f'Annual {agency} Funding & Awards Trends for Ontario Universities (2005-2021)')
    plt.show()
```

### II. Comparative Analysis Between Institutions
- **Objective**: Benchmark universities by funding performance and identify disparities.

#### Key Steps:  
1. Rank universities by total funding and awards (overall and per agency).  
2. Measure funding concentration (e.g., top 8 vs. bottom 8 institutions).  
3. Assess funding volatility using standard deviation and coefficient of variation. 

```python
# Sample Function
def top_bottom_universities(df, agency=None):
    uni_totals = df.groupby('University').agg({'Funding': 'sum', 'Awards': 'sum'}).reset_index()
    top8 = uni_totals.head(8)
    bottom8 = uni_totals.tail(8)
    ax1.barh(top8['University'], top8['Funding'], color='blue')
    ax1.set_title(f'Top 8 Universities by Total {agency} Funding (2005-2021)')    
    ax2.barh(bottom8['University'], bottom8['Funding'], color='orange')
    ax2.set_title(f'Bottom 8 Universities by Total {agency} Funding (2005-2021)')
    plt.show()
```  

### III. Agency-Specific Trend Breakdown 
- **Objective**: Uncover disciplinary strengths and funding distributions unique to each agency.

#### Key Steps:  
1. Compare agency dominance (e.g., CIHR for medical schools, SSHRC for social sciences).  
2. Calculate proportional funding from each agency per university.  
3. Identify institutions with specialized dominance (e.g., Waterloo for NSERC).  

```python
# Sample Function
def agency_specific_analysis(df, agency=None):
    uni_fund = df.groupby('University').agg({'Funding': 'sum'}).reset_index().sort_values('Funding', ascending=False)
    plt.barh(uni_fund['University'], uni_fund['Funding'])
    plt.title(f'Total {agency} Funding by University (2005-2021)')
    plt.show()
```

### IV. Statistical Modeling & Forecasting
- **Objective**: Predict future funding trends using historical data.

#### Key Steps:  
1. Apply **polynomial regression** to model funding growth.  
2. Use **ARIMA** for time-series forecasting.  

```python
# Sample Function
def funding_forecasting(df, agency=None):
    plt.plot(annual_data.index, annual_data['Funding'], label='Actual', marker='o')
    plt.plot(annual_data.index, poly_pred, label='Polynomial Regression', linestyle='--')
    plt.plot(annual_data.index, arima_pred, label='ARIMA Forecast', linestyle='-.')
    plt.title(f'{agency} Funding Trends and Forecasts for Ontario Universities')
    plt.show()
```

### V. Statistical and Advanced Analysis
- **Objective**: Explore structural patterns and inequalities in funding distribution.

#### Key Steps:  
1. **Clustering**: Group universities by funding profiles (K-Means).  
2. **Correlation Analysis**: Test relationships between awards and funding amounts.  
3. **Inequality Metrics**: Calculate Gini coefficients and Lorenz curves.  
4. **Geographic Analysis**: Map funding by region (e.g., Northern vs. Southern Ontario).

```python
# Sample Function
def advanced_analysis(df, agency=None):
    kmeans = KMeans(n_clusters=3, random_state=42)
    clusters = kmeans.fit_predict(scaled_features)
    uni_profiles['Cluster'] = clusters
    sns.scatterplot(data=uni_profiles, x='Total_Funding', y='Avg_Funding', 
                    hue='Cluster', palette='viridis', size='Avg_Awards', sizes=(50, 200))
    plt.title(f'University Clusters by {agency} Funding Profile')
    plt.show()
```

### VI. Benchmarking and Efficiency Metrics
- **Objective**: Evaluate funding allocation efficiency and institutional thresholds.  

#### Key Steps:  
1. Compute funding-to-awards ratios.  
2. Count universities exceeding $10M/year in funding. 

```python
# Sample Function
def efficiency_metrics(df, agency=None):
    threshold = 10e6  # $10 million
    above_threshold = df[df['Funding'] > threshold].groupby('Year')['University'].count()
    above_threshold.plot(kind='bar')
    plt.title(f'Number of Universities Receiving >${threshold/1e6:.0f}M Annually')
    plt.show()
```

## Data Source
- [Council of Ontario Universities (COU)](https://cudo.ouac.on.ca/)

## Concluding Remarks  
- **Dominance of Top Institutions**: The University of Toronto, Waterloo, and McMaster consistently lead, reflecting resource concentration.  
- **Agency Specialization**: Funding aligns with institutional strengths (e.g., medical research for CIHR).  
- **Policy Implications**: Smaller universities may require targeted support to reduce disparities. 