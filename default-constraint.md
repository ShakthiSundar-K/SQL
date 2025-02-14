# **🔹 DEFAULT Constraint in SQL**  

The **DEFAULT constraint** automatically assigns a default value to a column when no value is provided during an `INSERT` operation. This ensures data consistency and reduces the need for manual entry of common values.  

---

## **✅ Why is DEFAULT Important?**  
1️⃣ **Ensures Data Consistency** – Assigns a standard value when data is missing.  
2️⃣ **Reduces Manual Effort** – Saves time by automatically filling common values.  
3️⃣ **Prevents NULL Issues** – Ensures a column never gets NULL unless explicitly set.  
4️⃣ **Improves Data Integrity** – Helps maintain logical correctness in the database.  

---

## **✅ Defining DEFAULT While Creating a Table**  

📌 **Example 1: Setting a DEFAULT Value for a Column**  
```sql
CREATE TABLE employees (
    EmployeeID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200) NOT NULL,  
    LastName VARCHAR(200) NOT NULL,  
    DateOfBirth DATE,  
    Gender CHAR(1) DEFAULT 'M',  -- If no value is provided, 'M' is assigned  
    JoiningDate DATE DEFAULT CURRENT_DATE, -- Assigns today's date  
    Salary INT DEFAULT 50000  -- If salary is missing, assigns 50,000  
);
```
✅ Here, if we **insert** a new employee **without specifying Gender, JoiningDate, or Salary**, these defaults are used.  

📌 **Example 2: Using CONSTRAINT Name for DEFAULT**  
```sql
CREATE TABLE employees (
    EmployeeID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200) NOT NULL,  
    LastName VARCHAR(200) NOT NULL,  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    Salary INT,  
    CONSTRAINT DF_EMP_GENDER DEFAULT 'M' FOR Gender,  
    CONSTRAINT DF_EMP_SALARY DEFAULT 50000 FOR Salary  
);
```
✅ Using **constraint names** (`DF_EMP_GENDER`, `DF_EMP_SALARY`) makes it easier to **modify or drop** constraints later.  

---

## **✅ Adding DEFAULT to an Existing Table**  

If a column was created **without a DEFAULT constraint**, you can add it later.  

📌 **Without Constraint Name:**  
```sql
ALTER TABLE employees  
ALTER COLUMN Gender SET DEFAULT 'M';
```
📌 **With Constraint Name:**  
```sql
ALTER TABLE employees  
ADD CONSTRAINT DF_EMP_GENDER DEFAULT 'M' FOR Gender;
```
✅ Naming the constraint (`DF_EMP_GENDER`) makes it easier to manage.  

---

## **✅ Removing a DEFAULT Constraint**  

To **drop** a DEFAULT constraint, use:  
```sql
ALTER TABLE employees  
ALTER COLUMN Gender DROP DEFAULT;
```
Or if a **named constraint** was used:  
```sql
ALTER TABLE employees  
DROP CONSTRAINT DF_EMP_GENDER;
```
✅ Now, the column **no longer has a default value** when inserting data.  

---

## **✅ Real-World Use Cases in Companies**  

### ✅ **1. Employee Management (Default Joining Date & Salary)**  
🔹 Companies often set **default joining dates** and **minimum salary limits**.  
```sql
CREATE TABLE Employees (
    EmployeeID INTEGER PRIMARY KEY,  
    Name VARCHAR(255) NOT NULL,  
    JoiningDate DATE DEFAULT CURRENT_DATE,  
    Salary INT DEFAULT 30000
);
```
✅ If **JoiningDate or Salary is not provided**, the database **automatically fills them**.  

---

### ✅ **2. Banking System (Default Account Status & Minimum Balance)**  
🔹 Banks set **default statuses for new accounts** and **minimum balances**.  
```sql
CREATE TABLE Accounts (
    AccountID INTEGER PRIMARY KEY,  
    AccountHolder VARCHAR(255) NOT NULL,  
    Balance DECIMAL(10,2) DEFAULT 1000,  
    Status VARCHAR(50) DEFAULT 'Active'
);
```
✅ If a new account is created **without specifying Balance or Status**, it **defaults to ₹1000 and ‘Active’**.  

---

### ✅ **3. E-Commerce (Default Product Status & Stock Level)**  
🔹 Online stores **auto-assign stock levels** and **mark products as ‘Available’ by default**.  
```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,  
    Name VARCHAR(255) NOT NULL,  
    Price DECIMAL(10,2) NOT NULL,  
    Stock INT DEFAULT 10,  
    Status VARCHAR(20) DEFAULT 'Available'
);
```
✅ Ensures all products **start with 10 units in stock** and are **set as ‘Available’ unless specified otherwise**.  

---

## **🔹 Conclusion**  
✔ **DEFAULT** constraints **automate value assignment**, reducing manual work.  
✔ Prevents **NULL values** and maintains **data integrity**.  
✔ **Using CONSTRAINT names** makes modifications easier.  
✔ Helps **simplify queries** and **minimize errors** in applications.  

💡 **Try these queries in your SQL database and see how DEFAULT constraints make data handling easier!** 🚀
