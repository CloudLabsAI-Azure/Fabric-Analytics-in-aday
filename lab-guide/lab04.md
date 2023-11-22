Microsoft Fabric

Fabric Analyst in a Day
Lab 4

Lab 0
# ![](../media/Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.001.png)

# Contents
[Introduction	3]()

[Lakehouse	3]()

[Lakehouse – How to query data using SQL	3]()

[Lakehouse – How to create a model – Relationships:	10]()

[Lakehouse – How to create a model – Measures:	16]()

[References	19]()

Introduction	2

Lakehouse	2

Explore Lakehouse	2

Lakehouse – How to create Power BI dataset	3

Lakehouse – How to create Shortcut:	4

Lakehouse – How to query data using SQL	7

Lakehouse – How to create a model – Relationships:	13

Lakehouse – How to create a model – Measures:	18


#
#
#
#
#
#
#
#
#
#
#
#
# <a name="_toc150852367"></a>**Introduction** 
We have data from various sources ingested in the Lakehouse. In this lab, you work with the data model. Typically, we performed modeling activities like creating relationships, adding measures, etc in Power BI Desktop. Here we will learn how to perform these modeling activities in the service. 

By the end of this lab, you will have learned: 

- Explore Lakehouse.
- Explore SQL view of Lakehouse.
- Explore Data modeling in Lakehouse.
# <a name="_toc150852368"></a>**Lakehouse**
### Explore Lakehouse

1. Let’s navigate back to the **Fabric workspace** you created in the earlier lab.
1. Navigate back to **Data Factory** screen.
1. You will see 3 types of lh\_FAIAD – Dataset, SQL endpoint and Lakehouse. We explored Lakehouse option in an earlier lab.  Select **lh\_FAIAD Dataset SQL analytics endpoint(default)** option to explore the SQL option. You will be navigated to SQL view of the explorer.. We will explore the other two options shortly.

![A screenshot of Data Factory Home](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.002.png)

You will be navigated to Details of lh\_FAIAD screen. This screen provides an overview of the artifacts available in the Lakehouse. Notice in the center pane, there are two option we saw in the previous screen, Lakehouse and SQL analytics endpoint are available here as well. On the left pane lists the tables that are available in the Lakehouse. On the top pane and menu you have options to share, visualize the data using Power BI, Excel, Paginated report. We will be creating a Power BI report in a later lab, first we need to model the data.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.003.png)

1. Select **lh\_FAIAD -> Lakhouse** option from the center pane.

You will be navigated to a different view of the Lakehouse. Notice on the top there is a SQL connection string. This connection string could be used to connect to the Lakehouse using other tools like SSMS, custom applications, etc. In the top menu there are options to Refresh, Share and view Lineage. We will explore some of these options later.

1. Select **Open** under **Open this Lakehouse** section.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.004.png)

You will be navigated to a screen where you can view the tables and a preview of the data from each table of the Lakehouse. There is option to add more data using Get data option. If you are familiar with notebooks, there is option to create one using Open notebook and write code (e.g. for Machine Learning or data transformation).
### Lakehouse – How to create Power BI dataset

![](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.005.png)

1. From the top menu, select **New semantic model**. A dialog opens where you can select tables to create a new dataset (suppose you need a subset of the tables to create a dataset). We are going to use all the tables; hence we are not going to create a new dataset.
1. Select **Cancel** to navigate back.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.006.png)
### Lakehouse – How to create Shortcut:

1. You can create shortcuts to Fabric, ADLS Gen2 and Amazon S3, like creating shortcuts in windows desktop. Select the **ellipsis** next to **Files** in the left panel.
1. Select **New shortcut**.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.007.png)

1. New shortcut dialog opens. Select **Azure Data Lake Storage Gen2**. We will create a connection to the ADLS Gen2 container to showcase the capabilities.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.008.png)

1. Under **Connection settings -> URL** enter **<https://stvnextblobstorage.dfs.core.windows.net/>.** Since you have created the connection to ADLS Gen2 before, your credentials are recognized. 
1. Select **Next**.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.009.png)

