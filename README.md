Cichlid
===============
Cichlid is a distributed RDFS & OWL reasoning system based on [Spark](http://spark.apache.org/). Now, the master branch is in version 0.1. 

##Prerequisites
As Cichlid is based on Spark, you need to get Spark installed first. If you are not clear about how to setup Spark, please refer to the guidelines [here](http://spark.apache.org/docs/latest/). Currently, Startfish runs on Spark 1.0.x or newer version.

##Building Cichlid
Cichlid is built using [sbt](http://www.scala-sbt.org/). We have offered a default **build.sbt** file to manage the whole project. Make sure you have installed [sbt](http://www.scala-sbt.org/) and you can just type *sbt compile* & *sbt package* to get an assembly jar in the project directory.
Note that the default Spark version and Hadoop version used are defined in file **build.sbt**, you can modify it if necessary.

##Run Cichlid
We use spark-submit scrpit provied by Apache Spark to submit our job, here follows the usages:

for RDFS reasoning:

	${SPARK_HOME}/
	./bin/spark-submit \
	--calss nju.cichlid.RDFS \
	--master master_url \
	--executor-memory xG \
	--total-executor-cores xx \
	<application-jar> <inputInstanceTripleFile>	<inputSchemaTripleFile>	<output>[<memoryFraction>]

for OWL reasoning:

	${SPARK_HOME}/
	./bin/spark-submit \
	--calss nju.cichlid.OWL \
	--master master_url \
	--executor-memory xG \
	--total-executor-cores xx \
	<application-jar> <inputInstanceTripleFile> <inputSchemaTripleFile> <output> <StorageLevel> [<memoryFraction>]


##Test Data
Here we provided a small dataset for testing is directory *data*. The file named **schema** is schema file, and **instance** is instance file. The RDF triples are transformed by MD5 hashfunction and stored in Sequence File format.

