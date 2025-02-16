# 🔹 **Understanding SQL JOINS**  
When working with relational databases, we often need to retrieve **data from multiple tables**. This is where **JOINS** come in.  

A **JOIN** allows us to combine records from two or more tables based on a **related column**. This helps in retrieving meaningful insights from structured data.  

### 🏛 **Types of SQL JOINS**  

1️⃣ **INNER JOIN** – Returns only **matching** records between both tables.  
2️⃣ **LEFT JOIN (LEFT OUTER JOIN)** – Returns **all** records from the **left table** and matching records from the right.  
3️⃣ **RIGHT JOIN (RIGHT OUTER JOIN)** – Returns **all** records from the **right table** and matching records from the left.  
4️⃣ **FULL JOIN (FULL OUTER JOIN)** – Returns **all records** from both tables, matching where possible.  

![WhatsApp Image 2025-02-16 at 11 07 33_c345b877](https://github.com/user-attachments/assets/6de97440-ced5-495f-b8c7-f0a9944f2750)

---

## 🔹 **Example Scenario: Employees & Departments**  

Let’s consider an **Employee** table storing employee details and a **Department** table storing department names. Employees belong to departments, so we need to join these tables.

### **Table 1: Employee**
| EmployeeID | FirstName  | LastName  | DateOfBirth | Gender | DepartmentID |
|------------|------------|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | 2005-04-24 | F | 11 |
| 1002 | Anand | Venkat | 2005-05-22 | M | 12 |
| 1003 | Bala | Sundaram | 2004-11-02 | M | 13 |
| 1004 | Deepa | Mani | 2004-12-09 | F | 11 |
| 1005 | Deepa | Mahesh | 2005-05-29 | F | 14 |
| 1006 | Gokul | Ram | 2004-11-27 | M | 13 |
| 1007 | Shreya | Gopi | 2005-06-20 | F | 17 |
| 1008 | Abdul | Rahman | 2005-07-30 | M | 18 |

---

### **Table 2: Department**
| DepartmentID | DepartmentName  |
|------------|------------|
| 11 | Engineering |
| 12 | Finance |
| 13 | Sales |
| 14 | Marketing |
| 15 | Human Resources |
| 16 | IT |

---

## 🔹 **Applying SQL Joins**  

### **1️⃣ INNER JOIN (Most Common)**
Returns **only matching records** from both tables.

```sql
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName 
FROM employee e
INNER JOIN department d 
ON e.DepartmentID = d.DepartmentID;
```

| EmployeeID | FirstName  | LastName  | DepartmentName |
|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | Engineering |
| 1002 | Anand | Venkat | Finance |
| 1003 | Bala | Sundaram | Sales |
| 1004 | Deepa | Mani | Engineering |
| 1005 | Deepa | Mahesh | Marketing |
| 1006 | Gokul | Ram | Sales |

👉 **Employees with missing DepartmentIDs (17, 18) are excluded.**

---

### **2️⃣ LEFT JOIN**
Returns **all records from Employee**, and matching records from Department.

```sql
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName 
FROM employee e
LEFT JOIN department d 
ON e.DepartmentID = d.DepartmentID;
```

| EmployeeID | FirstName  | LastName  | DepartmentName |
|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | Engineering |
| 1002 | Anand | Venkat | Finance |
| 1003 | Bala | Sundaram | Sales |
| 1004 | Deepa | Mani | Engineering |
| 1005 | Deepa | Mahesh | Marketing |
| 1006 | Gokul | Ram | Sales |
| 1007 | Shreya | Gopi | NULL |
| 1008 | Abdul | Rahman | NULL |

👉 Employees **without a matching department (17, 18)** are still included, but their department appears as **NULL**.

---

### **3️⃣ RIGHT JOIN**
Returns **all records from Department**, and matching Employees.

```sql
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName 
FROM employee e
RIGHT JOIN department d 
ON e.DepartmentID = d.DepartmentID;
```

| EmployeeID | FirstName  | LastName  | DepartmentName |
|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | Engineering |
| 1002 | Anand | Venkat | Finance |
| 1003 | Bala | Sundaram | Sales |
| 1004 | Deepa | Mani | Engineering |
| 1005 | Deepa | Mahesh | Marketing |
| 1006 | Gokul | Ram | Sales |
| NULL | NULL | NULL | Human Resources |
| NULL | NULL | NULL | IT |

👉 Departments **without any employees** (HR & IT) appear with **NULL values** for Employee data.

---

### **4️⃣ FULL OUTER JOIN**
Returns **all records from both tables**.

```sql
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName 
FROM employee e
FULL JOIN department d 
ON e.DepartmentID = d.DepartmentID;
```

| EmployeeID | FirstName  | LastName  | DepartmentName |
|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | Engineering |
| 1002 | Anand | Venkat | Finance |
| 1003 | Bala | Sundaram | Sales |
| 1004 | Deepa | Mani | Engineering |
| 1005 | Deepa | Mahesh | Marketing |
| 1006 | Gokul | Ram | Sales |
| 1007 | Shreya | Gopi | NULL |
| 1008 | Abdul | Rahman | NULL |
| NULL | NULL | NULL | Human Resources |
| NULL | NULL | NULL | IT |

---

## 🎯 **Where Are Joins Used in Companies?**
- **HR Systems** – Employee details linked to department, salary.
- **E-Commerce** – Customers linked to orders, payments.
- **Banking** – Accounts linked to transactions, loans.
- **Healthcare** – Patients linked to doctors, treatments.

---

## 📝 **Practice Questions**

### ✅ **Easy:**  
Find all employees who belong to the "Sales" department.  
```sql
SELECT e.EmployeeID, e.FirstName, e.LastName 
FROM employee e
JOIN department d ON e.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'Sales';
```

### ✅ **Medium:**  
Find departments that have **no employees assigned**.
```sql
SELECT d.DepartmentID, d.DepartmentName 
FROM department d
LEFT JOIN employee e ON d.DepartmentID = e.DepartmentID
WHERE e.EmployeeID IS NULL;
```

---

## 🔹 **Final Thoughts**
SQL Joins are crucial for combining related data in real-world applications. Mastering them enables efficient querying and data analysis, making your applications more powerful and insightful.

