# Databricks Certified Associate Developer for Apache Spark: Study Plan

Topic weights come from the [official exam page](https://www.databricks.com/learn/certification/apache-spark-developer-associate). Re-check them before the exam, since they can change.

Practice stack: the `data-platform` project (Spark Connect at `sc://localhost:15002`, Spark UI at `:4040`, Kafka, SeaweedFS S3).

> Spark Connect has no `df.rdd` or `spark.sparkContext`, but the exam still asks about them. For those exercises use classic mode (`pyspark --master local[*]` or against the standalone master).

## 1. Apache Spark Architecture and Components (20%)
- [ ] Execution hierarchy: run a job with a shuffle, then map the application to jobs, stages and tasks in the Spark UI. Predict the stage count first.
- [ ] Lazy evaluation: chain transformations with no action, check nothing runs, then trigger one with `count()`. Compare `explain()` before and after.
- [ ] Fault tolerance: stop a worker mid-job and watch lineage-based recovery.
- [ ] Deploy modes: client against cluster mode, `local[*]` against a standalone cluster.
- [ ] Memory regions and garbage collection: read the GC time column in the UI.
- [ ] Broadcast variables and accumulators (classic mode).

## 2. Using Spark SQL (20%)
- [ ] Write the same query in SQL and in the DataFrame API and compare `explain()` output.
- [ ] Temp views, `CREATE TABLE`, joins and subqueries.
- [ ] Window functions: `rank`, `lag`, running totals.
- [ ] `CASE`, `explode`, array and map functions, `PIVOT`.
- [ ] Inspect tables after `saveAsTable`.

## 3. Developing Apache Spark DataFrame/DataSet API Applications (30%)
- [ ] Columns: `select`, `withColumn`, `withColumnRenamed`, `drop`, `cast`, `alias`, `col` against `F.expr`.
- [ ] Rows: `filter`, `distinct`, `dropDuplicates`, `orderBy`, `sort`, `limit`.
- [ ] Missing data: `fillna`, `dropna`, `na.replace`, `coalesce`, `isNull`.
- [ ] Aggregations: `groupBy().agg()`, `agg` without a group, multiple aggregates.
- [ ] Joins: inner, left, semi, anti, cross, and ambiguous column names after a join.
- [ ] Read and write: CSV, JSON, Parquet and Delta, explicit schemas (`StructType`) against `inferSchema`, write modes, `partitionBy`.
- [ ] Partitioning: `repartition` against `coalesce`, and `spark_partition_id()`.
- [ ] UDFs: plain Python against Pandas UDF, and why built-in functions are faster.

## 4. Troubleshooting and Tuning (10%)
- [ ] Data skew: create a skewed key, spot it in the UI, fix it with salting or AQE.
- [ ] Broadcast join against sort-merge join in `explain()` and the UI.
- [ ] `cache()` against `persist()`, storage levels, and when caching helps.
- [ ] `spark.sql.shuffle.partitions` and its effect on task count.
- [ ] Common errors: OOM, too many small files.
- [ ] AQE: toggle `spark.sql.adaptive.enabled` and compare plans.

## 5. Structured Streaming (10%)
- [ ] Read from Kafka with `readStream` and write to Delta.
- [ ] Output modes: append, update, complete.
- [ ] Triggers: default, `processingTime`, `availableNow`.
- [ ] Event-time windows and watermarks; observe late data being dropped.
- [ ] Checkpoints: stop and restart a query and confirm it resumes without duplicates.

## 6. Using Spark Connect to Deploy Applications (5%)
- [ ] Client–server architecture and what the client can and can't do.
- [ ] `SPARK_REMOTE` and `SparkSession.builder.remote("sc://...")`.

## 7. Using Pandas API on Apache Spark (5%)
- [ ] `pyspark.pandas` (`ps.DataFrame`), `to_spark()` and `pandas_api()`.
- [ ] Compare with `toPandas()`: what moves to the driver and the memory risk.

## Suggested order
1. Week 1: sections 3 and 2 (largest weights).
2. Week 2: section 1, with the Spark UI exercises.
3. Week 3: sections 4 and 5.
4. Then: sections 6 and 7, followed by the official sample questions and practice tests.
