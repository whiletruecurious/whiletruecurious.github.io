---
layout: post
title:  "PySpark development environment with debugger; leveraging PyCharm on mac"
author: dev
categories: [spark, pyspark, pycharm, bigdata, python, tech]
image: https://www.isdi.education/sites/default/files/styles/noticia_basico/public/noticias/big-data.png?itok=KjsLse-P
featured: true
hidden: true

---

# Working on HIVE

Apache Hive is a popular SQL interface for batch processing†on Hadoop... As we all know, Hadoop was built to organize and store massive amounts of data† . Hive gives another way to access Data inside the cluster in easy, quick way.

 Hive  provides a query language called†HiveQL†that closely resembles the common†Structured Query Language†(SQL) standard.  Hive †was one of the earliest project to  bring higher-level languages to Apache Hadoop. Hive Gives ability to  Analysts and Scientists to access data with out being expert in Java . Hive gives structure to Data on HDFS making it data warehousing platform. This interface to Hadoop not only accelerates the time required to produce results from data analysis, it significantly broadens who can use Hadoop and MapReduce. Let us take a moment to thank facebook team because Hive was developed by the Facebook Data team and, after being used internally, it was contributed to the Apache Software Foundation .Currently Hive is freely available as an open source software from Apache. 

Let us discuss used cases of Hive. Hive is typically used to place Large amount of unstrcured /Semi structured data on Hadoop and build Structure  of it.. Hive is best suited for batch jobs over Large Set of data for example WebLogs, Network Router logs. Analysts would be able query data on Ad-hoc basis to Data Analysis. Stable Version of hive is 0.13

Ok now we know what is hive , Motivation for Hive  and Used Cases of Hive , let us understand what Hive is not. Hive is not a Database  

Let us understand difference between RDBMS and HIVE

 RDBMS Stores Data, where as Hive uses Data which is on Hadoop and does not store actual data. RDBMS support for both OLTP AND OLAP , WHERE AS HIVE IS FOR OLAP.   . Hive in traditional is used for large scale volume. Hive is best suited for data warehouse applications, where there is no need for  real-time responsiveness to queries are not required.

 Hive looks very much like traditional database code with SQL access. However, because Hive is based on Hadoop and MapReduce operations  Hive is more used for batch processing.  Hadoop is intended for long sequential scans, and because Hive is based on Hadoop, you can expect queries to have a very high latency (many minutes). .Latency for hive queries is high for even for small jobs which means that Hive would not be appropriate for applications that need very fast response times.

In this Sample Table : if we want to delete SAM Rating on Documentary, in a RDBMS Table, we can run update/Delete  command to Update/ delete it, where as in Hive we cannot update/Delete a particular value. This kind of transactions are not supported in Hive. But Hive supports Overwrite of the entire table or appending additional Data to this table. Let us proceed to discuss Hive Architecture.

Hive is not 100 % SQL. HQL is limited in the commands it understands. Not all SQL commands work on Hive,  for example, Updates and deletes are not supported. 



What is Hive ?

Apache Hive is a popular SQL interface for batch processing on Hadoop. Hadoop was built to organize and store massive amounts of data Hive gives another way to access Data inside the cluster in easy, quick way.

 Hive  provides a query language called HiveQL that closely resembles the common Structured Query Language (SQL) standard.  Hive  was one of the earliest project to  bring higher-level languages to Apache Hadoop. Hive Gives ability to  Analysts and Data Scientists to access data with out being expert in Java . Hive gives structure to Data on HDFS making it data warehousing platform. This interface to Hadoop not only accelerates the time required to produce results from data analysis, it significantly broadens who can use Hadoop and MapReduce. Let us take a moment to thank Facebook team because Hive was developed by the Facebook Data team and, after being used internally, it was contributed to the Apache Software Foundation .Currently Hive is freely available as an open source software from Apache. 

SQL for Hadoop
HQL #  No need to be expert in Java
Easier to Learn and Many People Know already
Structure to Data on HDFS
Thank you Facebook
Open Source Project managed by ASF

