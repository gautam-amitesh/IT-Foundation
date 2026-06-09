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
eg.
```
select employee_id, first_name from employees
where lower(first_name) like 'peter';
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

4. To extract a specific portion of string.
   - `start_position` => starts from `1`
   - `number_of_characters` (optional) => if not supplied it will extract everything from the `start_position`
```
select substr(field_name, start_position, number_of_characters) from table_name;
```
eg. 1st position from start
```
select first_name, substr(first_name, 1, 4) from employees;
```
eg. 4th position from end
```
select first_name, substr(first_name, -4, 4) from employees;
```
eg. 4th position from end using `length`
  - `start_position` => `length(field_name) - (number_of_characters-1)`
```
select first_name, substr(first_name, length(first_name)-3, 4) from employees;
```

***

5. To find the starting position of a character/substring in a string
```
select instr(field_name, 'substring/character') from table_name;
```
eg.
```
select first_name, instr(first_name, 'e') from employees;
```
eg. 
```
select first_name, instr(lower(first_name), 'e') from employees;
```

***

6. To pad the left/right side of a string with a specific set of characters until it reaches a desired total length
  - left
  - `length` => total length you want the final string to be.
  - `pad_string` (optional) => character (or characters) you want to add to the left side. If you leave this parameter out, SQL will default to padding the string with spaces.
```
select lpad(field_name, length, pad_string) from table_name;
```
eg. last four characters remains intact but all previous characters get converted into #
```
select first_name, lpad(substr(first_name, -4, 4), length(first_name), '#') from employees;
```
  - right
```
select rpad(field_name, length, pad_string) from table_name;
```
eg. concatenate first name and last name with a space in between using rpad
```
select first_name, last_name, concat(rpad(first_name, length(first_name)+1), last_name) "Full Name" from employees;
```

***

7. To concatenate exactly two strings together
```
select concat(field_name1, field_name2) from table_name;
```
eg. to concatenate three string: we use nested `concat` function
```
select first_name, last_name, concat(concat(first_name, ' '), last_name) "Full Name" from employees;
```
