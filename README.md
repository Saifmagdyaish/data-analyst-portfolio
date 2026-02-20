# Data Analyst Portfolio

Hi, I'm Saif  
Aspiring Data Analyst passionate about turning data into actionable insights.

## Skills
- **Excel (Advanced)**
- SQL (Good)
- Python (Good)
- Power BI (Good)
- Data Cleaning
- Data Visualization

## Projects

### 1. Sales Data Analysis (Excel + Python)
📥 Dataset
Superstore Sales dataset
https://www.kaggle.com/datasets/sagnik1511/superstore-sales-data�
📊 Excel File
You create sales_analysis.xlsx with:
Pivot tables
Top products & regions
Sales trends by month
Example Sheets:
Summary
Pivot Tables
Charts
🐍 Python Notebook (superstore_analysis.ipynb)
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel("Superstore Sales.xlsx")

# sales by month
df["Order Date"] = pd.to_datetime(df["Order Date"])
df["Month"] = df["Order Date"].dt.to_period("M")
monthly_sales = df.groupby("Month")["Sales"].sum()

monthly_sales.plot(kind="bar", figsize=(10,5))
plt.title("Sales by Month")
plt.show()

### 2. Customer Segmentation (SQL)
📥 Dataset
E‑commerce Customer data
https://www.kaggle.com/datasets/akram24/ecommerce-customers�
📄 SQL Script (customer_segmentation.sql)
-- Top 10 Countries by Revenue
SELECT Country, SUM(TotalRevenue) AS Revenue
FROM ecommerce_customers
GROUP BY Country
ORDER BY Revenue DESC
LIMIT 10;

-- RFM analysis
SELECT
 CustomerID,
 SUM(TotalRevenue) AS Monetary,
 COUNT(OrderID) AS Frequency,
 MAX(OrderDate) AS Recency
FROM ecommerce_customers
GROUP BY CustomerID;

### 3. Netflix Data Analysis (Python)
Dataset
Netflix Movies & TV Shows
https://www.kaggle.com/datasets/shivamb/netflix-shows�
🐍 Python Notebook (netflix_analysis.ipynb)
import pandas as pd
import seaborn as sns

df = pd.read_csv("netflix_titles.csv")

# Most common genres
genres = df["listed_in"].str.split(", ").explode().value_counts().head(10)
sns.barplot(x=genres.values, y=genres.index)

### 4. Superstore Dashboard (Power BI)
📥 Dataset (Real)
Same Superstore dataset
📊 Power BI file (superstore_dashboard.pbix)
Include visuals: ✅ Sales by Category
✅ Profit vs Sales
✅ Region KPIs
✅ Filters by segment

### 5. Bank Transactions Analysis
📥 Dataset
Bank Marketing dataset
https://www.kaggle.com/datasets/ajay1735/bank-marketing�
🐍 Python Notebook (bank_analysis.ipynb)
import pandas as pd
df = pd.read_csv("bank-additional-full.csv", sep=";")

# Spending patterns
df["age_group"] = pd.cut(df["age"], bins=[17,30,45,60,100])
print(df.groupby("age_group")["balance"].mean())
