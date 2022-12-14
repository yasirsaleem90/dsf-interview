#Evaluation of the solution:

##Persists:
Persists is used to put dataframe in cache for high speed processing , performance is maintained for fill and pivot functions

##Repartition: 
coalesce() function limit the re-distribution of data from all partitions which is full shuffle leading to very expensive operation when dealing with billions and trillions of data.Calling groupBy(), union(), join() and similar functions on DataFrame results in shuffling data between multiple executors and even machines and finally repartitions data into 200 partitions by default.

##Garbage Collection

I have used garbage collection as Spark runs on the Java Virtual Machine and it can store large amounts of data in memory, it has a major reliance on Java's memory management and garbage collection (GC). Therefore, garbage collection (GC) can be a major issue that can affect many Spark applications

#Further Options:

##File Format:
A Spark job can be optimized by choosing the parquet file with snappy compression. Parquet file is native to Spark which carry the metadata along with its footer as we know parquet file is native to spark which is into the binary format and along with the data it also carry the footer it’s also carries the metadata and its footer so whenever you create any parquet file, you will see .metadata file  on the same directory along with the data file

##MarshalSerializer
Serializes objects using Python’s Marshal Serializer. This serializer is faster than PickleSerializer.

##Spark Streaming:
We can use structured spark streaming as it is built on top of SparkSQL engine of Apache Spark which will deal with running the stream as the data continues to recieve. Just like the other engines of Spark, it is scalable as well as it is fault-tolerant. Structured Streaming enhances Spark DataFrame APIs with streaming features

