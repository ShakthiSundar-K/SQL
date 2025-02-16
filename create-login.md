
### **🔹 Steps to Create a Login and User in SQL Server**
1. **Create a login** at the server level.  
2. **Create a database user** mapped to that login.  
3. **Grant permissions** to the user on specific tables.

---

### ✅ **Example: Creating a Login and User with Proper Naming**
```sql
-- Step 1: Create a login at the SQL Server level
CREATE LOGIN HR_Login WITH PASSWORD = 'Secure@123';

-- Step 2: Create a user inside the database for the login
USE HR_Database; -- Switch to the correct database
CREATE USER HR_User FOR LOGIN HR_Login;

-- Step 3: Grant SELECT permission on a specific table
GRANT SELECT ON employee_details TO HR_User;
```

---

### **🔹 Explanation**
✔ **`HR_Login`** → Login that allows authentication at the server level.  
✔ **`HR_User`** → A database user linked to the login.  
✔ **`GRANT SELECT ON employee_details`** → Gives read access to `employee_details`.  

---

### 🔥 **Best Practices**
✅ Use **meaningful names** (e.g., `HR_Login` for HR department).  
✅ Use **strong passwords** (`Secure@123` is just an example).  
✅ Assign only **necessary permissions** (Principle of Least Privilege).  

---

### **🔹 Common Variations**
1️⃣ **Granting access to all tables in a database:**  
```sql
GRANT SELECT ON SCHEMA::dbo TO HR_User;
```
*(Gives `HR_User` read access to all tables in the `dbo` schema.)*  

2️⃣ **Giving full control over a table:**  
```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON employee_details TO HR_User;
```



