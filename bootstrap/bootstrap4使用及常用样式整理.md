# bootstrap4使用及常用样式整理

[TOC]

### 简介

>   Bootstrap 是全球最受欢迎的前端组件库，用于开发响应式布局、移动设备优先的 WEB 项目。Bootstrap4 目前是 Bootstrap 的最新版本，是一套用于 HTML、CSS 和 JS 开发的开源工具集。利用我们提供的 Sass 变量和大量 mixin、响应式栅格系统、可扩展的预制组件、基于 jQuery 的强大的插件系统，能够快速为你的想法开发出原型或者构建整个 app 。Bootstrap4 放弃了对 IE8 以及 iOS 6 的支持，现在仅仅支持 IE9 以上 以及 iOS 7 以上版本的浏览器。如果对于其中需要用到以前的浏览器，那么请使用 Bootstrap3。

### 引入方式

1.  前端项目基于jquery去构建：可以直接引入cdn库，bootstrap4.css、jquery.js、bootstrap4.js
2.  前端项目基于react去构建：bootstrap4.css（scss,less）、react.js、react-bootstrap
3.  前端项目基于angular去构建：bootstrap4.css（scss,less）、angular4、ngx-bootstrap

## 1、容器和网格系统

>   容器

-   container 固定宽度，不同尺寸固定了不同的宽度
-   container-fluid 100%宽度

>   栅格系统

-   col-xs					 // < 768px
-   col-sm					 // > = 768px
-   col-md					 // > = 992px
-   col-lg					 // > = 1200px

## 2、字体颜色及背景颜色

>   字体

-   text-muted 柔和
-   text-primary 重要
-   text-success 成功
-   text-info 提示
-   text-warning 警告
-   text-danger 危险
-   text-secondary 副标题
-   text-dark 深灰色文字
-   text-light 浅灰色
-   text-white 白色

>   背景

-   bg-primary
-   bg-secondary
-   bg-success
-   bg-danger
-   bg-warning
-   bg-info
-   bg-light
-   bg-dark
-   bg-white

## 3、边框

>   增加边框

-   border					 //默认：1px solid #dee2e6 !important
-   border-top
-   border-left
-   border-right
-   border-bottom

>   删除边框

-   border-0					 //去除边框或者除去某一边的边框
-   border-top-0
-   border-left-0
-   border-right-0
-   border-bottom-0

>   边框颜色

-   border-primary
-   border-secondary
-   border-success
-   border-danger
-   border-warning
-   border-info
-   border-light
-   border-dark
-   border-white

>   圆角边框

-   rounded					 //border-radius: .25rem!important;
-   rounded-top					 //只有顶部的两边有圆角
-   rounded-right
-   rounded-bottom
-   rounded-left
-   rounded-circle 					//类可以设置椭圆形图片
-   rounded-0
-   img-thumbnail 类用于设置图片缩略图(图片有边框)

## 4 、内边距&外边距

```
m - for classes 代表 margin
p - for classes 代表 padding
t - for classes that set margin-top or padding-top
b - for classes that set margin-bottom or padding-bottom
l - for classes that set margin-left or padding-left
r - for classes that set margin-right or padding-right
x - for classes that set both *-left and *-right
y - for classes that set both *-top and *-bottom
```

>   内边距

-   p-1					 // padding: .25rem!important;
-   p-2					 // padding: .5rem!important;
-   p-3					 // padding: 1rem!important;
-   p-4					 // padding: 1.5rem!important;
-   p-5					 // padding: 3rem!important;

>   单边

-   pt-0
-   pl-0
-   pr-0
-   pb-0
-   px-2
-   py-2

```
pading:.5rem 0;					 //py-2
```

>   外边距

-   m-1					 // margin: .25rem!important;
-   m-2					 // margin: .5rem!important;
-   m-3					 // margin: 1rem!important;
-   m-4					 // margin: 1.5rem!important;
-   m-5					 // margin: 3rem!important;

>   单边

-   mt-0
-   ml-0
-   mr-0
-   mb-0

>   单边大小

-   mt-1					 // margin-left: ($spacer * .25) !important;
-   mt-2
-   mt-3
-   mt-4
-   mt-5
-   mx-auto

```
margin:0 auto;
```

>   auto

-   ml-auto					 // margin-left: auto!important;
-   mr-auto					 // margin-right: auto!important;
-   mt-auto					 // margin-top: auto!important;
-   mb-auto					 // margin-bottom: auto!important;

## 5、清除浮动

-   clearfix					 //清除浮动类实现方式如下

```
// Mixin itself
@mixin clearfix() {
    &::after {
    display: block;
    content: "";
    clear: both;
    }
}
// Usage as a mixin
.element {
	@include clearfix;
}
```

