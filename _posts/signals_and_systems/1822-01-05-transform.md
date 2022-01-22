---
title: "5. 我们为何需要数学变换？泰勒展开和傅里叶变换有什么本质联系"
subtitle: "信号与系统精讲：玩转卷积与变换"
layout: post
date:   2022-01-21
author: "Huanqing"
header-style: text
mathjax: true
catalog: true
hidden: true
tags:
  - 信号与系统专栏
---

对信息、电子专业的学生来说，本科阶段比较常用的变换有傅里叶变换、拉普拉斯变换和Z变换。

当然，还有希尔伯特变换等，包括最基础的泰勒级数，我觉得也可以算是一种变换。

科学家、工程师**为什么要搞这些稀奇古怪的变换呢？**

因为，**变换可以省事，极大地提升效率。**

- #### 什么是变换

  其实，**我们高中就学过一种数学变换，那就是“对数运算”。**

  这是一个通过变换来简化计算典型而通俗的例子。

  比如，需要计算：

  >  $8 \times 16 = ?$ 

  用对数计算，可以转换成（以2为底）：

  >  $\log _{2}(8 \times 16)=\log _{2} 8+\log _{2} 16=3+4=7$ 

  如果下一个环节需要继续计算：

  >  $(8 \times 16) \times 32$ 

  我们可以将32也变换到“对数域”，即：

  >  $\log _{2}32=5$ 

  则 $(8 \times 16) \times 32$ 在“对数域”就变成了加法：

  >  $\log _{2}[(8 \times 16) \times 32]=\log _{2}(8 \times 16)+\log _{2}32=7+5=12$ 

  需要结果？只需进行**“反变换”**：

  >  $2^{12}=4096$ 

  因此，**对数可以将“乘除法”变换成“加减法”。**

  **这在数字较大、环节较多的场景优势非常明显，**比如天文领域，天体动辄上亿的距离和质量。

  一亿在对数域（10为底），不过是8而已：

   $\log _{10}100000000=8$ 

  更重要的是，**乘除法运算就可能在“直尺”上用加减实现，这就是后来“计算尺”的基本原理。**

  

  ![6f281075778d9607f89438c6b3cfd0ad](https://gitee.com/hawkingwu/PicGo/raw/master/6f281075778d9607f89438c6b3cfd0ad.jpg)

   <center><font size="2">计算尺</font></center> 

  在没有电子计算机的时代，计算尺是非常重要的发明之一，它帮助了无数工程师和科学家。

  宫崎骏电影《起风了》的男主是一名飞机工程师，当他计算参数时，计算尺形影不离：

  ![d0185fa4d8130c8a51d2012a149079a0](https://gitee.com/hawkingwu/PicGo/raw/master/d0185fa4d8130c8a51d2012a149079a0.jpg)

  推动几下，然后记录计算结果，如此往复：

  ![6cce528efddf1b3928b7262b5c7e8803](https://gitee.com/hawkingwu/PicGo/raw/master/6cce528efddf1b3928b7262b5c7e8803.jpg)

  德国火箭专家**冯·布劳恩**二战后到美国从事航天工作时，**随身带了两把1930年代的“Nestler”计算尺。**

  **终其一生，他没有用过任何其它便携式计算器。**

  他的作品是，阿波罗登月飞船使用的大名鼎鼎的“土星5号”运载火箭。

  

- #### 泰勒级数

  在高等数学教科书上，“泰勒公式”不仅看起来吓人，而且来得非常突然，

  <math xmlns="http://www.w3.org/1998/Math/MathML">
    <mi>f</mi>
    <mo stretchy="false">(</mo>
    <mi>x</mi>
    <mo stretchy="false">)</mo>
    <mo>=</mo>
    <mfrac>
      <mrow>
        <mi>f</mi>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>0</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
      </mrow>
      <mrow>
        <mn>0</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mo>+</mo>
    <mfrac>
      <mrow>
        <msup>
          <mi>f</mi>
          <mrow>
            <mi data-mjx-alternate="1" mathvariant="normal">′</mi>
          </mrow>
        </msup>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>0</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
      </mrow>
      <mrow>
        <mn>1</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">(</mo>
      <mi>x</mi>
      <mo>−</mo>
      <msub>
        <mi>x</mi>
        <mrow>
          <mn>0</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">)</mo>
    </mrow>
    <mo>+</mo>
    <mfrac>
      <mrow>
        <msup>
          <mi>f</mi>
          <mrow>
            <mi data-mjx-alternate="1" mathvariant="normal">′</mi>
            <mi data-mjx-alternate="1" mathvariant="normal">′</mi>
          </mrow>
        </msup>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>0</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
      </mrow>
      <mrow>
        <mn>2</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">(</mo>
        <mi>x</mi>
        <mo>−</mo>
        <msub>
          <mi>x</mi>
          <mrow>
            <mn>0</mn>
          </mrow>
        </msub>
        <mo data-mjx-texclass="CLOSE">)</mo>
      </mrow>
      <mrow>
        <mn>2</mn>
      </mrow>
    </msup>
    <mo>+</mo>
    <mo>…</mo>
    <mo>+</mo>
    <mfrac>
      <mrow>
        <msup>
          <mi>f</mi>
          <mrow>
            <mo stretchy="false">(</mo>
            <mi>n</mi>
            <mo stretchy="false">)</mo>
          </mrow>
        </msup>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>0</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
      </mrow>
      <mrow>
        <mi>n</mi>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">(</mo>
        <mi>x</mi>
        <mo>−</mo>
        <msub>
          <mi>x</mi>
          <mrow>
            <mn>0</mn>
          </mrow>
        </msub>
        <mo data-mjx-texclass="CLOSE">)</mo>
      </mrow>
      <mrow>
        <mi>n</mi>
      </mrow>
    </msup>
    <mo>+</mo>
    <msub>
      <mi>R</mi>
      <mrow>
        <mi>n</mi>
      </mrow>
    </msub>
    <mo stretchy="false">(</mo>
    <mi>x</mi>
    <mo stretchy="false">)</mo>
  </math>

   <center><font size="2">泰勒公式</font></center> 

  它好像是无缘无故突然从石头缝里蹦出来的一个概念，但真相完全不是这样。

  

- #### 老板的计算问题

  假设我们出生在两百年前，**没有电子计算器。**

  我们的老板遇到一个工程问题，比如桥梁设计，要求我们计算$\sin31.1°$等于多少，而且要求结果精确到小数点后三位。

  按照三角公式的定义，我们得用量角器画图，然后用直尺测量边长，再计算直角边 $a$ 除以斜边 $c$ 。

  <img src="https://gitee.com/hawkingwu/PicGo/raw/master/aae104b2d6d9ee8e8a2d787d0a57b1a4.jpg" alt="aae104b2d6d9ee8e8a2d787d0a57b1a4" style="zoom: 75%;" />

  这不仅麻烦，而且精度说不清，**谁都不知道我们画的直角到底有多直，这种计算方法根本无法定量评估结果的精度。**

  

- #### 神奇拆解

  现在，有了泰勒展开公式，我们可以直接将 $\sin x$ 拆**“解成一堆”**关于 $x$ 的加减乘除运算（ $x$ 使用弧度）：

  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mi>sin</mi>
    <mo data-mjx-texclass="NONE">⁡</mo>
    <mi>x</mi>
    <mo>=</mo>
    <mo>+</mo>
    <mfrac>
      <msup>
        <mi>x</mi>
        <mrow>
          <mn>1</mn>
        </mrow>
      </msup>
      <mrow>
        <mn>1</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mo>−</mo>
    <mfrac>
      <msup>
        <mi>x</mi>
        <mrow>
          <mn>3</mn>
        </mrow>
      </msup>
      <mrow>
        <mn>3</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mo>+</mo>
    <mfrac>
      <msup>
        <mi>x</mi>
        <mrow>
          <mn>5</mn>
        </mrow>
      </msup>
      <mrow>
        <mn>5</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mo>−</mo>
    <mfrac>
      <msup>
        <mi>x</mi>
        <mrow>
          <mn>7</mn>
        </mrow>
      </msup>
      <mrow>
        <mn>7</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mo>+</mo>
    <mo>⋯</mo>
  </math>

   <center><font size="2">sinx 的泰勒展开</font></center> 

  注意，这里不是约等于，是“完美的”等于，只不过，后面是无穷多项累加。

  但是，我们也不需计算无穷多项，因为，**后面的高次项对于结果的“贡献”越来越小，**因此，我们往往只需计算前若干项即可，比如前三项：

  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mi>sin</mi>
    <mo data-mjx-texclass="NONE">⁡</mo>
    <mi>x</mi>
    <mo>=</mo>
    <mi>x</mi>
    <mo>−</mo>
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>3</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mi>x</mi>
      <mrow>
        <mn>3</mn>
      </mrow>
    </msup>
    <mo>+</mo>
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>5</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mi>x</mi>
      <mrow>
        <mn>5</mn>
      </mrow>
    </msup>
    <mo>+</mo>
    <mi>o</mi>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">(</mo>
      <msup>
        <mi>x</mi>
        <mrow>
          <mn>5</mn>
        </mrow>
      </msup>
      <mo data-mjx-texclass="CLOSE">)</mo>
    </mrow>
  </math>

  尾巴直接扔掉，虽然会造成误差，但余项都是比 $x^5$ 高阶的无穷小，因此可以得出：

  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mi>sin</mi>
    <mo data-mjx-texclass="NONE">⁡</mo>
    <mi>x</mi>
    <mo>≈</mo>
    <mi>x</mi>
    <mo>−</mo>
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>3</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mi>x</mi>
      <mrow>
        <mn>3</mn>
      </mrow>
    </msup>
    <mo>+</mo>
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>5</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <msup>
      <mi>x</mi>
      <mrow>
        <mn>5</mn>
      </mrow>
    </msup>
  </math>

    <center><font size="2">使用前三项估算</font></center> 

  而且，估算造成的误差不会超过：

  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mfrac>
      <mn>1</mn>
      <mrow>
        <mn>7</mn>
        <mo>!</mo>
      </mrow>
    </mfrac>
    <mrow>
      <mo stretchy="false">|</mo>
    </mrow>
    <mi>x</mi>
    <msup>
      <mo stretchy="false">|</mo>
      <mrow>
        <mn>7</mn>
      </mrow>
    </msup>
  </math>

  

