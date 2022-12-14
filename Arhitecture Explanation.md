# Description of Architecture:

 - First data flow will use GRPC as source 
 - Second data flow will use CSV as source.

## First Data Pipeline:
gRPC client will communicate with gRPC server to capture the data and for processing the data we will use Kafka + Spark. Data Storage will be done on Big Query and Hdfs. Analytical tools can be used such as Data Studio, Big Query ML , Power Bi and Databricks.

## First Data Pipeline:
Data will be ingested in CSV format to flink through CsvReaderFormat, and for processing we will also use flink because it's supporting data transformation and Mini batches ingestion. Data Storage will be done on Big Query/Hdfs, and connectors will be used for reliable data transfer. Analytical tools can be used such as Data Studio, Big Query ML, Power Bi and Databricks.

Please see the detailed overview of each component used in the data pipeline.

### gRPC:
It's compact binary format for high performance. Since it's pluggable with Http/2 so will use it for streaming.

### Protobuf structure:
Protobuf will be used to enforce the schema of structure and it will be also used to convert to parquet format later. Declarative input/output so that streaming application don't get failed due to incompatible data.

### kafka: 
Implement a service that will communicate between grpc and Kafka. Protobuf data is ingested in Kafka, it will provide robust and fault tolerant data flow. Secondly it provides high speed data streaming platform, as we can use multiple brokers to consume the data.

### Spark Application:
Individual spark application will be called for reliable data transfer. Data Transformation will be done inside data frames, and it will ingest the data to either big query or HDFS, depending upon the requirement. Data format will be used as Parquet for high-speed data ingestion.

### Parquet: 
It help to detect schema automatically and provide high performance in the data pipeline.

### Big Query:
Big Query is the data warehousing solutions that ensure scalable performance for the big datasets, and it can be further used with data analytics such as Data Studio, Big Query ML, Databricks and Power BI

### HDFS:
Hadoop is low-cost solution where we can compromise on speed against the cost, the workflows can define exact requirement and it can used alternatively for the less CPU consuming queries.

### Data Studio/ PowerBI:
Historical Data analysis can be done through Data Studio and PowerBI, both tools provide visualizations and will help for future business prediction and data analysis. 

### Flink: 
It provides support for processing bounded streams as well by integrating streaming with micro batch processing. Flink supports reading CSV files using CsvReaderFormat. The reader utilizes Jackson library and allows passing the corresponding configuration for the CSV schema and parsing options. Flink provides fine-grained control over the CSV schema or the parsing options

### Optional:
#### Data Bricks/BigQueryML:
This option optional if there is requirement of EDA then it can be done through Databricks notebook and for AI machine learning engines we can use BigQueryML.
