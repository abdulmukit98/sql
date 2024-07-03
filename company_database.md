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


<br><br>
