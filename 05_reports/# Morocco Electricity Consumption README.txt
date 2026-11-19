# Morocco Electricity Consumption and Environmental Factors Analysis

**Project Category:** Exploratory Data Analysis | Business Intelligence | Energy Analytics  
**Track:** Data Analytics  
**Tools:** Python, pandas, NumPy, Matplotlib, Seaborn, Plotly, Jupyter Notebook  
**Analysis Period:** January – December 2017

---

## 1. Business Context

Electricity consumption patterns influence demand monitoring, operational planning and resource allocation.

For electricity providers and energy management teams, understanding when consumption increases, how demand differs across service zones and whether environmental conditions are associated with consumption can support better operational decisions.

However, aggregated consumption figures alone may conceal important differences between geographical zones and changes occurring throughout the day, week or year.

This project investigates historical electricity consumption across three zones in Morocco to identify these patterns and translate the findings into actionable business insights.

The analysis focuses on three business questions:

1. **Demand distribution:** Which zones record the highest average consumption, and how does consumption variability differ across them?
2. **Demand patterns:** When do consumption peaks occur, and how do hourly, weekly and monthly patterns differ?
3. **Environmental relationships:** How are temperature, humidity and wind speed associated with electricity consumption?

The objective is to move beyond descriptive charts and produce evidence that can support consumption monitoring, management reporting and further demand forecasting investigations.

## 2. Analytical Objectives

The project was designed around the following objectives:

- Assess the completeness, consistency and structure of the source data.
- Prepare the dataset for reliable time-based analysis.
- Compare consumption levels and variability across the three zones.
- Identify recurring hourly, weekday and monthly consumption patterns.
- Examine relationships between environmental variables and recorded consumption.
- Develop interactive and static visualisations to communicate findings.
- Translate analytical results into practical monitoring and planning recommendations.

## 3. Dataset Overview

The analysis uses the Morocco electricity consumption dataset and its accompanying data dictionary.

### Dataset characteristics

| Attribute | Description |
|---|---|
| Geographic coverage | Morocco |
| Observation period | 1 January – 30 December 2017 |
| Total observations | 52,416 |
| Original variables | 9 |
| Recording frequency | 10-minute intervals |
| Electricity zones | 3 |
| Number of recorded dates | 364 |

### Data dictionary

| Variable | Business interpretation |
|---|---|
| Datetime | Timestamp of each observation |
| Temperature | Environmental temperature measurement |
| Humidity | Environmental humidity measurement |
| WindSpeed | Recorded wind speed |
| GeneralDiffuseFlows | General diffuse flow measurement |
| DiffuseFlows | Diffuse flow measurement |
| PowerConsumption_Zone1 | Recorded consumption for Zone 1 |
| PowerConsumption_Zone2 | Recorded consumption for Zone 2 |
| PowerConsumption_Zone3 | Recorded consumption for Zone 3 |

The three zone-level consumption variables form the primary measures used for comparative analysis.

Environmental variables provide additional context for investigating potential relationships with consumption.

**Measurement consideration:** The source data dictionary labels the zone consumption measurements as kWh. However, the precise interpretation of each 10-minute observation requires verification. Consequently, the analysis uses recorded consumption values and avoids treating their sums as confirmed total energy.

## 4. Analytical Approach and Thought Process

The analysis followed a structured workflow, with each stage addressing a specific analytical requirement.

### Stage 1: Business Understanding and Problem Definition

Before analysing the data, the business questions were defined around consumption distribution, demand patterns and environmental relationships.

This established the analytical direction and ensured that the work focused on questions relevant to energy monitoring and management reporting.

**Reasoning:** A consumption dataset can support many possible analyses. Defining the business questions first helps avoid producing visualisations that do not contribute to a meaningful decision.

### Stage 2: Data Understanding and Quality Assessment

The original files were loaded into Python using pandas.

Initial inspection covered:

- Dataset dimensions and column names.
- Data types and variable structure.
- Date and time coverage.
- Missing values.
- Duplicate records and timestamps.
- Negative numerical values.
- Observation frequency and date completeness.

