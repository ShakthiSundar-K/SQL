

# 🔹 **Views, Temporary Tables & Stored Procedures**  

| Feature           | Views  | Temporary Tables  | Stored Procedures |
|------------------|--------|-----------------|------------------|
| **Definition** | A virtual table that represents a saved SQL query. | A temporary table that stores intermediate results. | A set of SQL statements stored for reuse. |
| **Storage** | No physical storage; just a saved query definition. | Physically exists in tempdb while in use. | Stored in the database, executes queries when called. |
| **Scope** | Available as long as the database exists. | Available only for the session (or transaction). | Permanent but executed only when needed. |
| **Performance** | Can improve performance for complex queries. | Helps store intermediate results for complex queries. | Reduces query repetition, improving efficiency. |
| **Use Case** | Simplifies querying by hiding complexity. | Stores temporary results during query execution. | Automates tasks like data updates and reporting. |

---

## 🔹 **1️⃣ What is a View?**
A **View** is a virtual table that represents a pre-defined SQL query. It does not store data but allows users to interact with it as if it were a real table.  

### ✅ **Example**
Suppose we have an `employee` table and we frequently need to get employee details without exposing sensitive data like Date of Birth.  

```sql
CREATE VIEW EmployeeBasicInfo AS 
SELECT EmployeeID, FirstName, LastName, Gender 
FROM employee;
```

Now, instead of writing the full query every time, we can simply do:

```sql
SELECT * FROM EmployeeBasicInfo;
```

### 🔥 **When to Use Views?**
✔ To simplify complex queries.  
✔ To **restrict access** to specific columns for security.  
✔ To **standardize** commonly used queries.  

---

## 🔹 **2️⃣ What is a Temporary Table?**
A **Temporary Table** is a table that exists **only for the duration of a session or transaction**. It stores intermediate results.  

### ✅ **Example**
Let’s say we need to find **employees who earn above the average salary**. We can first store the average salary in a temporary table:

```sql
CREATE TEMP TABLE AvgSalary AS
SELECT AVG(Salary) AS AverageSalary FROM employee;

SELECT e.EmployeeID, e.FirstName, e.LastName, e.Salary
FROM employee e, AvgSalary a
WHERE e.Salary > a.AverageSalary;
```

Once the session ends, the temporary table disappears.  

### 🔥 **When to Use Temporary Tables?**
✔ When working with **intermediate data** for complex queries.  
✔ When handling **large datasets** to improve performance.  
✔ When performing **multiple operations on the same dataset** in a session.  

---

## 🔹 **3️⃣ What is a Stored Procedure?**
A **Stored Procedure** is a set of SQL queries that can be stored and executed as needed. It is **used for automation** and improving query efficiency.  

### ✅ **Example**
If we frequently fetch employee details by department, we can create a stored procedure:

```sql
CREATE PROCEDURE GetEmployeesByDepartment (@DeptID INT)
AS
BEGIN
    SELECT EmployeeID, FirstName, LastName, DepartmentID
    FROM employee
    WHERE DepartmentID = @DeptID;
END;
```

Now, instead of writing the full query, we can just call:

```sql
EXEC GetEmployeesByDepartment 11;
```

### 🔥 **When to Use Stored Procedures?**
✔ When queries need to be **reused frequently**.  
✔ When executing **multiple queries together**.  
✔ When dealing with **transaction management** (e.g., inserting data in multiple tables).  
✔ To **enhance security** by restricting direct access to tables.  

---

# 🔹 **Key Differences: When to Use What?**  

- ✅ **Use a View** when you need to **simplify queries** and **restrict access** to certain columns.  
- ✅ **Use a Temporary Table** when handling **intermediate results** for a session.  
- ✅ **Use a Stored Procedure** when you need **automation, parameterized queries, and repeated execution**.  

---

## **🚀 Real-World Use Cases**
| Use Case | Best Option |
|----------|------------|
| Showing a filtered version of employee data without exposing sensitive info | **View** |
| Storing temporary calculations for a complex financial report | **Temporary Table** |
| Automating salary updates for all employees at month-end | **Stored Procedure** |
| Frequently used joins for reporting dashboards | **View** |
| Storing results of a complex query for further filtering in the same session | **Temporary Table** |
| Creating a function that calculates and returns tax for given salary | **Stored Procedure** |

---

## **🔹 Final Thoughts**
- Views are like **saved queries** that improve readability and security.  
- Temporary tables **store temporary data** that disappears after the session.  
- Stored procedures **automate queries** and **optimize** frequently executed logic.  

