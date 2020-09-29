---
title: "2. 环境准备"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---
环境准备工作主要包括：
- 本实验将在新加坡（ap-southeast-1）区域进行；
- 本实验需要准备 rds 数据库；
- 对应的 EMR 处理对接的 S3 桶信息如下：
  - 文件夹： /glue/code, 存放 Glue ETL 脚本；
  - 文件夹： /spark/code, 存放 Spark 批处理 Java 代码 jar 包；
  - 文件夹： /spark/input/tbl_address, 存放客户地址数据；
  - 文件夹： /spark/input/tbl_customer, 存放客户信息数据；
  - 文件夹： /spark/input/tbl_product, 存放产品信息数据；
  - 文件夹： /spark/input/tbl_transaction, 存放历史交易流水和当天 近实时流水数据；
  - 文件夹： /spark/output, 存放 Spark 批处理结果数据；
