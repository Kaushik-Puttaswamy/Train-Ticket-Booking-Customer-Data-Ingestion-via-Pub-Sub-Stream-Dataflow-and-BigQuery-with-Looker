# Train Ticket Booking: Customer Data Ingestion via Pub/Sub Stream, Dataflow, and BigQuery with Looker Analytics

## Project Overview

This project demonstrates a train ticket booking customer data ingestion pipeline using Google Cloud Platform (GCP) services. Mock customer data is published to a Pub/Sub topic, processed through Dataflow, stored in BigQuery, and visualized using Looker.

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
