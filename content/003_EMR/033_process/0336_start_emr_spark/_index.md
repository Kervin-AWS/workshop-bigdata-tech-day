---
title: "3.6 启动 EMR 集群，执行 Spark"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---
创建集群参考：lab0-3-部署 RDS 和 EMR 集群-实验手册-20200825-v0.1.pdf

当集群创建好，可通过 ssh 方式登录集群，如下图所示，依据学员的操作系 统，选择登录方式：![Image](/images/003_EMR/3.37.png)
默认 EMR 的 Master 外网不通，找到安全组名称为 `ElasticMapReduce-master` 的条目，添加 ssh 远程可访问，然后就可以登录了。
![Image](/images/003_EMR/3.38.png)
登录后如下所示：![Image](/images/003_EMR/3.39.png)

本实验将采用两种方式进行批处理作业。第一种通过 spark-shell 交互式命 令进行批处理，第二种（可选）通过 spark-submit 提交 java 应用程序进行批处理，两种处理逻辑和输出结果一样。第二种，代码存放在 `http://122.248.225.198/lab2/spark/code/original-emr-0.0.1-SNAPSHOT.jar`，各位学员可以把代码取下来，放到例如：`s3://my-lab2-139846303839-sincom/spark/code/original-emr-0.0.1-SNAPSHOT.jar`

1. 用 spark-shell 提交

登录 emr 集群，输入 spark-shell 命令，并启动 spark-shell 环境。

1). 生成聚合数据集，如下代码和示例图所示（注意表的名称）：

```
val result = spark.sql("SELECT tt.tno tno, tt.tdate tdate, tt.uno uno, tt.pno pno, tt.tnum tnum, tc.uname uname, tc.umobile umobile, ta.ano ano, ta.acity acity, ta.aname aname, tp.pclass pclass, tp.pname pname, tp.pprice price FROM s3_tbl_transaction tt, s3_tbl_customer tc, s3_tbl_address ta, s3_tbl_product tp WHERE tp.pno = tt.pno and tt.uno = tc.uno and tc.ano = ta.ano ORDER BY tt.tuptime desc");
```

2). 查询 result 的 schema，检查是否生产所需结构；

```
result.printSchema();
```
![Image](/images/003_EMR/3.40.png)

3). 输出数据集结果至 S3（result 文件夹）

```
result.write.format("parquet").mode("append").save("s3://lab2-748313030715sin-com/spark/output");
```

4). 去对应 S3 目录（s3://lab2-748313030715-sin-com/spark/output）查看是否正 常输出结果（这些结果会在 Lab3 里面用到）。![Image](/images/003_EMR/3.41.png)


2. 用 spark-submit提交（可选）

本实验，以 java 代码为例，退出 spark-shell 环境，执行以下命令进行部署 （部署方式有多种，此处为 yarn 客户端模式）
```
spark-submit --master yarn --deploy-mode client --class com.demo.emr.spark.Lab2 s3://lab2-748313030715-sin-com/spark/code/original-emr-0.0.1-SNAPSHOT.jar s3://lab2-748313030715-sin-com/spark/output
```
恭喜你，你已经完成 Lab2 的实验内容。
