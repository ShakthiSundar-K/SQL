

# **📌 Table Operations in SQL**  

## **1️⃣ CREATE TABLE**  
### 🔹 **Purpose**  
The `CREATE TABLE` command is used to define a new table with specific columns and data types.  

### 🔹 **Syntax**  
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```

### 🔹 **Example**  
```sql
CREATE TABLE students (
    rollno INTEGER,
    name VARCHAR(256),
    department VARCHAR(200),
    age INTEGER,
    date_of_birth DATE,
    gender CHAR(1)
);
```
### 🔹 **Need & When to Use?**  
- Used when defining the structure of a table.  
- Ensures data is stored in an organized manner.  
- Each column is defined with a **data type** and optional **constraints** (e.g., `NOT NULL`, `PRIMARY KEY`).  

---

## **2️⃣ SELECT Statement**  
### 🔹 **Purpose**  
The `SELECT` statement is used to retrieve data from a table.  

### 🔹 **Syntax**  
```sql
SELECT column1, column2, ... FROM table_name;
```

### 🔹 **Example 1: Select All Columns**  
```sql
SELECT * FROM students;
```
✅ **Retrieves all columns and rows from the `students` table.**  

### 🔹 **Example 2: Select Specific Columns**  
```sql
SELECT rollno, name FROM students;
```
✅ **Retrieves only the `rollno` and `name` columns from the `students` table.**  

### 🔹 **Need & When to Use?**  
- Use `SELECT *` when you need **all columns** from a table.  
- Use `SELECT column_names` when fetching **specific columns** for efficiency.  

---

## **3️⃣ INSERT INTO (Adding Data to the Table)**  
### 🔹 **Purpose**  
The `INSERT INTO` statement is used to add new rows of data into a table.  

### 🔹 **Syntax**  
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### 🔹 **Example**  
```sql
INSERT INTO students VALUES (1001, 'Shakthi', 'CSE', 21, '2003-06-17', 'M');
```
✅ **Inserts a new student record into the `students` table.**  

### 🔹 **Need & When to Use?**  
- Use when adding new data into a table.  
- Always ensure the values match the column **data types and order**.  
- If inserting into specific columns, mention them explicitly:  
  ```sql
  INSERT INTO students (rollno, name, department) VALUES (1002, 'Sundar', 'IT');
  ```
  🚀 **This method is preferred** as it avoids issues when adding new columns in the future.  

---

### **🔴 Important Notes**
✔ Ensure the **column names match** while inserting values.  
✔ `CHAR(1)` is used for **gender** as it stores only a single character.  
✔ `DATE` format should be **YYYY-MM-DD** in SQL.  
✔ The `SELECT` statement can be used to verify inserted data.  

---

