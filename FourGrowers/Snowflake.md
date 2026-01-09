[[tools]]
[[Four Growers]] uses that to aggregate our bag data.

We currently populate it using an [[SQL Adapter]], which is inefficient and doesn't scale to large datasets.

Our input datasets are ROM 10GB per robot run, and multiple runs may be part of a single upload to S3.

## Snowflake Architecture
Snowflake does transparent clustering, but allows you to add your own cluster keys. By default, clusters on insert order, which likely is *correct* for us.

* Cluster on multi-terabyte tables
* Cluster only when queries benefit
* Cluster when queries are selective or sort (which again, we're clustering on insert order anyway, which gets us timeliness)
* Cluster on low cardinality columns
Reading up on Snowflake, it looks like I can (ab)use it like an RDBMS, and let the fact that it does a lot of other complicated weird stuff just live under the hood. It mostly automates all the hard stuff, and it seems like basic normalization works just fine.