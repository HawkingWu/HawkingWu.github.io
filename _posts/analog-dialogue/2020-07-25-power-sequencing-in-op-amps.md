---
layout:     post
title:      "运算放大器电源上电时序导致的风险分析"
subtitle:   " Analog Dialogue 50卷4期 OCT 2016 "
date:       2020-07-25
author:     "huanqing"
header-img: "img/post-bg-power-sequencing-in-op-amps.png"
mathjax: true
catalog: true
tags:
    - Analog Dialogue
    - 模拟对话
    - 模拟电路
    - 运放
---

## 运算放大器电源上电时序导致的风险分析

### 简介

在有多个供电电源的系统中，运算放大器电源必须在施加输入信号的同时或之前建立。否则，便可能发生过压和闩锁状况。

然而，在实际应用中，这个要求有时候可能难以满足。本文讨论运算放大器在不同上电时序情况下的行为表现（参见表2），分析可能的问题及原因，并提出一些建议。



### 上电时序问题多种多样

上电时序问题可能出现于多种不同情况。例如，在一个客户应用中，AD8616配置为缓冲器，在电源建立之前输入为0 V（图1），负电源先于正电源上电（负电源有而正电源无）。

<img src="https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_01.png?la=zh" alt="图1-AD8616测试电路，施加–3 V V–，V+没有连接电源" style="zoom:50%;" />

<center>图1. AD8616测试电路，施加–3 V V–，V+没有连接电源</center>

表1显示了这种情况下AD8616所有引脚的结果。在正电源管脚V+上的信号建立之前，V+引脚和OUT引脚上的电压为负值。这可能不会损害运算放大器，但若这些信号连接到其他尚未完全供电的芯片上的引脚（例如，假设ADC使用同一V+，其电源引脚一般只能承受最小–0.3 V电压），则这些芯片可能会受损。如果V+先于V–上电，会发生同样的问题。

表2列出了上电时序的一些可能情况。

<p><strong>表1. 施加–3 V V–而V+没有连接电源时的AD8616引脚电压</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #764a8b;">引脚1: OUTA<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚2: –INA<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚3: +INA<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚4: V–<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚5: +INB<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚6: –INB<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚7: OUTB<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #ffffff; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #acacac;">引脚8: V+<br>
            </td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–1.627<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–1.627<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–0.959<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–3.000<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–0.959<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–1.627<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–1.627<br>
            </td>
            <td style="text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; background-color: #f5f5f5;">–1.627</td>
        </tr>
    </tbody>
</table>


<p><strong>表2. 上电时序的可能情况IN</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 30%;">IN<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">V+<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">V–<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">放大器电源有其他负载<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">放大器输出有负载<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">情形 1<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">浮空<br>
            浮空
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">有<br>
            无<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">无<br>
            有<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">情形 2<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0 V<br>
            0 V<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">有<br>
            无<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">无<br>
            有<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">情形 3<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">正或负<br>
            正或负<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">有<br>
            无<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">无<br>
            有<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            否<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">情形 4<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">正或负<br>
            正或负<br>
            正或负<br>
            正或负<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">有<br>
            有<br>
            无<br>
            无<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">无<br>
            无<br>
            有<br>
            有<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">是<br>
            否<br>
            是<br>
            否<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">否<br>
            是<br>
            否<br>
            是</td>
        </tr>
    </tbody>
</table>



### 运算放大器内部的静电放电(ESD)二极管

静电放电可能引起过压事件。大部分运算放大器内置ESD二极管 以防止静电ESD事件。当V+或V–不存在时，ESD二极管是分析放大 器相关行为的重要工具。图2为ADA4077/ADA4177的简化框图。表3 显示了ADA4077-2/ADA4177-2内部ESD二极管和背靠背二极管的典 型压降。注意，背靠背二极管位于运算放大器的两个输入引脚之间， 用来箝位放大器允许输入的最大差分信号。

<img src="https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_02.png?la=zh" alt="图2-ADA4077/ADA4177简化框图" style="zoom:50%;" />

<center>图2. ADA4077/ADA4177简化框图</center>

