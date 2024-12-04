Follow the following steps to create a PostgreSQL database named grafanadb, followed by creating two tables.

#### Step 1: Create the grafanadb Database

```bash
CREATE DATABASE grafanadb;
```
#### Step 2: Create the query\_timeline Table

Once the database is created, you'll need to switch to it using the \\c command in psql or through your connection interface (if you're using a GUI like pgAdmin). After switching to the grafanadb database, you can create the query\_timeline table:

```bash
CREATE TABLE query_timeline (
    query_name VARCHAR(25),
    status VARCHAR(25),
    runtime VARCHAR(25)
);
```
#### Step 3: Create the process\_status Table

Similarly, create the process\_status table:
```bash
CREATE TABLE process_status (
    process_name VARCHAR(25),
    status VARCHAR(25)
);
```


