---
layout:     post
title:      "超低噪声LDO在应用中的注意事项"
subtitle:   " ADI最新发布的LDO产品——LT3045，噪声低于锂电池！ "
date:       2020-12-07
author:     "huanqing"
header-img: "img/post-bg-LT3042.jpg"
mathjax: true
catalog: true
tags:
    - 电源
    - 模拟电路
---

# Industry’s First 0.8µVRMS Noise LDO Has 79dB Power Supply Rejection Ratio at 1MHz  业界首款0.8µVRMS噪声的LDO，具备1MHz处79dB的电源纹波抑制比

When it comes to powering noise-sensitive analog/RF applications, low dropout (LDO) linear regulators are generally preferred over their switching counterparts. Low noise LDOs power a wide range of analog/RF designs, including frequency synthesizers (PLLs/VCOs), RF mixers and modulators, high speed and high resolution data converters (ADCs and DACs) and precision sensors. Nevertheless, these applications have reached capabilities and sensitivities that are testing the limits of conventional low noise LDOs.

当说到给那些对噪声敏感的模拟 /RF 应用供电时，低压差（LDO）线性稳压器通常比功能相同的开关稳压器更受用户的青睐。低噪声 LDO 可为众多的模拟 /RF 设计供电，包括频率合成器（PLL / VCO）、RF 混频器和调制器、高速和高分辨率数据转换器 （ADC 和 DAC）以及高精度传感器。然而，这些应用对于功能和灵敏度的要求已经开始逐步考验着传统低噪声 LDO 的性能极限。