The dataset contained 52,416 observations and nine original columns.

The date range covered 364 days, with 144 observations per recorded day.

**Quality assessment results:**

| Validation | Result |
|---|---:|
| Missing values | 0 |
| Duplicate rows | 0 |
| Repeated timestamps | 0 |
| Negative numerical values | 0 |
| Observations per recorded day | 144 |

**Reasoning:** Time-based consumption analysis depends on reliable timestamps and consistent observation frequency. These checks were necessary before aggregating the data into hourly, daily and monthly summaries.

### Stage 3: Data Preparation and Feature Engineering

The datetime column was converted into a proper datetime data type.

Additional analytical variables were created to support time-based comparisons:

- Year
- Month
- Date
- Day of week
- Hour
- Week

The original records were retained without missing-value imputation or record removal.

These features allowed the dataset to be grouped at different reporting levels without changing the underlying consumption measurements.

**Reasoning:** Management questions are often expressed in terms of reporting periods rather than individual observations. Feature engineering made it possible to compare consumption at hourly, daily, weekly and monthly levels.

### Stage 4: Exploratory and Statistical Analysis

Descriptive statistics were calculated for each electricity zone.

The analysis included:

- Mean and median consumption.
- Standard deviation.
- Minimum and maximum values.
- Consumption range.
- Coefficient of variation.

The coefficient of variation was particularly useful because it allowed relative variability to be compared across zones with different average consumption levels.

Time-based aggregations were then performed to identify consumption patterns by hour, weekday and month.

**Reasoning:** Average consumption identifies the relative scale of demand, while variability and time-based aggregations provide additional information about consistency and changing demand patterns.

### Stage 5: Environmental Relationship Analysis

The environmental analysis examined associations between electricity consumption and:

- Temperature
- Humidity
- Wind speed

Both Pearson and Spearman correlation coefficients were calculated.

Pearson correlation measures linear association, while Spearman correlation evaluates monotonic association using ranked values.

Regression scatter plots were also used to visually investigate the relationships.

**Reasoning:** Using both correlation methods provides a broader view of the relationships and helps identify cases where a linear association may not adequately describe the observed pattern.

Correlation does not establish causation.

### Stage 6: Data Visualisation and Communication

The analysis used Matplotlib, Seaborn and Plotly.

Static visualisations were developed for statistical comparisons and distributions, while Plotly was used for interactive time-based exploration.

The visualisation design focused on answering the original business questions rather than producing charts without a clear analytical purpose.

## 5. Key Findings and Business Interpretation

### Finding 1: Consumption Levels Differ Significantly Across Zones

| Zone | Average Consumption | Standard Deviation | Coefficient of Variation |
|---|---:|---:|---:|
| Zone 1 | 32,344.97 | 7,130.56 | 22.05% |
| Zone 2 | 21,042.51 | 5,201.47 | 24.72% |
| Zone 3 | 17,835.41 | 6,622.17 | 37.13% |

Zone 1 recorded the highest average consumption, approximately 81.4% above Zone 3.

Zone 3 had the highest coefficient of variation, indicating greater relative variability.

**Business interpretation:** A uniform monitoring approach may overlook important differences between zones. Zone-specific benchmarks and monitoring thresholds would provide a more meaningful view of consumption behaviour.

### Finding 2: All Three Zones Peak at 20:00

| Zone | Peak Hour | Average Consumption |
|---|---|---:|
| Zone 1 | 20:00 | 43,822.59 |
| Zone 2 | 20:00 | 28,186.91 |
| Zone 3 | 20:00 | 26,027.61 |

All three zones recorded their highest average hourly consumption at 20:00.

**Business interpretation:** The evening period is a priority for demand monitoring. Management could investigate peak-hour deviations and assess whether operational planning needs to account for recurring evening demand.

### Finding 3: Monthly Consumption Patterns Differ Across Zones

