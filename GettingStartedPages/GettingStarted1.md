# Microsoft Fabric: Analytics - Day 1

### Overall Estimated Duration: 4 Hours

## Overview

In this lab, you will get hands-on experience with Microsoft Fabric's end-to-end analytics capabilities. Participants will learn how to build a modern data architecture using lakehouses, ingest and transform enterprise data, and create insightful Power BI reports using DirectLake technology. You will also explore Fabric’s integrated AI capabilities by applying advanced text analytics functions such as sentiment analysis, translation, classification, entity extraction, grammar correction, and summarization directly within notebooks.

By completing this lab, learners will gain an understanding of how Microsoft Fabric unifies data engineering, data science, real-time analytics, and business intelligence into a single SaaS platform. They will be able to design, load, transform, and visualize data while leveraging built-in AI functions to enhance analytical insights.

## Objective

By the end of this lab, participants will be able to:

* **Create and configure a Microsoft Fabric workspace and lakehouse** to establish a unified data foundation.

* **Ingest raw data** into the lakehouse using file upload and Data Factory pipelines.

* **Transform and prepare data** using PySpark and SQL notebooks to build Silver and Gold-layer datasets.

* **Build semantic models and Power BI reports** using DirectLake for high-performance analytics.

* **Apply AI text functions** in Fabric notebooks to perform sentiment analysis, translation, summarization, classification, and entity extraction.

* **Generate AI-based insights** using built-in generative functions to enhance data understanding.

Understand the role of each Fabric component in delivering an end-to-end analytics and AI-powered data workflow.

## Prerequisites

Participants should have:

- Basic understanding of Power BI, data modeling concepts, and report building.
- Familiarity with data engineering or SQL, such as querying or transforming datasets.
- Basic knowledge of Python or Spark is helpful but not mandatory.
- Understanding of enterprise analytics workflows (data ingestion → transformation → reporting).
- No prior experience with Microsoft Fabric is required; this lab is beginner-friendly.

## Explanation of Components

The architecture for this lab involves the following key components:

1. **Microsoft Fabric Workspace**

    - Logical container that holds all analytics assets such as lakehouses, pipelines, notebooks, models, and reports.
    - Provides unified governance, security, and monitoring across assets.

2. **OneLake & Lakehouse**

    - **OneLake** is the organization-wide, unified storage layer built on Delta Lake.
    - The **Lakehouse** combines file-based storage and relational table storage under a single metadata and storage system.
    - Supports:

        - Raw files in *Files* (Bronze)
        - Managed Delta tables in *Tables* (Silver/Gold)
    - Enables streamlined ingestion and transformation workflows.

3. **Data Factory Pipelines (Copy Data Assistant)**

    - Used to ingest large volumes of structured and unstructured data from sample sources.
    - Supports scheduled and on-demand data refresh.
    - Enables ELT-style ingestion into lakehouse storage.

4. **Fabric Notebooks (with Live Spark Pool)**

    - Used for PySpark, Spark SQL, or Python transformations.
    - Key capabilities include:

        - Delta Lake optimizations (V-order, optimize-write)
        -  Partitioning and schema management
        - Business logic and aggregation creation
    - Notebooks run automatically on Fabric’s **Live Pool**, with no cluster management required.

5. **Semantic Model (Power BI Dataset)**

    - Provides the analytical model for reporting.
    - Includes:

        - Tables
        - Relationships
        - Measures (auto-generated)
    - Connects to lakehouse Delta tables via **DirectLake** for real-time performance.

6. **Power BI DirectLake**

    - Reads Delta files directly from OneLake into the Power BI engine.
    - Eliminates import mode latency and DirectQuery performance bottlenecks.
    - Allows instant reflection of upstream data changes.

7. **AI Functions (SynapseML in Fabric)**

    - Built-in AI capabilities accessible via pandas or Spark DataFrames.
    - Functions supported:

        - **Sentiment analysis**
        - **Text translation**
        - **Entity extraction**
        - **Classification**
        - **Grammar correction**
        - **Text summarization**
        - **Custom generative responses**
    - Allows embedding AI into data engineering and data science workflows easily.

8. **Generative AI Integration**

    - Uses Fabric-managed LLMs or custom Azure OpenAI endpoints.
    - Enables:

        - Automated content creation
        - Conversational intelligence
        - Enrichment of structured datasets with AI insights

9. **Workspace Cleanup**

    - Ensures resources are deleted after learning activities.
    - Helps maintain a cost-efficient environment.

## Architecture

In this lab, you will use Microsoft Fabric to build an end-to-end analytics workflow that unifies data ingestion, transformation, modeling, reporting, and AI enrichment. The process begins with creating a Fabric workspace and lakehouse to store raw data in OneLake. You will ingest sample datasets using file upload and Data Factory pipelines, forming the foundation of your Bronze layer.

You will then transform and refine this data using PySpark and SQL notebooks, producing optimized Silver and Gold Delta tables. These curated tables are added to a semantic model and consumed in Power BI using DirectLake, enabling fast, real-time analytics without data duplication.

Finally, you will apply Fabric’s built-in AI functions to perform sentiment analysis, translation, summarization, and other text intelligence tasks directly on your data, demonstrating how AI can be seamlessly integrated into modern analytics workflows.

## Architecture Diagram

## Getting Started with the Lab
 
Once the environment is provisioned, a virtual machine (LabVM) and lab guide will be loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the bottom of the Lab guide to switch to different exercises in the lab guide.
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.
 
   ![01](./media/Intro-00.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
   ![01](./media/Intro-01.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the top right corner.
 
![01](./media/Intro-02.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
![01](./media/Intro-03.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

  ![01](./media/Intro-04.png)
 
## Let's Get Started with Power BI Portal
 
1. On your virtual machine, open the **Microsoft Edge**.
 
    ![01](./media/Intro-05.png)
 
2.  In a new tab, navigate to the **Power BI** portal by copying and pasting the following URL into the address bar:

      ```
      https://app.powerbi.com/
      ```

3. On the **Enter your email, we'll check if you need to create a new account** tab, you will see the login screen, in that enter the following email/username, and click on **Submit**.

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![01](./media/Intro-06.png)
 
4. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![01](./media/Intro-07.png)

5. First-time users are often prompted to Stay Signed In. If you see any such pop-up, click on **No**.
   
    ![01](./media/Intro-08.png)

6. On Microsoft Fabric (Free) license assignment dialog appears, click **OK** to proceed.

    ![01](./media/Intro-09.png)

7. You will be navigated to the **Power BI Home page**.

    ![01](./media/Intro-10.png)

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.
 
![01](./media/Intro-11.png)

## Happy Learning!!