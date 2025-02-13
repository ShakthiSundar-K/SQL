

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

## **7️⃣ DELETE (Removing Specific Rows from a Table)**  
### 🔹 **Purpose**  
The `DELETE` statement removes specific rows from a table **without deleting the table structure**.  

### 🔹 **Syntax**  
```sql
DELETE FROM table_name WHERE condition;
```

### 🔹 **Example**  
```sql
DELETE FROM students WHERE rollno = 1003;
```
✅ **Removes only the student with `rollno = 1003` from the table.**  

### 🔹 **Need & When to Use?**  
- Use when **removing specific rows** while keeping the table intact.  
- Always include a `WHERE` condition to avoid deleting **all rows**.  
- If you accidentally run `DELETE FROM students;` without `WHERE`, all rows will be removed!  

---

## **8️⃣ TRUNCATE (Removing All Rows from a Table Quickly)**  
### 🔹 **Purpose**  
The `TRUNCATE TABLE` command removes **all rows from a table** but **preserves its structure**.  

### 🔹 **Syntax**  
```sql
TRUNCATE TABLE table_name;
```

### 🔹 **Example**  
```sql
TRUNCATE TABLE students;
```
✅ **Deletes all records from the `students` table but keeps the table structure intact.**  

### 🔹 **Need & When to Use?**  
- Use when you want to **delete all data quickly** without logging individual row deletions.  
- Faster than `DELETE FROM students;` because it does not log each row deletion.  
- Cannot use `WHERE` with `TRUNCATE`.  

**🛑 Difference Between DELETE and TRUNCATE:**  
| Feature  | DELETE  | TRUNCATE  |
|----------|--------|----------|
| Removes specific rows? | ✅ Yes (with `WHERE`) | ❌ No (removes all rows) |
| Logs individual row deletions? | ✅ Yes | ❌ No |
| Can be rolled back? | ✅ Yes (if inside a transaction) | ❌ No |
| Resets auto-increment? | ❌ No | ✅ Yes |

---

## **9️⃣ DROP TABLE (Completely Deleting a Table)**  
### 🔹 **Purpose**  
The `DROP TABLE` command **permanently deletes** a table along with its structure.  

### 🔹 **Syntax**  
```sql
DROP TABLE table_name;
```

### 🔹 **Example**  
```sql
DROP TABLE students;
```
✅ **Deletes the `students` table completely, along with all its data and structure.**  

### 🔹 **Need & When to Use?**  
- Use when you no longer need a table **at all**.  
- **⚠ Cannot be undone unless a backup exists.**  
- After dropping, you must recreate the table if needed.  

---

## **📌 Summary of Data Deletion Commands**  

| **Command**   | **Deletes Data?** | **Deletes Table Structure?** | **Can Be Rolled Back?** |
|--------------|----------------|--------------------|------------------|
| `DELETE`     | ✅ Specific rows | ❌ No | ✅ Yes (if inside a transaction) |
| `TRUNCATE`   | ✅ All rows | ❌ No | ❌ No |
| `DROP TABLE` | ✅ All rows | ✅ Yes | ❌ No |

---

