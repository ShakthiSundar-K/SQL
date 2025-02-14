

# **📌 Using the `WHERE` Clause in SQL**  

The `WHERE` clause is used to filter records based on **specific conditions** in an SQL query.  

## **1️⃣ Basic Filtering with `WHERE`**  
### 🔹 **Syntax:**  
```sql
SELECT * FROM table_name WHERE condition;
```

### 🔹 **Example:**  
```sql
SELECT * FROM Production.Product WHERE ProductID = 322;
```
✅ Retrieves the product with `ProductID = 322`.  

---

## **2️⃣ Filtering with Comparison Operators**  
| **Operator** | **Description** | **Example** |
|-------------|----------------|------------|
| `=`  | Equals | `ProductID = 322` |
| `>`  | Greater than | `ProductID > 900` |
| `<`  | Less than | `ProductID < 300` |
| `>=` | Greater than or equal to | `ProductID >= 350` |
| `<=` | Less than or equal to | `ProductID <= 400` |

### 🔹 **Example:**  
```sql
SELECT * FROM Production.Product WHERE ProductID >= 900;
```
✅ Retrieves all products where `ProductID` is **900 or greater**.  

---

## **3️⃣ Filtering with `BETWEEN` (Range Selection)**  
Instead of using `>=` and `<=`, you can use `BETWEEN`.  

### 🔹 **Example:**  
```sql
SELECT * FROM Production.Product WHERE ProductID BETWEEN 350 AND 400;
```
✅ Retrieves products where `ProductID` is **between 350 and 400 (inclusive)**.  

---

## **4️⃣ Filtering with String Values (`=`, `<>`, `IN`, `NOT IN`)**  

### 🔹 **Checking for Exact Match (`=` and `<>`)**  
```sql
SELECT * FROM Production.Product WHERE Color = 'Silver';
```
✅ Retrieves products **where color is Silver**.  

```sql
SELECT * FROM Production.Product WHERE Color <> 'Silver';
```
✅ Retrieves products **where color is NOT Silver**.  

---

### 🔹 **Checking for Multiple Values (`IN` and `NOT IN`)**  
```sql
SELECT * FROM Production.Product WHERE Color IN ('Silver', 'Black', 'Red');
```
✅ Retrieves products where the color is **Silver, Black, or Red**.  

```sql
SELECT * FROM Production.Product WHERE Color NOT IN ('Silver', 'Black', 'Red');
```
✅ Retrieves products where the color is **NOT Silver, Black, or Red**.  

---

## **5️⃣ Using `AND` & `OR` for Multiple Conditions**  
| **Operator** | **Description** |
|-------------|----------------|
| `AND` | Returns records **only if all conditions are true** |
| `OR` | Returns records **if at least one condition is true** |

```sql
SELECT * FROM Production.Product WHERE Color = 'Silver' AND StandardCost > 1000.00;
```
✅ Retrieves products **where Color is Silver AND StandardCost is greater than 1000**.  

```sql
SELECT * FROM Production.Product WHERE Color = 'Silver' OR StandardCost > 1000.00;
```
✅ Retrieves products **where Color is Silver OR StandardCost is greater than 1000**.  

---

## **6️⃣ Checking for NULL Values**  
| **Condition** | **Description** |
|-------------|----------------|
| `IS NULL` | Checks if a column has `NULL` values |
| `IS NOT NULL` | Checks if a column has **non-null** values |

```sql
SELECT * FROM Production.Product WHERE Size IS NULL;
```
✅ Retrieves products where **Size is NULL**.  

```sql
SELECT * FROM Production.Product WHERE Size IS NOT NULL;
```
✅ Retrieves products where **Size is NOT NULL**.  

---

## **7️⃣ Filtering with Date Values**  
```sql
SELECT * FROM Production.Product WHERE SellStartDate = '2008-04-30';
```
✅ Retrieves products with a **SellStartDate of April 30, 2008**.  

```sql
SELECT * FROM Production.Product WHERE SellStartDate BETWEEN '2011-04-30' AND '2012-05-31';
```
✅ Retrieves products **with SellStartDate between April 30, 2011, and May 31, 2012**.  

---

## **📌 Summary of `WHERE` Clause Uses**  
| **Condition Type** | **Example Query** |
|--------------------|------------------|
| Single value | `WHERE ProductID = 322` |
| Greater/Less than | `WHERE ProductID >= 900` |
| Range selection | `WHERE ProductID BETWEEN 350 AND 400` |
| Exact match | `WHERE Color = 'Silver'` |
| Excluding a value | `WHERE Color <> 'Silver'` |
| Multiple values | `WHERE Color IN ('Silver', 'Black', 'Red')` |
| Excluding multiple values | `WHERE Color NOT IN ('Silver', 'Black', 'Red')` |
| Multiple conditions (AND) | `WHERE Color = 'Silver' AND StandardCost > 1000.00` |
| Multiple conditions (OR) | `WHERE Color = 'Silver' OR StandardCost > 1000.00` |
| Checking for NULL | `WHERE Size IS NULL` |
| Checking for NOT NULL | `WHERE Size IS NOT NULL` |
| Date filtering | `WHERE SellStartDate = '2008-04-30'` |
| Date range filtering | `WHERE SellStartDate BETWEEN '2011-04-30' AND '2012-05-31'` |

---
