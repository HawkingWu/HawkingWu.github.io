---
title: "PCB的发展历史"
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
印刷电路板(PCB)是由相互连接的电子元件组成的独立模块，从我们身边日常使用的电子设备，如：手机、路由器、个人电脑到复杂的雷达、导弹、卫星上，都能找到它们的身影，只是它们靓丽的光芒被设备外壳给遮盖住了，你那天才般的设计往往被用户所忽视，直到设备出现故障或者需要功能扩展，拆开设备外壳的刹那才能领略它的美。

### PCB史前时代

电子学的起源可以追溯到1897年，**约瑟夫·汤姆森发现电子的存在**，电子学是在早期的电磁学和电工学的基础上发展起来的。在电子学诞生之前，人类对于电磁现象的研究已相当深入。一系列物理定律已经确立，如**库仑定律**、**安培定律**、 **欧姆定律**、 **楞次定律**、**法拉第电磁感应定律**等。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/James_Clerk_Maxwell.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/James_Clerk_Maxwell.jpg)

1831年6月13日，天降男神**詹姆斯·克拉克·麦克斯韦**（James Clerk Maxwell，1831年6月13日－1879年11月5日）于英国爱丁堡的印度街14号，麦克斯韦被普遍认为是十九世纪物理学家中，对于二十世纪初物理学的巨大进展影响最为巨大的一位。他在1864年发表的论文**《电磁场的动力学理论》**中，集以往电磁学研究之大成，提出电场和磁场以波的形式以光速在空间中传播，并提出光是引起同种介质中电场和磁场中许多现象的电磁扰动，同时从理论上预测了电磁波的存在，将电、磁、光统归为电磁场中现象，提出了著名的麦克斯韦方程组，建立了第一个完整的电磁学理论体系，为电磁学在生产生活中应用奠定了强大的理论基础。

电磁学是现代科技生活最重要的学科，它的高速发展，将人类带入了电气时代和信息时代。可以说，**没有电磁学的发展，就没有人类的现代文明**；这一自然科学理论的成果，奠定了现代的电力工业、电子工业和无线电工业的基础。

有了电磁学理论的支撑，人们便开始利用电磁学的理论服务于人类的生产活动，进而引发了第二次产业革命和第三次产业革命。

1831年法拉第发表了**《法拉第电磁感应定律》**，在发现了电磁感定律之后，1831年法拉第发明了圆盘发电机，这是人类创造出的第一个发电机。电磁感定律的发现也促进了电报通信应用的发展。

1839年，首条真正投入使用营运的电报线路于1839年在英国最先出现。它是大西方铁路装设在两个车站之间作通讯之用。这条线路长13英里，属指针式设计，由查尔斯·惠斯通及威廉·库克发明。两人并为发明在1837年取得英国的专利。

在美国，**萨缪尔·摩尔斯**在接近同一时间同时发明了电报，并在1837年在美国取得专利。摩尔斯还发展出一套将字母及数字编码以便拍发的方法，称为**摩斯电码**。

**最早期的电线属于单线式，需要透过地面完成回路，传送距离有限**。这里老wu马克一下，这个**地回路**的影响老wu在专栏后边的【PCB上没有地】章节里还会提到 🙂。

到了1850年，首条海底电缆横越英吉利海峡，把英国及欧洲大陆连接起来。首条横越大西洋的电报电缆则在1857年敷设完毕。但由于技术原因，这条越洋电缆只使用了数天便告失灵。**这里老wu再次马克一下**，这个越洋电缆为什么失败，老wu在专栏后边的**【阻抗和传输线】**的相关章节里还会提到 🙂。

最早的电报需要手工拍发，熟练的电报员使用摩斯码大约能每秒钟传送一个字母，随着电报业务的发展，这就需要大量的电报员，而且当时电报员的待遇都很不错的说，至少相当于现在互联网开发的待遇吧 😄 你还别说，这可以算得上是第一批码农了吧，不同的是我们敲C Code而他们敲摩斯码 😂。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/拍电报的小姐姐.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/拍电报的小姐姐.jpg)

