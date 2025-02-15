# Types of SQL Commands

In SQL, commands are categorized based on their functionality. The five main types of SQL commands are:  

1. **DDL (Data Definition Language)** – Defines and manages database structures.  
2. **DML (Data Manipulation Language)** – Modifies and manipulates data.  
3. **DCL (Data Control Language)** – Manages user permissions.  
4. **TCL (Transaction Control Language)** – Manages transactions in the database.  
5. **DQL (Data Query Language)** – Retrieves data from the database.  

---

### 1️⃣ **DDL (Data Definition Language)**  
Used to define and manage database objects like tables, indexes, and schemas.  

🔹 **Commands in DDL:**  
- `CREATE` → Creates database objects (tables, views, indexes, etc.).  
- `ALTER` → Modifies existing database structures (adds/removes columns, constraints, etc.).  
- `DROP` → Deletes database objects (tables, views, etc.).  
- `TRUNCATE` → Removes all data from a table but keeps its structure.  
- `RENAME` → Changes the name of a table or column.  
- `COMMENT` → Adds comments to database objects for documentation.  

📌 **When to use?**  
- Use `CREATE` when setting up a new database or table.  
- Use `ALTER` when you need to modify the structure of a table (e.g., add a new column).  
- Use `DROP` when permanently deleting an object from the database.  
- Use `TRUNCATE` when you want to remove all rows from a table efficiently.
  

### 🔥 **Difference Between `DROP` and `TRUNCATE`**  

| Feature        | `DROP` | `TRUNCATE` |
|--------------|--------|-----------|
| **What it does?** | Deletes the table and its structure completely. | Removes all rows but keeps the table structure. |
| **Affects Table Structure?** | Yes, the table is permanently deleted. | No, the table remains, but it becomes empty. |
| **Affects Indexes & Constraints?** | Yes, all associated indexes, constraints, and permissions are removed. | No, indexes and constraints remain. |
| **Can be Rolled Back?** | ❌ No, once dropped, it’s gone forever. | ✅ Yes, in some databases (if inside a transaction). |
| **Performance Impact?** | More expensive, as it requires updating system catalogs. | Faster, as it doesn’t log row deletions individually. |
| **Auto-Increment Reset?** | Yes, dropping and recreating the table resets `AUTO_INCREMENT`. | Yes, `AUTO_INCREMENT` is reset. |

---

### ✅ **When to Use?**
- Use `DROP` when you **no longer need** the table at all.  
- Use `TRUNCATE` when you **want to clear all data** but keep the table for future use.  

---

### 🚀 **Example Usage**  

#### 🔴 `DROP` Example (Deletes Table Permanently)
```sql
DROP TABLE students;
```
⚠ **After this, the `students` table is gone forever!**

---

#### 🟢 `TRUNCATE` Example (Clears Data but Keeps Table)
```sql
TRUNCATE TABLE students;
```
✅ **The `students` table remains, but it’s now empty.**  



---

### 2️⃣ **DML (Data Manipulation Language)**  
Used to manipulate data within database tables.  

🔹 **Commands in DML:**  
- `INSERT` → Adds new records to a table.  
- `UPDATE` → Modifies existing records in a table.  
- `DELETE` → Removes specific records from a table.  
- `MERGE` → Merges records from two tables based on conditions.  

📌 **When to use?**  
- Use `INSERT` to add new data into a table.  
- Use `UPDATE` when modifying existing records.  
- Use `DELETE` to remove specific records from a table.  
- Use `MERGE` when synchronizing data between two tables.  

---

### 3️⃣ **DCL (Data Control Language)**  
Used to control access and permissions in the database.  

🔹 **Commands in DCL:**  
- `GRANT` → Gives privileges to users.  
- `REVOKE` → Removes privileges from users.  

📌 **When to use?**  
- Use `GRANT` to provide specific access (e.g., read, write) to users.  
- Use `REVOKE` to remove granted permissions when no longer needed.  

---

### 4️⃣ **TCL (Transaction Control Language)**  
Used to manage transactions in a database (ensuring ACID properties).  

🔹 **Commands in TCL:**  
- `COMMIT` → Saves all changes made in the current transaction.  
- `ROLLBACK` → Undoes all changes in the current transaction.  
- `SAVEPOINT` → Creates a temporary point to which a transaction can be rolled back.  
- `SET TRANSACTION` → Defines properties of a transaction (e.g., isolation levels).  

📌 **When to use?**  
- Use `COMMIT` after executing a set of SQL operations that you want to save permanently.  
- Use `ROLLBACK` to undo changes if something goes wrong.  
- Use `SAVEPOINT` to create a rollback checkpoint within a transaction.  

---

### 5️⃣ **DQL (Data Query Language)**  
Used to retrieve data from a database.  

🔹 **Commands in DQL:**  
- `SELECT` → Retrieves data from one or more tables.  

📌 **When to use?**  
- Use `SELECT` whenever you need to fetch data from the database.  

---

