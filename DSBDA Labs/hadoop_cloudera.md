# Hadoop/Cloudera FAQ

## Hadoop Framework Interface
Users can interface with Hadoop through web UIs like YARN ResourceManager (port 8088), NameNode (port 50070/9870), Hue, or Cloudera Manager.

## Hadoop Configuration Files
- `core-site.xml`
- `hdfs-site.xml`
- `mapred-site.xml`
- `yarn-site.xml`
- `hadoop-env.sh`

## Multinode Cluster
A Hadoop deployment with multiple machines working together, having dedicated master nodes and multiple slave nodes.

## Reporter Usage
Updates task progress, emits counter values, and sends status messages during MapReduce execution.

## Putting Input Files in HDFS
Use: `hdfs dfs -put localfile.txt /destination/path/`

## Speculative Execution
Mechanism where Hadoop runs duplicate instances of slow tasks, keeping results from whichever finishes first.

## Basic Parameters of a Mapper
Input key, input value, output key, output value.

## Function of MapReducer Partitioner
Determines which reducer receives which keys from mapper output.

## Difference Between Input Split and HDFS Block
HDFS Block is physical storage division; Input Split is logical division for processing.

## JobTracker Task Scheduling
Schedules based on data locality, resource availability, and TaskTracker health.

## Hive Sorting Operations
- **ORDER BY**: Global sort (total order)
- **SORT BY**: Sort within reducer (partial order)
- **DISTRIBUTE BY**: Controls data distribution to reducers
- **CLUSTER BY**: Combines DISTRIBUTE BY and SORT BY

## HBase vs. Hive
Hive: SQL-like data warehouse; HBase: NoSQL database for real-time access.

## Default Hive Metastore Database
Apache Derby.

## Apache HBase and Its Use
Distributed NoSQL database for real-time random access to big data.

## Key Components of HBase
HMaster, RegionServer, Zookeeper, Region, Client, META tables, WAL.

## Use of get() Method
Retrieves data for a specific row by its row key.

## Reason for Using HBase
Real-time random read/write access to large datasets with high throughput.

## Column Families in HBase
Groups of related columns stored together physically on disk.

## Standalone Mode in HBase
Non-distributed configuration where all HBase daemons run in a single JVM.

## RegionServer
Hosts and manages regions, handles read/write requests.

## Use of MasterServer and HMaster
Manages region assignment, RegionServer registration, and metadata operations.

## Operational Commands of HBase
`status`, `create`, `list`, `disable/enable`, `describe`, `scan/get/put/delete`, `truncate`.

## Command to Run HBase Shell
`hbase shell`

## Use of ZooKeeper
Provides coordination services, configuration management, and failure detection.