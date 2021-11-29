# Python Database Utilities

By Kenneth Burchfiel

Released under the MIT license

## Part 1: Executive summary

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

Ultimately, I found the database setup process for AWS, GCP, and Azure to be fairly straightforward; once I learned how to upload data to one of them using PostgreSQL, it was relatively easy to create tables for the other two. Setting up databases on Heroku and Snowflake required some extra steps, but both worked well with SQLAlchemy and the to_sql Pandas function. 

Meanwhile, the Databricks setup process was considerably more complex, since I chose to use pyodbc rather than SQLAlchemy due to the terms of service attached to MS Build Tools for Visual Studio, which I would have needed to install to connect SQLAlchemy and Databricks. Airtable made it easy to view my database data online, but there were significant limits on the amount of data that I could upload.

Based on my experiences, if I simply needed to create a PostgreSQL database using Python and SQLAlchemy, I would likely choose AWS, GCP, or Azure. However, I imagine that Snowflake, Heroku, Airtable, and Databricks would be compelling or superior options for other use cases.

### 1.2. Comparing database import and query times

**Note:** This summary is by no means a definitive assessment of the speeds of each database provider. My results were undoubtedly influenced by my configuration settings for each database, and different configurations would likely have resulted in different outcomes. In addition, the tests I used may not match real-world usage scenarios. I do not recommend using these results to make decisions about which database provider to use.

(Airtable was excluded from the testing process because it did not have enough capacity to import all of my original SQLite database's tables.)

I used four different tests to measure database speeds:

1. A full database import
2. A simple query
3. A simple query (repeated 1000 times)
4. A complex query

I ranked the databases based on the time required to complete each test, then combined the results into a composite ranking. That ranking is as follows:

| Provider | Composite Ranking | Sum of individual rankings| 
|-------|-------|-------|
|AWS|1|9|
|Azure|2|10|
|Snowflake|3|12|
|Heroku|4|14|
|GCP|5|16|
|Databricks|6|23|

A table showing both the composite and individual rankings for each database can be found [here](https://github.com/kburchfiel/python_database_utilities/blob/master/metrics/overall_database_query_rankings.csv).


The following charts, which can also be found in this repository's [metrics](https://github.com/kburchfiel/python_database_utilities/tree/master/metrics) folder, show how long each database took to complete each trial of each test.

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/full_import_time.png "Full import test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/simple_query_results_1x.png "First simple query test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/simple_query_results_1000x.png "Second simple query test")

![Image](https://raw.githubusercontent.com/kburchfiel/python_database_utilities/master/metrics/complex_query_time.png "Complex query test")

### 1.3. Database pricing

It would be difficult to provide a comprehensive overview of pricing differences for these seven providers. Prices vary greatly based on the parameters set for a given database (virtual CPU count, RAM, etc.) My recommendation would be to determine how powerful a database you need, then compare prices for that type of database.

The links below offer more information on free service options and pricing information for each database service, with a focus on PostgreSQL.

1. AWS
    
    a. [Amazon RDS for PostgreSQL is avaialble for free for 12 months with certain conditions.](https://aws.amazon.com/free/)

    b. [Amazon RDS for PostgreSQL Pricing](https://aws.amazon.com/rds/postgresql/pricing/)

2. GCP

    a. [Information about free services and credits can be found here.](https://cloud.google.com/free)

    Note: [there does not appear to be a free version of PostgreSQL for GCP.](https://www.googlecloudcommunity.com/gc/Databases/Free-Tier-Postgres/td-p/168143)

    b. [Cloud SQL for PostgreSQL pricing calculator](https://cloud.google.com/sql/docs/postgres/pricing)


3. Azure

    a. [Azure Database for PostgreSQL is free for 12 months with certain conditions.](https://azure.microsoft.com/en-us/pricing/free-services/)

    b. [Azure Database for PostgreSQL price calculator](https://azure.microsoft.com/en-us/pricing/details/postgresql/server/)

4. Snowflake

    a. [a 'start for free' option is available.](https://signup.snowflake.com/)

    b. [Price calculator](https://www.snowflake.com/pricing/)


5. Airtable

    Airtable has a free option, but it's limited to just 1,200 records. Even the Enterprise plan is limited to "100,000 records per base." (See [pricing](https://airtable.com/pricing) page)


6. Heroku

    Heroku's [pricing page](https://www.heroku.com/pricing) is focused on apps rather than databases. There is a 'Free and Hobby' plan for non-commercial projects. However, I ended up choosing the $9/month 'Hobby Basic' plan so that I could upload up to 10,000,000 rows of data. Otherwise, I would have been limited to 10,000 rows under the 'Hobby Dev' plan.

7. Databricks

    a. Databricks offers a [14-day free trial](https://databricks.com/try-databricks).

    b. Databricks has separate pricing pages for [AWS](https://databricks.com/product/aws-pricing), [GCP](https://databricks.com/product/gcp-pricing), and [Azure](https://databricks.com/product/azure-pricing).


## Part 2: Repository information

This repository contains three main .ipynb files along with a 'data' and 'metrics' folder.

**sqlite_database_builder.ipynb** shows how to import data sources into a local SQLite database.

**database_uploader.ipynb** demonstrates how to extract data from a SQLite database, then import it into various database services (Amazon Web Services, Google Cloud Platform, Microsoft Azure, etc.). SQLAlchemy and the to_sql Pandas function are used extensively within this program.

**database_query_timer.ipynb** provides code for timing the length of various database operations.

The data folder stores the original data used in constructing the SQLite database, and the metrics folder stores the output of the database_query_timer function.

**For additional documentation, see the pdu_documentation file (uploaded in both .docx and .pdf form).**

**Note:** Two files in the repository could not be uploaded to GitHub because they are above 100 megabytes in size. To access these files, use the following Google Drive links: (if these links break for whatever reason, let me know by posting an issue within this project.)

1. routes_planes_coordinates.csv: https://drive.google.com/file/d/1TBj5_zgdhtH8eBcPXLthqGgkJSRb4WFC/view?usp=sharing
2. sqlite_database.db: https://drive.google.com/file/d/1THyBZYXXT4le6zQz2SBhQlIjMk2MjhYz/view?usp=sharing
