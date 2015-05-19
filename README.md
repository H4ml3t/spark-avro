# Spark SQL Avro Library

A library for querying Avro data with [Spark SQL](http://spark.apache.org/docs/latest/sql-programming-guide.html).

## Version
This is the version 0.1 of [https://github.com/databricks/spark-avro](https://github.com/databricks/spark-avro) with a fix for a bug with Spark 1.2.0 and Scala 2.10.4 for *Long Type not supported*:

```
java.lang.RuntimeException: Unsupported type LONG
    at scala.sys.package$.error(package.scala:27)
    at com.databricks.spark.avro.AvroRelation.com$databricks$spark$avro$AvroRelation$$toSqlType(AvroRelation.scala:116)
    at com.databricks.spark.avro.AvroRelation$$anonfun$5.apply(AvroRelation.scala:97)
    at com.databricks.spark.avro.AvroRelation$$anonfun$5.apply(AvroRelation.scala:96)
    at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
    at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
```

## Building
This library is built with [SBT](http://www.scala-sbt.org/0.13/docs/Command-Line-Reference.html), which is automatically downloaded by the included shell script. To build a JAR file simply run `sbt/sbt package` from the project root.

As an alternative you can import the classes under the path ```src/main/scala/com/databricks/spark/avro``` inside your project and build with Maven [read this article to see how create a project to build a Spark Scala jar](https://nosqlnocry.wordpress.com/2015/02/27/how-to-build-a-spark-fat-jar-in-scala-and-submit-a-job/).

## Using with Spark
This library requires Spark 1.2+.

The jar file produced above can be added to a spark using the `--jars` command line option.  For example, to include it when starting the spark shell:

```
$ bin/spark-shell --jars ../sql-avro/target/scala-2.10/sql-avro_2.10-0.1.jar
```
