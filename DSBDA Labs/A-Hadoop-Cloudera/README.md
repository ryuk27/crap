
# 🐘 Cloudera Hive Practical – README

This document contains all Hive commands executed in the Cloudera environment for your practicals. Each section is labeled and contains the command followed by its **significance** for clarity and understanding.

---

## 🅐 Create, Drop and Alter Tables

```bash
[cloudera@quickstart ~]$ hive
```
**▶️ Significance:** Launches the Hive shell on the Cloudera system.

```sql
hive> create database mydb2;
```
**▶️ Significance:** Creates a new Hive database named `mydb2`.

```sql
hive> use mydb2;
```
**▶️ Significance:** Sets `mydb2` as the current working database.

```sql
hive> create table flight(fno int,year int,dest varchar(10),delay float);
```
**▶️ Significance:** Creates a table named `flight` with 4 columns for storing flight data.

```sql
hive> alter table flight rename to air_flight;
```
**▶️ Significance:** Renames the `flight` table to `air_flight`.

```sql
hive> alter table air_flight add columns(source varchar(10));
```
**▶️ Significance:** Adds a new column `source` to the existing `air_flight` table.

```sql
hive> drop table flight;
```
**▶️ Significance:** Deletes the original `flight` table (if it still exists).

```sql
hive> desc air_flight;
```
**▶️ Significance:** Displays the schema (structure) of the `air_flight` table.

---

## 🅒 Load Table with Data, Insert New Values, Joins

```sql
hive> create table flight(fno int,year int,dest varchar(10),delay float)
    > row format delimited
    > fields terminated by ','
    > lines terminated by '\n'
    > stored as textfile;
```
**▶️ Significance:** Creates a new `flight` table where data is stored as a textfile with fields separated by commas.

```sql
hive> insert into flight values(123,2009,'mumbai',30.6);
hive> insert into flight values(124,2008,'pune',50.6);
```
**▶️ Significance:** Inserts two rows of sample flight data.

```sql
hive> select * from flight;
```
**▶️ Significance:** Retrieves and displays all records from the `flight` table.

```sql
// create a file name f.txt on desktop and add values in similar form eg. 123,2009,'mumbai',30.6
hive> load data local inpath "f.txt"
    > overwrite into table flight;
```
**▶️ Significance:** Loads data from the local file `f.txt` into the `flight` table, replacing existing data.

```sql
hive> select * from flight;
```
**▶️ Significance:** Confirms data has been loaded by displaying the table content.

```sql
hive> create table nflight(fno int,year int,source varchar(10))
    > row format delimited
    > fields terminated by ','
    > lines terminated by '\n'
    > stored as textfile;
```
**▶️ Significance:** Creates a new table `nflight` with different structure for demonstrating joins.

```sql
hive> insert into nflight values(923,2009,'pune');
```
**▶️ Significance:** Adds a sample row to the `nflight` table.

```sql
hive> select a.fno,a.year,a.dest,a.delay,b.source
    > from flight a join nflight b
    > on (a.fno=b.fno);
```
**▶️ Significance:** Performs an inner join on `flight` and `nflight` using the `fno` field.

```sql
hive> select * from nflight;
hive> select * from flight;
// Checking all tables
```
**▶️ Significance:** Verifies contents of both tables involved in the join.

---

## 🅓 Create Index on Flight Information Table

```sql
hive> create index flight_index on table flight(fno)
    > as 'org.apache.hadoop.hive.ql.index.compact.CompactIndexHandler'  
    > WITH DEFERRED REBUILD;
// Can replace 'org.apache.hadoop.hive.ql.index.compact.CompactIndexHandler' with 'COMPACT'
```
**▶️ Significance:** Creates an index on `fno` column to improve query performance (deferred rebuild means index will be built later).

```sql
hive> show tables;
// Verifying index created and table exists
```
**▶️ Significance:** Lists all tables in the current database to confirm index and table exist.

---

## 🅑 Create External Hive Table

```sql
hive> create database mydb3;
hive> use mydb3;
```
**▶️ Significance:** Creates and switches to a new database `mydb3`.

```sql
hive> create table hive_int(id int,name varchar(10),sal float) 
    > row format delimited
    > fields terminated by ','
    > lines terminated by '\n'
    > stored as textfile;
```
**▶️ Significance:** Creates a managed table `hive_int` for employee data.

