# IEX Cloud Real-Time Stock Data ETL Project

## Introduction

This project builds an end-to-end ETL pipeline for real-time stock data processing using Kafka and AWS. The pipeline can be summarized as follows. The data source is the open-source REST API for real-time stock data from IEX Cloud. The Apache Kafka server is deployed on an AWS EC2 machine. Real-time querying is enabled by AWS Glue and AWS Athena.


## Project Architecture 

<img src="assets/architecture.jpg">

## Technology Used

- Programing Language: Python (Jupyter Notebook)
- Streaming Data Technology: Apache Kafka
- Cloud Services: AWS EC2, AWS S3, AWS Glue, AWS Athena
- REST API: IEX Cloud

## Pipeline 

The ETL pipeline for this project can be summarized as follows.

1. The Kafka Producer sends API request to IEX Cloud and receive real-time stock data, then send to a Consumer.
2. The Kafka Consumer receives data, and dump the data as JSON files into the connected S3.
3. The AWS Glue (Crawler) monitors the S3 bucket, infer schema, and create a table in a Data Catalog database.
4. The AWS Athena connected to the Data Catalog provides SQL querying utilities for the real-time data in relational tables.