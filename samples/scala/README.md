azure-cosmosdb-spark-samples-scala
============================
Examples of Cosmos DB on Spark that can serve as starting points for Scala-based Cosmos DB Spark projects.

Setup
-----
Before running any of the samples, you will need

1. A working version of SBT (or higher recommended).

2. The following enviroment variables set:

```
export COSMOS_DB_ENDPOINT=
export COSMOS_DB_MASTER_KEY=
```

3. A Cosmos DB database setup on Azure. You may run something like the following Azure CLI commands:

```
az cosmosdb database create --db-name samples --url-connection $COSMOS_DB_ENDPOINT --key $COSMOS_DB_MASTER_KEY
az cosmosdb collection create --collection-name airports --db-name samples --throughput 5000 --url-connection $COSMOS_DB_ENDPOINT --key $COSMOS_DB_MASTER_KEY
```

Running Samples
---------------
The easiest way to run the samples is to build a uber jar and submit it to spark like so (replace `com.microsoft.partnercatalyst.cosmosdb.samples.CSVToCosmos` with your prefered sample):

```
sbt assembly
spark-submit --class com.microsoft.partnercatalyst.cosmosdb.samples.CountByCountry target/scala-2.11/azure-cosmosdb-spark-samples-assembly-0.1-SNAPSHOT.jar
```