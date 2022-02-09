# Pewlett Hackard Analysis

## Overview of the Analysis

Pewlett Hackard is a large company boasting several thousand employees and it's been around for a long time. As baby boomers begin to retire at a rapid rate Pewlett Hackard is looking toward the future in two ways. First, it's offering a retirement package for those who meet certain criteria. Second, it's starting to think about which positions will need to be filled in the near future. The number of upcoming retirements will leave thousands of job openings.

Bobby is an up and coming HR Analyst whose task is to perform employee research. Speciafically, he needs to find answers to the following questions, Who will be retitring in the next few years, and how many positions will Pewlett Hackard need to fill? This analysis will help future-proof Pewlett Hackard by generating a list of all employees eligible for the retirement package. The employee data Bobby needs is only available in the form of six CSV files because Pewlett Hackard has been mainly using Excel and VBA to work with their data. But now they've finally decided to update their methods and instead use SQL, a definite upgrade considering the amount of data.

#### Purpose

The purpose of this analysis is to help Bobby build an employee database with SQL by applying data modelling, engineering, and analysis skills. Also, now that Bobby has proven his SQL chops, his manager has given two more assignments: To determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. Then, to write a report that summarizes the analysis and helps prepare Bobby’s manager for the “silver tsunami” as many current employees reach retirement age.

## Results

Using the ERD (shown below) as a reference, four new tables are created to perform this analysis. The findings are as follows:

<img width="548" alt="ERD" src="https://user-images.githubusercontent.com/95826875/153299473-d27c1ec1-b2b5-4456-9af0-8b0e1039444a.png">

- A _retirement_titles_ table (shown below) is created by retrieving the 'emp_no', 'first_name', and 'last_name' columns from the _Employees table_ and 'title', 'from_date', and 'to_date' columns from the _Titles table_ and then joining them on the primary key. Then the data is filtered on the 'birth_date' column to retrieve the employees who were born between 1952 and 1955, orderd by the employee number.

   Total 133,776 rows returned with the list of employees who is going to retire in coming few years.

  <img width="666" alt="retirement_titles" src="https://user-images.githubusercontent.com/95826875/153288780-aa73e4eb-4c83-4a64-889b-c462c8830781.png">

- In the _retirement_titles_ table, there are duplicate entries for some employees because they have switched titles over the years. So now a new table _unique_titles_ (shown below) is created to remove these duplicates and to keep only the most recent title of each employee. This is done by using the 'DISTINCT ON' statement to retrieve the first occurrence of the employee number for each set of rows defined by the 'ON()' clause. Then excluding those employees that have already left the company by filtering on 'to_date' to keep only those dates that are equal to '9999-01-01', and then sorting in ascending order by the employee number and descending order by the last date (i.e., 'to_date') of the most recent title.

  Total 72458 rows of data returned with the list of employees with their most recent titles.

  <img width="488" alt="unique_titles" src="https://user-images.githubusercontent.com/95826875/153288791-93fb0d1f-3bac-4d12-916e-62e5ccb9fb2b.png">

- A _retiring_titles_ table (shown below) is created to retrieve the number of employees by their most recent job title who are about to retire, by first, retrieving the number of titles from the _unique_titles table_. Then, grouping the table by title, then sorting the count column in descending order.

  Total 7 rows returned with the count of employees by their most recent job titles. Maximum number of employees have senior titles, and the data suggest that 64% of the employees are about to retire.
  
  <img width="227" alt="retiring_titles" src="https://user-images.githubusercontent.com/95826875/153288805-0ae971c5-d0bf-4088-9b37-853e7833d9a8.png">

- A _mentorship_eligibility table_ (shown below) is created by retrieving the 'emp_no', 'first_name', 'last_name', and 'birth_date' columns from the _Employees table_, 'from_date' and 'to_date' columns from the _Department Employee table_, and 'title' column from the _Titles table_. 'DISTINCT ON' statement is used to retrieve the first occurrence of the employee number for each set of rows defined by the 'ON()' clause. _Employees table_ and the _Department Employee table_ are joined on the primary key. And _Employees table_ and the _Titles table_ are also joined on the primary key. Later, the data is filtered on the 'to_date' column to all the current employees, then on the 'birth_date' columns to get all the employees whose birth dates are between January 1, 1965 and December 31, 1965, order by the employee number.
  
  Total 1549 rows returned which displays a list of the current employees who were born between January 1, 1965 and December 31, 1965 and are eligible for the mentorship program.
 
  <img width="738" alt="mentorship_eligibilty" src="https://user-images.githubusercontent.com/95826875/153296660-937b88fc-b98d-48a3-a6da-96d7e86d0996.png">


## Summary

#### How many roles will need to be filled as the "silver tsunami" begins to make an impact?

Although the _retirement_titles table_ contains all the information about the employees that are about to retire. But to provide more insight into the upcoming "silver tsunami, a new table _retirement_per_department can be created displaying the employee data as per their department. So that we can break down the data as per each employee's department and help Bobby and his manager with what to expect in each department separately. 

<img width="803" alt="retirement_per_dept_query" src="https://user-images.githubusercontent.com/95826875/153304032-90b5de86-ce38-467a-ba93-bec355f558bc.png">

<img width="886" alt="retirement_per_dept_table" src="https://user-images.githubusercontent.com/95826875/153304074-f6f06bb7-7dea-4bb3-bdf0-a2d67ba1ff9a.png">


#### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
