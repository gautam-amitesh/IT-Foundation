# Functions in SQL
Function is an encapsulated reusable set of predefined instructions which returns value for supplied argument.

## Two types of SQL Functions
1. Single Value/Row return function(Scalar Functions): which returns single value
   * we can't use any field name with a single row return function but we can use multiple single row return functions in single query
     - eg. `select employee_id, count(employee_id) from employees;` not correct
     - eg. `select count(employee_id), sum(salary), avg(salary) from employees;` correct
   * we can't use single row return function with `where` clause
     - eg. `select employee_id from employees where sum(employee_id) = 100;` not correct
     - eg. `select first_name from employees where length(first_name) = 5;` correct
3. Multiple Value/Row return function(Table-Valued Functions - TVFs): which returns multiple rows of value

## SQL Functions
### Single row return functions
1. To count number of `records`
   - it doesn't count for `null`
   - `count(*)` => for each `record` if any `field` contains value it will be counted
```
select count(field_name) from table_name;
```
eg.
```
select count(employee_id) from employees;
```

***

2. To get sum of all `records` in a `field`
```
select sum(field_name) from table_name;
```
eg.
```
select sum(salary) from employees;
```

***

3. To get average of all `records` in a `field`
```
select avg(field_name) from table_name;
```
eg.
```
select avg(salary) from employees;
```

***

4. To round a value
```
select round(value, decimal_place) from table_name;
```
eg.
```
select round(avg(salary), 2) from employees;
```
eg. to get average for employees whose employee_id is 80
```
selectround(avg(salary), 2) from employees
where employee_id = 80;
```

***

5. To truncate a value
   - adds `0` after defined decimal place(+ve or -ve)
```
select trunc(value, decimal_places) from table_name;
```
eg. it will add `0` after 2 decimal places which will be ignored
```
trunc(3475.555, 2) => 3475.55
```
eg. it will add `0` after -2 decimal places
```
trunc(3475.555, -2) => 3400
```

***

6. To get max
```
select max(field_name) from table_name;
```
eg.
```
select max(salary) from employees;
```

***

7. To get min
```
select min(field_name) from table_name;
```
eg.
```
select min(salary) from employees;
```

***

### Multiple row return functions
1. To convert to upper case
```
select upper(field_name) from table_name;
```
eg.
```
select first_name, upper(first_name) from employees;
```

***

2. To convert to lower case
```
select lower(field_name) from table_name;
```
eg.
```
select first_name, lower(first_name) from employees;
```

***

3. To count number of characters in each record of a field
```
select length(field_name) from table_name;
```
eg.
```
select first_name, length(first_name) from employees;
```

***

4. 
