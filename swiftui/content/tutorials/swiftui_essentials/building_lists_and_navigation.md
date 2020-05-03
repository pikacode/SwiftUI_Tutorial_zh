---
title: "创建列表和导航"
date: 2020-04-30T10:09:35+08:00
weight: 2
---

地标详情页视图已经创建完成，我们需要提供一种方式让用户可以查看完整的地标列表，并且可以查看每一个地标的详情

下面会创建一个可以展示任何地标信息的视图，并动态生成一个可滚动列表，用户可以点击列表项去查看地标的详细信息。优化视图显示时，可以使用Xcode画布来渲染多个不同设备大小下的预览视图。

下载下面的工程文件，并跟着教程一步步学习构建列表和视图间导航

{{%attachments title="项目文件" style="blue" pattern=".*zip" /%}}

---

### 第一节 了解样本数据

前面的教程中，自定义视图所展示的信息都直接被写死在代码中，这篇教程中会学习给自定义视图传入样本数据进行展示

![swiftui-building-list](/tutorials/swiftui_essentials/images/swiftui-building-list.png?width=20pc)

**步骤1** 打开项目导航器，选择**Models->Landmark.swift**文件，这个文件中声明了需要在应用中展示一个地标所需要信息的结构化名称，并通过导入`landmarkData.json`文件中的数据，生成一个地标信息数组。

![building list model](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-model.png?width=50pc)

**步骤2** 在项目导航器中选择**Resources->landmarkData.json**，在后面的教程中我们都会使用这个样本数据文件

![building list sample data](/tutorials/swiftui_essentials/images/swiftui-building-list-sampe-data.png?width=50pc)

**步骤3** 注意，之前的`ContentView`视图，已经被改名为`LandmarkDetail`了，在本教程和后面的教程中，还会创建一些其它的视图

![landmark detail](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-detail.png?width=20pc)

### 第二节 创建行视图

本教程中创建的第一个视图就是用来显示每个地标的行视图，行视图把地标的相关信息存储在一个属性中，一行就可以代表一个地标，稍后就会把这些行组合成为一个列表。

![swiftui-building-list-landmark-row](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-row.png?width=20pc)

**步骤1** 创建一个名为`LandmarkRow.swift`的SwiftUI视图

![landmark row create](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-row-create.png?width=20pc)

**步骤2** 如果预览视图没有出现，可以选择菜单**编辑器->画布**，打开画布，并点击**Resume**进行预览，或者使用**Command+Option+Enter**快捷键调出画面，再使用**Command+Option+P**快捷键开始预览模式

**步骤3** 添加`landmark`属性做为`LandmarkRow`视图的一个存储属性。当添加`landmark`属性后，预览视图可能会停止工作，因为`LandmarkRow`视图初始化时需要有一个`landmark`实例。要想修复预览视图，需要修改`Preview Provider`

**步骤4** 在`LandmarkRow_Previews`的静态属性`previews`中给`LandmarkRow`初始化器中传入`landmark`参数，这个参数使用`landmarkData`数组的第一个元素。预览视图当前显示`Hello, World`

![landmark row layout](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-row-layout.png?width=20pc)

**步骤5** 在一个`HStack`中嵌入一个`Text`

**步骤6** 修改这个`Text`，让它使用`landmark`属性的`name`字段

**步骤7** 在`Text`视图前面添加一个图片视图，在`Text`视图后面添加`Spacer`视图

![landmark layout 1](/tutorials/swiftui_essentials/images/swiftui-building-list-landmark-row-layout-1.png?width=50pc)

### 第三节 自定义行预览

Xcode的画布会自动识别当前代码编辑器中遵循`PreviewProvider`协议的类型，并将它们渲染并展示在画面上。一个视图预览提供者(preview provider)返回一个或多个视图，这些视图可以配置不同的大小和设备型号。

可以定制从`preview provider`中返回的视图被渲染在何种场景下。

![row preivew](/tutorials/swiftui_essentials/images/swiftui-building-list-row-preview.png?width=20pc)

**步骤1** 在`LandmarkRow_Previews`中，把`landmark`参数更新为`landmarkData`数组的第二个元素，预览视图会立即刷新反映第二个元素的渲染情况

![preivew row 2](/tutorials/swiftui_essentials/images/swiftui-building-list-preview-row-2.png?width=40pc)

**步骤2** 使用`previewLayout(_:)`修改器设置一个行视图在列表中显示的尺寸大小。可以使用`Group`的方式，返回多个不同场景下的预览视图

![preview layout size](/tutorials/swiftui_essentials/images/swiftui-building-list-preivew-layout-size.png?width=40pc)

**步骤3** 把预览的行视图包裹在`Group`中，把之前的第一个行视图也加进去。`Group`是一个容器，它可以把视图内容组织起来，Xcode会把`Group`内的每个子视图当作画布内一个单独的预览视图处理

![preview group size](/tutorials/swiftui_essentials/images/swiftui-building-list-preivew-group.png?width=40pc)

**步骤4** 为了简化代码，可以把`previewLayout(_:)`这个修改器应用到外层的`Group`上，`Group`的每一个子视图会继承自己所处环境的配置。对`preivew provider`的修改只会影响预览画布的表现，对实际的应用不会产生影响。

![preview group coniguration](/tutorials/swiftui_essentials/images/swiftui-building-list-preview-layout-group-configuration.png?width=40pc)
