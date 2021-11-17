### Create a table in SQL Student(rollno, name, branch, semester, section)
```
SQL> CREATE TABLE Student_Naman(rollno INT PRIMARY KEY, name VARCHAR(25), branch VARCHAR(4), semester INT, section VARCHAR(2));

Table created.

SQL> desc student_naman;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 ROLLNO                                    NOT NULL NUMBER(38)
 NAME                                               VARCHAR2(25)
 BRANCH                                             VARCHAR2(4)
 SEMESTER                                           NUMBER(38)
 SECTION                                            VARCHAR2(2)

SQL> INSERT into Student_Naman VALUES(&rollno, '&name', '&branch', &semester, '&section');
Enter value for rollno: 169
Enter value for name: Naman Baranwal
Enter value for branch: CSE
Enter value for semester: 5
Enter value for section: C
old   1: INSERT into Student_Naman VALUES(&rollno, '&name', '&branch', &semester, '&section')
new   1: INSERT into Student_Naman VALUES(169, 'Naman Baranwal', 'CSE', 5, 'C')

1 row created.

SQL> INSERT into Student_Naman VALUES(&rollno, '&name', '&branch', &semester, '&section');
Enter value for rollno: 219
Enter value for name: Raunaq Soneja
Enter value for branch: CSE
Enter value for semester: 5
Enter value for section: C
old   1: INSERT into Student_Naman VALUES(&rollno, '&name', '&branch', &semester, '&section')
new   1: INSERT into Student_Naman VALUES(219, 'Raunaq Soneja', 'CSE', 5, 'C')

1 row created.

SQL> SELECT * FROM Student_naman;

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       169 Naman Baranwal            CSE           5 C
       219 Raunaq Soneja             CSE           5 C
       178 Nilesh Kumar Singh        CSE           5 C
        25 Barry                     CSE           2 A
         1 Hunter                    ECE           3 B
         
```

### Find the name of the students belong to CSE.
```
SQL> SELECT * FROM Student_naman where BRANCH in ('CSE', 'ECE');

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       169 Naman Baranwal            CSE           5 C
       219 Raunaq Soneja             CSE           5 C
       178 Nilesh Kumar Singh        CSE           5 C
        25 Barry                     CSE           2 A
         1 Hunter                    ECE           3 B

SQL> SELECT * FROM Student_naman where BRANCH = any('CSE', 'ECE');

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       169 Naman Baranwal            CSE           5 C
       219 Raunaq Soneja             CSE           5 C
       178 Nilesh Kumar Singh        CSE           5 C
        25 Barry                     CSE           2 A
         1 Hunter                    ECE           3 B

SQL> SELECT * FROM Student_naman where BRANCH = all('CSE', 'ECE');

no rows selected

### List all students whose rollno is in range 150 and 200
SQL> SELECT * FROM Student_Naman where rollno between 150 and 200;

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       169 Naman Baranwal            CSE           5 C
       178 Nilesh Kumar Singh        CSE           5 C
```
### Use Exists
```
SQL> SELECT * FROM Student_Naman WHERE EXISTS (SELECT * FROM STUDENT_nAMAN WHERE name='Naman Baranwal');

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       169 Naman Baranwal            CSE           5 C
       219 Raunaq Soneja             CSE           5 C
       178 Nilesh Kumar Singh        CSE           5 C
        25 Barry                     EN            2 A
         1 Hunter                    ECE           3 B
```
### Find the name of students of the department headed by Dr. C. S. Yadav.
```
SQL> select * from student_naman WHERE EXISTS (Select * from department where student_naman.branch = department.name and hod='DR. CS Yadav');

    ROLLNO NAME                      BRAN   SEMESTER SE
---------- ------------------------- ---- ---------- --
       178 Nilesh Kumar Singh        CS            5 C
       219 Raunaq Soneja             CS            5 C
       169 Naman Baranwal            CS            5 C

SQL> select * from student_naman s join department d on s.branch=d.name where hod = 'DR. CS Yadav';

ROLLNO NAME                      BRAN   SEMESTER SE    DNUMBER 	NAME 			HOD
---------- ------------------------- ---- ---------- --         ----------         ----------    -------------------------
       169 Naman Baranwal            CS            5 C           5 		CS 		DR. CS Yadav

       219 Raunaq Soneja             CS            5 C           5 			CS		DR. CS Yadav

       178 Nilesh Kumar Singh        CS            5 C           5 		CS		DR. CS Yadav
```
### USAGE OF UNION, INTERSECT and MINUS
```
SQL> CREATE TABLE account(account_number INT PRIMARY KEY, branch_name VARCHAR(25), balance NUMBER);

Table created.

SQL> CREATE TABLE loan(loan_number INT PRIMARY KEY, branch_name VARCHAR(25), amount NUMBER);

Table created.

SQL> INSERT INTO account VALUES(&number, '&branch', &balance);
Enter value for number: 1
Enter value for branch: noida
Enter value for balance: 50000
old   1: INSERT INTO account VALUES(&number, '&branch', &balance)
new   1: INSERT INTO account VALUES(1, 'noida', 50000)

1 row created.

SQL> INSERT INTO account VALUES(&number, '&branch', &balance);
Enter value for number: 2
Enter value for branch: delhi
Enter value for balance: 400000
old   1: INSERT INTO account VALUES(&number, '&branch', &balance)
new   1: INSERT INTO account VALUES(2, 'delhi', 400000)

1 row created.

SQL> INSERT INTO loan VALUES(&number, '&branch', &amount);
Enter value for number: 1
Enter value for branch: noida
Enter value for amount: 2000
old   1: INSERT INTO loan VALUES(&number, '&branch', &amount)
new   1: INSERT INTO loan VALUES(1, 'noida', 2000)

1 row created.

SQL> INSERT INTO loan VALUES(&number, '&branch', &amount);
Enter value for number: 2
Enter value for branch: lmp
Enter value for amount: 4000
old   1: INSERT INTO loan VALUES(&number, '&branch', &amount)
new   1: INSERT INTO loan VALUES(2, 'lmp', 4000)

1 row created.
```
