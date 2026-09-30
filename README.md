# Overview:

This project explores how MongoDB document design, data embedding, and aggregation pipelines can be used to improve query performance when working with healthcare provider data.

The project uses Medicare/Medicaid Provider Utilization and Payment Data from the Centers for Medicare & Medicaid Services (CMS). The data was extracted directly from data.cms.gov site in Json format using their API and storing it in AWS shared cluster, transformed into a MongoDB-friendly document structure, and loaded into MongoDB Atlas.

The primary focus is on data locality—embedding frequently accessed, related information within the same document to reduce the need for joins or multiple lookup operations.

# Project Objectives:

Improve query performance when accessing and analyzing millions of records in MongoDB compared with SQL.


# Dataset:

The project uses Medicare/Medicaid provider utilization and payment data published by CMS (Centers for Medicare & Medicaid Services).
The consolidated MongoDB collection contains information related to:

Healthcare providers
Provider specialties
Provider demographics and locations
Medical services
Drug utilization
Drug claim counts
Drug costs
Medicare payment amounts
Submitted charges

The data is organized into a consolidated npiInfo collection, with related services and drug information stored as embedded arrays.

# Data Pipeline: ETL workflow:

CMS API
   |
JSON Data Extraction (in AWS shared cluster)
   |
Data Transformation
   |
MongoDB Document Modeling
   |
JSON Schema Validation
   |
MongoDB Atlas
   |
Query & Aggregation Analysis 


NOTE: Additional millions of records were generated using the Python Faker library to increase the dataset size and support performance testing under larger data volumes.


# Conclusion: 
The performance comparison showed that MongoDB was faster for some of the queries tested in this project. For example, one query took approximately 120 ms in MongoDB compared with 350 ms in SQL.

One reason for this difference was the way the data was modeled in MongoDB. Provider information, drugs, and services were stored together in the same document. Embedding document structure helped maintain data locality, reducing the need to retrieve related information through joins across separate tables.

The results showed that MongoDB's document structure can improve query performance when the data is modeled based on how it will be accessed. However, the performance difference depends on the data model, query, indexes, dataset size, and workload, so MongoDB is not necessarily faster than an RDBMS for every type of query.
