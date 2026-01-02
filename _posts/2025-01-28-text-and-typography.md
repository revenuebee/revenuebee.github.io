---
title: 文本和排版
description: 文本、排版、数学方程式、图表、流程图、图片、视频等的示例。
author: cotes
date: 2025-01-28 14:00:00 +0800
categories: [博客, 演示]
tags: [排版]
math: true
mermaid: true
image:
  path: /assets/img/posts/text-and-typography-1.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: 在多种设备上对 Chirpy 主题进行响应式渲染。
---

## 标题

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
# H1 — 标题
{: .mt-4 .mb-0 }

## H2 — 标题
{: data-toc-skip='' .mt-4 .mb-0 }

### H3 — 标题
{: data-toc-skip='' .mt-4 .mb-0 }

#### H4 — 标题
{: data-toc-skip='' .mt-4 }
<!-- markdownlint-restore -->

## 段落

活着，还是活得安心。这是个问题。凡人的选择是无论如何先活下去再说，“活着”这件事情本身比什么都重要。而天才则把心灵的舒适看得更重，生死则次之。所以凡人可以忍辱，天才却情愿玉碎。每一种人都获得了他最看重的东西，说起来谁也不比谁亏。

## 列表

### 有序列表

1. 第一步
2. 第二步
3. 第三步

### 无序列表

- 章节
  - 小节
    - 段落

### 任务清单

- [ ] 工作
  - [x] 步骤 1
  - [x] 步骤 2
  - [ ] 步骤 3

### 描述列表

太阳
: 地球的自然卫星，通过太阳的反射光可见

月亮
: 地球的自然卫星，通过太阳的反射光可见

## 块引用

> 此行显示 _块引用_.

## 提示

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> 显示 `tip` 类型的示例。
{: .prompt-tip }

> 显示 `info` 类型的示例。
{: .prompt-info }

> 显示 `warning` 类型的示例。
{: .prompt-warning }

> 显示 `danger` 类型的示例。
{: .prompt-danger }
<!-- markdownlint-restore -->

## 表格

| 公司                      | 联系人          | 国家 |
| :--------------------------- | :--------------- | ------: |
| 小米 | 雷军 | 中国 |
| 苹果 | 库克 | 美国 |
| 亚马逊 | 贝索斯 | 美国 |

## 链接

<https://blog.revenuebee.top>

## 脚注

点击钩子会定位到脚注[^footnote], 这里是另一个脚注[^fn-nth-2].

## 内联代码

这是 `Inline Code` 的示例。

## 文件路径

这是 `/path/to/the/file.extend`{: .filepath}.

## 代码块

### 通用

```text
This is a common code snippet, without syntax highlight and line number.
```

### 指定语言

```bash
if [ $? -ne 0 ]; then
  echo "The command was not successful.";
  # 执行必要操作 / 退出
fi;
```

### 指定文件名

```sass
@import
  "colors/light-typography",
  "colors/dark-typography";
```
{: file='_sass/jekyll-theme-chirpy.scss'}

## 数学公式

数学公式由 [**MathJax**](https://www.mathjax.org/) 驱动：

$$
\begin{equation}
  \sum_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6}
  \label{eq:series}
\end{equation}
$$

我们可以将公式引用为 \eqref{eq:series} 。

当 $a \ne 0$ 时，方程 $ax^2 + bx + c = 0$ 的解为

$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$

## Mermaid SVG

```mermaid
 gantt
  title  为 Mermaid 添加甘特图功能
  苹果🍎 :a, 2025-01-10, 1w
  香蕉🍌 :crit, b, 2025-01-13, 1d
  樱桃🍒 :active, c, after b a, 1d
```

## 图片

### 默认（带标题）

![图片描述](/assets/img/posts/text-and-typography-2.png){: width="972" height="589" }
_全屏宽度并居中对齐_

### 左对齐

![图片描述](/assets/img/posts/text-and-typography-2.png){: width="972" height="589" .w-75 .normal}

### 向左浮动

![图片描述](/assets/img/posts/text-and-typography-2.png){: width="972" height="589" .w-50 .left}
大自然在人与人之间的道德和智力方面定下了巨大差别，但社会对这些差别视而不见，对每个人都一视同仁。更有甚者，社会地位和等级所造成的人为的差别取代了大自然定下的差别，前者通常和后者背道而驰。受到大自然薄待的人受益于社会生活的这种安排而获得了良好的位置，而为数不多得到了大自然青睐的人，位置却被贬低了。因此，后一种人总是逃避社交聚会。而每个社交聚会一旦变得人多势众，平庸就会把持统治的地位。社交聚会之所以会对才智卓越之士造成伤害，就是因为每一个人都获得了平等的权利，而这又导致人们对任何事情都提出了同等的权利和要求，尽管他们的才具参差不一。

### 向右浮动

![图片描述](/assets/img/posts/text-and-typography-2.png){: width="972" height="589" .w-50 .right}
当你老了，回顾一生，就会发觉：什么时候出国读书，什么时候决定做第一份职业、何时选定了对象而恋爱、什么时候结婚，其实都是命运的巨变。只是当时站在三岔路口，眼见风云千樯，你作出选择的那一日，在日记上，相当沉闷和平凡，当时还以为是生命中普通的一天。 ｜ 如果一个人说他什么都知道了，那么他已经是死人了；如果一个人认为他什么都不知道，但一直在发现与了解，他不急于寻找终点，也不想达到什么或变成什么，只问攀登不问高。这种人才是活生生的，这样的人生就是真理。 ｜ 云天明的问题在于他无法入世也无法出世,他没有入世的能力也没有出世的资本.只能痛苦地悬在半空。自己今后的人生之路怎么走,通向哪里,他心中一片茫然。

### 深色/浅色模式 & 阴影

下面的图片将根据主题偏好切换深色/浅色模式，注意它有阴影。

![仅限浅色模式](/assets/img/posts/text-and-typography-3.png){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }
![仅限深色模式](/assets/img/posts/text-and-typography-4.png){: .dark .w-75 .shadow .rounded-10 w='1212' h='668' }

## 视频

{% include embed/youtube.html id='LHOVDbuWPB8' %}

## 反向脚注

[^footnote]: 脚注来源
[^fn-nth-2]: 第二个脚注来源
