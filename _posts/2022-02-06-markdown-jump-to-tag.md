---
layout:     post
title:      "Markdown添加锚点，跳转到指定位置"
subtitle:   " 使用html标签跳转到文章中的指定位置 "
date:       2022-02-06
author:     "huanqing"
catalog: true
tags:
    - Markdown
    - html
---



在Markdown中添加锚点，跳转到指定位置。方法是使用 html 标签。

#### 示例

    索引

      <a href="#tag1">第一段</a>

      <a href="#tag2">第二段</a>

      <a href="#tag3">第三段</a>

    <a name="tag1">第一段</a>

        正文......

    <a name="tag2">第二段</a>

        正文......

    <a name="tag3">第三段</a>

        正文......



#### 示例源码

```markdown
索引
  <a href="#tag1">第一段</a>
  <a href="#tag2">第二段</a>
  <a href="#tag3">第三段</a>
  
  <a name="tag1">第一段</a>
    正文......
  <a name="tag2">第二段</a>
    正文......
  <a name="tag3">第三段</a>
      正文......
```

