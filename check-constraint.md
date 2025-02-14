# **🔹 CHECK Constraint in SQL**  

The **CHECK constraint** is used to **enforce conditions** on column values, ensuring data validity. If a value does not satisfy the condition, the database rejects the entry.  

---

## **✅ Why is CHECK Important?**  
1️⃣ **Ensures Data Accuracy** – Prevents invalid data entries.  
2️⃣ **Applies Business Rules** – Enforces company policies, such as minimum salary.  
3️⃣ **Reduces Application-Level Validation** – Shifts validation to the database, making queries more reliable.  
4️⃣ **Improves Data Integrity** – Prevents incorrect data from being inserted or updated.  

---

## **✅ Defining CHECK While Creating a Table**  

📌 **Example 1: Defining CHECK Directly in Column Definition**  
```sql
CREATE TABLE employee (
    EmployeeID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200),  
    LastName VARCHAR(200),  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    Salary INT CHECK (Salary >= 5000)  -- Salary must be at least 5000
);
```
✅ Here, any employee with a **salary below 5000 will not be allowed**.  

📌 **Example 2: Defining CHECK Using CONSTRAINT Name**  
```sql
CREATE TABLE employee (
    EmployeeID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200),  
    LastName VARCHAR(200),  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    Salary INT,  
    CONSTRAINT CHK_EMPLOYEE CHECK (Salary >= 5000 AND DateOfBirth >= '1980-01-01')
);
```
✅ This applies two conditions:  
- **Salary must be at least 5000**  
- **Date of Birth must be after or on January 1, 1980**  

Using **CONSTRAINT CHK_EMPLOYEE** makes it easier to **modify or delete** the constraint later.  

---

## **✅ Adding CHECK to an Existing Table**  

If the column was initially **created without a CHECK constraint**, you can add it later.  

📌 **Without Constraint Name:**  
```sql
ALTER TABLE employee  
ADD CHECK (Salary >= 5000);
```
📌 **With Constraint Name:**  
```sql
ALTER TABLE employee  
ADD CONSTRAINT CHK_EMPLOYEE CHECK (Salary >= 5000 AND DateOfBirth >= '1980-01-01');
```
✅ Naming the constraint (`CHK_EMPLOYEE`) makes it easier to manage.  

---

## **✅ Dropping a CHECK Constraint**  
To remove a **CHECK** constraint, use:  

```sql
ALTER TABLE employee  
DROP CONSTRAINT CHK_EMPLOYEE;
```
✅ Now, salary and date of birth **can have any values**.  

---

## **✅ Real-World Use Cases in Companies**  

### ✅ **1. Employee Management (Minimum Salary & Age Limit)**  
🔹 Companies ensure that employees receive **at least a minimum salary** and are **above a certain age**.  
```sql
CREATE TABLE Employees (
    EmployeeID INTEGER PRIMARY KEY,  
    Name VARCHAR(255) NOT NULL,  
    Salary INT CHECK (Salary >= 10000),  
    Age INT CHECK (Age >= 18)
);
```
✅ Prevents hiring employees **under 18** or with **salary below 10,000**.  

---

### ✅ **2. Banking System (Minimum Balance Requirement)**  
🔹 Banks require **a minimum balance** to be maintained in accounts.  
```sql
CREATE TABLE Accounts (
    AccountID INTEGER PRIMARY KEY,  
    AccountHolder VARCHAR(255) NOT NULL,  
    Balance DECIMAL(10,2) CHECK (Balance >= 1000)
);
```
✅ Prevents customers from **having less than ₹1000** in their accounts.  

---

### ✅ **3. E-Commerce (Valid Product Prices & Stock Levels)**  
🔹 Online stores ensure that **product prices are positive** and **stock levels are non-negative**.  
```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,  
    Name VARCHAR(255) NOT NULL,  
    Price DECIMAL(10,2) CHECK (Price > 0),  
    Stock INT CHECK (Stock >= 0)
);
```
✅ Prevents **negative prices or negative stock** values.  

---

## **🔹 Conclusion**  
✔ **CHECK** enforces conditions at the database level, preventing invalid data entry.  
✔ **Use CHECK constraints** for **business rules** like minimum salary, valid age, stock levels, etc.  
✔ **Using CONSTRAINT names** makes modifications easier.  
✔ Helps **reduce bugs** and **improves data integrity** in applications.  

💡 **Try these queries in your SQL database and see how CHECK constraints work in real-world scenarios!** 🚀
