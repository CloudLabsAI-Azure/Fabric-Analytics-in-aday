# Microsoft Fabric - Fabric Analyst in a Day - Lab 2

# ![](../media/new4.png)

# Contents

  * Introduction

  * Fabric License

      * Task 1: Enable a Microsoft Fabric trial license
        

  * Overview of Fabric Experiences:

      * Task 2: Data Factory Experience
  
      * Task 3: Data Activator Experience
  
      * Task 4: Synapse Data Engineering Experience
  
      * Task 5: Synapse Data Science Experience
  
      * Task 6: Synapse Data Warehouse Experience
  
      * Task 7: Real-Time Analytics Experience

  * Fabric Workspace

      * Task 8: Create a Fabric Workspace
  
      * Task 9: Create a Lakehouse

  * References

# Introduction
Today you will learn about various key features of Microsoft Fabric. This is an introductory workshop intended to introduce you to the various product experiences and items available in Fabric. By the end of this workshop, you will learn how to use Lakehouse, Dataflow Gen2, Data Pipeline, and DirectLake feature.

By the end of this lab, you will have learned: 

  - How to create a Fabric workspace
  - How to create a Lakehouse  

# Fabric License
### Task 1: Enable a Microsoft Fabric trial license
1. Open the **browser** and navigate to https://app.powerbi.com/. You will be navigated to the login page.

    >**Note:** If you have an existing Power BI account, you may want to use the browser in private / incognito mode.
1. Enter the **Email** provided by the instructor and click **Submit**.

      ![Picture17](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/3995afaf-cf69-4541-894e-b2b06ee8caf5)


1. You will be navigated to the **Password** screen. Enter the password shared with you by the instructor. 
1. Click **Sign in** and follow the prompts to sign into Fabric.

      ![Picture18](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/5428ffb9-7039-4fcc-818c-42fb5cf2b4f5)

1. You will be navigated to the familiar **Power BI Service Home page**.
1. We assume you are familiar with the layout of Power BI Service. If you have any questions, please do not hesitate to ask the instructor.

    Currently, you are in **My Workspace**. To work with Fabric items, you will need a trial license and a workspace that has Fabric license. Let’s do this.

1. On the top right corner of the screen, select the **user icon**.
1. Select **Start trial**.

      ![Picture19](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/9f2a3001-5e81-4bed-8408-ec4287467842)
  
1. Upgrade to a free Microsoft Fabric trial dialog opens. Select **Start trial**.

      ![Picture20](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/c910b821-9662-42a4-91f2-501ec2f81828)

1. Successfully upgraded to a free Microsoft Fabric trial dialog opens. Select **Fabric Home Page**. 

      ![Picture21](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/709b1a4e-5a75-4b40-b2ab-8d010e2a8dd4)


1. You will be navigated to the **Microsoft Fabric Home page**.

      ![Picture22](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/dc8dcdc9-8b10-4e09-8c70-67f22a47a7b3)

# Overview of Fabric Experiences:

### Task 2: Data Factory Experience

1. Select the **Microsoft Fabric** icon on the bottom left of your screen. A dialog with the list of Fabric experiences will open. Notice that Power BI, Data Factory, and Data Activator are independent experiences. Data Engineering, Data Science, Data Warehouse, and Real-Time Analytics are Synapse experiences and these four experiences are powered by Synapse. Let’s explore.
  
3. Select **Data Factory**.
 
      ![Picture23](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/793c431e-6942-4e80-9bc2-774f95e60eba)

4. You are navigated to the **Data Factory Home page**. The page contains three main sections.
   
    1. **New:** This lists the items available in Data Factory – Dataflow Gen2 and Data pipeline.
         1. Dataflow Gen2 is the next generation of Dataflow.
         1. Data pipeline is used for data orchestration.
    2. **Recommended**: This section provides access to quick start learning documentation.
    3. **Quick Access**: This section lists the recently used or favorite items.

   ![Picture24](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/4cfa0615-359d-47ad-b4f3-a5432201c44b)

### Task 3: Data Activator Experience

1. Select **Data Factory** on the bottom left of your screen. Fabric experience dialog opens.

      ![Picture25](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/98c00246-ad57-4b6a-873d-7e3527ad30df)

2. Select **Data Activator** from the dialog. You will be navigated to **Data Activator Home page**. Data Activator is a no-code experience in Microsoft Fabric for automatically taking actions when patterns or conditions are detected in changing data. Notice the three sections are like the Data Factory experience. In the New section, notice the items:
    1. **Reflex:** Used to monitor datasets, queries, and event streams for patterns.
    1. **Reflex sample:** Sample solution.

        ![Picture26](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/b517d1b3-8fda-4df2-9a7a-8db844fb33c6)

### Task 4: Synapse Data Engineering Experience

1. Select **Data Activator** on the bottom left of your screen. Fabric experience dialog opens.
2. Select **Data Engineering**. You will be navigated to the **Data Engineering Home page**. Again, the page contains three main sections. In the New section, notice the items: 
   1. **Lakehouse:** Used to store big data for cleaning, querying, reporting, and sharing.
   1. **Notebook**: Used to run queries on the data to produce shareable tables and visuals.
   1. **Spark Job Definition**: Used to define, schedule, and manage Apache jobs.
   1. **Data pipeline**: Used to orchestrate data solution.
   1. **Import notebook**: Used to import notebooks from local machine.
   1. **Use a sample**: Used to create a sample.

   ![Picture27](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/19abeee2-ff05-49fd-8c93-974ede877f61)

### Task 5: Synapse Data Science Experience

