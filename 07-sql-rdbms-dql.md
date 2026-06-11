# Structured Query Language (SQL) is used to interact with the database and the language is case insensitive

## RDBMS - Relational Database Management System
* R (Relational): Data was managed till 90s or early 20s with `DBMS` later on developers introduced `RDBMS`. Oracle, PostgreSQL, My SQL, MS SQL Server, etc.
* D (Data): Any meaningful information
* DB (Database): Where we store our data
  - Structured DB: When data is stored in row and column format and where we call rows as records and columns as fields.
  - Unstructured DB: excel sheet, word files, etc
* MS (Management System): Data is managed

Q. We store data in excel in row and column format still we don't call it a database instead we call it excell sheet.
- If any DBMS application follows all 12 rules of Codd's (1985) it is called RDBMS.

## Three layers of an Application
1. `Application/user layer/user interface` - End-User interacts with application from here
2. `Backend/Bussiness layer` - Logic checking is done here 
3. `DB layer` - To interact with DB we use a language `SQL` and a tool `SQL Plus`

## Types of SQL
* DDL
* DML
* TCL
* DCL
* DQL

## DQL
1. To see DBs in our server
```
cat /etc/oratab
```

2. To check which DB is running
```
ps -ef | grep pmon
```
* `pmon` stands for process monitor
* in result if any DB_name shown with pmon (eg. ora_pmon_prod) then it is running (eg. prod)

3. To connect with DB
* setup environment
```
. oraenv
```
* connect
```
sqlplus DB_user_name/password
```
or enter separately
```
sqlplus DB_user_name
```
```
password: ____typePassword
```
eg.
```
sqlplus hr/oracle
```

4. To come out of `SQL` prompt
* temporary way
```
!
```
to enter back
```
exit
```
* temporary way
```
ho
```
to enter back
```
exit
```
* permanent way
```
exit
```
To comeback to `sql` prompt login again

5. To clear screen
```
clear
```
or
```
cle scr
```

6. To display current session DB username
```
show user
```

7. To display all information(fields/columns) from the table called `tab` inside DB
```
select * from tab;
```

8. To reduce the column size while viewing
`for` - format how the data in a specific column is displayed (a20, a12, etc...)
```
col field_name for format_model
```
eg.
```
col tname for a20
```

9. To repeat previous query
```
r
```

10. To display the blueprint of a table
`desc` stands for describe
```
desc table_name
```
eg.
```
desc employee
```

11. To display records for asked fields
```
select field_name1, field_name2, field_name3... from table_name;
```

12. To fix formating issue in records
```
set line number_of_characters
```
eg. 100 characters allowed in a row
```
set line 100
```

13. To set repeating heading after a particular interval only
- heading appears after page break. So, we set page size
```
set pagesize number_of_records
```
eg.
```
set pagesize 100
```

14. To display different heading name
```
select field_name1 as new_field_name1, field_name2 as new_field_name2, ... from table_name;
```
- if there is space between Field Name => "Field Name"
- if field_name is provided inside "" its case remains unchanged but if not it gets capitalized => FIELD_NAME
- `as` can be removed from the statement it changes nothing => `select field_name new_field_name from table_name`

15. To do arithematic operations
```
select field_name operator operand result_field_name from table_name;
```
eg.
```
select salary*.10 PF, salary-(salary*.10) "Net Salary" from employees;
```

16. Concatenate operator (`||`)
```
select field_name1 || " " || field_name2 "Field Name" from table_name;
```
eg.
```
select first_name || " " || last_name "Full Name" from employees
```

17. Compare (case sensitive)
```
select field_name from table_name
where field_name condition comparing_amount;
```
eg.
```
select salary from employees
where salary > 10000;
```

* `and` => where `condition1` and `condition 2`;
* `or` => where `condition1` or `condition2`;
* `in` => where in (`value1`, `value2`); includes `value1` and `value2`
* `between` => where between `value1` and `value2`; includes `value1`...`value2`
* `like` => where field_name like 'string'
  - eg1. `where first_name like 'Peter';` returns all records with Peter name
  - eg2. `where first_name like 'P%';` return all records whose first name starts with 'P'
  - eg3. `where first_name like '_e%';` return all records whose first name's second character is 'e'
  - eg4. `where first_name like '_e%e_';` return all records whose first name's second and second last character are 'e'
* `is` => where `field_name` is `null`; => null is a junk character (neither '_', 'character', nor 'number') and `is` always used for `null`
* `is not` => where `field_name` is not `null`;