<p><strong>表3. 运算放大器内部二极管</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">ADA4077<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;">ADA4177<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D1<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.838<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D2<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.845</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知</td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D3<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.837</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D4</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.844</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D5</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D6</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知<br>
            </td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">未知</td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D7</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.841</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.849</td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">D8</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.842</td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;">0.849</td>
        </tr>
    </tbody>
</table>

还要注意，当利用DMM测量ADA4077-2的D5/D6时，结果显示两个输 入引脚之间无二极管。事实上，背靠背二极管之前有两个串联电阻， 用来将输入电流限制在±10 mA以下。内部电阻和背靠背二极管将 差分输入电压限制在±Vs，以防止基极-发射极结点击穿。

A DA4177集成了OVP单元以提高鲁棒性。它们位于ESD二极管和 背靠背二极管之前，因此很难用DMM测量这些二极管的管压降。 ADA4177的输出ESD二极管的管压降是可以测量的。



### 建立评估系统

图3用于测量运算放大器电路的电流流向等行为。通道A和通道B各 自配置为缓冲器，通道B同相输入端经由100 kΩ电阻连接到GND。让 V+不供电（V–供电）或V+供电（V–不供电），便可利用安培表和电 压表测量输入及电源相关变量（电压值和电流值）。通过分析这些 变量，可以确定电流流动的路径。

<img src="https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_03.png?la=zh" alt="图3-放大器电流路径评估系统建立" style="zoom:50%;" />

<center>图3. 放大器电流路径评估系统建立</center>



### 情形1：输入悬空

表4显示了一个输入悬空和一个电源未供电时的结果。当V–供电而 V+不供电时，V+引脚上有一个负电压。当V+供电而V–不供电时，V– 引脚上有一个正电压。

测试ADA4077-2和ADA4177-2得到类似的结果。输入引脚和电源引 脚上没有观测到大电流，输入悬空的运算放大器在一个供电轨没 有供电时仍然是安全的。



### 情形2：输入接地

表5显示了输入接地时的结果。注意，对于IB+，负值意味着电流流 出+IN引脚。对于IOUT，负值意味着电流流出–IN引脚。

<p><strong>表4. ADA4077-2/ADA4177-2输入悬空时的结果</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><span style="font-size: 13px;"><br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">条件<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 8%;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;width: 8%;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY+ (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY– (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 15%;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 15%;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 15%;"><span style="font-size: 13px;">IN (V)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 15%;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td rowspan="3" style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">ADA4077-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源都上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.02</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.01</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00005</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00007</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.008</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–13.1</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.12</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–13.73</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–14.42</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">13.06</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">12.93</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">13.62</span></td>
        </tr>
        <tr>
            <td rowspan="3" style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">ADA4177-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源都上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.98</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.96</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00002</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.001</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–14.26</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.14</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00002</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00137</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–13.77</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–13.78</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">12.96</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.14</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00039</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">12.26</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">12.31</span></td>
        </tr>
    </tbody>
</table>

<p><strong>表5. ADA4077-2/ADA4177-2输入接地时的结果</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><br>
            </td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">条件<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY+&amp;(mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY– (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">IN (V)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="3"><span style="font-size: 13px;">ADA4077-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源都上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.01</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00005</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.019</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.846</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.30</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.300</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.60</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.017</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.68</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.847</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.78</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.758</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.064</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.12</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.116</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="3"><span style="font-size: 13px;">ADA4177-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源都上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.98</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.96</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00001</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00002</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–11.99</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.3</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.300</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.200</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.068</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–11.98</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 无</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.848</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.84</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.823</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.067</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.013</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.851</span></td>
        </tr>
    </tbody>
</table>

以ADA4077-2 V+未上电的情况为例，ESD二极管将V+箝位于VIN电压。

- V I N通过E S D箝位二极管连接到V+，因此当V I N为0 V时，V+ 为–0.846 V。
- 电流流动路径：如图4中的红色路径所示，0.7 mA电流从GND (+IN)流到V+。1.6 mA电流从GND (+IN)经过内部电阻、D5以及–IN 和OUT之间的反馈路径，流入输出端。最后，这两个电流（0.7 mA 和1.6 mA）汇合流至–15 V，合并后的电流流回GND (+IN)。

