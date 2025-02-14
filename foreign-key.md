

# **🔹 FOREIGN KEY Constraint in SQL**  

A **FOREIGN KEY** is a constraint that establishes a **link** between two tables. It ensures **referential integrity**, meaning that the column referencing another table must contain values that either:  
✅ Match a **primary key value** from the referenced table (parent table).  
✅ Be **NULL**, allowing flexibility in cases where no related record exists.  

---

## **✅ Why Do We Need a FOREIGN KEY?**  

1️⃣ **Reduces Data Redundancy** – Instead of storing all details in one table, we create separate tables and link them using foreign keys.  
2️⃣ **Ensures Consistency** – Prevents invalid references (e.g., a student cannot enroll in a non-existent course).  
3️⃣ **Supports Database Normalization** – Breaks large tables into smaller, structured ones.  
4️⃣ **Allows Flexibility** – If a foreign key allows `NULL`, it does not force an immediate relationship.  

---

## **✅ Defining a FOREIGN KEY While Creating a Table**  

📌 **Example 1: Without Constraint Name**  
```sql
CREATE TABLE Students (
    StudentID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200),  
    LastName VARCHAR(200),  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    CourseID INTEGER FOREIGN KEY REFERENCES Course(CourseID)  
);
```
✅ Here, `CourseID` in `Students` references `CourseID` in `Course`. A student **can be linked** to an existing course but is not required to be.  

📌 **Example 2: With Constraint Name**  
```sql
CREATE TABLE Students (
    StudentID INTEGER PRIMARY KEY,  
    FirstName VARCHAR(200),  
    LastName VARCHAR(200),  
    DateOfBirth DATE,  
    Gender CHAR(1),  
    CourseID INTEGER,  
    CONSTRAINT FK_Students FOREIGN KEY (CourseID) REFERENCES Course(CourseID)  
);
```
✅ Using **constraint names** (`FK_Students`) makes it **easier to modify or drop** later.  

---

## **✅ Inserting Data Into Tables**  

📌 **First, insert data into the parent table (`Course`)**  
```sql
INSERT INTO Course  
VALUES  
(401, 'Computer Science', 'Radha'),  
(402, 'Electronics and Communication', 'Meera'),  
(403, 'Information Technology', 'Geetha'),  
(404, 'Electronics and Instrumentation', 'Sivakumar');
```

📌 **Now, insert data into the child table (`Students`)**  
```sql
INSERT INTO Students  
VALUES (1001, 'Aishwarya', 'Jayaram', '2005-04-24', 'F', 401);
```
✅ The `CourseID` **can be NULL or match an existing `CourseID` in the `Course` table**.  

📌 **What happens if we insert a `NULL` CourseID?**  
```sql
INSERT INTO Students  
VALUES (1002, 'Anand', 'Venkat', '2005-05-22', 'M', NULL);
```
✅ This works because `NULL` means "no course assigned yet."  

📌 **What happens if we insert an invalid `CourseID`?**  
```sql
INSERT INTO Students  
VALUES (1003, 'Bharath', 'Rajan', '2004-12-15', 'M', 405);
```
⛔ **Error:** `CourseID = 405` does not exist in `Course`, so the insertion fails.  

---

## **✅ Adding a FOREIGN KEY to an Existing Table**  

📌 **Without Constraint Name:**  
```sql
ALTER TABLE Students  
ADD FOREIGN KEY (CourseID) REFERENCES Course(CourseID);
```
📌 **With Constraint Name:**  
```sql
ALTER TABLE Students  
ADD CONSTRAINT FK_Students FOREIGN KEY (CourseID) REFERENCES Course(CourseID);
```
✅ Naming the constraint (`FK_Students`) makes **future modifications easier**.  

---

## **✅ Deleting a FOREIGN KEY Constraint**  

📌 **To remove the foreign key constraint:**  
```sql
ALTER TABLE Students  
DROP CONSTRAINT FK_Students;
```
✅ Now, `CourseID` in `Students` **no longer has a restriction** and can contain any value.  

---

## **✅ Deleting Data When a FOREIGN KEY Exists**  

📌 **Trying to delete a referenced row:**  
```sql
DELETE FROM Course WHERE CourseID = 402;
```
⛔ **Error:** Cannot delete `CourseID = 402` **because it is referenced in the `Students` table**.  

📌 **Fix: Delete referenced records first, then delete the parent row:**  
```sql
DELETE FROM Students WHERE CourseID = 402;
DELETE FROM Course WHERE CourseID = 402;
```
✅ Now, `CourseID = 402` is removed from both tables.  

---

## **✅ Key Takeaways**  
🔹 **FOREIGN KEYs reduce redundancy** and improve database structure.  
🔹 A foreign key can be **NULL or reference an existing record**.  
🔹 **Ensures valid relationships** but allows flexibility.  
🔹 Prevents accidental deletions in the referenced table.  

Would you like additional real-world use cases for **FOREIGN KEYs** in companies? 🚀
