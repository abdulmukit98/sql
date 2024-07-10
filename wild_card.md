---
title: Wildcards
layout: template
filename: wild_card
---

### Dataset
<img src="https://github.com/abdulmukit98/sql/assets/56398175/1e897f3e-aea0-4c2b-ae66-69094c956589" width="1000px">

### Wildcards
fetch row where client_name contain "LLC" keyword

````sql
   select * from client
   where client_name like '%llc';

   % mean any number of character in the position
   - mean a single character
````

find employee whose birth date is october(10)
````sql
   select * from employee
   where birth_date like '____-10%';

   first 4 character _ _ _ _ then - then 10 % (remaining)

   select * from client where client_name like "%school%"
````

## Union
Multiple queries together
````sql
   select client_name from client
   union
   select birth_date from employee
   union 
   select first_name from employee
   ;
````

## JOIN
We can use **ON** instead of **WHERE** if single query comparison
````sql
      select employee.emp_id, employee.first_name, branch.branch_name 
      from employee
      join branch
      where employee.emp_id = branch.mgr_id;

      -- on employee.emp_id = branch.mgr_id

````

Find all employee who work with client from works_with table
````sql
      select employee.emp_id, employee.first_name, client.client_id, client.client_name , works_with.total_sales	
      from employee
      join client, works_with
      where employee.emp_id = works_with.emp_id and client.client_id = works_with.client_id	
      ;

````

Find all employee and corresponding branch

````sql
      select employee.first_name, branch.branch_name 
      from employee
      join branch
      where employee.branch_id = branch.branch_id;

````

## Nested Query
Query inside query

````sql
   find all employee whose branch is which branch manager id 102 (branch 2)

   select employee.first_name 
   from employee
   where employee.branch_id in (
       select branch.branch_id 
       from branch
       where branch.mgr_id = 102
   );

````

## On Delete

if a foreign key is set to **on delete set null**,  <br>
whenever the primary row is deleted, the foreign key is set to null.
<br><br>
if a foreign key is set to **on delete cascade**, <br>
whenever the primary key row is deleted, the foreign key row also deleted <br><br>

````sql
create table works_with(
    emp_id int,
    client_id int,
    total_sales int,
    primary key(emp_id, client_id),
    foreign key(emp_id) references employee(emp_id) on delete cascade,
    foreign key(client_id) references client(client_id) on delete cascade
);


create table client(
    client_id int primary key,
    client_name varchar(40),
    branch_id int,
    foreign key(branch_id) references branch(branch_id) on delete set null
);


If a foreign key is also the primary key it must be on delete cascade
create table branch_supplier(
    branch_id int,
    supplier_name varchar(40),
    supply_type varchar(40),
    primary key(branch_id, supplier_name),
    foreign key(branch_id) references branch(branch_id) on delete cascade
);
````
