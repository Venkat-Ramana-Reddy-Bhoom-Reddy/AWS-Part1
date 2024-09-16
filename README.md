# AWS-Part1-Venkat

___

# Project Description: 311 Service Requests of City of Vancouver
This is my documentation of the design & implementatio of City of Vancouver Data Analytical Platform by using the free [Source](https://opendata.vancouver.ca/explore/dataset/3-1-1-service-requests/information/?disjunctive.department&disjunctive.service_request_type&disjunctive.status&disjunctive.closure_reason&disjunctive.local_area&disjunctive.channel) datasets available in the Open Data portal website of segment 3-1-1 service requests. This project concentrates on details of designing and implementing DAP in detail.

## Project Title: DAP Design & Implementation for 311 Contact Center of City of Vancouver
* Customer initiated service requests received by 3-1-1 Contact Centre from 2022-2024.
* Service requests refer only to those call types that generate a requ​​es​​t to a City of Vancouver department to provide service.
* The City of Vancouver is increasingly leveraging data to improve its operations and services to citizens.
* This document outlines the implementation of an AWS Data Analytic Platform (DAP) designed to address the city's needs in 3-1-1 service request analysis.
* The DAP offers a secure, scalable, and cost-effective solution for data management, processing, and analysis, empowering city officials to make data-driven decisions for the benefit of Vancouver residents.
## Project Objective:
* To design and implement DAP for City of vancouver's 3-1-1 Service Requests..
## Datasets
* The Dataset used is taken from [City of Vancouver Open Data Portal](https://opendata.vancouver.ca/explore/dataset/3-1-1-service-requests/information/?disjunctive.department&disjunctive.service_request_type&disjunctive.status&disjunctive.closure_reason&disjunctive.local_area&disjunctive.channel) for the category of "3-1-1 Service Request metrics"<br>
[cumulative_3-1-1-service-requests_2023_open.xlsx](https://github.com/user-attachments/files/17021197/cumulative_3-1-1-service-requests_2023_open.xlsx)
 This dataset contains location information such as address or intersection where service was requested and the local area corresponding to the case (incident) location.
## Methodology:
* The process involves different steps explained in detail below:
### Step1: Data Analytical Question Formulation
* In this dataset I will be using the 3-1-1 Service Requests services. The main metric we will be suing here will be about “What is the count of service request for each type of requests respectively.” I felt after having a business established next comes the part where we can utilise various services available from the City of Vancouver for its residents. I felt we can understand this from the information of 3-1-1 Service requests. 
### Step2: Data Discovery
* After the identification of analytical questions above, the next step was the identification of data. Having a virtually developed data structure of metrics and columns we can use from dataset we can proceed.
* It was important to understand these fields to be able to design the succeeding data processing and analysis workflows.
* I have selected the information of “3-1-1 Service Requests” from (City of Vancouver, n.d) portal.
### Step3: Data Storage Design
* In this part we will mainly be discussing on storage. The storage design for the application is raw data storage, Amazon S3, structured data, and Amazon Redshift. This way, the data is retained at scale, and retrieval is very efficient.
* The calls data od 3-1-1 Service Requests as mentioned above are stored in a separate table so that historical data does not get updated and modified and is easily accessible for comparisons.
### Step4: Data Preparation
* In this the data collected in raw format is then preprocessed to make it less erroneous and more standard. 
* This step is essential to ensure the data will be clean and ready to offer good information during the analysis.
* Similarly other metrics were used in the rest of the datasets.
### Step5: Data Ingestion
* In this, raw data is in the form of call logs extracted from the city's 3-1-1 service requests records and loaded to Amazon S3 using AWS Data Pipeline.
* This configuration permits daily updating of current year data and ensures that the medium provides the most recent calls data.
* It's set up to allow for regular bulk updates and live ingesting for real-time analytical purposes.








### Step6: Data Storage
* In this the processed raw datasets are stored in Amazon S3/Redshift, making the processed data available for analysis.
* The data storage phase also has data security measures, such as encryption, to prevent unauthorized access to the data by any unauthorized personnel.<br>
![6-1 s3](https://github.com/user-attachments/assets/f8d302c4-a7ae-4012-b6c8-c8ee92d4061d)
* The above image shows the data storage (S3) of 3-1-1 contact center call details.<br>
![6-2 s3](https://github.com/user-attachments/assets/f74b98a4-8dd3-4679-b60b-8ace7951f043)
* The above image shows the data storage (S3) of abandoned 3-1-1 call details.
### Step7: Data Pipeline Design
* In this an AWS Glue/Step Functions data pipeline is created for the movement of data, which means that data can be processed automatically.
* All the processes, starting from the intake of data, processing it, storing it, and eventually analyzing it, are planned and in place to facilitate the movement of data and its subsequent processing.<br>
![7-data pipeline preperation](https://github.com/user-attachments/assets/ff88012e-b444-424e-b44d-7c02e6b149b7)
* The above image shows the data pipeline of 3-1-1 contact center call details.
### Step8 & 9:	Data Cleaning & Structuring
* In Cleaning preliminary cleaning of the data was explained as crucial for the desired quality of the data set. This consists of removing such records as duplicates, methods utilized to eliminate data entry errors, and gaps in the values. The data must be adequately cleaned so that correct analysis and correct decisions can be made.
* In Structuring the collecting data is arranged in a rather formal format, which can be easily filtered and analysed. This is done to sort the data into tables or partitions, all in an attempt to have the key attributes of the database organized appropriately, like in this manner; Date_Recorded, Call_Abandoned, and Call_Offered to enhance quick and accurate data retrieval.<br>
![8-1-1 cleaning](https://github.com/user-attachments/assets/6da00ace-95b1-4d13-98bf-32402897af50)
* The above image shows the data cleaning of 3-1-1 contact center call details.<br>
![8-1-2 cleaning](https://github.com/user-attachments/assets/b634fb20-7814-4a6f-8498-f632804b4e43)
* The above image shows the data cleaning of 3-1-1 contact center call details.<br>
![8-2-1 cleaning](https://github.com/user-attachments/assets/d28e7b55-6f6c-4565-a87c-5fc11f5bf2a6)
* The above image shows the data cleaning of abandoned calls of 3-1-1 center.<br>
![8-2-2 cleaning](https://github.com/user-attachments/assets/3285c5d5-f151-494c-aec4-85b5cf884ce3)
* The above image shows the data cleaning of abandoned calls of 3-1-1 center.<br>
![8-3 cleaning](https://github.com/user-attachments/assets/a71bfa7a-ebea-4246-a2a1-a9dc3e939501)
* The above image shows the job details of data cleaning of abandoned calls of 3-1-1 center.
### Step10: Data Pipeline Implementation
* In this the data pipeline is the pipeline configuration for Data as explained above: This includes checking on the status of jobs and eliminating any issue that may occur during the job process. It also ensures that the data offered is well-processed and available for implementation promptly.<br>
![10 pipeline 0001](https://github.com/user-attachments/assets/af862d5f-e911-4b15-be7e-5b03d09a74bd)
* The above image shows the data ETL Pipeline for abandoned calls of 3-1-1 center.<br>
![10 pipeline 0002](https://github.com/user-attachments/assets/1e4080fc-8667-4f23-99b9-471790ee1c10)
* The above image shows the data ETL Pipeline for abandoned calls of 3-1-1 center.<br>
![10 pipeline 0003](https://github.com/user-attachments/assets/30a3f61b-2b43-4e82-86ee-cd0884aa1c41)
* The above image shows the data ETL Pipeline for abandoned calls of 3-1-1 center.<br>
![10 pipeline 0004](https://github.com/user-attachments/assets/2159f077-a6a8-4924-9983-6d1f139d44f7)
* The above image shows the data ETL Pipeline for abandoned calls of 3-1-1 center.
### Step11:	Data Analysis
* In this Data analysis is done, and to make queries such as those in the analytical question above, one can use Amazon Athena or QuickSight.<br>
![11 analysis](https://github.com/user-attachments/assets/eb7b9bde-89f6-4701-8e56-a2875a77d1aa)
* The above image shows the data analysis for abandoned calls of 3-1-1 center.
### Step 12: Data Visualization
* These visualizations are ways the data analysis results are presented in an easily understood format. These renderings glance at the audiences by displaying a time series or the cross tab of trends over time or across kinds of work or regions.<br>
![12 visualisation](https://github.com/user-attachments/assets/1bfd06ae-3733-4fb7-84a6-81dbd5405670)
* The above image shows the data Visualization for abandoned calls of 3-1-1 center.
### Step 13: Data Publishing
* Data publishing can be defined as the grouping or disseminating of the analysis results to other parties(Alaimo et al.,2021). This could be in compressed files copied to an S3 bucket for consumption, pre-built and ready dashboards in QuickSight, or weekly, daily, or monthly summaries sent as email or dropped into a folder or S3 bucket.<br>
![13-1 publishing](https://github.com/user-attachments/assets/791d8e64-c61b-4853-af72-272d9bbbefce)
* The above image shows the data publishing for abandoned calls of 3-1-1 center.<br>
![13-2 publishing](https://github.com/user-attachments/assets/aa688c4b-ffb3-4b88-a675-bec524891c1b)
* The above image shows the data publishing for abandoned calls of 3-1-1 center.<br>
![13-3 publishing](https://github.com/user-attachments/assets/70d37d26-9651-4192-8931-4237b89b3433)
* The above image shows the data publishing for abandoned calls of 3-1-1 center.<br>
![13-4 publishing](https://github.com/user-attachments/assets/35c82dca-5d29-41f2-8f62-00e60081d907)
* The above image shows the data publishing for abandoned calls of 3-1-1 center.<br>
![13-5 publishing](https://github.com/user-attachments/assets/b3b982e6-0493-4a2c-accf-c84be4682e21)
* The above image shows the data publishing for abandoned calls of 3-1-1 center.
### Step14: Cost Estimation
* The AWS Pricing Calculator was used to estimate the cost of setting up and the subsequent running of the data analytic platform.
* It costs approximately $ 630.84 to process and analyze the business license data every month using Amazon S3, Athena, Glue, and Quick Sight.
* This estimate will factor in the data's size, its quality in terms of storage, processing, and data visualization, and the frequency of updates of the business license records.<br>
![14 cost](https://github.com/user-attachments/assets/1691f02f-7406-46e2-8b81-b5bd7036db82)
* The above image shows the cost estimation of City of Vancouver project.
