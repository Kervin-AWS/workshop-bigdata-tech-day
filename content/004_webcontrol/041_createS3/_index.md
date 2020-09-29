---
title: "1. 部署静态前端网页"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 110
---
1. 创建S3存储桶，起名为auto-iot-lab-xx（如auto-iot-lab-01）, 用于托管与IoT交互的静态网站，需要开放Public访问权限。
    ![Image](/images/png/39.png)
    ![Image](/images/png/40.png)

2. 然后返回Cloud9 中，进入Lab3文件夹

    您只需要更改Cloud9 中 Lab3 文件夹下 index.js 中的 26行的 `deviceName` 为您的IOT设备名称，如 car-01

3. 将文件同步到目标储存桶中，在terminal中输入：
    ```shell
    aws configure set default.region cn-north-1
    cd /home/ec2-user/workspace/auto-iot-lab/lab3
    aws s3 cp --recursive --acl public-read . s3://auto-iot-lab-01（请换成您创建的储存桶名称）
    ```
    ![Image](/images/png/41.png)
    ![Image](/images/png/42.png)

4. 点击属性，选择静态网站托管
    ![Image](/images/png/43.png)

    选择使用此储存桶托管网站，并填写索引文档为index.html
    ![Image](/images/png/44.png)
    
5. 点击S3存储桶中的index.html,复制右边的对象URL
    ![Image](/images/png/45.png)

6. 进入Cloud9， 启动Lab2的脚本，查看当前shadow状态，车灯状态是on。
    ```shell
    node ./exercise-lab2.js
    ```
    ![Image](/images/png/46.png)

7. 打开前述index.html的网址，进入如下页面，点击Toggle car1’s lights，可以对车灯进行开和关
    ![Image](/images/png/47.png)

8. 进入Cloud9环境，查看car1设备车灯情况，发现和web操作一致。也可以在云端查看shadow和delta信息进一步核对
    ![Image](/images/png/48.png)