---
title: "2.1 PCB设计拉线到底拉的是什么"
subtitle: "第二章 PCB设计必知必会的概念"
layout: post
date:   2021-01-01
author: "Huanqing"
header-style: text
hidden: true
catalog: true
tags:
  - PCB一板成功
---

![https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E7%94%A8%E6%B0%B4%E6%B5%81%E6%AF%94%E4%BD%9C%E7%94%B5%E6%B5%81.webp](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E7%94%A8%E6%B0%B4%E6%B5%81%E6%AF%94%E4%BD%9C%E7%94%B5%E6%B5%81.webp)

还记得我们初中物理课上老师把电流类比为水流的这张图吗？上图中的泵A使水在恒定压力P1下绕着一个闭合回路运动。只要阀门B保持开启或至少部分开启的状态，在管道中流动的水就会达到稳定的速度V1。泵的压力、水的粘度以及回路中使用的管道、阀门和弯头的有效流体流动阻力决定了这个速度。这也类似于一个简单的电路回路，老师在课上做实验时会拿出一个电池、一个电阻、以及一些导线组成一个简单的回路。电池类似于水箱，电池产生的静电压与泵头的水压相对应。导线中电流的循环与管道中水的循环相对应。

这样的类比有利于学生们对于电路行为的理解，因为我们日常生活中都有接触过水管中水流的经验，但这是对电路行为细节的简化，如果我们只是需要学习一些基本的电路知识，这就足够了。

但到了大学物理，学习了电磁学之后，同样是电池、电阻和导线组成的电路则表示成：

![https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/Poynting_vectors_of_DC_circuit.svg.webp](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/Poynting_vectors_of_DC_circuit.svg.webp)

![https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%9D%A1%E5%8D%B0%E5%BB%B7%E7%9F%A2%E9%87%8F.webp](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%9D%A1%E5%8D%B0%E5%BB%B7%E7%9F%A2%E9%87%8F.webp)

在电路理论中，认为是用导体来运输能量，这在采用集总参数为核心思想的电路理论中是正确的。

当实际电路的线性尺寸远小于电路工作时电磁波的波长或者说电磁波通过电路的时间是瞬时的，则整个电路的实际尺寸可以忽略不计，因而可以把它集总在一起，用足以反映其电磁性质的一个或有限个分立的电阻、电感、电容等元件来加以描述，这种理想电路元件就叫做集总参数元件，或者称为集总元件(Lumped Circuit Elements) 。在集总参数元件中，电阻、电感、电容是3种最基本的元件。[1]

电路理论可以让我们得到一组互相连接的元件的电路电压及其流动的电流。对于RLC(电阻-电感-电容)的分析可以直接利用基尔霍夫定律进行分析。

而真实世界的情形是，导体本身是不能传输和存储能量的。能量存储在场中，也通过场来传输能量，而导体只是为能量流动路径提供了方向指引。



<link href="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.css" rel="stylesheet">
<div id="dplayer"></div>
<script src="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.js"></script>
<script src="https://cdn.bootcss.com/blueimp-md5/2.12.0/js/md5.min.js"></script>
<script>
var url1="https://files.catbox.moe/0o2plz.mp4";    //这里填写视频地址
var pic1="https://files.catbox.moe/7oq66d.jpg";   //这里填写预览图片地址
var id=md5(url1);
const dp = new DPlayer({
    container: document.getElementById('dplayer'),
    autoplay: false,
    theme: '#FADFA3',
    loop: true,
    lang: 'zh-cn',
    screenshot: true,
    hotkey: true,
    preload: 'auto',
    volume: 0.7,
    mutex: true,
    video: {
        url: url1,
        pic: pic1,
        thumbnails: pic1,
        type: 'auto',
    },
    contextmenu: [
        {
            text: 'custom1',
            link: 'https://huanqingwu.github.io/',
        },
        {
            text: 'custom2',
            click: (player) => {
                console.log(player);
            },
        },
    ],

});
</script>


**这看起来很疯狂不是吗，但这就是真实的世界。**

以电磁场的视角，我们所关心的是发生在某一物理系统中空间各点的电磁过程以及电磁能量在空间的传输和分布情况。所涉及的能量损耗与电场能量都以能量体密度的形式出现。

在电路问题中，用电路模型以及电路的物理量来描述一个物理系统的电磁过程。表征这些电磁过程的物理量是电流、电压、磁通和电荷。常见的电路模型则由电阻、电感及电容等无源元件以及电压源、电流源有源元件联结而成。

