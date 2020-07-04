# Project: Data Modeling with Postgres

## Scenario

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Project Objectives

* extract song and artist data from JSON files in path data/song_data and loads it into a PostgreSQL database.
* extract log data about song plays from JSON files in data/log_data, transforms the data to match up with the song data, and inserts the records into the PostgreSQL database.

## Files

* create_tables.py - Python script that creates table based on schema below. Drops tabls if they already exist.
* etl.ipynb - Notebook for developing ETL process
* etl.py - Python script that extracts JSON data from data/song_data and data/log_data and loads into SQL tables
* sql_queries - Collections of queries used for ETL process
* test.ipynb - Notebook used to test queries and ETL process

## Executing Code

1. Open create_tables.py and set appropriate connection information for your PostgreSQL environment
1. Open Python terminal
1. Execute python create_tables.py
1. Database tables are created
1. Open etl.py and set appropriate connection information for your PostgreSQL environment
1. Execute python etl.py
1. Data is extracted from JSON and loaded into SQL tables

## Database Schema

### Table: **songplays**

|Column|Data Type|Description|
|------|---------|-----------|
|songplay_id|INT|Primary key|
|start_time|BIGINT|Unix epoch timestamp in milliseconds|
|user_id|INT|User ID|
|level|VARCHAR|Subscription Level|
|song_id|VARCHAR|Foreign key to songs table|
|artist_id|VARCHAR|Foreign key to artists table|
|session_id|INT|Session ID|
|location|VARCHAR|Recorded location|
|user_agent|VARCHAR|Recorded user agent|

### Table: **users**

|Column|Data Type|Description|
|------|---------|-----------|
|user_id|INT|Primary key|
|first_name|VARCHAR|User First Name|
|last_name|VARCHAR|User Last Name|
|gender|VARCHAR|User Gender|
|level|VARCHAR|User Subscription Level|

### Table: **songs**

|Column|Data Type|Description|
|------|---------|-----------|
|song_id|VARCHAR|Primary key|
|title|VARCHAR|Song Title|
|artist_id|VARCHAR|Foreign key to artist table|
|year|INT|Year song was recorded|
|duration|NUMERIC|Length of song|

### Table: **artists**

|Column|Data Type|Description|
|------|---------|-----------|
|artist_id|VARCHAR|Primary Key|
|name|VARCHAR|Artist Name|
|location|VARCHAR|Aritst Location|
|latitude|VARCHAR|Aritst Latitude|
|longitude|VARCHAR|Artist Longitude|

### Table: **time**

|Column|Data Type|Description|
|------|---------|-----------|
|start_time|BIGINT|Start of song play, Unix epoch timestamp in milliseconds|
|hour|INT|Hour (0-24)|
|day|INT|Day of month|
|week|INT|Week of year|
|month|INT|Month of year|
|year|INT|Year|
|weekday|INT|Day of week (0-6)|
