# Improving DataBase Performance in MongoDB

 * Medicare / Medicaid Provider Utilization and Payment data from CMS (The Centers for Medicare and Medicaid Services)
 * This design keeps all the frequently accessed data by the queries local to each other due to embeddings, thus reducing disk lookups or joins. This locality helps in query performance and reduces the number of lookup stages needed for querying.
 * In python, extracted data directly from data.cms.gov site in Json format using their API and storing it in AWS shared cluster.
 * MongoDB Import: Using "mongoimport" to import the json files in MongoDB ATLAS
 * JsonSchema applied on the collection to validate documents during insertion in the MongoDB database
 * Performed some transformation steps (ETL) to consolidate collections into ONE collection.
 * The MongoDB collection has information of Medicare specialists, specialization, services, drugs prescribed information and costs.
 * Embedding multiple tables in to one table increases the query performance by accessing the single collection/table instead of following or joining multiple tables/collections by references.
 * Generated millions of extra data using Python Faker library according to the probability distribution of certain attributes.
 * Perform certain complex queries in MongoDB.
 * Recorded the performance for each query and compared it with RDBMS query.
 * Concluded that how MongoDB helps in maintaining data locality when designed correctly and hence improving certain query performance
# Overview:

This project explores how MongoDB document design, data embedding, and aggregation pipelines can be used to improve query performance when working with healthcare provider data.

The project uses Medicare/Medicaid Provider Utilization and Payment Data from the Centers for Medicare & Medicaid Services (CMS). The data was extracted through the CMS API, transformed into a MongoDB-friendly document structure, and loaded into MongoDB Atlas.

The primary focus is on data locality—embedding frequently accessed, related information within the same document to reduce the need for joins or multiple lookup operations.

# Project Objectives:

Extract healthcare provider data from the CMS API.
Transform and consolidate related datasets into a MongoDB document model.
Design documents using embedded arrays for frequently accessed information.
Apply MongoDB JSON Schema validation to maintain data consistency.
Load and manage the data using MongoDB Atlas.
Generate additional test data using Python Faker.
Develop and execute MongoDB queries and aggregation pipelines.
Analyze query results and evaluate the impact of document design on query performance.
Compare MongoDB query approaches with equivalent relational database queries.


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
   ↓
JSON Data Extraction
   ↓
Data Transformation
   ↓
MongoDB Document Modeling
   ↓
JSON Schema Validation
   ↓
MongoDB Atlas
   ↓
Query & Aggregation Analysis 


NOTE: Additional records were generated using the Python Faker library to increase the dataset size and support performance testing under larger data volumes.


# Conclusion: 
