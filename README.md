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