ADA4177-2和ADA4077-2的结果类似。注意，ADA4177-2中的D1是通 过横向PNP晶体管的发射极基极实现的。该晶体管将过压电流从V+ 带走到V–。图4中的ADA4177电路显示有9.1 mA电流从V+流回V–，并 与反馈路径中的0.2 mA电流汇合，产生9.3 mA电流流至–15 V，然后 该电流流回GND。

ADA4077-2或ADA4177-2的输入引脚和电源引脚均未观测到大电流（表 5）。增益为+1且+IN接地时，这些运算放大器可承受任何时序的PU上电。



### 情形3：有输入

在一个电源未上电的情况下，将一个正信号或负信号（+10 V或-10 V） 施加于+IN端。表6显示没有大电流，因此当增益为+1且+IN有输入时， 这些运算放大器可承受任何顺序的PU上电。

电流流动路径分析与情形2（0 V输入）相似，参见图5。

![图4-V+未上电时ADA4077/ADA4177电流路径（输入接地）](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_04.png?la=zh)

<center>图4. V+未上电时ADA4077/ADA4177电流路径（输入接地）</center>

![图5-V+未上电时ADA4077/ADA4177电流路径（10 V输入）](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_05.png?la=zh)

<center>图5. V+未上电时ADA4077/ADA4177电流路径（10 V输入）</center>



<p><strong>表6</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><br>
            </td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">条件<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 10%;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY+ (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY– (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 10%;"><span style="font-size: 13px;">IN (V)<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 10%;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="5"><span style="font-size: 13px;">ADA4077-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源均上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.03</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.01</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.00098</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00003</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">10</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.97</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V + 不存在，正输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.14</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.4</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.396</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.653</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.99</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">7.3</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V + 不存在，负输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.83</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.41</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.308</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.651</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.02</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.66</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V – 不存在，正输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">10.83</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.81</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.689</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.055</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">10.02</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">12.09</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 不存在，负输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.77</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.759</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.031</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.99<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–7.88</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="5"><span style="font-size: 13px;">ADA4177-2<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源均上电</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.02</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00099</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.00009</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.99</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.97</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 不存在，正输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.09<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.86</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.866</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.113<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.92</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.06<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 不存在，负输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.33<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">4.31</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">4.18</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.039<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.02<br>
            </span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.32<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 不存在，正输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">11.42</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.33</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.2</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.056</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.99</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">11.43</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V– 不存在，负输入</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–8.33</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.51</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.492</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.062</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.97</span></td>
            <td style="padding: 10px 3px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–8.32</span></td>
        </tr>
    </tbody>
</table>



### 情形4：有输入且电源/输出有负载

在实际应用中，运算放大器电路可能要与其他电路一起工作。例如， 运算放大器的输出可能会驱动一个负载，或者运算放大器的电源 会为其他电路供电。这会引起问题。

在该测试中，一个47 Ω电阻连接在输出与GND之间，或连接在未上 电的电源引脚与GND之间。图7显示了ADA4077的测试结果。三种可 能情况会带来风险（假定V+未上电）：

<blockquote style="margin: 0px 0px 0px 40px; border: medium none; padding: 0px;">
<p>
情况1：当输入为10 V且OUT负载为47 Ω时，输出为1.373 V。有23
mA电流从运算放大器的输出引脚流出（参见图6），电流路径为：</p>
<p>
</p>
<ul>
    <li>输入信号源提供30.2 mA电流</li>
    <li>24 mA电流流经D1至V+，6.2 mA电流流经D5和反馈路径至OUT</li>
    <li>来自V+的24 mA电流分为1 mA（至V–）和23 mA（至OUT）</li>
    <li>29.2 mA电流流经47 Ω负载至GND</li>
</ul>
<p>
</p>
</blockquote>

ADA4077-2允许的输入电流最大为10mA，所以需要限流。在+IN端 增加一个1 kΩ电阻，可使输入电流降至6.8 mA。

<blockquote style="margin: 0px 0px 0px 40px; border: medium none; padding: 0px;">
<p><span>情况2：当输入为10 V且V+负载为47 Ω时，170 mA电流会流入
ADA4077-2，并从V+引脚流出到47 Ω电源负载。170 mA电流会烧
毁内部二极管，损坏芯片。在+IN端增加一个1 kΩ电阻，可使输入
电流降至8.9 mA。图7显示了电流流动路径。<br>
<br>
</span></p>
</blockquote>

