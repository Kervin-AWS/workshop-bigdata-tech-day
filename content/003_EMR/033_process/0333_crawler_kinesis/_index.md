---
title: "3.3 爬取 Kinesis 元数据"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---
{{% notice info %}}
如果 Lab1 成功完成，推荐使用 Lab1 输出到 S3 的数据，可以跳过这个步骤。

如果 Lab1 未完成或者希望使用我们提前准备了的 5 年（2015-2020）的 Kinesis 流历史数据，请安顺序操作。
{{% /notice %}}


1. 登录 Lab0 部署的 Linux 客户端（*这个 Linux 客户端必须配置了 AKSK，具体参考 Lab0 的内容*）：
```shell
cd ~
mkdir s3his
cd s3his
wget http://122.248.225.198/lab2/kinesis/2015-2020.tar.gz --http-user=bdd --http-passwd=bdd@2020
tar zxvf 2015-2020.tar.gz
aws s3 mb s3://lab2-748313030715-sin-com
aws s3 sync ./2020 s3://lab2-748313030715-sin-com/2020
```
然后进入 S3 控制台查看对应数据：![Image](/images/003_EMR/3.20.png)

2. 爬取 Kinesis 元数据

创建名为 `my-lab2-crawler-kinesis` 的爬网程序，如下图所示：![Image](/images/003_EMR/3.21.png)
添加数据存储（选择 Lab1 的输出目的地或者上一个步骤准备的 S3 桶）：![Image](/images/003_EMR/3.22.png)
选择 IAM 角色：![Image](/images/003_EMR/3.23.png)
配置输出： ![Image](/images/003_EMR/3.24.png)
完成后，运行爬网程序，元数据目录中会出现 1 张 Kinesis 元数据表，如下图所示：![Image](/images/003_EMR/3.25.png)
