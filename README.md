# Comprehensive Financial Analysis and Reporting using Excel and PowerQuery 

## Table of Contents
1. [Problem Statement](#problem-statement)
2. [Data Sourcing](#data-sourcing)
3. [Data Preparation](#data-preparation)
4. [Data Modeling](#data-modeling)
5. [Data Visualization](#data-visualization)
6. [Data Analysis](#data-analysis)
7. [Insights](#insights)
8. [Challenges Faced and How They Were Overcome](#challenges-faced-and-how-they-were-overcome)


## Problem Statement
The objective of this analysis is to assist the client in unlocking the potential of financial analysis and reporting. The goal is to produce comprehensive insights into the client's finances using her financial data.

## Data Sourcing
The dataset used for this analysis was provided by our professor extracted frm one of the public datasets domains. Attached the dataset for reference: 

## Data Preparation
The data transformation was performed in Power Query and the dataset was loaded into Microsoft Excel Power Pivot for modeling. The client's financial data consists of two worksheets containing two tables:

1. **Transactions Table**
   - Contains 4 columns and 296 rows of observations.
   - Columns:
     - `Date`: Represents the date of the transaction.
     - `Description`: Describes the transaction narration.
     - `Category`: Describes the category of the transaction.
     - `Amount`: Represents the amount of the transaction.

2. **Budget Table**
   - Contains 15 columns and 24 rows of observations.
   - Columns:
     - `Category`: Describes the category of the budget.
     - `Class`: Describes the class of the budget.
     - `Type`: Describes the type of the budget.
     - `Jan 2021 - Dec 2021`: Represents the budget amount for each month respectively.

### Data Cleaning
Data cleaning was performed in Power Query:

- For the Budget table, the columns from January 2021 to December 2021 were unpivoted.
- The resulting `Attribute` and `Value` columns were renamed to `Date` and `Amount` respectively.
- The `Date` column's accuracy was validated by changing its type to date only.
- The `Amount` column's accuracy was validated by changing its type to a whole number.
- A dimension table named `Categories` was created by referencing the Budget table.
- Unnecessary columns were removed from the Categories table.
- Duplicate rows were removed from the Categories table.

To ensure the accuracy of the dates in the Date column each of the tables, a date table was created for referencing using the M-formula:

{Number.From(List.Min(Transactions[Date]))..Number.From(List.Max(Transactions[Date]))}

Here is a breakdown of what the formula does:

For the dataset, we want the start date to reflect the earliest to latest date that we have in the data: January 01, 2021 - December 01, 2021.

Month, Month Name, Year columns were extracted from the date table

The date table was named Calender.

### Data Modeling
After cleaning and transforming the dataset, it was ready for modeling using Power Pivot:

The Calendar table was marked as the official date table.
Relationships were created:
A one-to-many (*:1) relationship between the Budget and Calendar tables using the Date column.
A one-to-many (*:1) relationship between the Transactions and Calendar tables using the Date column.
A one-to-many (*:1) relationship between the Transactions and Categories tables using the Category column.
A one-to-many (*:1) relationship between the Budget and Categories tables using the Category column.
The relationships formed in the data model represent a Star Schema.

### Data Visualization
Data visualization was performed using Microsoft Excel:

### Dashboard Worksheet: Displays the actual amount, budget amount, balance, etc., of the client.
Figure 1 shows visualizations from the Dashboard worksheet.
![1](https://github.com/shivanibadinehal/Project-Finance-/assets/127629111/e23a8ea9-d799-44fa-905e-978cd872e60c)

### Data Analysis
The measures used in visualization include:

Actual = SUM(Transactions[Amount])
Balance = SUM(Budget[Amount])
Balance = [Budget] - [Actual]
Based on the data visualization, the following can be deduced for the year ending December 2021:

The client budgeted a total amount of $230,502.
The client spent a total amount of $193,228.
The client has a balance of $37,274.
Insights
The analysis reveals the following insights:

The client spent the most in the month of January.
The client spent the least in the month of November.
The highest spending category was Social.
Key Note: The client has a monthly budget amount of more than $16k and has been able to stay within this budget, indicating financial stability sufficient for monetary investment.

## Challenges Faced and How They Were Overcome
### Data Quality and Consistency
### Challenge: The initial dataset had inconsistencies, such as missing values, varying date formats, and duplicate entries, which could affect the accuracy of the analysis.
### Solution:
Missing values were identified and appropriately handled by either filling in with relevant data or removing incomplete entries.
Date formats were standardized using Power Query to ensure consistency across the dataset.
Duplicate rows were identified and removed from the Categories table to maintain data integrity.

### Data Transformation
### Challenge: The Budget table had a wide format with monthly columns that needed to be transformed into a long format for effective analysis.
### Solution:
The columns from January 2021 to December 2021 were unpivoted in Power Query to create a Date column and an Amount column. This transformation facilitated easier aggregation and comparison of budget data.

### Relationship Establishment
### Challenge: Establishing correct relationships between tables in the data model was crucial for accurate analysis but was initially complex due to different formats and categorizations.
### Solution:
A Calendar table was created and marked as the official date table to standardize date references.
Clear relationships were defined using common columns (Date and Category) to link the Transactions, Budget, Categories, and Calendar tables, forming a Star Schema for efficient data querying.

### Data Accuracy
### Challenge: Ensuring the accuracy of transformed data, especially the Date and Amount columns, was critical to the reliability of the analysis.
### Solution:
Data types for the Date and Amount columns were validated and converted to appropriate formats (date type and whole number) in Power Query.
A custom M-formula was used to create a Date table, ensuring that it covered the complete range of transaction dates for comprehensive analysis.
Complex Calculations
Challenge: Performing complex calculations and aggregations, such as calculating the actual amounts spent, budget amounts, and balances, was essential but challenging.
Solution:
Measures were created in Power Pivot to perform necessary calculations:
Actual = SUM(Transactions[Amount])
Budget = SUM(Budget[Amount])
Balance = [Budget] - [Actual]
These measures were then used in the data visualization to provide clear insights into financial performance.

### Data Visualization
### Challenge: Presenting the data in a clear, understandable, and insightful manner was critical for effective communication with the client.
### Solution:
A comprehensive Dashboard worksheet was created in Excel, displaying key metrics such as actual amounts, budget amounts, and balances.
Various visualizations were included to highlight spending patterns, budget adherence, and other critical insights.

### Insights Extraction
### Challenge: Deriving meaningful insights from the data to inform the client's financial decisions was the ultimate goal but required careful analysis.
### Solution:
Detailed analysis was conducted using the visualizations and measures, leading to insights such as the highest and lowest spending months and categories.
Key findings were summarized, demonstrating the client's ability to stay within the budget and highlighting areas for potential financial adjustments or investments.
By addressing these challenges systematically, the project was able to provide the client with accurate, reliable, and insightful financial analysis.