老wu查了下资料，1879年（光绪5年）当时的大清就开始架设有电报线路，晚清时期，电报局的报务人员都由电报学堂的学生组成，每月可以拿到30两银子的薪水，这在当时算是一个比较吃香的工作了。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/电报密码.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2021/01/电报密码.jpg)

大概与现在很多同学入坑互联网开发一样，“码农”电报员也成了当时年轻人就业的一个热门方向，像托马斯-爱迪生，奥利弗·亥维赛可都当个初代码农的哈。

这里还要感谢一下**奥利弗·亥维赛**所做的贡献，也正是由于电报员的经历和针对电报学中的一系列问题的研究，提出了电报员方程，利用所发明的矢量微积分符号，将原来用繁杂的四元数描述的麦克斯韦方程组精简至4个，并明确给出麦克斯韦方程组的正式公式表述（麦克斯韦本人并没有明确地写出所有方程的数学形式，后来将此方程组写出的人还有海因里希·赫兹）。这项成就大举简化了这一19世纪最为重要的科学成就，使它更容易被学习者们掌握。

亚历山大-格雷厄姆-贝尔在1876年发明了电话，托马斯-爱迪生1879年发明了白炽灯、尼古拉-特斯拉于1888年发明了电动机，所有这些，**都为电子学的诞生准备了充足的条件。**

1883年，爱迪生在致力于延长碳丝白炽灯的寿命时，意外地发现了在灯丝与加有正电压的电极间有电流流过，电极为负时则无电流，这就是**爱迪生效应**。这一发现导致了后来电子管的发明。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/爱迪生发明灯泡.jpeg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/爱迪生发明灯泡.jpeg)

1887年，德国H.R.赫兹进行了一项实验，他用火花隙激励一个环状天线，用另一个带缝隙的环状天线接收，**证实了麦克斯韦关于电磁波存在的预言**，这一重要的实验导致了后来**无线电报的发明**。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/赫兹电磁波实验.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/赫兹电磁波实验.jpg)

无线电报的发明，是人类利用电磁波的第一个巨大成就，电子学从此开始了一个研究和利用电磁波的极其兴旺的时期。

1897年德国科学家布朗（Braun）制造出第一个真空管（vacuum tube），之后电子学的真空管时期就此展开。基本上，布朗的真空管只是一个阴极射线管（Cathode Ray Tube）的雏型，功能并不大。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/布朗制造出第一个真空管-2.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/布朗制造出第一个真空管-2.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/布朗制造出第一个真空管-1.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/布朗制造出第一个真空管-1.jpg)

1904年，英国的弗莱明（John Fleming）发明了真空二极管（diode，当时也称作valve），是由一放射电子的加热灯丝与接收电子的屏极所组成；当屏极加入正电压便会产生电流，加入负电压便没有电流产生。



[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/约翰·安布罗斯·弗莱明发明二极管.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/约翰·安布罗斯·弗莱明发明二极管.jpg)

到了1906年，德佛雷斯特（De Forest）在二极真空管内加入栅极，发明了三极真空管（audion，或称triode），可以控制电子的活动，使其具有放大信号与控制电量的强大功能，从而使得电子电路技术进入了实际应用阶段，同时也推动了无线电及其他电子行业的发展，这之后的20年中，各种电子设备不断涌现出来，德佛雷斯特也被誉为无线电之父”、“电视始祖”、“电子管之父”。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/德佛雷斯特发明三极真空管.jpeg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/德佛雷斯特发明三极真空管.jpeg)

电子管是电子器件的第一代，在晶体管发明以前的近半个世纪里，电子管几乎是各种电子设备中唯一可用的电子器件。电子学随后取得的许多成就，如电视、雷达、计算机的发明，都是和电子管分不开的。就是在固体电子学十分兴旺的现代，以大功率电子管（特别是微波功率电子管）和电子束管为代表的真空电子学也仍然是一个活跃的领域。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ibm-电子管计算机模块.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ibm-电子管计算机模块.jpg)

