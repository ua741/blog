---
title: "Hbase: Notes [Draft]" 
date: 2018-04-16T11:55:40+05:30
draft: true
tags: [
    "development",
    "hbase",
    "nosql"
]
---

#### Important Points:
* Relaxes the ACID (Atomicity, Consistency, Isolation & Durability) properties.
* Ideal for non-structured or semi structerd data.

#### Scalability:

-  **RDBMS**: VeriticalScalining:Easy:: HorizonatalScaling:Hard
-  **HBASE**: Easy to scale horizontally.
-  RDBMS Horizonatal Scaling
  *  Primarly designed for single node, not cluster mode.
  *  Sharding or Partition for scalining horizontally.
  *  Less control on querying, consistency and transactions across shards.

#### Distributed Joins
 * RDBMS: Data is normalized, storage efficient.
 * This Can lead to distributed join in RDBMS.
 * HBbase: Data which is accessed together, is stored together.

### HBase Arch
  * Data which is accessed together is stored together.
  * Grouping the data by key is central to running the cluster.
  * **KeyRange** is used for sharding the data accross cluster.
  * Scales by splitting rows into regions.
  * Each region is hosted by excatly one server.
  * Writes are held(stored) into the memory until flush.
  * Reads & writes to single are consistent.


### HBase DataModel:
Table: Design-time namespace, has many rows.
	row: atomic key/valye containers/map, with one row key
	column: a key in the k/v container inside the row.
	value: a value in the k/v container inside the row
Example
 - rowKey1 : [k1=v1, k2=v2, k3=v3]
 - rowKey2 : [k2=v2, k3,v4, k5,v5]
* Column Families/Qualifiers: Controlling the performance characterstics of a table by grouping a set of columns by grouping a set of columns into a locality group. Divide columns into a physical files.
* Table and column family names are characters [Written into file system]
* Every "cell" (i.e. time-verioned value of one column in one row) is stored fully qualified (with its full rowKey, column family, column name etc) on disk.

* No foriegn keys or joins or cross table transactions.
* Hbase can define columns at runTime. A column does not have to represent a prede
* Nested entities.
* Coulmn families are just name spaces.




