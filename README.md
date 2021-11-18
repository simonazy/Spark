# Spark

### DAG
![image](https://user-images.githubusercontent.com/56880104/142511395-9ad48035-b903-49a9-8bf3-f3fea9bbab38.png)


The concept of DAG: Directly Acyclic Graph exist in many big data analysis tools such as AirFlow, Spark.... What is DAG and how it works? The following will take DAG in Spark for an example. 

Spark is written by Scala. A functional programming language. We can manipulate Spark with the PySpark API, which is also written with functional programming principles in mind. 

Spark uses a functional programming concept called `lazy evaluation`. 

1. Before Spark does anything with the data in your program, it first built step-by-step direction of what functions and data it will need.  
2. Once Spark builds the DAG from your code, it checks if it can procrastinate, waiting until the last moment to get the data.
