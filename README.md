# Library Management Database App (Azure Databricks, Azure Storage, PowerApps) - May 2023   
<img src='https://github.com/omkardabholkar/Library-Management-Database-App/assets/163356063/b27e5705-5cf9-4c70-a60b-7842558d261f' width=300> <img src='https://github.com/omkardabholkar/Library-Management-Database-App/assets/163356063/a5121ea8-1548-4e0e-b884-8911e9b04a04' width=300> <img src='https://github.com/omkardabholkar/Library-Management-Database-App/assets/163356063/bc6f6843-4547-4652-aade-12993acdc1d0' width=300>



## Link to the project  
[Library Managemnet App](https://video.syr.edu/media/t/1_ximhd1n20)
## Table of Contents
1. [Project Description](#project-description)
2. [Technologies Used](#technologies-used)
3. [Features](#features)
4. [Project Implementation](#project-implementation)
   - [Azure Databricks Workflow](#azure-databricks-workflow)
   - [Azure Storage Accounts](#azure-storage-accounts)
   - [PowerApps Interface](#powerapps-interface)
5. [Logical Diagram](#logical-diagram)
6. [Example SQL Code for Data Analysis](#example-sql-code-for-data-analysis)
## Project Description
In May 2023, I spearheaded the development of a cloud-based Library Management Database App, utilizing the robust capabilities of Azure technology to streamline library operations. This project was designed to enhance data security, efficiency, and accessibility by leveraging Azure Databricks for advanced data processing, Azure Storage Accounts for secure data storage, and a user-friendly interface created with PowerApps. The system was developed with the end-user in mind, incorporating Azure role-based access control to ensure data security and a PowerApps interface to minimize errors and improve data management workflows. The project covered the full software development lifecycle, from initial requirements gathering to deployment and user training, ensuring a comprehensive, secure, and efficient library management solution.

## Technologies Used
- **Azure Databricks**: For advanced data processing and analytics.
- **Azure Storage**: Secure data storage solution.
- **PowerApps**: Developed a user-friendly interface for efficient data management.
- **Azure Data Studio**: Integrated with PowerApps for enhanced data accessibility.

## Features
- **Cloud-based Library Management**: Leveraging Azure technologies for secure and efficient operations.
- **Enhanced Data Security**: Utilizing Azure role-based access control to safeguard sensitive information.
- **Streamlined Workflows**: A user-friendly PowerApps interface that minimizes errors and maximizes efficiency.
- **Comprehensive SDLC Involvement**: From requirements gathering to user training, ensuring a tailored and effective solution.

## Project Implementation
### Azure Databricks Workflow
- Utilized for processing and analyzing library transaction data to optimize inventory and user engagement.
### Azure Storage Accounts
- Served as the backbone for storing extensive library data securely and scalably.
### PowerApps Interface
- Designed to streamline library operations, from book checkouts to inventory management, through an intuitive application.
## Logical Diagram
![logical](https://github.com/omkardabholkar/Library-Management-Database-App/assets/163356063/784e0f9b-9072-4789-89e5-b9ffe21c8f5b)

## Example SQL Code for Data Analysis
Here's a snippet of SQL used within Azure Databricks to analyze library loan data, aimed at identifying trends in book borrowing and return rates, which informed inventory decisions.

```sql
-- SQL Snippet: Analyzing Library Loan Data
SELECT 
    books.title AS BookTitle,
    COUNT(loans.book_id) AS TotalLoans,
    AVG(DATEDIFF(loans.return_date, loans.loan_date)) AS AvgLoanDuration
FROM 
    loans
JOIN 
    books ON loans.book_id = books.id
GROUP BY 
    books.title
HAVING 
    TotalLoans > 50
ORDER BY 
    TotalLoans DESC, AvgLoanDuration DESC
LIMIT 10;
