Microsoft Fabric

Fabric Analyst in a Day

Lab 3

# ![](../media/Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.001.png)

# Contents
  [Introduction	3]()
  
  [Dataflow Gen 2	3]()
  
  [How to connect to Snowflake and transform data:	3]()
  
  [How to connect to Dataverse and transform data:	10]()
  
  [How to connect to SharePoint and transform data:	16]()
  
  [References	22]()

Introduction	2

Dataflow Gen 2	2

How to connect to Snowflake and transform data:	2

How to connect to Dataverse and transform data:	8

How to connect to SharePoint and transform data:	15

# <a name="_toc150852388"></a>**Introduction** 
In our scenario, Campaign Supplier Data is in Snowflake, Customer Data is in Dataverse and Employee Data is in SharePoint. All these data sources are updated at different times. To minimize the number of data refreshes of Dataflows, we are going to create individual Dataflows for each of these data sources.

Note: Multiple data sources are supported in a single Dataflow.

By the end of this lab, you will have learned: 

- How to connect to Snowflake using Dataflow Gen2 and ingest data into Lakehouse.
- How to connect to SharePoint using Dataflow Gen2 and ingest data into Lakehouse.
- How to connect to Dataverse using Dataflow Gen2 and ingest data into Lakehouse

# <a name="_toc150852389"></a>**Dataflow Gen 2**
### <a name="_toc150852390"></a>How to connect to Snowflake and transform data:

1. Let’s navigate back to the **Fabric workspace** you created in the earlier lab.
1. Navigate back to **Data Factory** screen.
1. From the top menu, select **New -> Dataflow Gen2**.

![A screenshot to select New -> Dataflow Gen2]

You will be navigated to Dataflow page. Now that we are familiar with Dataflow, let’s go ahead and copy the queries from Power BI Desktop into Dataflow.

1. If you have not already opened it, open **FAIAD.pbix** located in **/Report** folder of the lab material. 
1. From the ribbon select **Home -> Transform data**. Power Query window opens. As you have noticed in the earlier lab, queries in the left panel are organized by data source.
1. Power Query window opens. From the left panel, under SnowflakeData folder **Ctrl+Select** or Shift+Select the following queries.
   1. SupplierCategories
   1. Suppliers
   1. Supplier
   1. PO
   1. PO Line Items
1. **Right click** and select **Copy**.

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.003.png)![A screenshot to copy queries from Power Query window](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.004.png)

1. Navigate back to the **browser**.
1. In the Dataflow pane select the center pane, enter **Ctrl+V** (current right click Paste is not supported).

Notice the 5 queries are pasted and now you have the Queries panel on the left. Since we do not have a connection created for Snowflake, you will see a warning message requesting you to configure the connection.

1. Select **Configure connection**.

![A screenshot of dataflow to configure connection](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.005.png)

1. Connect to data source dialog opens. In the **Connection** dropdown make sure, **Create new connection** is selected.
1. **Authentication kind** should be **Snowflake**.
1. **Username** should be **TE\_SNOWFLAKE**.
1. **Password** should be **)EHZ3h7!eGym8EWR**.
1. Select **Connect**.

![A screenshot to connect to data source](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.006.png)

Connection is established and you can view the data in the preview panel. Feel free to navigate through the Applied Steps of the queries. Basically Suppliers query has the details of suppliers and SupplierCategoreis as the name implies has supplier categories. These two tables are joined to create Supplier dimension, with the columns we need. Similarly, we have PO Line Items merged with PO to create the PO fact. Now we need to ingest Supplier and PO data into Lakehouse.

1. As mentioned earlier, we do are not Staging any of this data. So right click on **Supplier** query in the Queries pane and select **Enable staging** to remove the check mark.

![A screenshot to Enable Staging](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.007.png)

1. Similarly, right click on **PO** query. Select **Enable staging** to remove the check mark.
1. Note: We do not have to disable staging for the other 3 queries because Enable Load was disabled in Power BI Desktop (from where these queries were copied from).
1. Select **Supplier** query.
1. On the bottom right corner select “**+**” next to **Data destination**.
1. Select Lakehouse from the dialog.
1. ![A screenshot to select Data Destination for Supplier query](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.008.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.009.png)

1. Connect to data destination dialog opens. From the **Connection dropdown** select **Lakehouse (none)**.

   ![A screenshot to Connect to data destination]

1. Select **Next**.
1. Choose destination target dialog opens. Make sure the **New table radio button** is selected, since we are creating a new table.
1. We want to create the table in the Lakehouse we created earlier. In the left panel, navigate to **Lakehouse -> <your workspace name>.** 
1. Select **lh\_FAIAD.**
1. We can leave the table name as **Supplier**.
1. Select **Next**.