通过上边的图片我们看到，在PCB技术没有大规模应用之前，生产这样一台电子设备是多么的麻烦而低效，大量的电子管，需要使用涂有绝缘树脂的导线在器件之间进行人工布线并焊接，这就带来一些问题：

- 人工接线效率低，没办法实现机器化大规模生产
- 人工接线容易出现安装错误，检查困难
- 端子的焊接可靠性低容易松动造成接触不良

当时的电路体积大而又非常笨重，同时还很脆弱。生产是劳动密集型的，这导致高额的间接成本转嫁到买方身上。为了简化电子机器的制作，减少电子零件间的配线，降低制作成本、提高电子机器的可靠性，人们开始钻研以印刷的方式取代配线的方法，以利用机器实现精密的大规模化生产。

### 印刷电路板的诞生与发展

1831年法拉第发表电磁感应定律之后，人们就开始研究如何利用电磁原理来实现远距离通信，萨缪尔·摩尔斯1837年发明了电报，贝尔于1876获得了电话的发明专利。到了1904年美国有300万电话需要靠人工电话交换连接。

印刷电路板也是随着电子连接系统发展而来的，以解决电报/电话系统的连接问题。初期，金属条或金属棒用于连接安装在木制底座上的大型电子元件。随着时间的推移，金属条被螺丝端子和可拧入其中的电缆所取代，这样连接更具有灵活性，而木制底座则被金属底板所取代。但是，随着电报/电话业务的发展，电话交换门数越来有多，电话系统相关的电子操作也越来越复杂，这就需要更小、更紧凑的设计。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/图为1907年的汉口路14号英商华洋德律风公司的人工电话交换所.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/图为1907年的汉口路14号英商华洋德律风公司的人工电话交换所.jpg)

### 印刷电路板的摇篮期

与PCB有关的发明专利最早的时间节点应该在1903年，当时一位名叫**阿尔伯特·汉森（Albert Hanson）**的德国著名发明家申请了一项英国专利，他首创利用“线路”的观念应用于电话交换机系统，利用金属箔切割成线路导体，然后线路导体上下面都粘上石蜡纸，在线路交点上设置导通孔实现不同层间的电气互联。这与我们现代的PCB制造方法有明显的区别，因为当时苯酚树脂还未发明，而化学蚀刻技术也还未成熟，阿尔伯特·汉森发明的方法可以说是现代PCB制造的雏形吧。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/该图描绘了Albert-Hanson获得的第一项PCB专利-2.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/该图描绘了Albert-Hanson获得的第一项PCB专利-2.png)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/该图描绘了Albert-Hanson获得的第一项PCB专利.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/该图描绘了Albert-Hanson获得的第一项PCB专利.png)

1907年，出生于比利时的美国化学家利奥·亨德里克·贝克兰（Leo Hendrik Baekeland，1863年－1944年）改进了酚醛树脂的生产技术，将树脂实用化、工业化。这也为印制电路板的问世与发展，创造了必要的条件。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Baekeland-Leo-Hendrik5.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Baekeland-Leo-Hendrik5.jpg)

1920年代–早期的PCB板材几乎无所不包，从电木（就是上边说的酚醛树脂，俗称电木）和松石到普通的旧薄木板。 可以在材料上钻一些孔，然后将扁铜丝铆接到该材料上。 外形看起来可能不是很美观，但是后来的印刷电路板的理念就从这里诞生。 当时，这些电路板主要用于收音机和留声机。

### 印刷电路板的发明

还记得上边提到的赫兹吗，1887年赫兹通过实验证实了麦克斯韦关于电磁波的预测之后，到了1920年代，无线电已经引起了全世界的关注，而且电子管技术已经相当成熟，成熟到可以开始无线电广播的程度了，广播收音机将很快被引入到每个家庭，如何快速制造收音机，也在促进着印刷电路板相关技术的演进。

1925年，美国的 Charles Ducas 在绝缘的基板上印刷出线路图案，再以电镀的方式，成功建立导体作配线。这时，“PCB”这个名词就诞生了。这种方法使得制造电器变得容易。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Ducas-Charles-PCB-发明专利-2.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Ducas-Charles-PCB-发明专利-2.jpg)[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Ducas-Charles-PCB-发明专利-1.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Ducas-Charles-PCB-发明专利-1.jpg)

