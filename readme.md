## Python Database Utilities

By Kenneth Burchfiel

Released under the MIT license


This repository contains scripts for creating, modifying, and testing databases using Python.

**sqlite_database_builder** shows how to import data sources into a local SQLite database.

**database_uploader** demonstrates how to extract data from a SQLite database, then import it into various database services (Amazon Web Services, Google Cloud Platform, Microsoft Azure, etc.). SQLAlchemy and the to_sql Pandas function are used extensively within this program.

**database_query_timer** provides code for timing the length of various database operations.

The data folder stores the original data used in constructing the SQLite database, and the metrics folder stores the output of the database_query_timer function.

More information about these scripts and the repository as a whole will be provided in the future.