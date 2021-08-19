---
layout:     post
title:      "MathpixOCR小工具"
subtitle:   " 智能识别公式的小软件 "
date:       2020-04-03
author:     "Huanqing"
header-img: "img/post-bg-mathpix.jpg"
tags:
    - Math
    - OCR
---

### Mathpix收费了！

其实这种套路国内互联网公司都玩烂了，先培养习惯再收割一波韭菜。目前来看联网识别这种方式基本能确定无法破解，普通用户一个月50次的识别确实有些少（虽然我这个电子攻城狮一个月可能也用不了10次）。

不过对于开发者，Mathpix还是留了一个后门，它提供的API可以每月免费使用1000次！超过部分按阶段收费（0.004~0.001刀不等）。

### 下面提供一种方法使用API将公式转换成Markdown文本并插入Word

#### 需要工具：

1. 开发者账号，注册地址：[https://dashboard.mathpix.com](https://dashboard.mathpix.com)
2. 信用卡一张
3. **[Visual Studio](https://visualstudio.microsoft.com/zh-hans/downloads/)**

#### 教程：

1. 登陆开发者账号，填写信用卡信息，激活后会显示app_id和app_key
2. 下载天若OCR项目源码，链接：[https://github.com/huanqingwu/MathpixOCR](https://github.com/huanqingwu/MathpixOCR)
3. 双击下载的源码里的 **TrOCR.sln** 打开项目，搜索 **app_id** ，将 **app_id** 和 **app_key** 替换成你自己的。
4. 点击 **生成 → 生成解决方案** ，快捷键 `Ctrl`+`Shift`+`B`



#### 使用方法：

1. 使用MathYype：

   ![](https://onedrive.gimhoy.com/sharepoint/aHR0cHM6Ly9lZHVpbmhrLW15LnNoYXJlcG9pbnQuY29tLzppOi9nL3BlcnNvbmFsL2h1YW5xaW5nX2VkdWluaGtfb25taWNyb3NvZnRfY29tL0VYTkhrSm92R1ZWTnZhaV9TTTlDaWE4QmNubDNiUVd2YmNVN1F0d1EybTE5Nnc/ZT1RVTFFVDE=.gif)

   

2. 作为程序员最爱使用的方法：将Markdown文本复制Typora，再导出Word公式

<img src="https://onedrive.gimhoy.com/sharepoint/aHR0cHM6Ly9lZHVpbmhrLW15LnNoYXJlcG9pbnQuY29tLzppOi9nL3BlcnNvbmFsL2h1YW5xaW5nX2VkdWluaGtfb25taWNyb3NvZnRfY29tL0VmSDdWS0xvNHg1UG44dTlNQU1TUWRVQk9zT3lkUDhOZFhPc3RmQTE1RjBXV1E/ZT1mbmREQ0E=.jpg" style="zoom: 67%;" />
