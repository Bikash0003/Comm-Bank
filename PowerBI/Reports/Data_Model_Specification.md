# Power BI Data Model Specification

## Data Source Configuration
- **Source:** Excel Workbook
- **File:** `Home Loan Data for Analysis.xlsx`
- **Connection Type:** Import (not DirectQuery for better performance)

## Expected Data Columns
Based on typical home loan data, your Excel file should contain:

### Primary Columns:
- **Customer ID** (Text/Number)
- **Customer Name** (Text)
- **Age** (Number)
- **Annual Income** (Currency)
- **Loan Amount** (Currency)
- **Loan Status** (Text: Approved/Rejected/Pending)
- **Application Date** (Date)
- **Loan Duration** (Number - months/years)
- **Interest Rate** (Decimal)
- **Location/City** (Text)
- **Credit Score** (Number)

## Data Transformations Needed:

### 1. Date Formatting
- Convert Application Date to proper date format
- Create Month/Year columns for trend analysis

### 2. Calculated Columns
```dax
Age Group = 
SWITCH(
    TRUE(),
    [Age] < 25, "Under 25",
    [Age] < 35, "25-34",
    [Age] < 45, "35-44",
    [Age] < 55, "45-54",
    [Age] < 65, "55-64",
    "65+"
)

Income Bracket = 
SWITCH(
    TRUE(),
    [Annual Income] < 30000, "Low Income",
    [Annual Income] < 60000, "Lower Middle",
    [Annual Income] < 100000, "Upper Middle",
    [Annual Income] < 200000, "High Income",
    "Very High Income"
)

Loan Amount Category = 
SWITCH(
    TRUE(),
    [Loan Amount] < 100000, "Small Loan",
    [Loan Amount] < 300000, "Medium Loan",
    [Loan Amount] < 500000, "Large Loan",
    "Very Large Loan"
)
```

### 3. Key Measures
```dax
Total Applications = COUNTROWS(HomeLoanData)

Total Loan Amount = SUM(HomeLoanData[Loan Amount])

Average Loan Amount = AVERAGE(HomeLoanData[Loan Amount])

Approval Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(HomeLoanData), HomeLoanData[Loan Status] = "Approved"),
    COUNTROWS(HomeLoanData)
)

Rejection Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(HomeLoanData), HomeLoanData[Loan Status] = "Rejected"),
    COUNTROWS(HomeLoanData)
)

Average Credit Score = AVERAGE(HomeLoanData[Credit Score])

Monthly Applications = 
CALCULATE(
    COUNTROWS(HomeLoanData),
    FILTER(
        ALL(HomeLoanData),
        MONTH(HomeLoanData[Application Date]) = MONTH(MAX(HomeLoanData[Application Date]))
    )
)
```

## Relationships (if multiple tables):
- **Primary Table:** HomeLoanData
- **Date Table:** Create a separate date table for better time intelligence
- **Location Table:** Create location dimension table

## Data Quality Checks:
1. **Remove duplicates** based on Customer ID
2. **Handle missing values** in critical fields
3. **Validate data ranges** (Age: 18-100, Income: >0, etc.)
4. **Standardize text fields** (Status values, Location names)

## Performance Optimization:
1. **Remove unused columns** after data import
2. **Use appropriate data types** (Date, Currency, Whole Number)
3. **Create indexes** on frequently filtered columns
4. **Limit data refresh** to necessary frequency

## Security Considerations:
1. **Row-level security** if needed for different user groups
2. **Data sensitivity** - mask sensitive information if required
3. **Access controls** for different dashboard sections
