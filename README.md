# End-to-End DataPipeline with AWS

## Introduction
This project demonstrates the implementation of an end-to-end data pipeline for sales_records data using <strong>AWS services</strong>. It showcases how to build a scalable <strong>ETL (Extract, Transform, Load)</strong> process using <strong>Infrastructure as Code (IaC)</strong> and <strong>PySpark</strong> for data transformation. The project helps in understanding how to ingest, process, and store data efficiently in a cloud-based environment.

## Problem Statement
Organizations handling large-scale sales data face challenges like:

- Manual data processing leading to inefficiencies.
- Slow ETL workflows preventing real-time insights.
- On-premise storage limitations, impacting scalability and cost.

To address these challenges, this project implements a fully automated, cloud-native data pipeline using AWS services. This solution enables businesses to:
- Automate data ingestion and transformation, minimizing manual effort.
- Process large datasets efficiently using AWS Glue and PySpark.
- Store transformed data in Amazon Redshift, enabling fast analytics.
- Ensure security, scalability, and cost optimization through AWS-native tools.

This project serves as a real-world demonstration of how cloud technologies can improve data workflows, decision-making, and operational efficiency.

## Project Overview
The project aims to construct an end-to-end data pipeline within the AWS environment.

*   It utilises several AWS components, starting with S3 for data storage.
*   AWS Glue is used to catalog the data using a crawler.
*   The data is processed using PySpark within interactive Jupyter Notebooks in Glue.
*   Finally, the processed data is loaded into Redshift.


## Key Highlights

*   **Infrastructure as Code (IaC):** Defining and managing infrastructure through code to automate the deployment process.
*   **ETL Pipeline:** Extracting data from a source, transforming it, and loading it into a data warehouse.
*   **AWS Glue Crawlers:** Automatically discover the schema of data stored in S3 and create metadata tables in the Glue Data Catalog.
*   **PySpark:** Using Python and Spark for large-scale data processing.
*   **Dynamic Frame:** A data structure in AWS Glue that is similar to a Spark DataFrame but provides different syntax for performing actions.
*   **Data Transformation:** Converting data from one format to another to make it suitable for analysis.
*   **Data Aggregation:** Combining data from multiple rows into a single row to summarise the information.
*   **AWS Redshift:** A data warehouse service used for storing and analysing large datasets.

## Architecture Diagram
#### AWS ETL Architecture for Data Engineering
![Architecture Diagram](https://github.com/YaswanthiUnnam/Data-Pipeline-in-AWS/blob/c18fb781eaaa8fc54e67d1b1f1cb82250af36da0/Images/Architecture%20Diagram.png)
The data flows through the following steps:
1. <strong>Amazon S3 (Source Storage):</strong> Raw data is loaded into Amazon S3, acting as a data lake for storage.
2. <strong>AWS Glue (ETL Initiation):</strong> AWS Glue detects new data in S3 and initiates one or more ETL (Extract, Transform, Load) jobs.
3. <strong>AWS Glue ETL (Data Transformation & Processing):</strong> AWS Glue ETL jobs process and transform the raw data into a structured format. This step includes cleaning, filtering, aggregating, or enriching data.
4. <strong>AWS Glue Data Catalog (Metadata Management):</strong> The AWS Glue Data Catalog manages metadata, providing schema and table definitions.
5. <strong>Amazon CloudWatch (Monitoring & Logging):</strong> Logs, alerts, and notifications are sent to Amazon CloudWatch for monitoring.
6. <strong>Amazon Redshift / Amazon S3 (Target Data Storage):</strong> The transformed data is loaded into Amazon Redshift (for analytics) or Amazon S3 (for further storage and archiving). This happens within a VPC (Virtual Private Cloud) for secure data processing.

## AWS Services Used
* Amazon S3
* AWS Glue
* Amazon Redshift
* AWS CloudFormation
* AWS IAM

## CloudFormation Template Overview
![s3-glue-redshift-iam.yaml](https://github.com/YaswanthiUnnam/Data-Pipeline-in-AWS/blob/1894d5d73f9bb42326b6a38ec52dac45d69d28f6/s3-glue-redshift-iam.yaml)

1. <strong>Amazon S3:</strong> Creates a bucket to store raw and processed sales data.
2. <strong>AWS Glue:</strong> AWS Glue defines an ETL job using PySpark to transform data and utilizes a Glue Database for efficient metadata management and schema discovery.
3. <strong>Amazon Redshift:</strong> Deploys a cluster to store transformed data for analytics.
4. <strong>AWS CloudFormation:</strong> AWS CloudFormation automates the deployment of the entire data pipeline architecture by provisioning VPC, Subnets, IAM roles, S3 buckets, Glue jobs, and Redshift in a single setup, ensuring infrastructure is managed as code for easy replication and scalability.
5. <strong>IAM Roles:</strong> Grants secure access between Glue, S3, and Redshift using IAM role-based policies.

## Analysis of Regional Sales Data using AWS Redshift

Using Amazon Redshift Query Editor v2, I executed SQL queries on the <strong>dev</strong> database within the <strong>ETL-Redshift-Cluster</strong>. 

1. Counting Rows in a Table - Ensures data completeness by checking total records.
2. Retrieving Data from the Table - Provides a preview of the dataset, including fields like region, country, year, quarter, and total_revenue.
3. Yearly Revenue and Profit Analysis - Aggregates revenue per year to analyze sales trends and profitability.

(Query execution images are stored in the Images folder.)

## Jupyter Notebook - sales-agg.ipynb

In addition to AWS Redshift SQL queries, I performed further data aggregation and analytics using Python in Jupyter Notebook ![sales-agg.ipynb](https://github.com/YaswanthiUnnam/Data-Pipeline-in-AWS/blob/d1feb2cda87cf1d6257e3b185af7d22a50bcef7c/sales-agg.ipynb).

### Notebook Highlights:
- Aggregating sales data to identify key revenue trends.
- Performing additional transformations for deeper insights.
- Generating visualizations for improved business decision-making.

This Python-based analysis complements the AWS Redshift queries, ensuring enhanced analytics and validation of transformed data.

## Summary of Project
This project provides a hands-on approach to building a real-world data pipeline using AWS services. It demonstrates how cloud-based ETL processes can be efficiently implemented for data ingestion, transformation, and storage.

By leveraging AWS Glue, Amazon Redshift, and other AWS-native tools, this pipeline enables:

- Automated data processing, reducing manual intervention.
- Scalable and cost-effective analytics with Amazon Redshift.
- Secure and optimized cloud storage with Amazon S3 and IAM policies.

This solution can help organizations enhance their data-driven decision-making while ensuring efficiency, security, and scalability.


## Contributors
<strong>Yaswanthi Unnam</strong>

## Credits
<strong>DataTech</strong>

## References
[https://www.youtube.com/watch?v=6VJKR3sLTow&ab_channel=DataTech]