| Zone | Peak Month | Average Consumption |
|---|---|---:|
| Zone 1 | August | 36,435.19 |
| Zone 2 | August | 24,656.22 |
| Zone 3 | July | 28,194.11 |

Zones 1 and 2 peaked in August, whereas Zone 3 peaked in July.

Zone 3 also experienced a substantial decline in monthly average consumption between July and December.

**Business interpretation:** Seasonal monitoring should be performed independently for each zone. The unusual decline in Zone 3 should be investigated before drawing operational conclusions.

### Finding 4: Weekday Differences Are Relatively Small

The highest weekday averages occurred on:

- Wednesday for Zone 1.
- Thursday for Zone 2.
- Saturday for Zone 3.

Sunday recorded the lowest averages for Zones 1 and 2.

**Business interpretation:** Day-of-week analysis provides useful context for routine monitoring, although the hourly and monthly patterns showed more prominent differences.

### Finding 5: Temperature Has the Strongest Environmental Association

Pearson correlation results:

| Environmental Variable | Zone 1 | Zone 2 | Zone 3 |
|---|---:|---:|---:|
| Temperature | 0.44 | 0.38 | 0.49 |
| Humidity | -0.29 | -0.29 | -0.23 |
| Wind speed | 0.17 | 0.15 | 0.28 |

Temperature demonstrated moderate positive associations with consumption, while humidity demonstrated negative associations.

Wind speed showed weaker positive associations, with substantially weaker Spearman correlations.

**Business interpretation:** Temperature and humidity may be useful explanatory variables in further demand analysis. Their predictive value should be tested rather than assumed.

## 6. Business Recommendations

| Finding | Recommended Action | Suggested Performance Measure |
|---|---|---|
| Evening consumption peaks at 20:00 | Strengthen evening peak monitoring | Peak-hour average and peak-to-off-peak ratio |
| Zone 3 has the highest relative variability | Investigate zone-specific consumption changes | Coefficient of variation and monthly percentage change |
| Different monthly peaks across zones | Introduce zone-specific seasonal monitoring | Monthly average and month-on-month change |
| Temperature and humidity are associated with consumption | Investigate environmental variables in demand forecasting | Forecast error and model performance |
| Consumption varies by reporting period | Develop recurring management reporting | Reporting completion and significant deviations identified |

### Priority Actions

**Priority 1: Improve demand monitoring**

Establish hourly consumption monitoring, with particular attention to the 20:00 peak.

**Priority 2: Investigate Zone 3 variability**

Examine the higher relative variability and the decline in monthly averages observed during the second half of the year.

**Priority 3: Improve management reporting**

Develop a recurring reporting framework that compares consumption across zones and highlights significant changes.

**Priority 4: Investigate forecasting opportunities**

Use additional historical data and operational variables to assess whether environmental factors improve demand forecasting.

These recommendations are proposed actions. Their financial or operational impact has not been measured in this exploratory project.

## 7. Visualisation Catalogue

The following visualisations were produced.

| Visualisation | Analytical Purpose | File |
|---|---|---|
| Daily consumption trends | Examine changes in consumption over time | `daily_consumption_trends.html` |
| Average consumption by zone | Compare average consumption levels | `average_consumption_by_zone.png` |
| Hourly consumption patterns | Identify peak and low-demand hours | `hourly_consumption_patterns.html` |
| Monthly consumption patterns | Compare seasonal consumption trends | `monthly_consumption_patterns.html` |
| Weekday consumption comparison | Assess differences across weekdays | `weekday_consumption_comparison.png` |
| Environmental relationships | Examine environmental associations | `environmental_relationships.png` |
| Zone consumption distribution | Compare consumption distributions and variability | `zone_consumption_distribution.png` |
| Environmental correlation heatmap | Summarise Pearson correlations | `environmental_correlation_heatmap.png` |

Interactive HTML charts can be opened in a modern web browser.

## 8. Limitations and Further Work

The analysis has several limitations:

