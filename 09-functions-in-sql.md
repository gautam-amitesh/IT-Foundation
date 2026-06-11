# SQL Functions

* To convert a number or date/time value into a formatted character string
  - `value`: date,timestamp or number needed to convert
  - `format_mask` (optional but recommended): pattern for output string
```
to_char(value, format_mask)
```
eg.
```
select to_char(hire_date, 'dd - mm - yyyy') from employees;
```

***

* `DUAL` table in Oracle SQL
  - every `select` statement must have a `from` clause.
  - `dual` is a built-in table containing 1 `record` and 1 `field`
  - a universal dummy table to evaluate expressions, run functions, or do calculations without querying a massive real table which return result in each record.
  - eg.
```
select 50+50 as result from dual;
```

***

* To get current date and time configured on OS of our databse server
```
select sysdate from dual;
```

***

* To get current detailed time configured on OS of our databse server
```
select systimestamp from dual;
```

***

* To convert string into date
  - inverse of `to_char()`
  - `string_value`: string containing `date`
  - `format_mask`: pattern(how to know which part is year, month, day, and time) of the provided string
```
to_date(string_value, format_mask)
```
eg.
```
select employee_id, first_name, hire_date from employees
where hire_date>to_date('31-12-2006','dd-mm-yy');
```
eg. instead of hard-coding take input for string_value. `&`: substitution variable
```
select employee_id, first_name, hire_date from employees
where hire_date>to_date(`&dt`,'dd-mm-yy');
```

***

* To extract single component(year, month, or date) from date
```
extract(component from datetime_value)
```
eg.
```
select extract(year from hire_date) from employees;
```

***

* To sort(asc/desc) the listing of table contents
  - `order by` clause will be the last clause of any query
  - `sorting_order`: `asc` ascending (default if not provided) / `desc` (descending)
  - we can supply multiple `field_name` for sorting
```
select <field_name>, <field_name> from table/view_name
where condition
order by <field_name> sorting_order, <field_name> sorting_order;
```
eg. sort in ascending order
```
select employee_id, first_name, salary, hire_date, extract(year from sysdate) - extract(year from hire_date) "Total Exp" from employees
where extract(year from sysdate) - extract(year from hire_date) > 20
order by salary;
```
eg. sort in descending order
```
select employee_id, first_name, salary, hire_date, extract(year from sysdate) - extract(year from hire_date) "Total Exp" from employees
where extract(year from sysdate) - extract(year from hire_date) > 20
order by salary desc;
```
eg. multiple sorting options
```
select employee_id, first_name, salary, hire_date, extract(year from sysdate) - extract(year from hire_date) "Total Exp" from employees
where extract(year from sysdate) - extract(year from hire_date) > 20
order by salary desc, first_name asc;
```

***

* To take a large number of rows and summarize them down to a smaller set of rows based on common values in one or more columns
  - this way we use single row return function with field name
  - `group by` is used mostly with COUNT, SUM, AVG, MAX, or MIN functions
```
select <field_name>, <field_name>, single_row_return_fn() from table_name
group by <field_name>, <field_name>;
```
eg. it display department wise number of employees
```
select department_id, count(*) from employees
group by department_id;
```
eg. `department_id != 50` this condition also filters out `null` to fix this `department_id != 50 or department_id is null`
```
select department_id, count(*) from employees
where department_id != 50 or department_id is null
group by department_id;
```
eg. display those `first_name` which is repeated (more than 1 times)
```
select first_name, count(*) as "Duplicate" from employees
group by first_name
having count(*) > 1;
```

***

* To filter data after it has been grouped
  - `having` clause can only be used with `group by` clause
  - `having` can be used with single row return function unlike `where`
  - just like `where` is used for filtering ungrouped data `having` is used for grouped data
```
select department_id, count(*) from employees
group by department_id
having count(*) > 5;
```