由此可见，电磁场与电路都是研究一个物理系统中所发生的电磁过程的。而任何真实存在的电磁现象都必须遵循电磁场基本定律。也即在专栏【信号完整性的历史（互联是透明阶段）】章节里提到的：

“物理世界的行为与麦克斯韦方程的预测是完全一致的，如果我们将量子力学加入到与麦克斯韦方程的原理中，也就是所谓的量子电动力学（QED），我们最终会得到一个真实世界的模型。”

电磁场理论所描述的电磁现象要比电路理论更普遍。如在电路理论中的“电压”、“电流”的概念，在本质上是什么?对于这些电路理论常用却又解释不清，电磁场理论都给予了清楚的回答。即电流是电流密度沿某一面积的面积分，而电压则是电场强度沿某一路径的线积分。[2]

**什么意思，难道说麦克斯韦方程组才是真相而基尔霍夫定律是错的吗？**

**显然不是！**

电磁场科学理论体系的创立要归功于伟大的物理学家同时也是数学教授的麦克斯韦(J.C．Maxwell)。 1864年，他集前人之大成创立了不朽的麦克斯韦方程组，以严格的数学形式描述了电与磁的内在联系，同时他还发表了存在电磁波的伟大预言。他的理论和预言后来在1887年被赫兹(H.R.Hertz)用实验所证明，从而又开创了无线电及电子科学的新纪元。

为电路理论奠定基础的是伟大的德国物理学家基尔霍夫(G.R.Kirchhoff)。1847年，刚满23岁的大学生基尔霍夫发表了划时代论文“关于研究电流线性分布所得到的方程的解”，文中提出了分析电路的第一定律(电流定律KCL)和第二定律(电压定律KVL)，同时还确定了网孔回路分析法的原理。

可从电磁场理论体系的核心麦克斯韦方程组推导出电路理论体系的核心KCL和KVL，这又充分表明了电磁场问题与电路问题之间存在着必然的内在联系和辩证的统一。

基尔霍夫的两个定律都可以理解为麦克斯韦方程在低频极限下的必然结果。它们对于直流电路以及电磁辐射波长与电路相比非常大的频率下的交流电路都是准确的。

虽然麦克斯韦方程可以解释所有的电现象，但从数学上来讲它们是相当复杂的。因此，在可能的情况下，就使用较简单的近似方法，如集总参数电路模型和基尔霍夫定律。

比如我们画原理图，我们需要把复杂问题简化成原理图符号，以电路理论描述电路的组成结构和基本性能。

![https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%8E%9F%E7%90%86%E5%9B%BE.webp](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%8E%9F%E7%90%86%E5%9B%BE.webp)

但原理图开始转换到PCB上，也即我们Layout时，我们要意识到这是一种简化。

![https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%AE%9E%E9%99%85PCB%E4%BF%A1%E5%8F%B7.webp](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/%E5%AE%9E%E9%99%85PCB%E4%BF%A1%E5%8F%B7.webp)

在低频时，PCB上的互联线可以看成是透明的，可以等价为原理图上的连接关系，使用电路的分析方法来解决问题。但在足够高的频率下，元件会失去其简单的电路特性。

例如，可以把电容器看作具有串联的电阻和电感。有了电感则意味着有磁场参与了能量的传递。如果采用简单的电路理论方法去分析可能是无效的。如果我们求助于场论，我们也得不到精确的解。如果我们想要了解电路中实际发生了什么，必须将场理论和电路理论都应用到这个问题中。**基于“场”的思维，运用“路”的方法研究信号的本质，这样我们才能做出好的工程决策。**

**总结一下**，PCB设计拉线到底拉的是什么？ 我们拉的是能量，能量储存在场中，能量主要通过导线周围的介质传播，导线只是指引了方向。

[1] 杨洪波，《电路分析基础》，清华大学出版社， pp. 2.

[2] 李凤霞，《由基尔霍夫定律看电磁场理论与电路理论的关系》



### 附件

<a href="https://www.mr-wu.cn/wp-content/uploads/2021/01/电路分析基础.pdf" target="_blank">电路分析基础.pdf 8.29 MB</a>

<a href="https://www.mr-wu.cn/wp-content/uploads/2021/01/电磁现象的基本规律-与电磁波.pdf" target="_blank">电磁现象的基本规律 与电磁波.pdf 2.46 MB</a>

<a href="https://www.mr-wu.cn/wp-content/uploads/2021/01/由基尔霍夫定律看电磁场理论与电路理论的关系.pdf" target="_blank">由基尔霍夫定律看电磁场理论与电路理论的关系.pdf 318.84 KB</a>

