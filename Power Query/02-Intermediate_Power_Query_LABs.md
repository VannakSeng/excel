
# 🟡 Intermediate Power Query LABs

---

## 🔬 LAB 1: Using Parameters

**Data File**: `LAB_1_Sales_By_Region.csv`

### 🎯 Objective
- Create parameter to filter data dynamically

### 📝 Tasks
1. Create parameter `SelectedRegion`
2. Load sales data
3. Filter `Region = SelectedRegion`
4. Rename query to `FilteredSalesByRegion`

---

## 🔬 LAB 2: Conditional Columns

**Data File**: `LAB_2_Employee_Salaries.csv`

### 🎯 Objective
- Add logic-based column

### 📝 Tasks
1. Load employee data
2. Add column: If `Department = Sales` then 1000 else 500
3. Rename column to `Bonus`

---

## 🔬 LAB 3: Index and Custom Columns

**Data File**: `LAB_3_Products.csv`

### 🎯 Objective
- Add index and calculate tax

### 📝 Tasks
1. Load product data
2. Add Index column
3. Add custom column: `[Price] * 1.2`
4. Rename `Price with Tax`

---

## 🔬 LAB 4: Combining Files from Folder

### 🎯 Objective
- Auto-load multiple files

### 📝 Tasks
1. Get Data > From Folder
2. Select folder with Excel files
3. Combine and Transform
4. Load final appended table

---

## 🔬 LAB 5: Date Functions

**Data File**: `LAB_5_Sales_Dates.csv`

### 🎯 Objective
- Extract Year, Month, Day from dates

### 📝 Tasks
1. Load sales data
2. Add columns: Year, Month Name, Day of Week
3. (Optional) Add Month Number for sorting
