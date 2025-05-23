---
title: 使用绘制上下文
description: 学习如何使用 DrawContext 类来渲染各种图形、文字、纹理。
authors:
  - IMB11
---

本文假设您已经看过[基本渲染概念](./basic-concepts)。

`DrawContext` 类是用于在游戏内渲染的主类。 用于渲染图形、文字、纹理，而且之前也见过，用于操纵 `MatrixStack` 和使用 `BufferBuilder`。

## 绘制图形{#drawing-shapes}

使用 `DrawContext` 绘制**矩形**十分容易。 如果想绘制三角形或其他非矩形的图形，需要使用 `BufferBuilder`。

### 绘制矩形{#drawing-rectangles}

可以使用 `DrawContext.fill(...)` 方法绘制一个实心矩形。

@[code lang=java transcludeWith=:::1](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![矩形](/assets/develop/rendering/draw-context-rectangle.png)

### 绘制轮廓和边框{#drawing-outlines-borders}

假设我们想勾勒出刚刚绘制的矩形的轮廓。 我们可以使用 `DrawContext.drawBorder(...)` 方法来绘制轮廓。

@[code lang=java transcludeWith=:::2](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![带边框的矩形](/assets/develop/rendering/draw-context-rectangle-border.png)

### 绘制独立线条{#drawing-individual-lines}

我们可以使用 `DrawContext.drawHorizontalLine(...)` 和 `DrawContext drawVerticalLine(...)` 来绘制线条。

@[code lang=java transcludeWith=:::3](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![线条](/assets/develop/rendering/draw-context-lines.png)

## 裁剪管理器{#the-scissor-manager}

`DrawContext` 有一套内建的裁剪功能。 可以用来把渲染裁剪为特定区域。 这个功能在绘制某些元素时十分有用，比如悬浮提示，或者其他不应该超出指定渲染区域的界面元素。

### 使用裁剪管理器{#using-the-scissor-manager}

:::tip
裁剪区域可以嵌套！ 但是请一定配对 `enableScissor` 和 `disableScissor`，否则错误的裁剪区域将影响到其他界面元素。
:::

要启用裁剪管理器，只需使用 `DrawContext.enableScissor(...)` 方法。 同样地，要禁用裁剪管理器，使用 `DrawContext.disableScissor()` 方法。

@[code lang=java transcludeWith=:::4](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![裁剪区域](/assets/develop/rendering/draw-context-scissor.png)

如您所见，即使我们告诉游戏用渐变色铺满整个屏幕，也只在裁剪区域内渲染。

## 绘制纹理{#drawing-textures}

在屏幕上绘制纹理没有唯一“正确”的方法，因为 `drawTexture(...)` 方法有很多不同的重载。 本节内容只会涵盖最常用的方法。

### 绘制整个纹理{#drawing-an-entire-texture}

一般来说，我们推荐您使用需要指定 `textureWidth` 和 `textureHeight` 参数的 `drawTexture` 方法重载。 因为如果使用不指定的重载， `DrawContext` 会假设您的纹理文件尺寸是 256x256，而您的纹理文件不一定是这个尺寸，于是渲染结果就不一定正确。

你还需要指定绘制纹理的渲染层。 对于基本纹理，这通常始终是 `RenderLayer::getGuiTextured`。

@[code lang=java transcludeWith=:::5](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![绘制整个纹理](/assets/develop/rendering/draw-context-whole-texture.png)

### 绘制纹理的一部分{#drawing-a-portion-of-a-texture}

在这个情形中，我们需要指定纹理区域的 `u` 和 `v`。 这俩参数用于指定纹理区域左上角的坐标。另外，`regionWidth` 和 `regionHeight` 参数用于指定纹理区域的尺寸。

我们以此纹理为例。

![配方书纹理](/assets/develop/rendering/draw-context-recipe-book-background.png)

如果我们只希望绘制包含放大镜的区域，我们可以使用如下 `u`、`v`、`regionWidth`、`regionHeight` 值：

@[code lang=java transcludeWith=:::6](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![区域纹理](/assets/develop/rendering/draw-context-region-texture.png)

## 绘制文字{#drawing-text}

`DrawContext` 提供了许多渲染文字的方法，都解释得很清楚，您可以自行尝试，此处不再赘述。

假设我们想在屏幕中绘制“Hello World”。 我们可以使用 `DrawContext.drawText(...)` 方法来完成。

@[code lang=java transcludeWith=:::7](@/reference/latest/src/client/java/com/example/docs/rendering/DrawContextExampleScreen.java)

![绘制文字](/assets/develop/rendering/draw-context-text.png)
