# Sparkify: Data Modeling with Postgres

 Sparkify is a music streaming app.Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to.

In this project, I've apply what I've learned on data modeling with Postgres and build an ETL pipeline using Python.

# File Overview

  ```data/song_data/```- This file contains our song data in json format. Files are partitioned by the first three letters of each song's track ID.
  ```data/log_data/```- This file contains our user activity logs in json format. files are partitioned by year and month.
  ```test.ipynb```-This file displays the first few rows of each table to let you check your database.
  ```create_tables.py```-This file drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
```etl.ipynb```-This file reads and processes a single file from song_data and log_data and loads the data. into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
```etl.py``` reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.
```sql_queries.py``` contains all your sql queries, and is imported into the last three files above.
```README.md``` This file provides description of this project.

## Required libraries
* pandas
* psycopg2
* sql_queries

## Data

### Songs metadata
The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

```python
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json 
```

And below is an example of what a single song file, TRAABJL12903CDCF1A.json, looks like.
```python
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "
```
### User activity logs
The log files in the dataset you'll be working with are partitioned by year and month. For example, here are filepaths to two files in this dataset.

```python
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json
```

And below is an example of what a single activity log in 2018-11-13-events.json, looks like.
```python
{"artist":null,"auth":"Logged In","firstName":"Kevin","gender":"M","itemInSession":0,"lastName":"Arellano","length":null,"level":"free","location":"Harrisburg-Carlisle, PA","method":"GET","page":"Home","registration":1540006905796.0,"sessionId":514,"song":null,"status":200,"ts":1542069417796,"userAgent":"\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.125 Safari\/537.36\"","userId":"66"}
```

## Star Schema for this project
**Fact table**: songplays
**Dimension table**: users, songs, artists and time.

![star_schema](https://user-images.githubusercontent.com/44708711/88259187-6d322e80-ccdf-11ea-8f15-ed79cc7455d0.png)
