# 微信小程序WXSS设置样式

## 一、wxml

界面结构wxmL比较容易理解，主要是由八大类基础组件构成：

| **一、视图容器(View Container)：** |                  | **二、基础内容(Basic Content)**   |            |
| ---------------------------------- | ---------------- | --------------------------------- | ---------- |
| 组件名                             | 说明             | 组件名                            | 说明       |
| view                               | 视图容器         | icon                              | 图标       |
| scroll-view                        | 可滚动视图容器   | text                              | 文字       |
| swiper                             | 可滑动的视图容器 | progress                          | 进度条     |
| **三、表单组件(Form)**             |                  | **四、操作反馈组件(Interaction)** |            |
| 组件名                             | 说明             | 组件名                            | 说明       |
| button                             | 按钮             | action-sheet                      | 上拉菜单   |
| form                               | 表单             | modal                             | 模态弹窗   |
| input                              | 输入框           | progress                          | 进度条     |
| checkbox                           | 多项选择器       | toast                             | 短通知     |
| radio                              | 单项选择器       | 五、导航(Navigation)              |            |
| picker                             | 列表选择器       | 组件名                            | 说明       |
| slider                             | 滑动选择器       | navigator                         | 应用内跳转 |
| switch                             | 开关选择器       |                                   |            |
| label                              | 标签             |                                   |            |
| **六、多媒体(Media)**              |                  | **七、地图(Map)**                 |            |
| 组件名                             | 说明             | 组件名                            | 说明       |
| audio                              | 音频             | map                               | 地图       |
| image                              | 图片             |                                   |            |
| video                              | 视频             |                                   |            |
| **八、画布(Canvas)**               |                  |                                   |            |
| 组件名                             | 说明             |                                   |            |
| canvas                             | 画布             |                                   |            |

## 二、wxss

wxml理解起来容易，但光搭好了框架，并不能达到我们想要的界面效果，这就需要用到wxss样式了。

wxss样式决定了组件应该如何显示，并在css的基础上做了一些功能扩展，主要包括：

### 1. 尺寸单位	rpx（responsive pixel）: 

可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。一般以iphone6屏幕做为视觉设计标准。

rpx 与 px单位换算如下： 

| 设备     | rpx换算px (屏幕宽度/750) | px换算rpx (750/屏幕宽度) |
| -------- | ------------------------ | ------------------------ |
| iPhone5  | 1rpx = 0.42px            | 1px = 2.34rpx            |
| iPhone6  | 1rpx = 0.5px             | 1px = 2rpx               |
| iPhone6s | 1rpx = 0.552px           | 1px = 1.81rpx            |

### 2. 样式导入

可以使用@import语句来导入外联样式表，其后面跟需要导入外联样式表的相对路径，并以分号结束。

例如：

```
/** other.wxss **/

.appText{

  margin:10px;

}

/** app.wxss **/

@import "other.wxss";

.content_text:{

  margin:15px;

}
```

app.wxss是全局样式，作用于每一个页面，而page下的每一个的wxss文件只作用于当前页面，并对全局样式中的相同属性会覆盖。

 对于微信小程序wxss样式的使用来说，其实大部分都和css样式一致，下面简单的进行介绍一下：

### wxss样式属性

#### 一、wxss display(显示)

| 属性               | 说明                                                     |
| ------------------ | -------------------------------------------------------- |
| flex               | 多栏多列布局<br />flex-direction:row/column              |
| inline-block       | 行内块元素                                               |
| inline             | 此元素会被显示为内联元素，元素前后没有换行符             |
| inline-table       | 作为内联表格来显示（类似 <table>），表格前后没有换行符   |
| inline-flex        | 将对象作为内联块级弹性伸缩盒显示                         |
| none               | 此元素不会被显示                                         |
| block              | 此元素将显示为块级元素，此元素前后会带有换行符           |
| list-item          | 此元素会作为列表显示                                     |
| table              | 会作为块级表格来显示（类似 <table>），表格前后带有换行符 |
| table-caption      | 作为一个表格标题显示（类似 <caption>）                   |
| table-cell         | 作为一个表格单元格显示（类似 <td> 和 <th>）              |
| table-column       | 作为一个单元格列显示（类似 <col>）                       |
| table-column-group | 作为一个或多个列的分组来显示（类似 <colgroup>）          |
| table-row          | 作为一个表格行显示（类似 <tr>）                          |
| table-row-group    | 作为一个或多个行的分组来显示（类似 <tbody>）             |
| table-header-group | 作为一个或多个行的分组来显示（类似 <thead>）             |
| table-footer-group | 作为一个或多个行的分组来显示（类似 <tfoot>）             |
| inherit            | 从父元素继承 display 属性的值                            |

