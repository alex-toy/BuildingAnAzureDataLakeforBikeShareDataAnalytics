# Building an Azure Data Lake for Bike Share Data Analytics

In this project, we'll build a data lake solution for Divvy bikeshare.

Divvy is a bike sharing program in Chicago, Illinois USA that allows riders to purchase a pass at a kiosk or use a mobile application to unlock a bike at stations around the city and use the bike for a specified amount of time. The bikes can be returned to the same station or to another station. The City of Chicago makes the anonymized bike trip data publicly available for projects like this where we can analyze the data. The dataset looks like this:

<img src="/pictures/data-model.jpeg" title="data model"  width="600">

The goal of this project is to develop a data lake solution using **Azure Databricks** using a lake house architecture. We will:

- Design a star schema based on the business outcomes listed below;
- Import the data into Azure Databricks using Delta Lake to create a Bronze data store;
- Create a gold data store in Delta Lake tables;
- Transform the data into the star schema for a Gold data store;

The business outcomes we are designing for are as follows:
1. Analyze how much time is spent per ride
- Based on date and time factors such as day of week and time of day
- Based on which station is the starting and / or ending station
- Based on age of the rider at time of the ride
- Based on whether the rider is a member or a casual rider
2. Analyze how much money is spent
- Per month, quarter, year
- Per member, based on the age of the rider at account start
3. EXTRA CREDIT - Analyze how much money is spent per member
- Based on how many rides the rider averages per month
- Based on how many minutes the rider spends on a bike per month

Hint: To view your DBFS files, enable the DBFS file browser in Databricks by going to Admin Console -> Workspace Settings -> Advanced

Hint: If you are going to use PySpark Pandas, make sure you create your Spark Cluster using a Databricks runtime >= 10.0




# Steps To Reproduce The project

## Task1 : Creating resources

1. Create an **Azure Databricks Workspace**
<img src="/pictures/databricks-workspace1.png" title="databricks workspace"  width="500">

2. Create a **Spark Cluster** inside the **Databricks Workspace**.
The real power of Databricks comes from the Apache Spark compute power available on-demand from Azure.
To add and monitor the Apache Spark compute power associated with our workspace, we access the Computer node from the main Databricks workspace menu.

Select **Compute** tab and hit  **Create Cluster**:

<img src="/pictures/cluster1.png" title="spark clsuter"  width="500">
<img src="/pictures/cluster2.png" title="spark clsuter"  width="500">