1936年，奥地利人Paul Eisler博士在英国发表箔膜技术，他在一个收音机装置内采用了印刷电路板；也是在1936年，日本的宫本喜之助以喷附配线法成功申请专利。而两者中 Paul Eisler 的方法与现今的印刷电路板最为相似，这类做法称为减去法，是把不需要的金属除去；而 Charles Ducas、宫本喜之助的做法是只加上所需的配线，称为加成法。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/my-life-with-the-printed-circuit.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/my-life-with-the-printed-circuit.jpg)

**Paul Eisler 也被称为“印刷电路之父”，**但因为当时的电子管元件发热量大，体积笨重，不方便在印刷电路板上进行安装，Paul Eisler 的这一重大发明当时并未被英国所注重，而在美国也只是将PCB制造技术应用于军工产品之中。

到了1942年,Paul Eisler博士继续改进他的PCB生产方法，发明了世界最早实用化的双面PCB,并在Pye公司正式生产。该专利申请于1943年获准。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Radio-with-first-Printed-Circuit-Board-by-Paul-Eisler-1942.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Radio-with-first-Printed-Circuit-Board-by-Paul-Eisler-1942.jpg)[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/QQ截图20200627114449.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/QQ截图20200627114449.png)

大约在1943年，美国开始大规模使用Paul Eisler的这项技术发明来制造近炸引信，用于第二次世界大战，使用印刷电路作为炸弹上的近炸引信，以便在接近预定目标时做为炸弹的爆炸计时装置。同时还将该技术大量使用于军用收音机内。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/MK53_fuze.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/MK53_fuze.jpg)

1947年，环氧树脂开始用作制造基板。同时NBS开始研究以印刷电路技术形成线圈、电容器、电阻器等制造技术。

1948年，美国正式认可印刷电路板发明用于商业用途。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Motorola-Model-VT-73-VT-71.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Motorola-Model-VT-73-VT-71.jpg)

但是，1950年代，采用PCB的电子设备还很少。比如上图这台1948年的摩托罗拉生产的电视，依然没有出现PCB。好家伙，密密麻麻的全是电子管，这当时要是维修这机器肯定是一脸懵逼。如果你现在拥有一台还能工作的摩托罗拉的电子管电视，那得值多少钱呢？1948能用得起电视的可都是有钱人。

### 印刷电路板的春天

从1950年代到1990年代。这是PCB产业形成并快速成长的阶段，即PCB产业化的早期阶段，此时PCB已经成为一个产业。

1948年后，美国正式认可了PCB这个发明用于商业用途，这也意味着PCB从军事领域用途开始大规模商用的步伐。

随着电子技术的发展，到了1947年12月，美国贝尔实验室的肖克利、巴丁和布拉顿组成的研究小组研发出了晶体管，发热量较低体积更小巧的晶体管从50年代开始大量取代电子管的地位，这也为印刷电路板技术的广泛使用创造了条件。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/诞生于贝尔实验室的第一个晶体管.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/诞生于贝尔实验室的第一个晶体管.jpg)

1950年，日本公司尝试在玻璃基板上涂银作为导体，在酚醛树脂纸基板上使用铜箔作为导体。从1950年开始，印刷电路的制造技术开始被广泛接受，这时蚀刻起到了主导作用。伴随着晶体管开始走向实用化，以金属箔腐蚀法制成的单面PCB在美国开发成功,并很快地得到工业化应用。

1951年，聚酰亚胺材料诞生。

1953年，Motorola开发出电镀过孔法的双面板。大约在1955年，日本的东芝公司推出了一种在铜箔表面生成氧化铜的技术，并出现了覆铜板（CCL）。这两种技术后来都被广泛用于多层印刷电路板的制造，它们对多层印刷电路板的出现起到了推波助澜的作用。此后，多层PCB得到了广泛的应用。