- The dataset covers one year, which limits longer-term trend assessment.
- The dataset ends on 30 December 2017 and does not include 31 December.
- The exact measurement-unit interpretation requires confirmation.
- Correlation does not establish causation.
- The dataset does not include electricity prices, customer numbers, generation information, outages or other operational variables.
- The project is descriptive and exploratory; no validated forecasting model was developed.

### Proposed Further Work

Future analysis could extend this project through:

1. Multi-year consumption comparisons to investigate longer-term trends.
2. Investigation of the July–December decline observed in Zone 3.
3. Integration of additional operational and economic variables.
4. Forecasting experiments with a proper time-based validation approach.
5. Development of a management dashboard for recurring consumption monitoring.

## 9. Reproducing the Analysis

### Prerequisites

Install Anaconda or Miniconda with Python and Jupyter Notebook.

Required libraries:

```python
%pip install pandas numpy matplotlib seaborn plotly
```

### Project Directory

```text
Morocco_Electricity_Consumption_and_Environmental_Factors_Analysis/
│
├── 01_raw_data/
│   ├── powerconsumption.csv
│   └── powerconsumption_datadictionary.csv
│
├── 02_processed_data/
│   └── cleaned_powerconsumption.csv
│
├── 03_notebooks/
│   └── Morocco_Electricity_Consumption_Analysis.ipynb
│
├── 04_visualisations/
│   ├── daily_consumption_trends.html
│   ├── average_consumption_by_zone.png
│   ├── hourly_consumption_patterns.html
│   ├── monthly_consumption_patterns.html
│   ├── weekday_consumption_comparison.png
│   ├── environmental_relationships.png
│   ├── zone_consumption_distribution.png
│   └── environmental_correlation_heatmap.png
│
├── 05_reports/
│   └── Morocco_Electricity_Consumption_Report.pdf
│
└── README.md
```

### Execution Instructions

**Step 1:** Download or clone the project and retain the folder structure.

**Step 2:** Ensure both original CSV files are available inside `01_raw_data`.

**Step 3:** Open Anaconda Navigator and launch Jupyter Notebook.

**Step 4:** Open `03_notebooks/Morocco_Electricity_Consumption_Analysis.ipynb`.

**Step 5:** Update the notebook's source and output directory paths to match the local project location.

**Step 6:** Install any missing dependencies using the installation command above.

**Step 7:** Run the notebook cells sequentially, beginning with data loading and ending with visualisation and analytical outputs.

**Step 8:** Review the generated tables, statistical results and visualisations.

The notebook contains the data preparation and analytical steps required to reproduce the project.

### Reproducibility Notes

- The original source data should remain unchanged.
- The notebook should be executed from beginning to end to recreate intermediate analytical variables.
- The environmental relationship visualisation uses a sample of 5,000 observations with a fixed random seed for reproducibility.
- Exported visualisations are stored in `04_visualisations`.
- The analysis uses descriptive statistics and correlation methods; it does not require a machine-learning training environment.

## 10. Project Deliverables

| Deliverable | Description |
|---|---|
| Jupyter Notebook | Reproducible analysis and execution workflow |
| Cleaned Dataset | Prepared dataset for further analysis |
| Visualisations | Eight static and interactive analytical charts |
| Business Insights and Recommendations | Evidence-based interpretation and proposed actions |
| Analytical Report | Management-oriented summary of findings |
| README | Project documentation and reproduction instructions |

## 11. Conclusion

This project demonstrates how structured data analysis can transform historical electricity consumption records into business-relevant insights.

By examining consumption levels, time-based patterns and environmental relationships, the analysis identified differences across zones and highlighted periods requiring closer monitoring.

The results provide a foundation for zone-specific reporting, improved demand monitoring and further forecasting investigations.

The project demonstrates an end-to-end analytical workflow: understanding the business problem, assessing data quality, preparing data, analysing patterns, communicating findings and translating evidence into recommended actions.

---

**Author:** Data Analytics Portfolio Project  
**Project Focus:** Energy Consumption Analytics and Business Intelligence