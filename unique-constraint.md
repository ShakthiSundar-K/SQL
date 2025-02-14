# **🔹 UNIQUE Constraint in SQL**  

The **UNIQUE** constraint ensures that **all values in a column or a combination of columns are distinct**. It prevents **duplicate values** but **allows a single NULL** (unlike PRIMARY KEY, which does not allow NULL at all).  

---

## **✅ Why is UNIQUE Important?**  
1️⃣ **Prevents Duplicate Entries** – Ensures data consistency.  
2️⃣ **Allows One NULL Value** – Unlike PRIMARY KEY, a column with UNIQUE **can store a single NULL**.  
3️⃣ **Improves Data Integrity** – Useful for columns like **email, phone number, Aadhar number, etc.**  
4️⃣ **Enhances Query Performance** – Helps in faster lookups when combined with indexing.  

---

## **✅ Defining UNIQUE While Creating a Table**  
You can apply `UNIQUE` while creating a table.  

📌 **Example 1: Defining UNIQUE Directly in Column Definition**  
```sql
CREATE TABLE students (
    StudentID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200) NOT NULL,  
    LastName VARCHAR(200) NOT NULL,  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    AadharNumber BIGINT UNIQUE  -- Unique constraint applied
);
```
✅ Here, `AadharNumber` must be **unique**, but it **can be NULL once**.  

📌 **Example 2: Defining UNIQUE Using CONSTRAINT Name**  
```sql
CREATE TABLE students (
    StudentID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200) NOT NULL,  
    LastName VARCHAR(200) NOT NULL,  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    AadharNumber BIGINT,  
    CONSTRAINT UC_STUDENTS UNIQUE(AadharNumber)
);
```
✅ This assigns a **name (`UC_STUDENTS`) to the UNIQUE constraint**, making it easier to manage.  

---

## **✅ Adding UNIQUE to an Existing Table**  
If a column was initially **not unique**, you can add the constraint later.  

📌 **Without Constraint Name:**  
```sql
ALTER TABLE students  
ADD UNIQUE(AadharNumber);
```
📌 **With Constraint Name:**  
```sql
ALTER TABLE students  
ADD CONSTRAINT UC_STUDENTS UNIQUE(AadharNumber);
```
✅ Using a **constraint name (`UC_STUDENTS`)** makes it easier to **drop or modify** later.  

---

## **✅ Dropping a UNIQUE Constraint**  
To remove a `UNIQUE` constraint, use:  

```sql
ALTER TABLE students  
DROP CONSTRAINT UC_STUDENTS;
```
✅ Now, `AadharNumber` can have **duplicate values**.  

---

## **✅ Difference Between UNIQUE and PRIMARY KEY**  

| Feature           | UNIQUE Constraint | PRIMARY KEY |
|------------------|----------------|-------------|
| **Enforces Uniqueness** | ✅ Yes | ✅ Yes |
| **Allows NULL Values** | ✅ Yes (Only one NULL) | ❌ No |
| **Number of Constraints per Table** | ✅ Multiple UNIQUE constraints allowed | ❌ Only **one** PRIMARY KEY per table |
| **Can Be Composite?** | ✅ Yes (Multiple columns) | ✅ Yes |
| **Indexing** | ✅ Indexed automatically | ✅ Indexed automatically |
| **Usage Example** | Email, Phone Number, AadharNumber | StudentID, EmployeeID |

✅ **Use PRIMARY KEY when:** The column is the **main identifier** (e.g., `StudentID`).  
✅ **Use UNIQUE when:** The column must be **distinct but not necessarily an identifier** (e.g., `AadharNumber`).  

---

## **🔹 Real-World Use Cases in Companies**  

### ✅ **1. User Registration (Email & Phone Number)**  
🔹 Users **must have a unique email and phone number**, but these are **not primary keys**.  
```sql
CREATE TABLE Users (
    UserID SERIAL PRIMARY KEY,  
    Email VARCHAR(255) UNIQUE,  
    PhoneNumber VARCHAR(15) UNIQUE
);
```
✅ Prevents duplicate emails or phone numbers.  

---

### ✅ **2. Employee Database (Aadhar/PAN Number)**  
🔹 Each employee has a **unique Aadhar or PAN number**, but not all employees may have a PAN card.  
```sql
CREATE TABLE Employees (
    EmployeeID INTEGER PRIMARY KEY,  
    Name VARCHAR(255) NOT NULL,  
    AadharNumber BIGINT UNIQUE,  
    PANNumber VARCHAR(10) UNIQUE
);
```
✅ Aadhar and PAN numbers **must be unique**, but **one NULL is allowed** for employees without PAN.  

---

### ✅ **3. E-Commerce (Order Tracking Numbers)**  
🔹 Each order has a **unique tracking number**, but it is **not the primary key**.  
```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,  
    TrackingNumber VARCHAR(50) UNIQUE,  
    OrderDate DATE NOT NULL
);
```
✅ Ensures no **two orders have the same tracking number**.  

---

## **🔹 Conclusion**  
✔ **UNIQUE** ensures that a column’s values are **distinct**, but allows **one NULL**.  
✔ **PRIMARY KEY** uniquely identifies each row and **does not allow NULL**.  
✔ Use **UNIQUE** for fields like **email, Aadhar, phone number, etc.**  
✔ Use **PRIMARY KEY** for fields like **StudentID, EmployeeID, OrderID**.  

💡 **Try these queries in your SQL database and see how UNIQUE works in real-world scenarios!** 🚀