####  二、wxss position(定位)

| 属性     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| absolute | 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
| relative | 生成相对定位的元素，相对于其正常位置进行定位。 因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。 |
| fixed    | 生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。 |
| static   | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明） |
| inherit  | 规定应该从父元素继承 position 属性的值                       |

####  三、wxss float(浮动)

| 属性       | 说明                                         |
| ---------- | -------------------------------------------- |
| left       | 元素向左浮动                                 |
| right      | 元素向右浮动                                 |
| none默认值 | 元素不浮动，并会显示在其在文本中出现的位置。 |
| inherit    | 规定应该从父元素继承 float 属性的值。        |

####  四、wxss background(背景)

| 属性                  |           说明                                         |                          语法(属性值)                                        |
| --------------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| background            | 简写属性，作用是将背景属性设置在一个声明中       | background: color position size repeat origin clip attachment image; |
| background-color      | 指定要使用的背景颜色                             |                                                              |
| background-position   | 指定背景图像的位置                               | background-position:center                                   |
| background-size       | 指定背景图片的大小                               | background-size:80px 60px;宽度 高度                          |
| background-repeat     | 指定如何重复背景图像                             | repeat,repeat-x,repeat-y,no-repeat,inherit                   |
| background-origin     | 指定背景图像的定位区域                           | padding-box 背景图像填充框的相对位置 border-box 背景图像边界框的相对位置 content-box 背景图像的相对位置的内容框 |
| background-clip       | 指定背景图像的绘画区域                           | 属性值，同上                                                 |
| background-attachment | 设置背景图像是否固定或者随着页面的其余部分滚动。 | scroll 背景图片随页面的其余部分滚动。这是默认 fixed 背景图像是固定的 inherit 指定background-attachment的设置应该从父元素继承 local 背景图片随滚动元素滚动 |
| background-image      | 指定要使用的一个或多个背景图像                   | url('URL') 图像的URL none 无图像背景会显示。这是默认 inherit 指定背景图像应该从父元素继承 |
####  五、wxss border(边框) 

| 属性                  | 说明                  | 语法(属性值)                                                 |
| --------------------- | --------------------------- | ------------------------------------------------------------ |
| border                | 简写属性，用于把针对四个边的属性设置在一个声明             | border:5px solid red;                                        |
| border-width          | 用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度 | border-top-width 上右下左边框厚度 属性值：thin medium thick length |
| border-style          | 设置元素所有边框的样式，或者单独地为各边设置边框样式。     | border-top-width 上右下左边框样式 属性值：solid,dashed,dotted,double等 |
| border-color          | 元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色    | border-top-width 上右下左边框颜色                            |
####  六、wxss 轮廓（outline）
| 属性                     | 说明                             | 语法(属性值)                                         |
| ------------------------ | -------------------------------- | ---------------------------------------------------- |
| outline                  | 在一个声明中设置所有的外边框属性 | outline: outline-color, outline-style, outline-width |
| outline-color            | 设置外边框的颜色                 |                                                      |
| outline-style            | 设置外边框的样式。               | 属性值：solid,dashed,dotted,double等                 |
| outline-width            | 设置外边框的宽度                 | 属性值：thin medium thick length                     |
####  七、wxss 文本属性（text）

