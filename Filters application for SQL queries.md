# Filters application for SQL queries

## Project description

In this case, the organization was enhancing its system security, and my role was to ensure its protection. I was responsible for identifying potential security threats, investigating issues, and updating employee computers as necessary. Below are examples of how I have used SQL filters to carry out security-related tasks.

**NB**: On each step’s screenshot, the selected text shows my query, and the second part displays a portion of the output. At the end of the document, you will find some resources about table formats.

## After hours failed login attempts

I queried the log\_in\_attempts table and reviewed after hours login activity. To do so, I used filters in SQL to create a query that identifies all failed login attempts that occurred after 18:00. This query filters failed login attempts that occurred after 18:00.  
To achieve this, I first selected all data from the log\_in\_attempts table. Then, I applied a WHERE clause combined with an AND operator to refine the results, displaying only unsuccessful login attempts made after 18:00.

* The condition login\_time \> ‘18:00’ filters for login attempts occurring after 18:00.  
* The condition success \= ‘0’ ensures that only failed login attempts are included in the output.

![1 - I queried the log_in_attempts table and reviewed after hours login activity  To do so, I used filters in SQL to create a query that identifies all failed login attempts that occurred after 18_00](https://github.com/user-attachments/assets/518d34e3-9e11-41d8-b23a-4d42c045f98c)



## Login attempts on specific dates

A suspicious event occurred on 2022-05-09. To investigate this event, I reviewed all login attempts which occurred on this day and the day before. To do so, I used filters in SQL to create a query that identifies all login attempts that occurred on 2022-05-09 or 2022-05-08. 

To achieve this, I first selected all data from the log\_in\_attempts table. Then, I applied a WHERE operator with an OR operator to filter the results, ensuring only login attempts from these specific dates were included.

* The condition login\_date \= ‘2022-05-08’ filters for logins on **May 8, 2022**.  
* The condition login\_date \= ‘2022-05-09’ filters for logins on **May 9, 2022**.

![2 - A suspicious event occurred on 2022-05-09  To investigate this event, I reviewed all login attempts which occurred on this day and the day before  To do so, I used filters in SQL to create a query that iden (1)](https://github.com/user-attachments/assets/25d99bec-b15f-4438-b8b7-5b5eaef75503)


## Login attempts outside of Mexico

There has been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. So I investigated login attempts that occurred outside of Mexico. To do so, I filtered in SQL to create a query that identifies all login attempts that occurred in all countries other than Mexico.

To do this, I first selected all data from the log\_in\_attempts table. Then, I applied a WHERE with the NOT operator to exclude entries from Mexico. Since the dataset represents Mexico as both MEX and MEXICO, I used the LIKE operator with the pattern **'**MEX%**'** to filter out both variations. The **%** wildcard allows matching any additional characters following "MEX."

![3 - There has been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico  So I investigated login attempts that occurred outside of Mexico  To do so, I f](https://github.com/user-attachments/assets/e99158d6-e505-4685-ad2a-c93596ce1cbf)



## Employees in Marketing

The team wanted to perform security updates on specific employee machines in the Marketing department. I had to get information on these employees' machines and needed to query the employees table. To do so, I used filters in SQL to create a query that identifies all employees in the Marketing department located in the East building.

To do it, I first selected all data from the employees table. Then, I applied a WHERE clause with the AND operator to filter results, ensuring that only employees from the Marketing department and the East building were included.

* The condition department \= ‘Marketing’ filters for employees in the Marketing department.  
* The condition office LIKE ‘East%’ filters for employees in the East building, as the office column contains specific office numbers prefixed with "East." The **%** wildcard allows matching any additional characters after "East."

![4 - The team wants to perform security updates on specific employee machines in the Marketing department  I had to get information on these employees' machines and needed to query the employees table  To do so, I u](https://github.com/user-attachments/assets/dd1a3d39-9bf1-4cf7-b704-0e5664e2b8f3)



## Employees in Finance or Sales

The team then needed to perform a different security update on machines for employees in the Sales and Finance departments. So I used filters in SQL to create a query that identifies all employees in the Sales or Finance departments. 

To do it, I first selected all data from the employees table. Then, I applied a WHERE clause with the OR operator to include employees from both departments. I used the OR operator instead of AND because the goal is to retrieve employees from either department, not both.

* The condition department \= ‘Sales’ filters for employees in the **Sales** department.  
* The condition department \= ‘Finance’ filters for employees in the Finance department.

![5 - The team then needed to perform a different security update on machines for employees in the Sales and Finance departments  So I used filters in SQL to create a query that identifies all employees in the Sales ](https://github.com/user-attachments/assets/4588b0ed-15df-433a-97a3-76086c45cab1)


## All employees not in IT

The team finally needed to make one more update to employee machines. The employees who are in the Information Technology department already had this update, but employees in all other departments needed it. I used filters in SQL to create a query which identifies all employees not in the IT department.  
To achieve this, I first selected all data from the employees table. Then, I applied a WHERE with the NOT operator to exclude employees belonging to this department.

![6 - The team finally needed to make one more update to employee machines  The employees who are in the Information Technology department already had this update, but employees in all other departments needed it  I ](https://github.com/user-attachments/assets/1c12956a-2362-431e-95b7-8e97a57e3908)


## Summary

I applied filters to SQL queries to extract specific information about login attempts and employee devices. Using two distinct tables (log\_in\_attempts and employees) I leveraged AND, OR, and NOT operators to refine the data according to each task's requirements. Additionally, I utilized the LIKE operator along with the % wildcard to identify patterns efficiently.

# Table formats

This document describes how the tables used for this portfolio activity are organized. The organization database contains the following two tables: 

* log\_in\_attempts  
* employees

## log\_in\_attempts

The log\_in\_attempts table has the following columns:

* event\_id: The identification number assigned to each login event  
* username: The username of the employee  
* login\_date: The date the login attempt was recorded  
* login\_time: The time the login attempt was recorded  
* country: The country where the login attempt occurred  
* ip\_address: The IP address of that employee’s machine  
* success: The success of the login attempt; FALSE indicates a failed attempt

In the MariaDB shell, these columns are returned as:

![7- log_in_attempts](https://github.com/user-attachments/assets/e9b2fbe1-3a7e-432f-b8ff-2eb6b789df8c)


## employees

The employees table has the following columns:

* employee\_id: The identification number assigned to each employee  
* device\_id: The identification number assigned to each device used by the employee  
* username: The username of the employee  
* department: The department the employee is in  
* office: The office the employee is located in

In the MariaDB shell, these columns are returned as:

![8 - employees](https://github.com/user-attachments/assets/e8795a9e-4bbb-4fee-80bd-925101a7b45c)
