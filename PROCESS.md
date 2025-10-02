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
- Check cardinality of relationships between tables (Many (fact table) to One (dim table))
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

DimDate (Date Dimension) for time intelligence
- Date (Primary Key)
- Year
- Quarter
- Month
- Month Name
- Day
- Weekday 
- Note: mark as Date table.

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

- created DimDate with DAX CALENDAR function
- connected FactSales[Order Date] to DimDate[Date]
- marked DimDate as date table

## 4. DAX Measures Created

1. **Total Revenue** = SUM(FactSales[Sales])
   - Core metric for business performance

2. **Total Profit** = SUM(FactSales[Profit])
   - Bottom-line profitability

3. **Profit Margin %** = DIVIDE([Total Profit], [Total Revenue], 0)
   - Efficiency metric showing profit per dollar of revenue

4. **Average Discount %** = AVERAGE(FactSales[Discount])
   - Tracks discounting behavior

5. **Total Quantity** = SUM(FactSales[Quantity])
   - Volume metric

6. **YoY Revenue Growth %** = Uses SAMEPERIODLASTYEAR for time intelligence
   - Shows growth compared to prior year same period

7. **Customer Count** = DISTINCTCOUNT(FactSales[Customer ID])
   - Unique customer tracking
## 5. Dashboard Design
- Visual choices and why
- Layout decisions
- Interactivity

## 6. Insights & Recommendations
- discoveries, etc.