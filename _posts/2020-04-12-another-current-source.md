---
layout:     post
title:      "另一种电流源"
subtitle:   " 适用于小信号调理的电流源 "
date:       2020-04-12
author:     "huanqing"
header-img: "img/post-bg-digital-control-power.jpg"
mathjax: true
catalog: true
tags:
    - 电源
    - 模拟电路
---

### 另一种仅使用运放的电流源

还记得上一篇关于数控可调电源的博文吗？那里面将运放+三极管做的sink类型电流源并在DC-DC芯片的FB引脚上，通过灌入电流调整DC-DC的输出电压。然而由于三级管CE极电压降的问题，那样的电路不适合参考电压较低的DC-DC芯片。

下面我将介绍另一种恒流源电路，更适合低电压的恒流控制。

#### source类型电流源

先上原理图：

<img src="https://s1.ax1x.com/2020/07/11/UQzTG8.jpg" alt="source" style="zoom: 50%;" />

$R_2$ 是电流采样电阻。当反馈电阻远大于 $R_2$ 时，反馈回路上的电流忽略不计。可以看出这是一个同向加法电路， $R_5$ 和 $R_3$ 分压取得 $V_{set}$ 和 $V_{o2}$ 的平均，$R_4$ 和 $R_1$ 构成了同向2倍放大。


$$
V_+ = {(V_{set} +V_{o2}) \over 2}
$$

$$
V_- = V_+
$$

$$
V_{o1} = 2V_- = V_{set} +V_{o2}
$$

得到
$$
V_{o1} - V_{o2} = V_{set}
$$

$V_{set}$ 被传递到 $R_2$ 上，$R_2$ 上电流 $i= {V_{set} \over R_2}$

#### sink类型电流源

直觉告诉我，将 $R_2$ 两端的采样线交换一下，就会得到电流灌入运放的恒流源

<img src="https://s1.ax1x.com/2020/07/11/UlSSiV.jpg" alt="sink1" style="zoom: 50%;" />

推导一遍也会得到  $V_{o2} - V_{o1} = V_{set}$

此电路的优点是即使恒流源输出的电位低到0.3V，运放仍能吸收几百uA的电流，而几百uA电流能在100K电阻上叠加几十V的电压！

<img src="https://s1.ax1x.com/2020/07/11/UlS9RU.jpg" alt="sink2" style="zoom: 50%;" />

至此，普通DC-DC变身数字可调电源的方案算是完善了。相信FP6601这样的快充协议芯片，内部也是类似的结构吧？