## 6、display 显示

>   .d-{value} for all					 //任何尺寸使用
>
>   .d-{breakpoint}-{value} for sm, md, lg, and xl.//对应尺寸加载

-   d-none
-   d-inline
-   d-inline-block
-   d-block
-   d-table
-   d-table-cell
-   d-table-row
-   d-flex
-   d-inline-flex

>   打印样式					 //使用较少

-   d-print-none
-   d-print-inline
-   d-print-inline-block
-   d-print-block
-   d-print-table
-   d-print-table-row
-   d-print-table-cell
-   d-print-flex
-   d-print-inline-flex

## 7、嵌入元素样式

>   包含`<iframe>, <embed>, <video>, and <object>`等元素样式

-   embed-responsive					 //外部盒子
-   embed-responsive-21by9（16by9,4by3,1by1）//宽高比
-   embed-responsive-item					 //添加在元素上的样式

```
<div class="embed-responsive embed-responsive-21by9">
	<`iframe class="embed-responsive-item" src="..."></iframe`>
</div>
```

## 8、弹性布局

-   d-flex					 //将对象作为弹性伸缩盒显示
-   d-inline-flex					 //将对象作为内联块级弹性伸缩盒显示
-   d-sm-flex					 //对应尺寸加载
-   d-sm-inline-flex
-   d-md-flex
-   d-md-inline-flex
-   d-lg-flex
-   d-lg-inline-flex
-   d-xl-flex
-   d-xl-inline-flex

>   方向
>
>   >   水平

-   flex-row
-   flex-row-reverse					 //相反方向

>   >   垂直

-   flex-column
-   flex-column-reverse

>   同样的不同尺寸适配样式

-   flex-row
-   flex-row-reverse
-   flex-column
-   flex-column-reverse
-   flex-sm-row
-   flex-sm-row-reverse
-   flex-sm-column
-   flex-sm-column-reverse
-   flex-md-row
-   flex-md-row-reverse
-   flex-md-column
-   flex-md-column-reverse
-   flex-lg-row
-   flex-lg-row-reverse
-   flex-lg-column
-   flex-lg-column-reverse
-   flex-xl-row
-   flex-xl-row-reverse
-   flex-xl-column
-   flex-xl-column-reverse

>   justify content					 //可匹配到不同尺寸

-   justify-content-start
-   justify-content-end
-   justify-content-center
-   justify-content-between
-   justify-content-around

>   wrap

-   flex-nowrap					 //支持不同尺寸匹配
-   flex-wrap
-   flex-sm-wrap-reverse

>   order					 //子元素设置 支持不同尺寸匹配

-   order-0
-   order-1
-   order-2
-   order-3
-   order-4
-   order-5
-   order-6
-   order-7
-   order-8
-   order-9
-   order-10
-   order-11
-   order-12

>   Align items					 //子元素设置 支持不同尺寸匹配

-   align-items-start
-   align-items-end
-   align-items-center
-   lign-items-baseline
-   align-items-stretch

>   Align self//子元素设置 支持不同尺寸匹配

-   align-self-start
-   align-self-end
-   align-self-center
-   align-self-baseline
-   align-self-stretch

>   Align content//子元素设置 支持不同尺寸匹配ß

-   align-content-start
-   align-content-end
-   align-content-center
-   align-content-around
-   align-content-stretch

## 9、浮动 

>   可适配：float-(sm,md lg xl)-xxx

-   float-left
-   float-right
-   float-none

## 10、图片替换文字

-   text-hide				 //使用.text-hide类来帮助用背景图像替换元素的文本内容。

```
<h1 class="text-hide" style="background-image: url('/assets/brand/bootstrap-solid.svg'); width: 50px; height: 50px;">Bootstrap</h1>
```

## 11、定位

-   position-static
-   position-relative
-   position-absolute
-   position-fixed
-   position-sticky

>   固定定位

-   fixed-top
-   fixed-bottom

```
.fixed-top {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    z-index: 1030;
}
```

-   sticky-top					 //使用较少，兼容性一般

```
position: sticky;					 //粘性布局 这是一个结合了 position:relative 和 position:fixed 两种定位功能于一体的特殊定位，适用于一些特殊场景。
生效规则
position:sticky 的生效是有一定的限制的，总结如下：
须指定 top, right, bottom 或 left 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。
并且 top 和 bottom 同时设置时，top 生效的优先级高，left 和 right 同时设置时，left 的优先级高。
设定为 position:sticky 元素的任意父节点的 overflow 属性必须是 visible，否则 position:sticky 不会生效。这里需要解释一下：
如果 position:sticky 元素的任意父节点定位设置为 overflow:hidden，则父容器无法进行滚动，所以 position:sticky 元素也不会有滚动然后固定的情况。
如果 position:sticky 元素的任意父节点定位设置为 position:relative | absolute | fixed，则元素相对父元素进行定位，而不会相对 viewprot 定位。
达到设定的阀值。这个还算好理解，也就是设定了 position:sticky 的元素表现为 relative 还是 fixed 是根据元素是否达到设定了的阈值决定的。
```