<p><strong>表7.ADA4077的输出引脚或无电源的电源引脚上有负载</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><span style="font-size: 13px;">ADA4077-2</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">条件<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IN (V)</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY+ (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY– (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="8"><span style="font-size: 13px;">V+ 无<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 或 V+ 无负载/正输入</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.99</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.14</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.4</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.396</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.653</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">7.3</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.98</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.77</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.00</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">30.22</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–6.174</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.373</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND 和 1 kΩ</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.98</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.389</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.76</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">6.828</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.104</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.284</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 47 Ω 至 GND</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.59</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.01</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">170</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">5.05</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">175</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–5.0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">6.06</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 47 Ω 至 GND 和 1 kΩ</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.94</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.295</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">6.27</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.69</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.96</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.69</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.876</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 或 V+ 无负载/负输出</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.02</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.83</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.41</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.308</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.651</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.66</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.97</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–3.226</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">48.6</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–4.65</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">4.885</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.501</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND 和 1 kΩ</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.02</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.83</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">14.30</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.284</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–1.629</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.563</span></td>
        </tr>
    </tbody>
</table>



![Figure 6](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_06.png?la=zh)

<center>图6. V+未上电时ADA4077的电流路径（10 V输入和47 Ω输出负载）</center>

![Figure 7](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_07.png?la=zh)

<center>图7. V+未上电时ADA4077的电流路径（10 V输入和47 Ω电源负载）</center>

<blockquote style="margin: 0px 0px 0px 40px; border: medium none; padding: 0px;">
<div>
<p>情况3：当输入为负(-10 V)且OUT负载为47 Ω时（参见图8），有48
mA电流流经芯片。由此产生的功耗为48 mA × (–2.5 V + 15 V) =
0.6 W。ADA4077-2的θJA为158°C/W，因此结温比环境温度高出
94.8°。若有两个通道或负载更重，结温可能高于150°，致使芯片
受损。<br>
<br>
</p>
</div>
<div>
<p>不应在输入端增加限流电阻，而应在输出端增加限流电阻。<br>
<br>
</p>
</div>
<div>
<p>当V+上电而V–未上电时，会发生同样的现象。通过增加外部电
阻来限制电流，电路鲁棒性可以变得更好。<br>
<br>
</p>
</div>
</blockquote>

对于ADA4177-2，仅情况3适用。当有很大的负输入，同时输出端有 很重的负载，且V+未上电时，有53 mA电流流经芯片，功耗可能会 增加，结温随之提高（参见图9）。通过在输出端增加一个1 kΩ电阻， 可以避免这种风险。

在这两款运算放大器中，ADA4177-2比ADA4077-2更鲁棒。在同时要 求高精度和鲁棒性的应用中，前者是不错的选择。



### 其他运算放大器在不同上电时序下的表现

在运算放大器内部，二极管、电阻和OVP单元有各种各样的实施方式。 有些运算放大器没有内部OVP单元，有些没有背靠背二极管，有些没 有内部限流电阻。如果一个电源未上电，放大器不同的内部结构会产 生不同的结果。此外，不同的运算放大器设计也会产生不同的结果。

例如，ADA4084-2没有内部限流电阻和OVP单元，其ESD二极管连接 到电源和背靠背二极管。表9和图10显示了V+未上电且有10 V输入 时的结果。ADA4084的电流路径与ADA4077-2和ADA4177-2相似（上 文中的情形3已讨论）。然而，ADA4084没有内部电阻或OVP单元来 限制电流，60 mA电流会流入芯片，可能引起损害。

![Figure 8](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_08.png?la=zh)

<center>图8. V+未上电时ADA4077的电流路径（-10 V输入和47 Ω输出负载）</center>

![Figure 9](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_09.png?la=zh)

<center>图9. V+未上电时ADA4177的电流路径（-10 V输入和47 Ω输出负载）</center>

