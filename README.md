# Spark

Principle one: Always refer to the [PySpark](http://spark.apache.org/docs/latest/api/python/) Documentation when run into bugs!

### Understanding DAG
![image](https://user-images.githubusercontent.com/56880104/142511395-9ad48035-b903-49a9-8bf3-f3fea9bbab38.png)


The concept of DAG: Directly Acyclic Graph exist in many big data analysis tools such as AirFlow, Spark.... What is DAG and how it works? The following will take DAG in Spark for an example. 

Spark is written by Scala. A functional programming language. We can manipulate Spark with the PySpark API, which is also written with functional programming principles in mind. 

Spark uses a functional programming concept called `lazy evaluation`. 

1. Before Spark does anything with the data in your program, it first built step-by-step direction of what functions and data it will need.  
2. Once Spark builds the DAG from your code, it checks if it can procrastinate, waiting until the last moment to get the data.


## General functions
T1he following general functions in Spark are quite similar to methods of Pandas dataframes:

- select(): returns a new dataframe with the selected columns
- filter(): filters rows using the given condition
- where(): is just an alias for filter()
- groupBy(): groups the DataFrame using the specified columns, so we can run aggregation on them
- sort(): returns a new DataFrame sorted by the specified column(s). By default the second parameter 'ascending' is True
- dropDuplicates(): returns a new dataframe with unique rows based on all or just a subset of columns
- withColumn(): returns a new DataFrame by adding a column or replacing the existing column that has the same name. The first parameter is the name of the new column, the second is an expression of how to compute it

## Aggregate functions
Spark SQL provides built-in methods for the most common aggregations such as count(), countDistinct(), avg(), max(), min(), etc. in the pyspark.sql.functions module. These methods are not the same as the built-in methods in the Python Standard Library, where we can find min() for example as well, hence you need to be careful not to try to use them interchangeably.

In many cases, there are multiple ways to express the same aggregations. For example, if we would like to compute one type of aggregate for one or more columns of the dataframe we can just simply chain the aggregate method after a groupBy(). If we would like to use different functions on different columns agg() comes in handy. For example agg({"salary": "avg", "age": "max"}) computes the average salary and maximum age.

## User defined functions (UDF)
In Spark SQL we can define our own functions with the udf method from the pyspark.sql.functions module. The default type of the returned variable for UDFs is string. If we would like to return an other type we need to explicitly do so by using the different types from the pyspark.sql.types module.

## Window functions
Window functions are a way of combining the values of ranges of rows in a dataframe. When defining the window we can choose how to sort and group (with the partitionBy method) the rows and how wide of a window we'd like to use (described by rangeBetween or rowsBetween).

For further information see the [Spark SQL, DataFrames and Datasets Guide](https://spark.apache.org/docs/latest/sql-programming-guide.html) and the [Spark Python API Docs](https://spark.apache.org/docs/latest/api/python/index.html) .
