# Spark Sample Project
**Note:** this file will be used in some of the examples shown in `spark-test.ipynb`

This is a **dummy project** to demonstrate working with **Apache Spark** using Python (`pyspark`).  
It contains some sample data, Spark DataFrame examples, and basic transformations.

---

## Overview

Apache Spark is a **distributed computing framework** that allows processing of large datasets across multiple machines.  
It provides APIs for Python, Scala, Java, and R, with built-in support for SQL, machine learning, and streaming.

In this project, we will use **Spark DataFrames** to handle tabular data efficiently.

---

## Sample Spark Operations

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Create Spark session
spark = SparkSession.builder.appName("DummyProject").getOrCreate()

# Load sample CSV
df = spark.read.option("header", True).csv("sample_data.csv")

# Show first 5 rows
df.show(5)

# Filter rows using Spark
high_population = df.filter(col("population") > 100000)
high_population.show()

# Count total rows
total_rows = df.count()
print(f"Total rows in DataFrame: {total_rows}")
