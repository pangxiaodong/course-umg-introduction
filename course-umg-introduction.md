### 1.入门篇介绍

略

### 2.UI的创建、显示与移除

- Create UI Widget：创建UIWidget
- SET：设置创建的UIWidget为变量UI
- Is Valid：检查变量UI是否存在，防止重复创建
- Add to Viewport：显示UI
- Remove From Parent：移除UI

![Create-UI](_IMG\Create-UI.png)

![Remove-UI.png](_IMG\Remove-UI.png)

### 3.CanvasPanel控件主要属性讲解

- Tool Tip Text：悬浮文本，Bind可以绑定一个函数
- Is Enable：是否启用
- Visibility：若干种（隐藏不占空间，隐藏占空间，是否影响孩子的时间点击）
- Render Opactiy：影响孩子的透明度
- Tool Tip Widget：背包悬停界面，绑定一个Widget

![Canvas-Panel](_IMG\Canvas-Panel.png)

### 4.Text控件主要属性讲解

Slot

- Slot：表示这个Text是在Canvas Panel的插槽中
- Anchors：锚点



![Text-Slot](_IMG\Text-Slot.png)

锚点作为点： 如果想让这个Text保持在正中间，应该把锚点放在正中间。

![Anchor-Is-Point](_IMG\Anchor-Is-Point.png)

锚点作为线

- 线表示会拉伸。目前锚点X轴是线，表示控件的X方向，会随着屏幕的拉伸而拉伸（屏幕X或者Y方向拉伸都会影响控件的X方向拉伸）
- 线表示百分比。

![Anchor-Is-Line](_IMG\Anchor-Is-Line.png)

![Anchor-Is-Line-Percent.png](_IMG\Anchor-Is-Line-Percent.png)

Alignment：原点，默认是左上角 (0,0)

Size To Content：尺寸自适应

ZOrder：排序相关

![Alignment.png](_IMG\Alignment.png)

 文字的左中右对齐

![Text-Justification.png](_IMG\Text-Justification.png)

Text的中心点，影响自身的旋转中心

![Text-Pivot.png](_IMG\Text-Pivot.png)

### 5.UI响应玩家输入以及响应机制

UserWidget 中不能直接接受键盘鼠标收入（Keyboard T）。Player的蓝图可以。

UI检测按键

- Override OnKeyDown函数
- 返回值Handled表示按键消息不会继续传递到输入流（先UI 蓝图的按键处理，然后Character蓝图的按键处理）
- 需要支持焦点

![UI-Override-OnKeyDown-Function.png](_IMG\UI-Override-OnKeyDown-Function.png)

![UI-SetFocus.png](_IMG\UI-SetFocus.png)

### 6.UI响应玩家输入以及响应机制

三种模式

- Game 和 UI
- 只有Game
- 只有UI

![SetInputMode.png](_IMG\SetInputMode.png)

### 7.ProgressBar与Image控件

渲染顺序

- 上面的先渲染，下面的后渲染。这点与Unity一样的。
- ZOrder，数值越小的越优先渲染。

![UI-RenderOrder.png](_IMG\UI-RenderOrder.png)

ProgressBar的Marquee模式

- 不会跟着Precent数值来改变，是循环移动图片

![ProgressBar-Marquee.png](_IMG\ProgressBar-Marquee.png)

Image Size

- 只是图像的大小，只有勾选了Size To Content，才会影响到图像控件的大小。

 ![Image-ImageSize.png](_IMG\Image-ImageSize.png)

### 8.尺寸、水平与垂直框

SizeBox

- 强制控制孩子的尺寸
- 只能容纳一个孩子

SizeBox的ChildLayout，勾选Size To Content

- 属性1-属性6：覆盖宽度，覆盖高度，最小宽度，最小高度，最大宽度，最大高度
- 优先级：属性1,2 > 属性3-6，

SizeBox的ChildLayout，不勾选Size To Content

- 属性7-属性8：最小纵横比，最大纵横比 （都设置为1，可以保证等比缩放）

![SizeBox-ChildLayout.png](_IMG\SizeBox-ChildLayout.png)

HorizontalBox-Auto模式

- 虽然Image Size还是512x512，但是高度被压了。水平框会直接限制高度，不会直接限制宽度。

HorizontalBox-Fill模式

- 会让图片会尽可能填充满HorizontalBox。如果HorizontalBox的尺寸超过512*512，不会拉伸图片。
- 如果想要拉伸，在Alignment里面选择对齐方式。

![HorizontalBox.png](_IMG\HorizontalBox.png)

两个图像，一样的设置，都是Fill，都是填充满，平分秋色。

![HorizontalBox-Fill-2-Image.png](_IMG\HorizontalBox-Fill-2-Image.png)

第1个图像是Auto，后两个图像是FIll。先处理Auto，剩下的空间平分秋色。

![HorizontalBox-Fill-3-Image.png](_IMG\HorizontalBox-Fill-3-Image.png)

两个图像，都是Auto，限制高度，尽可能满足宽度，但是第二个图像的宽度不能完全满足。

![HorizontalBox-Fill-2-Image-Auto.png](_IMG\HorizontalBox-Fill-2-Image-Auto.png)

### 9.Spacer、Border与Overlay控件

Spacer在水平框里面：宽度有用，高度没用。

![Spacer-In-Horizontal.png](_IMG\Spacer-In-Horizontal.png)

Border：适合用来制作背景

Appearance

- Brush，Image：颜色，图片
- Desired Size Scale：与Size To Content搭配使用

![Border.png](_IMG\Border.png)

Overlay

- 自动叠罗汉

![Overlay.png](_IMG\Overlay.png)

### 10.Button控件

NormalPadding影响的是Button下面的子控件的位置。

![Button-NormalPadding.png](_IMG\Button-NormalPadding.png)

Button的Event事件

- Click事件一定会包含一个Press事件
- 点击加号会自动调到EventGraph

![Button-Event.png](_IMG\Button-Event.png)

![Button-EventGraph.png](_IMG\Button-EventGraph.png)

  交互-Click

![Button-Interaction-Click.png](_IMG\Button-Interaction-Click.png)

### 11.外部图片的导入与设置