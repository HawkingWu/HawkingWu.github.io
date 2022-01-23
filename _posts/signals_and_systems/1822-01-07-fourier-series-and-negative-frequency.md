---
title: "7. 什么是傅里叶级数？傅里叶变换为何产生负频率？"
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



要理解这个问题，我们需要从傅里叶变换的最基本的原理说起。

首先，傅里叶变换来源于傅里叶级数。



- ##### 傅里叶级数

  所谓傅里叶**级数**，就是：

  > 把一个周期信号，拆解成一堆正弦波的叠加。

  比如，一个似乎是**方波**的周期信号 $f(t)$ ：

  ![b52d3f02eabf45951449be9c79899d49](https://gitee.com/hawkingwu/PicGo/raw/master/b52d3f02eabf45951449be9c79899d49.jpg)

  可以拆分成多个**正弦波的叠加：**

  ![66841c916628c28d710ab69165d018fe](https://gitee.com/hawkingwu/PicGo/raw/master/66841c916628c28d710ab69165d018fe.jpg)

  至于为什么要把信号拆成这样，专栏的一篇文章**“我们为何需要数学变换”**讲了，这里不再赘述。

  那么，理论上，一个方波，可以拆分成**无穷多个**正弦波的叠加。

  整个过程可以描述为：

  > $f(t)$ = 第一个正弦波 + 第二个正弦波 + ······ + 第n个正弦波 + ······

  用数学语言描述就是：
  
  $$
  \begin{equation}
  f(t)=B+\sum_{n=1}^{\infty} A_{n} \cos \left(n \Omega_{0} t+\varphi_{n}\right) \tag{1}
  \end{equation}
  $$
  

  这里的 $\Omega_{0}$ 并非变量，是一个常数，即“基频”。

  本例中，假设方波周期 $T$ ，则 $\Omega_{0}=2\pi/T$ ， $B$ 也是常数，它可以抬升或降低合成的曲线，使其整体处在正确的高度。

  那么，我们将

  **第一个、第二个、一直到第 $n$ 个**正弦波的**系数 $An$** 与**频率 $n\Omega_{0}$** 的对应关系，刻画在坐标轴上，就是“频谱”：

  ![92cec08f301ae922c0cb666aac311c29](https://gitee.com/hawkingwu/PicGo/raw/master/92cec08f301ae922c0cb666aac311c29.jpg)

  但是， $(1)$ 式看上去过于复杂，不够简洁，因此，我们采用欧拉公式：
  
  $$
  \begin{equation}
  e^{i \theta}=\cos \theta+i \cdot \sin \theta
  \end{equation}
  $$
  
  将**实正弦波**形式的 $(1)$ 式，转换成**复指数**形式的 $(2)$ 式（推导过程略）：
  
  $$
  \begin{equation}
  f(t)=\sum_{n=-\infty}^{\infty} \frac{1}{2} \cdot A_{n} \cdot e^{j \varphi_{n}} \cdot e^{j n \Omega_{0} t} \tag{2}
  \end{equation}
  $$
  
  这看起来整洁多了。

  但现在有一个根本问题：

  > 只有计算出 $An$ ，我们才能画频谱图呀！

  那么，如何具体计算系数 $An$ 呢？

  傅里叶说，**我有办法**。

  关于这段历史，请看专栏的视频节目**“如何理解傅里叶变换？从人文角度再看哲学家傅里叶”。**

  总之，历史再复杂，结论很简单。即，我们可以计算出 $(2)$ 式的系数：
  
  $$
  \begin{equation}
  \frac{1}{2} \cdot A_{n} \cdot e^{j \varphi_{n}}=\frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} f(t)\left[\cos \left(n \Omega_{0} t\right)-j \sin \left(n \Omega_{0} t\right)\right] dt \tag{3}
  \end{equation}
  $$
  
  我们将这个系数记作 $Fn$ ：
  
  $$
  \begin{equation}
  f(t)=\sum_{n=-\infty}^{\infty} F_{n} \cdot e^{j n \Omega_{0} t} \tag{4}
  \end{equation}
  $$
  
  显然，系数 $F_n$ 与原函数 $f(t)$ 有密切的关系， $(4)$ 式称为**傅里叶级数的复数形式，**它表示：

  > 任意周期信号，可以分解为许多**不同频率的复指数的加权和。**
  
  所谓不同频率，就是，随着 $n$ 的变化， $n \Omega_{0}$ 也逐渐变大，频率也因此逐渐变大。其中， $F_{n}$ 的模值 $\lvert\mathrm{Fn}\rvert$ ，就是**加权系数**（注意，此时积分上下限已经变成了 $\infty$ ）。

  

- ##### 为什么有负频率

  至此，傅里叶变换何会有负频率就很好理解了。

  因为，对于 $(4)$ 式所描述的**复数形式**，实际上是将信号拆解成**复指数的加权和，而不是实三角波的和。**

  被拆出来的某频率的一个**正的**复指数与一个**负的**复指数, 可以**合成出一个实三角波 ，**即：
  
  $$
  \begin{aligned}
  F_{n} e^{j n \Omega_{0} t}+F_{-n} e^{-j n \Omega_{0} t} &=\left|F_{n}\right|\left[e^{j\left(\varphi_{n}+n \Omega_{0} t\right)}+e^{-j\left(\varphi_{n}+n \Omega_{0} t\right)}\right] \\
  &=2\left|F_{n}\right| \cos \left(n \Omega_{0} t+\varphi_{n}\right)
  \end{aligned}
  $$
  
  这样一来，本质上，**我们其实还是在用正弦波表示原函数 $f(t)$ 。**

  因此，**单一出现的负频率本身没有物理意义，**同一频率 $n \Omega_{0}$ 下，正负频率总是共轭出现的，一正一负只是**正弦波的另一种数学表现形式。**
  
  那么，由于**傅里叶变换**也采用**复指数**形式，因此，理论上，**傅里叶变换的结果也有负频率。**
  
  好玩吧。

