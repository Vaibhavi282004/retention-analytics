# Customer Retention & Repeat-Order Analytics

## 📌 Project Overview

Customer Retention & Repeat-Order Analytics is a data analytics project designed to understand customer purchasing behavior and identify patterns related to repeat orders.

The project analyzes customer order history to answer business questions such as:

- Which customers are more likely to place repeat orders?
- How frequently do customers place orders?
- How many days are there between customer orders?
- Which customer segments are more active?
- Which product departments have higher reorder rates?
- Where can the business focus its customer-retention efforts?

The project uses Python, SQL and SQLite for data processing and analysis and provides an interactive dashboard for exploring the results.

---

## 🎯 Business Problem

For an e-commerce business, retaining existing customers is important because repeat customers can contribute significantly to future sales.

However, customers do not behave in the same way. Some customers order frequently, while others order only occasionally. Understanding these differences can help a business identify valuable customers and customers who may require additional retention efforts.

This project uses customer order history to segment customers based on their ordering behavior and analyze repeat-purchase patterns.

---

## 🛠️ Technologies Used

### Programming & Data Analysis
- Python
- Pandas
- NumPy

### Database & SQL
- SQLite
- SQL
- CTEs
- Window Functions
- Aggregations
- Joins

### Dashboard & Reporting
- HTML
- JavaScript
- Interactive charts
- Excel VBA

### Development Tools
- Git
- GitHub
- VS Code
- Command Prompt

---

## 📊 Dataset

The project is designed around the Instacart-style customer order dataset.

The dataset contains information related to:

- Customers
- Orders
- Products
- Departments
- Order-product relationships

The analysis uses customer order history to understand purchasing frequency and repeat-order behavior.

> **Note:** The current version of the project may use sample/test data when the original dataset is not available. Results generated from sample data should not be interpreted as real business results.

---

## 🔄 Project Workflow

The project follows an end-to-end analytics workflow:

```text
Raw Data
   ↓
Data Cleaning
   ↓
Data Validation
   ↓
SQLite Database
   ↓
SQL Analysis
   ↓
Customer Segmentation
   ↓
Retention Analysis
   ↓
Dashboard
   ↓
Business Insights
```

---

## 🧹 Data Processing

Python is used to prepare the data before analysis.

The processing stage includes:

- Loading CSV files
- Checking the structure of datasets
- Handling missing values
- Removing duplicate records
- Validating important fields
- Preparing data for database loading
- Creating analysis-ready datasets

Pandas is mainly used for data manipulation and preparation.

---

## 🗄️ Database

The processed data is loaded into a SQLite database.

The database structure allows different datasets to be connected using common identifiers such as:

- Customer ID
- Order ID
- Product ID
- Department ID

SQL is then used to combine and analyze these tables.

---

## 🔎 SQL Analysis

SQL is used to perform different types of analysis, including:

### Customer Analysis

- Number of orders per customer
- Customer ordering frequency
- Customer order history
- Customer segmentation

### Retention Analysis

- Repeat-order behavior
- Reorder rate
- Days between orders
- Customer ordering patterns

### Product Analysis

- Department-level reorder rates
- Product purchasing patterns
- Repeat-order behavior across departments

SQL techniques used in the project include:

- `SELECT`
- `WHERE`
- `GROUP BY`
- `ORDER BY`
- `JOIN`
- `CASE`
- CTEs
- Window functions
- Aggregations

---

## 👥 Customer Segmentation

Customers are grouped into different segments according to their ordering behavior.

The project uses the following segments:

### 🏆 Champions

Customers with frequent ordering behavior and strong repeat-purchase activity.

### ⭐ Loyal

Customers who regularly place orders and show consistent purchasing behavior.

### 👤 Regular

Customers with moderate ordering activity.

### 🌱 Light

Customers with relatively fewer orders.

### ⚠️ At-Risk

Customers whose ordering behavior indicates lower or less frequent activity.

The purpose of segmentation is to make the analysis easier to understand and help identify groups that may require different retention strategies.

---

## 📈 Dashboard