印刷电路板广泛被使用10年后的1960年代，PCB技术也日益成熟。而自从Motorola的双面板问世，多层印刷电路板开始出现，使配线与基板面积之比更为提高。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/1920px-Dec_SYSTEM_BUILDING_BLOCKS_1103.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/1920px-Dec_SYSTEM_BUILDING_BLOCKS_1103.jpg)

图为DEC 公司在1950年代推出的”Digital Laboratory Module”

### 印刷电路板已经必不可少

1958年：仙童公司Robert Noyce与德仪公司基尔比间隔数月分别发明了集成电路，开创了世界微电子学的历史；

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Jack-Kilby-is-holding-the-first-integrated-circuit.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Jack-Kilby-is-holding-the-first-integrated-circuit.jpg)

1960年代，多层(4+层数)PCB开始生产。而电镀贯穿孔金属化双面PCB实现了大规模生产。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/1960年代PCB.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/1960年代PCB.jpg)

1964年：Intel摩尔提出摩尔定律，预测晶体管集成度将会每18个月增加1倍

1971年：Intel推出1kb动态随机存储器（DRAM），标志着大规模集成电路出现

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Intel-C1103-DRAM.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/Intel-C1103-DRAM.png)

1971年：全球第一个微处理器4004由Intel公司推出，采用的是MOS工艺，这是一个里程碑式的发明。

**随着集成电路的大规模应用，这时如果电子产品的生产不使用印刷电路板的话，那生产会带来大麻烦。**

1970年代，多层PCB迅速发展，并不断向高精度、高密度、细线小孔、高可靠性、低成本和自动化连续生产方向发展，以适应摩尔定律的步伐。

虽然1970年代开始多层PCB就开始迅速发展，但当时的PCB设计工作还是靠人工完成的。

**苦逼的PCB设计人员**

在1950-1970年代设计一个电路板需要掌握多种技能，包括绘图、制造和电子理论的知识。PCB设计人员的角色是处于在电气工程师和PCB制造商之间充当中介的角色

当时的PCB Layout工程师，拿着彩色铅笔和直尺，在透明的聚酯薄膜胶片上绘制电路，为了提高绘图效率，会有一些常见器件的封装模板和电路模板。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-3.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-3.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-2.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-2.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-4.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-4.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-5.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-5.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-6.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-6.jpg)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-7.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/手工绘制PCB-7.jpg)

1980年代，表面安装技术开始逐渐替代通孔安装技术成为主流，也开始进入到了数字时代，随着例如个人计算机，光盘，相机，游戏机，随身听等电子设备的发展，使我们在媒体消费方式方面发生了巨大变化。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/cw_evolution_of_the_macintosh_02-100771325-large.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/cw_evolution_of_the_macintosh_02-100771325-large.jpg)

微软在1981年发布了MS-DOS1.0系统、1984年乔布斯的苹果公司发布了Macintosh 麦金塔电脑（现多被简称为Mac），1984联想成立，开始组装个人计算机，个人计算机开始普及，基于DOS的CAD 软件开始出现并快速发展。

CAD软件的出现，提高了设计人员的绘图效率，同时也提高了PCB设计的复用率，节约的重复设计时间，PCB设计完成后，直接导出Gerber文件输入到光绘设备中，同时,PCB的制造也开始大量还用了机械替代了人工，PCB生产效率的提高，之前需要几周才能交付的PCB现在最快几个小时就能交付，这时快板厂开始出现。

### 1990年代至今，PCB产业开始走向成熟

1993年，摩托罗拉的Paul T. Lin申请了一种称为BGA（球栅阵列）封装的专利，这标志着有机封装基板的开始。

1995年，松下公司开发出ALIVH（任意层间通孔）结构的BUM PCB制造技术。这也标致着PCB开始进入HDI高密度互联时代。

在2000年初期，PCB变得更小、更复杂。5-6密耳线宽/线距已经是常规工艺，对于高端PCB板厂来说，开始制造3.5-4.5 mil 线宽/线距的电路板。

同时，柔性PCB变得更加普遍。

