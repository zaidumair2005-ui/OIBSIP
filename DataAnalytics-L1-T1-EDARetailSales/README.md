# OASIS Infobyte - Retail Sales Exploratory Data Analysis

## Project Overview

This project was completed as part of the **OASIS Infobyte Data Analytics Internship**.

The objective of this project is to perform Exploratory Data Analysis (EDA) on retail sales data to identify sales trends, customer behavior patterns, product performance, and actionable business insights.

The analysis was conducted using Python, Pandas, Matplotlib, Seaborn, and Jupyter Notebook.

---

## Objectives

The main objectives of this analysis were to:

- Understand the structure and quality of the retail sales dataset
- Identify and handle duplicate records
- Calculate descriptive statistics for numerical variables
- Analyze monthly and quarterly revenue trends
- Examine transaction activity across different age groups and genders
- Identify the top 10 best-selling products
- Analyze revenue contribution by product category
- Examine relationships between numerical variables using correlation analysis
- Identify differences in profit margins across product categories
- Generate actionable business recommendations based on the findings

---

## Dataset

**Dataset:** Customer Segmentation and Sales Data

The dataset contains retail transaction-level information, including:

- Date
- Customer Age
- Age Group
- Customer Gender
- Country
- State
- Product Category
- Sub-Category
- Product
- Order Quantity
- Unit Cost
- Unit Price
- Profit
- Cost
- Revenue

### Dataset Size

- Original records: **113,036**
- Duplicate records removed: **1,000**
- Final records analyzed: **112,036**
- Total columns: **18**
- Missing values: **0**

---

## Tools and Technologies

- **Python**
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical operations
- **Matplotlib** - Data visualization
- **Seaborn** - Statistical visualization
- **Jupyter Notebook / Google Colab** - Development environment

---

## Analysis Performed

### 1. Data Inspection and Quality Check

The dataset was inspected for:

- Number of rows and columns
- Column names
- Data types
- Missing values
- Duplicate records

The dataset contained no missing values. A total of **1,000 exact duplicate records** were identified and removed before further analysis.

### 2. Descriptive Statistics

Mean, median, mode, and standard deviation were calculated for the numerical variables to understand their central tendency and variation.

### 3. Sales Trend Analysis

Monthly and quarterly revenue trends were analyzed to identify changes in sales activity over time.

The analysis showed substantially stronger revenue levels during the later years of the dataset. Some periods contained no transaction records or represented partial quarters, which were considered when interpreting the trends.

### 4. Customer Analysis

Transaction activity was analyzed by age group and gender.

The largest number of transaction records came from:

- **Adults (35–64): 55,358**
- **Young Adults (25–34): 38,299**

Transaction activity was also relatively balanced between genders.

### 5. Best-Selling Products

Products were ranked according to total units sold.

The top-selling products included:

1. Water Bottle - 30 oz.
2. Patch Kit/8 Patches
3. Mountain Tire Tube
4. AWC Logo Cap
5. Sport-100 Helmet, Red
6. Fender Set - Mountain
7. Sport-100 Helmet, Black
8. Road Tire Tube
9. Sport-100 Helmet, Blue
10. Touring Tire Tube

The **Water Bottle - 30 oz.** recorded the highest total quantity sold at **162,051 units**.

### 6. Revenue by Product Category

Bikes were the dominant revenue-generating category.

| Product Category | Revenue |
|---|---:|
| Bikes | 61,434,484 |
| Accessories | 15,022,766 |
| Clothing | 8,369,522 |

Bikes generated approximately **72.4% of total revenue**, making them the primary revenue driver.

### 7. Correlation Analysis

A correlation matrix and heatmap were used to examine relationships between numerical variables.

Some notable relationships included:

- Revenue and Cost: **0.99**
- Revenue and Profit: **0.96**
- Profit and Cost: **0.90**
- Revenue and Unit Cost: **0.82**
- Revenue and Unit Price: **0.82**
- Revenue and Customer Age: **-0.01**

The results indicate strong relationships among the financial variables, while customer age showed almost no linear relationship with revenue.

### 8. Profit Margin Analysis

Profit margin was calculated for each product category to compare profitability relative to revenue.

| Product Category | Revenue | Profit | Profit Margin |
|---|---:|---:|---:|
| Accessories | 15,022,766 | 8,807,194 | **58.63%** |
| Clothing | 8,369,522 | 2,839,319 | **33.92%** |
| Bikes | 61,434,484 | 20,399,726 | **33.21%** |

Although Bikes generate the highest total revenue and absolute profit, **Accessories have the highest profit margin at 58.63%**.

---

## Key Insights

The analysis produced several important business insights:

- Revenue activity increased substantially during the later years of the dataset.
- Adults aged 35–64 and Young Adults aged 25–34 account for the largest share of transaction records.
- Transaction activity is relatively balanced between male and female customers.
- The Water Bottle - 30 oz. is the highest-selling product by quantity.
- Bikes generate the majority of total revenue, contributing approximately 72.4%.
- Accessories have the highest profit margin at 58.63%.
- Financial variables such as Revenue, Cost, and Profit show strong positive correlations.
- Customer Age has almost no linear correlation with Revenue in this dataset.

---

## Actionable Recommendations

### 1. Expand High-Margin Accessories Opportunities

Accessories have the highest profit margin at **58.63%**. The business could increase their visibility through product bundles, promotions, and cross-selling alongside Bike purchases.

### 2. Protect and Strengthen the Bike Category

Bikes are the company's primary revenue driver, generating **61.43 million** in revenue. Maintaining strong inventory availability and monitoring Bike sales performance should remain a priority.

### 3. Focus Marketing on the Most Active Age Groups

Adults (35–64) and Young Adults (25–34) account for the largest number of transaction records. Marketing campaigns and product recommendations could prioritize these customer segments while testing targeted strategies for less represented age groups.

---

## Project Structure

```text
DataAnalytics-L1-EDARetailSales/
│
├── README.md
├── OASIS_Task1_Retail_Sales_EDA.ipynb
│
├── data/
│   ├── Customer_Segmentation_py.csv
│   └── retail_sales_cleaned.csv
│
├── outputs/
│   ├── monthly_sales.png
│   ├── quarterly_sales.png
│   ├── age_groups.png
│   ├── gender_distribution.png
│   ├── top_products.png
│   ├── revenue_by_category.png
│   ├── correlation_heatmap.png
│   └── profit_margin_by_category.png
│
└── screenshots/
    └── [project screenshots]

    
### One thing I deliberately did **not** include

I didn't add claims such as:

> "The business should discontinue Clothing."

or

> "Accessories should become the company's main focus."

Our analysis **doesn't support those conclusions**. Accessories have the highest *margin*, but Bikes still generate substantially more absolute revenue and profit. Keeping that distinction makes the README analytically credible.

### Your README is now essentially ready

Your project will have three different layers:

**`OASIS_Task1_Retail_Sales_EDA.ipynb`**  
→ Shows the complete analytical process.

**`outputs/`**  
→ Shows the polished visual results.

**`README.md`**  
→ Explains the project and summarizes the findings for someone viewing your GitHub portfolio.

The only remaining piece before we assemble everything is **creating the actual `outputs/` PNG files and the selected screenshots**.