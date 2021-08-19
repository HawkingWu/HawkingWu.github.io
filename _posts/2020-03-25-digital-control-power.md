---
layout:     post
title:      "数控可调电源"
subtitle:   " 从快充识别芯片到数控可调电源 "
date:       2020-03-25
author:     "huanqing"
header-img: "img/post-bg-digital-control-power.jpg"
tags:
    - 电源
    - 模拟电路
---

### 从快充识别芯片到数控可调电源

目前的快充电源结构基本可以分为两种：一种是集成各种协议的专用开关电源芯片(如英集芯的大部分芯片)；另一种是通用开关电源+快充识别芯片。

如天钰的FP6601，在小米充电宝、紫米充电头上都有非常多的应用。

<img src="https://onedrive.gimhoy.com/sharepoint/aHR0cHM6Ly9lZHVpbmhrLW15LnNoYXJlcG9pbnQuY29tLzppOi9nL3BlcnNvbmFsL2h1YW5xaW5nX2VkdWluaGtfb25taWNyb3NvZnRfY29tL0VZQktWbWhJTTdsTW1aSzNVWFVybGJZQk5EeVltRnI0enJXM3RWbnBFMXlhUVE/ZT16MG5Id1E=.jpg" alt="FP6601" style="zoom: 67%;" />

我在刚开始做快充时只知道这是一个握手芯片，把FBO引脚接到DC-DC芯片的FB脚，就可以调整输出电压。具体做法是把反馈的分压电阻R1取100K，R2取适当的值使DC-DC电路输出5V，然后识别芯片和设备握手后会通过FBO脚调整输出电压。

<img src="https://onedrive.gimhoy.com/sharepoint/aHR0cHM6Ly9lZHVpbmhrLW15LnNoYXJlcG9pbnQuY29tLzppOi9nL3BlcnNvbmFsL2h1YW5xaW5nX2VkdWluaGtfb25taWNyb3NvZnRfY29tL0VRT0dIRlBTN2VOS2taU3dIZ2RGZ3lVQmVleFp2Z2ZVTG5hSDlIN3FJUEhpMXc/ZT1hdHQxSHY=.jpg" alt="FP6601PIN" style="zoom:80%;" />

后来仔细看FBO脚的描述，发现这是一个sink或source的电流源，电流步进是2uA，乘上R1就是200mV，而这正好是FP6601的最小电压步进！于是我仿照这样的结构，用一个恒流源并在FB引脚上，验证了可以通过这种方式调整DC-DC的输出电压。

<img src="https://onedrive.gimhoy.com/sharepoint/aHR0cHM6Ly9lZHVpbmhrLW15LnNoYXJlcG9pbnQuY29tLzppOi9nL3BlcnNvbmFsL2h1YW5xaW5nX2VkdWluaGtfb25taWNyb3NvZnRfY29tL0VmUnkyODlGaHFGS3FZM0FGQm1KS1V3QjMxTkdKczR5ekZqWmlHNXU1cWhRZ2c/ZT1MVmdtVko=.png" alt="sink" style="zoom: 25%;" />

需要注意的是VFB的电压是DC-DC芯片FB脚的电压，也是芯片内部参考源的电压，一般是1V上下。而VSET的电压需要低于VFB，否则VFB将无法提供足够的电压达到设定电流。

三极管Q1不能用MOS代替，我测试发现使用MOS会改变芯片FB的电压，使电路无法工作。原因我暂时没有找到。
