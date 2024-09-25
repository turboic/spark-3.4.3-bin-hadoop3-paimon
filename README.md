# Apache Spark

Spark is a unified analytics engine for large-scale data processing. It provides
high-level APIs in Scala, Java, Python, and R, and an optimized engine that
supports general computation graphs for data analysis. It also supports a
rich set of higher-level tools including Spark SQL for SQL and DataFrames,
pandas API on Spark for pandas workloads, MLlib for machine learning, GraphX for graph processing,
and Structured Streaming for stream processing.

<https://spark.apache.org/>

[![GitHub Actions Build](https://github.com/apache/spark/actions/workflows/build_main.yml/badge.svg)](https://github.com/apache/spark/actions/workflows/build_main.yml)
[![AppVeyor Build](https://img.shields.io/appveyor/ci/ApacheSoftwareFoundation/spark/master.svg?style=plastic&logo=appveyor)](https://ci.appveyor.com/project/ApacheSoftwareFoundation/spark)
[![PySpark Coverage](https://codecov.io/gh/apache/spark/branch/master/graph/badge.svg)](https://codecov.io/gh/apache/spark)
[![PyPI Downloads](https://static.pepy.tech/personalized-badge/pyspark?period=month&units=international_system&left_color=black&right_color=orange&left_text=PyPI%20downloads)](https://pypi.org/project/pyspark/)


## Online Documentation

You can find the latest Spark documentation, including a programming
guide, on the [project web page](https://spark.apache.org/documentation.html).
This README file only contains basic setup instructions.

## Building Spark

Spark is built using [Apache Maven](https://maven.apache.org/).
To build Spark and its example programs, run:

```bash
./build/mvn -DskipTests clean package
```

(You do not need to do this if you downloaded a pre-built package.)

More detailed documentation is available from the project site, at
["Building Spark"](https://spark.apache.org/docs/latest/building-spark.html).

For general development tips, including info on developing Spark using an IDE, see ["Useful Developer Tools"](https://spark.apache.org/developer-tools.html).

## Interactive Scala Shell

The easiest way to start using Spark is through the Scala shell:

```bash
./bin/spark-shell
```

Try the following command, which should return 1,000,000,000:

```scala
scala> spark.range(1000 * 1000 * 1000).count()
```

## Interactive Python Shell

Alternatively, if you prefer Python, you can use the Python shell:

```bash
./bin/pyspark
```

And run the following command, which should also return 1,000,000,000:

```python
>>> spark.range(1000 * 1000 * 1000).count()
```

## Example Programs

Spark also comes with several sample programs in the `examples` directory.
To run one of them, use `./bin/run-example <class> [params]`. For example:

```bash
./bin/run-example SparkPi
```

will run the Pi example locally.

You can set the MASTER environment variable when running examples to submit
examples to a cluster. This can be a mesos:// or spark:// URL,
"yarn" to run on YARN, and "local" to run
locally with one thread, or "local[N]" to run locally with N threads. You
can also use an abbreviated class name if the class is in the `examples`
package. For instance:

```bash
MASTER=spark://host:7077 ./bin/run-example SparkPi
```

Many of the example programs print usage help if no params are given.

## Running Tests

Testing first requires [building Spark](#building-spark). Once Spark is built, tests
can be run using:

```bash
./dev/run-tests
```

Please see the guidance on how to
[run tests for a module, or individual tests](https://spark.apache.org/developer-tools.html#individual-tests).

There is also a Kubernetes integration test, see resource-managers/kubernetes/integration-tests/README.md

## A Note About Hadoop Versions

Spark uses the Hadoop core library to talk to HDFS and other Hadoop-supported
storage systems. Because the protocols have changed in different versions of
Hadoop, you must build Spark against the same version that your cluster runs.

Please refer to the build documentation at
["Specifying the Hadoop Version and Enabling YARN"](https://spark.apache.org/docs/latest/building-spark.html#specifying-the-hadoop-version-and-enabling-yarn)
for detailed guidance on building for a particular distribution of Hadoop, including
building for particular Hive and Hive Thriftserver distributions.

## Configuration

Please refer to the [Configuration Guide](https://spark.apache.org/docs/latest/configuration.html)
in the online documentation for an overview on how to configure Spark.

## Contributing

Please review the [Contribution to Spark guide](https://spark.apache.org/contributing.html)
for information on how to get started contributing to the project.


/opt/streaming/spark-3.4.3-bin-hadoop3/bin/spark-sql --jars /opt/lib/paimon-spark-3.4-0.9.0.jar --conf 'spark.sql.catalog.paimon.metastore=filesystem' --conf 'spark.sql.catalog.paimon.warehouse=s3a://paimon/warehouse' --conf 'spark.sql.catalog.paimon.s3.endpoint=http://ip:31212' --conf 'spark.sql.catalog.paimon.s3.access-key=uotAvnxXwcz90yNxWhq2' --conf 'spark.sql.catalog.paimon.s3.secret-key=MlDBAOfRDG9lwFTUo9Qic9dLbuFfHsxJfwkjFD4v' --conf 'spark.serializer=org.apache.spark.serializer.KryoSerializer' --conf 'spark.sql.catalog.paimon=org.apache.paimon.spark.SparkCatalog' --conf 'spark.sql.extensions=org.apache.paimon.spark.extensions.PaimonSparkSessionExtensions' --conf 'spark.sql.catalog.paimon.s3.path-style.access=true' --conf 'spark.delta.logStore.class=org.apache.spark.sql.delta.storage.S3SingleDriverLogStore' --conf 'spark.hadoop.fs.s3a.multipart.size=104857600' --conf 'spark.hadoop.fs.s3a.impl=org.apache.hadoop.fs.s3a.S3AFileSystem' --conf 'spark.hadoop.fs.s3a.access.key=uotAvnxXwcz90yNxWhq2' --conf 'spark.hadoop.fs.s3a.secret.key=MlDBAOfRDG9lwFTUo9Qic9dLbuFfHsxJfwkjFD4v' --conf 'spark.hadoop.fs.s3a.endpoint=http://ip:31212' --conf 'spark.hadoop.fs.s3a.connection.timeout=200000'



use command spark.sql.catalog.paimon=org.apache.paimon.spark.SparkCatalog  default catalog is paimon 


USE paimon;

create database m31094;

use m31094;

create table m31094.paimon_table (
    id int,
    name string
) tblproperties (
    'primary-key' = 'id'
);

INSERT INTO m31094.paimon_table VALUES (1, 'M*****'), (2, 'JY*****');


SELECT * FROM m31094.paimon_table;


jars/aws-java-sdk-bundle-1.12.772.jar big more not upload
