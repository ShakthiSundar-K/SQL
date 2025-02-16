# SQL Views

## **🔹 What is a View?**
A **View** in SQL is a **virtual table** based on the result of a SQL query. It does **not store actual data** but provides a **structured representation** of the underlying tables. Views are used for:

✔ **Security** – Restrict access to sensitive data.
✔ **Data Abstraction** – Simplify complex queries.
✔ **Performance Optimization** – Improve read performance (especially with indexed views).
✔ **Consistency** – Maintain consistent query logic across multiple applications.
✔ **Readability** – Provide a user-friendly interface to interact with the data.

---

## **🔹 Purpose of Views in SQL**

### **1️⃣ Security: Restrict Access to Sensitive Data**
Using views, you can expose **only necessary columns** while hiding confidential data.

#### **📝 Example: Protecting Salary Data**
```sql
CREATE VIEW employee_public AS
SELECT EmployeeID, FirstName, LastName, DepartmentID
FROM employee;
```
✅ This hides sensitive fields like `Salary` and `DateOfBirth` from unauthorized users.

---

### **2️⃣ Simplifying Complex Queries**
Instead of writing long, repetitive queries, we can create a view once and reuse it.

#### **📝 Example: Employee Department Details**
```sql
CREATE VIEW employee_dept_details AS
SELECT e.EmployeeID, e.FirstName, e.LastName, e.DepartmentID, d.DepartmentName
FROM employee e
JOIN department d ON e.DepartmentID = d.DepartmentID;
```
✅ Now, instead of writing the **JOIN query every time**, users can simply:
```sql
SELECT * FROM employee_dept_details;
```
---

### **3️⃣ Ensuring Data Consistency**
If business logic changes, updating a view **automatically updates all dependent queries**.

#### **📝 Example: Standardizing Date Format**
```sql
CREATE VIEW formatted_employee AS
SELECT EmployeeID, FirstName, LastName, FORMAT(DateOfBirth, 'yyyy-MM-dd') AS DOB
FROM employee;
```
✅ Ensures all date outputs follow the `yyyy-MM-dd` format.

---

### **4️⃣ Performance Optimization** *(Using Indexed Views)*

Views can improve query performance when indexed. Some databases (like SQL Server) allow **indexed/materialized views**, which store the result set for faster retrieval.

#### **📝 Example: Fast Employee Count per Department**
```sql
CREATE VIEW department_counts AS
SELECT DepartmentID, COUNT(*) AS employee_count
FROM employee
GROUP BY DepartmentID;
```
✅ Avoids re-executing the `COUNT(*)` function repeatedly.

---

## **🔹 Real-World Use Cases of Views**
| Use Case | Description |
|----------|------------|
| **Security** | Restrict sensitive columns like `Salary`, `SSN`, `DOB` |
| **Data Abstraction** | Simplifies multi-table joins for end users |
| **Reporting** | Generates department-wise sales or employee reports |
| **Performance Boost** | Indexed views improve read-heavy workloads |
| **Mutual Friends in Social Media** | Finding mutual friends using `JOIN` views |

---

## **📝 Try Yourself: SQL View Practice Questions**

### **(1) Easy: Employees Born After 2005**
👉 **Create a view `young_employees` that selects employees born after 2005.**
```sql
CREATE VIEW young_employees AS
SELECT EmployeeID, FirstName, LastName, DateOfBirth
FROM employee
WHERE DateOfBirth > '2005-01-01';
```
✅ **Check the Output**
```sql
SELECT * FROM young_employees;
```

---

### **(2) Medium: Count Employees per Department**
👉 **Create a view `department_counts` that counts employees per department.**
```sql
CREATE VIEW department_counts AS
SELECT d.DepartmentName, COUNT(e.EmployeeID) AS employee_count
FROM employee e
JOIN department d ON e.DepartmentID = d.DepartmentID
GROUP BY d.DepartmentName;
```
✅ **Check the Output**
```sql
SELECT * FROM department_counts;
```

---

### **(3) Hard: Employees with No Department**
👉 **Create a view `no_department_employees` that lists employees without a department.**
```sql
CREATE VIEW no_department_employees AS
SELECT EmployeeID, FirstName, LastName
FROM employee
WHERE DepartmentID IS NULL;
```
✅ **Check the Output**
```sql
SELECT * FROM no_department_employees;
```

---

## **🔗 For Differences Between Views, Temp Tables, and Stored Procedures**

[Refer to File 1](./file1.md)
---

## **📌 Final Thoughts**
✔ **Use Views for:** Security, Data Abstraction, Performance Optimization.
✔ **Views are Virtual:** They store queries, not actual data.
✔ **Cannot Always Modify Views:** Avoid using joins if you need updates.
✔ **Try Indexed Views:** Improve query speed with indexed/materialized views.