2006年，每层互连（ELIC）工艺被开发出来。该工艺使用堆叠的铜填充微孔，通过电路板的每一层进行连接。这种独特的工艺使开发人员能够在PCB中的任何两层之间建立起堆叠后的连接。虽然这种工艺提高了灵活性水平，使设计人员能够最大限度地提高互连密度，但直到2010年代，ELIC PCB才被广泛使用。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ELICCrossSection_0.png)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ELICCrossSection_0.png)

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ELIC-任意层互联技术.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/ELIC-任意层互联技术.jpg)

### 随着智能手机的发展，驱动着HDI PCB技术的发展

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/智能手机的演变.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/智能手机的演变.jpg)

随着智能手机的发展，21世纪初，第二代HDI应运而生。在保留激光钻微通孔的同时，堆叠的通孔开始取代交错的导通孔，并结合“任意层”构建技术，HDI板最终的线宽/线距达到了40μm。

这种任意层的方法仍然基于减成法工艺，而且可以肯定的是，对于移动电子产品来说，大多数高端HDI仍然采用这种技术。然而，在2017年，HDI开始迈入新的发展阶段，开始从减成法工艺转向基于图形电镀的工艺。

例如，在0.3毫米间距的BGA设计中，BGA焊盘之间要过两条走线，通孔尺寸通常为75微米，焊盘尺寸为150微米。布局设计需要30 µm/30 µm的线宽/线距。用现有的减法工艺来实现这种细线结构是很有挑战性的。蚀刻能力是关键因素之一，其中成品铜厚和电镀均匀性需要与成像工艺一起优化。这也是为什么PCB行业现在采用mSAP工艺的原因，与减法工艺相比，mSAP工艺可以很容易地生产出具有优化导体形状的线路，在整个PCB面板上，PCB蚀刻的端面上端宽度几乎与下端宽度相等–线路形状易于控制。mSAP的另一个优点是利用现有资源和技术，采用标准的PCB工艺，如钻孔、电镀等，并采用传统材料，使铜与介电层之间具有良好的附着力，保证了最终产品的高可靠性。

[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/mSAP工艺-2.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/mSAP工艺-2.jpg)[![img](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/mSAP工艺-1.jpg)](https://cdnimg.mr-wu.cn/wp-content/uploads/2020/09/mSAP工艺-1.jpg)

半加成法（mSAP）和改良型半加成法（amSAP）是经过修改和高级修改后的版本，现在有望成为下一代HDI PCB主要采用的工艺。

### 下一代HDI工艺

由于小型化，HDI和微孔为高密度提供了巨大的推动作用。这些技术将跟随着IC单元的几何形状继续发展，变得更小。所以下一次革命将在光学导体领域。

随着超大规模集成电路工艺的不断提升使得计算机系统的处理器性能提高，但是目前电子计算机依旧使用传统的铜线来实现芯片–芯片、处理器–处理器、电路板–电路板之间的连接，国际半导体技术蓝图（ITRS）已经指出未来的电子系统将会受芯片之间的互连所限制，因为目前主要采用的铜线面临的主要问题是：

（1）高速信号失真，带宽有限；
（2）金属导线的传输损耗随着信号频率的增大而增大，限制了高频信号的传输距离；
（3）容易受到电磁干扰；
（4）高功耗等

而光通信有很多传统电信号不具备的优势，比如带宽高、损耗低、无串扰、抗电磁干扰等等。实际上光纤已经彻底替代传统铜线用于长距离通信长达几十年之久，未来的发展趋势是光互连的通信距离将会逐渐变短，从国家之间的长距离通信到未来芯片内部的信号传输。

目前业界普遍认为，当单通道速率达到25 Gb/s以上时，无论从技术实现还是成本上比较，电互连都将面临着极大的挑战。因此，要想克服电子计算机的“瓶颈”，就必须改变传统的基于铜线的互连方式，将光科技引入到电子系统中，用新的光互连代替传统的电互连，才能够大幅度提升计算机的运行速度并促进高速信息通信网的发展，进而满足社会发展的需要。
