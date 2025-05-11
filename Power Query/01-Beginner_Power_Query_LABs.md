
# 🟢 Beginner Power Query LABs

---

## 🔬 LAB 1: Loading & Inspecting Data

**Data File**: `LAB_1_Sales_2024.csv`

### 🎯 Objective
- Load Excel/CSV data
- Navigate Power Query Editor

### 📝 Tasks
## 📝 Tasks & Step-by-Step Instructions

### ✅ Step 1: Open Power BI Desktop
> _Alternatively, you can do this in Excel using the **Data** tab > **Get & Transform Data**._

---

### ✅ Step 2: Go to "Get Data"
- In **Power BI**:
  - Click `Home` > `Get Data` > `Excel Workbook` (or `Text/CSV` if it's a `.csv` file)
- In **Excel**:
  - Click `Data` > `Get Data` > `From File` > `From Workbook` (or `From Text/CSV`)

---

### ✅ Step 3: Select the File
- Locate and select `LAB_1_Sales_2024.csv` or `.xlsx`
- Click **Open**

---

### ✅ Step 4: Use the Navigator Window
- Select the sheet or table containing the data (e.g., `Sheet1`, `SalesData`, etc.)
- Click **Transform Data** (⚠️ Important: Not "Load")

---

### ✅ Step 5: Explore Power Query Editor
- **Left Pane**: List of queries (you should see one for your data)
- **Center Pane**: The actual data preview
- **Right Pane**: Applied Steps (e.g., Source, Navigation, Changed Type)

---

### ✅ Step 6: Rename the Query
- In the **Query Settings** (right-side panel):
  - Click the query name at the top (default might be `Sheet1` or `Table1`)
  - Change it to `Sales_2024`
  - Press `Enter`

---

### ✅ Step 7: Close & Load
- Click `Home` > `Close & Load`
- Power BI: Loads the data into the model
- Excel: Loads into a table or Power Pivot model

---

## 🔬 LAB 2: Cleaning and Filtering Data

**Data File**: `LAB_2_Employees.csv`

### 🎯 Objective
- Remove blanks and filter data

### 📝 Tasks
1. Load employee data into Power Query
2. Remove rows with blank Department
3. Filter `Status = Active`
4. Remove `Status` column
5. Rename query `Active_Employees`

---

## 🔬 LAB 3: Splitting Columns

**Data File**: `LAB_3_Names_Emails.csv`

### 🎯 Objective
- Split names and emails by delimiter

### 📝 Tasks
1. Load data with `Full Name` and `Email`
2. Split `Full Name` by space
3. Split `Email` by `@`
4. Rename resulting columns

---

## 🔬 LAB 4: Grouping and Summarizing

**Data File**: `LAB_4_Region_Sales.csv`

### 🎯 Objective
- Group by region and sum sales

### 📝 Tasks
1. Load sales by region
2. Use `Group By` on `Region`
3. Summarize `Sales` with Sum

---

## 🔬 LAB 5: Merging Queries

**Data Files**: `LAB_5_Orders.csv`, `LAB_5_Products.csv`

### 🎯 Objective
- Merge Orders and Products tables

### 📝 Tasks
1. Load both queries
2. Merge on `ProductID`
3. Expand to show `Product Name`

---

## 🔬 LAB 6: Unpivoting Columns

**Data File**: `LAB_6_Sales_Wide.csv`

### 🎯 Objective
- Normalize wide data to long format

### 📝 Tasks
1. Load sales data (Product, Jan, Feb, Mar)
2. Select months > Unpivot Columns
3. Rename as `Month` and `Sales`
