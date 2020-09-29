---
title: "3.4 加载 RDS 和 Kinesis 的数据源到目标"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---
本步骤，利用 Glue ETL 功能，加载 RDS 和 Kinesis 的两个数据源至 `s3://lab2748313030715-sin-com/spark/input/``，对应的文件夹中，ETL 作业可通过可视化向导方式生成代码。

为节省时间，已为学员准备好 ETL 脚本，存放在 `http://122.248.225.198/lab2/glue/code/lab2_load_rds_and_kinesis_to_s3_for_spark_input`

下载此脚本，并上传到对应 S3 目录下（手工创建桶和目录，并上传，过程略）：`s3://lab2-748313030715-sincom/glue/code/lab2_load_rds_and_kinesis_to_s3_for_spark_input`

1. 创建 ETL 作业如下图所示：![Image](/images/003_EMR/3.26.png)
2. 配置作业属性：![Image](/images/003_EMR/3.27.png)
3. 保存并编辑作业： ![Image](/images/003_EMR/3.28.png)
4. 保存作业后（**这一步记得修改表名和桶名**），运行作业，执行完成作业大约需要几分钟，如下图所示：![Image](/images/003_EMR/3.29.png)
5. 运行中：![Image](/images/003_EMR/3.30.png)
6. 作业运行完成后，可检查 `s3://lab2-748313030715-sin-com/spark/input/` 目录下的 `tbl_customer`、`tbl_product`、`tbl_address`、`tbl_transaction` 文件夹中，是否产生对应的 parquet 格式的数据，以验证 ETL 作业是否执行成功。
![Image](/images/003_EMR/3.31.png)
