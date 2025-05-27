# Inventory Aging Analysis

### Dashboard Link : https://app.powerbi.com/links/q4A7PPfeDh?ctid=3d8ac827-9b32-4896-834d-be68f11fc784&pbi_source=linkShare

## Problem Statement

This dashboard helps the operations and inventory management teams understand the aging of inventory across products, locations, and categories. It identifies items with excessive aging (e.g., >1 year) and highlights where improvements are needed in managing stock to reduce risks of overstocking and waste. The analysis also supports warehouse management by providing actionable insights.

Since some inventory has been held for more than a year (or even over 30 days), this dashboard helps in prioritizing movement and operational decisions.

### Steps Followed
- Step 1: Loaded multiple tables (InventoryOnHand, Items, ItemCategory, ItemSubCategory, Location) into Power BI Desktop.

- Step 2: Opened Power Query Editor and enabled Column Quality, Column Distribution, and Column Profile options under the View tab.

- Step 3: Checked for nulls in fields like Kgs and BoxCount and handled them appropriately.

- Step 4: Created key calculated columns and measures:

Total Kgs = SUM(InventoryOnHand[Kgs])

Total Boxes = SUMX(InventoryOnHand, RELATED(Items[BoxCount]))

Kgs > 1 Year = CALCULATE(SUM(InventoryOnHand[Kgs]), FILTER(InventoryOnHand, [Age(days)] > 365))

Boxes > 1 Year = CALCULATE(SUM(InventoryOnHand, RELATED(Items[BoxCount])), FILTER(InventoryOnHand, [Age(days)] > 365))

% of Inventory > 30 Days = DIVIDE(Kgs > 30 Days, Total Kgs) * 100

% of Inventory > 1 Year = DIVIDE(Kgs > 1 Year, Total Kgs) * 100

- Step 5: Applied visual-level filters to exclude zero values from visuals and highlight items with critical aging.

- Step 6: Created a matrix table grouped by Category > Subcategory > Location > Item to show detailed aging analysis.

- Step 7: Created bar/column charts for Total Kgs and Boxes by Age Bucket.

- Step 8: Added slicers for dynamic filtering by Location, Category & Subcategory, Age Bucket, and InventoryLotDate.

- Step 9: Applied conditional formatting to highlight critical items in matrices.

- Step 10: Created scatter plots and line charts to visualize trends over time and by pack weight.

- Step 11: Added tooltips with enhanced details like ItemDesc, PackWeight, and Location.

- Step 12: Published the report to Power BI Service.

### Snapshot of Dashboard (Power BI Service)
![Image](https://github.com/user-attachments/assets/de0115c9-aa2b-4a14-80b0-259c11818313)

### Insights
#### Total Inventory Overview
Total Kgs: 5,634,951.35

Total Boxes: 59,531

% of Inventory > 1 Year: 0.04%

Average Age of Inventory: ~29 days

#### Key Insights
Inventory distributed across Age Buckets:

1-3 Days, 4-7 Days, 8-15 Days, 15-30 Days, >30 Days, >1 Year.

Items with >1 year age are highlighted in the Detailed View matrix.

Location-wise analysis helps identify warehouses with older inventory.

Aging trends shown over time help predict and plan for inventory movement.

Concentration analysis by Category and Pack Weight helps with operational planning.

#### Slicers Added
Location

Category & Subcategory

Age Bucket

InventoryLotDate

#### Conditional Formatting
Applied in matrix to highlight products with aging >1 year.

#### Key Visuals
Matrix: Detailed View of Items Aged Over 1 Year (with Category, Subcategory, Location, Item)

Bar Charts: Total Kgs and Boxes by Age Bucket

Line Chart: Inventory Aging Trends over Time

Scatter Plot: Inventory Concentration by Category and Pack Weight

KPI Cards: Total Kgs, Boxes >1 Year, % Inventory >1 Year, Average Age

### Additional Recommendations
Consider adding Inventory Turnover Ratio for comprehensive stock health analysis.

Integrate with real-time systems to keep inventory data updated.

Add filters for Seasonality or Item Criticality for targeted decision-making.

### Publication & Access
The report is published to Power BI Service for secure access and sharing with stakeholders.

