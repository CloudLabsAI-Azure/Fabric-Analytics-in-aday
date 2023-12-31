# Microsoft Fabric - Fabric Analyst in a Day

![tesb](../media/Aspose.Words.2ed70cc0-be12-4074-8ce5-48f6b0305ec4.001.png)

Lab Prerequisites 

# Contents
[Document Structure](#DocumentStructure)

[Scenario / Problem Statement](###Scenario/ProblemStatement)

[Overview of Power BI Desktop Report](#OverviewofPowerBIDesktopReport)

[References](#References)

# Document Structure

The lab includes steps for the user to follow along together with associated screenshots that provide a visual aid. In the screenshots, sections are highlighted with red or orange boxes to indicate the area the user needs to focus on.

### Scenario / Problem Statement

Fabrikam, Inc. is a wholesale novelty goods distributor. As a wholesaler, Fabrikam’s customers are mostly companies who resell to individuals. Fabrikam sells to retail customers across the United States including specialty stores, supermarkets, computing stores and tourist attraction shops. Fabrikam also sells to other wholesalers via a network of agents who promote the products on Fabrikam’s behalf. While all of Fabrikam's customers are currently based in the United States, the company is intending to push for expansion into other countries/regions.

You are a Data Analyst in the Sales team. You collect, clean, and interpret data sets to solve business problems. You also put together visualizations like charts and graphs, write reports, and present them to the decision-makers in the organization.

In order to draw valuable insights from the data, you pull data from multiple systems, clean it and mash it up together. You pull data from the following sources:

- Sales Data: This data comes from the ERP System and is stored in an ADLS Gen 2 database or Databricks. It gets updated at noon every day.
- Supplier Data: This data comes from the different suppliers and is stored in a Snowflake database. It gets updated at midnight every day.
- Customer data: this data comes from Customer Insights and is stored in Dataverse. The data is always up to date.
- Employees Data: This data comes from the HR system, it is stored as an export file in a SharePoint folder.  It gets updated every morning at 9 AM.   

   ![A diagram of data flow](../media/Picture3.png)

You currently build a dataset on Power BI premium that pulls the data from the above source systems in order to satisfy your reporting needs as well as provide end users the ability to self-serve. You use Power Query to update your dataset. 

You are facing the following challenges:

- You need to refresh your dataset at least 3 times a day to accommodate the different update times for the different data sources.
- Your refreshes take a long time as you need to do a full refresh every time to capture any updates that happened to the source systems.
- Any errors in any of the data sources that you are pulling from will result in your dataset refresh breaking. A lot of times the employee file doesn’t upload on time resulting in your dataset refresh breaking. 
- It takes a very long time to make any changes to your data model as Power Query takes a long time to refresh your previews given the large data sizes and complex transformations. 
- You need to have a Windows PC to use Power BI Desktop even though the corp standard is Mac. 



You heard about Fabric and you decided to try to use Fabric to see if it will address the challenges you are facing.

## Overview of Power BI Desktop Report

Before we start with Fabric, let’s look at the current Report in Power BI Desktop to understand the transformations and the model.

1. Open the **FAIAD.pbix** located in **reports/FAIAD.pbix** folder of the lab material. The file will open in Power BI Desktop.

   The report analyzes Sales for Fabrikam. KPIs are listed on the left top of the page. The remaining visuals highlight Sales over time, by Territory, by Product Group, Resellers. 

    ![A screenshot of Power BI Desktop report](../media/Picture4.png)

1. **Note:** In this training, we are focusing on the data acquisition, transformation and modeling using tools available in Fabric. We will not be focusing on report development or navigation. Let’s spend a couple of minutes to understand the report and move to the next steps.
1. Let’s analyze the data by Sales Territory. Select New England from the Sales Territory (Scatter plot) visual.

      Notice from the Sales over Time, Reseller Tailspin Toys has more sales compared to Wingtip Toys in New England. If you look at Sales YoY% column chart you will notice that Wingtip sales growth has been low and declining quarter over quarter during the past year. After a small rebound in Q3 it went down again in Q4. 

      ![A screenshot of Power BI Desktop report with New England selected](../media/Picture5.png)
1. Let’s compare this to Rocky Mountain territory. Select Rocky Mountain from Sales Territory (Scatter plot) visual.

      Notice in the Sales YoY% column chart sales for Wingtip Toys has increased dramatically in 2022 Q4 after being low for the previous 2 quarters.

      ![A screenshot of Power BI Desktop report with Rocky Mountain selected](../media/Picture6.png)
1. Select **Rocky Mountain from Sales Territory** to remove the filter.
1. From the Scatter plot on the bottom center of the screen (Sales Orders by Sales) select the outlier on the top right (4th quadrant).

      Notice the margin % is 52%, which is above the average of 50%. Also the Sales YoY% has gone up the last 2 quarters of 2022.

      ![A screenshot of Power BI Desktop with Scatter plot selection](../media/Picture7.png)

1. Select the outlier Reseller in the scatter plot to remove the filter.
1. Let’s get the Product details by Product Group and Reseller. From the Sales by Product Group and Reseller Company bar chart right click on the **Packaging Materials bar for Tailspin Toys** and from the dialog select Drill through -> Product Details.
      ![A screenshot of Power BI Desktop with Drill through selection](../media/Picture8.png)
   
1. You will be navigated to the page which provides the Product Details. Notice there are some future orders in place as well.
1. Once you are done reviewing this page, select the Ctrl+back arrow on the top right of the page to be navigated back to the Sales Report.

    ![A screenshot of Power BI Desktop Product Details page](../media/Picture9.png)

1. Feel free to further analyze the report. Once ready let’s look at the model view. From the left panel, select **Model view icon**. Notice there are two fact tables, Sales and PO. 
   1. Granularity of Sales data is by Date, by Reseller, by Product and People. Date, Reseller, Product and People connect to Sales.
   1. Granularity of PO data is by Date, by Product and People. Date, Product and People connect to PO.
   1. We have Supplier data by Product. Supplier connects to Product.
   1. We have Reseller’s location. Geo connects to Reseller.
   1. We have Customer information by Reseller. Customer connects to Reseller. 
1. Let’s look at Power Query to understand the data sources. From the ribbon select **Home -> Transform data.**

    ![A screenshot of data model](../media/Picture10.png)

1. Power Query window opens. From the ribbon, select **Home -> Data** source settings. Data source settings dialog opens. Notice that we have 4 data sources as mentioned in the problem statement.
   1. Snowflake
   1. Sharepoint
   1. Azure Data Lake Gen2
   1. Dataverse
1. Select **Close** to close the Data source settings dialog.

    ![A screenshot of Datasour](../media/Picture11.png)

1. In the left Queries panel, notice the queries are grouped by data source. 
1. Notice **DataverseData** folder has CustomerData available in 4 different queries, BabyBoomer, GenX, GenY and GenZ. These 4 queries are appended to create Customer query.

    ![A screenshot of queries](../media/Picture12.png)

   Notice **ADLSData** folder has multiple dimensions – Geo, Product, Reseller and Date. It also has Sales fact.
   1. Geo dimension is created by merging data from Cities, Countries and States query. 
   1. Product dimension is created by merging data from Product Groups and Product Item Group query.
   1. Reseller dimension is filtered using BuyingGroup query.
   1. Sales fact is created by merging InvoiceLineItems with Invoice query.
1. Notice Snowflake**Data** folder has Supplier dimension and PO (Order/Spend) fact.
   1. Supplier dimension is created by merging Suppliers query with SupplierCategories query.
   1. PO fact is created by merging PO with PO Line Items query.
1. Notice SharepointData folder has People dimension.

Now we know what we are dealing with. In the following labs, we will create a similar Power Query using Dataflow Gen2 and model using Lakehouse.

# References
Fabric Analyst in a Day introduces you to some of the key functions available in Microsoft Fabric. In the menu of the service, the Help section has links to some great resources.

   ![A screenshot of help options](../media/Picture13.png)

Here are a few more resources that will help you with your next steps with Microsoft Fabric.

See blog post to read the full [Microsoft Fabric GA announcement](https://aka.ms/build2023-fabricblog)

- Explore Fabric through the [Guided Tour](https://aka.ms/Fabric-GuidedTour)

Sign up for the [Sign up for the Microsoft Fabric free trial](https://aka.ms/try-fabric)

Visit the [Microsoft Fabric website](https://aka.ms/microsoft-fabric)

- Learn new skills by exploring the [Fabric Learning modules](https://aka.ms/learn-fabric)

- Explore the [Fabric technical documentation](https://aka.ms/fabric-docs)

Read the [free e-book on getting started with Fabric](https://aka.ms/fabric-get-started-ebook) (https://info.microsoft.com/ww-landing-introduction-to-microsoft-fabric-webinar-series.html?lcid=en-us)

Read the more in-depth Fabric experience announcement blogs:

[Data Factory experience in Fabric blog](https://aka.ms/Fabric-Data-Factory-Blog) 

[Synapse Data Engineering experience in Fabric blog](https://aka.ms/Fabric-DE-Blog) 

[Synapse Data Science experience in Fabric blog](https://aka.ms/Fabric-DS-Blog) 

[Synapse Data Warehousing experience in Fabric blog](https://aka.ms/Fabric-DW-Blog) 

[Synapse Real-Time Analytics experience in Fabric blog](https://aka.ms/Fabric-RTA-Blog)

[Power BI announcement blog](https://aka.ms/Fabric-PBI-Blog)

[Data Activator experience in Fabric blog](https://aka.ms/Fabric-DA-Blog) 

[Administration and governance in Fabric blog](https://aka.ms/Fabric-Admin-Gov-Blog)

[OneLake](https://aka.ms/Fabric-OneLake-Blog)[ in Fabric blog](https://aka.ms/Fabric-OneLake-Blog)

[Dataverse and Microsoft Fabric integration blog](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation. All rights reserved.