- #### 展开的优势

  经过这么一番折腾，即使在没有电子计算器的情况下，**我们通过手算加减乘，也可以“控制”结果的精度。**

  老板要求多高的精度，就可以有多高的精度，我们对着泰勒公式，在草稿纸上一直算下去即可。

  泰勒公式本质上是一种“幂级数”，**它将复杂的运算，统一成为“代数加减乘除”运算。**

  因此，**泰勒公式可以将运算本身“质的复杂度”，转换为“量的复杂度”，并进行估算。**

  现代编程语言中，很多库函数，就是通过泰勒展开实现计算的。

  计算机可以算加减乘除，泰勒公式正好提供了“一堆”加减乘除。



- #### 傅里叶级数

  类似泰勒级数的“拆解”原理，我们可以将一些函数展开成“傅里叶级数”。

  比如，可以在一个周期内，将 $x^2$ 展开：
  
  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <msup>
      <mi>x</mi>
      <mrow>
        <mn>2</mn>
      </mrow>
    </msup>
    <mo>=</mo>
    <mfrac>
      <msup>
        <mi>π</mi>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msup>
      <mn>3</mn>
    </mfrac>
    <mo>−</mo>
    <mn>4</mn>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">(</mo>
      <mi>cos</mi>
      <mo data-mjx-texclass="NONE">⁡</mo>
      <mi>x</mi>
      <mo>−</mo>
      <mfrac>
        <mrow>
          <mi>cos</mi>
          <mo data-mjx-texclass="NONE">⁡</mo>
          <mn>2</mn>
          <mi>x</mi>
        </mrow>
        <msup>
          <mn>2</mn>
          <mrow>
            <mn>2</mn>
          </mrow>
        </msup>
      </mfrac>
      <mo>+</mo>
      <mfrac>
        <mrow>
          <mi>cos</mi>
          <mo data-mjx-texclass="NONE">⁡</mo>
          <mn>3</mn>
          <mi>x</mi>
        </mrow>
        <msup>
          <mn>3</mn>
          <mrow>
            <mn>2</mn>
          </mrow>
        </msup>
      </mfrac>
      <mo>−</mo>
      <mo>⋯</mo>
      <mo data-mjx-texclass="CLOSE">)</mo>
    </mrow>
  </math>
  
  其中 $(-\pi \leq x \leq \pi)$ 
  
  注意，和泰勒展开类似，这里也是“完美的等于“，不是“约等于”。
  
  只不过，傅里叶级数是拆解成“三角函数”的累加。
  
  
  