![A screenshot to Choose destination target](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.011.png)

1. Choose destination settings dialog opens. Every time Dataflow Gen2 is refreshed we would like to perform a full load. Make sure Update method is set to **Replace**.
1. Notice there is a warning. Lakehouse does not support column names with space in it. Select **Fix it**, to fix the warning.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.012.png) ![A screenshot to Choose destination settings](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.013.png)

1. Column mapping can be used to map dataflow columns to existing columns. In our case, it is a New Table. Hence, we can use the defaults. Select **Save settings**.
1. You will be navigated back to Power Query window. Notice on the bottom **right corner**, Data destination is set to Lakehouse.
1. Similarly, set up the Data Destination for PO query. Once it is done, your PO query should have Data Destination set to Lakehouse as show in the screenshot below.
1. ![A screenshot showing Data Destintion for PO](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.014.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.015.png)

1. On the bottom right corner, select **Publish**.From the top of the screen, select the arrow next to Dataflow1 to rename.
1. In the dialog, change the name to **df\_Supplier\_Snowflake.**
1. Click on Enter** to save the name change.
1. ![A screenshot showing renaming of Dataflow1](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.016.png)
1. On the bottom right corner, select **Publish**.
1. ![A screenshot to Publish Dataflow](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.017.png)

You will be navigated back to Data Factory screen. It may take a few moments for the Dataflow to Publish. 

Note: Sometimes, Dataflow name does not get updated. In this case, follow steps 37 to 40. If Dataflow name is updated, move to step 41.

1. Once Dataflow 1 is finished publishing, let’s rename it. Click on the **ellipsis** next to Dataflow 1. Select **Properties**.

![A screenshot to select Properties for Dataflow1]

1. Dataflow properties dialog opens. Change the **name** to **df\_Supplier\_Snowflake**.
1. In Description text box add **Dataflow to ingest Supplier data from Snowflake to Lakehouse**.
1. Select **Save**.

![A screenshot of Properties dialog of Dataflow1](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.019.png)

You will be navigated back to the Data Factory screen. Now let’s create a dataflow to bring in data from Dataverse.
### <a name="_toc150852391"></a>How to connect to Dataverse and transform data:

1. From the top menu, select **New -> Dataflow Gen2**.

![A screenshot to select New -> Dataflow Gen2]

You will be navigated to Dataflow page. Now that we are familiar with Dataflow, let’s go ahead and copy the queries from Power BI Desktop into Dataflow.

1. If you have not already opened it, open **FAIAD.pbix** located in **/Report** folder of the lab material. 
1. From the ribbon select **Home -> Transform data**. Power Query window opens. As you have noticed in the earlier lab, queries in the left panel are organized by data source.
1. Power Query window opens. From the left panel, under DataverseData folder **Ctrl+Select** the following queries.
   1. BabyBommer
   1. GenX
   1. GenY
   1. GenZ
   1. Customer
1. **Right click** and select **Copy**.

![A screenshot copy queries from Power Query window](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.020.png)

1. Navigate back to the Dataflow page in your **browser**.
1. In the Dataflow pane, enter **Ctrl+V** (current right click Paste is not supported).

Notice the 5 queries are pasted and now you have the Queries panel on the left. Since we do not have a connection created for Dataverse, you will see a warning message requesting you to configure the connection.

1. Select **Configure connection**.

![A screenshot Configure connection in Dataflow](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.021.png)

1. Connect to data source dialog opens. In the **Connection** dropdown make sure, **Create new connection** is selected.
1. **Authentication kind** should be **Organizational Account**.
1. Select **Connect**.

![A screenshot of Connect to data source](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.022.png)

Connection is established and you can view the data in the preview panel. Feel free to navigate through the Applied Steps of the queries. Customer data is available by Category, Baby Boomers, GenX, GenY and GenZ. This 4 queries are appended to create Customer query. Now we need to ingest Customer data into Lakehouse.

1. As mentioned earlier, we do are not Staging any of this data. So right click on **Customer** query in the Queries pane and select **Enable staging** to remove the check mark.

![A screenshot to disable Staging](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.023.png)

1. Select **Customer** query.
1. On the bottom right corner select “**+**” next to **Data destination**.
1. Select Lakehouse from the dialog.
1. ![A screenshot to configure Data Destination for Customer query](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.024.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.025.png)

1. Connect to data destination dialog opens. From the **Connection dropdown** select **Lakehouse (none)**.

   ![A screenshot of Connect to data destination][A screenshot to Connect to data destination]

1. Select **Next**.
1. Choose destination target dialog opens. Make sure the **New table radio button** is selected, since we are creating a new table.
1. We want to create the table in the Lakehouse we created earlier. In the left panel, navigate to **Lakehouse -> <your workspace name>.** 
1. Select **lh\_FAIAD.**
1. We can leave the table name as **Customer**.
1. Select **Next**.

