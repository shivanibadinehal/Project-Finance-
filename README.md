# Client Financial Analysis with Excel

## Table of Contents
1. [Problem Statement](#problem-statement)
2. [Data Sourcing](#data-sourcing)
3. [Data Preparation](#data-preparation)
4. [Data Modeling](#data-modeling)
5. [Data Visualization](#data-visualization)
6. [Data Analysis](#data-analysis)
7. [Insights](#insights)
8. [Shareable Link](#shareable-link)

## Problem Statement
The objective of this analysis is to assist the client in unlocking the potential of financial analysis and reporting. The goal is to produce comprehensive insights into the client's finances using her financial data.

## Data Sourcing
The dataset used for this analysis was provided by Finex Skills Hub and is available at:

- [Client Finance Data](#)

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

To ensure the accuracy of the dates in the `Date` column in each table, a date table was created for referencing using the M-formula:

```m
