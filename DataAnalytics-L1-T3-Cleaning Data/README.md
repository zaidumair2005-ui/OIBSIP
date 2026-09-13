# Data Cleaning — Online Retail Dataset

## Project Overview

This project focuses on cleaning and preparing a messy retail transaction dataset for reliable analysis.

The dataset contains online retail transactions with information about invoices, products, quantities, prices, customers, dates, and countries. The goal was to identify data-quality issues, apply appropriate cleaning strategies, validate the results, and produce a clean dataset suitable for further analysis.

This project was completed as part of the **OASIS Infobyte Data Analytics Internship — Task 3 (Level 1: Cleaning Data).**

---

## Objectives

The main objectives were to:

* Identify missing values and determine appropriate handling strategies.
* Detect and remove exact duplicate records.
* Standardize inconsistent text formatting.
* Investigate unusual and invalid numeric values.
* Detect statistical outliers using the IQR method.
* Correct inappropriate data types.
* Validate the dataset before and after cleaning.
* Export the final cleaned dataset as a new CSV file.

---

## Dataset

The dataset contains **525,461 transaction records** and **8 columns**:

| Column        | Description                       |
| ------------- | --------------------------------- |
| `Invoice`     | Invoice or transaction identifier |
| `StockCode`   | Product identifier                |
| `Description` | Product description               |
| `Quantity`    | Number of products purchased      |
| `InvoiceDate` | Date and time of the transaction  |
| `Price`       | Unit price of the product         |
| `Customer ID` | Customer identifier               |
| `Country`     | Customer's country                |

The dataset covers transactions from **December 2009 to December 2010**.

---

## Data Quality Issues Identified

The initial assessment identified several data-quality problems:

* **110,855 missing values**
* **6,865 exact duplicate rows**
* Missing `Customer ID` values
* Missing `Description` values
* Negative quantities
* Negative and zero prices
* Statistical outliers in `Quantity` and `Price`
* Inconsistent whitespace in text fields
* `Customer ID` stored as a numeric type even though it represents an identifier

---

## Cleaning Process

### 1. Missing Values

Missing values were handled according to the meaning of each column rather than using one strategy for the entire dataset.

#### Customer ID

There were **107,927 missing Customer ID values** in the original dataset.

Investigation showed that the affected records belonged to invoices where the Customer ID was missing for the entire invoice. Therefore, the customer identity could not be reliably recovered.

**Decision:** Remove records with missing Customer ID.

Mean, median, mode, and forward-fill methods were not appropriate because they could create incorrect customer identities.

#### Description

There were **2,928 missing product descriptions**.

A StockCode-based investigation found that **2,150 records** could be reliably recovered because their StockCode was associated with exactly one known description elsewhere in the dataset.

The remaining **778 records** could not be reliably recovered and were removed.

---

### 2. Duplicate Removal

Exact duplicate rows were identified using all eight columns.

* Duplicate rows before cleaning: **6,865**
* Duplicate rows remaining after cleaning: **0**

Only exact duplicates were removed. Records that shared individual values but represented different transactions were retained.

---

### 3. Text Standardization

Leading and trailing whitespace was removed from:

* `Invoice`
* `StockCode`
* `Description`
* `Country`

Capitalization was not arbitrarily changed because differences in capitalization did not necessarily represent data errors.

After standardization, no leading or trailing whitespace remained.

---

### 4. Numeric Data Validation

`Quantity` and `Price` were investigated for unusual values.

Negative quantities were retained because they correspond to legitimate business events such as cancellations and returns. In particular, many negative quantities were associated with cancellation invoices beginning with `C`.

Three negative-price records associated with **"Adjust bad debt"** entries were identified during the initial quality assessment. They did not remain in the final dataset after missing-value filtering.

Zero-price records were not automatically removed because some represented legitimate non-standard business transactions.

---

### 5. Outlier Detection

The **Interquartile Range (IQR)** method was applied to `Quantity` and `Price`.

| Variable | Outliers Detected | Outliers Removed |
| -------- | ----------------: | ---------------: |
| Quantity |            27,342 |                0 |
| Price    |            34,703 |                0 |

The detected outliers were inspected before making a decision.

Many unusual `Quantity` values represented legitimate returns, cancellations, or bulk purchases. Similarly, many higher `Price` values represented valid products rather than data-entry errors.

**Decision:** Retain all IQR-detected outliers.

This avoids distorting legitimate transaction data simply because values are statistically unusual.

---

### 6. Data Type Correction

The final dataset uses the following data types:

| Column        | Final Type |
| ------------- | ---------- |
| `Invoice`     | string     |
| `StockCode`   | string     |
| `Description` | string     |
| `Quantity`    | int64      |
| `InvoiceDate` | datetime64 |
| `Price`       | float64    |
| `Customer ID` | string     |
| `Country`     | string     |

All **8 of 8 columns** passed the final data-type validation.

---

## Before vs. After

| Metric                    | Before Cleaning | After Cleaning |
| ------------------------- | --------------: | -------------: |
| Rows                      |         525,461 |        410,763 |
| Columns                   |               8 |              8 |
| Total Missing Values      |         110,855 |              0 |
| Duplicate Rows            |           6,865 |              0 |
| Quantity Outliers Removed |               — |              0 |
| Price Outliers Removed    |               — |              0 |
| Correct Data Types        |               — |            8/8 |

The final dataset contains **410,763 rows**, meaning approximately **78.2% of the original records were retained**.

---

## Final Validation

The cleaned dataset was validated to ensure:

* No missing values remain.
* No exact duplicate rows remain.
* All columns have the expected data types.
* No negative prices remain.
* No zero quantities remain.
* Text fields contain no leading or trailing whitespace.
* Transaction dates remain within the original dataset's date range.
* Legitimate negative quantities representing returns/cancellations were preserved.

---

## Project Files

```text
DataAnalytics-L1-CleaningData/
│
├── README.md
├── Data_Cleaning_Task3.ipynb
└── cleaned_online_retail.csv
```

### Files included

**`Data_Cleaning_Task3.ipynb`**
Contains the complete data-cleaning workflow, analysis, validation, and documented decisions.

**`cleaned_online_retail.csv`**
The final cleaned dataset produced by the notebook.

---

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook / Google Colab

---

## Key Takeaway

Data cleaning is not simply about deleting missing, unusual, or extreme values.

A value that looks abnormal statistically may still represent a legitimate business event. In this project, contextual investigation showed that negative quantities could represent returns or cancellations, while high prices and large quantities could represent valid transactions.

The cleaning process therefore combined **statistical techniques with business-context reasoning** to produce a more reliable analysis-ready dataset.
