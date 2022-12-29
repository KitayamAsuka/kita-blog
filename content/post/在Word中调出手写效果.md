---
title: "在Word中调出手写效果"
date: 2022-12-29T11:23:52+08:00
draft: false 
tags: 
    - 实验
categories: 
    - Life Hack
---
1. 首先，在百度上找一段文字

致 200 米运动员：  
200 百米跑道虽不长，运动健儿志高扬。摸拳擦掌跃欲试，分秒必争斗志扬今天的你们英姿飒爽，今天的你们朝气蓬勃，今天的你们一马当先。相信自己，你是最棒的！不要放弃，不要气馁。  
成功永远属于你们。运动员！加油！  
激动的血液因今天而沸腾，平静的情绪因今天而激动。在明媚的蓝天下，在宽广的赛场上，一颗颗炽热的心为你们而跳动，一双双期待的眼神因你们而牵动。努力吧！运动健儿们，相信自己，胜利的光环将永远环绕你们！  
生命的意义在于奋斗，青春的意义在于拼搏，我们的激情在燃烧，我们的活力在四射，在今天这激动人心的日子里，运动健儿们，请尽情发挥你们的风采本色吧。

## 2. 在文字前加个抬头，假装是大学信纸写的

蹲大下面的横线如图设置

![](https://pic3.zhimg.com/v2-5bdaa4b31dcb7e6a95a2d91f3bfdad1e_r.jpg)

## 3. 寻找合适的字体

这里我分别用的 **汉仪尚巍手书 W** 和 **【嵐】芊柔体**

稍微调整一下格式，如下图所示

![](https://pic3.zhimg.com/v2-3e3a29e1bdbaa5703dc90fcb1ff8367e_r.jpg)

感觉已经差不多了，但灵魂问题就是，这样太整齐了，我们得想办法让文字乱一些

## 4. 宏命令

文件 - 选项 - 信任中心 - 信任中心设置 - 启用所有宏

![](https://pic1.zhimg.com/v2-1ce4fe9a54749419c8de3dd66b583e58_r.jpg)

视图 - 宏 - 创建一个宏

![](https://pic1.zhimg.com/v2-0599180fd39835eafd6b905712b20320_r.jpg)

进去把代码 copy 上

* 代码参考

[如何让打印出来的字体看起来像手写的？](https://www.zhihu.com/question/20308770/answer/241699602)

```
Sub 字体修改()
'
' 字体修改 宏
'
'
Dim R_Character As Range

Dim FontSize(5)
'指定五种字号
FontSize(1) = "16"
FontSize(2) = "16.2"
FontSize(3) = "16.5"
FontSize(4) = "17"
FontSize(5) = "17.2"

Dim ParagraphSpace(5)
'指定五种行间距
ParagraphSpace(1) = "12"
ParagraphSpace(2) = "13"
ParagraphSpace(3) = "17"
ParagraphSpace(4) = "9"
ParagraphSpace(5) = "12"

For Each R_Character In ActiveDocument.Characters
    VBA.Randomize
'字号在5种指定大小中随机选取
    R_Character.Font.Size = FontSize(Int(VBA.Rnd * 5) + 1)
'位置在1—3之间随机选取
    R_Character.Font.Position = Int(VBA.Rnd * 3) + 1
    R_Character.Font.Spacing = 0

Next
Application.ScreenUpdating = True

For Each Cur_Paragraph In ActiveDocument.Paragraphs
'行间距在5个指定值中随机选取
    Cur_Paragraph.LineSpacing = ParagraphSpace(Int(VBA.Rnd * 5) + 1)
    
Next
    Application.ScreenUpdating = True
    


End Sub
```

保存 - 运行

![](https://pic3.zhimg.com/v2-d89c482ba36e107a24298a9884761fce_r.jpg)

回来看原文件，已经 “良莠不齐” 了

![](https://pic1.zhimg.com/v2-3c490a5404d7761e2ba3121d15044dbc_r.jpg)

## 5. 调整

如果对结果不满意，可以多运行几次宏，找到合适的一版，再微调一下

![](https://pic3.zhimg.com/v2-77b4c92dadc14d2b4117f4e0a7b1201a_r.jpg)

下划线格式在下拉菜单能找到详细设置，用空格延长下划线

word 默认段首空格是缩进

解决办法是在上一行倒数几个空格的地方回车，下面一段接上就可以了

(经评论提醒，可以设置取消首行缩进)

![](https://pic1.zhimg.com/v2-fabd3dfd97e9ed86b7ced9a53ac987b0_b.jpg)

## 6. 保存

另存为 pdf，免得打印的时候乱了格式

![](https://pic1.zhimg.com/v2-549bce95df0ada5288f747db6571755c_r.jpg)

最终效果（横线粗细不一是显示的原因，放大后自动消失）

![](https://pic1.zhimg.com/v2-e9ac9c91ddea0d38f042eac8b59bde88_r.jpg)

当然，这种奇技淫巧可能在写反思的时候更有用吧（逃）
