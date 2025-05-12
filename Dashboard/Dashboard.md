# 📘 Excel Dashboard Tutorial – SuperStore Sales Dataset

## 🧱 Part 1: Prepare Your Data (Detailed)

Creating a solid dashboard starts with **clean, structured, and well-formatted data**. This step ensures all charts, PivotTables, and filters work properly.

---

### 🔹 Step 1: Load the Dataset into Power Query

1. Open Excel and go to `Data ➝ Get Data ➝ From File ➝ From Text/CSV`.
2. Select the file: `SuperStore_Sales_Dataset.csv`.
3. Click **Transform Data** to open Power Query Editor.

---

### 🔹 Step 2: Clean and Transform Data in Power Query

1. **Rename Columns**:
   - Ensure column headers are clear and consistent (e.g., `Order Date`, `Sales`, `Profit`).

2. **Remove Unnecessary Columns**:
   - Select columns like `ind1`, `ind2`, or any blank columns ➝ Right-click ➝ Remove Columns.

3. **Handle Missing Values**:
   - Select columns with missing data ➝ Go to `Transform ➝ Replace Values` or `Fill Down` as needed.

4. **Remove Duplicates**:
   - Go to `Home ➝ Remove Rows ➝ Remove Duplicates`.

5. **Format Dates**:
   - Select `Order Date` and `Ship Date` columns.
   - If the dates are not recognized correctly due to regional settings, use the following steps:
     1. Select the column ➝ Go to `Transform ➝ Data Type ➝ Text`.
     2. Add a new column:
        - Go to `Add Column ➝ Custom Column`.
        - Use the formula:  
          ```powerquery
          = Date.FromText(Text.Middle([Order Date], 6, 4) & "-" & Text.Middle([Order Date], 3, 2) & "-" & Text.Start([Order Date], 2))
          ```
        - Replace `[Order Date]` with the column name.
     3. Rename the new column to `Order Date (Fixed)` and delete the original `Order Date` column.
     4. Repeat for `Ship Date` if necessary.

6. **Add Helper Columns** *(Optional)*:
   - Go to `Add Column ➝ Custom Column` and use formulas:
     - **Year**: `= Date.Year([Order Date])`
     - **Month**: `= Date.ToText([Order Date], "MMM")`
     - **Full Month**: `= Date.ToText([Order Date], "yyyy-MM")`
     - **Profit Margin**: `= [Profit] / [Sales]`
     - **IsReturned**: `= if Text.IsNull([Returns]) then "No" else "Yes"`

---

### 🔹 Step 3: Load Data into Excel

1. Click `Close & Load ➝ Close & Load To...`.
2. Choose **Table** and load it into a new worksheet.
3. Rename the table to `SalesData`:
   - Go to `Table Design ➝ Table Name` ➝ Enter `SalesData`.

---

### 🧪 Final Sanity Checks

- All dates are valid and sorted.
- No missing Region, Segment, or Category.
- No blank Product Names or zero sales values.
- Table name is set and working.

---

## 📊 Part 2: Create Pivot Tables

PivotTables are one of Excel’s most powerful tools. They let you **quickly summarize**, **analyze**, and **slice through large datasets** with minimal effort. In this section, we’ll create four essential PivotTables for your dashboard.

---

### 🛠️ Prerequisites

- Ensure your data is formatted as a table (named `SalesData`)
- All date fields (like `Order Date`) are recognized as dates in Excel
- Column names like `Sales`, `Profit`, `Quantity`, etc. are consistent

---

### 🔹 Pivot Table 1: Total Sales by Region

**Steps**:

1. Go to `Insert ➝ PivotTable`
2. Choose the entire `SalesData` table.
3. Place the PivotTable in a new worksheet.
4. In the PivotTable Fields pane:
   - Drag **Region** into the **Rows** area.
   - Drag **Sales** into the **Values** area.
   - Optionally, drag **Segment** into the **Filters** area.
5. **Name the PivotTable**:
   - Click anywhere inside the PivotTable.
   - Go to `PivotTable Analyze ➝ PivotTable Name`.
   - Enter a descriptive name, such as `PT_SalesByRegion`.

