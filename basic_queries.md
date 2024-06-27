---
title: Basic Queries
layout: template
filename: basic_queries
---

#### Order By
First sort by major. If duplicate major, sort by id
````sql
  select * from student
  order by major, student_id desc;
  
  select * from student
  order by student_id desc;
````

#### limit
````sql
  select * from student
  limit 2;
````

#### OR
````sql
  select * from student
  where major="CSE" or major="EEE";
````

#### Not Equal
  ````sql
  select * from student
  where major <> "CSE";
````

#### IN
````sql
  select * from student
  where name in('jake', 'lira', 'tom');
````
