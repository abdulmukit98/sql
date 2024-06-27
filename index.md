---
title: Index 
layout: template
filename: index
--- 

## Basic SQL Syntax
#### DB Creation

```sql
show databases;
create database mydb;
use mydb;

drop database mydb;
show databases;
show tables;
```

#### Create Table
```sql
create table student(
    student_id int,
    name varchar(20),
    major varchar(20),
    primary key (student_id)
);
show tables;
drop table student;


create table student(
    student_id int,
    name varchar(20) not null,       
    major varchar(20) unique,
    primary key (student_id)
);

```

- **Inserting Data**

```sql
    insert into student values(1 , 'Jack', 'Biology');
    insert into student values(2, 'Kate', 'Sociology');
    insert into student values(3, 'Clair', "Science");
    select * from student;

```

- **Create Table With Default Values**

```sql
    create table student(
        student_id int,
        name varchar(20) not null,
        major varchar(20) default 'undecided',
        primary key(student_id)
    );
    show tables;
    
    // no major 
    insert into student (student_id, name) values(4, 'Perry');
    select * from student;

```

#### Auto Increment Primary key

```sql

    create table student(
        student_id int auto_increment, 
        name varchar(20) not null,
        major varchar(20) default 'undecided',
        primary key(student_id)
    );
    
    insert into student (name, major) values('Perry', "Sociology");
    insert into student (name, major) values('Kate', "CS");
    insert into student (name, major) values('Lorem', "EEE");
    select * from student;

```

#### Update a column value

```sql
    update student 
    set major='Bio' where major = 'Biology';
    select * from student;

    update student 
    set major='Biochemestry'
    where major = 'Bio' or major = "Chemistry";
    
    update student 
    set name = "Tom", major = "Philosophy"
    where student_id = 1;

```

#### Delete Queries
```sql
    delete from student 
    where student_id = 3;

    // delete everything
    delete from student;

```