For instance, in many high end VCOs, power supply noise directly affects the VCO output phase noise (jitter). Moreover, to meet overall system efficiency requirements, the LDO usually post-regulates the output of a relatively noisy switching converter, so the high frequency power supply rejection ratio (PSRR) performance of the LDO becomes paramount. With its ultralow output noise and ultrahigh PSRR performance, the [LT3042](https://www.analog.com/en/products/lt3042.html) can directly power some of most noise-sensitive applications while post-regulating the output of a switching converter, without requiring bulky filtering. Table 1 compares the LT3042’s noise performance with conventional low noise regulators.

例如，在许多高端 VCO 中，电源噪声直接影响着 VCO 输出相位噪声（抖动）。而且，为了满足整体 系统效率要求，LDO 通常对噪声相对较大的开关转换器之输出进行后置稳压，因此 LDO 的高频电源抑制比（PSRR）性能变得至关重要。凭借其超低输出噪声和超高 PSRR 性能，[LT3042](https://www.analog.com/en/products/lt3042.html) 能够直接为某些对噪声最为敏感的应用供电，同时对开关转换器的输出实施后置稳压，并不需要庞大的滤波电路。表 1 比较了 LT3042 与传统低噪声稳压器的噪声性能。

**Table 1. The LT3042 vs traditional low noise LDOs**

| **Parameter** | **LT1763** | **LT3062** | **LT3082** | **LT3042** |
| ------| :---: | :----: | :----: | ------|
| RMS Noise (10Hz to 100kHz) | 20µVRMS | 30µVRMS | 33µVRMS | 0.8µVRMS |
| Spot Noise (10kHz) | 35nV/√Hz | 80nV/√Hz | 100nV/√Hz | 2nV/√Hz |
| PSRR at 1MHz | 22dB | 55dB | 45dB | 79dB |
| Minimum PSRR (DC to 1MHz) | 22dB | 30dB | 40dB | 77dB |
| Directly Parallelable | | | ✓ | ✓ |
| Programmable Current Limit | | | | ✓ |
| Programmable Power Good | | | | ✓ |
| Fast Start-up Capability | | | | ✓ |
| Rail-to-Rail Output Range | | | | ✓ |
| Quiescent Current | 30µA | 45µA | 300µA | 2mA |



**表1. LT3042 vs 传统低噪声LDO**

| **参数** | **LT1763** | **LT3062** | **LT3082** | **LT3042** |
| ------| :---: | :----: | :----: | :----:|
| RMS噪声 (10Hz ~ 100kHz) | 20µVRMS | 30µVRMS | 33µVRMS | 0.8µVRMS |
| 点噪声 (10kHz) | 35nV/√Hz | 80nV/√Hz | 100nV/√Hz | 2nV/√Hz |
| 1MHz 时的 PSRR | 22dB | 55dB | 45dB | 79dB |
| 最小 PSRR (DC ~ 1MHz) | 22dB | 30dB | 40dB | 77dB |
| 可直接并联 | | | ✓ | ✓ |
| 可编程限流 | | | | ✓ |
| 可编程电源良好 | | | | ✓ |
| 快速启动能力 | | | | ✓ |
| 轨到轨输出范围 | | | | ✓ |
| 静态电流 | 30µA | 45µA | 300µA | 2mA |



## 高性能、坚固性和简单性  Performance, Robustness & Simplicity

The LT3042 is a high performance low dropout linear regulator featuring Linear Technology’s ultralow noise and ultrahigh PSRR architecture for powering noise-sensitive applications. Even with its high performance, the LT3042 maintains simplicity and robustness. Figure 1 is a typical application and Figure 2 shows a complete demonstration circuit. The LT3042’s tiny 3mm × 3mm DFN package and minimal component requirements keep overall solution size small.

LT3042 是一款高性能低压差线性稳压器，其采用凌力尔特的超低噪声和超高 PSRR 架构以为对噪声敏感的应用供电。LT3042 尽管拥有高性能，但其同时也保持了简单性和坚固性。图 1 为该器件的一款典型应用电路，图 2 则示出一个完整的演示电路。 LT3042 的纤巧型 3mm x 3mm DFN 封装和极低的组 件要求可使整体解决方案尺寸保持小巧。

<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure1.PNG" alt="figure1" style="zoom: 67%;" />
<center> Figure 1. Typical LT3042 application. </center>

<img src="https://huanqingwu.coding.net/p/picgo/d/PicGo/git/raw/master/figure2.PNG" alt="figure2" style="zoom:50%;" />
<center> Figure 2. LT3042 demonstration circuit. </center>


Designed as a precision current reference followed by a high performance voltage buffer, the LT3042 is easily paralleled to increase output current, spread heat on the PCB and further reduce noise—output noise decreases by the square-root of the number of devices in parallel. Its current-reference based architecture offers wide output voltage range (0V to 15V) while maintaining unity-gain operation, thereby providing virtually constant output noise, PSRR, bandwidth and load regulation, independent of the programmed output voltage.


LT3042 被设计为一款后随高性能电压缓冲器的高精度电流基准，其可容易地通过并联以增加输出电流、在 PCB 上散播热量并进一步降低噪声，输出噪声的降幅为并联器件数目的平方根。该器件基于电流基准的架构可提供宽输出电压范围 （0V 至 15V）并保持单位增益运作，从而获得了几乎恒定的输出噪声、PSRR、带宽和负载调节，这与编程输出电压无关。


In addition to offering ultralow noise and ultrahigh PSRR performance, the LT3042 includes features desired in modern systems, such as programmable current limit, programmable power good threshold and fast start-up capability. Furthermore, the LT3042 incorporates protection features for battery-powered systems. Its reverse input protection circuitry tolerates negative voltages at the input without damaging the IC or developing negative voltages at the output—essentially acting as if an ideal diode is connected in series with the input. In battery backup systems where the output can be held higher than the input, the LT3042’s reverse output-to-input protection circuitry prevents reverse current flow to the input supply. The LT3042 includes internal foldback current limit, as well as thermal limit with hysteresis for safe-operating-area protection.


除了提供超低噪声和超高 PSRR 性能之外， LT3042 还拥有新式系统中期望的特性，例如：可编程电流限值、可编程电源良好门限和快速启动能力。 此外，LT3042 还内置了针对电池供电型系统的保护功能。其反向输入保护电路可耐受输入端上的负电压，并不会损坏 IC 或在输出端上产生负电压，作用基本上就像连接了一个与输入相串联的理想二极管。在那些可以使输出高于输入的电池后备系统中， LT3042 的反向输出至输入保护电路可避免反向电流流至输入电源。LT3042 包括内部折返电流限制以及具迟滞的热限制功能，可用于提供安全工作区保护。



## 超低输出噪声  Ultralow Output Noise

With its 0.8µVRMS output noise* in 10Hz to 100kHz bandwidth, the LT3042 is the industry’s first sub-1µVRMS noise regulator. Figure 3 compares the LT3042’s integrated output noise from 10Hz to 100kHz to that of the LT1763, Linear’s lowest noise regulator for over a decade. The LT3042’s ultralow noise performance opens up applications that were previously not possible, or otherwise required expensive and bulky filtering components.


凭借其 0.8μVRMS 的输出噪声*（在 10Hz 至 100kHz 带宽内），LT3042 成为了业界首款噪声低于1μVRMS 的稳压器 。 图 3 把 LT3042 在 10Hz 至 100kHz 范围内的积分输出噪声与 LT1763（其为凌力尔特 10 多年来噪声最低的一款稳压器）的相应指标做了对比。LT3042 的超低噪声性能可开辟以往无法实现的应用，或者需要采用昂贵笨重的滤波组件才能实现的应用。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure3.PNG" alt="figure3" style="zoom:50%;" />
<center>Figure 3. Output noise: 10Hz to 100kHz. </center>


The SET pin capacitor (CSET) bypasses the reference current noise, the base current noise (of the error amplifier’s input stage) and the SET pin resistor’s (RSET) inherent thermal noise. As shown in Figure 4, low frequency noise performance is significantly improved with increasing CSET. With a 22µF CSET, the output noise is under 20nV/√Hz at 10Hz. Note that capacitors can also produce 1/f noise, particularly electrolytic capacitors. To minimize 1/f noise, use ceramic, tantalum or film capacitors on the SET pin.


SET 引脚电容器（CSET）负责对基准电流噪声、（误差放大器输入级）的基极电流噪声以及 SET 引脚电阻器（RSET）的固有热噪声进行旁路。如图 4 所示，通过增加 CSET 可显着地改善低频噪声性能。当采用一个 22μF CSET 时，输出噪声在 10Hz 时低于 20nV/√Hz。需要注意的是，电容器还会产生 1/f 噪声，特别是电解电容器。为了尽量降低 1/f 噪声，应在 SET 引脚上采用陶瓷电容器、钽电容器或薄膜电 容器。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure4.PNG" alt="figure4" style="zoom:50%;" />
<center>Figure 4. Noise spectral density. </center>


Actively driving the SET pin with either a battery or a lower noise voltage reference reduces noise below 10Hz. Doing so essentially eliminates the reference current noise at lower frequencies, leaving only the extremely low error amplifier noise. This ability to drive the SET pin is another advantage of the current-reference architecture. The integrated RMS noise also improves as the SET pin capacitance increases, dropping below 1µVRMS with just 2.2µF CSET, as shown in Figure 5.


利用一个电池或一个较低噪声的电压基准对 SET 引脚主动地进行驱动可减少噪声低于 10Hz。这么做基本上可以消除较低频率上的基准电流噪声，仅剩下极低的误差放大器噪声。这种驱动 SET 引脚的能力是电流基准架构的另一项优势。此外，积分 RMS 噪声还会随着 SET 引脚电容的增大而得到改善，在只采用 2.2μF CSET 的情况下可降至 1μVRMS 以下，如图 5 所示。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure5.PNG" alt="figure5" style="zoom:50%;" />
<center>Figure 5. Integrated RMS output noise (10Hz to 100kHz). </center>


Increasing SET pin bypass capacitance for lower output noise generally leads to increased start-up time. But the LT3042’s fast start-up circuitry alleviates this trade-off. The fast start-up circuitry is easily configured using two resistors; Figure 6 shows the significant improvement in start-up time.


通过增大 SET 引脚旁路电容以降低输出噪声 通常会导致启动时间的增加。但是，LT3042 的快速 启动电路则使此项折衷的难度有所降低。该快速启 动电路可容易地利用两个电阻器来配置；图 6 示出 了启动时间的显着改善。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure6.PNG" alt="figure6" style="zoom:50%;" />
<center>Figure 6. Fast start-up capability. </center>



## 超高 PSRR 性能  Ultrahigh PSRR Performance

LT3042’s high PSRR* is important when powering noise-sensitive applications. Figure 7 shows the LT3042’s incredible low and high frequency PSRR performance—approaching almost 120dB at 120Hz, 79dB at 1MHz, and better than 70dB all the way to 3MHz. PSRR performance is even better with decreasing load currents, as shown in Figure 8.


当给对噪声敏感的应用供电时，LT3042 的高 PSRR 是很重要。图 7 示出了 LT3042 令人难以置信的低频和高频 PSRR 性能，几乎接近 120dB （在120Hz）、79dB（在 1MHz）和优于 70dB（一直到 3MHz）。当负载电流减小时，PSRR 性能则更好，如 图 8 所示。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure7.PNG" alt="figure7" style="zoom:50%;" />
<center>Figure 7. PSRR performance. </center>

<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure8.PNG" style="zoom:50%;" />
<center>Figure 8. PSRR for various load currents. </center>


Unlike conventional LDOs whose PSRR performance deteriorates into the 10s of dB as you approach dropout, the LT3042 maintains high PSRR at even low input-to-output differentials. As Figure 9 illustrates, LT3042 maintains 70dB PSRR up to 2MHz with only 1V input-to-output differential and almost 60dB PSRR up to 2MHz at a mere 600mV input-to-output differential. This capability allows the LT3042 to post-regulate switching converters at low input-to-output differentials—for high efficiency—while its PSRR performance satisfies the requirements of noise-sensitive applications.


当接近压差状态时，传统 LDO 的 PSRR 性能会下降至几十 dB，LT3042 则与之不同，即使在低输入至输出差分电压条件下其亦可保持高 PSRR。如图 9 所示，LT3042 能在高达 2MHz 频率和仅 1V 输入至输出差分电压条件下保持 70dB PSRR，并在高达 2MHz 频率和仅 600mV 输入至输出差分电压条件下 保持几乎 60dB PSRR。这种能力允许 LT3042 在低输入至输出差分电压下对开关转换器进行后置稳压 （以实现高效率），而其 PSRR 性能则满足了对噪声敏感之应用的要求。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure9.PNG" alt="figure9" style="zoom:50%;" />
<center>Figure 9. PSRR vs input-to-output differential. </center>



## 对开关电源实施后置稳压  Post-Regulating A Switcher

In applications where the LT3042 is post-regulating the output of a switching converter to achieve ultrahigh PSRR at high frequencies, care must be taken with the electromagnetic coupling from the switching converter to the output of the LT3042. In particular, while the “hotloop” of the switching converter should be as small as possible, the “warm-loop” (with AC currents flowing at the switching frequency) formed by the switcher IC, output inductor, and output capacitor (for a buck converter) should also be minimized, and it should either be shielded or placed a couple of inches away from ultralow noise devices like the LT3042 and its load. While the LT3042’s orientation with respect to the “warm-loop” can be optimized for minimum magnetic coupling, it can be challenging in practice to achieve 80dB of rejection simply with optimized orientation—multiple iterations of the PC board may be required.


在那些采用 LT3042 对开关转换器的输出进行后置稳压以在高频条件下实现超高 PSRR 的应用中，必须谨慎地对待从开关转换器至 LT3042 输出的电磁耦合。特别地，不仅开关转换器的“热环路” （hot-loop）应尽可能地小，由开关电源 IC、输出电感器和输出电容器（用于一个降压型转换器）形成的“暖环路”（warm-loop）（AC 电流在高开关频率下流动）也应该尽量地缩小，而且应对其进行屏蔽或将其布设在距离超低噪声器件（比如：LT3042 及其负载）几英寸的地方。虽然 LT3042 相对于“暖环路”的取向可为实现最小的磁耦合而优化，但在现实中仅仅利用优化的取向来实现 80dB 抑制会十分困难，有可能需要进行 PC 板的多次迭代。


Consider Figure 10, where the LT3042 is post-regulating the LT8614 Silent Switcher® regulator running at 500kHz with an EMI filter at switching regulator input. With the LT3042 located just one to two inches from the switching converter and its external components, almost 80dB rejection at 500kHz is achieved without any shielding.


我们来研究一下图 10，在该图所示的电路中， LT3042 负责对以 500kHz 频率运行的 LT8614 进行后置稳压，并在开关稳压器输入端上布设了一个EMI 滤波器。由于 LT3042 被布设在距离开关转换器及其外部组件仅 1～2 英寸的地方，因此不需要采取任何屏蔽措施就能在 500kHz 频率下实现接近 80dB 的抑制。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure10.PNG" alt="figure10" style="zoom:80%;" />
<center>Figure 10. The LT3042 post-regulating LT8614 Silent Switcher regulator. </center>


To achieve this performance, however, as Figure 11a highlights, no additional capacitor—other than the 22µF at switcher’s output—is placed at the input of the LT3042. However, as shown in Figure 11b, even placing a small 4.7µF capacitor directly at the input of the LT3042 results in over 10× degradation in PSRR.


然而，如图 11a 突出显示的那样，为了实现该性能，在 LT3042 的输入端上并未布设附加的电容器 （除了开关电源输出端上的 22μF 电容器之外）。 不过，如图 11b 所示，即使直接在 LT3042 的输入端上布设一个 4.7μF 的小电容器，也将导致 PSRR 性能下降 10 倍以上。


<img src="https://gitee.com/hawkingwu/PicGo/raw/master/figure11.PNG" alt="figure11" style="zoom: 80%;" />
<center>Figure 11. The LT3042 post-regulating the LT8614 Silent Switcher (a) without any capacitor at the LT3042 input, (b) with a 4.7µF capacitor at LT3042 input. </center>


This is peculiarly counter-intuitive—adding input capacitance *generally reduces* output ripple—but at 80dB rejection, the magnetic coupling, which is usually insignificant, resulting from moderately high frequency (500kHz) switching currents flowing though this 4.7µF capacitor, significantly degrades output ripple. While changing the orientation of the 4.7µF input capacitor and the traces connecting the switcher’s output to this capacitor help minimize magnetic coupling, it remains rather difficult to achieve nearly 80dB of rejection at these frequencies, not to mention the multiple PC board iterations it may require.


这一点特别有悖于人们的直觉——增设输入电容一般是可以减小输出纹波的——但是在 80dB 抑制水平下，由流过该 4.7μF 电容器的较高 频 （500kHz）开关电流所引起的磁耦合（常常是无关紧要的）却会使输出纹波性能显着变差。尽管改变该 4.7μF 输入电容器以及把开关电源的输出连接至该电容器之走线的取向有助最大限度地减少磁耦合，但是要在这些频率条件下实现接近 80dB 的抑制依然是相当困难的，更不用说它可能还需要进行多次 PC 板迭代。


The relatively high input impedance of the LT3042 prevents high frequency AC currents from flowing to its input terminal. Given that the LT3042 is stable without an input capacitor if located within three inches of the pre-regulating switching power supply’s output capacitor, to achieve best PSRR performance, we recommend not placing a capacitor at the LT3042’s input, or minimizing it.


LT3042 相对较高的输入阻抗可避免高频 AC 电流流至其输入端。如果 LT3042 布设在与前置稳压开关电源的输出电容器相距 3 英寸以内的地方， 则其可在未使用输入电容器的情况下保持稳定，考虑到这一点，为了实现最佳的 PSRR 性能，我们建议不要在 LT3042 的输入端上安放一个电容器，或者尽量减小该电容器的数值。


A couple of inches of trace inductance connecting the LT8614 to the LT3042 input significantly attenuates the very high frequency power switch transition spikes. Some spikes still propagate to the output due to magnetic coupling from the LT8614’s “hot-loop.” Optimizing the LT3042 board orientation reduces the remaining spikes. Due to instrumentation bandwidth limitation, these very high frequency spikes are not shown in Figure 11’s output ripple.


把 LT8614 连接至 LT3042 输入的几英寸走线之电感可显着地衰减非常高频率的电源开关瞬态尖峰。由于来自 LT8614“热环路”之磁耦合的原因， 有些尖峰仍将传播至输出。优化 LT3042 电路板取向可减小剩余的尖峰。由于仪表带宽的限制，这些非常高频率的尖峰未在图 11 的输出纹波中示出。


For perspective, trying to achieve 80dB rejection at 500kHz *without* using the ultrahigh PSRR LT3042 LDO is a tall order. Alternatives don’t measure up. For instance, an LC filter would require nearly 40µH of inductance and 40µF of capacitance to achieve 80dB rejection at 500kHz, adding large, expensive components. Costs and board real estate aside, the LC can resonate if not properly damped, adding complexity. Using an RC filter is untenable, requiring impractical resistance to achieve 80dB rejection. Similarly, using conventional LDOs require cascading at least two of them to achieve 80dB rejection at 500kHz, which requires additional components and cost, and degrades the dropout voltage.


从中可以看出，如果不采用具超高 PSRR 的 LT3042 LDO，那么想在 500kHz 频率下实现 80dB 抑制是一项难以完成的任务。其他替代产品无法胜任。 例如：在 500kHz 下，一个 LC 滤波器将需要接近 40μH 电感和 40μF 电容才能实现 80dB 的抑制， 因而不得不增设庞大、昂贵的组件。撇开成本和电路板空间不谈，如果未进行正确的阻尼，LC 也会发生共振，从而导致复杂性增加。采用一个 RC 滤波器的想法是站不住脚的，因为实现 80dB 抑制所需的电阻是不切实际的。同样，采用传统 LDO 时需要级联至少两个 LDO 才能在 500kHz 频率下实现 80dB 抑制，这就必需增加组件和成本，并降低压差电压性能。


Additionally, to achieve 80dB rejection, these alternatives also require attention to magnetic field couplings. In particular, high frequency AC currents must be minimized.


此外，为了实现 80dB 抑制，这些替代方案还需要关注磁场耦合。特别地，必须最大限度地减小高频 AC 电流。


Owing to its ultrahigh PSRR over a wide frequency range, the LT3042 allows lower frequency operation of the upstream switching converter—for improved efficiency and EMI—without requiring any increase in filter component size for powering noise-sensitive applications.


LT3042 在一个很宽的频率范围内拥有超高的 PSRR，因此可实现上游开关转换器的较低频运作（以改善效率和 EMI），而且在为那些对噪声敏感的应用供电时完全不需要增加滤波器组件尺寸。



## 结论  Conclusion

The LT3042’s breakthrough noise and PSRR performance, coupled with its robustness and ease-of-use, make it ideal for powering noise-sensitive applications. With its current-reference based architecture, noise and PSRR performance remain independent of the output voltage. Additionally, multiple LT3042s can be directly paralleled to further reduce output noise, increase output current and spread heat on the PCB.


LT3042 突破性的噪声和 PSRR 性能，再加上其坚固性和易用性，使之非常适合为噪声敏感型应用供电。凭借其基于电流基准的架构，噪声和 PSRR 性能不会受到输出电压的影响。此外，还可以把多个 LT3042 直接并联起来，以进一步降低输出噪声、增加输出电流和在 PCB 上散播热量。
