---
title: "2. 配置虚拟车辆"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 10
---

1.	在Cloud9界面IDE中选中lab1-2文件夹，点击File，upload local files，将创建IOT物品步骤中生成的certificate.pem.crt和private.pem.key上传。

    您也可以直接用拖拽的方式将文件拖到目标文件夹。
    ![Image](/images/png/21.png)

2. exercise-lab1.js为实验1的代码，代码主要分为两部分，第一部分配置IoT endpoint，证书，private key等信息，并定义auto/（devicename）为消息topic
    ![Image](/images/png/22.png)
    
    首先编辑exercise-lab1.js 中24行的 `deviceName` 以及 [`endpointAddress`](https://console.amazonaws.cn/iot/home?region=cn-north-1#/settings)（IOT 的endpoint在下图中获得）
    ![Image](/images/png/23.png)
    例如：
    ```nodejs
    const deviceName = 'car-01';
    const endpointAddress = 'a1ba8o0iqbelxz.ats.iot.cn-north-1.amazonaws.com.cn'
    ```


3. 代码第二部分模拟汽车行驶状态，随机生成一些速度，油量，位置，紧急刹车事件等信息
    ![Image](/images/png/24.png)

4. 然后在命令行中，进入lab1-2文件夹，并运行exercise-lab1.js程序，模拟汽车运行
    ```shell
    cd /home/ec2-user/workspace/auto-iot-lab/lab1-2
    npm install aws-iot-device-sdk
    node exercise-lab1.js
    ```
    ![Image](/images/png/25.png)

5. 在[IoT core](https://console.amazonaws.cn/iot/home?region=cn-north-1#/test) 中选择Test-Subscribe to a topic，填写代码中定义的topic：auto/(device_name) 如auto/car-01，并订阅
    ![Image](/images/png/26.png)

    代码中定义每5秒生产一次数据，测试界面中将会持续收到car的行驶信息

    Lab1测试成功
    ![Image](/images/png/27.png)

6. 在Cloud9 中ctrl + C 终止程序，我们进入下一个实验。
    ![Image](/images/png/28.png)

