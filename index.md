---
title: Index 
layout: template
filename: index
--- 

### DB Creation

```
show databases;
create database mydb;
use mydb;

drop database mydb;
show databases;
show tables;
```

### Create Table
```
create table student(
  	student_id int,
    name varchar(20),
    major varchar(20),
    primary key (student_id)
);
show tables;
```

- Inserting Data
```
    insert into student values(1 , 'Jack', 'Biology');
    insert into student values(2, 'Kate', 'Sociology');
    insert into student values(3, 'Clair', "Science");
    select * from student;
```