**Output**:
```
Region        Total Sales
--------------------------
Central       $341,007.52
East          $450,234.66
South         $252,121.08
West          $522,441.05
```

---

### 🔹 Pivot Table 2: Monthly Sales Trend

**Steps**:

1. Insert another PivotTable using the `SalesData` table.
2. Drag **Order Date** into **Rows**.
3. Right-click any date in the Pivot ➝ Select **Group** ➝ By **Months** and **Years**.
4. Drag **Sales** into **Values**.
5. **Name the PivotTable**:
   - Click inside the PivotTable.
   - Go to `PivotTable Analyze ➝ PivotTable Name`.
   - Enter a name like `PT_MonthlySales`.

**Output**:
```
Year   Month     Total Sales
-----------------------------
2023   Jan       $18,616.43
       Feb       $19,978.81
       ...
2024   Jan       $54,763.37
       Feb       $52,068.13
       ...
```

---

### 🔹 Pivot Table 3: Sales by Product Category

**Steps**:

1. Insert a new PivotTable.
2. Drag **Category** into **Rows**.
3. Drag **Sales** into **Values**.
4. **Name the PivotTable**:
   - Click inside the PivotTable.
   - Go to `PivotTable Analyze ➝ PivotTable Name`.
   - Enter a name like `PT_SalesByCategory`.

**Output**:
```
Category           Sales
---------------------------
Furniture          $451,508.64
Office Supplies    $643,707.68
Technology         $470,587.99
```

---

### 🔹 Pivot Table 4: Top 10 Customers by Sales

**Steps**:

1. Insert another PivotTable.
2. Drag **Customer Name** into **Rows**.
3. Drag **Sales** into **Values**.
4. Right-click on any value in the Sales column ➝ Sort ➝ **Largest to Smallest**.
5. Click the dropdown next to **Row Labels** ➝ **Value Filters** ➝ **Top 10**.
6. **Name the PivotTable**:
   - Click inside the PivotTable.
   - Go to `PivotTable Analyze ➝ PivotTable Name`.
   - Enter a name like `PT_TopCustomers`.

**Output**:
```
Customer Name        Total Sales
-------------------------------
Caroline Jumper      $11,596.974
Karen Ferguson       $10,941.274
Seth Vernon          $10,751.148
...
```

---

### 🧠 Extra Tips for PivotTables

| Tip                         | Description |
|-----------------------------|-------------|
| 🖊 Rename PivotTables        | Use `PivotTable Analyze ➝ PivotTable Name` |
| 🔄 Refresh All              | Press `Ctrl + Alt + F5` |
| 📑 Label Sheets             | Use names like `PT_SalesByRegion` |
| 📌 For Dashboard            | Base charts on these PivotTables |

---

## 📈 Part 3: Creating Dashboard Charts

PivotTables summarize your data, but **charts tell the story**. A well-designed chart can highlight patterns, trends, and insights at a glance. In this section, we will convert your PivotTables into interactive visualizations and prepare them for dashboard integration.

---

### 🧰 Before You Begin

Ensure you have these PivotTables already created from Part 2:
- `PT_RegionSales`
- `PT_MonthlySales`
- `PT_CategorySales`
- `PT_TopCustomers`

They will serve as the **data source** for each chart.

---

## 🔹 Chart 1: Column Chart – Total Sales by Region

### ✅ Purpose:
Visually compare how much revenue each region generates.

### 📌 Instructions:

1. Click anywhere inside `PT_RegionSales`.
2. Go to `Insert ➝ Column or Bar Chart ➝ Clustered Column`.
3. The chart will appear on the same sheet. Move it to your `Dashboard` sheet.
4. Add a title: **"Sales by Region"**.
5. Right-click ➝ Format Axis ➝ Sort regions by descending values for impact.

### 🎨 Design Tips:
- Enable **data labels** above each bar
- Remove the legend if it’s redundant
- Use a single, professional color (e.g., dark blue) unless highlighting a specific region

---

## 🔹 Chart 2: Line Chart – Monthly Sales Trend

