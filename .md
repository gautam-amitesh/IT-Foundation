# SQL Functions

1. A sub-query/inner-query is a `SELECT` statement nested inside main-query (SQL statement). Main query use the result of sub-query to evaluate the statement. Inner most sub-query gets executed first
  * eg. it provide the details of employee earning highest salary
```
select employee_id, first_name, salary, department_id from employees
where salary = (select max(salary) from employees);
```
  * eg. it provide details of employees earning more the average salary
```
select employee_id, first_name, salary, department_id from employees
where salary > (select avg(salary) from employees);
```
  * eg. it provides the detail of employee earning lowest salary
```
select employee_id, first_name, salary, department_id from employees
where salary = (select min(salary) from employees);
```
  * eg. it provide details of employees earning second highest salary
```
select employee_id, first_name, salary, department_id from employees
where salary = (select max(salary) from employees
where salary < (select max(salary) from employees));
```
  * eg. it provide details of employees earning third highest salary
```
select employee_id, first_name, salary, department_id from employees
where salary = (select max(salary) from employees
where salary < (select max(salary) from employees
where salary < (select max(salary) from employees)));
```

***

2. Joining tables
   * If there is relation (atleast 1 common `<field>` eg. `department_id`) between two tables
     <img width="942" height="167" alt="image" src="https://github.com/user-attachments/assets/79cd2e6c-66ee-46fc-a4d2-378ac015af50" />


   * There are three method to join two tables
     - `inner join/equi join`: it will only display those `records` which are common in both the tables `on` the basis of `<field_name>`
       <img width="947" height="167" alt="image" src="https://github.com/user-attachments/assets/73542749-612f-48a4-a9ec-9aeb9cde3197" />


     - `outer join`: extends the functionality of `inner join` by preserving unmatched rows from one or both tables and padding the missing details with `null`
        - `left outer join`: displays all records (empty records also) from left table and matched records from right table
          <img width="942" height="168" alt="image" src="https://github.com/user-attachments/assets/9a12131e-d3fc-46af-a59d-7e575e64bf1f" />

        - `right outer join`: displays all records (empty records also) from right table and matched records from left table
          <img width="943" height="163" alt="image" src="https://github.com/user-attachments/assets/35245960-de71-4158-9519-500fd8fdea87" />

        - `full outer join`: displays all records (empty records also) from both the table
          <img width="942" height="167" alt="image" src="https://github.com/user-attachments/assets/ac7780fe-5b01-4c89-ae13-4bbc9027b733" />

     - `self join`: 
          
***

   * To join two tables and fetch data from it using `inner join`
     - we use `pseudo` table name instead of full table name. eg. `emp`/`e`: employees, `dept`/`d`: departments
```
select emp.employee_id, emp.first_name, emp.salary, emp.department_id, dept.department_name
from employees emp
inner join departments dept on emp.department_id = dept.department_id;
```
```
select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
from employees e
inner join departments d on e.department_id = d.department_id
where lower(d.department_name) like 'marketing' or lower(d.department_name) like 'finance';
```

***

   * To join two tables and fetch data from it using `equi join`
     - insted of using `inner join` we write `,`
     - in place of `on` we write `where`
```
select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
from employees e, departments d
where e.department_id=d.department_id and lower(d.department_name) like 'marketing' or lower(d.department_name) like 'finance';
```

***

   * To join two table and fetch data from it using `left outer join`

- eg. it will display all records from employees table
```
select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
from employees e left join departments d
on e.department_id = d.department_id;
```
- eg. it will display all records from departments table
```
select e.employee_id, e.first_name, e.salary, d.department_id, d.department_name
from departments d left join employees e
on e.department_id = d.department_id;
```

***

   * To join two table and fetch data from it using `right outer join`

- eg. it will display all records from departments table
```
select e.employee_id, e.first_name, e.salary, d.department_id, d.department_name
from employees e right join departments d
on e.department_id = d.department_id;
```
- eg. it will display all records from employees table
```
select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
from departments d right join employees e
on e.department_id = d.department_id;
```

***

   * To join two table and fetch data from it using `full outer join`

- eg. it will display all records from departments table and employees table
```
select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
from employees e full join departments d
on e.department_id = d.department_id;
```