![A screenshot of Choose destination target](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.026.png)

1. Choose destination settings dialog opens. Every time Dataflow Gen2 is refreshed we would like to perform a full load. Make sure Update method is set to **Replace**.
1. Notice there is a warning. Lakehouse does not support column names with space in it. Select **Fix it**, to fix the warning.
1. ![A screenshot of Choose destination settings](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.027.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.028.png)

1. Column mapping can be used to map dataflow columns to existing columns. In our case, it is a New Table. Hence, we can use the defaults. Select **Save settings**.
1. You will be navigated back to Power Query window. Notice on the bottom **right corner**, Data destination is set to Lakehouse.
1. On the bottom right corner, select **Publish**.
1. ![A screenshot to Publish queries](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.029.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.030.png)

You will be navigated back to Data Factory screen. It may take a few moments for the Dataflow to Publish. 

1. Dataflow 1 is the dataflow we were working in. Let’s rename it before we continue. Click on the **ellipsis** next to Dataflow 1. Select **Properties**.

![A screenshot to select Dataflow1 -> Properties]

1. Dataflow properties dialog opens. Change the **name** to df\_Customer\_Dataverse**	.
1. In Description text box add **Dataflow to ingest Customer data from Dataverse to Lakehouse**.
1. Select **Save**.

![A screenshot of Properties dialog of Dataflow1](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.032.png)

You will be navigated back to the Data Factory screen. Now let’s create a dataflow to bring in data from SharePoint.
### <a name="_toc150852392"></a>How to connect to SharePoint and transform data:

1. From the top menu, select **New -> Dataflow Gen2**.

![A screenshot to select New -> Dataflow Gen2]

You will be navigated to Dataflow page. Now that we are familiar with Dataflow, let’s go ahead and copy the queries from Power BI Desktop into Dataflow.

1. If you have not already opened it, open **FAIAD.pbix** located in **/Report** folder of the lab material. 
1. From the ribbon select **Home -> Transform data**. Power Query window opens. As you have noticed in the earlier lab, queries in the left panel are organized by data source.
1. Power Query window opens. From the left panel, under SharepointData folder **select** **People** query.
1. **Right click** and select **Copy**.

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.034.png) ![A screenshot to copy queries from Power Query window](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.035.png)

1. Navigate back to the Dataflow screen in the **browser**.
1. In the Dataflow pane, enter **Ctrl+V** (current right click Paste is not supported).

Notice the query is pasted and is available in the left panel. Since we do not have a connection created to SharePoint, you will see a warning message requesting you to configure the connection.

1. Select **Configure connection**.

![A screenshot to configure connection for People query in Dataflow](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.036.png)

1. Connect to data source dialog opens. In the **Connection** dropdown make sure, **Create new connection** is selected.
1. **Authentication kind** should be **Organizational Account**.
1. Select **Connect**.

![A screenshot of Connect to data source](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.037.png)

Connection is established and you can view the data in the preview panel. Feel free to navigate through the Applied Steps of the queries. Now we need to ingest People data into Lakehouse.

1. As mentioned earlier, we do are not Staging any of this data. So right click on **People** query in the Queries pane and select **Enable staging** to remove the check mark.

![A screenshot to disable Staging](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.038.png)

1. Select **People** query.
1. On the bottom right corner select “**+**” next to **Data destination**.
1. Select Lakehouse from the dialog.
1. ![A screenshot to configure Data Destination for People query](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.039.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.040.png)

1. Connect to data destination dialog opens. From the **Connection dropdown** select **Lakehouse (none)**.

   ![A screenshot of Connect to data destination]

1. Select **Next**.
1. Choose destination target dialog opens. Make sure the **New table radio button** is selected, since we are creating a new table.
1. We want to create the table in the Lakehouse we created earlier. In the left panel, navigate to **Lakehouse -> <your workspace name>.** 
1. Select **lh\_FAIAD.**
1. We can leave the table name as **People**.
1. Select **Next**.

![A screenshot of Choose destination target](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.042.png)

1. Choose destination settings dialog opens. Every time Dataflow Gen2 is refreshed we would like to perform a full load. Make sure Update method is set to **Replace**.
1. Notice there is a warning. Lakehouse does not support column names with space in it. Select **Fix it**, to fix the warning.
1. ![A screenshot of Choose destination settings](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.043.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.044.png)

1. Column mapping can be used to map dataflow columns to existing columns. In our case, it is a New Table. Hence, we can use the defaults. Select **Save settings**.
1. You will be navigated back to Power Query window. Notice on the bottom **right corner**, Data destination is set to Lakehouse.
1. On the bottom right corner, select **Publish**.
1. ![A screenshot of publishing People query](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.045.png)

