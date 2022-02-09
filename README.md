# Pewlett Hackard Analysis

## Overview of the Analysis

Pewlett Hackard is a large company boasting several thousand employees and it's been around for a long time. As baby boomers begin to retire at a rapid rate Pewlett Hackard is looking toward the future in two ways. First, it's offering a retirement package for those who meet certain criteria. Second, it's starting to think about which positions will need to be filled in the near future. The number of upcoming retirements will leave thousands of job openings.

Bobby is an up and coming HR Analyst whose task is to perform employee research. Speciafically, he needs to find answers to the following questions, Who will be retitring in the next few years, and how many positions will Pewlett Hackard need to fill? This analysis will help future-proof Pewlett Hackard by generating a list of all employees eligible for the retirement package. The employee data Bobby needs is only available in the form of six CSV files because Pewlett Hackard has been mainly using Excel and VBA to work with their data. But now they've finally decided to update their methods and instead use SQL, a definite upgrade considering the amount of data.

#### Purpose

The purpose of this analysis is to help Bobby build an employee database with SQL by applying data modelling, engineering, and analysis skills. Also, now that Bobby has proven his SQL chops, his manager has given two more assignments: To determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. Then, to write a report that summarizes the analysis and helps prepare Bobby’s manager for the “silver tsunami” as many current employees reach retirement age.

## Results

The findings of this analysis are as follows:

- A 'retirement_titles' table (shown below) is created by retrieving the emp_no, first_name, and last_name columns from the Employees table and title, from_date, and to_date columns from the Titles table and then joining them on the primary key. Then the data is filtered on the birth_date column to retrieve the employees who were born between 1952 and 1955, orderd by the employee number.

  Total 133,776 rows are returned with the list of employees who is going to retire in coming few years.

<img width="666" alt="retirement_titles" src="https://user-images.githubusercontent.com/95826875/153288780-aa73e4eb-4c83-4a64-889b-c462c8830781.png">

<img width="488" alt="unique_titles" src="https://user-images.githubusercontent.com/95826875/153288791-93fb0d1f-3bac-4d12-916e-62e5ccb9fb2b.png">

<img width="227" alt="retiring_titles" src="https://user-images.githubusercontent.com/95826875/153288805-0ae971c5-d0bf-4088-9b37-853e7833d9a8.png">

<img width="738" alt="mentorship_eligibilty" src="https://user-images.githubusercontent.com/95826875/153288822-acf4c42d-a17c-4411-9a59-e81e7660a838.png">


## Summary

#### How many roles will need to be filled as the "silver tsunami" begins to make an impact?

#### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
