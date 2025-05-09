
# 🧠 Advanced Power Query LABs
_Audience: Intermediate to Advanced Excel Users_

---

## 🔬 LAB 1: Writing and Editing M Code

### 🎯 Objective
- Understand and modify M code in the Advanced Editor

### 📁 Required File
**Data File**: `LAB_3_Products.csv`

### 📝 Tasks
1. Load data via **Get Data > From Workbook**
2. Click **Transform Data** to open Power Query
3. Go to **Home > Advanced Editor**
4. Review the script; rename `"Changed Type"` to `"TypedColumns"`
5. Add a new manual step:
   ```m
   = Table.AddColumn(TypedColumns, "Price with Tax", each [Price] * 1.2)
   ```
6. Click **Done** and confirm changes
7. Rename the query and click **Close & Load**

### ✅ Expected Output
A column added manually via M code

### 🧠 Best Practices
- Use `//` to comment M code
- Avoid duplicate step names

---

## 🔬 LAB 2: Creating and Invoking Custom Functions

### 🎯 Objective
- Reuse logic using custom M functions

### 📁 Required File
**Data File**: `LAB_2_Employee_Salaries.csv`

### 📝 Tasks
1. Go to **Home > New Source > Blank Query**
2. Open **Advanced Editor** and paste:
   ```m
   (salary as number) => if salary > 50000 then "High" else "Low"
   ```
3. Name the function `ClassifySalary`
4. Load salary data into Power Query
5. Click **Add Column > Invoke Custom Function**
6. Apply to the `Salary` column

### ✅ Expected Output
A column showing "High"/"Low" classification

### 🧠 Best Practices
- Declare parameter types (`as number`)
- Test functions with sample inputs

---

## 🔬 LAB 3: Error Handling with `try...otherwise`

### 🎯 Objective
- Handle risky operations like divide-by-zero

### 📁 Required File
**Data File**: `LAB_5_Sales_Dates.csv` (with extra Quantity column)

### 📝 Tasks
1. Load the data into Power Query
2. Add custom column:
   ```m
   try [Amount] / [Quantity] otherwise null
   ```
3. Or return a string:
   ```m
   try [Amount] / [Quantity] otherwise "Error"
   ```

### ✅ Expected Output
No errors in query; fallback values instead

### 🧠 Best Practices
- Always guard calculations with `try`
- Use `Value.Is` or `Record.HasFields` for checks

---

## 🔬 LAB 4: Nested Queries + Parameterized Joins

### 🎯 Objective
- Use parameters to dynamically filter before a merge

### 📁 Required File
**Data Files**: `LAB_5_Orders.csv`, `LAB_5_Products.csv` (simulate join via parameter)

### 📝 Tasks
1. Create a **Text** parameter `CustomerRegion` with value (e.g. "East")
2. Load `Customers` and filter by `Region = CustomerRegion`
3. Load `Orders` and merge with the filtered `Customers`
4. Expand customer fields and rename query as `FilteredOrders`

### ✅ Expected Output
A region-filtered set of orders based on the parameter

### 🧠 Best Practices
- Test filtered queries independently
- Always verify join direction (Left Join for safe merge)

---

## 🔬 LAB 5: Pivoting with Aggregation

### 🎯 Objective
- Pivot data to summarize with totals

### 📁 Required File
**Data File**: `LAB_6_Sales_Wide.csv`

### 📝 Tasks
1. Load the data into Power Query
2. Select the `Month` column > **Pivot Column**
3. Use `Amount` as Values; set aggregation to **Sum**
4. Rename columns and fill nulls with 0 if needed

### ✅ Expected Output
One row per product with monthly totals

### 🧠 Best Practices
- Use `Fill Down` or `Replace Nulls` as needed
- Numeric fields must be of correct type for aggregation
