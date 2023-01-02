---
title: "CS142中的CSS技巧"
date: 2023-01-02T20:54:15+08:00
draft: false 
description: 硬着头皮做，做着做着拳头就硬了 
tags:
    - CS142
    - CSS
    - 实验
categories:
    - 编程
---

1. CSS Flexible Box Layout
Flex作为目前最推荐的排版方式，可谓是不得不掌握。而我的记忆还停留在用表格和float排版的年代，为什么我掌握的是这么古早的知识啊！

`flex` flex-grow、flex-shrink、flex-basis的简写，这玩意按照双值三值取才能用得到后面的，麻烦得要死就不管了

`flex-basis` 这个比width又更高的优先级，指示flex元素在主轴方向上的初始大小

`flex-direction` 指定内部元素在flex容器中的布局，定义主轴方向（正或者反）有`row row-reverse column column-reverse`基本上就是字面意思

`flex-flow` 是flex-direction和flex-wrap的简写，取值分别为row和nowrap

`flex-grow` flex增长系数，分配剩余空间的比例

`flex-shrink` flex收缩规则，可以理解为grow的反义词，数字越高占地越小

`flex-wrap` 指定单行还是多行显示。nowrap表示摆放到一行，可能会溢出。wrap为多行，wrap-reverse多行且首尾互换

`order` 布局顺序，按照order的值递增布局

Flex Item为弹性容器的以及子元素

交叉轴指和设置的轴垂直方向的轴

预定义的flex值
initial：0 1 auto
auto：1 1 auto
none：0 0 auto

align-items使元素在交叉轴对齐，默认为stretch，拉伸来填满。flex-start顶部对齐，flex-end下部对齐，center居中对齐

justify-content使元素在主轴上对齐，也是有stretch，flex-start，flex-end，center和space-around每个元素左右空间相等，space-between元素排列好后剩余空间平均分配到元素之间（不会在靠边的地方留空间）

[对齐的实际用例](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Aligning_Items_in_a_Flex_Container)

Q:margin-left: auto 为什么可以使元素靠右?
A:将 margin-left 设为 auto 后, **元素左边的 margin 会被尽可能的撑大**, 所以自然就把元素挤到右边去了

