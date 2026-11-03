# 📊 Excel Assignment 2 – Data Exploration & Transformation

> **Course:** AI-Driven Data Analytics  
> **Student:** Rasika Thiruppathi  
> **Workstation:** Windows OS | Microsoft Excel & Power Query  
> **Status:** 🟢 Completed (Project 01 of 25 Portfolio Target)

---

## 📌 Project Overview
This project focuses on auditing, cleaning, and transforming an raw product database (`product_db`) into an executive-ready, visually formatted Excel spreadsheet. The core objectives were to resolve missing data points, standardize inconsistent text attributes, eliminate duplicate entries, parse compound product variables, and apply conditional formatting rules for visual reporting.

The full data cleaning pipeline was executed in **Power Query**, with final reporting and conditional formatting applied directly in **Microsoft Excel**.

---

## 🎯 Key Objectives & Deliverables
1. **Data Exploration & Audit:** Identify incomplete records, inconsistent text casing, duplicate rows, and compound strings.
2. **Missing Value Imputation:** Resolve `null` values in categorical fields to restore dataset completeness.
3. **Data Standardization:** Correct irregular formatting using *Find & Replace* and text transformation utilities.
4. **Data Deduplication:** Audit and purge duplicate records to prevent metric inflation.
5. **Attribute Normalization:** Parse composite product keys into individual fields and merge related brand/product text fields.
6. **Visual Reporting:** Implement dynamic conditional formatting (Data Bars and Category Highlighting) for quick business analysis.

---

## 🛠️ Data Cleaning & Transformation Workflow

### 1. Missing Value Handling
* **Issue:** Several rows in the `Category` column contained `null` or blank values.
* **Resolution:** Evaluated each missing entry against corresponding product attributes (`Product Name`). Missing values were populated with their accurate parent categories (*Electronics*, *Fashion*, *Kitchen*, *Outdoor*) to ensure 100% categorical coverage without corrupting pre-existing records.

### 2. Find and Replace Corrections
* **Issue:** Text formatting inconsistencies and casing irregularities existed across product names and brand labels.
* **Resolution:** Executed text trimming, casing standardization, and targeted **Replace Values** operations to align all string entries to uniform naming conventions. This prevents misgrouping during downstream pivot table analysis.

### 3. Duplicate Removal Process
* **Issue:** Duplicate rows were present, posing a risk of double-counting total revenue, inventory counts, and price averages.
* **Resolution:** Applied the **Remove Duplicates** transformation in Power Query to audit unique primary keys. All redundant entries were permanently removed from the data model.

### 4. Column Splitting and Merging
* **Column Splitting (`Product ID`):** Parsed composite product strings (e.g., `28-JAN-US`) using hyphen delimiters (`-`) to isolate distinct variables:
  * `Day`
  * `Month`
  * `Country Code`
* **Column Merging (`Product Brand`):** Combined the `Brand` and `Product Name` text columns using space delimiters to create a single, clean visual label for summary reports.

### 5. Conditional Formatting & Final Formatting
After executing **Close & Load** to export the cleaned table from Power Query into Microsoft Excel:
* **Date Standardization:** Standardized the `Manufacturing Date` column format to display as `DD-MM-YYYY`.
* **Price Distribution (Data Bars):** Applied **Data Bars** to the `Price ($)` column to enable visual comparison of item pricing at a glance.
* **Category Highlighting (Custom Rule):** Created a text-based conditional formatting rule (`Text that Contains: "Electronics"`) with custom fill shading to immediately highlight high-priority technology inventory.

---

## 📁 Repository File Structure

```text
├── data/
│   ├── raw_product_db.xlsx         # Original uncleaned dataset
│   └── cleaned_product_db.xlsx     # Final transformed Excel workbook
├── docs/
│   └── Data_Cleaning_Report.pdf    # PDF submission with step-by-step screenshots
└── README.md                       # Project documentation
