These are first attempts at Spark. I try to solve a question on StackOverflow that attracts a lot of interest. It was viewed 28,494 times in 3 years, until summer 2019, and I stumbled over it, too:
https://stackoverflow.com/questions/39355149/how-to-read-json-with-schema-in-spark-dataframes-spark-sql

My goal is to explicitly define a schema for this json structure that, well, actually works. I find it's remarkably hard.

### Prerequisites

Download Spark from https://spark.apache.org/downloads.html

You'll need Java, and if you plan to use Python, python. Alternatively, use scala - the way we use it here it's not scary. I'll use scala below.

Start a scala shell, cd to your Spark Home (for me, `cd $HOME/spark-2.4.3-bin-hadoop2.7`) and run:  `bin/spark-shell`. 
First, have a look at the inferred schema:
```
var file = "/your_path_to/stackoverflow.json"
var df_inferred = spark.read.format("json").option("inferSchema", "true").load(file)
df_inferred.show(3)
df_inferred.printSchema()

```
Now, let's define the schema explicity. It's quite complicated with all those objects and arrays. And it fails. Run the code in define_json_schema.txt, and then use it for your data frame: 

```
scala> var df_explicit = spark.read.format("json").option("inferSchema", "false").schema(accountSchema).load(file)
df_explicit: org.apache.spark.sql.DataFrame = [accountid: string, accountdetails: struct<category: struct<currentinfo: struct<value: int>, subcategory: array<string> ... 1 more field>, total: double> ... 1 more field]

scala> df_explicit.show(3)
+---------+--------------+--------+
|accountid|accountdetails|billdate|
+---------+--------------+--------+
|     null|          null|    null|
|     null|          null|    null|
|     null|          null|    null|
+---------+--------------+--------+


scala> 

```

Not good.



