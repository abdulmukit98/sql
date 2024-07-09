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

   % mean any character in the position
   - mean a single character
````

find employee whose birth date is october(10)
````sql
   select * from employee
   where birth_date like '____-10%';

   first 4 character _ _ _ _ then - then 10 % (remaining)

   select * from client where client_name like "%school%"
````


