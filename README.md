# PipeGlot

**PipeGlot** is a versatile data pipeline library that abstracts the underlying execution engines, allowing developers to seamlessly build and manage data workflows across ingestion, storage, serving, and transformation. 

With PipeGlot, you can focus on designing your data architecture without worrying about the specifics of the engine being used behind the scenes.

## Features

- **Unified API**: Interact with multiple data processing engines using a single, consistent interface.
- **Modular Architecture**: Separate components for ingestion, storage, serving, and transformation to enhance clarity and reusability.
- **Flexible Engine Support**: Easily switch between engines like Apache Spark, Flink, DuckDB, RisingWave, and more.
- **Simplified Workflow Management**: Streamline the creation, management, and execution of data pipelines for batch and streaming workloads.
- **Extensible**: Easily add support for additional data processing engines or custom transformations as needed.

## Architecture

PipeGlot is built around four core components:

1. **Ingestion**: 
   - Sync data from various sources, including relational databases like MySQL and PostgreSQL, NoSQL databases like MongoDB, and streaming platforms such as Kafka.
   - Supported engines for ingestion include Apache Spark and DuckDB.

2. **Storage**: 
   - Define where your data is stored using object storage options like MinIO and S3.
   - Supports data formats such as JSON, CSV, and Parquet.

3. **Transformation**: 
   - Perform data transformations as needed to clean, aggregate, or enrich your data.
   - Utilize powerful engines like Apache Spark and DuckDB for processing.

4. **Serving**: 
   - Manage how your data is accessed and queried using serving engines like ClickHouse, Redis, PostgreSQL, and Kafka topics.
   - Simplify data access for analytical queries and real-time applications.


## Supported Sources

### Ingestion Sources
- **Databases**: MySQL, PostgreSQL, MongoDB
- **Streaming**: Kafka topics

### Serving Engines
- **Databases**: ClickHouse, PostgreSQL
- **Streaming**: Kafka topics
- **In-Memory**: Redis
- **Analytics**: DuckDB

### Storage Options
- **Object Storage**: MinIO, S3
- **Formats**: JSON, CSV, Parquet

## Installation

You can install PipeGlot via pip:

```bash
pip install pipeglot
```


## Getting Started

```python
import pipeglot

# Initialize a pipeline
pipeline = pipeglot.Pipeline()

# Ingest data from MySQL and a Kafka topic
data_source_mysql = pipeline.ingest('mysql', engine='spark', source='my_database')
data_source_kafka = pipeline.ingest('kafka', engine='duckdb', topic='my_topic')

# Store the ingested data in S3
storage_location = pipeline.store(data_source_mysql, location='s3://my-bucket/data', format='parquet')

# Transform the data
transformed_data = pipeline.transform(data_source_kafka).filter('column_name > 10')

# Serve the transformed data to ClickHouse
pipeline.serve(transformed_data, endpoint='http://localhost:8123/my_table')

```
## Contributing
I welcome contributions to PipeGlot! If you have suggestions for improvements or new features, please open an issue or submit a pull request.