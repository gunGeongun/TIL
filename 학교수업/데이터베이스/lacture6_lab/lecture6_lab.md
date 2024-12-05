## Nested Queries

- Write a SQL query to find the highest-paid employee in
  each department. The result should include the
  department name, the employee's first name, last
  name, and salary.

```sql
select d.dname,e.fname,e.lname,e.salary 
    from employee e join department d on e.dno = d.dnumber
    where salary = (
    select MAX(salary)
    from employee e2
    where e2.dno = d.dnumber
    );
```

## Inner Join

- Write a SQL query to list the first name and last name
  of employees along with the project name they are
  working on. Use JOIN to connect the EMPLOYEE,
  WORKS_ON, and PROJECT tables.

```sql
select e.fname, e.lname, p.pname
from employee e 
join department d
on e.dno = d.dnumber
join project p 
on d.dnumber = p.dnum;
```

## Inner Join with CASE

- Write a SQL query to retrieve the project name, first
  name, last name, and salary of employees who are
  working on any project. Additionally, categorize the
  employees’ salaries into three groups: 'High' for
  salaries of 50,000 or more, 'Medium' for salaries
  between 30,000 and 49,999, and 'Low' for salaries
  below 30,000.

```sql
select p.pname,e.fname, e.lname, e.salary, 
    case 
    when e.salary >= 50000 then 'High'
    when e.salary between 30000 and 49999 then 'Medium'
    when e.salary < 30000 then 'Low'
    end as salarycategory
    from employee e 
    join works_on w
    on e.ssn = w.essn
    join project p 
    on w.pno = p.pnumber;

```

## Outer Join (1 / 2)

- Write a SQL query to retrieve the first name, last name,
  and salary of all employees along with their dependent
  names. Ensure that all employees are included in the
  results, even if they do not have any dependents.
  • Use an OUTER JOIN to achieve this.

```sql
select e.fname, e.lname, e.salary, d.dependent_name
    from employee e left outer join dependent d on e.ssn = d.essn;
```

## Outer Join (2 / 2)

- Write a SQL query to retrieve the first and last names
  of all employees along with the first and last names of
  their supervisors. Ensure that the results include
  employees who do not have supervisors.
  • Use an OUTER JOIN to include all employees, even those
  without assigned supervisors.

```sql
select e1.fname as employee_first_name,e1.lname as employee_last_name,e2.fname as supervisor_first_name,e2.lname as supervisor_last_name
    from employee e1 left outer join employee e2 on e1.super_ssn = e2.ssn;
```