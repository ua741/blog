---
title: "HBase : notes"
date: 2018-07-31T11:55:40+05:30
draft: false
tags: [
    "notes",
    "hbase"
]
---
# What is HBase
* NoSql datastore build on the top of HDFS filesystem
* Column Family oriented database
* Based on Google BigTable paper
* Data can be quickly retrieved or back processed with MapReduce/Spark or any other similar processing engine.

# Use Cases
* Need Big data
* High Throughput
* Variable columns
* Random reads and writes

# Components of HBase

### HDFS Service:
* Standby NameNode (A)
* Active NameNode
* Data Node (B)

### HBase Service
* Masters [A]
* Doing all coordination with the region servers
* More than one master for HA
* Region Server (B)

### ZooKeeper
* Use zookeeper quorum to select a master.
* How big the quorum needs to be?

### Yarn Server
* Doing the work of processing.


# Table Arch
 * Column Descriptor (Identify the columns)
 * Row Key (row identifier)
 * Table namesapce
 * Data

**Column Families** 

* Stores frequently accessed data together.  Settings can be customized per family bases.
* Previous versions of the data can be accessed. Column can be missing. Non-existense of data is like null value in RDBMS.
* user_data
* pictures


# Regions
* Tables are broken into smaller pieces called regions. Regions are divided by row keys.

**Write Path**
* Master will figure to which particular region server should the write go to. Master use rowKey to identify that.

# HBase API
* Primarily JAVA APIs
* Rest Interfaces
* Thrift gateway
* **Non-Native SQL Interfaces** : Apache Phenix, Impala, Presto, Hive

# Differences with RDBMS
* RDBMS is about relationships or normalized data
* HBase is about access patterns or denormalizing data

**Questions to ask**

* How is the data being accessed?
* What is the fastest way to read/write data?
* What is the optimal way to organize the data?

# Schema Design and Row Keys
* Only one index/primary key
* Normally row key is composed of multiple vectors.
**General Best Practices**
* Fewer, bigger(denormalized) tables
* Spend some time in designing upfront.
* Use bulk loading for incremental/time series data

todo: add source and images
