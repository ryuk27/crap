
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

## 🅔 HDFS and External Table Setup

```bash
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
