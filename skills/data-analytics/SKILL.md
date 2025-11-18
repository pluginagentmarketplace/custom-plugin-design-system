---
name: data-analytics
description: Master data analysis, visualization, and business intelligence using Python, SQL, and BI tools. Learn data exploration, statistical analysis, and machine learning fundamentals for data-driven decision making.
---

# Data Analytics & Science

## Quick Start

Data analytics transforms raw data into actionable insights.

### Python Data Analysis:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load and explore data
df = pd.read_csv('data.csv')
print(df.describe())

# Basic analysis
avg_sales = df['sales'].mean()
top_products = df.groupby('product')['sales'].sum().nlargest(5)

# Visualization
plt.scatter(df['date'], df['sales'])
plt.show()
```

### SQL for Analytics:

```sql
-- Analyze customer purchases
SELECT
  customer_id,
  COUNT(*) as purchase_count,
  SUM(amount) as total_spent,
  AVG(amount) as avg_purchase
FROM purchases
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 10;
```

### Tableau/Power BI:
- Create interactive dashboards
- Real-time data visualization
- Business intelligence reports

## Core Concepts

### 1. Data Exploration (EDA)

```python
# Check data quality
print(df.isnull().sum())  # Missing values
print(df.dtypes)          # Data types
print(df.duplicated().sum())  # Duplicates

# Statistical summary
print(df.describe())
print(df.corr())          # Correlation matrix
```

#### Key EDA Techniques
- Univariate analysis
- Bivariate analysis
- Outlier detection
- Distribution analysis
- Correlation analysis

### 2. Data Cleaning

```python
# Handle missing values
df = df.dropna()  # Remove rows
df = df.fillna(df.mean())  # Fill with mean

# Remove duplicates
df = df.drop_duplicates()

# Data type conversion
df['date'] = pd.to_datetime(df['date'])

# Outlier removal
df = df[df['value'].between(lower_quantile, upper_quantile)]
```

### 3. Statistical Analysis

#### Descriptive Statistics
- Mean, median, mode
- Standard deviation
- Variance
- Skewness and kurtosis
- Percentiles

#### Inferential Statistics
```python
from scipy import stats

# T-test
t_stat, p_value = stats.ttest_ind(group1, group2)

# Chi-square test
chi2, p_value = stats.chi2_contingency(contingency_table)[:2]

# Correlation test
correlation, p_value = stats.pearsonr(x, y)
```

### 4. Data Visualization

#### Python Libraries
- **Matplotlib**: Basic plotting
- **Seaborn**: Statistical visualization
- **Plotly**: Interactive charts
- **Bokeh**: Large dataset visualization

```python
import seaborn as sns

# Scatter plot
sns.scatterplot(data=df, x='feature1', y='feature2', hue='category')

# Distribution
sns.histplot(df['value'], kde=True)

# Correlation heatmap
sns.heatmap(df.corr(), annot=True)
```

### 5. BI Tools

#### Tableau
- Dashboards and workbooks
- Real-time data sources
- Interactive filters
- Storytelling with data

#### Power BI
- Power Query for data prep
- DAX formulas
- Visual analytics
- Report publishing

### 6. SQL for Analytics

#### Window Functions
```sql
SELECT
  date,
  sales,
  SUM(sales) OVER (ORDER BY date) as running_total,
  LAG(sales) OVER (ORDER BY date) as prev_sales,
  ROW_NUMBER() OVER (PARTITION BY category ORDER BY sales DESC) as rank
FROM daily_sales;
```

#### Common Table Expressions (CTEs)
```sql
WITH monthly_sales AS (
  SELECT
    DATE_TRUNC('month', date) as month,
    SUM(amount) as total
  FROM sales
  GROUP BY DATE_TRUNC('month', date)
)
SELECT * FROM monthly_sales WHERE total > 10000;
```

## Advanced Topics

### Machine Learning for Analytics
- Clustering (K-means, hierarchical)
- Classification
- Regression for prediction
- Feature engineering
- Model evaluation

### Big Data Analytics
- Apache Spark for large datasets
- Data warehousing (Snowflake, BigQuery)
- Data lakes architecture
- Streaming analytics

### Analytics Engineering
- dbt (data build tool)
- Data pipeline orchestration
- Dimensional modeling
- Metrics definition

## Real-World Projects

1. **Sales Dashboard** - Track KPIs and trends
2. **Customer Segmentation** - Identify customer groups
3. **Predictive Analytics** - Forecast sales or churn
4. **A/B Testing Analysis** - Statistical test results
5. **Revenue Analysis** - Multi-dimensional analysis

---

**Use this skill when:**
- Analyzing business data
- Creating dashboards
- Performing statistical tests
- Learning BI tools
- Data exploration and quality
