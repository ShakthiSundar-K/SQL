

# 📌 **Aggregate Functions in SQL**  

## 🚀 **Overview**  
Aggregate functions in SQL **perform calculations on a group of rows** and return a **single result per group**. These functions are commonly used with **GROUP BY** to summarize data.  

### ✅ **List of Aggregate Functions**  

| Function | Description |
|----------|------------|
| **COUNT()** | Returns the number of rows in a group. |
| **SUM()** | Returns the total sum of a numeric column. |
| **MIN()** | Returns the smallest value in a column. |
| **MAX()** | Returns the largest value in a column. |
| **AVG()** | Returns the average value of a numeric column. |

---

## 🔍 **Using Aggregate Functions**

### 1️⃣ **COUNT() – Counting Records**  
The `COUNT()` function returns the total number of rows in a table or a specific column.  

#### **Example:** Count total products  
```sql
SELECT COUNT(ProductID) AS total_products FROM Production.Product;
```
💡 This query counts **all products** available in the `Production.Product` table.  

#### **Example:** Count products by color  
```sql
SELECT Color, COUNT(ProductID) AS num_of_products 
FROM Production.Product
GROUP BY Color;
```
💡 Here, `GROUP BY Color` groups products by their colors, and `COUNT(ProductID)` returns the count of products in each color category.

---

### 2️⃣ **SUM() – Adding Up Values**  
The `SUM()` function calculates the **total sum** of a column (used only for numeric data).  

#### **Example:** Calculate total ListPrice  
```sql
SELECT SUM(ListPrice) AS total_price FROM Production.Product;
```
💡 This query returns the **sum of all ListPrice values** from the `Production.Product` table.  

#### **Example:** Sum of ListPrice for each color  
```sql
SELECT Color, SUM(ListPrice) AS total_list_price 
FROM Production.Product
WHERE Color IS NOT NULL
GROUP BY Color;
```
💡 This calculates the **total ListPrice for each color**, excluding `NULL` values.

---

### 3️⃣ **MIN() & MAX() – Finding Smallest & Largest Values**  
- `MIN()` returns the **smallest value** in a column.  
- `MAX()` returns the **largest value** in a column.  

#### **Example:** Find the lowest and highest ListPrice  
```sql
SELECT MIN(ListPrice) AS min_price, MAX(ListPrice) AS max_price 
FROM Production.Product;
```
💡 This returns the **minimum and maximum ListPrice** from all products.  

#### **Example:** Find the minimum and maximum StandardCost for each color  
```sql
SELECT Color, 
       MIN(StandardCost) AS min_standard_cost, 
       MAX(StandardCost) AS max_standard_cost
FROM Production.Product
WHERE Color IS NOT NULL
GROUP BY Color
ORDER BY Color;
```
💡 This groups products by `Color` and calculates **the minimum and maximum StandardCost** for each color.

---

### 4️⃣ **AVG() – Calculating the Average**  
The `AVG()` function calculates the **average value** of a numeric column.  

#### **Example:** Calculate average ListPrice  
```sql
SELECT AVG(ListPrice) AS avg_price FROM Production.Product;
```
💡 This returns the **average ListPrice** of all products.  

#### **Example:** Find the average ListPrice for each color & size  
```sql
SELECT Color, Size, AVG(ListPrice) AS avg_list_price
FROM Production.Product
WHERE Color IS NOT NULL AND Size IS NOT NULL
GROUP BY Color, Size
ORDER BY Color, Size;
```
💡 This groups products by `Color` and `Size` and calculates the **average ListPrice** for each group.

---

## 🎯 **Key Concepts Related to Aggregate Functions**

### ✅ **Aliasing (AS) – Naming Columns**  
- Aliases (`AS`) allow us to rename the output column for better readability.  

#### **Example:**  
```sql
SELECT COUNT(ProductID) AS total_products FROM Production.Product;
```
💡 Instead of showing `COUNT(ProductID)`, the result column is labeled as **total_products**.

---

### ✅ **GROUP BY – Grouping Data**  
- Used **with aggregate functions** to group rows based on a specific column.  

