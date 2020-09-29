---
title: "0.3.3.1 部署RDS数据库"
weight: 11
chapter: false
draft: false
---
1. 准备参数组
打开 RDS 控制台：![Image](/images/011_lab0-3/0.3.1.png)
选择左边菜单栏的参数组：![Image](/images/011_lab0-3/0.3.2.png)
点击创建参数组，选择系统默认已有的对应版本，输入名字和描述，点击创建：![Image](/images/011_lab0-3/0.3.3.png)
打开刚才创建的参数组：![Image](/images/011_lab0-3/0.3.4.png)
输入“character_set”过滤参数并点击编辑参数：![Image](/images/011_lab0-3/0.3.5.png)
把所有能改的编码全部改成“utf8mb4”后，保存： ![Image](/images/011_lab0-3/0.3.6.png)

2. 准备选项组
打开 RDS 控制台，选择左边菜单栏的选项组：![Image](/images/011_lab0-3/0.3.7.png)
点击创建选项组，输入对应名字，描述，选择对应版本，点击创建：![Image](/images/011_lab0-3/0.3.8.png)

3. 部署 RDS 数据库
登录 AWS 控制台，选择 RDS，进入数据库页面，选择创建数据库：![Image](/images/011_lab0-3/0.3.9.png)
选择标准创建和 MySQL 引擎：![Image](/images/011_lab0-3/0.3.10.png)
选择对应版本，模板，以及数据库实例标识：![Image](/images/011_lab0-3/0.3.11.png)
创建对应用户名，密码（此处设置为 `QazWsx2020`），选择对应类型：![Image](/images/011_lab0-3/0.3.12.png)
存储空间设置（支持弹性伸缩，此处选择默认值用来做测试）：![Image](/images/011_lab0-3/0.3.13.png)
因为是开发测试，所以此处选择不创建备用实例：![Image](/images/011_lab0-3/0.3.14.png)
选择默认的 VPC 和网络配置：![Image](/images/011_lab0-3/0.3.15.png)
选择密码身份验证：![Image](/images/011_lab0-3/0.3.16.png)
配置初始数据库，选择对应数据库参数组和选项组（其他全部默认）：![Image](/images/011_lab0-3/0.3.17.png)
然后，选择“创建数据库”即可。

4. 导入 RDS 数据库

RDS 数据库可用以后，会产生一个终端节点，如下图所所示：![Image](/images/011_lab0-3/0.3.18.png)
点开安全组，修改入站规则：![Image](/images/011_lab0-3/0.3.19.png)
在之前部署的 Linux 上安装 MySQL 客户端：![Image](/images/011_lab0-3/0.3.20.png)

通过如下命令下载数据文件
```
mkdir ~/sql
cd ~/sql
wget http://122.248.225.198/lab2/rds/tbl_address.sql --http-user=bdd --http-passwd=bdd@2020
wget http://122.248.225.198/lab2/rds/tbl_customer.sql --http-user=bdd --http-passwd=bdd@2020
wget http://122.248.225.198/lab2/rds/tbl_product.sql --http-user=bdd --http-passwd=bdd@2020
wget http://122.248.225.198/lab2/rds/tbl_transaction.sql --http-user=bdd --http-passwd=bdd@2020
```
![Image](/images/011_lab0-3/0.3.21.png)
远程连接：
```
mysql -h bdd.cj6hmgaefgej.ap-southeast-1.rds.amazonaws.com -u admin -p bdd
```
![Image](/images/011_lab0-3/0.3.22.png)
用如下方式导入上述五个 sql 脚本文件：
```
source ~/sql/tbl_address.sql
source ~/sql/tbl_customer.sql
source ~/sql/tbl_product.sql
source ~/sql/tbl_transaction.sql
```
导入完毕后我们看到数据库表的数据如下：![Image](/images/011_lab0-3/0.3.23.png) 请确保数据量一致。
