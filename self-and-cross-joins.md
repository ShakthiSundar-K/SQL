# 🔹 **Understanding SQL SELF JOIN & CROSS JOIN**
When working with relational databases, we often need to compare records **within the same table**. This is where **SELF JOIN** and **CROSS JOIN** come into play.

## 🏛 **Types of Joins Covered**
1️⃣ **SELF JOIN** – Joins a table to itself, comparing rows within the same table.
2️⃣ **CROSS JOIN** – Returns a Cartesian product of all possible row combinations between two tables.

---

## 🔹 **1️⃣ SELF JOIN** (Joining a Table to Itself)
A **SELF JOIN** is used when we want to relate rows within the same table. It is commonly used in hierarchical relationships like employees and managers.

### 📌 **Example Scenario: Employee & Manager Relationship**
Let's consider an **Employee** table where each employee has a **ManagerID** referring to another EmployeeID.

### **Table: Employee**
| EmployeeID | FirstName  | LastName  | ManagerID |
|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | 1002 |
| 1002 | Anand | Venkat | 1003 |
| 1003 | Bala | Sundaram | 1007 |
| 1004 | Deepa | Mani | 1007 |
| 1005 | Deepa | Mahesh | 1007 |
| 1006 | Gokul | Ram | 1001 |
| 1007 | Shreya | Gopi | 1002 |
| 1008 | Abdul | Rahman | NULL |

### **Applying SELF JOIN**
```sql
SELECT e1.EmployeeID, e1.FirstName, e1.LastName, e1.ManagerID,
       e2.FirstName + ' ' + e2.LastName AS Manager_Name
FROM employee e1
JOIN employee e2
ON e1.ManagerID = e2.EmployeeID;
```

### **Output:**
| EmployeeID | FirstName  | LastName  | ManagerID | Manager_Name |
|------------|------------|------------|------------|------------|
| 1001 | Aishwarya | Jayaram | 1002 | Anand Venkat |
| 1002 | Anand | Venkat | 1003 | Bala Sundaram |
| 1003 | Bala | Sundaram | 1007 | Shreya Gopi |
| 1004 | Deepa | Mani | 1007 | Shreya Gopi |
| 1005 | Deepa | Mahesh | 1007 | Shreya Gopi |
| 1006 | Gokul | Ram | 1001 | Aishwarya Jayaram |
| 1007 | Shreya | Gopi | 1002 | Anand Venkat |

👉 **EmployeeID 1008 is missing because they have no manager (ManagerID = NULL).**

### 📌 **Real-World Use Cases for SELF JOIN**
- **Finding Employees & Managers**
- **Finding Mutual Friends (Social Networks)** 🏆
  - **Example:** In a **friendship table** where users are connected via `UserID` and `FriendID`, we can use a SELF JOIN to find mutual friends.

  ```sql
  SELECT f1.UserID, f2.FriendID AS MutualFriend
  FROM Friends f1
  JOIN Friends f2
  ON f1.FriendID = f2.UserID
  WHERE f1.UserID = 1;
  ```

---

## 🔹 **2️⃣ CROSS JOIN** (Cartesian Product)
A **CROSS JOIN** returns every possible combination of rows from two tables. It does not require a matching column.

### 📌 **Example Scenario: Employee Pairings**
We want to **pair every employee with every other employee** (excluding self-pairs).

```sql
SELECT e1.FirstName + ' ' + e1.LastName AS Employee_1,
       e2.FirstName + ' ' + e2.LastName AS Employee_2
FROM employee e1
CROSS JOIN employee e2
WHERE e1.EmployeeID <> e2.EmployeeID;
```

### **Output (Sample Rows):**
| Employee_1 | Employee_2 |
|------------|------------|
| Aishwarya Jayaram | Anand Venkat |
| Aishwarya Jayaram | Bala Sundaram |
| Anand Venkat | Deepa Mani |
| Deepa Mani | Deepa Mahesh |
| Gokul Ram | Abdul Rahman |

👉 **Each employee is paired with every other employee, avoiding self-pairing.**

### 📌 **Real-World Use Cases for CROSS JOIN**
- **Generating Test Data Combinations**
- **Pairing Employees for Teamwork Assignments**
- **Matching Products with Promotions**

---

## 🎯 **Practice Questions**
### ✅ **Easy:**
Find all employees who do not have a manager (ManagerID is NULL).
```sql
SELECT EmployeeID, FirstName, LastName
FROM employee
WHERE ManagerID IS NULL;
```

### ✅ **Medium:**
Find employees who share the same manager.
```sql
SELECT e1.FirstName AS Employee_1, e2.FirstName AS Employee_2, e1.ManagerID
FROM employee e1
JOIN employee e2
ON e1.ManagerID = e2.ManagerID
AND e1.EmployeeID <> e2.EmployeeID;
```

### ✅ **Hard:**
Find mutual friends from a `Friends` table where each row has `UserID` and `FriendID`.
```sql
SELECT f1.UserID, f2.FriendID AS MutualFriend
FROM Friends f1
JOIN Friends f2
ON f1.FriendID = f2.UserID;
```

---

## 🔹 **Final Thoughts**
- **SELF JOIN** is useful for hierarchical relationships like managers and employees.
- **CROSS JOIN** is useful when all possible combinations are needed.

Mastering these joins helps in handling complex relationships in databases efficiently! 🚀

