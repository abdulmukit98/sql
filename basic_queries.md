---
title: Basic Queries
layout: template
filename: basic_queries
---

#### Order By
First sort by major. If duplicate major, sort by id
````
  select * from student
  order by major, student_id desc;
````

#### limit
````
  select * from student
  limit 2;
````
