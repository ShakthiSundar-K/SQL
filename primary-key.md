# **🔹 Primary Key Constraint in SQL**  

A **Primary Key** is a column or a set of columns that **uniquely identifies** each row in a table. It ensures that the data remains **distinct and non-null**, helping maintain **data integrity** in a relational database.  

---

## **✅ Need & Purpose of a Primary Key**  
The **primary need of a primary key** is to **uniquely identify each record in a table**. This is crucial because:  
1. **Uniqueness** – Ensures that no two rows have the same identifier.  
2. **Non-Nullability** – A primary key column **cannot have NULL values**.  
3. **Efficient Searching & Indexing** – The database **automatically creates an index**, making queries faster.  
4. **Data Integrity & Consistency** – Ensures **no duplicate records** exist.  
5. **Used in Relationships** – Foreign keys in other tables refer to primary keys to maintain relationships.  

---

## **✅ Types of Primary Keys**  

1️⃣ **Single-Column Primary Key**  
   - Uses a **single column** to uniquely identify each row.  
   - Example: `StudentID` in a **Students** table.  
   ```sql
   CREATE TABLE Students (
       StudentID INTEGER PRIMARY KEY,
       Name VARCHAR(256),
       Age INTEGER
   );
   ```

2️⃣ **Composite Primary Key (Multi-Column Primary Key)**  
   - When a **single column is not enough**, multiple columns together ensure uniqueness.  
   - Example: A student enrolling in multiple courses. Here, `StudentID` alone is not unique, so we combine it with `CourseID`.  
   ```sql
   CREATE TABLE Enrollments (
       StudentID INTEGER,
       CourseID INTEGER,
       EnrollmentDate DATE,
       CONSTRAINT pk_enrollments PRIMARY KEY(StudentID, CourseID)
   );
   ```

3️⃣ **Natural Primary Key**  
   - Uses an **existing real-world value** (like **email, SSN, passport number**) as a primary key.  
   - Example: Using **Email** as a primary key in a **Users** table.  
   ```sql
   CREATE TABLE Users (
       Email VARCHAR(255) PRIMARY KEY,
       Name VARCHAR(100),
       Age INTEGER
   );
   ```

4️⃣ **Surrogate Primary Key**  
   - A **system-generated** unique identifier, usually an **auto-incremented integer**.  
   - Example: Using an **auto-generated `UserID`** instead of an email.  
   ```sql
   CREATE TABLE Users (
       UserID SERIAL PRIMARY KEY,
       Email VARCHAR(255) UNIQUE,
       Name VARCHAR(100)
   );
   ```

---

## **✅ Defining a Primary Key in SQL**  

There are **two main ways** to define a primary key when creating a table:  

📌 **Method 1 – Inline Definition**  
```sql
CREATE TABLE students (
    rollno INTEGER PRIMARY KEY,
    name VARCHAR(256),
    department VARCHAR(200),
    age INTEGER,
    date_of_birth DATE,
    gender CHAR(1)
);
```
✅ This is **quick and simple** but does not allow custom constraint names.  

📌 **Method 2 – Using `CONSTRAINT` Name**  
```sql
CREATE TABLE students (
    rollno INTEGER,
    name VARCHAR(256),
    department VARCHAR(200),
    age INTEGER,
    date_of_birth DATE,
    gender CHAR(1),
    CONSTRAINT pk_students PRIMARY KEY(rollno)
);
```
✅ **Advantages of using a constraint name (`pk_students`)**:  
- Easier to **drop or modify** later.  
- Improves **readability and maintainability**.  

---

## **✅ Adding a Primary Key to an Existing Table**  
If a table is **already created without a primary key**, you can **add it later** using `ALTER TABLE`.  

📌 **Without Constraint Name**  
```sql
ALTER TABLE students  
ADD PRIMARY KEY(rollno);
```
📌 **With Constraint Name**  
```sql
ALTER TABLE students  
ADD CONSTRAINT pk_students PRIMARY KEY(rollno);
```
✅ **Before adding a primary key, ensure the column has no NULL or duplicate values**.  

---

## **✅ Composite Primary Key in an Existing Table**  
📌 **Example (Adding Composite Key Using `ALTER TABLE`)**  
```sql
ALTER TABLE students  
ADD CONSTRAINT pk_students PRIMARY KEY(rollno, department);
```
✅ **Use Case:** `rollno` alone is not unique, so `rollno + department` together ensure uniqueness.  

---

## **✅ Dropping a Primary Key**  
If you need to **remove** a primary key, use `DROP CONSTRAINT`.  

📌 **Example:**  
```sql
ALTER TABLE students  
DROP CONSTRAINT pk_students;
```
✅ This allows duplicates and null values in those columns again.  

---

## **🔹 Real-World Use Cases in Companies**  

### ✅ **1. E-Commerce (Order Management)**
🔹 In an online shopping system, each **order needs a unique identifier**.  
```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    UserID INTEGER,
    OrderDate DATE,
    TotalAmount DECIMAL(10,2)
);
```
✅ **Why?** Without a unique `OrderID`, duplicate or missing orders could occur.  

---

### ✅ **2. Banking (Account Numbers & Transactions)**
🔹 Every **bank account** must have a unique identifier.  
```sql
CREATE TABLE BankAccounts (
    AccountNumber VARCHAR(20) PRIMARY KEY,
    CustomerID INTEGER,
    Balance DECIMAL(15,2)
);
```
✅ **Why?** If `AccountNumber` is not unique, two customers might end up with the same account.  

---

### ✅ **3. Healthcare (Patient Records)**
🔹 Hospitals use **unique patient IDs** to manage records.  
```sql
CREATE TABLE Patients (
    PatientID INTEGER PRIMARY KEY,
    Name VARCHAR(255),
    DateOfBirth DATE,
    ContactNumber VARCHAR(15)
);
```
✅ **Why?** Without `PatientID`, duplicate records can lead to **misdiagnosis** or **wrong treatment**.  

---

### ✅ **4. Ride-Sharing Apps (Driver & Ride Data)**
🔹 Uber assigns a **unique ride ID** to each trip.  
```sql
CREATE TABLE Rides (
    RideID INTEGER PRIMARY KEY,
    DriverID INTEGER,
    PassengerID INTEGER,
    RideStatus VARCHAR(50)
);
```
✅ **Why?** Without a `RideID`, ride details might get **mixed up**.  

---

### ✅ **5. Universities & Colleges (Student Data)**
🔹 A university uses a **composite primary key** for student enrollments.  
```sql
CREATE TABLE Enrollments (
    StudentID INTEGER,
    CourseID INTEGER,
    EnrollmentDate DATE,
    CONSTRAINT pk_enrollments PRIMARY KEY(StudentID, CourseID)
);
```
✅ **Why?** Since a student can enroll in multiple courses, `StudentID` alone is **not unique**.  

---

## **🔹 Conclusion**
✔ **Primary Keys** ensure **uniqueness** and **data integrity**.  
✔ **Types of Primary Keys:** Single, Composite, Natural, and Surrogate.  
✔ **Use Constraint Names** for better maintainability.  
✔ **Used in e-commerce, banking, healthcare, education, ride-sharing**, and more.  

💡 **Try these SQL queries in your database and see how they work!** 🚀
