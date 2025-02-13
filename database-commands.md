
# **Database Commands: Creating, Using, and Dropping a Database**  

## **1️⃣ CREATE DATABASE**  
### 🔹 **Purpose**  
The `CREATE DATABASE` command is used to create a new database in the SQL server.  

### 🔹 **Syntax**  
```sql
CREATE DATABASE database_name;
```
### 🔹 **Example**  
```sql
CREATE DATABASE student;
```
### 🔹 **Need & When to Use?**  
- Used when setting up a new project or system that requires a separate database.  
- Ensures data is stored in an organized manner.  
- Required before creating tables and inserting records.  

---

## **2️⃣ USE DATABASE**  
### 🔹 **Purpose**  
The `USE` command selects a specific database to work on.  

### 🔹 **Syntax**  
```sql
USE database_name;
```
### 🔹 **Example**  
```sql
USE student;
```
### 🔹 **Need & When to Use?**  
- Required before executing any queries on a specific database.  
- Ensures that subsequent operations apply to the correct database.  

---

## **3️⃣ DROP DATABASE**  
### 🔹 **Purpose**  
The `DROP DATABASE` command permanently deletes a database along with all its tables and data.  

### 🔹 **Syntax**  
```sql
DROP DATABASE database_name;
```
### 🔹 **Example**  
```sql
DROP DATABASE student;
```
### 🔹 **Need & When to Use?**  
- Use when a database is no longer needed.  
- Removes all data permanently (cannot be undone).  
- Frees up storage space.  

### ⚠ **Caution**  
- Once a database is dropped, **all data inside it is lost forever**.  
- Ensure you have backups before executing this command.  

---

