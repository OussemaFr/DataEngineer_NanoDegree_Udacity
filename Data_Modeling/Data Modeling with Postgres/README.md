# Summray :

This is the first project submission for the Data Engineering Nanodegree. This project consists on putting into practice the following concepts: 

- Data modeling with Postgres 
- Database Star schema created 
- ETL pipeline using Python.

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

# Document Process : 

- Purpose of the database

Since, Sparkify's analytics team don't have an easy way to query their data, this database provides an optimised and easy access to all their data in order to answer their business questions and let them focus on analytics rather than manipulating data with complexe queries wasting so much time and eventually money.

- Database schema design and ETL design

Using a relational database is justified since :

1- Data types are structured (Sructure of Json files ,how and where to extract and transform each field is already known).

2- Data is not large enough to require the use of fancy Big Data solutions.

4- The analytics team is interested in understanding what songs users are listening to. =>  business questions can be modeled using simple ERD models.

5- SQL is suitable for this type of analysis and particulary JOINS. 

The schema used for this exercise is the Star Schema: There is one main fact table containing all the measures associated to each event (user song plays), and 4 dimentional tables, each with a primary key that is being referenced from the fact table.

- Schema for Song Play Analysis

**Fact Table**

songplays records in log data associated with song plays i.e. records with page NextSong.
*songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

**Dimension Tables**

**users** in the app.-*user_id, first_name, last_name, gender, level

**songs** in the music database.-*song_id, title, artist_id, year, duration

**artists** in the music database.-*artist_id, name, location, lattitude, longitude

**time**: timestamps of records in songplays broken down into specific units-*start_time, hour, day, week, month, year, weekday

Star schema is optimized for the types of queries on this song play analysis and we can profit from all th benefits of Star Schema like denormalization, simplified queries and espacially fast aggregations.

ETL Design is also simplified,  first read json files and parse them accordingly to store the tables into specific columns with proper formatting.

# How to run the Python scripts

Run python create_tables.py in the console before running etl.py to create/reset tables.
Run python etl.py in the console to execute the entire ETL Pipeline.


# Relevant Files in the repository


**test.ipynb** displays the first few rows of each table for database validation.

**create_tables.py** drops and creates tables.

**etl.ipynb** reads and processes a single file from song_data and log_data and loads into tables in a Jupyter notebook.

**etl.py** processes the entire datasets with what has been completed in etl.ipynb.

**sql_queries.py** containg all sql queries to be imported into the last three files above.

 