## Python Database Utilities

By Kenneth Burchfiel

Released under the MIT license


This repository contains scripts for creating, modifying, and testing databases using Python.

**sqlite_database_builder** shows how to import data sources into a local SQLite database.

**database_uploader** demonstrates how to extract data from a SQLite database, then import it into various database services (Amazon Web Services, Google Cloud Platform, Microsoft Azure, etc.). SQLAlchemy and the to_sql Pandas function are used extensively within this program.

**database_query_timer** provides code for timing the length of various database operations.

The data folder stores the original data used in constructing the SQLite database, and the metrics folder stores the output of the database_query_timer function.

For additional documentation, see the pdu_documentation file (uploaded in both .docx and .pdf form).

**Note:** Two files in the repository could not be uploaded to GitHub because they are above 100 megabytes in size. To access these files, use the following Google Drive links: (if these links break for whatever reason, let me know by posting an issue within this project.)

1. routes_planes_coordinates.csv: https://drive.google.com/file/d/1TBj5_zgdhtH8eBcPXLthqGgkJSRb4WFC/view?usp=sharing
2. sqlite_database.db: https://drive.google.com/file/d/1THyBZYXXT4le6zQz2SBhQlIjMk2MjhYz/view?usp=sharing
