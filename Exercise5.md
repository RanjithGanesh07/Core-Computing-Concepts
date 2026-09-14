# Experiment 5: Implementation of SQL for DDL and DML Commands

```
Name: Ranjith Ganesh B.
Reg No: 212223060222
```

## Aim

To write and execute SQL commands to implement **DDL (Data Definition Language)** and **DML (Data Manipulation Language)** operations on a database and perform various operations such as creating tables, inserting, retrieving, updating, deleting, and querying data.

---

# Algorithm – DDL Commands

1. **Start the program.**
2. Create a database named `COLLEGE`.
3. Select the `COLLEGE` database using the `USE` command.
4. Create the `DEPARTMENT` table with **primary key, unique, and not-null constraints**.
5. Create the `STUDENT` table with **primary key, foreign key, check, unique, and default constraints**.
6. Add a `Phone` column to the `STUDENT` table using `ALTER TABLE`.
7. Add a check constraint to validate the phone number length.
8. Add a check constraint to ensure that `Student_Name` is not empty.
9. Display the structure of the tables using `DESCRIBE`.
10. Rename the `STUDENT` table to `STUDENT_DETAILS`.
11. Remove the `Phone` column using `ALTER TABLE ... DROP COLUMN`.
12. Create the `COURSE` table with appropriate constraints.
13. Remove all records from the `COURSE` table using `TRUNCATE`.
14. Permanently remove the `COURSE` table using `DROP TABLE`.
15. **Stop the program.**

---

# Algorithm – DML Commands

1. **Start the program.**
2. Create a database named `HOSPITAL`.
3. Select the `HOSPITAL` database using the `USE` command.
4. Create the `PATIENT` table with fields for patient ID, name, age, gender, disease, and fees.
5. Insert patient records into the `PATIENT` table using the `INSERT` command.
6. Display all patient records using the `SELECT` command.
7. Retrieve patients whose age is greater than `40` using the `WHERE` clause.
8. Retrieve patients suffering from **Diabetes** using the `WHERE` clause.
9. Increase the fees of all patients by `500` using the `UPDATE` command.
10. Update Anu's disease from **Asthma** to **Allergy** using the `UPDATE` command.
11. Delete patients whose fees are less than `3000` using the `DELETE` command.
12. Display patient records in descending order of fees using `ORDER BY`.
13. Calculate the average patient fees using the `AVG()` function.
14. Find the highest patient fees using the `MAX()` function.
15. **Stop the program.**

---

# Procedure

1. Open any SQL environment such as **MySQL Workbench**.
2. Create a new SQL query.
3. Type or paste the given SQL commands.
4. Execute the DDL commands to create and modify the database and tables.
5. Execute the DML commands to insert records into the `PATIENT` table.
6. Use `SELECT` commands to retrieve and filter records.
7. Use `UPDATE` commands to modify existing records.
8. Use `DELETE` commands to remove records based on the specified condition.
9. Execute aggregate and sorting queries to obtain the required results.
10. Observe the database structure and output of each SQL command.

---

# Program

```sql
-- ============================================
-- DDL COMMANDS
-- ============================================

CREATE DATABASE COLLEGE;

USE COLLEGE;

CREATE TABLE DEPARTMENT (
    Dept_ID INT PRIMARY KEY,
    Dept_Name VARCHAR(30) NOT NULL UNIQUE,
    Location VARCHAR(30)
);

CREATE TABLE STUDENT (
    Student_ID INT PRIMARY KEY,
    Student_Name VARCHAR(50) NOT NULL,
    Email VARCHAR(50) UNIQUE,
    Age INT CHECK (Age >= 17),
    Dept_ID INT,
    Status VARCHAR(10) DEFAULT 'Active',
    FOREIGN KEY (Dept_ID) REFERENCES DEPARTMENT(Dept_ID)
);

ALTER TABLE STUDENT
ADD Phone VARCHAR(15);

ALTER TABLE STUDENT
ADD CONSTRAINT chk_phone
CHECK (CHAR_LENGTH(Phone) BETWEEN 10 AND 15);

ALTER TABLE STUDENT
ADD CONSTRAINT chk_student_name
CHECK (TRIM(Student_Name) <> '');

DESCRIBE DEPARTMENT;

DESCRIBE STUDENT;

RENAME TABLE STUDENT TO STUDENT_DETAILS;

ALTER TABLE STUDENT_DETAILS
DROP COLUMN Phone;

CREATE TABLE COURSE (
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(50) NOT NULL UNIQUE,
    Credits INT CHECK (Credits > 0),
    Dept_ID INT,
    FOREIGN KEY (Dept_ID) REFERENCES DEPARTMENT(Dept_ID)
);

TRUNCATE TABLE COURSE;

DROP TABLE COURSE;


-- ============================================
-- DML COMMANDS
-- ============================================

CREATE DATABASE HOSPITAL;

USE HOSPITAL;

CREATE TABLE PATIENT (
    Patient_ID INT PRIMARY KEY,
    Patient_Name VARCHAR(50),
    Age INT,
    Gender CHAR(1),
    Disease VARCHAR(50),
    Fees INT
);

INSERT INTO PATIENT VALUES
(201, 'Kumar', 45, 'M', 'Diabetes', 5000),
(202, 'Priya', 32, 'F', 'Fever', 2000),
(203, 'Ravi', 60, 'M', 'Heart Disease', 15000),
(204, 'Anu', 28, 'F', 'Asthma', 6000);

SELECT * FROM PATIENT;

SELECT * FROM PATIENT
WHERE Age > 40;

SELECT * FROM PATIENT
WHERE Disease = 'Diabetes';

UPDATE PATIENT
SET Fees = Fees + 500;

UPDATE PATIENT
SET Disease = 'Allergy'
WHERE Patient_Name = 'Anu';

DELETE FROM PATIENT
WHERE Fees < 3000;

SELECT * FROM PATIENT
ORDER BY Fees DESC;

SELECT AVG(Fees) AS Average_Fees
FROM PATIENT;

SELECT MAX(Fees) AS Highest_Fees
FROM PATIENT;
```

---

# Output

## Database: `COLLEGE`

### Department Table Structure

<img width="590" height="176" alt="image" src="https://github.com/user-attachments/assets/7751e658-9b0b-4a09-aae8-ecfc749de770" />


### Student Table Structure

<img width="591" height="238" alt="image" src="https://github.com/user-attachments/assets/3f405249-3601-492b-97a5-2c4740512eed" />


---

## Database: `HOSPITAL`

### Initial Patient Records

<img width="594" height="195" alt="image" src="https://github.com/user-attachments/assets/3e5d1d1c-de5f-42c5-bc4c-c332ca293574" />


<img width="589" height="137" alt="image" src="https://github.com/user-attachments/assets/027371cb-233f-474e-8ba3-93157ea6772a" />

<img width="576" height="135" alt="image" src="https://github.com/user-attachments/assets/535ca1c1-5e99-408a-85ae-fa1ccddfda8b" />

<img width="576" height="108" alt="image" src="https://github.com/user-attachments/assets/0d5215fd-5104-427e-87a7-03bdc32f0bd0" />

<img width="576" height="108" alt="image" src="https://github.com/user-attachments/assets/07c77289-9c52-4f81-ad4a-5986b2ab9db8" />

<img width="570" height="143" alt="image" src="https://github.com/user-attachments/assets/6208b602-9464-4802-bde7-e6341b2d421a" />

---

# Result

Thus, the SQL program to implement **DDL and DML commands** was successfully executed. The database and tables were created and modified using **DDL commands**, while data was successfully **inserted, retrieved, updated, deleted, sorted, and analyzed** using **DML commands**.
