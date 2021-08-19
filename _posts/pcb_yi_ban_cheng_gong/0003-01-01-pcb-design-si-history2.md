---
title: "信号完整性的历史（黑魔法开始出现）"
subtitle: "PCB设计一板即成功专栏"
layout: post
date:   2021-01-01
author: "Huanqing"
header-style: text
hidden: true
catalog: true
tags:
  - PCB一板成功
---

也许历史上第一次遇到信号完整性问题的应该是在始于1854年的跨大西洋电报项目，该项目于1858年完成了海底电缆的铺设。电缆铺设完工之后，要举行一个庆典仪式，也即由英国的维多利亚女王通过跨大西洋电报向美国总统布坎南发出欢迎信。遗憾的是，信号完整性问题导致女王的99个字的欢迎致辞需要近17个小时的时间来传输，而不是预期的几分钟。信号完整性问题使跨大西洋电报电缆传输速度降低到了几乎无法使用的速度。为了尝试解决这个问题，次月， 怀尔德曼·怀特豪斯向电缆施加了过高电压，同时试图实现更快的运行速度时，电缆被毁了，该项目仅仅运行了三个星期就宣告失败。

<link href="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.css" rel="stylesheet">
<div id="dplayer"></div>
<script src="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.js"></script>
<script src="https://cdn.bootcss.com/blueimp-md5/2.12.0/js/md5.min.js"></script>
<script>
var url1="https://files.catbox.moe/c9awxa.mp4";    //这里填写视频地址
var pic1="https://files.catbox.moe/tmg0nm.jpg";   //这里填写预览图片地址
var logopng="https://gitee.com/hawkingwu/PicGo/raw/master/linearroglogo_l.png";  //logo
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
    logo: logopng,
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

1865年人们对跨大西洋电报项目进行了第二次尝试，使用了大大改进的材料，并在遇到一些挫折之后，完成了连接并于1866年7月28日投入使用。这次电缆的制造方法以及发送消息的方法已得到了极大的改进。 1866年铺设的电缆每分钟可以传输8个字——比1858电缆快80倍。 奥利弗·亥维赛和米海洛·卜平在随后的几十年中了解到，电缆的带宽会受到电容性电抗和电感性电抗之间的不平衡的阻碍，从而导致严重的色散 ，进而导致信号失真。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/1858年跨大西洋电缆路线图.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/1858年跨大西洋电缆路线图.jpg)

1858年跨大西洋电缆路线图

跨大西洋电缆的长度非常长，好几千公里，而电子产品上的互联线虽然短，但随着信号上升/下降沿时间变短，也遇到了信号完整性问题。

随着ASTTL(**A**dvanced **S**chottky **T**ransistor **T**ransistor **L**ogic)的出现，信号完整性问题开始出现。ASTTL比标准TTL快得多。上升时间降到了2纳秒，栅极延迟降到了6纳秒，时钟周期来到了100MHz–这已经非常快了! 这也即有些书上描述的，时钟周期高于100MHz就视为高速的缘由吧。

**不过它真正的原因是信号上升时间降到了2纳秒**，我们所需要关注的频率为0.35/2ns，也即175MHz，换算为FR4上的1/10波长电尺寸约为：8.57 cm！这个尺寸已经接近甚至要小于实际产品的电路板尺寸了！这时候互联线已经不能再视为“透明”！

然而，潜意识里认为只要把线拉通就行的工程师们仍然沿用着为标准TTL开发的布线规则。信号传输的时间延迟和传输线效应都没有进行考虑。人们想不明白，明明就是一条铜箔导线而已，怎么就冒出来看不见摸不着的电阻、电感和电容来，这简直就是有人要害朕，施展了深不可测的黑魔法！

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/黑魔法.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/黑魔法.png)

更玄学的是，由于74系列封装一样，通过尾标来区分标准TTL还是高速或者低功耗TTL、可能是管理疏忽或者装配人员看错型号，用高速TTL器件替换了标准TTL器件，本来已经大规模量产的稳定产品开始出现大面积的不稳定状况，百思不得其姐，莫非被友商施展了黑魔法不成？

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/74-TTL-系列.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/74-TTL-系列.jpg)

其实TI在Advanced Schottky Family就有注明了高速信号相关的PCB Layout Guide，老wu这里找了一份1985年编写的，上传到专栏的资源区里头了，感兴趣的朋友可以下载下来看一下。

老wu这里对这份TI的Advanced Schottky Family截取了部分内容，让我们看看1980年代，当时对于解决信号完整性问题的一些关注点：

[TI Advanced Schottky Family](https://www.mr-wu.cn/wp-content/uploads/2021/01/TI-Advanced-Schottky-Family.pdf)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-1.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-1.jpg)由于信号上升沿时间变短，需要关注更高次谐波对信号频谱的贡献，哪怕信号周期只有几MHz！我们所关注的最高频率也能超过100MHz！

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/截屏2021-01-14-下午11.31.47.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/截屏2021-01-14-下午11.31.47.png)

还要关注阻抗的控制

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-串扰问题.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-串扰问题.png)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-串扰问题2.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-串扰问题2.png)

还要关注信号间的串扰问题，减小走线到参考平面的距离H或者拉大走线间距S都能减小走线间的串扰。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-反射问题.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/信号完整性的历史（黑魔法开始出现）-反射问题.jpg)

还要关注阻抗不匹配造成的反射影响

<div class="tutor-page-segment tutor-attachments-wrap">
        <h3>附件</h3>
                    <a href="https://www.mr-wu.cn/wp-content/uploads/2021/01/TI-Advanced-Schottky-Family.pdf" download="TI Advanced Schottky Family.pdf" class="tutor-lesson-attachment clearfix">
                <div class="tutor-attachment-icon">
                    <i class="tutor-icon-document"></i>
                </div>
                <div class="tutor-attachment-info">
                    <span>TI Advanced Schottky Family.pdf</span>
                    <span>1.85 MB</span>
                </div>
            </a>
                </div>
