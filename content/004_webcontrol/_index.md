---
title: "Lab3 通过web与AWS IoT交互"
weight: 14
chapter: true
draft: false
---

#        实验说明      

除了MQTT外，另外一个非常典型的场景是使用https，通过web和AWS IoT交互。

Lab3将通过aws cognito验证身份，并通过web对shadow进行操作

![Image](/images/png/38.png)

为了简化实验，本Lab已经配置好了统一的Congnito 身份池

我们将分别从以下步骤进行配置：

{{% children showhidden="false" %}}
