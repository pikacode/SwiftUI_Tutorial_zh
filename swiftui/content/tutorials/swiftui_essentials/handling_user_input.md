---
title: "处理用户输入"
date: 2020-04-30T10:09:51+08:00
weight: 3
---

在`Landmark`应用中，标记喜爱的地方，过滤地标列表，只显示喜欢的地标。要增加这些特性，首先要在列表上添加一个开关，用来过滤用户喜欢的地标。在地标上添加一个星标按钮，用户可以点击它来标记这个地标为自己喜欢的。

下载工程文件并且跟着下面的教程实践

{{%attachments title="项目文件" style="blue" pattern=".*zip" /%}}

---

### 第一节 标记用户最喜欢的地标

![mark-favorite](/tutorials/swiftui_essentials/images/swiftui-handle-user-input-mark-favorite.png?width=20pc)

给地标列表的每一行添加一个星标用来表示用户是否标记该地标为自己喜欢的

**步骤1** 打开工程项目，在项目导航下选择`LandmarkRow.swift`文件

**步骤2** 在空白占位后面添加一个`if`表达式，`if`表达式判断是否当前地标是用户喜欢的，如果用户标记当前地标为喜欢就显示星标。可以在SwitUI的代码块中使用`if`语句来条件包含视图

**步骤3** 由于系统图片是矢量类型的，可以使用`foregroundColor(_:)`来改变它的颜色。当地标landmark的`isFavorite`属性为真时，星标显示，稍后会讲怎么修改属性值。

![star](/tutorials/swiftui_essentials/images/swiftui-handle-user-input-star.png?width=50pc)

### 第二节 过滤列表

可以定制地标列表，让它只显示用户喜欢的地标，或者显示所有的地标。要实现这个功能，需要给`LandmarkList`视图类型添加一些状态变量。

`状态(State)`是一个值或者一个值的集合，会随着时间而改变，同时会影响视图的内容、行为或布局。在属性前面加上`@State`修饰词就是给视图添加了一个状态值

![state](/tutorials/swiftui_essentials/images/swiftui-handle-user-input-state.png?width=20pc)

**步骤1** 选择`LandmarkList.swift`文件，并给`LandmarkList`添加一个名为`showFavoritesOnly`的状态，初始值设置为`false`

**步骤2** 点击`Resume`按钮或快捷键`Command+Option+P`刷新画布。当对视图进行添加或修改属性等结构性改变时，需要手动刷新画布

**步骤3** 代码中通过检查`showFavoritesOnly`属性和每一个地标的`isFavorite`属性值来过滤地标列表所展示的内容

![state favorite](/tutorials/swiftui_essentials/images/swiftui-handle-user-input-state-favorite.png?width=50pc)

### 第三节 添加控件来切换状态


