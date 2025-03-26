# Loan Analysis Dashboard

## Project Overview
This project is a **Loan Analysis Dashboard** built using **MS SQL Server** and **Power BI**. The dashboard provides insights into loan applications, funded amounts, interest rates, and various borrower attributes.

## Features
- **Data Extraction & SQL Queries**
  - Importing raw data into SQL Server
  - Querying key loan metrics (Total Loan Applications, Funded Amount, Interest Rates, DTI, Loan Status, etc.)
  - Regional and categorical analysis (State-wise trends, Loan Purpose, Home Ownership, etc.)
- **Power BI Dashboard**
  - Connecting Power BI to SQL Server
  - Data Cleaning, Modeling, and Relationships
  - Interactive visualizations with slicers and navigators
  - Monthly trends, loan term analysis, and borrower segmentation

## Technologies Used
- **Database:** MS SQL Server
- **Visualization:** Power BI
- **Languages:** SQL
- **Data Sources:** Loan Application Dataset (CSV/SQL Dump)
---

## Installation & Setup

### **Step 1: Set Up SQL Database**

1. **Create a new database** in MS SQL Server:
   ```sql
   CREATE DATABASE LoanAnalysis;
   ```
   
2. **Import the loan data** into SQL Server:
   ```sql
   BULK INSERT LoanData
   FROM 'C:\Path\to\LoanData.csv'
   WITH (FORMAT='CSV', FIRSTROW=2, FIELDTERMINATOR=',', ROWTERMINATOR='\n');
   ```
   
### **Step 2: Power BI Connection**
1. Open **Power BI Desktop**.
2. Click on **Get Data > SQL Server**.
3. Enter **Server Name** and **Database Name** (`LoanAnalysis`).
4. Load necessary tables for analysis.
---

## SQL Queries

### 1. Total Loan Applications
```sql
SELECT COUNT(*) AS Total_Loan_Applications FROM LoanData;
```

### 2. Total Funded Amount
```sql
SELECT SUM(FundedAmount) AS Total_Funded_Amount FROM LoanData;
```

### 3. Average Interest Rate
```sql
SELECT AVG(InterestRate) AS Avg_Interest_Rate FROM LoanData;
```

### 4. Good Loan vs Bad Loan Analysis
```sql
SELECT LoanStatus, SUM(FundedAmount) AS Total_Amount FROM LoanData
GROUP BY LoanStatus;
```

### 5. Monthly Loan Trends
```sql
SELECT FORMAT(IssueDate, 'yyyy-MM') AS Month, COUNT(*) AS Total_Loans
FROM LoanData
GROUP BY FORMAT(IssueDate, 'yyyy-MM');
```

## Power BI Dashboard Components

### 1. Data Modeling
- **Created relationships** between Loan Status, Borrower Info, and Loan Metrics.
- **Created a Date Table** for time-based analysis.

### 2. Visualizations
- **Loan Summary Metrics** (Total Loans, Funded Amount, Avg Interest Rate, Avg DTI)
- **Regional Analysis** (Loan distribution by state)
- **Good vs Bad Loan Segmentation**
- **Home Ownership Impact on Loans**
- **Monthly Trends** (Using line charts and slicers)

### 3. Interactive Features
- **Slicers** for filtering data by Loan Status, Loan Term, and State.
- **Navigation buttons** for switching between overview and detailed dashboards.
---

## Usage
1. Run the **SQL scripts** to set up the database.
2. Connect **Power BI** to the database and refresh the data.
3. Explore the dashboard and apply filters to gain insights.
---

## Folder Structure
```
Loan-Analysis-Dashboard/
│── SQL/
│   ├── Create_Database.sql
│   ├── Import_Data.sql
│   ├── Loan_Metrics.sql
│── PowerBI/
│   ├── LoanAnalysis.pbix
│── README.md
```

## Future Enhancements
- Integrate **Python for predictive analytics** (loan default predictions)
- **Automate ETL processes** for real-time dashboard updates
- Add **more advanced DAX calculations** in Power BI

## Author
Nahid Azad