1. Select **Data Engineering** on the bottom left of your screen. Fabric experience dialog opens.
2. Select **Data Science**. You will be navigated to the **Data Science Home page**. Again, there are three sections. In the New section, notice the items:
    1. **ML model**: Used to create machine learning models.
    1. **Experiment**: Used to create, run, and track development of multiple models.
    1. **Notebook**: Used to explore data and build machine learning solutions.
    1. **Import Notebook**: Used to import notebooks from local machine.
    1. **Sample**: Sample solution.

      ![Picture28](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/ad8c4969-b773-4729-ac6f-b051f6f0568d)

### Task 6: Synapse Data Warehouse Experience

1. Select **Data Science** on the bottom left of your screen. Fabric experience dialog opens.
2. Select **Data Warehouse**. You will be navigated to **Data Warehouse Home page**. Again, there are three sections. In the New section, notice the items. Notice Data pipeline and Dataflow Gen2 are available here as well.
   1. **Warehouse**: Used to provide strategic insights from multiple sources.
   1. **Sample warehouse**: Sample warehouse solution.
   1. **Data pipeline**: Used to orchestrate data solution.

        ![Picture29](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/fd991d84-d9ba-45df-867d-0b4f3ce00174)

### Task 7: Real-Time Analytics Experience

1. Select **Data Warehouse** on the bottom left of your screen. Fabric experience dialog opens.
2. Select **Real-Time Analytics**. You will be navigated to **Real-Time Analytics Home page**. Again, there are three sections. In the New section, notice the items: 
   1. **KQL Database**: Used to rapidly load structured, unstructured, and streaming data for querying.
   1. **KQL Queryset**: Used to run queries on the data to produce shareable tables and visuals.
   1. **Eventstream**: Used to capture, transform, and route real-time event stream.
   1. **Use a sample**: Used to create a sample.

      ![Picture30](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/69f664d3-c1b7-429f-b539-f3a7c5f3ff58)

# Fabric Workspace

### Task 8: Create a Fabric Workspace

1. Now let’s create a workspace with Fabric license. Select **Workspaces** from the left navigation bar. A dialog opens.
2. Select **New workspace**.

      ![Picture31](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/1abb5726-062b-4e6f-b31d-7e64154e9a08)

3. **Create a workspace** dialog opens on the right side of the browser.
4. In the **Name** field enter **FAIAD_username**.

    **Note:** Workspace name must be unique. We are using FAIAD as the workspace name for this document. However, your workspace name must be different. Make sure a green check mark with **“This name is available”** is displayed below the Name field.
   
6. If you choose, you can enter a **Description** for the workspace. This is an optional field.
7. Click on **Advanced** to expand the section.

     ![Picture32](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/7753b82d-3e75-44ae-ade7-922d7ce6aa82)

8. Under **License mode**, make sure **Trial** is selected. (It should be selected by default.)
9. Select **Apply** to create a new workspace.

      ![Picture33](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/53c16aaa-f5aa-40e1-ae81-6b3419b8320d)

    A new workspace is created, and you will be navigated into this workspace. We will bring data from the different data sources into Lakehouse and use the data from the Lakehouse to build our model and report on it. The first step is to create a Lakehouse.

### Task 9: Create a Lakehouse
1. Select **Real-Time Analytics** on the bottom left of your screen. Fabric experience dialog opens.
2. Select **Data Engineering** to be navigated to Data Engineering Home page.

      ![Picture34](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/5d99fdea-b065-4fe7-af9c-c3e7fee8a0c2)

3. Select **Lakehouse**.

     ![Picture35](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/3ee5be4a-be9b-4cce-bf4b-9587895bfa1c)

4. New lakehouse dialog opens. Type **lh_FAIAD** in the Name textbox. 
    **Note**: lh here refers to Lakehouse. We are prefixing lh so that it is easy to identify and search.
5. Select **Create**.

      ![Picture36](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/13961927-fea2-485f-8d53-ca04a496915f)

      Within a few moments, a Lakehouse is created, and you will be navigated to the Lakehouse interface. On the **left panel**, notice that below your workspace, you will have the Lakehouse icon. You can easily navigate to the Lakehouse by clicking on this icon at any time.

      Within the Lakehouse explorer you will notice **Tables** and **Files**. Lakehouse could expose Azure Data Lake Storage Gen2 files under the files section, or a dataflow could load data to Lakehouse tables. There are various options available. We are going to show you some of the options as in the following labs.

      ![Picture37](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/c610b936-304c-431c-87ed-72def4c4ba1d)

      In this lab, we explored the Fabric interface, created a Fabric workspace, and a Lakehouse. In the next lab, we will learn how to use Dataflow Gen2 to connect to ADLS Gen2 to extract, transform, and ingest data into the Lakehouse.

# References
Fabric Analyst in a Day (FAIAD) introduces you to some of the key functions available in Microsoft Fabric. In the menu of the service, the Help (?) section has links to some great resources.

   ![Picture38](https://github.com/CloudLabsAI-Azure/Fabric-Analytics-in-aday/assets/121504071/a1caeee4-9c00-4538-b506-aedbe4b62445)

Here are a few more resources that will help you with your next steps with Microsoft Fabric.

- See blog post to read the full [Microsoft Fabric GA announcement](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Explore Fabric through the [Guided Tour](https://aka.ms/Fabric-GuidedTour)
- Sign up for the [Microsoft Fabric free trial](https://aka.ms/try-fabric)
- Visit the [Microsoft Fabric website](https://aka.ms/microsoft-fabric)
- Learn new skills by exploring the [Fabric Learning modules](https://aka.ms/learn-fabric)
- Explore the [Fabric technical documentation](https://aka.ms/fabric-docs)
- Read the [free e-book on getting started with Fabric](https://aka.ms/fabric-get-started-ebook)
- Join the [Fabric community](https://aka.ms/fabric-community) to post your questions, share your feedback, and learn from others

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

