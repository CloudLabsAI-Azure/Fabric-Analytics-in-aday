Microsoft Fabric

Fabric Analyst in a Day
Lab 2


# ![](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.001.png)

# Contents
  [Introduction](#_toc150852522)
  
  [Dataflow Gen 2](#_toc150852523)
  
  [How to create Dataflow Gen 2:](#_toc150852524)
  
  [How to connect to ADLS Gen2 and transform data:](#_toc150852525)
  
  [How to copy Queries from Power BI Desktop – Option 1:](#_toc150852526)
  
  [How to copy Queries from Power BI Desktop – Option 2:](#_toc150852527)
  
  [How to configure Data Destination:](#_toc150852528)
  
  [Configure Dataflow to ingest remaining queries:](#_toc150852529)
  
  [References](#_toc150852530)

# <a name="_toc150852522"></a>**Introduction** 
In our scenario, Sales Data comes from the ERP System and is stored in an ADLS Gen 2 database. It gets updated at noon every day. We need to transform and ingest this data into Lakehouse and use it in our model. 

There are multiple ways to ingest this data. 

- Shortcuts: This does not provide a way to transform data. 
- Notebooks: This requires us to write code. It is a developer-friendly approach.
- Dataflow Gen2: You are probably familiar with Power Query or Dataflow Gen1. Dataflow Gen2, as the name indicates, is the newer version of Dataflow. It provides all the capabilities of Power Query/ Dataflow Gen1 with the added ability to transform and ingest data into multiple data sources. We are going to introduce this in the next couple of labs.
- Data Pipeline: This is an orchestration tool.Activities can be orchestrated to extract, transform, and ingest data. We will be using Data Pipeline to execute Dataflow Gen2 activity which in turn will perform extraction, transformation and ingestion. 
- We will start with Dataflow to create the connection to the data source and the necessary transformations. And then we will use Data Pipeline to orchestrate/execute the Dataflow.

By the end of this lab, you will have learned: 

- How to create Dataflow Gen2.
- How to connect to ADLS Gen2 using Dataflow Gen2 and transform data.
- How to ingest data into Lakehouse.

# <a name="_toc150852523"></a>**Dataflow Gen 2**
### <a name="_toc150852524"></a>How to create Dataflow Gen 2:

1. Let’s navigate back to the **Fabric workspace** you created in the earlier lab.
1. If you have not navigated away after the previous lab, you will be in the Lakehouse screen. If you have navigated away that is fine. Select **Data Engineering** from the bottom left of your screen.
1. A dialog box opens. Select **Data Factory**. Data Factory has workloads needed to extract, transform and ingest data.

  ![A screenshot of a dialog to select Data Factory experience](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.002.png)

1. You will be navigated to Data Factory page. Under New, select **Dataflow Gen2.** 

  ![A screenshot of a dialog to select Dataflow Gen2](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.003.png)

You will be navigated to Dataflow page. This screen will look familiar as it is like Dataflow Gen1 or Power Query. You will notice the options to connect to various data sources are available, along with the ability to transform data. Let’s connect to ADLS Gen2 data source and perform some transformations.
### <a name="_toc150852525"></a>How to connect to ADLS Gen2 and transform data:

1. From the ribbon, select **Home -> Get data -> More…** 

  ![A screenshot of Dataflow screen to select Get Data](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.004.png)

1. You will be navigated to Choose data source dialog. You can search for the data source by typing in the search box. Notice, on the left panel, there are options to use a Blank table or Blank query. You will also find a new option to Upload file. We will explore this option in a later lab. For now, let’s click on **View more ->** on the right corner of your screen. 

  ![A screenshot of Choose data source](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.005.png)

Now you can view all the available data sources. You have the option to filter the data sources by File, Database, Microsoft Fabric, Powe Platform, Azure etc.
  ![A screenshot of available data sources](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.006.png)

1. Select **Azure** from the filter to filter down to Azure data sources. 
1. Select **Azure Data Lake Storage Gen2**.

  ![A screenshot of select Azure Data Lake Storage Gen2](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.007.png)

1. You will be navigated to connection screen. You need to create a connection to ADLS Gen2 data source. Under **Connection Settings -> URL** enter <https://stvnextblobstorage.dfs.core.windows.net/>

  ![A screenshot of Connect to data source](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.008.png)

1. Select **Account Key** from the Authentication Type drop down.
1. Enter following in the **Account Key text box**: Lpwn8hQASMpe5r4F+VFXAvpnzKF9x9Kjt5GMvMCFWB0xCFuM4fyVwOW6rF200bTop3LpKpsIno/T+AStx6cz6w==

   ![A screenshot of Connect to data source](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.009.png)

1. Select **Next** on the bottom right of the screen.
1. Once the connection is established, you will be navigated to the Preview folder data screen. There are a lot of files in the ADLS Gen2 folder. We need data from a few of them. Select **Create** to create a connection to the folder.

   ![A screenshot of Preview folder data](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.010.png)

1. You are back in the Power Query dialog. This will be the connection to the root folder of ADLS. We will reference this query in subsequent queries. Let’s rename the query. In the **right panel**, under **Query settings -> Properties -> Name**, change the name to **ADLS Base Folder.**
1. All queries from Dataflow Gen2 are loaded to a Staging Lakehouse by default. Staging is used when we need to stage data to be used in further transformation before it is ready for consumption. As part of this lab, we will not be staging data. To disable this load, in the **left panel**, **right click on ADLS Base Folder** query. 
1. **Uncheck Enable Staging** option.

   ![A screenshot to disable Staging](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.011.png)

Data we need from ADLS Gen2 is located in fabrikam-sales/Delta-Parquet-Format folder. Within this folder, each dimension and fact are in a subfolder. E.g. Cities parquet file is located in fabrikam-sales/Delta-Parquet-Format/Application.Cities. 

1. Let’s add a filter. Select the **dropdown** for **Folder Path** column (you may have to scroll to the right). 
1. Select **Text filters -> Contains.**

  ![A screenshot to filter by Folder Path](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.012.png)

1. Filter rows dialog opens. Enter **fabrikam-sales/Delta-Parquet-Format** (case-sensitive) in the text box for contains.
1. Select **OK.**

  ![A screenshot of Filter rows dialog](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.013.png)


Notice there are two file formats in the folder, **json** and **parquet**.

**Parquet** is an open-source file format built to handle flat columnar storage data formats. Parquet operates well with complex data in large volumes and is known for its both performant data compression and its ability to handle a wide variety of encoding types.

**Json** file contains metadata like schema, data type of the parquet file.

1. We need only the parquet file as this has the data we need. Select the **Extension** column **dropdown**.
1. Uncheck **.json** so it is filtered down to .parquet files.
1. Select **OK**.

  ![A screenshot to filter out json files](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.014.png)

Now we have the Base query set up. We can reference this for all the queries from ADLS Gen2 source.

Sales data is available at Geography, Product, SalesPerson, Date granularity. Let’s first create a query to get Geography dimension. Geography data is available in three different files located in the following subfolders.

- Cities - Application.Cities
- Countries -Application.Countries
- State - Application.StateProvinces

We need to combine City, State and Country data from these three files to create the Geography dimension.

1. Let’s start with City. On the left panel, **right click on ADLS Base folder**. Select **Reference** to create a new query that references ADLS Base folder query.

   ![A screenshot to Reference ADLS Base folder](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.015.png)

1. Select the **dropdown** for the **Folder Path** column. 

![A screenshot to filter Folder Path](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.016.png)

1. Select **Text filters -> Contains**.
1. In the **Filter Rows dialog** enter **Application.Cities** (case-sensitive)**.**

   ![A screenshot of Filter Rows dialog](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.017.png)

1. Select **OK**.
1. Data will be filtered to a single row. Select **Binary** under **Content** column.

   ![Screenshot of ADLS Base Folder(2)](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.018.png)

1. Notice you will see all the City details. In the **right panel**, under **Query settings -> Properties -> Name**, change the name to **Cities.** 

   ![A screenshot to Rename query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.019.png)

In the right panel, under Applied steps notice all the steps are registered. This behavior is like Power Query. Now let’s follow a similar process to create **Country** query.

1. On the left panel, **right click on ADLS Base folder**. Select **Reference** to create a new query that references ADLS Base folder query.

   ![A screenshot to reference ADLS Base Folder](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.020.png)

1. Select the **dropdown** for the **Folder Path** column. 
1. Select **Text filters -> Contains**.

  ![A screenshot to filter by Folder Path](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.021.png)

1. In the **Filter Rows dialog** enter **Application.Countries** (case-sensitive).
1. Select **OK**.

  ![A screenshot of Filter rows dialog](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.022.png)

1. Data will be filtered to a single row. Select **Binary** under **Content** column.

   ![Screenshot of ADLS Base Folder(2)](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.023.png)

1. Notice you will see all the Country details. In the **right panel**, under **Query settings -> Properties -> Name**, change the name to **Countries**.

   ![A screenshot to Rename query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.024.png)

We need to bring in State next. But the steps are getting repetitive. We already have the queries in the Power BI Desktop file. Let’s see if we can copy over the queries from there.

**Note:** Please wait for the Countries query to finish execution before moving to the next step. This may take a couple of minutes.
### <a name="_toc150852526"></a>How to copy Queries from Power BI Desktop – Option 1:
1. If you have not already opened it, open **FAIAD.pbix** located in **/Report** folder of the lab material. 
1. From the ribbon select **Home -> Transform data**. Power Query window opens. As you have noticed in the earlier lab, queries in the left panel are organized by data source.

  ![ screenshot Power BI Desktop report](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.025.png)
  
  ![A screenshot of Power BI Desktop report.](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.026.png)

1. From the left panel, under ADLSData folder, right click **States** query and select **Copy.**

  ![A screenshot Power Query window](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.027.png)

1. Navigate back to the **browser**. You should be in the Dataflow we were working on.
1. On the left panel under select **Queries** panel and enter **Ctrl+V** (current right click Paste is not supported).

   ![A screenshot Dataflow queries](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.028.png)

Notice ADLS Base Folder (2) is copied as well. This is because States refers to ADLS Base Folder in Power BI Desktop. But we already have ADLS Base Folder. Let’s solve this.

1. Select **States** query.
1. From the **right panel**, under **Applied** **Steps**, select **Source**.

   ![A screenshot of States query Source step](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.029.png)

1. In the formula bar, change from **#"ADLS Base Folder (2)"** to **#"ADLS Base Folder"**. 
1. Select the **check mark** next to the formula bar or hit **enter**.

   ![A screenshot of States query Source step after updating formula bar](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.030.png)

1. Now we can remove ADLS Base Folder (2). In the left panel, under **Queries** section right click **ADLS Base Folder (2)** query and select **Delete**.

   ![A screenshot of delete ADLS Base Folder (2) delete](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.031.png)

1. Delete query dialog appears. Select **Delete** to confirm.

### <a name="_toc150852527"></a>How to copy Queries from Power BI Desktop – Option 2:
Now we need to merge these queries to create Geography dimension. Let’s copy the query again from the Power BI Desktop file. This time let’s copy the code from Advanced Editor.

1. Navigate back to the **Power Query window** of the Power BI Desktop file.
1. From the left panel, under **Queries** select **Geo** query in ADLSData folder.
1. From the ribbon select **Home -> Advanced Editor**.

![A screenshot of Power Query window from Power BI Desktop](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.032.png)

1. Advanced Editor window open. **Highlight all the text** in Advanced Editor
1. Right click and select **Copy**.

   ![A screen shot of Advanced Editor](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.033.png)

1. Select **X** on the top right corner of the window or select **Done** to **close** Advanced Editor window.
1. **Navigate** back to the Dataflow window in the **browser**. 
1. From the ribbon **Get Data -> Blank query.**

![A screenshot of Get Data -> Blank Query in Dataflow](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.034.png)

1. Advanced Editor dialog opens. **Highlight all the text** in the editor.
1. Select **Delete** on your keyboard to Delete all the text.
1. Advanced Editor should be blank. Now enter **Ctrl+V** to paste the content you had copied from the Power BI Desktop’s Advanced Editor.
1. Select **Next**.

` `![A screenshot of Advanced Editor](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.035.png)

1. Now we have the Geo dimension. Let’s rename the query. In the **right panel**, under **Query settings -> Properties -> Name**, change the name to **Geo**.

Let’s walk through the steps to understand how Geo is created. From the right panel, under Applied Steps, select Source. If you look at the formula bar or click on Settings you will notice that the Source of this query is a join between Cities and States. As you walk through the steps, you will notice the result of the first join is in turn joined with Countries. So, all three of the queries are used to create Geo dimension.

  ![A screenshot of Formula bar for Geo query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.036.png)
### <a name="_toc150852528"></a>How to configure Data Destination:

Now we have a dimension let’s ingest this data into Lakehouse. This is the new feature available in Dataflow Gen2.

1. As mentioned earlier, we are not Staging any of this data. So right click on **Cities** query and select **Enable staging** to remove the check mark.

  ![A screenshot to disable Staging](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.037.png)

1. Follow the same steps for **Countries**, **States and Geo** queries to remove the check mark next to **Enable staging**.
1. Select **Geo** query.
1. On the bottom right corner select “**+**” next to **Data destination**.
1. Select Lakehouse from the dialog.

  ![A screenshot select Data Destination](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.038.png)


1. Connect to data destination dialog opens. We need to create a new Connection to the Lakehouse. With **Create new connection** selected in the **Connection dropdown** and **Authentication kind** set to **Organizational account**, select **Next**.

  ![A screenshot of Connect to data destination](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.039.png)

1. Once connection is created, Choose destination target dialog opens. Make sure the **New table radio button** is selected, since we are creating a new table.
1. We want to create the table in the Lakehouse we created earlier. In the left panel, navigate to **Lakehouse -> <your workspace name>.** 
1. Select **lh\_FAIAD.**
1. We can leave the table name as **Geo**.
1. Select **Next**.

  ![A screenshot to Choose destination target](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.040.png)

1. Choose destination settings dialog opens. Every time Dataflow Gen2 is refreshed we would like to perform a full load. Make sure Update method is set to **Replace**.
1. Notice there is a warning. Lakehouse does not support column names with space in it. Select **Fix it**, to fix the warning.

   Notice you also have an option to Append data. If you select this, every time dataflow is refreshed, new data is appended to existing data.

![A screenshot to Choose destination settings](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.041.png)

1. Column mapping can be used to map dataflow columns to existing columns. In our case, it is a New Table. Hence, we can use the defaults. Select **Save settings**.

**Note:** If you do not want some of the columns in the Lakehouse, use the check box to the right of Source column to uncheck the columns you do not need.

1. You will be navigated back to Power Query window. Notice on the bottom **right corner**, Data destination is set to Lakehouse.
1. Let’s Publish these queries so we can review	 the Lakehouse. We will come back to add more queries. On the bottom right corner, select **Publish**.

  ![A screenshot to Publish Dataflow](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.042.png)

1. You will be navigated back to Data Factory screen. It may take a few moments for the Dataflow to Publish. Once done, select **lh\_FAIAD Lakehouse.**

   ![A screenshot to select Lakehouse](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.043.png)

1. You will be navigated to Lakehouse Explorer screen. In the left panel, expand **lh\_FAIAD -> Tables**.
1. Notice we have **Geo** table in the Lakehouse now. Expand **Geo** and notice all the columns. 
1. **Select Geo** table and the data preview will open in the right panel.

  ![A screenshot to explore Lakehouse tables](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.044.png)

There is a SQL Endpoint as well, which can be used to query this table. We will look at this option in a later lab. Now that we know Geo data is landed in Lakehouse, let’s bring the rest of the data from ADLS.
### <a name="_toc150852529"></a>Configure Dataflow to ingest remaining queries:

1. In the left menu bar, select **<your workspace name>** to be navigated back to the **workspace**.
1. We are working with Dataflow 1. Let’s rename it before we continue. Click on the **ellipsis** next to Dataflow 1. Select **Properties**.

  ![A screenshot to select Dataflow1 Properties](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.045.png)

1. Dataflow properties dialog opens. Change the **name** to **df\_Sales\_ADLS**.

Note: We are prepending Dataflow name with “**df**”. This will make it easy to search and sort.

1. In Description text box add, **Dataflow to ingest Sales Data from ADLS to Lakehouse**.
1. Select **Save**.

   ![A screenshot Dataflow Properties dialog](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.046.png)

1. You will be navigated back to the Data Factory screen. Select Dataflow **df\_Sales\_ADLS** to navigate back into the dataflow.

  ![A screenshot to select df_Sales_ADLS](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.047.png)

To make things easy, let’s see if we can copy over the queries from Power BI Desktop.

1. If you have not already opened it, open **FAIAD.pbix** located in **/Report** folder of the lab material.
1. From the ribbon select **Home -> Transform**. Power Query window opens.
1. From the **Queries** panel on the left, **Ctrl+Select** following queries from **ADLSData**.
   1. **Product**
   1. **Product Groups**
   1. **Product Item Group**
   1. **Product Details**
   1. **Invoice**
   1. **InvoiceLineItems**
   1. **Sales**
   1. **BuyingGroup**
   1. **Reseller**
   1. **Date**

  ![A screenshot to copy queries from Power Query window](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.048.png)

1. **Right click** and select **Copy**.
1. Navigate back to **df\_Sales\_ADF** Dataflow window of the **browser**.
1. On the left panel under select **Queries** panel and enter **Ctrl+V** (current right click Paste is not supported).

  ![A screenshot to paste queries in Dataflow](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.049.png)

Now let’s follow the steps we took earlier. Remove the reference to ADLS Base Folder (2) and use ADLS Base Folder.

1. Select **Product** query.
1. From the right panel, under **Applied Steps**, select **Source**.
1. In the formula bar, change from **#"ADLS Base Folder (2)" to #"ADLS Base Folder"**.
1. Select the **check mark** next to the formula bar or hit enter.

  ![A screenshot of formula bar for Product query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.050.png)

1. Perform the same action of replacing reference to **#"ADLS Base Folder (2)"** with **#"ADLS Base Folder"** for the following queries.
   1. **Product Groups**
   1. **Product Item Group**
   1. **Product Details**
   1. **Invoice**
   1. **InvoiceLineItems**
   1. **BuyingGroup**
   1. **Reseller**
   1. **Date**
1. Now we can remove ADLS Base Folder (2). In the left panel, under Queries section **right click ADLS Base Folder (2)** query and select **Delete**.
1. Delete query dialog appears. Select **Delete** to confirm.

  ![A screenshot to Delete ADLS Base Folder (2) query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.051.png)

1. As mentioned earlier, we do are not Staging any of this data. So **right click** on following queries and select **Enable staging** to remove the check mark.
   1. Product
   1. Product Details
   1. Reseller
   1. Date
   1. Sales

**Note**: If load is disabled in Power BI Desktop, we do not have to disable staging in Dataflow. Hence, we do not have to disable staging for Product Item Group, Product Groups, etc.

  ![A screenshot to disable Staging](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.052.png)

Now let’s ingest this data into Lakehouse

1. Select **Product** query.
1. On the bottom right corner select “**+**” next to **Data destination**.
1. Select **Lakehouse** from the dialog.

` `![A screenshot configure Data Destination for Product query](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.053.png)

1. Connect to data destination dialog opens. From the **Connection dropdown** select **Lakehouse (none)**.

   ![A screenshot of Connect to data destination](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.054.png)

1. Select **Next**.
1. Choose destination target dialog opens. Make sure the **New table radio button** is selected, since we are creating a new table.
1. We want to create the table in the Lakehouse we created earlier. In the left panel, navigate to **Lakehouse -> <your workspace name>.** 
1. Select **lh\_FAIAD.**
1. We can leave the table name as **Product**.
1. Select **Next**.

   ![A screenshot of Choose destination target](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.055.png)

1. Choose destination settings dialog opens. Every time Dataflow Gen2 is refreshed we would like to perform a full load. Make sure Update method is set to **Replace**.
1. Notice there is a warning. Lakehouse does not support column names with space in it. Select **Fix it**, to fix the warning.

  ![A screenshot of Choose destination settings](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.056.png)

1. Column mapping can be used to map dataflow columns to existing columns. In our case, it is a New Table. Hence, we can use the defaults. Select **Save settings**.
1. You will be navigated back to Power Query window. Notice on the bottom **right corner**, Data destination is set to **Lakehouse**.
1. Similarly, set the **Data Destination** for the following queries.
   1. **Product Details**
   1. **Reseller**
   1. **Date**
   1. **Sales**

We have a data flow that ingests data from ADLS into Lakehouse. Let’s go ahead and publish this dataflow. 

1. Select **Publish** in the bottom right corner.

  ![A screenshot of dataflow to Publish](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.057.png)

You will be navigated back to Data Factory page. It will take a few minutes for the dataflow to refresh.

In the next lab, we will ingest data from the other data sources.

# <a name="_toc150777627"></a><a name="_toc150852530"></a>**References**
Fabric Analyst in a Day introduces you to some of the key functions available in Microsoft Fabric. In the menu of the service, the Help section has links to some great resources.

  ![A screenshot of help options](../media/Aspose.Words.d9e40fe6-e088-40f4-b33d-59abff8ed5bb.058.png)

Here are a few more resources that will help you with your next steps with Microsoft Fabric.

- See blog post to read the full [Microsoft Fabric GA announcement](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Explore Fabric through the [Guided Tour](https://aka.ms/Fabric-GuidedTour)
- Sign up for the [Microsoft Fabric free trial](https://aka.ms/try-fabric)
- Visit the [Microsoft Fabric website](https://aka.ms/microsoft-fabric)
- Learn new skills by exploring the [Fabric Learning modules](https://aka.ms/learn-fabric)
- Explore the [Fabric technical documentation](https://aka.ms/fabric-docs)
- Read the [free e-book on getting started with Fabric](https://aka.ms/fabric-get-started-ebook)

Read the more in-depth Fabric experience announcement blogs:

- [Data Factory experience in Fabric blog](https://aka.ms/Fabric-Data-Factory-Blog) 
- [Synapse Data Engineering experience in Fabric blog](https://aka.ms/Fabric-DE-Blog) 
- [Synapse Data Science experience in Fabric blog](https://aka.ms/Fabric-DS-Blog) 
- [Synapse Data Warehousing experience in Fabric blog](https://aka.ms/Fabric-DW-Blog) 
- [Synapse Real-Time Analytics experience in Fabric blog](https://aka.ms/Fabric-RTA-Blog)
- [Power BI announcement blog](https://aka.ms/Fabric-PBI-Blog)
- [Data Activator experience in Fabric blog](https://aka.ms/Fabric-DA-Blog) 
- [Administration and governance in Fabric blog](https://aka.ms/Fabric-Admin-Gov-Blog)
- [OneLake](https://aka.ms/Fabric-OneLake-Blog)[ in Fabric blog](https://aka.ms/Fabric-OneLake-Blog)
- [Dataverse and Microsoft Fabric integration blog](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation. All rights reserved.

By using this demo/lab, you agree to the following terms:

The technology/functionality described in this demo/lab is provided by Microsoft Corporation for purposes of obtaining your feedback and to provide you with a learning experience. You may only use the demo/lab to evaluate such technology features and functionality and provide feedback to Microsoft. You may not use it for any other purpose. You may not modify, copy, distribute, transmit, display, perform, reproduce, publish, license, create derivative works from, transfer, or sell this demo/lab or any portion thereof.

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED.

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A SIMULATED ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE DESCRIBED ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT REPRESENT FULL FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK. WE ALSO MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL ENVIRONMENT MAY ALSO BE DIFFERENT.

**FEEDBACK**. If you give feedback about the technology features, functionality and/or concepts described in this demo/lab to Microsoft, you give to Microsoft, without charge, the right to use, share and commercialize your feedback in any way and for any purpose. You also give to third parties, without charge, any patent rights needed for their products, technologies and services to use or interface with any specific parts of a Microsoft software or service that includes the feedback. You will not give feedback that is subject to a license that requires Microsoft to license its software or documentation to third parties because we include your feedback in them. These rights survive this agreement.

MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS WITH REGARD TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF MERCHANTABILITY, WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. MICROSOFT DOES NOT MAKE ANY ASSURANCES OR REPRESENTATIONS WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT THAT DERIVES FROM USE OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION CONTAINED IN THE DEMO/LAB FOR ANY PURPOSE.

**DISCLAIMER**

This demo/lab contains only a portion of new features and enhancements in Microsoft Power BI. Some of the features might change in future releases of the product. In this demo/lab, you will learn about some, but not all, new features.
Version: 11.15.2023                                Copyright 2023 Microsoft   	                                                         33|Page 

Maintained by:  Microsoft Corporation 
