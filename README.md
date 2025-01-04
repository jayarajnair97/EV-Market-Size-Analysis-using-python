# EV-Market-Size-Analysis-using-python
# Electric Vehicle (EV) Market Size Analysis

## Scope of the Study
The electric vehicle (EV) market is rapidly expanding, driven by technological advancements, environmental concerns, and shifting consumer preferences. This study aims to analyze the market size, adoption trends, and key factors influencing EV growth using real-world data. By examining the dataset of registered EVs, this project provides insights into adoption patterns, geographical distribution, popular manufacturers, and advancements in EV technology. It also includes projections for future market growth based on historical trends.

---

## Dataset Overview
- **Dataset Name:** Electric Vehicle Population Data
- **Columns:**
  - Model Year
  - County
  - City
  - Make
  - Model
  - Electric Vehicle Type (BEV, PHEV, etc.)
  - Electric Range
- **Primary Focus:** Analyze EV registrations across years, geographies, and manufacturers to forecast future trends.

---

## Analysis Steps

### 1. Data Preprocessing
- Loaded the dataset using Pandas.
- Checked for null values and removed incomplete rows.

```python
import pandas as pd

ev_data = pd.read_csv('Electric_Vehicle_Population_Data.csv')
ev_data = ev_data.dropna()
```

---

### 2. EV Adoption Over Time
- Visualized the number of EVs registered by model year to analyze growth trends.

```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style("whitegrid")
ev_adoption_by_year = ev_data['Model Year'].value_counts().sort_index()
sns.barplot(x=ev_adoption_by_year.index, y=ev_adoption_by_year.values, palette="viridis")
plt.title('EV Adoption Over Time')
plt.xlabel('Model Year')
plt.ylabel('Number of Vehicles Registered')
plt.show()
```

**Findings:**
- Significant upward trend starting around 2016.
- Peak adoption in 2023.

---

### 3. Geographical Distribution
- Analyzed EV registrations at the county and city levels.

```python
ev_county_distribution = ev_data['County'].value_counts().head(3).index
top_counties_data = ev_data[ev_data['County'].isin(ev_county_distribution)]
```

**Visualization:** Top cities in top counties by EV registrations.

---

### 4. EV Types Distribution
- Explored consumer preferences for BEVs vs. PHEVs.

```python
ev_type_distribution = ev_data['Electric Vehicle Type'].value_counts()
sns.barplot(x=ev_type_distribution.values, y=ev_type_distribution.index, palette="rocket")
```

**Findings:**
- BEVs are more popular than PHEVs.

---

### 5. Manufacturer and Model Popularity
- Identified top manufacturers and their most popular models.

```python
ev_make_distribution = ev_data['Make'].value_counts().head(10)
top_makes_data = ev_data[ev_data['Make'].isin(ev_make_distribution.index)]
```

**Findings:**
- TESLA dominates the market.
- TESLA MODEL Y and MODEL 3 lead among models.

---

### 6. Electric Range Analysis
- Analyzed the distribution and progression of EV ranges over time.

```python
sns.histplot(ev_data['Electric Range'], bins=30, kde=True, color='royalblue')
plt.axvline(ev_data['Electric Range'].mean(), color='red', linestyle='--')
plt.show()
```

**Findings:**
- Average range is improving over time.
- TESLA models lead in range capabilities.

---

### 7. Market Size Estimation
- Used exponential growth models to forecast future EV registrations.

```python
from scipy.optimize import curve_fit
import numpy as np

# Curve fitting and forecasting
params, _ = curve_fit(lambda x, a, b: a * np.exp(b * x), x_data, y_data)
forecasted_values = exp_growth(forecast_years, *params)
```

**Visualization:**
- Graph showing actual and forecasted EV registrations.

---

## Key Takeaways
1. EV adoption is accelerating, with TESLA leading the market.
2. King County dominates in geographical EV registrations.
3. Significant improvements in electric range over the years.
4. The EV market is poised for exponential growth, with substantial investment opportunities.

---

## Future Scope
- **Policy Impact Analysis:** Examine the influence of government incentives on EV adoption.
- **Consumer Behavior Study:** Analyze preferences for EV features.
- **Global Trends:** Compare EV adoption patterns across countries.

---

### Repository Structure
- **Data:** Electric_Vehicle_Population_Data.csv
- **Scripts:** Python scripts for data preprocessing and analysis.
- **Visualizations:** PNG files for all generated charts.
- **README.md:** Detailed documentation.

---

### Author
[Jayaraj K] - Data Analyst passionate about leveraging data-driven insights for sustainable growth.