#### **Example:** Count products for each color  
```sql
SELECT Color, COUNT(ProductID) AS num_of_products 
FROM Production.Product
GROUP BY Color;
```
💡 Groups products **by color** and counts the number of products in each group.

---

### ✅ **HAVING – Filtering Aggregated Data**  
- `HAVING` is used **after GROUP BY** to filter groups based on aggregate function results (unlike `WHERE`, which filters individual rows).  

#### **Example:** Only show colors with more than 10 products  
```sql
SELECT Color, COUNT(ProductID) AS num_of_products 
FROM Production.Product
WHERE Color IS NOT NULL
GROUP BY Color
HAVING COUNT(ProductID) > 10;
```
💡 Filters only those **colors that have more than 10 products**.

#### **Example:** Only show colors where total ListPrice > 300  
```sql
SELECT Color, SUM(ListPrice) AS total_list_price 
FROM Production.Product
WHERE Color IS NOT NULL
GROUP BY Color
HAVING SUM(ListPrice) > 300;
```
💡 Filters only those **colors where the total ListPrice exceeds 300**.

---

### ✅ **ORDER BY – Sorting Data**  
- `ORDER BY` sorts the result set **in ascending (`ASC`) or descending (`DESC`) order**.  

#### **Example:** Sort by total StandardCost  
```sql
SELECT Size, SUM(StandardCost) AS total_standard_cost 
FROM Production.Product
WHERE Size IS NOT NULL
GROUP BY Size
HAVING SUM(StandardCost) > 1000
ORDER BY Size;
```
💡 This sorts the results by `Size` in **ascending order**.

---

### ✅ **DISTINCT – Removing Duplicates**  
- `DISTINCT` returns **unique values** from a column.  

#### **Example:** Get all unique colors  
```sql
SELECT DISTINCT Color FROM Production.Product;
```
💡 This fetches all **distinct colors** from the `Production.Product` table.

#### **Example:** Get unique combinations of Color and Size  
```sql
SELECT DISTINCT Color, Size FROM Production.Product
WHERE Color IS NOT NULL AND Size IS NOT NULL
ORDER BY Color, Size;
```
💡 Retrieves **unique combinations of Color and Size** in an ordered manner.

---

### 🛠️ **Practice Questions – Test Your SQL Skills!**  

Now that you've got a solid understanding of aggregate functions, it's time to put your skills to the test! Try writing SQL queries for the following:  

#### 🔹 **1. Sum of StandardCost based on Size**  
✅ Find the **sum of StandardCost** for each `Size`.  
✅ Exclude `NULL` values for `Size`.  
✅ Only show results where the total StandardCost is **greater than 1000**.  
✅ Arrange the results **in order of Size**.  

```sql
SELECT Size, SUM(StandardCost) AS total_standard_cost 
FROM Production.Product
WHERE Size IS NOT NULL
GROUP BY Size
HAVING SUM(StandardCost) > 1000
ORDER BY Size;
```

---

#### 🔹 **2. Find the Minimum & Maximum StandardCost for Each Color**  
✅ Get the **minimum and maximum** `StandardCost` for each `Color`.  
✅ Exclude `NULL` values for `Color`.  
✅ Arrange the results **in order of Color**.  

```sql
SELECT Color, MIN(StandardCost) AS min_standard_cost, 
              MAX(StandardCost) AS max_standard_cost
FROM Production.Product
WHERE Color IS NOT NULL
GROUP BY Color
ORDER BY Color;
```

---

### 🎯 **Challenge Yourself!**  
Try tweaking the queries:  
- What happens if you remove `HAVING SUM(StandardCost) > 1000`?  
- Can you sort the results in **descending order** instead?  
- Modify the queries to show results for **only a specific Color or Size**.  

🚀 **The best way to learn SQL is to practice! So, go ahead and experiment with these queries!**  

And hey, **if you’re enjoying these notes, don’t forget to give this a ⭐!** 😄

---

### ⭐ **Final Thoughts**
Aggregate functions are **powerful tools** in SQL that help **summarize data efficiently**. Whether you need **counts, sums, averages, or filtering** results based on conditions, these functions **make SQL queries more insightful and useful**.  