![image](https://user-images.githubusercontent.com/15700993/53741956-899cb380-3ebd-11e9-8ca0-2e45728ac5c4.png)



### Databases in Hive:

The concept database is just a catalog or a namespace of tables.

It is important to create databases before we create the tables so that permissions can be given to users at database levels. it also avoids table name collisions.

If we don't specify a particular database well creating a table the default database is used.

**In this tutorial. Let us try to understand how to:**

* CREATE DATABASE
* DESCRIBE DATABASE
* ALTER DATABASE
* DROP DATABASE


##### Displaying Databases in Hive

`SHOW DATABASES` command will provide the list of all the databases that are present in the cluster.

```sql
hive> SHOW DATABASES;
OK
default
Time taken: 6.017 seconds, Fetched: 3 row(s)
```

If we have to pull multiple databases inside the cluster we can use regular expressions. In this example let us try to grab the database inside the cluster which starts with the letter `m`.

```sql
hive> SHOW DATABASES like ‘m*’;
OK
movies
Time taken: 6.017 seconds, Fetched: 3 row(s)
```

##### Creating Databases in Hive

```sql
hive> CREATE DATABASE movies;
OK
Time taken: 6.014 seconds
```

Note: Hive will throw the error if the movie's database already exists.

```sql
hive> CREATE DATABASE movies;

FAILED: Execution Error, return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. Database movies already exists
```

To suppress the above warning we can provide another variation of create database command with `IF NOT EXISTS` keywords.

```sql
hive> CREATE DATABASE IF NOT EXISTS movies;
OK
Time taken: 6.014 seconds

```

We can also add a comment which will help us to understand more about the database. Let us create a database but adding a couple of comments.

```sql
hive> CREATE DATABASE IF NOT EXISTS Movies_Database comment ‘Holds Users ratings on all the movies’;
OK
Time taken: 6.014 seconds

```

Let us use this command to understand about a particular database. In this example we are describing about the database movies.

```sql
hive> DESCRIBE DATABASE movies;
OK
movies          hdfs://ip-10-143-129-157.ap-southeast-1.compute.internal:8020/user/hive/warehouse/movies.db     hadoop  USER
Time taken: 6.016 seconds, Fetched: 1 row(s)
```

As you can see when the database is created HIVE creates a directory inside the HDFS under the `warehouse` directory, All the tables inside the database will be stored in the subdirectories on the main database directory.

`DFS` command helps to run Hadoop commands on the HIVE command line interface.
Let us check inside the warehouse directory with the help of the DFS command. movies directory it is created inside hive warehouse directory.

we can override this default the location of warehouse with the new directory location under prefered path for that particular database.

```sql
hive> CREATE DATABASE accounting
    > LOCATION '/user/cloudera';
OK
Time taken: 8.035 seconds
```

##### Altering Databases in Hive

Once the databases are created in HIVE we can only alter the database properties, no other metadata properties can be changed once the database is created. If we want to change the datebase name or change the datebase location, we need to drop the database and recreate a new database.

```sql
hive> ALTER DATABASE movies SET DBPROPERTIES ('edited-by' = 'DEV');
OK
Time taken: 6.021 seconds
```

##### Dropping Databases in Hive

A database can be dropped with just a simple command like `drop database <database_name>`. We can also pass `if exists` optional parameters in order to suppress the warnings if database doesn't exist.

By default HIVE does not premits to drop a database if it has any table is inside it. To drop a database first we need to drop the tables inside it or append the keyword `CASCADE` to the `drop database` command.

```sql
hive> use movies;
OK
Time taken: 6.023 seconds
hive> set hive.cli.print.current.db=true;
hive (movies)> create table testtable(column1 int);
OK
Time taken: 8.284 seconds
hive (movies)> drop database movies;
FAILED: Execution Error, return code 1 from org.apache.hadoop.hive.ql.exec.DDLTask. InvalidOperationException(message:Database movies is not empty. One or more tables exist.)
hive (movies)> drop database movies CASCADE;
OK
Time taken: 8.987 seconds
```

`Note: ‘set hive.cli.print.current.db=true;’ command will print current database name in cli`



### DataTypes in Hive:

### Two Types:
* Primitive Data Type
* Complex Data Type

![image](https://user-images.githubusercontent.com/15700993/53741565-b56b6980-3ebc-11e9-8046-f5fa34e5089b.png)

![image](https://user-images.githubusercontent.com/15700993/53742072-cf597c00-3ebd-11e9-8e5f-f4cc4c6635f6.png)

![image](https://user-images.githubusercontent.com/15700993/53742261-3ecf6b80-3ebe-11e9-9bd6-af9c513a4f7d.png)

![image](https://user-images.githubusercontent.com/15700993/53742400-8ce46f00-3ebe-11e9-805f-1bdae3bbc187.png)

Note: As hive support schema-on-read at any point of time after analyzing the dataset we can always tweak the data type for a perticular column bases on the value set.



