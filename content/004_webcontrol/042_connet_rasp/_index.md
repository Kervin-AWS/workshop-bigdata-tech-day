---
title: "2. 部署到树莓派"
date: 2018-10-03T10:17:52-07:00
draft: false
weight: 110
---
## 将代码拉取到树莓派中

1.	通过ssh进入树莓派， Mac用户可以直接通过terminal进入， Windows用户请确认系统以开启ssh功能后，再运用相关软件进行连接

    用户名： pi 

    密码： `awsworkshop`

    ```shell
    ssh pi@192.xxx.xxx.xx
    ```

2.	首先拉取github树莓派端的代码

```shell
git clone https://github.com/Kervin-AWS/auto-iot-lab-rasp.git
```

3.	在本地terminal通过cd命令内进入“创建智能灯泡模拟器”步骤中下载的证书文件夹，将生成的 certificate.pem.crt、private.pem.key 通过scp的方式传入树莓派的`auto-iot-lab-rasp/src`文件夹中

    ```shell
    scp ./certificate.pem.crt pi@xxx.xxx.xxx.xxx:/home/pi/auto-iot-lab-rasp/src

    scp ./private.pem.key pi@xxx.xxx.xxx.xxx:/home/pi/auto-iot-lab-rasp/src
    ```

4. 在树莓派内通过 vim 或者 nano 修改`exercise-lab3.js`中的**thingName**为自己设置的IOT 设备名称，如car-01

5. 然后在树莓派中启动exercise-lab3.js
    ```shell
    node exercise-lab3.js
    ```