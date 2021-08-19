---
title: "PCB上信号传播的速度，绕等长？不！我们要的是等时！（蛇形线）"
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

对于有时序控制要求的布线，我们会进行蛇形绕线进行长度补偿，以图让所有时序相关的走线在物理长度上尽量相等，最终的目的是让信号的传播延时尽量一致，以满足时序要求。

但走线间物理长度相等了，信号传播时间也会不一致，在[PCB上信号传播的速度，绕等长？不！我们要的是等时！（一）](https://huanqing.netlify.app/2021/01/01/pcb-weidaixian/) 这篇专栏文章我们了解到微带线和带状线由于有效介电常数不一致，物理长度相等而信号传播延时不相等的情况，此篇我们来了解绕蛇线等长而不等时的情况。


<div id="dplayer1"></div>


如上视频所示，两条微带线物理长度相等，我们可以看到信号在走线中传播的路径有很大区别，并且信号传播的时间也不一致。

<img src="https://cdnimg.mr-wu.cn/wp-content/uploads/2021/03/绕等长延时示意图.png" alt="img" style="zoom: 33%;" />

通过对比我们可以看到，电磁波A并没有按照我们的设想的引导路径来蜿蜒前进而是直接跨过了线段之间的间隙走了捷径。

这是由于走线分段边与边之间的间隙不够，产生了串扰，这是同网络间的串扰。

当PCB上走线间距较近时，一条走线上传输的电磁波，会在邻近的走线上引起噪声，这种现象称为串扰。串扰实际上是相邻走线之间的一种能量传递现象。

<img src="https://cdnimg.mr-wu.cn/wp-content/uploads/2021/03/串扰场数据-1.png" alt="img" style="zoom: 33%;" />

关于串扰的具体内容，专栏后续会有单独的讲解，这里先理解串扰会会对时序产生影响。

蛇形线内部的串扰由信号产生，反过来又叠加到信号本身，可以看作是特殊走线方式下信号对其自身的干扰。蛇形线内部的串扰总是表现为近端串扰，串扰噪声的跳变方向和 信号相同，因此这种串扰总是加速信号的传播，使信号提前到达接收端。如果绕线处理不好，就会较多地偏离预期延迟值，达不到预期效果。[1]

既然造成信号加速的原因是绕线区域的串扰，那么只要能最大限度地减小这种串扰， 就不会对信号的延迟甚至造成太大的影响。在绕线过程中有两个参数是很容易控制的，即控制

走线间距（g)和走线间耦合长度（h）,如下所示:

<img src="https://cdnimg.mr-wu.cn/wp-content/uploads/2021/03/蛇形线间距.png" alt="img" style="zoom: 33%;" />

**控制走线间距（g)为多少合适？**


<div id="dplayer2"></div>

通过上边的演示视频我们可以发现，走线间距（g)为多少合适考虑到走线与参考层间距H的因素

<img src="https://cdnimg.mr-wu.cn/wp-content/uploads/2021/03/串扰-关于h关系.png" alt="img" style="zoom: 33%;" />



<link href="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.css" rel="stylesheet">
<script src="https://cdn.bootcss.com/dplayer/1.25.0/DPlayer.min.js"></script>
<script src="https://cdn.bootcss.com/blueimp-md5/2.12.0/js/md5.min.js"></script>
<script>
var url1="https://files.catbox.moe/uof8wj.mp4";    //这里填写视频地址
var pic1="https://files.catbox.moe/m0nbx0.jpg";   //这里填写预览图片地址
var url2="https://files.catbox.moe/0qghyi.mp4";    //这里填写视频地址
var pic2="https://files.catbox.moe/mg8ouv.jpg";   //这里填写预览图片地址
var logopng="https://gitee.com/hawkingwu/PicGo/raw/master/linearroglogo_l.png";  //logo
var id=md5(url1);
var id=md5(url2);
const dp1 = new DPlayer({
    container: document.getElementById('dplayer1'),
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

const dp2 = new DPlayer({
    container: document.getElementById('dplayer2'),
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
        url: url2,
        pic: pic2,
        thumbnails: pic2,
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