![A screenshot of a computer

Description automatically generated](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.046.png)

You will be navigated back to Data Factory screen. It may take a few moments for the Dataflow to Publish. 

1. Dataflow 1 is the dataflow we were working in. Let’s rename it before we continue. Click on the **ellipsis** next to Dataflow 1. Select **Properties**.

   ![A screenshot of Dataflow1 -> Properties][A screenshot to select Properties for Dataflow1]

1. Dataflow properties dialog opens. Change the **name** to **df\_People\_SharePoint**.
1. In Description text box add **Dataflow to ingest People data from SharePoint to Lakehouse**.
1. Select **Save**.

![A screenshot of Dataflow1 dialog](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.047.png)

You will be navigated back to the Data Factory screen. We have now ingested all the data into Lakehouse. In the next lab, we will work with Lakehouse.

# <a name="_toc150777627"></a><a name="_toc150779083"></a><a name="_toc150852393"></a>**References**
Fabric Analyst in a Day introduces you to some of the key functions available in Microsoft Fabric. In the menu of the service, the Help section has links to some great resources.

![A screenshot of help options](Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.048.png)

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

Here are a few more resources that will help you with your next steps with Microsoft Fabric.

- See blog post to read the full [Microsoft Fabric preview announcement](https://aka.ms/build2023-fabricblog)
- [Sign up for the Microsoft Fabric free trial](https://aka.ms/try-fabric)
- [Visit the Microsoft Fabric website](https://aka.ms/microsoft-fabric)
- Learning path: [Get started with Microsoft Fabric - Training | Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/get-started-fabric/)
- Webinar series: [Microsoft Fabric Webinar Series](https://info.microsoft.com/ww-landing-introduction-to-microsoft-fabric-webinar-series.html?lcid=en-us)

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
- [Microsoft 365 data integration in Fabric blog](https://aka.ms/buil2023-m365-fabric-blog)
- [Dataverse and Microsoft Fabric integration blog](https://aka.ms/Dataverse-Fabric-Blog)
- Explore the [Fabric technical documentation](https://aka.ms/fabric-docs)
- Read the [free e-book on getting started with Fabric](https://aka.ms/fabric-get-started-ebook)
- Watch the [free Fabric webinar series](https://aka.ms/fabric-webinar-series)
- Explore Fabric through the [Guided Tour](https://aka.ms/Fabric-GuidedTour)

© 2023 Microsoft Corporation. All rights reserved.

By using this demo/lab, you agree to the following terms:

The technology/functionality described in this demo/lab is provided by Microsoft Corporation for purposes of obtaining your feedback and to provide you with a learning experience. You may only use the demo/lab to evaluate such technology features and functionality and provide feedback to Microsoft. You may not use it for any other purpose. You may not modify, copy, distribute, transmit, display, perform, reproduce, publish, license, create derivative works from, transfer, or sell this demo/lab or any portion thereof.

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED.

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A SIMULATED ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE DESCRIBED ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT REPRESENT FULL FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK. WE ALSO MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL ENVIRONMENT MAY ALSO BE DIFFERENT.

**FEEDBACK**. If you give feedback about the technology features, functionality and/or concepts described in this demo/lab to Microsoft, you give to Microsoft, without charge, the right to use, share and commercialize your feedback in any way and for any purpose. You also give to third parties, without charge, any patent rights needed for their products, technologies and services to use or interface with any specific parts of a Microsoft software or service that includes the feedback. You will not give feedback that is subject to a license that requires Microsoft to license its software or documentation to third parties because we include your feedback in them. These rights survive this agreement.

MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS WITH REGARD TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF MERCHANTABILITY, WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. MICROSOFT DOES NOT MAKE ANY ASSURANCES OR REPRESENTATIONS WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT THAT DERIVES FROM USE OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION CONTAINED IN THE DEMO/LAB FOR ANY PURPOSE.

**DISCLAIMER**

This demo/lab contains only a portion of new features and enhancements in Microsoft Power BI. Some of the features might change in future releases of the product. In this demo/lab, you will learn about some, but not all, new features.


Version: 11.15.2023                                Copyright 2023 Microsoft   	                                                         30|Page 

Maintained by:  Microsoft Corporation 

[A screenshot to select New -> Dataflow Gen2]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.002.png
[A screenshot to Connect to data destination]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.010.png
[A screenshot to select Properties for Dataflow1]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.018.png
[A screenshot to select Dataflow1 -> Properties]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.031.png
[A screenshot to select New -> Dataflow Gen2]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.033.png
[A screenshot of Connect to data destination]: Aspose.Words.12ee924b-aa27-4137-9af5-6e5d681a1e05.041.png
