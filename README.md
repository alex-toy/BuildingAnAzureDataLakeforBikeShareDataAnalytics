# Building an Azure Data Lake for Bike Share Data Analytics

In this project, we'll build a data lake solution for Divvy bikeshare.

Divvy is a bike sharing program in Chicago, Illinois USA that allows riders to purchase a pass at a kiosk or use a mobile application to unlock a bike at stations around the city and use the bike for a specified amount of time. The bikes can be returned to the same station or to another station. The City of Chicago makes the anonymized bike trip data publicly available for projects like this where we can analyze the data. The dataset looks like this:

<img src="/pictures/data-model.jpeg" title="data model"  width="400">

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
3. Analyze how much money is spent per member
- Based on how many rides the rider averages per month
- Based on how many minutes the rider spends on a bike per month

Hint: To view your DBFS files, enable the DBFS file browser in Databricks by going to Admin Console -> Workspace Settings -> Advanced

Hint: If you are going to use PySpark Pandas, make sure you create your Spark Cluster using a Databricks runtime >= 10.0




# Steps To Reproduce The project

## Step 1 : Create resources

1. Create an **Azure Databricks Workspace**
<img src="/pictures/databricks-workspace1.png" title="databricks workspace"  width="500">

2. Create a **Spark Cluster** inside the **Databricks Workspace**.
The real power of Databricks comes from the Apache Spark compute power available on-demand from Azure.
To add and monitor the Apache Spark compute power associated with our workspace, we access the Computer node from the main Databricks workspace menu. Select **Compute** tab and hit  **Create Cluster**:

<img src="/pictures/cluster1.png" title="spark cluster"  width="700">
<img src="/pictures/cluster2.png" title="spark cluster"  width="500">

3. Make sure you have the right setting in order to see DBFS
<img src="/pictures/setting1.png" title="setting"  width="200">
<img src="/pictures/setting2.png" title="setting"  width="500">



## Step 2 : Ingest Data into Azure Databricks

This method is useful for one time ingestion of data into the **DBFS**. This is not the preferred method for setting up a data pipeline that needs to run regularly. For that, you should integrate other Azure tools such as **Azure Data Factory** or **Azure Functions** for getting data into **Azure Databricks**.

1. Go to **Data** tab and upload your data files to *FileStore/tables*
<img src="/pictures/upload_data1.png" title="upload data"  width="500">
<img src="/pictures/upload_data2.png" title="upload data"  width="500">

You should then see your files in the filestore
<img src="/pictures/upload_data3.png" title="upload data"  width="500">



## Step 3 : ELT on Notebook

1. Go to **Workspace** tab and create notebook. Make sure you choose the right cluster.
<img src="/pictures/notebook1.png" title="notebook"  width="300">

2. Create dataframes for all four files riders, stations, payments and trips.
<img src="/pictures/dataframe.png" title="dataframe"  width="500">

3. Write all your data out to delta
<img src="/pictures/delta.png" title="delta"  width="500">

Check that your data has been created as tables
<img src="/pictures/delta2.png" title="delta"  width="500">

3. Create **Star Model** tables
<img src="/pictures/delta.png" title="delta"  width="500">
