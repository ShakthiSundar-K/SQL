

# **📌 Table Modification Commands in SQL**  

## **4️⃣ ALTER TABLE (Modifying Table Structure)**  
### 🔹 **Purpose**  
The `ALTER TABLE` command is used to modify an existing table by adding, deleting, or modifying columns.  

### 🔹 **Syntax**  
```sql
ALTER TABLE table_name ADD column_name datatype;
ALTER TABLE table_name DROP COLUMN column_name;
ALTER TABLE table_name MODIFY COLUMN column_name new_datatype;
```

### 🔹 **Example 1: Adding a New Column**  
```sql
ALTER TABLE students ADD gpa FLOAT;
```
✅ **Adds a new column `gpa` of type `FLOAT` to the `students` table.**  

### 🔹 **Example 2: Dropping a Column**  
```sql
ALTER TABLE students DROP COLUMN age;
```
✅ **Removes the `age` column from the `students` table permanently.**  

### 🔹 **Need & When to Use?**  
- Use `ADD` when you need to include additional attributes in a table.  
- Use `DROP COLUMN` when a column is no longer needed (⚠ **Irreversible** unless restored manually).  
- Use `MODIFY COLUMN` when changing the datatype of an existing column.  

---

## **5️⃣ UPDATE (Modifying Data in a Table)**  
### 🔹 **Purpose**  
The `UPDATE` statement is used to modify existing records in a table.  

### 🔹 **Syntax**  
```sql
UPDATE table_name SET column_name = value WHERE condition;
```

### 🔹 **Example**  
```sql
UPDATE students SET gpa = 9.27 WHERE rollno = 1001;
```
✅ **Updates the `gpa` of the student with `rollno = 1001` to `9.27`.**  

### 🔹 **Need & When to Use?**  
- Use when modifying **existing** records instead of inserting new ones.  
- Always include a `WHERE` condition to avoid updating **all rows unintentionally**.  
- If you need to update multiple columns at once:  
  ```sql
  UPDATE students SET name = 'Shakthi Sundar', gpa = 9.5 WHERE rollno = 1001;
  ```

---

## **6️⃣ Other `ALTER TABLE` Methods**  
### **🔹 Changing the Data Type of a Column**  
```sql
ALTER TABLE students MODIFY COLUMN gpa DECIMAL(3,2);
```
✅ **Changes the `gpa` column to `DECIMAL(3,2)`, allowing values like `9.27`.**  

---

### **🔹 Renaming a Column**  
```sql
ALTER TABLE students RENAME COLUMN gpa TO cgpa;
```
✅ **Renames `gpa` to `cgpa`.**  

---

### **🔹 Renaming a Table**  
```sql
ALTER TABLE students RENAME TO student_records;
```
✅ **Changes the table name from `students` to `student_records`.**  

---

### **🔹 Adding a NOT NULL Constraint to an Existing Column**  
```sql
ALTER TABLE students MODIFY name VARCHAR(256) NOT NULL;
```
✅ **Ensures that the `name` column cannot have `NULL` values.**  

---

### **🔹 Adding a PRIMARY KEY Constraint**  
```sql
ALTER TABLE students ADD PRIMARY KEY (rollno);
```
✅ **Sets `rollno` as the primary key, ensuring uniqueness.**  

---

## **📌 Summary of `ALTER TABLE` Uses**  

| **Operation**        | **Command** |
|----------------------|------------|
| Add a Column | `ALTER TABLE students ADD gpa FLOAT;` |
| Remove a Column | `ALTER TABLE students DROP COLUMN age;` |
| Change Data Type | `ALTER TABLE students MODIFY COLUMN gpa DECIMAL(3,2);` |
| Rename a Column | `ALTER TABLE students RENAME COLUMN gpa TO cgpa;` |
| Rename the Table | `ALTER TABLE students RENAME TO student_records;` |
| Add `NOT NULL` Constraint | `ALTER TABLE students MODIFY name VARCHAR(256) NOT NULL;` |
| Add Primary Key | `ALTER TABLE students ADD PRIMARY KEY (rollno);` |

---
