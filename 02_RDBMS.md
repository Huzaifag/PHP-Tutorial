## Using RDBMS & SQL With php
**Introduction**
A Relational Database Management System (RDBMS) is a structured data management system that organizes information into tables, each composed of rows and columns. In this model, rows represent individual records, while columns denote specific attributes or fields. Key concepts in RDBMS include primary and foreign keys, ensuring unique identification and relationships between tables. Normalization, a process of minimizing redundancy and enhancing data integrity, is employed to structure databases efficiently. ACID properties (Atomicity, Consistency, Isolation, Durability) govern transaction reliability. Popular RDBMS examples encompass MySQL, Oracle Database, Microsoft SQL Server, and PostgreSQL, each serving diverse applications with features such as scalability, robustness, and standards compliance. RDBMS is fundamental in providing a systematic framework for storing, managing, and retrieving structured data across various industries and applications.

**What is Database**
A database is a kind of storage usually implemented inside a server for small-scale applications and outside the server if the data is huge or complex in size.

In website development, most of the data is fetched and stored in the database at the server-side.

There are many types of database systems that have been developed since now. The choice among different database systems depends upon the nature of the application. Here in this lesson and for the rest of this course, we will be following MYSQL. We will discuss it in the next sections.

**Introduction to SQL**
SQL is a standard language (Structured Query Language) for storing, retrieving, and manipulating data in the database.

There are some terms that need to be defined related to Database tables. Consider the following table for the next terms.

```
----------------------------------------------

| ID | NAME     | AGE | ADDRESS   | SALARY   |

----------------------------------------------

|  1 | Jawad   |  22 | Dubai |  2400.00 |

|  2 | Harris   |  25 | India   |  1600.00 |

|  3 | Ahmad  |  24   | Pakistan  |  2300.00 |

|  4 | Sumaira |  32 | Canada    |  6100.00 |

|  5 | Ali   |  37   | USA    |  8200.00 |

|  6 | Usama    |  24 | UAE    |  3500.00 |

|  7 | Muffy    |  31 | Canada    | 2000.00 |

-----------------------------------------------
```
**What is a table?**
A table is a structured form of data. The data is stored in the form of database objects called tables. The basic building blocks of a table are rows and columns. Refer to the table above. Suppose the name of the above table is Employees.
**What is a field?**
A table is divided into smaller entities called fields. In the above employees' table, ID, NAME, AGE, ADDRESS, and SALARY are its fields.

What is a Row or Record?

Record is also known as a row of data. For example, in the Employees table above, there are 7 rows of data refer to as 7 records alternatively.
```
| 7 | Muffy    | 31 | Indore    | 2000.00 |
```
**What is a column?**
Each vertical entity of the database table is named a column. In the Employees table, we have 5 columns.
```
| Dubai    | 
| India    | 
| Pakistan | 
| Canada   | 
| USA      |
| UAE      | 
| Canada   |
```

**Why prefer Tables over File system to store data**
Data can also be stored in the files. But there are many complexities that arise with the passage of time, so computer developers have to introduce and prefer DB over file systems.

- The file system does not support quick searching of data.
- The file system is not efficient for millions of records.
- The file system cannot develop relationship between data.
- Data cannot be filtered from the files.
 
