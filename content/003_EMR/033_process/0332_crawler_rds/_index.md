---
title: "3.2 爬取 RDS 元数据"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---
1. 创建名为 `my-lab2-crawler-rds` 的爬网程序，如下图所示：![Image](/images/003_EMR/3.14.png)
2. 点击“添加爬网程序”后：![Image](/images/003_EMR/3.15.png)
3. 配置对应参数（包含路径那里输入：`bdd/%`）：![Image](/images/003_EMR/3.16.png)
4. 选择对应的 role：![Image](/images/003_EMR/3.17.png)
5. 配置输出（点击添加数据库，名字为 `default` 即可）：![Image](/images/003_EMR/3.18.png)
6. 完成后，运行爬网程序，爬取成功后，元数据目录中会出现 4 张 RDS 元数据表，如下图所示：![Image](/images/003_EMR/3.19.png)
