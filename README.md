# Train Ticket Booking: Customer Data Ingestion via Pub/Sub Stream, Dataflow, and BigQuery with Looker Analytics

## Project Overview

This project demonstrates a train ticket booking customer data ingestion pipeline using Google Cloud Platform (GCP) services. Mock customer data is published to a Pub/Sub topic, processed through Dataflow, stored in BigQuery, and visualized using Looker.

## Folder Structure

Project/

├── GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/

│   ├── Bigquery_Table_Details.png

│   ├── Dataflow_Graph_View.png

│   ├── Ingested_Customer_Data_Preview_in_Bigquery.png

│   ├── Pubsub_Topic.png

│   └── Train_Ticket_Booking_Data_Visulaization_Using_Looker.png

├── Project Architecture.png

├── bigquery_create_table.sql

├── train_ticket_booking_customer_mock_data_to_pubsub.py

└── transform_udf.py

## Architecture
![Project Architecture.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/Project%20Architecture.png)

## Prerequisites

1.	GCP Services Enabled: Pub/Sub, Dataflow, BigQuery, Looker.
	
2.	Python Environment: Install Google Cloud libraries (google-cloud-pubsub, etc.).

3.	Service Account: Proper roles for Pub/Sub, Dataflow, and BigQuery access.

## Steps to Implement

### 1. Pub/Sub Configuration

#### Pub/Sub Topic

•	A Pub/Sub topic named train-ticket-data is created to ingest customer data.

![Pubsub_Topic.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/Pubsub_Topic.png)

#### Mock Data Script

The script train_ticket_booking_customer_mock_data_to_pubsub.py:

•	Generates mock customer data.

•	Publishes data to the Pub/Sub topic.

### 2. Dataflow Pipeline

The dataflow pipeline:

•	Transforms the data using the transform_udf.py script.
 
•	Writes the transformed data into BigQuery.

 ![Dataflow_Graph_View.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/Dataflow_Graph_View.png)

 ### 3. BigQuery Table

A BigQuery table train_ticket_dwh.train_ticket_stream_tb is created with the following schema:

```
CREATE TABLE `train_ticket_dwh.train_ticket_stream_tb` (
  row_key STRING,
  name STRING,
  age INT64,
  email STRING,
  join_date DATE,
  last_login TIMESTAMP,
  loyalty_points INT64,
  account_balance FLOAT64,
  is_active BOOL,
  inserted_at TIMESTAMP,
  updated_at TIMESTAMP,
  loyalty_status STRING,
  account_age_days INT64
);

```

![Bigquery_Table_Details.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/Bigquery_Table_Details.png)


### 4. Data Transformation

Using the transform_udf.py script:
	
 •	Validates, enriches, and cleans data.
	
 •	Adds fields such as loyalty_status and account_age_days.

 ### 5. Visualizing Data with Looker

Looker is used to visualize ingested customer data. Example visualizations include:

•	Customer demographics: Age distribution and Active vs. inactive customers.
	
•	Finacial insights: Loyalty points vs account  balance and Total account balance vs loyalty status.

![Train_Ticket_Booking_Data_Visulaization_Using_Looker.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/Train_Ticket_Booking_Data_Visulaization_Using_Looker.png)

## Ingested Data Preview

A preview of the ingested data in BigQuery:

![Ingested_Customer_Data_Preview_in_Bigquery.png](https://github.com/Kaushik-Puttaswamy/Train-Ticket-Booking-Customer-Data-Ingestion-via-Pub-Sub-Stream-Dataflow-and-BigQuery-with-Looker/blob/main/GCP_Console_Train_Ticket_Booking_Data_Ingestion_Screenshot/Ingested_Customer_Data_Preview_in_Bigquery.png)

## Key Python Scripts

### 1. Mock Data Generator

train_ticket_booking_customer_mock_data_to_pubsub.py
	
 •	Generates mock data: Random names, email, loyalty points, etc.
	
 •	Publishes to the Pub/Sub topic.

### 2. Transformation Logic

transform_udf.py
	
 •	Validates data (e.g., formats dates, defaults missing fields).
	
 •	Enriches data with calculated fields like loyalty_status and account_age_days.

## Conclusion

This project demonstrates an end-to-end data ingestion pipeline leveraging GCP services. From data generation to visualization, it highlights real-time data handling and analytics capabilities.
