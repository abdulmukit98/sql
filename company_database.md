---
title: Conpany Database 
layout: template
filename: company_database
---

## Company Database Table
**Employee Table**

| emp_id | first_name | last_name | birth_date | sex |  salary  | supervisor_id | branch_id |
|:------:|:----------:|:---------:|:----------:|:---:|:--------:|:-------------:|:---------:|
| 100    |  David     | wallace   | 1967-11-17 | M   | 250.,000 |      NULL     |      1    |
| 101    |  Jan       | Levinson  | 1961-05-11 | F   | 110.,000 |      100      |      1    |

<br><br>
**Branch Table**

| branch_id | branch_name | manager_id | manager_start_date |
|:---------:|:-----------:|:----------:|:------------------:|
| 1         | corporate   | 100        |  2006-02-09        |
| 2         | scranton    | 102        |  1992-04-06        |
| 3         | stampford   | 106        |  1998-02-13        |

<br><br>
**Client Table**

| client_id | client_name        | branch_id |
|:---------:|:------------------:|:---------:|
| 400       | Dunmore Highschool | 2         |
| 401       | Lackawana Coutry   | 2         |
| 402       | FedEX              |  3        |
| 403       | Jogn Dally law llc |  3        |

<br><br>
**Works_With Table**

| emp_id | client_id | total_sales |
|:------:|:---------:|:-----------:|
| 105    | 400       | 55000       |
| 102    | 401       | 267000      |
| 108    | 402       | 22500       |
| 107    | 403       |  5000       |

<br><br>
**Branch Supplier Table**

| branch_id | supplier_name | supply_type      |
|:---------:|:-------------:|:----------------:|
| 2         | Hammer Mill   | Paper            |
| 2         | Uni Bann      | Writing Utensils |
| 3         | Patriot Paper | Paper            |

<br><br>
### Creating Tables
**Employee Table**
```sql
create table employee (
    emp_id int primary key,
    first_name varchar(40),
    last_name varchar(40),
    birth_date date,
    sex varchar(1),
    salary int,
    super_id int, 
    branch_id int
  );

-- super_id and branch_id are foreign key
-- but we can't define them now since the
-- the corresponding table has not been created yet.

```
<br>

Create **Branch_table** with **manager_id foreign key** from **employee table**

```sql
create table branch(
    branch_id int primary key,
    branch_name varchar(40),
    mgr_id int,
    mgr_start_date date,
    foreign key(mgr_id) references employee(emp_id) on delete set null
);
```

<br>

Add foreign key to **employee table branch_id** from branch table and **employee table super_id** from **itself** 
```sql
	alter table employee 
	add foreign key(branch_id)
	references branch(branch_id)
	on delete set null;
	
	alter table employee
	add foreign key(super_id)
	references employee(emp_id)
	on delete set null;
```

<br>

Add Client Table
```sql
	create table client(
	client_id int primary key,
	client_name varchar(40),
	branch_id int,
	foreign key(branch_id) references branch(branch_id) on delete set null
	);
```

<br>

Add works_with table. Here **empid and clientid** both primary key also they are foreign key.
````sql
create table works_with(
    emp_id int,
    client_id int,
    total_sales int,
    primary key(emp_id, client_id),
    foreign key(emp_id) references employee(emp_id) on delete cascade,
    foreign key(client_id) references client(client_id) on delete cascade
);

````
<br>

Branch_supplier table

````sql
create table branch_supplier(
    branch_id int,
    supplier_name varchar(40),
    supply_type varchar(40),
    primary key(branch_id, supplier_name),
    foreign key(branch_id) references branch(branch_id) on delete cascade
);
````
<br>

## Data
<img src="https://github.com/abdulmukit98/sql/assets/56398175/1e897f3e-aea0-4c2b-ae66-69094c956589" width="1200px">

## Insert Data
insert into **employee and branch** table

````sql
	insert into employee values(100, 'David', 'Wallace', '1967-11-17', 'M', 250000, NULL, NULL);
	insert into branch values(1, "Corporate", 100, "2006-02-09");
	update employee 
	set branch_id = 1
	where emp_id = 100;
	insert into employee values(101, "Jan", "Levinson", "1961-05-11", "F", 110000, 100, 1);
	insert into employee values(102, "Michael", "Scott", "1964-03-15", "M", 75000, 100, null);
	insert into branch values(2, "Scranton", 102, "1992-04-06");
	update employee 
	set branch_id = 2
	where emp_id = 102;
	insert into employee values(103, "Angela", "Martin", "1971-06-25", "F", 63000, 102, 2);
	insert into employee values(104, "Kelly", "Kapoor", "1980-02-05", "F", 55000, 102, 2);
	insert into employee values(105, "Stanley", "Hudson", "1958-02-19", "M", 69000, 102, 2);
	insert into employee values(106, "Josh", "Porter", "1969-09-05", "M", 78000, 100, null);
	insert into branch values(3, "Stamford", 106, "1998-02-13"); 
	update employee 
	set branch_id = 3
	where emp_id = 106;
	insert into employee values(107, "Andy", "Bernard", "1973-07-22", "M", 65000, 106, 3);
	insert into employee values(108, "Jim", "Halpert", "1978-10-01", "M", 71000, 106, 3);

````

insert into **client table**
````sql
	insert into client values(400, "Dunmore Highschool", 2);
	insert into client values(401, "Lackawana Country", 2);
	insert into client values(402, "FedEx", 3);
	insert into client values(403, "John Daly Law, LLC", 3); 
	insert into client values(404, "Scranton Whitepages", 2);
	insert into client values(405, "Times Newspaper", 3);
	insert into client values(406, "FedEx", 2);
````

insert into **branch_supplier** table
````sql
	insert into branch_supplier values(2, "Hammer Mill", "Paper");
	insert into branch_supplier values(2, "Uni-ball", "Writing Utensils");
	insert into branch_supplier values(3, "Patriot Paper", "Paper");
	insert into branch_supplier values(2, "J.T. Forms & Labels", "Custom Forms");
	insert into branch_supplier values(3, "Uni-ball", "Writing Utensils");
	insert into branch_supplier values(3, "Hammer Mill", "Paper");
	insert into branch_supplier values(3, "Stamford Labels", "Custom Forms");
````

<br><br>