```sql
// Create a file name data.txt on desktop and add values in similar form eg. 1,'aakash',50.0
hive> load data local inpath 'data.txt' into table hive_int;
```
**▶️ Significance:** Loads local data from `data.txt` into `hive_int`.

```sql
hive> select * from hive_int;
// Checking data loaded into hive_int
```
**▶️ Significance:** Displays contents of `hive_int`.

```sql
hive> create external table hive_ext(id int,name varchar(10),sal float)
    > row format delimited
    > fields terminated by ','
    > lines terminated by '\n'
    > stored as textfile;
```
**▶️ Significance:** Creates an external table `hive_ext`—data is stored outside Hive's warehouse directory.

```sql
hive> insert into hive_ext select * from hive_int;
```
**▶️ Significance:** Copies all data from the internal table to the external table.

```sql
hive> select * from hive_ext;
// Verifying transfer from hive_int to hive_ext
```
**▶️ Significance:** Confirms successful transfer by displaying contents of `hive_ext`.

---

## 🅔 Find the average departure delay per day in 2008

```bash
//Open A Terminal, that's Terminal 1 for you
[cloudera@quickstart ~]$ hdfs dfs -mkdir /HiveDirectory
```
**▶️ Significance:** Creates a new directory in HDFS for storing Hive data.

```bash
[cloudera@quickstart ~]$ hdfs dfs -put hive/emp_details /HiveDirectory
// Error shown due to file not present
```
**▶️ Significance:** Attempts to upload a local file to HDFS.

```bash
[cloudera@quickstart ~]$ hive
```
**▶️ Significance:** Reopens Hive shell.

```sql
hive> create external table emplist (Id int, Name string , Salary float)
    > row format delimited
    > fields terminated by ',' 
    > location '/HiveDirectory';
```
**▶️ Significance:** Creates an external table `emplist` using data from `/HiveDirectory`.

```sql
hive> select * from emplist;
```
**▶️ Significance:** Displays contents of `emplist` (if data was successfully loaded).

```sql
hive> CREATE TABLE flight_data(
    >    year INT,
    >    month INT,
    >    day INT,
    >    day_of_week INT,
    >    dep_time INT,
    >    crs_dep_time INT,
    >    arr_time INT,
    >    crs_arr_time INT,
    >    unique_carrier STRING,
    >    flight_num INT,
    >    tail_num STRING,
    >    actual_elapsed_time INT,
    >    crs_elapsed_time INT,
    >    air_time INT,
    >    arr_delay INT,
    >    dep_delay INT,
    >    origin STRING,
    >    dest STRING,
    >    distance INT,
    >    taxi_in INT,
    >    taxi_out INT,
    >    cancelled INT,
    >    cancellation_code STRING,
    >    diverted INT,
    >    carrier_delay STRING,
    >    weather_delay STRING,
    >    nas_delay STRING,
    >    security_delay STRING,
    >    late_aircraft_delay STRING
    > )
    > ROW FORMAT DELIMITED
    > FIELDS TERMINATED BY ',';
```
**▶️ Significance:** Defines the structure of the `flight_data` table. It maps each column in the CSV file to its corresponding data type. The use of `ROW FORMAT DELIMITED` and `FIELDS TERMINATED BY ','` specifies that the data is in CSV format.
```sql
//Now open another terminal, that's terminal 2 for you
hive> [cloudera@quickstart ~]$ hive
```
**▶️ Significance:** You open a new Hive shell session in another terminal to continue executing commands. This simulates a typical use case where Hive runs independently from the file system terminal.
```sql
//NEED A CSV FILE TO PERFORM, HERE IT IS 2008.CSV, MUST BE GIVEN TO YOU BY EXAMINER
hive> LOAD DATA LOCAL INPATH '/home/cloudera/2008.csv' OVERWRITE INTO TABLE flight_data;
```
**▶️ Significance:** Loads data from the local file system into the `flight_data` Hive table. The `OVERWRITE` keyword ensures any previous data in the table is replaced with this fresh dataset.
```sql
hive> SHOW TABLES;
```
```sql
hive> SELECT avg(arr_delay)
    FROM flight_data
    WHERE month = 1
    AND origin = 'SFO';
```
**▶️ Significance:** Computes the average arrival delay of flights originating from SFO in the month of January. This is a basic aggregation query demonstrating the analytical power of Hive.
