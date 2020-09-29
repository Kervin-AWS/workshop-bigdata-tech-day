---
title: "3.1 创建 RDS 数据库连接"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---

1. 创建IAM Role

登录并打开 IAM 的控制台，选择创建角色: ![Image](/images/003_EMR/3.2.png)
在实体类型那里往下拉，选择 `Glue`: ![Image](/images/003_EMR/3.3.png)
然后选择下一步：![Image](/images/003_EMR/3.4.png)
把 `AdministratorAccess` 的权限赋予它（严格意义上来讲，这不符合最小权限原 则，此处为了测试，我们就简单化了）：![Image](/images/003_EMR/3.5.png)
其他都默认值，在审核保存页面输入对应名字（此处为 `lab-role`）后保存： ![Image](/images/003_EMR/3.6.png)


2. 创建S3终端节点

登录并打开 VPC 控制台，往下拉选择左边的终端节点：![Image](/images/003_EMR/3.7.png)
选中 S3，选择对应 VPC（此处我们只有一个默认 VPC）和路由表： ![Image](/images/003_EMR/3.8.png)
其他默认，点击“创建终端节点”即可。

3. 创建 RDS 数据库

参考：lab0-3-部署 RDS 和 EMR 集群-实验手册-20200825-v0.1.pdf

4. 创建 RDS 数据库连接

登录并打开 AWS Glue 控制台（确认在 AWS 的新加坡区域），选择添加数据库 连接：![Image](/images/003_EMR/3.9.png)
设置连接名称（`Lab2-Glue-RDS-connection`）和类型![Image](/images/003_EMR/3.10.png)
选择对应配置（请输入之前部署 rds 时 admin 的密码）：![Image](/images/003_EMR/3.11.png)
审核并完成，然后开始连接测试，测试时需要使用第一步创建的 role：![Image](/images/003_EMR/3.12.png)
需要 1-2 分钟的时间，略微等待即可。![Image](/images/003_EMR/3.13.png)