## 12 、尺寸（size）

-   w-25

```
//width: 25%!important; 以下值同理
```

-   w-50
-   w-75
-   w-100

>   区间

-   mw-100
-   mh-100

## 13、文本

>   文本定位

-   text-left					 //文本居左
-   text-center
-   text-right
-   text-sm-left
-   text-md-left
-   text-lg-left
-   text-xl-left

>   文本 转换（Text transform）					 //所有浏览器都支持该属性

-   text-lowercase 					//字母文本小写
-   text-uppercase					 //字母文本大写
-   text-capitalize					 //文本中的每个单词以大写字母开头。

>   字体 加重和斜体（Font weight and italics）

-   font-weight-bold					 //字体加重
-   font-weight-normal				//正常字体
-   font-weight-light					 //字体变细
-   font-italic					 	//斜体

## 14、 垂直对齐

**（Vertical alignment）**

-   align-baseline
-   align-top
-   align-middle
-   align-bottom
-   align-text-top
-   align-text-bottom

```
vertical-align: text-bottom!important;			 //.align-text-bottom
```

## 15、显示隐藏

-   show
-   hidden or sr-only
-   hide					 //类仍然可用，但是它不能对屏幕阅读器起作 不建议使用
-   invisible 				//隐藏保留该元素的文档位置
-   visible					 //可见

```
visibility: hidden!important;
```

## 16、表格

-   table					 		//默认样式
-   table-striped					 	//条纹表格
-   table-bordered					 //边框表格
-   table-hover					 	//鼠标悬停
-   table-dark					 	//黑色背景表格
-   table-condensed					 //紧凑的表格
-   table-responsive					 //响应式表格

>   表格行设置背景色

-   active 					 //鼠标悬停在行或单元格上时所设置的颜色
-   success					 //标识成功或积极的动作
-   info 					 //标识普通的提示信息或动作
-   warning					 //标识警告或需要用户注意
-   danger 					 //标识危险或潜在的带来负面影响的动作

## 17、按钮及按钮组

>   按钮

-   btn-primary					 //主要按钮
-   btn-secondary					 //次要按钮
-   btn-success					 //成功按钮
-   btn-info					 //信息按钮
-   btn-danger					 //危险
-   btn-outline-primary					 //按钮边框
-   btn-xs btn-sm btn-lg					 //小大号按钮
-   btn-block					 //块级按钮
-   active					 //可用
-   disabled					 //禁用

>   按钮组

-   btn-group					 //按钮组
-   btn-group-lg|sm|xs 			//控制按钮组大小
-   btn-group-vertical 			//垂直按钮组

## 18、列表组

-   list-group					 //列表组
-   list-group-item				//列表li
-   list-unstyled					 //无样式列表
-   list-inline					 //内联列表 添加在ul上

>   列表背景色

-   list-group-item-action
-   list-group-item-success
-   list-group-item-secondary
-   list-group-item-info
-   list-group-item-warning
-   list-group-item-danger
-   list-group-item-dark
-   list-group-item-light

## 19、表单

-   form-inline					 //form元素添加该类，可构成内联表单
-   form-horizontal				 //可以将 label 标签和控件组水平并排布局
-   form-group					 //表单组 margin-bottom: 15px;
-   input-group-addon			 //配合input表单使用，可再起前后添加图标或者后缀
-   form-control					 //该表单元素宽度变成100%
-   sr-only 						//隐藏表单

>   控制表单尺寸

-   input-lg
-   input-sm

>   多选和单选

-   checkbox					 //包裹复选框
-   checkbox-inline					 // 内联多选
-   radio					 // 包裹单选框
-   radio-inline					 // 内联单选
-   disabled					 //不可点击

>   下拉列表（select）

-   form-control

>   校验状态

-   has-success					 //可配合.form-group使用
-   has-warning					 //可配合.form-group使用
-   has-error					 //可配合.form-group使用

## 20 、信息提示框

-   alert 类

>   背景色 追加以下类名

-   alert-success
-   alert-info
-   alert-warning
-   alert-danger
-   alert-primary
-   alert-secondary
-   alert-light
-   alert-dark 类来实现暗黑提示框

## 21、三角符号

-   caret					 //css实现向下小三角
