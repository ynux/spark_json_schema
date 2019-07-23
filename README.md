These are first attempts at Spark. I try to solve a question on StackOverflow that attracts a lot of interest. It was viewed 28,494 times in 3 years, until summer 2019, and I stumbled over it, too:
https://stackoverflow.com/questions/39355149/how-to-read-json-with-schema-in-spark-dataframes-spark-sql

My goal is to explicitly define a schema for this json structure that, well, actually works. I find it's remarkably hard.

### Prerequisites

Download Spark from https://spark.apache.org/downloads.html

You'll need Java, and if you plan to use Python, python. Alternatively, use scala - the way we use it here it's not scary. I'll use scala below.

Start a scala shell with:





