# Welcome to my Polygon Finance ElT data pipeline project!

## Project Overview
This initiative entails the development of an Extract, Load, Transform (ELT) data pipeline dedicated to retrieving data from the Polygon Finance website through its API. The extracted data is then loaded into a PostgreSQL database, subsequently transferred to a Google Cloud Storage (GCS) bucket, and finally moved to BigQuery, the analytical database. This entire process is orchestrated using Airflow with the Celery executor on Docker-compose. The tasks are categorized into stocks, forex, and crypto, each featuring three distinct workflows: extraction to PostgreSQL, upload to GCS, and upload to BigQuery.

## Impact and Usefulness
This pipeline offers a robust and automated solution for collecting, processing, and analyzing financial data across various markets, including stocks, forex, and cryptocurrencies. Businesses and investors can leverage this data to make well-informed decisions based on both real-time and historical market trends. The pipeline's automation significantly reduces the time and effort needed for data gathering and processing, allowing organizations to focus more on insightful analysis and decision-making.

## Data Dictionary
For a detailed understanding of the data fields in the tables containing daily open, high, low, and close (OHLC) data, refer to the provided [Data Dictionary Link](https://docs.google.com/document/d/10Vmmcs7miKZ3VB2K5HKOE2j8AaI1VO04tMVaPde0ViM/edit?usp=sharing). The dictionary encompasses information for stocks/equities, forex, and cryptocurrencies, with specific details for each market, such as adjustments for splits, request IDs, exchange symbols, and more.

## Data Quality Checks and Testing
A notable enhancement to this pipeline is the integration of robust data quality checks and testing within dbt. These checks ensure the reliability and accuracy of processed data, contributing to the overall integrity of analytics and insights derived from the pipeline.

## Data Transformation and Metrics
The dbt tool is employed for transformations and metric generation. Metrics, such as average trading prices and the number of transactions, are developed for each of the three finance data categories (stock, crypto, forex). These metrics are represented in the agg_stock_avg, agg_crypto_avg, and agg_forex_avg tables.

## Technical Details
The pipeline utilizes various technologies and tools to execute tasks. The Polygon Finance API is used for data extraction, which is then loaded into a PostgreSQL database. Subsequently, the data is transferred to a GCS bucket using the PostgresToGCSOperator in Airflow. The GCSToBigQuery Operator is then employed to move the data from GCS to BigQuery. Finally, dbt is used within BigQuery for further transformations, metric generation, and rigorous data quality checks. Airflow orchestrates the entire process from data extraction to the final stage involving dbt (triggered after data finishes loading into BigQuery).

## Image Workflows
Below are images illustrating the Airflow logs, complete table lineage, data in BigQuery, and data in GCS. These images offer a visual representation of the pipeline's operation and the data it processes.

- Airflow dag log
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/23cb53c1-c0f5-41b6-8e3c-170431c77f54)

- Table Lineage
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/7c909848-1015-4611-ae02-9be89ef5ed61)

- Data at GCS Bucket
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/447cd451-6125-4067-a113-b81d645b6f5b)

- Raw tables in BiQuery
- Crypto
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/8c8c5d4f-8b9b-44f1-8907-81b76366c54a)

- Forex
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/996885b7-fc23-4150-aeff-fa97480f259d)

- Stock
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/180b7c56-59ba-4b8c-a963-bcdf0ea00535)

- Stock data in Postgres
![image](https://github.com/krissemmy/Polygon-Finance-Data-ELT/assets/119800888/98825322-bb18-4600-94ec-6f70f03d7a9c)


## Installation and Setup
There is a separate README file that provides detailed instructions on how to install and set up Airflow with the necessary connections. This file can be accessed via the provided link. Check out the Airflow setup instructions [here](https://github.com/krissemmy/Polygon-Finance-Data-ELT/blob/main/Airflow_Codes/airflow_setup/airflow_setup.md)

## Future Improvement
Continuing the pursuit of improvement and scalability, future enhancements for this data pipeline include:

- Expanding metrics based on specific business needs.
- Integrating additional financial markets for broader insights.
- Optimizing pipeline performance for scalability.

## Conclusion
This project represents a robust and automated solution, streamlining the collection, processing, and analysis of financial data from diverse markets. Beyond delivering valuable insights, it showcases the power and flexibility of modern data pipeline technologies. Open to feedback and improvement, the project maintains an adaptive stance, providing opportunities for further enhancements, scalability, and a steadfast commitment to data quality. Contributions through pull requests are welcome to shape the evolution of this dynamic data engineering solution.