- #### 三角级数的优势

  三角函数 $\sin x$（或 $\cos x$）的微分依然是三角函数：

  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mo stretchy="false">(</mo>
    <mi>sin</mi>
    <mo data-mjx-texclass="NONE">⁡</mo>
    <mi>x</mi>
    <msup>
      <mo stretchy="false">)</mo>
      <mrow>
        <mi data-mjx-alternate="1" mathvariant="normal">′</mi>
      </mrow>
    </msup>
    <mo>=</mo>
    <mi>cos</mi>
    <mo data-mjx-texclass="NONE">⁡</mo>
    <mi>x</mi>
  </math>

  积分也依然是三角函数：
  $$
  \int \sin x d x=-\cos x+c
  $$
  在信号分析时，这个特点会带来很大的优势。

  **因为，微分和积分运算，只可能改变三角信号的“相位”和“幅度”，而不改变其类型。**

  这样，**我们可以将信号“拆解”成一堆正弦信号，然后就可以只关心每个正弦波的“幅相”变化，运算起来极其方便。**

  

- #### 拉普拉斯变换

  > 将微积分转换为代数运算，应用场景：解线性微分方程。

  > 将卷积运算转换为乘法运算，应用场景：系统的传递函数。

  限于篇幅，欢迎请大家收看专栏的视频节目。

  

- #### 生活中的变换

  比如，我们发邮件。

  如果要发送上百个KB级别的小文件，我们往往不会选择一个一个地上传并发送,而是选择先压缩成zip压缩包，再发送这个“打包”的文件。

  接收方收到后再进行“解压缩”即可。

  文件在电脑间传输，只需以压缩包的形式流通，这样更高效。

  因此，**变换其实就像一个买卖，变换带来的好处更多，那我们就愿意变换，省时省力。**

  各种稀奇古怪的方法能流传至今，都是有原因的。

  

