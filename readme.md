# Python Database Utilities

By Kenneth Burchfiel

Released under the MIT license

## Part 1: Executive Summary

This repository contains scripts for creating, modifying, and testing databases using Python. In the process of creating the repository, I had the opportunity to compare seven database hosting options: 
1. Amazon Web Services (AWS)
2. Google Cloud Platform (GCP)
3. Microsoft Azure
4. Heroku
5. Airtable
6. Snowflake
7. Databricks

### 1.1. Comparing setup processes

My choice to use SQLAlchemy and Python to set up these databases influenced my experiences with the setup process. Users who prefer to create tables using a web interface or command prompt may form different impressions of each provider.

Ultimately, I found the database setup process for AWS, GCP, and Azure to be fairly straightforward; once I learned how to upload data to one of them using PostgreSQL, creating tables for the other two proved to be very similar. Setting up databases on Heroku and Snowflake required some extra steps, but both worked well with SQLAlchemy and the to_sql Pandas function. 

Meanwhile, the Databricks setup process was considerably more complex, since I chose to use pyodbc rather than SQLAlchemy due to the terms of service attached to MS Build Tools for Visual Studio, which I would have needed to install to connect SQLAlchemy and Databricks. Airtable made it easy to view my database data online, but there were significant limits on the amount of data that I could upload.

Based on my experiences, if I simply needed to create a PostgreSQL database using Python and SQLAlchemy, I would likely choose AWS, GCP, or Azure. However, I imagine that Snowflake, Heroku, Airtable, and Databricks would be compelling or superior options for other use cases.

### 1.2. Comparing database import and query times

**Note:** This notebook is by no means meant as a definitive assessment of the speeds of each database provider. My results were undoubtedly influenced by my configuration settings for each database, and different configuration settings would likely result in different outcomes. In addition, the tests I used may not match real-world usage scenarios. Do not use these results to make decisions about which database provider to use.

(Note: Airtable was excluded from the testing process because it did not have enough capacity to import all of my original SQLite database's tables.)

I used four different tests to measure database speeds:

1. A full database import
2. A simple query
3. A simple query (repeated 1000 times)
4. A complex query

I ranked the databases based on the time required to complete each test, then combined the results into a composite ranking. That ranking is as follows:

| Provider | Ranking | 
|-------|-------|
|AWS|1|
|Azure|2|
|Snowflake|3|
|Heroku|4|
|GCP|5|
|Databricks|6|

A table showing both the composite and individual rankings for each database can be found [here](https://github.com/kburchfiel/python_database_utilities/blob/master/metrics/overall_database_query_rankings.csv).


The following charts, which can also be found in this repository's [metrics](https://github.com/kburchfiel/python_database_utilities/tree/master/metrics) folder, show how long each database took to complete each trial of each test.

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/full_import_time.png "Full import test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/simple_query_results_1x.png "First simple query test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/simple_query_results_1000x.png "Second simple query test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/complex_query_time.png "Complex query test")

### 1.3. Comparing prices




## Part 2: Repository Information



**sqlite_database_builder** shows how to import data sources into a local SQLite database.

**database_uploader** demonstrates how to extract data from a SQLite database, then import it into various database services (Amazon Web Services, Google Cloud Platform, Microsoft Azure, etc.). SQLAlchemy and the to_sql Pandas function are used extensively within this program.

**database_query_timer** provides code for timing the length of various database operations.

The data folder stores the original data used in constructing the SQLite database, and the metrics folder stores the output of the database_query_timer function.

**For additional documentation, see the pdu_documentation file (uploaded in both .docx and .pdf form).**

**Note:** Two files in the repository could not be uploaded to GitHub because they are above 100 megabytes in size. To access these files, use the following Google Drive links: (if these links break for whatever reason, let me know by posting an issue within this project.)

1. routes_planes_coordinates.csv: https://drive.google.com/file/d/1TBj5_zgdhtH8eBcPXLthqGgkJSRb4WFC/view?usp=sharing
2. sqlite_database.db: https://drive.google.com/file/d/1THyBZYXXT4le6zQz2SBhQlIjMk2MjhYz/view?usp=sharing
