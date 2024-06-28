---
title: Conpany Database 
layout: template
filename: company_database
---

## Company Database Table
**Employee Table**

| emp_id | first_name | last_name | birth_date | sex |  salary  | supervisor_id | branch_id |
|--------|------------|-----------|------------|-----|----------|---------------|-----------|
| 100    |  David     | wallace   | 1967-11-17 | M   | 250.,000 |      NULL     |      1    |
| 101    |  Jan       | Levinson  | 1961-05-11 | F   | 110.,000 |      100      |      1    |


**Branch Table**

| branch_id | branch_name | manager_id | manager_start_date |
|-----------|-------------|------------|--------------------|
| 1         | corporate   | 100        |  2006-02-09        |
| 2         | scranton    | 102        |  1992-04-06        |
| 3         | stampford   | 106        |  1998-02-13        |
{:.table-striped}

**Client Table**

| client_id | client_name        | branch_id |
|-----------|--------------------|-----------|
| 400       | Dunmore Highschool | 2         |
| 401       | Lackawana Coutry   | 2         |
| 402       | FedEX              |  3        |
| 403       | Jogn Dally law llc |  3        |
{:.table-striped}

**Works_With Table**

| emp_id | client_id | total_sales |
|--------|-----------|-------------|
| 105    | 400       | 55000       |
| 102    | 401       | 267000      |
| 108    | 402       | 22500       |
| 107    | 403       |  5000       |
{:.table-striped}

**Branch Supplier Table**

| branch_id | supplier_name | supply_type      |
|-----------|---------------|------------------|
| 2         | Hammer Mill   | Paper            |
| 2         | Uni Bann      | Writing Utensils |
| 3         | Patriot Paper | Paper            |
{:.table-striped}


