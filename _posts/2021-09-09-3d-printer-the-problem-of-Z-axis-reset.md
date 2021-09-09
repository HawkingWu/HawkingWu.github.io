---
layout:     post
title:      "低成本3D打印机Z轴回差问题的软件解决方案"
subtitle:   " 用C语言编写程序修改gcode文件 "
date:       2021-09-09
author:     "huanqing"
catalog: true
tags:
    - 3D打印
    - C语言
---

### 低成本3D打印机Z轴回差问题的软件解决方案

- #### 问题描述

前段时间手贱花了七百多买了台打印机，一开始用的便宜PLA是陈年老料，打印底层的时候喷头蹭料，就像滑泥巴一样（见图）。

![img](https://bn1302files.storage.live.com/y4mGJe8Tf7MQvw5bWK8SyWFHnnCeGft58mcls9-xFiQwVOY530jjlNFtLjRLliF6lcaxT2pml0CCrlc1ehmYtczyJgAgklhbkf8IwmyQC3chqZ3pgiZUZNxswkAusCjdSkBEjfbHTh3Bw-YWr_svP5TF7lWwCQWKYyltTpEVCEaIvom8Oz6ZnIvzvDMXnPm_npj?width=3200&height=1197&cropmode=none)

起初以为是材料膨胀系数太大，于是调整挤出量暂时消除了这个问题。一周后店铺做好评活动给我寄了一卷好材料，试用了一下发现“出料过多”的现象没有了，取而代之的是喷头堵住，挤出机滑齿，并且打印出来的零件不论大小，高度统统低1mm。联系厂家客服也承认打印机回零点后会有Z轴空驶的情况，但是不会这么大。我用手晃了下Z轴的滑块，丝杆螺母和丝杆之间确实有零点几的间隙，于是参考知乎文章《[关于3D打印机Z轴的回差问题及G Code应对](https://zhuanlan.zhihu.com/p/337591131)》，尝试后仍不能解决问题。

问题似乎还与Z轴单侧丝杆传动有关，淘宝的低成本打印机XYZ轴几乎都只用了一个电机，由于Prusa i3 类打印机热床是移动的，Z轴丝杆就只能安装在一侧，另一侧只能靠长长的导轨传动。

经过测试，我将打印第2、3、4、5层时抬升的高度全都增加了0.2mm，一定程度上抵消了Z轴移动时无丝杆侧的滞后现象，打印件的高度也能和设计保持一致。

- #### 解决方案

程序思路大概是这样：以只读文件打开源gcode文件，按行查找gcode文件中的高度（Zx.x），将修改后的字符保存到新文件里。

主函数中按行读取，当读到换行符时将缓存传入子函数 layer_edit() 中进行查找和替换。

```C/C++
int main()
{

    if ((fp1 = fopen("1.gcode", "r")) == NULL)
    {
        printf("文件无法打开\n");
        system("pause");
        return 0;
    }
    if ((fp2 = fopen("2.gcode", "w")) == NULL)
    {
        printf("文件无法创建\n");
        system("pause");
        return 0;
    }

    char c[256] = { 0 };
    char* cptr = c;

    while ((*cptr = fgetc(fp1)) != EOF)//文件没结束
    {
        if (*cptr != '\n') //一行没结束
        {
            cptr++;
        }
        else   //一行结束了，处理该行数据
        {
            layer_edit(c);
            for (int i = 0; i < 256; i++) //清空缓存，为下一行处理做准备
                c[i] = 0;
            cptr = c;       //重新指向缓存首地址
        }
    }
    fclose(fp1);
    fclose(fp2);

    printf("\n\n    处理结束！ ");

    system("pause");
    return 0;
}
```

layer_edit() 中有几个变量需要和切片设置一致。

```C/C++
void layer_edit(char* cptr)
{
    static int layer_num = 1;    //当前层
    static float layer_h = 0.2f;  //当前层高

    char str_search[8] = { 0 };      //查找缓存
    char* p_str_search = str_search; //对应指针

    sprintf(p_str_search + 1, "%.2f", layer_h);  //转换到查找缓存里
    str_search[0] = 'Z';
    //清“.x0”小数
    for (int i = 0; i < 6; i++)
    {
        if (str_search[i] == '.')
        {
            if (str_search[i + 2] == '0')
            {
                str_search[i + 2] = 0;
            }
        }
    }
    //清“.0”小数
    for (int i = 0; i < 6; i++)
    {
        if (str_search[i] == '.')
        {
            if (str_search[i + 1] == '0' && str_search[i + 2] == 0)
            {
                str_search[i] = 0;
                str_search[i + 1] = 0;
            }
        }
    }
    for (int i = strlen(str_search); i < 10; i++)//对齐字符串宽度
    {
        printf(" ");
    }
    printf("%s", str_search);

    char* ret; //出现的位置
    ret = strstr(cptr, p_str_search);

    char output_buffer[256] = { 0 };  //输出缓存
    char* p_output_buffer = output_buffer;

    char str_write[7] = { 0 };       //改写缓存
    char* p_str_write = str_write;
    if (ret) //找到该串字符
    {
        for (int i = (int)cptr; i < (int)ret; i++)
        {
            *p_output_buffer = *cptr;  //前段直接复制
            p_output_buffer++;
            cptr++;
        }
        if (layer_num == 1)         //第1层0.2
        {
            sprintf(p_str_write + 1, "%.1f", 0.2);  //转换到查找缓存里
            str_write[0] = 'Z';
        }
        else if (layer_num == 2)    //第2层0.4→0.6
        {
            sprintf(p_str_write + 1, "%.1f", 0.6);//转换到查找缓存里
            str_write[0] = 'Z';
        }
        else if (layer_num == 3)    //第3层0.6→1.0
        {
            sprintf(p_str_write + 1, "%.1f", 1.0);//转换到查找缓存里
            str_write[0] = 'Z';
        }
        else if (layer_num == 4)    //第4层0.8→1.4
        {
            sprintf(p_str_write + 1, "%.1f", 1.4);//转换到查找缓存里
            str_write[0] = 'Z';
        }
        else if (layer_num == 5)    //第5层1.0→1.8
        {
            sprintf(p_str_write + 1, "%.1f", 1.8);//转换到查找缓存里
            str_write[0] = 'Z';
        }

        //其余固定偏移
        else
        {
            sprintf(p_str_write + 1, "%.1f", (layer_h + 0.8));//转换到查找缓存里
            str_write[0] = 'Z';
        }

        //数据整合写入输出缓存
        while (*p_str_write != 0)
        {
            *p_output_buffer = *p_str_write;
            p_output_buffer++;
            p_str_write++;
        }

        *p_output_buffer = '\n';
        fprintf(fp2, "%s", output_buffer);
        layer_num++;
        layer_h += 0.2f;

    }
    else//没找到该串字符，直接复制
    {
        while (*cptr != 0)
        {
            *p_output_buffer = *cptr;
            p_output_buffer++;
            cptr++;
        }
        fprintf(fp2, "%s", output_buffer);
    }

}
```

为什么需要清.0小数操作？因为我的切片软件（Ultimaker Cura）输出的高度为整数时，如2mm高度对应字符串是 Z2 而不是 Z2.0 ，实际上打印机执行这两条命令结果是相同的，所以输出文件那里没有进行操作。如果你的切片软件输出的格式是 Z2.0 或 Z2.00，需要注释掉对应的for循环。

改写层高的函数（sprintf格式化输出）暂时只用了一位小数，如果打印层高用到了0.15mm，需改成 .2f 。

抵消Z轴空驶距离的方法有很多，本文使用的方法不一定是最好的，待我先使用一段时间看看能不能再改进。如果你有更好的方法，欢迎在评论区留言。
