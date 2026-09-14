# Experiment 6: Implementation of SQL for TCL Commands

```
Name: Ranjith Ganesh B.
Reg No: 212223060222
```

## Aim

To implement **Transaction Control Language (TCL)** commands such as `COMMIT`, `ROLLBACK`, `SAVEPOINT`, and `ROLLBACK TO SAVEPOINT` using SQL and verify transaction operations.

---

# Algorithm

1. **Start the program.**
2. Create a database named `COLLEGE`.
3. Select the `COLLEGE` database.
4. Create the `STUDENT` table with Student ID, Name, Department, and Marks.
5. Insert student records into the `STUDENT` table.
6. Use `COMMIT` to permanently save the inserted records.
7. Start a new transaction using `START TRANSACTION`.
8. Create a savepoint named `sp1`.
9. Insert a new student record.
10. Create another savepoint named `sp2`.
11. Update the marks of an existing student.
12. Display the records to verify the changes.
13. Use `ROLLBACK TO SAVEPOINT sp2` to undo changes made after `sp2`.
14. Display the records and verify the rollback.
15. Use `ROLLBACK TO SAVEPOINT sp1` to undo changes made after `sp1`.
16. Display the records and verify the rollback.
17. Use `COMMIT` to permanently save the remaining transaction changes.
18. Display the final contents of the `STUDENT` table.
19. **Stop the program.**

---

# Procedure

1. Open any SQL environment such as **MySQL Workbench**.
2. Create a new SQL query.
3. Type or paste the given TCL commands.
4. Execute the commands to create the `COLLEGE` database and select it.
5. Create the `STUDENT` table with the required fields.
6. Insert the initial student records into the table.
7. Execute the `COMMIT` command to permanently save the inserted records.
8. Start a new transaction using `START TRANSACTION`.
9. Create a savepoint using `SAVEPOINT sp1`.
10. Insert a new student record and create another savepoint using `SAVEPOINT sp2`.
11. Update the marks of an existing student and display the table contents.
12. Execute `ROLLBACK TO SAVEPOINT sp2` and verify that the update is undone.
13. Execute `ROLLBACK TO SAVEPOINT sp1` and verify that the insertion after `sp1` is undone.
14. Execute `COMMIT` to save the remaining transaction.
15. Display the final contents of the `STUDENT` table using `SELECT`.
16. Observe and verify the effects of the TCL commands.

---

# Program

```sql id="q1y87n"
CREATE DATABASE COLLEGE;

USE COLLEGE;

CREATE TABLE STUDENT (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Department VARCHAR(30),
    Marks INT
);

INSERT INTO STUDENT VALUES (101, 'Arun', 'CSE', 85);
INSERT INTO STUDENT VALUES (102, 'Bala', 'ECE', 78);

COMMIT;

START TRANSACTION;

SAVEPOINT sp1;

INSERT INTO STUDENT VALUES (103, 'Chris', 'EEE', 90);

SAVEPOINT sp2;

UPDATE STUDENT
SET Marks = 95
WHERE Student_ID = 101;

SELECT * FROM STUDENT;

ROLLBACK TO SAVEPOINT sp2;

SELECT * FROM STUDENT;

ROLLBACK TO SAVEPOINT sp1;

SELECT * FROM STUDENT;

COMMIT;

SELECT * FROM STUDENT;
```

---

# Output

## After Initial Commit
<img width="576" height="133" alt="image" src="https://github.com/user-attachments/assets/c514dbc8-691e-4f81-91d9-f3e0198216f9" />



---

## After Savepoint `sp1`
<img width="576" height="133" alt="image" src="https://github.com/user-attachments/assets/68530de2-6139-4a0b-8176-5158151a58cf" />



---

## After Savepoint `sp2`

<img width="575" height="146" alt="image" src="https://github.com/user-attachments/assets/1288f0f1-5fc7-4714-942b-5f4b74615947" />


---

## After Updation

<img width="575" height="163" alt="image" src="https://github.com/user-attachments/assets/bd35f104-3f6d-4936-a177-3f9fac781481" />


---

## Rollback to `sp2`

<img width="575" height="163" alt="image" src="https://github.com/user-attachments/assets/6594ccc7-f1bd-44b2-810a-b1582f76517e" />


---

## Rollback to `sp1`

<img width="575" height="146" alt="image" src="https://github.com/user-attachments/assets/282aeff7-d763-45a9-9cc0-7461e51a09bd" />

---

## After Final Commit
<img width="571" height="145" alt="image" src="https://github.com/user-attachments/assets/b9b5fbc3-9b6d-4637-a0c5-a67e4e97393a" />



---

# Result

Thus, the TCL commands **`COMMIT`, `ROLLBACK`, `SAVEPOINT`, and `ROLLBACK TO SAVEPOINT`** were successfully implemented, and the transaction operations were verified.
