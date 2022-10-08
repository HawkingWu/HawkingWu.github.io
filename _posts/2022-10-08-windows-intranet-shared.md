---
layout:     post
title:      "局域网共享文件夹的注意事项"
subtitle:   " 共享文件提示“用户账户限制阻止了此用户进行登录”的解决方法 "
date:       2022-10-08
author:     "huanqing"
catalog: true
tags:
    - Windows
    - 网络
    - 局域网共享
---



## 共享文件提示“用户账户限制阻止了此用户进行登录”的解决方法

用户账户限制阻止了此用户进行登录例如不允许空密码，登录时间限制，或强制的策略限制。

#### 1. Win + R 打开运行，输入 gpedit.msc

<img src="https://gitee.com/hawkingwu/PicGo/raw/master/image-20221008183739171.png" alt="image-20221008183739171" style="zoom: 67%;" />



#### 2. 依次打开 Windows 设置 → 安全设置 → 本地策略 → 安全选项，将 “帐户:使用空密码的本地帐户只允许进行控制台登录” 设置为禁用。

![image-20221008184141273](https://gitee.com/hawkingwu/PicGo/raw/master/image-20221008184141273.png)



#### (附) Windows家庭版安装本地组策略编辑器的方法

将以下代码另存为批处理文件（xxx.bat），记事本保存时 **编码选择ANSI** ，右键以管理员身份运行。

```
@echo off
pushd "%~dp0"
dir /b %systemroot%\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >gp.txt
dir /b %systemroot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>gp.txt
for /f %%i in ('findstr /i . gp.txt 2^>nul') do dism /online /norestart /add-package:"%systemroot%\servicing\Packages\%%i"
pause
```
