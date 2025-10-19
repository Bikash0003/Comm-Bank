# Power BI Home Loan Analysis Project

## Project Overview
This Power BI project analyzes home loan data to provide insights into loan patterns, customer demographics, and financial performance.

## Data Source
- **File:** `Home Loan Data for Analysis.xlsx`
- **Location:** `PowerBI/Data/`
- **Type:** Excel workbook with home loan transaction data

## Power BI Report Structure

### Recommended Visualizations:

1. **Loan Amount Distribution**
   - Chart Type: Histogram or Bar Chart
   - Purpose: Show distribution of loan amounts
   - Fields: Loan Amount (Y-axis), Count (X-axis)

2. **Loan Status Overview**
   - Chart Type: Pie Chart or Donut Chart
   - Purpose: Visualize loan status distribution
   - Fields: Loan Status, Count

3. **Monthly Loan Trends**
   - Chart Type: Line Chart
   - Purpose: Track loan applications over time
   - Fields: Date (X-axis), Loan Amount (Y-axis)

4. **Customer Demographics**
   - Chart Type: Bar Chart
   - Purpose: Analyze customer age groups
   - Fields: Age Group, Count of Customers

5. **Geographic Distribution**
   - Chart Type: Map Visualization
   - Purpose: Show loan distribution by location
   - Fields: Location, Loan Amount

6. **Income vs Loan Amount**
   - Chart Type: Scatter Plot
   - Purpose: Analyze relationship between income and loan amount
   - Fields: Income (X-axis), Loan Amount (Y-axis)

## Setup Instructions

### Step 1: Open Power BI Desktop
1. Launch Power BI Desktop
2. Click "Get Data" → "Excel workbook"
3. Navigate to `PowerBI/Data/Home Loan Data for Analysis.xlsx`
4. Select the relevant worksheet(s)

### Step 2: Data Transformation
1. Use Power Query Editor to clean data
2. Create calculated columns if needed:
   - Age Group (based on customer age)
   - Loan Status Category
   - Income Bracket

### Step 3: Create Visualizations
1. Add the recommended charts to your report canvas
2. Apply consistent formatting and colors
3. Add filters for interactivity

### Step 4: Save Report
1. Save as `.pbix` file in `PowerBI/Reports/` folder
2. Name: `HomeLoan_Analysis.pbix`

## File Structure
```
PowerBI/
├── Data/
│   └── Home Loan Data for Analysis.xlsx
├── Reports/
│   └── HomeLoan_Analysis.pbix (to be created)
└── Documentation/
    └── PowerBI_Setup_Instructions.md
```

## Next Steps
1. Create the Power BI report following these instructions
2. Add screenshots of key visualizations
3. Document insights and findings
4. Commit to Git repository

## Notes
- Use consistent color scheme (banking theme: blues, greens)
- Add tooltips for better user experience
- Include summary cards for key metrics
- Ensure mobile-friendly layout
