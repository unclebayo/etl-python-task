# etl-python-task

## Language and Script
1. Python
2. SQL

## Databases 
1. Source DB: JSON data provided for the assessment directly from a Git Repository
2. Staging DB: Locally hosted PostgreSQL DB created with Docker
3. Warehouse (OLAP): Locally hosted PostgreSQL DB created with Docker

## Tools and Technology Used
1. Pandas on Python, for reading data from source, loading data into destination
2. Docker

## Architecture
![etl-task drawio](https://user-images.githubusercontent.com/62335314/184490004-001f4248-4fb1-4622-9da2-f30b34a673af.png)


## Approach
##### The below shows a step-step of how this prject was started and ended
This task is considered to be a full-on ETL task involving moving data from the source to a staging environment and finally to a production database (warehouse). 

For the sake of this task, we will first be getting the data from the Github directly via an API which we then read using Pandas DataFrame. This will read all the tables the way they are without doing any form of change or transaformation.
I considered working with the data in CSV instead of the .json format in came with. Hence, I moved the data from the original .json source to a STAGING environment (.stg, _stg extensions in the code base).
Note that, at this stage, I noticed some of the tables do not have headers which were tricky at this point. So I manually assigned headers to this data as at the point of moving from source to staging. Hence in my approach I two functions to cater for such

 a. def data_without_header (for continents, countries.3to2, countries.2to3)
 b. def data_with_header (for all other tables)

In moving the data from source to staging, the following were considered:
 1. I want the data the way it is without any transformation or changes at this point 
 2. The only change done was the file format: json to csv which allowed for easily manipulation for the data without column headers
 3. I implemented a "TRUNCATE TABLE" query to always empty the table first before loading whenever the ETL pipeline runs (FULL REPLICATION)




  
