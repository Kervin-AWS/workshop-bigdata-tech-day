---
title: "1. 实验目标"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---

在本练习中，您将学习如何使用 Amazon EMR（Spark）和 AWS Glue （ETL）构建批量数据分析处理程序。

为了使本实验的练习更加贴近实际的业务场景，我们模拟了完整的从数据 产生（模拟历史数据和流数据）、数据存储、数据处理、到数据分析和数据可 视化的完整过程（数据可视化在 Lab3/Lab4 中完成）。具体可参考如下架构图：![Image](/images/003_EMR/1.1.png)

组件说明如下：
- RDS 作为 Lab2 次实验的历史数据源，RMDBS 格式，包含人员信息表 `tbl_customer`、产品信息表 `tbl_product`、地址信息表 `tbl_address`、交易历史流水表 `tbl_transaction`，等 4 张表，参与批处理计算
- Lab1 实验中 Kinesis 的输出（存放在 Lab1 指定的 S3 文件夹中，Json 格 式），为近实时当日交易流水，也可以作为 Lab2 批处理的输入，参与批处理计算（**注意：学员可以考虑使用 Lab1 的输出数据或者使用我们提前准备好的数据**）；
- S3 桶作为数据湖的存储基础，包含 `input` 文件夹（用于 EMR Spark 批处理的输入），存放通过 Glue ETL 加载进来的 RDS 历史数据源和 Kinesis 当日近实时数据，以 Parquet 格式存放。`output` 文件夹，存放 EMR Spark 批处理的结果数据（Parquet 格式）；

详细的数据链路图和说明如下：![Image](/images/003_EMR/1.2.png)

具体说明如下：

1.1 通过 Glue Crawler 功能爬取 RDS 库中 4 张表的元数据和 Kinesis 输出的数 据的元数据；

1.2 Glue Crawler 将爬取 RDS 和 Kinesis 的元数据，存入到 Glue 的 Data Catalog 数据库；

1.3 Glue ETL 通过 Data Catalog 识别 RDS 表元数据和 Kinesis 元数据，以便 ETL 作业引用；

1.4 Glue ETL 加载 4 张表数据和 Kinesis 输出的数据，到指定的 S3 存储桶的 input 文件夹中，作为 Spark 批处理的数据源输入；

1.5 通过 Glue Crawler 功能爬取 S3 桶中 input 文件夹中数据的元数据；

1.6 Glue Crawler 将爬取 input 文件夹中数据的元数据，存入 Glue 的 Data Catalog 数据库；

1.7 EMR Spark 环境通过 Data Catalog 获取 input 文件夹的元数据，进而开展 批处理作业；

1.8 将 EMR Spark 批处理作业的结果输出至指定的 S3 存储桶的 output 文件 夹中；

1.9 通过 Glue Crawler 功能爬取 S3 桶中 output 文件夹中数据的元数据；

2.0 Glue Crawler 将爬取 output 文件夹中数据的元数据，存入 Glue 的 Data Catalog 数据库；

2.1 利用 Athena 服务，查询 input、output 数据；
