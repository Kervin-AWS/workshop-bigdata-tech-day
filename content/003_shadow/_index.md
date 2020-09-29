---
title: "Lab2 AWS IoT的设备影子"
weight: 13
chapter: false
draft: false
---

利用IoT shadow，可以在云端创建一个真实设备的影子，用于在设备断网时记录状态信息，联网后影子将和设备进行状态同步

![Image](/images/png/29.png)

1. 我们在IoT core中找到car-xx，查看shadow状态

    ![Image](/images/png/30.png)

2. 打开Lab2的代码exercise-lab2.js，可以看到代码定义了车灯开和车灯关两个状态
    ![Image](/images/png/31.png)

    修改exercise-lab2.js 的21行的物品名称，
    ![Image](/images/png/06.png)

    在当前目录执行代码，可以看到当前状态为车灯关闭
    ![Image](/images/png/32.png)

    在云端查看car1点影子状态，可以看到已经实时同步为lights:false，即车灯关闭
    ![Image](/images/png/33.png)

    我们在云端对car1的影子发布指令，把车灯打开。
    在IoT core中选择Test-Publish to a topic，输入`$aws/things/car-xx/shadow/update`，将xx替换为你的编号，在方框中写入执行代码，
    
    ```shell
    {
        "state": {
            "desired": {
                "lights": true
            }
        }
    }
    ```

    然后Publish
    ![Image](/images/png/34.png)

3. 在Cloud9客户端可以看到car1 reporting了一个新的状态，车灯状态从off 变成了on，云端指令下发成功
    ![Image](/images/png/35.png)

    在云端查看之前订阅的$aws/things/car1/shadow/update/documents，可以看到影子状态从false变成true

    ![Image](/images/png/36.png)

4. 在云端多次改变shadow状态，在cloud9设备端查看car1车灯状态
    ![Image](/images/png/37.png)