### ✅ Purpose:
Track how sales fluctuate over time.

### 📌 Instructions:

1. Click into `PT_MonthlySales` (should be grouped by Month + Year).
2. Go to `Insert ➝ Line Chart ➝ Line with Markers`.
3. Move to the `Dashboard` sheet.
4. Title it: **"Monthly Sales Trend"**.
5. Ensure the X-axis is correctly grouped by time. Right-click X-axis ➝ Format Axis ➝ Set number format to `"mmm yyyy"`.

### 🎨 Design Tips:
- Use line markers for visibility.
- Apply a subtle gradient or solid fill under the line for a modern look.
- Avoid clutter: only display relevant gridlines.

---

## 🔹 Chart 3: Pie Chart – Sales by Product Category

### ✅ Purpose:
See how total sales are distributed across product categories.

### 📌 Instructions:

1. Click into `PT_CategorySales`.
2. Select only the `Category` and `Sales` columns.
3. Go to `Insert ➝ Pie Chart ➝ 2-D Pie`.
4. Title: **"Sales by Product Category"**.
5. Add **Data Labels ➝ Category Name + Percentage**.

### 🎨 Design Tips:
- Use muted, pastel colors with distinct contrast.
- Keep slices under 6 for clarity (combine small ones into "Other" if needed).
- Avoid 3D Pie – they distort perception.

---

### 🔹 Optional: Add KPI Cards (Formulas)

KPI cards provide a quick summary of key metrics at the top of your dashboard. Follow these steps to create them:

1. **Insert Shapes for KPI Cards**:
   - Go to `Insert ➝ Shapes ➝ Rectangle (Rounded Corners)`.
   - Draw a rectangle on the `Dashboard` sheet.
   - Copy and paste the rectangle to create 3–4 cards (one for each KPI).
   - Align the shapes horizontally or vertically using `Shape Format ➝ Align ➝ Align Top` or `Distribute Horizontally`.

2. **Add Text Boxes for Metrics**:
   - Go to `Insert ➝ Text Box`.
   - Draw a text box inside each rectangle.
   - Type placeholder text like "Total Sales", "Total Profit", etc.

3. **Link Text Boxes to Formulas**:
   - Click on a text box ➝ Select the formula bar.
   - Enter the formula for the KPI:
     - **Total Sales**: `=SUM(SalesData[Sales])`
     - **Total Profit**: `=SUM(SalesData[Profit])`
     - **Total Orders**: `=COUNTA(SalesData[Order ID])`
     - **Avg Profit/Order**: `=AVERAGE(SalesData[Profit])`
   - Press `Enter` to link the text box to the formula.

4. **Format the KPI Cards**:
   - Select each rectangle ➝ Go to `Shape Format ➝ Shape Fill` and choose a soft color (e.g., light blue, green, or gray).
   - Remove the border by selecting `Shape Outline ➝ No Outline`.
   - Adjust the font size and style in the text box:
     - Font: Segoe UI or Arial
     - Size: 20–28
     - Style: Bold
   - Center-align the text within the rectangle.

5. **Add Titles to KPI Cards**:
   - Above each rectangle, insert a smaller text box.
   - Type the title for each KPI (e.g., "Total Sales", "Total Profit").
   - Format the title text box:
     - Font: Segoe UI or Arial
     - Size: 12–14
     - Style: Bold
     - Align the title above the rectangle.

6. **Align and Distribute KPI Cards**:
   - Select all KPI cards and their titles.
   - Go to `Shape Format ➝ Align ➝ Align Top` to ensure they are aligned.
   - Use `Shape Format ➝ Align ➝ Distribute Horizontally` to evenly space them.

7. **Test the KPI Cards**:
   - Update the `SalesData` table to ensure the formulas in the KPI cards update dynamically.
   - Refresh all linked PivotTables and slicers using `Ctrl + Alt + F5`.

### 🔹 Add Slicers for Interactivity

**Steps**:
1. Select any PivotTable ➝ Insert Slicer
2. Choose fields: Segment, Category, Region, Ship Mode
3. Position and format consistently
4. Use Report Connections to link all relevant PivotTables