![Figure 10](https://www.analog.com/-/media/images/analog-dialogue/en/volume-50/number-4/articles/improper-power-sequencing-in-op-amps-analyzing-the-risks/136254_fig_10.png?la=zh)

<center>图10. V+未上电时ADA4084的电流路径（10 V输入）</center>



<p><strong>表8. ADA4177的输出引脚或无电源的电源引脚上有负载</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><span style="font-size: 13px;">ADA4177-2</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">条件<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IN (V)</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY+ (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">ISY– (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="8"><span style="font-size: 13px;">V+ 无<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 或 V+ 浮空和负输入</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.02<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.33</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">4.31</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">4.18</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.039</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–12.32</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–9.97</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–3.218</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">51.53</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.473</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">2.632</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–2.543</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">Vo 47 Ω 至 GND 和 1 kΩ</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–10.4</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.10</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.003</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0.147</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.428</span></td>
        </tr>
    </tbody>
</table>



<p><strong>表9</strong></p>

<table cellspacing="2" style="width: 100%;">
    <tbody>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #7c4a8b;"><span style="font-size: 13px;">ADA4084-2</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">Condition<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">V+<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">V–<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">I+&nbsp;(mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">I– (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IB+ (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac; width: 12%;"><span style="font-size: 13px;">IOUT (mA)<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">IN (V)</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #ffffff; background-color: #acacac;"><span style="font-size: 13px;">OUT (V)<br>
            </span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;" rowspan="8"><span style="font-size: 13px;"><br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">正负电源均上电</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15<br>
            </span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.38</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">1.37</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.001</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–0.0001</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">10</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.98</span></td>
        </tr>
        <tr>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">V+ 未上电，正输入</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">8.71</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–15</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">0</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">60.1</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">60.102</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">–51.89</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">9.56</span></td>
            <td style="padding: 10px 7px; border-top: 2px solid #ffffff; border-left: 2px solid #ffffff; text-align: center; vertical-align: middle; color: #636363; font-weight: lighter; background-color: #f5f5f5;"><span style="font-size: 13px;">7.99</span></td>
        </tr>
    </tbody>
</table>

在系统应用中，不同的运算放大器、不同的拓扑结构（如同相放大、 反相放大、差动放大等）、不同的负载和外部连接都可能存在。如 果存在有某个电源未上电的情况，需要对风险进行评估。本文介绍 了如何搭建评估风险的电路（图2）、如何分析电流路径以及评估潜 在的风险。



### 总结

为了避免过压或闩锁情况，必须同时建立运算放大器电源。一般指 南如下：

- 上电时，先接通电源，再在输入端施加信号
- 关断时，先关闭输入信号，再关闭电源

在实际应用中，可能难以遵守这些指导原则。这可能会引起问题， 尤其是当有输入信号时，设计人员需要适当评估风险。一种有效的 解决方案是限制运算放大器的输入电流，使它在数据手册给出的 规格以内。在无法同时上电的应用中，输入端和输出端增加限流电 阻会有帮助。

我们在电源未上电的应用中测试了三款ADI运算放大器（ADA4084-2、 ADA4077-2和ADA4177-2）。集成内部电阻的ADA4077-2表现不错。集 成OVP电路的ADA4177的鲁棒性最好。在某个电源在某个时间段可 能未上电且无法增加外部限流电阻的应用中，推荐使用ADA4177以 避免精度性能下降。



### 参考电路

[ADA4077](https://www.analog.com/cn/products/ada4077-1.html). ADI公司。

[ADA4177](https://www.analog.com/cn/products/ADA4177-1.html). ADI公司。

> Arkin, Michael and Eric Modica. "[鲁棒的放大器提供集成过压保护。](https://www.analog.com/cn/analog-dialogue/articles/robust-amplifiers-provide-integrated-overvoltage-protection.html)"《模拟对话》，第46卷，第1期，2012年。
>
> Blanchard, Paul and Brian Pelletier. "[ESD二极管用于电压箝位.](https://www.analog.com/cn/analog-dialogue/articles/esd-diodes-as-voltage-clamps.html)"《模拟对话》，第49卷，第10期，2015年。

欲了解更多有关ADA4177和ADA4077的信息，请参见产品页面和数 据手册[ADA4177](https://www.analog.com/cn/products/ada4177-2.html) 和 [ADA4077](https://www.analog.com/cn/products/ADA4077-2.html)。



**作者**

David Guo 是ADI公司位于北京的中国应用支持部门的一名现场应用工程师。获得北京理工大学机电工程硕士学位后，他在长峰集团工作过两年，担任导航终端硬件工程师。他于2007年加入ADI公司。
