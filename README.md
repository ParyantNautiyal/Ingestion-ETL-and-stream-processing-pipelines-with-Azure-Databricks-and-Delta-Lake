# Ingestion-ETL-and-stream-processing-pipelines-with-Azure-Databricks-and-Delta-Lake

- This project is inspired by official microsoft Article. -> https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/articles/ingest-etl-stream-with-adb
- Services Used :
  1. Azure Event Hubs
  2. DataBricks
  3. Azure data factory
  4. Azure Delta lake
 
# Project Scenario 
- Your organization needs to ingest data of any format, size, and speed into the cloud in a consistent way. The solution in this article meets that need with an architecture that implements extract, transform, and load (ETL) from your data sources to a data lake. The data lake can hold all the data, including transformed and curated versions at various scales. The data can be used for data analytics, business intelligence (BI), reporting, data science, and machine learning.

# Data Flow 

1.Data is ingested in the following ways:
        - Event queues like Event Hubs, IoT Hub, or Kafka send streaming data to Azure Databricks, which uses the optimized Delta Engine to read the data.
        - Scheduled or triggered Data Factory pipelines copy data from different data sources in raw formats. The Auto Loader in Azure Databricks processes the data as it arrives.

2. Azure Databricks loads the data into optimized, compressed Delta Lake tables or folders in the Bronze layer in Data Lake Storage.

3. Streaming, scheduled, or triggered Azure Databricks jobs read new transactions from the Data Lake Storage Bronze layer.
      - The jobs join, clean, transform, and aggregate the data before using ACID transactions to load it into curated data sets in the Data Lake Storage Silver and Gold layers.

5. The data sets are stored in Delta Lake in Data Lake Storage.
      - Each service ingests data into a common format to ensure consistency. The architecture uses a shared data lake based on the open Delta Lake format. Raw data is ingested            from different batch and streaming sources to form a unified data platform. The platform can be used for downstream use cases such as analytics, BI reporting, data                 science, AI, and machine learning.
