# End to End Realtime Data Engineering Project

![Project Architecture](SysArch.png)

## Overview
This project demonstrates an end-to-end ETL (Extract, Transform, Load) process using Apache Spark. It extracts data from various sources, performs transformations, and loads the processed data into a target destination.

## Technologies Used
- Apache Spark
- Python
- Kafka
- Docker
- AWS S3
- AWS GLue
- AWS Redshift
## Data Creatinon
The idea is to capture a vehicle realtime data travelliing from point A to point B. This data is create using python functions.

## ETL Process
### 1. Docker Setup
As the first step I installed docker desktop to spin up containers required to execute this project.\
which include
- Kafka Server
- Zookeeper
- Spark-master
- Spark-worker1
- sparl-worker2
![Data Extraction](docker.png)


![Data Extraction](screenshots/data_extraction.png)
We extract data from multiple sources, including databases, APIs, and CSV files.

### 2. Data Transformation
![Data Transformation](screenshots/data_transformation.png)
We perform various transformations on the extracted data to clean, filter, and enrich it.

### 3. Data Loading
![Data Loading](screenshots/data_loading.png)
We load the transformed data into a target destination, such as a data warehouse or a database.

## Usage
To run the ETL process, follow these steps:
1. Clone the repository.
2. Set up the necessary dependencies.
3. Execute the extraction, transformation, and loading scripts in sequence.

## Conclusion
This README provides an overview of the ETL project, including its architecture, technologies used, and the ETL process. By following the provided instructions, users can run the ETL process and analyze the transformed data.

Feel free to customize this template according to your project's specific requirements and add additional sections as needed.
