---
title: "视图动画和转场"
date: 2020-05-07T23:20:35+08:00
weight: 2
---

使用SwiftUI可以把视图状态的改变转成动画过程，`SwiftUI`会处理所有复杂的动画细节

在这篇中，会给跟踪用户徒步的图表视图添加动画。使用`animation(_:)`修改器给一个视图添加动画效果非常容易

下载起步项目并跟着本篇教程一步步实践，或者查看本篇完成状态时的工程代码去学习

{{%attachments title="项目文件" style="blue" pattern=".*zip" /%}}

---

### 第一节 给每个视图单独添加动画

在视图上使用`animation(_:)`修改器时，`SwiftUI`会在视图的任何可进行动画的属性发生改变时产生对应的动画效果。视图的颜色、不透明度、旋转角度、大小及一些其它属性都是可进行动画的

![animate button](/tutorials/drawing_and_animation/images/swiftui-drawing-path-and-shape-animate-button.png?width=20pc)

**步骤1** 在`HikeView.swift`中，打开实时预览，体验一下图表的打开和隐藏，此时的状态改变时是没有添加动画效果的。在本篇的实践中，保持实时预览一直打开，每一步修改的效果就可以实时的看到

![live preview animation](/tutorials/drawing_and_animation/animating_views_and_transitions.files/live-preview-animations.mp4?width=20pc)

**步骤2** 给显示/隐藏切换的箭头按钮添加旋转动画，会发现现在按钮点击时的旋转有一个动画过渡的效果了

![rotate button animation](/tutorials/drawing_and_animation/images/swiftui-animation-transition-rotate-button-animation.png?width=30pc)

![rotate button animation video](/tutorials/drawing_and_animation/animating_views_and_transitions.files/rotate-button-aniamtion.mp4?width=20pc)

**步骤3** 当视图从隐藏到展示时，让切换按钮变大1.5倍

![rotate button scale](/tutorials/drawing_and_animation/images/swiftui-animation-transition-rotate-button-scale.png?width=30pc)

![rotate button scale video](/tutorials/drawing_and_animation/animating_views_and_transitions.files/rotate-button-animation-scale.mp4?width=20pc)

**步骤4** 把动画的类型从`easeInOut`改为`spring()`。SwiftUI包含一些预设或可自定义的动画类型，像`弹簧(spring)`动画和类型`液体(fluid)`动画类型。可以调整动画开始前的等待时长、动画的速度也可以指定让动画循环重复的进行

![rotate button spring](/tutorials/drawing_and_animation/images/swiftui-animation-transtion-rotate-button-spring.png?width=30pc)

**步骤5** 如果只想让按钮具有缩放动画而不进行旋转动画，可以在`scaleEffect`添加`animation(nil)`来实现。可以在这里做一些实验，如果把其它的一些动画效果结合在一起，会怎么样

![rotate button no rotate](/tutorials/drawing_and_animation/images/swiftui-animation-transition-rotate-button-no-rotate.png?width=30pc)

**步骤6** 学下一节之前，把本节中添加的`animation(_:)`修改器都去掉

![rotate button resume](/tutorials/drawing_and_animation/images/swiftui-animation-transition-rotate-button-resume.png?width=30pc)

### 第二节

**步骤1** 
**步骤2** 
**步骤3** 
**步骤4** 

### 第三节

**步骤1** 
**步骤2** 
**步骤3** 
**步骤4** 

### 第四节 

**步骤1** 
**步骤2** 
**步骤3** 
**步骤4** 

### 检查是否理解

**问题1** 
**问题2** 
**问题3** 
**问题4** 