---

## 🧩 Part 4: Designing the Final Excel Dashboard

### 🔹 Step 1: Create and Name the Dashboard Sheet

- Add a new worksheet
- Rename it: `Dashboard`
- Right-click ➝ Tab Color ➝ Choose a distinctive color (e.g., gray or blue)
- Drag it to the far left of your sheet tabs for easy access

---

### 🔹 Step 2: Add KPI Metric Cards (Visual Summary)

These are **key performance indicators (KPIs)** placed at the top.

1. Go to `Insert ➝ Shapes ➝ Rectangle (Rounded Corners)`
2. Draw 3 or 4 boxes side-by-side (one for each KPI)
3. Inside each, insert a **Text Box** (Insert ➝ Text Box)
4. Enter metrics using formulas like:
   - Total Sales: `=SUM(SalesData[Sales])`
   - Total Profit: `=SUM(SalesData[Profit])`
   - Total Orders: `=COUNTA(SalesData[Order ID])`
   - Avg Profit/Order: `=AVERAGE(SalesData[Profit])`

5. Format Each Card:
   - Fill Color: soft blue, green, or gray
   - Border: none or soft shadow
   - Font: Segoe UI / Arial, Bold, Size 20–28
   - Align Text Box in center of the shape

---

### 🔹 Step 3: Move and Align Your Charts

From previous sheets:

- Go to each chart ➝ `Ctrl + X` (Cut)
- Navigate to the `Dashboard` sheet ➝ `Ctrl + V` (Paste)
- Resize and drag them into the layout grid you created

**Recommended Chart Placement**:

| Chart                            | Placement              |
|----------------------------------|------------------------|
| Column Chart: Sales by Region    | Top-left quadrant      |
| Pie Chart: Category Sales        | Top-right quadrant     |
| Line Chart: Monthly Trends       | Bottom-left quadrant   |
| Bar Chart: Top 10 Customers      | Bottom-right quadrant  |

---

### 🔹 Step 4: Add Slicers for Interactivity

Slicers make your charts **filterable with one click**.

1. Click on any PivotTable
2. Go to: `PivotTable Analyze ➝ Insert Slicer`
3. Select dimensions:
   - `Segment`
   - `Region`
   - `Category`
   - `Ship Mode`
4. Arrange slicers vertically on the **left side** or horizontally across the top
5. Resize to match height or width uniformly

**Style Your Slicers**:

- Use `Slicer Tools ➝ Options`
- Choose "Light" color scheme
- Set font to bold, center alignment
- Turn off the header if you insert your own label above

---

### 🔗 Step 5: Link Slicers to All Relevant PivotTables

1. Right-click the slicer ➝ `Report Connections`
2. Check all PivotTables relevant to your dashboard:
   - `PT_RegionSales`
   - `PT_MonthlySales`
   - `PT_CategorySales`
   - `PT_TopCustomers`

---

### 🔹 Step 6: Apply Final Visual Polishing

**Remove Distractions**:

- View ➝ Uncheck `Gridlines`, `Headings`, and `Formula Bar`
- File ➝ Options ➝ Advanced ➝ Uncheck “Show scrollbars”

**Add Title and Branding**:

- Insert ➝ Text Box ➝ “2025 SuperStore Sales Dashboard”
- Font size: 26–32, Bold
- Optional: Insert logo (Insert ➝ Pictures)
- Add timestamp: `=TODAY()` in a cell or textbox

**Align Elements**:

- Use Drawing Tools ➝ Align ➝ Align Top/Middle/Distribute
- Maintain consistent spacing and padding

---

## 🧪 Final Review Checklist

| Task                        | Completed? |
|-----------------------------|------------|
| ✅ Charts are placed cleanly | ✔          |
| ✅ Slicers control all visuals | ✔        |
| ✅ KPIs are bold and accurate | ✔         |
| ✅ Gridlines/headers removed | ✔          |
| ✅ Exported for sharing (PDF/XLSX) | ✔     |

---

### 🖨️ Export & Share

- Save Excel file: `Dashboard_v1.xlsx`

---
