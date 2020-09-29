---
title: "1. 创建 IOT Core"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---

1.	在浏览器中，打开 [IoT core控制台](https://console.amazonaws.cn/iot/home?region=cn-north-1#/) ，选择管理物品，并选择创建
    ![Image](/images/png/14.png)

2.	选择创建单个物品
    ![Image](/images/png/15.png)

3.	取名car-xx(建议为树莓派纸盒上的编号)，本次lab不需要设置或选择type，然后点击下一步
    ![Image](/images/png/16.png)


4.	选择一键式创建证书， **<span style="color: red;">点击激活证书</span>**，并**保存下载证书、公钥和私钥**至您的本地笔记本电脑，去掉文件名前面的c838e129ec-
    
    并点击完成。至此car创建完成, 您将看到下面的内容
    ![Image](/images/png/17.png)


5.	添加物品策略

    点击左侧管理、物品，找到您创建的物品，并选中，随后点击安全性中的证书
    ![Image](/images/png/18.png)

    然后点击左侧的策略，我们可以看到目前没有策略    
    ![Image](/images/png/19.png)

    点击右上角的操作，选择附加策略，选择`demo-iot-policy`, 点击附加
    ![Image](/images/png/20.png)