
# 🟢 Beginner Power Query LABs

---

## 🔬 LAB 1: Loading & Inspecting Data

**Data File**: `LAB_1_Sales_2024.csv`

### 🎯 Objective
- Load Excel/CSV data
- Navigate Power Query Editor

### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Open Power BI Desktop
> _Alternatively, you can do this in Excel using the **Data** tab > **Get & Transform Data**._

---

#### ✅ Step 2: Go to "Get Data"
- In **Power BI**:
  - Click `Home` > `Get Data` > `Excel Workbook` (or `Text/CSV` if it's a `.csv` file)
- In **Excel**:
  - Click `Data` > `Get Data` > `From File` > `From Workbook` (or `From Text/CSV`)

---

#### ✅ Step 3: Select the File
- Locate and select `LAB_1_Sales_2024.csv` or `.xlsx`
- Click **Open**

---

#### ✅ Step 4: Use the Navigator Window
- Select the sheet or table containing the data (e.g., `Sheet1`, `SalesData`, etc.)
- Click **Transform Data** (⚠️ Important: Not "Load")

---

#### ✅ Step 5: Explore Power Query Editor
- **Left Pane**: List of queries (you should see one for your data)
- **Center Pane**: The actual data preview
- **Right Pane**: Applied Steps (e.g., Source, Navigation, Changed Type)

---

#### ✅ Step 6: Rename the Query
- In the **Query Settings** (right-side panel):
  - Click the query name at the top (default might be `Sheet1` or `Table1`)
  - Change it to `Sales_2024`
  - Press `Enter`

---

#### ✅ Step 7: Close & Load
- Click `Home` > `Close & Load`
- Power BI: Loads the data into the model
- Excel: Loads into a table or Power Pivot model

---

### 🎉 You’re Done!
You have successfully:
- Loaded data
- Explored the Power Query Editor
- Renamed the query
- Loaded the cleaned data into your workspace

---

## 🔬 LAB 2: Cleaning and Filtering Data

**Data File**: `LAB_2_Employees.csv`

### 🎯 Objective
- Remove blanks and filter data

### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Load Employee Data into Power Query
- Open **Power BI Desktop** (or **Excel**)
- Go to `Home` > `Get Data` > `Text/CSV`
- Select the file `LAB_2_Employees.csv`
- Click **Transform Data**

---

#### ✅ Step 2: Remove Rows with Blank Department
- In Power Query Editor:
  - Select the **Department** column
  - Go to the top menu: `Home` > `Remove Rows` > `Remove Blank Rows`

---

#### ✅ Step 3: Filter Status = Active
- Click the dropdown arrow in the **Status** column
- Uncheck all options except **Active**
- Click **OK**

---

#### ✅ Step 4: Remove the Status Column
- Right-click the **Status** column header
- Select **Remove**

---

#### ✅ Step 5: Rename the Query
- In the **Query Settings** pane (right side):
  - Click the query name (e.g., `LAB_2_Employees`)
  - Rename it to `Active_Employees`

---

#### ✅ Step 6: Close & Load
- Click `Home` > `Close & Load`

---

### 🎉 You’re Done!
You have successfully:
- Removed blank rows in Department
- Filtered only active employees
- Cleaned up the query and renamed it
---

## 🔬 LAB 3: Splitting Columns

**Data File**: `LAB_3_Names_Emails.csv`

### 🎯 Objective
- Split names and emails by delimiter

### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Load the Data into Power Query
- Open **Power BI Desktop** (or **Excel**)
- Go to `Home` > `Get Data` > `Text/CSV`
- Select `LAB_3_Names_Emails.csv`
- Click **Transform Data**

---

#### ✅ Step 2: Split Full Name by Space
- Select the **Full Name** column
- Go to the menu: `Home` > `Split Column` > `By Delimiter`
- Choose `Space` as the delimiter
- Choose to split at each occurrence of the delimiter
- Click **OK**

---

#### ✅ Step 3: Split Email by @
- Select the **Email** column
- Go to `Home` > `Split Column` > `By Delimiter`
- Choose `@` as the delimiter
- Choose to split at the left-most delimiter
- Click **OK**

---

#### ✅ Step 4: Rename the Resulting Columns
- Rename the columns as follows (or according to your structure):
  - `Full Name.1` → `First Name`
  - `Full Name.2` → `Last Name`
  - `Email.1` → `Username`
  - `Email.2` → `Domain`

---

#### ✅ Step 5: Close & Load
- Click `Home` > `Close & Load`

---

### 🎉 You’re Done!
You have successfully:
- Loaded name and email data
- Split full names into first and last names
- Split email addresses into username and domain
- Renamed the resulting columns

---

## 🔬 LAB 4: Grouping and Summarizing

**Data File**: `LAB_4_Region_Sales.csv`

### 🎯 Objective
- Group by region and sum sales


### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Load the Sales Data into Power Query
- Open **Power BI Desktop** (or **Excel**)
- Go to `Home` > `Get Data` > `Text/CSV`
- Select the file `LAB_4_Region_Sales.csv`
- Click **Transform Data**

---

#### ✅ Step 2: Group by Region
- In Power Query Editor:
  - Select the **Region** column
  - Go to the menu: `Transform` > `Group By`
  - In the dialog box:
    - **Group by**: `Region`
    - **New column name**: `Total Sales`
    - **Operation**: `Sum`
    - **Column**: `Sales`
  - Click **OK**

---

#### ✅ Step 3: Review the Summarized Data
- Confirm that you now have a summarized table with:
  - One row per Region
  - A column for `Total Sales` containing the sum of sales

---

#### ✅ Step 4: Rename the Query (Optional)
- In the **Query Settings** pane:
  - Rename the query to `Region_Sales_Summary`

---

#### ✅ Step 5: Close & Load
- Click `Home` > `Close & Load`

---

### 🎉 You’re Done!
You have successfully:
- Grouped the data by region
- Summed the sales per region
- Created a summarized report
---

## 🔬 LAB 5: Merging Queries

**Data Files**: `LAB_5_Orders.csv`, `LAB_5_Products.csv`

### 🎯 Objective
- Merge Orders and Products tables


### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Load Both Data Files into Power Query
- Open **Power BI Desktop** (or **Excel**)
- Go to `Home` > `Get Data` > `Text/CSV`
- Load `LAB_5_Orders.csv` and click **Transform Data**
- Repeat for `LAB_5_Products.csv`

You should now have two queries in the Power Query Editor:
- `LAB_5_Orders`
- `LAB_5_Products`

---

#### ✅ Step 2: Merge Queries on ProductID
- In the Power Query Editor:
  - Select the `LAB_5_Orders` query
  - Go to `Home` > `Merge Queries` > `Merge Queries as New`
  - In the Merge dialog:
    - Select `ProductID` from both tables
    - Use `Inner Join` (default) or another join type as needed
  - Click **OK**

This creates a new query with merged data.

---

#### ✅ Step 3: Expand to Show Product Name
- In the new merged query:
  - Click the expand icon (🔽) next to the `LAB_5_Products` column
  - Uncheck all columns except `Product Name`
  - Click **OK**

Now the merged table includes the product name next to each order.

---

#### ✅ Step 4: Rename the Query (Optional)
- In the **Query Settings** pane:
  - Rename the query to `Orders_With_ProductName`

---

#### ✅ Step 5: Close & Load
- Click `Home` > `Close & Load`

---

### 🎉 You’re Done!
You have successfully:
- Loaded two datasets
- Merged them on `ProductID`
- Expanded to show the product name
- Created a combined orders view
---

## 🔬 LAB 6: Unpivoting Columns

**Data File**: `LAB_6_Sales_Wide.csv`

### 🎯 Objective
- Normalize wide data to long format


### 📝 Tasks & Step-by-Step Instructions

#### ✅ Step 1: Load the Sales Data into Power Query
- Open **Power BI Desktop** (or **Excel**)
- Go to `Home` > `Get Data` > `Text/CSV`
- Select the file `LAB_6_Sales_Wide.csv`
- Click **Transform Data**

---

#### ✅ Step 2: Select the Month Columns
- In Power Query Editor, you should see columns like:
  - `Product`, `Jan`, `Feb`, `Mar`
- Select the columns for the months: `Jan`, `Feb`, `Mar`

---

#### ✅ Step 3: Unpivot the Selected Columns
- With the month columns selected:
  - Go to `Transform` > `Unpivot Columns`

This will convert the wide data format into a long format with two new columns:
- `Attribute` (original column headers)
- `Value` (original values)

---

#### ✅ Step 4: Rename the New Columns
- Rename `Attribute` to `Month`
- Rename `Value` to `Sales`

---

#### ✅ Step 5: Rename the Query (Optional)
- In the **Query Settings** pane:
  - Rename the query to `Sales_Long_Format`

---

#### ✅ Step 6: Close & Load
- Click `Home` > `Close & Load`

---

### 🎉 You’re Done!
You have successfully:
- Loaded wide-format sales data
- Unpivoted the month columns
- Normalized the dataset into a long format
