# Data Engineering YouTube Analysis Project

![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/architecture.jpeg?raw=true)

(note: didnt used all optional resources)
## Overview

This project aims to securely manage, streamline, and perform analysis on the structured and semi-structured YouTube videos data based on the video categories and the trending metrics.

## Project Goals
1. Data Ingestion — Build a mechanism to ingest data from different sources
2. ETL System — We are getting data in raw format, transforming this data into the proper format
3. Data lake — We will be getting data from multiple sources so we need centralized repo to store them
4. Scalability — As the size of our data increases, we need to make sure our system scales with it
5. Cloud — We can’t process vast amounts of data on our local computer so we need to use the cloud, in this case, we will use AWS
6. Reporting — Build a dashboard to get answers to the question we asked earlier

## Services we will be using
1. Amazon S3: Amazon S3 is an object storage service that provides manufacturing scalability, data availability, security, and performance.
2. AWS IAM: This is nothing but identity and access management which enables us to manage access to AWS services and resources securely.
3. QuickSight: Amazon QuickSight is a scalable, serverless, embeddable, machine learning-powered business intelligence (BI) service built for the cloud.
4. AWS Glue: A serverless data integration service that makes it easy to discover, prepare, and combine data for analytics, machine learning, and application development.
5. AWS Lambda: Lambda is a computing service that allows programmers to run code without creating or managing servers.
6. AWS Athena: Athena is an interactive query service for S3 in which there is no need to load data it stays in S3.

## Dataset Used
This Kaggle dataset contains statistics (CSV files) on daily popular YouTube videos over the course of many months. There are up to 200 trending videos published every day for many locations. The data for each region is in its own file. The video title, channel title, publication time, tags, views, likes and dislikes, description, and comment count are among the items included in the data. A category_id field, which differs by area, is also included in the JSON file linked to the region.

https://www.kaggle.com/datasets/datasnaek/youtube-new

## Execution

###Stages:

### 1.Data Storage Setup:

![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/Bukets.png?raw=true)

   - Created an S3 bucket to store both raw and cleaned data.
   - Utilized AWS CLI to upload data to the S3 bucket.

### 2.Database Setup and Data Ingestion:

![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/Tables.png?raw=true)

   - Created a database and crawler to fetch data from the S3 bucket.
   - 
![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/JSON%20Error.png?raw=true)
 
   - Encountered an error with the query editor's inability to support JSON data.

### 3.Data Transformation and Conversion:

![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/lambda%20funtion.png?raw=true)

   - Developed a Lambda function to convert JSON data to Parquet format.
   - Successfully fetched JSON files using Athena.
   - Expanded data accessibility and efficiency by converting JSON to Parquet.

### 4.ETL Process Implementation:
   - Converted CSV files to Parquet format using an ETL job with a script.
   - Crawled the Parquet data into the clean database, enhancing data organization and query performance.

### 5.Analytics Data Preparation:

![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/athenaquery%20run%20sucessfully.png?raw=true)

   - Established a separate S3 bucket for analytics data.
   - Created an analytics database to facilitate advanced data analysis.

### 6.ETL Job for Analytics:
![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/ETL%20job%20for%20output.png?raw=true)

   - Developed an ETL job using a visual interface to merge data from two tables in the clean database.
   - Saved the joined data to the analytics bucket, preparing it for in-depth analysis.



## AWS Roles Setup for YouTube Analysis Project:
### Glue Role:
![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/Screenshot%202024-05-10%20174829.png?raw=true)

  - Purpose: Used for AWS Glue service, responsible for data transformation and ETL processes.
  - Access Policies:
    - Full access to S3 buckets: Enabled Glue to read from and write to S3 buckets containing raw and cleaned data.
    - AWS Glue service role: Provided necessary permissions for Glue service operations.
### Lambda Role:
  - Purpose: Utilized by AWS Lambda functions for converting data formats and automated tasks.
  - Access Policies:
    - Similar access as Glue service role: Granted Lambda permissions required for Glue operations.
    - Full access to S3 buckets: Enabled Lambda to interact with S3 buckets for data processing tasks.

### Usage of Roles:
Roles were applied throughout the project to ensure proper access control and security compliance.

### Benefits:
1. Granular Access Control: Fine-grained control over permissions ensured each AWS service had access only to necessary resources.
2. Security Compliance: Restricted access to specific resources and operations enhanced project security.
3. Facilitated Automation: Appropriately configured roles allowed seamless execution of automated processes, reducing manual intervention and enhancing efficiency.

## Dashboard Creation:
![](https://github.com/rahulbmogal/Youtube-AWS-data-Engineering-Project/blob/main/Dashboard.png?raw=true)
- Created dashboard Using Quick sight.
   
## Conclusion:
The project successfully established a data pipeline on AWS for YouTube data analysis, covering storage, ingestion, transformation, and preparation for analytics. The setup of roles with defined access policies ensured security while enabling efficient data processing and analysis tasks.

### Next Steps:
Regular review and updates of roles and access policies to align with evolving project requirements and security best practices. Further analysis of prepared data in the analytics database to derive actionable insights for decision-making.


## Reference & credits:
Darshil Parmar
https://youtu.be/yZKJFKu49Dk