| 属性                      | 说明                     | 语法(属性值)                                                 |
| ------------------------- | ------------------------ | ------------------------------------------------------------ |
| color                     | 设置文本颜色             |                                                              |
| direction                 | 设置文本方向。           | ltr:文本方向从左到右;rtl:文本方向从右到左                    |
| letter-spacing            | 设置字符间距             |                                                              |
| line-height               | 设置行高                 |                                                              |
| text-align                | 对齐元素中的文本         | left：把文本排列到左边。默认值，由浏览器决定。 right：把文本排列到右边。 center：把文本排列到中间。 justify：实现两端对齐文本效果。 inherit: 规定应该从父元素继承 text-align 属性的值。 |
| text-decoration           | 向文本添加修饰           | underline 定义文本下的一条线。 overline 定义文本上的一条线。 line-through 定义穿过文本下的一条线。 blink 定义闪烁的文本。 |
| text-indent               | 缩进元素中文本的首行     |                                                              |
| text-shadow               | 设置文本阴影             | text-shadow: h-shadow v-shadow blur color; h-shadow:水平阴影的位置,允许负值; v-shadow:垂直阴影的位置,允许负值; blur:模糊的距离; color:阴影的颜色 |
| text-transform            | 控制元素中的字母         | capitalize 文本中的每个单词以大写字母开头。 uppercase 定义仅有大写字母。 lowercase 定义无大写字母，仅有小写字母。 |
| unicode-bidi              | 设置或返回文本是否被重写 |                                                              |
| vertical-align            | 设置元素的垂直对齐       |                                                              |
| white-space               | 设置元素中空白的处理方式 |                                                              |
| word-spacing              | 设置字间距               |                                                              |
#### 八、wxss 字体属性（font）
| 属性                      | 说明                               | 语法(属性值)                                                 |
| ------------------------- | ---------------------------------- | ------------------------------------------------------------ |
| font                      | 在一个声明中设置所有字体属性       | font:font-style font-variant font-weight font-size/line-height font-family(按顺序) |
| font-style                | 指定文本的字体样式                 | normal 默认值。浏览器显示一个标准的字体样式。 italic 浏览器会显示一个斜体的字体样式。 oblique 浏览器会显示一个倾斜的字体样式。 inherit 规定应该从父元素继承字体样式。 |
| font-variant              | 以小型大写字体或者正常字体显示文本 | normal 默认值。浏览器会显示一个标准的字体。 small-caps 浏览器会显示小型大写字母的字体。 inherit 规定应该从父元素继承 font-variant 属性的值。 |
| font-weight               | 指定字体的粗细                     | normal 默认值。定义标准的字符。 bold 定义粗体字符。 bolder 定义更粗的字符。 lighter 定义更细的字符。 inherit 规定应该从父元素继承字体的粗细。 |
| font-size                 | 指定文本的字体大小                 | smaller 把 font-size 设置为比父元素更小的尺寸。 larger 把 font-size 设置为比父元素更大的尺寸。 length 把 font-size 设置为一个固定的值。 % 把 font-size 设置为基于父元素的一个百分比值。 |
| font-family               | 指定文本的字体系列                 |                                                              |
#### 九、wxss margin(外边距)（margin）
| 属性          | 说明                             |
| ------------- | -------------------------------- |
| margin        | 在一个声明中设置所有外边距属性。 |
| margin-top    | 设置元素的上外边距。             |
| margin-right  | 设置元素的右外边距。             |
| margin-bottom | 设置元素的下外边距。             |
| margin-left   | 设置元素的左外边距               |
#### 十、wxss padding(填充)（padding）
| 属性           | 说明                                       |
| -------------- | ------------------------------------------ |
| padding        | 使用缩写属性设置在一个声明中的所有填充属性 |
| padding-top    | 设置元素的顶部填充。                       |
| padding-right  | 设置元素的右部填充                         |
| padding-bottom | 设置元素的底部填充                         |
| padding-left   | 设置元素的左部填充                         |
#### 十一、wxss 选择器 
| 选择器            | 样例          | 样例描述                                   |
| ----------------- | ------------- | ------------------------------------------ |
| .class(类选择器)  | .intro        | 选择所有拥有class="intro"的组件            |
| #id(id选择器)     | #firstname    | 选择拥有id="firstname"的组件               |
| element           | view          | 选择所有view组件                           |
| element, element  | view checkbox | 选择所有文档的view组件和所有的checkbox组件 |
| ::after           | view::after   | 在view组件后边插入内容                     |
| ::before          | view::before  | 在view组件前边插入内容                     |

 