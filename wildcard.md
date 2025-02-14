

# **🔍 Using `LIKE` for Pattern Matching in SQL**  

The `LIKE` operator in SQL is used for **pattern-based searching** within text fields. It allows the use of **wildcards** to match specific patterns in string-based columns.  

## **🛠 Wildcards Used in `LIKE`**  
| Wildcard | Meaning |
|----------|---------|
| `%` | Matches **0 or more characters** |
| `_` | Matches **exactly 1 character** |
| `[abc]` | Matches **one character from the given set** (`a`, `b`, or `c`) |
| `[a-z]` | Matches **one character within the range** (`a` to `z`) |
| `[^a]` | Matches **any character except `a`** |

---

## **🔹 Real-World Use Cases in Companies**  

### ✅ **1. E-commerce (Search Functionality & Product Filtering)**
🔹 When users search for a product, the backend can use `LIKE` to find similar items.  

📌 **Example:** A user searches for "Nike Shoes." The system can retrieve all variations (e.g., "Nike Air Max," "Nike Zoom") using:  
```sql
SELECT * FROM Products WHERE ProductName LIKE '%Nike%Shoes%';
```
🔹 Similarly, filtering products based on size or category can be done with:  
```sql
SELECT * FROM Products WHERE Category LIKE '%Clothing%' AND Size LIKE 'M%';
```

---

### ✅ **2. CRM & Customer Management (Finding Customers with Similar Names)**
🔹 Customer support teams often **search for users by name** (even if they don’t remember the full name).  

📌 **Example:** Searching for customers with names starting with "Rob":  
```sql
SELECT * FROM Customers WHERE FirstName LIKE 'Rob%';
```
🔹 If a user enters **partial details**, the system can retrieve close matches:  
```sql
SELECT * FROM Customers WHERE Email LIKE '%@gmail.com';
```
_(Finds all customers with Gmail accounts.)_

---

### ✅ **3. Banking & FinTech (Filtering Transactions & Fraud Detection)**
🔹 Banks use `LIKE` to **identify transactions with specific descriptions or patterns**.  

📌 **Example:** Find transactions related to "Amazon":  
```sql
SELECT * FROM Transactions WHERE Description LIKE '%Amazon%';
```
🔹 Detect **suspicious transaction IDs** that start with a certain prefix (e.g., fraud patterns):  
```sql
SELECT * FROM Transactions WHERE TransactionID LIKE 'FRD%';
```

---

### ✅ **4. Healthcare (Finding Patient Records & Diagnoses)**
🔹 Hospitals use `LIKE` to **search for patient records by symptoms or conditions**.  

📌 **Example:** Find patients diagnosed with diabetes:  
```sql
SELECT * FROM Patients WHERE Diagnosis LIKE '%diabetes%';
```
🔹 Searching for patient addresses based on street names:  
```sql
SELECT * FROM Patients WHERE Address LIKE '1234%St.';
```

---

### ✅ **5. Cybersecurity & User Authentication (Detecting Invalid Logins)**
🔹 Security teams use `LIKE` to **detect login attempts from suspicious locations**.  

📌 **Example:** Identify failed login attempts from an IP address range:  
```sql
SELECT * FROM LoginAttempts WHERE IPAddress LIKE '192.168.1.%';
```
🔹 Detect **usernames with special characters** (potential bot accounts):  
```sql
SELECT * FROM Users WHERE Username LIKE '%[^a-zA-Z0-9]%';
```

---

## **🧩 Try These! SQL Challenge Questions**  

### **🔹 Question 1: Find Addresses with a Specific Format**  
💡 **Find all addresses where:**  
✅ The **first four characters of AddressLine1** must be **numbers**.  
✅ The **address must end with `'St.'`**.  

👨‍💻 **Try running this query:**  
```sql
SELECT * FROM Person.Address 
WHERE AddressLine1 LIKE '[0-9][0-9][0-9][0-9]%St.';
```

---

### **🔹 Question 2: Find Addresses with Multiple Conditions**  
💡 **Retrieve all addresses where:**  
✅ `AddressLine1` should **not start with a number**.  
✅ `PostalCode` should be a **4-digit number starting with 4**.  
✅ The **second character of the city name must be `o`**.  

👨‍💻 **Try running this query:**  
```sql
SELECT * FROM Person.Address 
WHERE AddressLine1 LIKE '[^0-9]%' 
AND PostalCode LIKE '4[0-9][0-9][0-9]' 
AND City LIKE '_o%';
```

---

## **✨ Why Try These Queries?**  
✅ Helps you **master pattern matching** with `LIKE`.  
✅ Shows **real-world use cases** across industries.  
✅ Encourages **hands-on SQL experimentation**.  

💡 **Try modifying the queries with different conditions and see the results!** 🚀  

---

