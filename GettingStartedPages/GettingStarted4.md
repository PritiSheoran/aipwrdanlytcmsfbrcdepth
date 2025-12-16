# Microsoft Fabric: Analytics - Day 4

### Overall Estimated Duration: 4 Hours

## Overview

In this lab, you will get hands-on experience with the machine learning, data science, and document intelligence capabilities of Microsoft Fabric. Participants will learn how to train and track machine learning models using MLflow, implement a complete data science workflow using notebooks and Spark, and process unstructured documents using Azure AI Document Intelligence combined with retrieval-augmented generation (RAG).
By completing this lab, learners will be equipped to build, track, and operationalize machine learning models, prepare and score data at scale, and construct intelligent document-questioning systems using Azure OpenAI and vector search.

## Objective

By the end of this lab, participants will be able to:

- **Create Fabric workspaces and lakehouses** to store and manage machine learning datasets.

- **Train and track ML models** using scikit-learn and MLflow, including run comparison and model registration.

- **Perform end-to-end data science workflows** including ingestion, preparation, transformation, feature engineering, model training, and batch scoring.

- **Extract and process unstructured documents** using Azure AI Document Intelligence and SynapseML.

- **Generate text embeddings and store them in Azure AI Search** to enable semantic retrieval and RAG workflows.

- **Build a question-answering pipeline** combining Azure OpenAI, embeddings, and vector search.

Understand the role of each component in delivering the full machine learning, data science, and document intelligence lifecycle within Microsoft Fabric.

## **Pre-requisites**

Participants should have:

- Basic understanding of Python, machine learning concepts, and Jupyter notebooks.

- Familiarity with Microsoft Fabric workspaces, lakehouses, and notebooks.

- Awareness of Azure AI services such as Document Intelligence, OpenAI, and AI Search.

- Basic experience with Spark or distributed data processing.

## Architecture

In this lab, you will use Microsoft Fabric to perform end-to-end machine learning, data science, and intelligent document processing.
The workflow begins with creating a Fabric workspace and lakehouse to store the training datasets. Using notebooks, you will load data into Pandas and Spark DataFrames, explore and prepare features, and train machine learning models. MLflow is used to track experiment runs, compare results, and register the best model for future use.

For the broader data science scenario, you will ingest, clean, and transform customer churn data, create multiple ML experiments, score the trained models, and write predictions back to the lakehouse for downstream analytics. Power BI is used to visualize churn predictions using DirectLake mode.

The document intelligence portion of the architecture leverages Azure AI Document Intelligence to extract structured content from PDF documents. Extracted text is chunked and transformed into embeddings using SynapseML and Azure OpenAI. These embeddings are stored in Azure AI Search for vector retrieval. A retrieval-augmented generation (RAG) pipeline is then implemented, allowing users to query documents using natural language and receive accurate responses grounded in their own data.

Throughout the lab, you will interact with Fabric notebooks, MLflow tracking, lakehouse storage, Azure AI Services, SynapseML, and Power BI—experiencing a unified platform for machine learning and intelligent AI workloads.

## Explanation of Components

The architecture for this lab involves the following key components:

1. **Fabric Workspace**

    A centralized environment for managing all machine learning, data science, and document intelligence assets.

    - Stores lakehouses, notebooks, MLflow experiments, registered models, and reports.
    - Enables collaboration and lifecycle management.

2. **Fabric Lakehouse**

    A unified storage layer built on Delta Lake.

    - Stores the training datasets, transformed data, and model scoring outputs.
    - Supports both Spark and SQL compute for data science workflows.

3. **Notebooks (PySpark & Python)**

    The core development interface for ML and document workflows.

    - Used for data loading, cleaning, feature engineering, and model training.
    - Integrates seamlessly with Spark, MLflow, SynapseML, and Azure AI services.

4. **MLflow**

    A model tracking and registry service embedded in Fabric.

    - Tracks model parameters, metrics, artifacts, and versions.
    - Allows comparison of experiment runs and registration of best models.
    - Provides governance for deploying and managing ML models.

5. **Azure AI Document Intelligence**

    Extracts text, tables, and structures from PDF documents.

    - Converts unstructured documents into machine-readable JSON.
    - Forms the basis for semantic processing and embedding generation.

6. **SynapseML**

    A distributed machine learning library used for advanced processing.

    - Performs text chunking for long documents.
    - Generates embeddings using Azure OpenAI models.
    - Supports scalable ML operations across Spark clusters.

7. **Azure OpenAI Service**

    Provides LLM-based intelligence for embeddings and response generation.

    - Generates vector embeddings for document chunks.
    - Powers the generative component of the RAG pipeline.

8. **Azure AI Search**

    A vector search engine that stores and retrieves embeddings.

    - Enables semantic similarity search over document chunks.
    - Used to fetch the most relevant context for RAG.

9. **RAG (Retrieval-Augmented Generation) Pipeline**

    Combines Azure OpenAI with vector search to build a question-answering system.

    - Retrieves relevant document chunks from AI Search.
    - Uses LLMs to generate accurate, context-grounded responses.

10. **Power BI**

    Used to visualize machine learning prediction results.

    - Connects to the lakehouse using DirectLake mode.
    - Displays churn prediction outcomes or model performance metrics.

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
 
2.  In the new tab, navigate to the **Microsoft Fabric** portal by copying and pasting the following URL into the address bar.

      ```
      https://app.fabric.microsoft.com
      ```

3. On the **Enter your email, we'll check if you need to create a new account** tab, you will see the login screen, in that enter the following email/username, and click on **Submit (2)**.

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject> **(1)**
 
       ![01](./media/image1.png)
 
4. Next, provide your Temporary Access Password **(1)** and click on **Sign in (2)**:
 
   - **Temprory Access Pass:** <inject key="AzureAdUserPassword"></inject>
 
       ![01](./media/image2.png)

5. If you see the pop-up Stay Signed in?, select **No**.
   
    ![01](./media/Intro-08.png)

6. On Microsoft Fabric (Free) license assignment dialog appears, click **OK** to proceed.

    ![01](./media/Intro-09.png)

7. When the **Welcome to the Fabric view** dialog appears, click **Cancel**.   

    ![01](./media/image4.png)    

8. You will be navigated to the **Microsoft Fabric Home page**.

    ![01](./media/image3.png)

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.
 
![01](./media/Intro-11.png)

## Happy Learning!!