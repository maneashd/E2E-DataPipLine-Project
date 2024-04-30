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
The idea is to capture a vehicle realtime data travelliing from point A to point B. This data is create using python functions written in main.py.\
The important function involved in publishing data to kafka topic is:
```python
def simulate_journey(producer, device_id):
    while True:
        vehicle_data = generate_vehicle_data(device_id)                    # Dummy data is being generated.
        gps_data = generate_gps_data(device_id, vehicle_data['timestamp'])
        traffic_camera_data = generate_traffic_camera_data(device_id, vehicle_data['timestamp'],
                                                           vehicle_data['location'], 'Nikon-Cam123')
        weather_data = generate_weather_data(device_id, vehicle_data['timestamp'], vehicle_data['location'])
        emergency_incident_data = generate_emergency_incident_data(device_id, vehicle_data['timestamp'],
                                                                   vehicle_data['location'])

        if (vehicle_data['location'][0] >= BIRMINGHAM_COORDINATES['latitude']
                and vehicle_data['location'][1] <= BIRMINGHAM_COORDINATES['longitude']):
            print('Vehicle has reached Birmingham. Simulation ending...')
            break

        produce_data_to_kafka(producer, VEHICLE_TOPIC, vehicle_data)        #data is being published to VEHICLE_TOPIC.
        produce_data_to_kafka(producer, GPS_TOPIC, gps_data)
        produce_data_to_kafka(producer, TRAFFIC_TOPIC, traffic_camera_data)
        produce_data_to_kafka(producer, WEATHER_TOPIC, weather_data)
        produce_data_to_kafka(producer, EMERGENCY_TOPIC, emergency_incident_data)

        time.sleep(3)
```

## ETL Process
### 1. Docker Setup
As the first step I installed docker desktop and executed docker-compose.yml file to spin up containers required to execute this project.\
which include
- Kafka Server
- Zookeeper
- Spark-master
- Spark-worker1
- sparl-worker2
![Data Extraction](docker.png)

### 1. Data Extraction
- Step 1
  
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
