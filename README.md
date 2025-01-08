# MySQL_solved_exercise

This series of SQL queries covers various tasks involving employee data management and retrieval, demonstrating the use of **joins, subqueries, groupings, aggregations, case statements, functions, procedures, triggers**, and more. Here's a detailed explanation of each query:

### **Exercise 1: Average Salary by Gender in Each Department**
- **Objective**: Calculate the average salary of male and female employees in each department.
- **Explanation**: This query joins the `salaries`, `employees`, `dept_emp`, and `departments` tables. It calculates the average salary for each department (`dept_name`) and gender (`gender`). The `GROUP BY` clause groups the results by department and gender, and the `ORDER BY` ensures the results are ordered by department.
  
### **Exercise 2: Find the Lowest and Highest Department Numbers**
- **Objective**: Retrieve the smallest and largest department numbers from the `dept_emp` table.
- **Explanation**: The first query uses `MIN()` to find the smallest department number, and the second uses `MAX()` to find the largest. Both queries work directly on the `dept_emp` table.

### **Exercise 3: Retrieve Employee Information with Manager Assignment**
- **Objective**: For all employees with a number less than or equal to 10040, get their employee number, the smallest department number they have worked in, and assign a manager ID based on their employee number.
- **Explanation**: The query uses a **subquery** in the `SELECT` clause to find the minimum department number an employee worked in. It uses a `CASE` statement to assign a manager ID based on the employee number, with a different ID for employees with numbers less than or equal to 10020 and those between 10021 and 10040. 

### **Exercise 4: List Employees Hired in 2000**
- **Objective**: Retrieve a list of employees who were hired in the year 2000.
- **Explanation**: This query filters employees by the `hire_date` column, using the `YEAR()` function to extract the year from the `hire_date` and compare it to 2000.

### **Exercise 5: Retrieve Engineers and Senior Engineers**
- **Objective**: Get a list of employees with titles that include "engineer" or "senior engineer."
- **Explanation**: The `LIKE` operator is used to match titles with these keywords. The first query retrieves all employees with "engineer" in their title, and the second specifically retrieves "senior engineers."

### **Exercise 6: Stored Procedure for Employee's Last Department**
- **Objective**: Create a procedure that takes an employee number as input and returns their last department along with the department number.
- **Explanation**: The stored procedure `last_dept` finds the employee’s last department using a **subquery** to retrieve the most recent `from_date` for that employee from the `dept_emp` table. The result is returned for the specified employee.

### **Exercise 7: Count Contracts with Specific Salary Conditions**
- **Objective**: Count how many salary contracts have a duration of more than a year and a salary of $100,000 or more.
- **Explanation**: This query uses `DATEDIFF()` to calculate the duration of salary contracts and filters those with a salary above $100,000 and a duration greater than 365 days (i.e., one year).

### **Exercise 8: Trigger to Validate Hire Date**
- **Objective**: Create a trigger to ensure that if an employee's hire date is in the future, it is set to the current date.
- **Explanation**: The trigger `trig_hire_date` checks if a new hire date is in the future (`NEW.hire_date > today`). If it is, the trigger updates the hire date to the current system date. This is done before inserting the employee data into the `employees` table.

### **Exercise 9: Functions to Retrieve Highest and Lowest Salaries**
- **Objective**: Define two functions, one to get the highest salary and another to get the lowest salary for a given employee.
- **Explanation**: The function `f_highest_salary` retrieves the maximum salary for an employee by joining the `employees` and `salaries` tables and using `MAX()`. The function `f_lowest_salary` works similarly but returns the minimum salary using `MIN()`.

### **Exercise 10: Function to Retrieve Salary Based on Condition**
- **Objective**: Create a function that retrieves either the highest or lowest salary based on a condition, or the difference between them if the condition is neither "min" nor "max."
- **Explanation**: The function `f_salary` accepts two parameters: `emp_no` and a string (`min_or_max`). It uses a `CASE` statement to return either the highest salary, the lowest salary, or the difference between the highest and lowest salary based on the value of `min_or_max`. If an invalid string is provided, the difference is returned.

---

Each of these tasks demonstrates key aspects of SQL functionality such as **joins**, **aggregation**, **subqueries**, **conditional logic**, **stored procedures**, **triggers**, and **user-defined functions**. These operations are used to retrieve, manipulate, and analyze data effectively in a relational database system.  

Query:
