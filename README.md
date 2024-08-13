# Hands-on-Lab-Querying-the-Data-Warehouse-Cubes-Rollups-Grouping-Sets-and-Materialized-Views-

This hands-on lab provide hands-on experience in advanced SQL query techniques using PostgreSQL. 

The lab focuses on teaching how to create grouping sets, rollups, and cubes for data aggregation and summarization, as well as how to implement and utilize Materialized Query Tables (Materialized views) for efficient data querying. These skills are essential for managing and analyzing large datasets, particularly in data warehousing and business intelligence contexts.

# Software Used in this Lab

To complete this lab you will utilize the PostgreSQL Database relational database service.

![image](https://github.com/user-attachments/assets/c6222840-2fcc-43df-b885-b0a8078b8c47)

# Objectives

The objectives of this lab were to learn how to create:

1. Grouping sets
2. Rollup
3. Cube
4. Materialized views

# Highlghts

GROUPING SETS, CUBE, and ROLLUP allow us to easily create subtotals and grand totals in a variety of ways. All these operators are used along with the GROUP BY operator.

GROUPING SETS operator allows us to group data in a number of different ways in a single SELECT statement.

The ROLLUP operator is used to create subtotals and grand totals for a set of columns. The summarized totals are created based on the columns passed to the ROLLUP operator.

The CUBE operator produces subtotals and grand totals. In addition, it produces subtotals and grand totals for every permutation of the columns provided to the CUBE operator.

# Data Used in this Lab
The following are the SQL data files used in this lab.

The production database contains:

Star Schema - Use the SQL script here to create tables in the Production database (https://drive.google.com/file/d/1pzGEQ5DV2EBiEeteqDSHK7G0nHMKUYBP/view?usp=sharing )
DimCustomer - Use the SQL script here to create the DimCustomer table (https://drive.google.com/file/d/1j8M0NqeQVYecoJCWHSblY5fmtRpD-zSr/view?usp=sharing)
DimMonth - Use the SQL script here to create the DimMonth table (https://drive.google.com/file/d/1kgfe5Wq9UlQj6FzCdezMGut0Om3AHGYr/view?usp=sharing)
FactBilling - Use the SQL script here to create the FactBilling table (https://drive.google.com/file/d/1lxCnZoFqL6J9HTBMRG3KTHIiCmD_ApR_/view?usp=sharing)

# Task A: Create a database

1. Open the pgAdmin Graphical User Interface
   
2. Once the pgAdmin GUI opens, click on the Servers tab on the left side of the page. You will be prompted to enter a password.

![image](https://github.com/user-attachments/assets/51aa4680-d798-48e5-98f6-5bfd5aa7772b)

3. Input your password, then click OK.

![image](https://github.com/user-attachments/assets/8d7f2d64-b412-49af-9558-67acbbcbb576)

4. You will then be able to access the pgAdmin GUI tool.

5. In the left tree-view, right-click on Databases> Create > Database.

![image](https://github.com/user-attachments/assets/5fdc2ff1-98d9-4c02-9573-94551be1a9bb)

6. In the Database box, type Production as the name for your new database, and then click Save. Proceed to Task B.

![image](https://github.com/user-attachments/assets/2949f399-0869-4c7c-b97c-a3e09d0b31d7)

# Task B: Create tables

Now, that you have your PostgreSQL service active and have created the Production database using pgAdmin, 
let's go ahead and create a few tables to populate the database and store the data that we wish to eventually upload into it.

1. Click on the Production database and in the top of the page go to Query tool and then click on Open File. Next a new page pops up called Select File. Click on Upload icon as shown in the screenshot.

![image](https://github.com/user-attachments/assets/f9d6901d-ca3c-4aef-b5f5-b9d6bdbffd84)

2. In the new blank page that appears drag and drop the star-schema.sql file inside the blank page. Once the star-schema.sql file is successfully loaded, click on the X icon on the right hand side of the page as shown in the screenshot.

![image](https://github.com/user-attachments/assets/b1cbecc0-d02a-4b8a-9e67-a53b7fd1727b)

3. Once you click on the X icon a new page appears with the file star-schema.sql. Select the star-schema.sql file from the list and click the Select tab.

![image](https://github.com/user-attachments/assets/9cdfe6d3-1996-4e1f-bd8b-cd2c59b8390c)

4. Once the file opens up click on the Run option to execute the star-schema.sql file.

![image](https://github.com/user-attachments/assets/b4e77188-c827-4839-a5a0-1493be2b037b)

5. Next, right-click on the Production database and click on the Refresh option from the dropdown.

![image](https://github.com/user-attachments/assets/f5641287-7a26-4ac5-a1df-89f84870d944)

6. After the database is refreshed the 3 tables (DimCustomer, DimMonth,FactBilling) are created under the Databases > Production > Schemas > Public > Tables.
   
![image](https://github.com/user-attachments/assets/b2f7f91a-a5c6-4eb4-8c29-dfc19f30693d)

# Task C: Load tables

1. Click on Query tool and then click Open file and click on Upload icon.

![image](https://github.com/user-attachments/assets/df383bdd-39a6-44f3-a390-ef5625d797d8)

2. In the new blank page that appears drag and drop the DimCustomer.sql file inside the blank page. Once the DimCustomer.sql file is successfully loaded.

3. Click on the small X icon on the right hand side of the page as shown in the screenshot.

![image](https://github.com/user-attachments/assets/648bfcdf-1398-4605-81cf-88cdc44649d8)

4. Once you click on the X icon a new page appears with the file DimCustomer.sql. Select the DimCustomer.sql file from the list and click on Select tab.

![image](https://github.com/user-attachments/assets/6c5c35d0-c88d-424f-b5cc-7ab9b2acb8f8)

5. Once the file opens up, click on the Run option to execute the DimCustomer.sql file.

![image](https://github.com/user-attachments/assets/e689f14a-a63e-4173-af17-e0ea6c8eab6a)

6. Note: Repeat the steps as given in Task C to upload the remaining sql files to insert data in DimMonth and FactBilling.

# Task D: Preview the tables you just uploaded

To preview the table, right-click on the table, navigate to View > First 100 Rows

DimCustomer Table

![image](https://github.com/user-attachments/assets/86308067-7bbe-412b-9209-350f093df2f4)

DimMonth Table

![image](https://github.com/user-attachments/assets/3d397bed-43df-440a-9bb3-7c4a463e0cc1)

FactBilling Table

![image](https://github.com/user-attachments/assets/dbb4dfc2-596e-40fa-96fe-4d27a5ac0d6f)

# Task E: Solve some SQL problems

- Problem 1 - Write a query using grouping sets

  To create a grouping set for three columns labeled year, category, and sum of billedamount, I issued the sql statement below:

      SELECT year,category, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY GROUPING SETS (year,category);

  The output can be seen in the image below:

  ![image](https://github.com/user-attachments/assets/85d0d53f-40a4-403a-9bfc-bb8431741d2b)

- Problem 2: Write a query using rollup

  To create a rollup using the three columns year, category and sum of billedamount, I issued the sql statement below:

      SELECT year,category, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY ROLLUP (year,category)
      ORDER BY year, category;

  The output can be seen in the image below:

  ![image](https://github.com/user-attachments/assets/eb87a3b5-dc3c-4249-964d-d52d97dd7035)

- Problem 3: Write a query using cube
  
  To create a cube using the three columns labeled year, category, and sum of billedamount, I issued the sql statement below:

      SELECT year,category, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY CUBE (year,category)
      ORDER BY year, category;

The output can be seen in the image below:

  ![image](https://github.com/user-attachments/assets/e16b46dd-f024-4f0c-9a17-365c196e8382)

# Task F: Create a Materialized Query Table(Materialized views)

In pgAdmin we can implement materialized views using Materialized Query Tables.

- Step 1: Create the Materialized views.

To create an Materialized views named countrystats, I executed the sql statement below:

      CREATE MATERIALIZED VIEW countrystats (country, year, totalbilledamount) AS
      (SELECT country, year, SUM(billedamount)
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY country,year);

![image](https://github.com/user-attachments/assets/d22ff524-656b-496a-a960-6abd786b5155)

- Step 2: Populate/refresh data into the Materialized views.
  
To populate the Materialized views countrystats, I executed the sql statement below:

      REFRESH MATERIALIZED VIEW countrystats;

Alternatively, right-click on the Materialized view and then select "Refresh". After refreshing, right-click again to chose View > First 100 Rows

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/605bcc21-75bc-4604-84f3-7aa31d0bc235)

- Step 3: Query the Materialized views.

Once an Materialized views is refreshed, you can query it.

To query the Materialized views countrystats, I executed the sql statement below:

      SELECT * FROM countrystats;

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/36177bfa-457c-4644-83e3-986922d70a5d)

# Task G: Create a grouping set for the columns year, quartername, sum(billedamount).

To tackle this task, I isssued the following query statement:

      SELECT year,quartername, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY GROUPING SETS (year,quartername);

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/166bd28f-7323-49f9-87a5-6dde5cf48150)

# Task H: Create a rollup for the columns country, category, sum(billedamount).

To tackle this problem, I isssued the following query statement:

      SELECT year,quartername, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY rollup(year, quartername)
      ORDER BY year, quartername;

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/ff93daf0-b62f-44e4-b408-0dbf7bf6b903)

# Task I: Create a cube for the columns year,country, category, sum(billedamount).

  To tackle this problem, I isssued the following query statement:
  
      SELECT year,quartername, sum(billedamount) AS totalbilledamount
      FROM "FactBilling"
      LEFT JOIN "DimCustomer"
      ON "FactBilling".customerid = "DimCustomer".customerid
      LEFT JOIN "DimMonth"
      ON "FactBilling".monthid="DimMonth".monthid
      GROUP BY CUBE (year, quartername)
      ORDER BY year, category;

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/d50646bb-b327-469c-b846-bce5c7462a0a)

# Task J: Create an Materialized views named average_billamount with columns year, quarter, category, country, average_bill_amount.

  To tackle this problem, I isssued the following query statement:

      CREATE MATERIALIZED VIEW average_billamount (year,quarter,category,country, average_bill_amount) AS
       (SELECT   year,quarter,category,country, avg(billedamount) AS average_bill_amount
       FROM "FactBilling"
       LEFT JOIN  "DimCustomer"
       ON "FactBilling".customerid =  "DimCustomer".customerid
       LEFT JOIN "DimMonth"
       ON "FactBilling".monthid="DimMonth".monthid
       GROUP BY year,quarter,category,country
       );

![image](https://github.com/user-attachments/assets/98c30271-cd3d-4835-aab9-41dcd8a559c8)

To populate the Materialized views countrystats, I executed the sql statement below:

      REFRESH MATERIALIZED VIEW countrystats;

Alternatively, right-click on the Materialized view and then select "Refresh". After refreshing, right-click again to chose View > First 100 Rows

The output can be seen in the image below:

![image](https://github.com/user-attachments/assets/b0334b34-4b76-4db5-8d41-a576aeee44d4)


