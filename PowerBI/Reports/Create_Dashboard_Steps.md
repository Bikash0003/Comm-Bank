# Step-by-Step: Create Power BI Dashboard

## Step 1: Open Power BI Desktop
1. Launch Power BI Desktop
2. Click "Get Data" → "Excel workbook"
3. Navigate to: `D:\Comm-Bank\PowerBI\Data\Home Loan Data for Analysis.xlsx`
4. Select the worksheet(s) with your data
5. Click "Load"

## Step 2: Data Preparation
1. Go to "Data" view (left panel)
2. Check your data columns
3. Create calculated columns if needed:
   - Right-click on a column → "New Column"
   - Use DAX formulas from the template

## Step 3: Create Visualizations

### Dashboard Layout (Create these in order):

#### 1. **Key Metrics Cards** (Top Row)
- **Total Loans Card:**
  - Visual: Card
  - Field: Count of rows
  - Format: Large number, blue background

- **Average Loan Amount Card:**
  - Visual: Card  
  - Field: Average of Loan Amount
  - Format: Currency, green background

- **Approval Rate Card:**
  - Visual: Card
  - Field: Custom measure (approved loans / total loans)
  - Format: Percentage, orange background

#### 2. **Loan Distribution** (Second Row)
- **Loan Amount Distribution:**
  - Visual: Column Chart
  - X-axis: Loan Amount (grouped into ranges)
  - Y-axis: Count
  - Color: Blue gradient

#### 3. **Status Overview** (Second Row, Right)
- **Loan Status Pie Chart:**
  - Visual: Pie Chart
  - Legend: Loan Status
  - Values: Count
  - Colors: Green (Approved), Red (Rejected), Yellow (Pending)

#### 4. **Trends** (Third Row)
- **Monthly Loan Trends:**
  - Visual: Line Chart
  - X-axis: Date (grouped by month)
  - Y-axis: Sum of Loan Amount
  - Color: Blue line

#### 5. **Demographics** (Fourth Row)
- **Customer Age Groups:**
  - Visual: Bar Chart
  - X-axis: Age Group (calculated column)
  - Y-axis: Count of Customers
  - Color: Green bars

#### 6. **Correlation Analysis** (Fourth Row, Right)
- **Income vs Loan Amount:**
  - Visual: Scatter Chart
  - X-axis: Annual Income
  - Y-axis: Loan Amount
  - Size: Loan Duration
  - Color: Income Bracket

## Step 4: Formatting
1. **Theme:** Apply "Banking" theme or custom colors
2. **Colors:** Use blues (#1f4e79), greens (#70ad47), and accent colors
3. **Fonts:** Use professional fonts (Segoe UI)
4. **Layout:** Ensure mobile-friendly responsive design

## Step 5: Add Interactivity
1. **Filters:** Add filter pane with:
   - Loan Status
   - Age Group
   - Date Range
   - Income Bracket

2. **Cross-filtering:** Enable cross-filtering between visuals

## Step 6: Save Dashboard
1. File → Save As
2. Navigate to: `D:\Comm-Bank\PowerBI\Reports\`
3. Name: `HomeLoan_Dashboard.pbix`
4. Click Save

## Step 7: Test Dashboard
1. Switch to "Report" view
2. Test all filters and interactions
3. Check mobile layout
4. Verify all calculations are correct

## DAX Formulas to Create:

### Calculated Columns:
```
Age Group = 
IF([Age] < 30, "Under 30", 
   IF([Age] < 40, "30-39", 
      IF([Age] < 50, "40-49", 
         IF([Age] < 60, "50-59", "60+"))))

Loan Amount Range = 
IF([Loan Amount] < 100000, "Under $100K", 
   IF([Loan Amount] < 300000, "$100K-$300K", 
      IF([Loan Amount] < 500000, "$300K-$500K", "Over $500K")))
```

### Measures:
```
Total Loans = COUNTROWS(Table)

Average Loan Amount = AVERAGE([Loan Amount])

Approval Rate = 
DIVIDE(
    COUNTROWS(FILTER(Table, [Status] = "Approved")), 
    COUNTROWS(Table)
)
```

## Next Steps After Creating:
1. Take screenshots of your dashboard
2. Save the .pbix file
3. Commit to Git repository
4. Share with team members
