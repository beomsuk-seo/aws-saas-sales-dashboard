# Development Process

## 1. Business Problem
A B2B SaaS company is experiencing growth but lacks visibility into which customer segments, products, and regions are driving profitability.
- Which customer segments generate the most revenue and profit?
    - Split by industry/region 
- How are discounts impacting profitability across products?
- Which geographic markets show the strongest performance and growth potential?
- Are there underperforming segments that need attention?

## 2. Data Preparation
- Download data
- Load data into Power BI Desktop 
    - Transform Data
        - Check for null values
        - Verify data types of each column
        - Split data into separate tables for data model (DimCustomer, DimProduct, DimDate, FactSales)
            - Remove duplicates
            - e.g. removing duplicates from the DimCustomer table from 999+ rows to 99 rows.
    - Disable loading on source query.

## 3. Data Model

DimCustomer 
- Customer ID (Primary Key)
- Contact Name
- Customer
- Country
- City
- Region
- Subregion
- Industry
- Segment

DimProduct 
- Product (Primary Key)
- License

DimDate (Date Dimension)
- Date (Primary Key)
- Year
- Quarter
- Month
- Month Name
- Day
- Weekday 

FactSales 
- Row ID
- Order ID
- Order Date
- Customer ID
- Product
- Sales
- Quantity
- Discount 
- Profit

### Relationships

## 4. DAX Measures
+ reasoning! todo

## 5. Dashboard Design
- Visual choices and why
- Layout decisions
- Interactivity

## 6. Insights & Recommendations
- discoveries, etc.