1. Under **Shortcut settings -> Shortcut Name** enter **Sales**.
1. Under **Target Location -> Sub Path** enter **/fabrikam-sales/Delta-Parquet-Format/**
1. Select **Create**.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.010.png)

1. You are** navigated back to the Lakehouse Explorer screen. Expand **Files** in the left panel.

![A screenshot of a computer

Description automatically generated](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.011.png)

1. Notice you have access to all the parquet files from ADLS Gen2. Similarly you can select **Sales** folder in the **center pane** to navigate through the folder structure. 
### <a name="_toc150852369"></a>Lakehouse – How to query data using SQL

If you would like to explore the data before creating a data model, you can use SQL to do so. Let’s look at two options to use SQL, the first one is developer friendly, and second option is for analysts. 

Let’s assume you want to quickly find out the Units sold by Supplier using SQL. We have two options, writing a SQL statement or using a visual to create the SQL statement.

1. On the **top right** of the screen, select **Lakehouse dropdown**.
1. Select **SQL analytics endpoint**. You will be navigated to SQL view of the explorer.

![](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.012.png)

Notice on the left panel, you can view the Tables. If you expand the tablestables, you can view the Columns that make up the table. Also, there are options to create SQL Views, Functions, Stored Procedures. If you have SQL background, feel free to explore these options. Let’s try to write a simple SQL query.

1. From the **top menu** select **New SQL query** or from the **bottom of the left panel** select **Query**. You will be navigated to SQL query view.

![A screenshot of SQL Query view](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.013.png)

1. **Paste** below SQL query in the **query window**. This query will return the units by Supplier Name. It is joining Sales table with Product and Supplier table to achieve this.

SELECT su.Supplier\_Name, SUM(Quantity) as Units

FROM dbo.Sales s

JOIN dbo.Product p on p.StockItemID = s.StockItemID

JOIN dbo.Supplier su on su.SupplierID = p.SupplierID

GROUP BY su.Supplier\_Name

1. Select **Run** to view the results.
1. Notice there is an option to	save this query as a View by selecting **Save as view**.
1. On the right **Explorer** panel, under **Queries section** notice this query is saved under **My queries** as **SQL query 1**. This provides an option to rename the query and save it for future use. There is also an option to view queries that are shared with you using **Shared queries** folder.

![A screenshot of SQL query screen](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.014.png)

1. We can also visualize the result of this query. **Highlight the query** in the query pane and select **Visualize results** from the **Results pane**.

![A screenshot of SQL query screen with result](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.015.png)

1. Visualize results dialog opens. Select **Continue**.

![A screenshot of Visualize results dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.016.png)

1. Familiar report view dialog opens. From the **Data** pane, expand **SQL query 1**.
1. Select **Supplier\_Name** and **Units** **fields**. Table visual is created by default.
1. Change the visual type by selecting **Stacked column chart** from the **Visualization** section.
1. **Resize** the visual as needed.

Chart type changes. Notice all the options available to format a visual in Power BI report are available here as well.

1. Select **Save as report**.
1. Save your report dialog opens. Enter “**Units by Supplier**” as the **report name.**
1. Make sure the destination workspace is **<your workspace name>.**
1. Select **Save.**

![A screenshot of Visualize results screen](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.017.png)

You will be navigated back to SQL analytics endpoint view. If you are not familiar with SQL, you can execute a similar query using visual query.

1. From the top menu select **New visual query**. A visual query pane opens.
1. From the **Explorer** pane, drag **Sales, Product and Supplier** tables to the visual query pane.
1. With **Sales** table selected, from the Visual query pane menu, select **Combine -> Merge queries**.

![A screenshot of Visual query screen](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.018.png)

1. Merge dialog opens. From the **Right table for merge** dropdown select **Product**.
1. Select **StockItemID** from both **Sales** and **Product** table. This is to merge Product and Sales tables.
1. From the **Join Kind**, select **Left Outer**.
1. Select **OK**.

![A screenshot of merge query dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.019.png)

1. In the **results** pane, click on the **double arrow** next to **Product** column.
1. Dialog opens, select **SupplierID** from the dialog.
1. Select **OK**.

![A screenshot of visual query dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.020.png)

1. Similarly, let’s merge Supplier table. With **Sales** table select, from the Visual query pane menu, select **Combine -> Merge queries**.
1. Merge dialog opens. From the **Right table for merge** dropdown select **Supplier**.
1. Select **SupplierID** from both **Sales** and **Supplier** table. This is to merge Supplier and Sales tables.
1. From the **Join Kind**, select **Left Outer**.
1. Select **OK**.

![A screenshot of merge query dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.021.png)

1. In the **results** pane, click on the **double arrow** next to **Supplier** column.
1. Dialog opens, select **Supplier\_Name** from the dialog.
1. Select **OK**. Notice in the Sales table all the **steps are recorded**.
1. Now we have the query ready, let’s view the result. Select **Visualize results** from the results pane.

![A screenshot of visual query dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.022.png)

1. **Visualize results dialog** opens which looks like Power BI window. From the **Data** pane in the right, select **Supplier\_Name and Quantity** fields.
1. This will create a table visual, with the result like the SQL query result from earlier. If you choose to, you can Save this report. Since we saved a similar report earlier, we are going to select **Cancel**.

![A screenshot of visualize report dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.023.png)
### <a name="_toc150852370"></a>Lakehouse – How to create a model – Relationships:

Ok now we are ready to build the model, build relationships between tables and create measures.

1. From the **bottom of the left panel** select **Model**. You will notice the center pane looks like the Model view we see in Power BI Desktop.
1. **Resize and rearrange** the tables as needed.
1. Let’s create a relationship between Sales and Reseller. Select **ResellerID** from **Sales** table and drag it over **ResellerID** in **Reseller** table.

![A screenshot of modeling view](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.024.png)

1. New relationship dialog opens. Make sure **Table 1** is **Sales** and **Column** is **ResellerID.**
1. Make sure **Table 2** is **Reseller** and **Column** is **ResellerID.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is single**.
1. Select **Ok**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.025.png)

1. Similarly, create a relationship between Sales and Date. Select **InvoiceDate** from **Sales** table and drag it over **Date** in **Date** table.
1. New relationship dialog opens. Make sure **Table 1** is **Sales** and **Column** is **InvoiceDate.**
1. Make sure **Table 2** is **Date** and **Column** is **Date.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is single**.
1. Select **Ok**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.026.png)

1. Similarly, create a **many to one** relationship between **Sales** and **Product**. Select **StockItemID** from **Sales** and **StockItemID** from **Product**.
1. Similarly, create a **many to one** relationship between **Sales** and **People**. Select **SalespersonPersonID** from **Sales** and **PersonID** from **People**. 

Your model should look like below.

![A screenshot of modeling view](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.027.png)

1. Now let’s create a relationship between Product and Supplier. Select **SupplierID** from **Product** table and drag it over **SupplierID** in **Supplier** table.
1. New relationship dialog opens. Make sure **Table 1** is **Product** and **Column** is **SupplierID.**
1. Make sure **Table 2** is **Supplier** and **Column** is **SupplierID.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is both**.
1. Select **Ok**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.028.png)

1. Similarly, create a **many to one** relationship with Cross filter direction as **Both** between **Product\_Details** and **Product**. Select **StockItemID** from **Product\_Details** and **StockItemID** from **Product**.
1. Now let’s create a relationship between Reseller and Geo. Select **PostalCityID** from **Reseller** table and drag it over **CityID** in **Geo** table.
1. New relationship dialog opens. Make sure **Table 1** is **Reseller** and **Column** is **PostalCityID.**
1. Make sure **Table 2** is **Geo** and **Column** is **CityID.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is both**.
1. Select **Ok**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.029.png)

1. Now let’s create a relationship between Customer and Reseller. Select **ResellerID** from **Customer** table and drag it over **ResellerID** in **Reseller** table.
1. New relationship dialog opens. Make sure **Table 1** is **Customer** and **Column** is **ResellerID.**
1. Make sure **Table 2** is **Reseller** and **Column** is **ResellerID.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is single**.
1. Select **Ok**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.030.png)**	

Your model should look like the screenshot below.

![A screenshot of modeling view](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.031.png)

1. Now let’s create a relationship between PO and Date. Select **Order\_Date** from **PO** table and drag it over **Date** in **Date** table.
1. New relationship dialog opens. Make sure **Table 1** is **PO** and **Column** is **Order.**
1. Make sure **Table 2** is **Date** and **Column** is **Date.**
1. Make sure **Cardinality is Many to one**.
1. Make sure **Cross filter direction is single**.
1. Select **OK**.

![A screenshot of New relationship dialog](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.032.png)

1. Similarly, create a **many to one** relationship between **PO** and **Product**. Select **StockItemID** from **PO** and **StockItemID** from **Product**.
1. Similarly, create a **many to one** relationship between **PO** and **People**. Select **ContactPersonID** from **PO** and **PersonID** from **People**. 

We are done creating all the relationships. Your model should look like below.

![A screenshot of modeling view](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.033.png)
### <a name="_toc150852371"></a>Lakehouse – How to create a model – Measures:
Let’s add a few measures which we need to create the Sales dashboard.

1. Select **Sales table** from the model view. We want to add the measures to the Sales table.
1. From the top menu, select **Home -> New Measure**. Notice formula bar is displayed.
1. Enter **Sales = SUM(Sales[Sales\_Amount])** in the **formula bar**.
1. Select the **check mark** in the formula bar or click Enter button.
1. In the Properties panel on the right, expand **Formatting** section.
1. From the **Format** dropdown select **Currency**.
1. Set **Decimal places** to **0**.

![A screenshot of modeling view with formula bar to add measure](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.034.png)

1. With the Sales table selected, select **New Measure** from the top menu.
1. Enter **Units = SUM(Sales[Quantity])** in the formula bar.
1. Select the **check mark** in the formula bar or click **Enter** button.
1. In the Properties panel on the right, expand **Formatting** section.
1. From the **Format** dropdown select **Whole number**.
1. Set the **Thousands Separator** to **Yes**.

![A screenshot of modeling view with formula bar to add measure](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.035.png)

1. With the Sales table selected, select **New Measure** from the top menu.
1. Enter **Orders = DISTINCTCOUNT(Sales[InvoiceID])** in the formula bar.
1. Select the **check mark** in the formula bar or click **Enter** button.
1. In the Properties panel on the right, expand **Formatting** section.
1. From the **Format** dropdown select **Whole number**.
1. Set the **Thousands Separator** to **Yes**.

![A screenshot of modeling view with formula bar to add measure](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.036.png)

1. With the Sales table selected, select **New Measure** from the top menu.
1. Enter **Avg Order = DIVIDE([Sales], [Orders])** in the formula bar.
1. Select the **check mark** in the formula bar or click **Enter** button.
1. Once the measure is saved, notice the Measure tools option on the top menu. Select **Measure tools**.
1. From the Format drop down, select **Currency**.

![A screenshot of modeling view with formula bar to add measure](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.037.png)

1. Follow similar steps to add following measures
   1. **GM = SUM(Sales[Line\_Profit])** formatted as **Currency, Decimal places of 2**
   1. **GM% = DIVIDE([GM], [Sales])** formatted as **Percentage, Decimal places of 2**
   1. **No of Customers = COUNTROWS(Customer)** formatted as **Whole Number**

We have created a data model; the next step is to set up a refresh schedule for the different data sources. We will do that in the following labs.











# <a name="_toc150777627"></a><a name="_toc150779083"></a><a name="_toc150852372"></a>**References**
Fabric Analyst in a Day introduces you to some of the key functions available in Microsoft Fabric. In the menu of the service, the Help section has links to some great resources.

![A screenshot of help options](Aspose.Words.0b1dbfd3-f5c1-48c3-9789-d82b03cb6b9e.038.png)

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


Version: 11.15.2023                                Copyright 2023 Microsoft   	                                                         27|Page 

Maintained by:  Microsoft Corporation 
