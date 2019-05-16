## LESS 原理及使用方式
CSS（层叠样式表）是一门历史悠久的标记性语言，同 HTML 一道，被广泛应用于万维网（World Wide Web）中。HTML 主要负责文档结构的定义，CSS 负责文档表现形式或样式的定义。
作为一门标记性语言，CSS 的语法相对简单，对使用者的要求较低，但同时也带来一些问题：CSS 需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码，造成这些困难的很大原因源于 CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。LESS 为 Web 开发者带来了福音，它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，LESS 可以让我们用更少的代码做更多的事情。
本质上，LESS 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。LESS 并没有裁剪 CSS 原有的特性，更不是用来取代 CSS 的，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。下面是一个简单的例子：
##### LESS 文件
```
@color:#4D926F;
#header {
	color: @color;
} 
 h2 {
	color: @color;
}
```
经过编译生成的 CSS 文件如下：
```
#header {
	color:#4D926F;
} 
h2 {
	color:#4D926F;
}
```
从上面的例子可以看出，学习 LESS 非常容易，只要你了解 CSS 基础就可以很容易上手。
LESS 可以直接在客户端使用，也可以在服务器端使用。在实际项目开发中，我们更推荐使用第三种方式，将 LESS 文件编译生成静态 CSS 文件，并在 HTML 文档中应用。

#### 客户端
我们可以直接在客户端使用.less（LESS 源文件），只需要从 [http://lesscss.org](http://lesscss.org/)下载 less.js 文件，然后在我们需要引入 LESS 源文件的 HTML 中加入如下代码：
```
<link rel="stylesheet/less" type="text/css" href="styles.less">
```
LESS 源文件的引入方式与标准 CSS 文件引入方式一样：
```
<link rel="stylesheet/less" type="text/css" href="styles.less">
```
需要注意的是：在引入.less 文件时，rel 属性要设置为“stylesheet/less”。还有更重要的一点需要注意的是：LESS 源文件一定要在 less.js 引入之前引入，这样才能保证 LESS 源文件正确编译解析。
#### 服务器端
LESS 在服务器端的使用主要是借助于 LESS 的编译器，将 LESS 源文件编译生成最终的 CSS 文件，目前常用的方式是利用 node 的包管理器 (npm) 安装 LESS，安装成功后就可以在 node 环境中对 LESS 源文件进行编译。
在项目开发初期，我们无论采用客户端还是服务器端的用法，我们都需要想办法将我们要用到的 CSS 或 LESS 文件引入到我们的 HTML 页面或是桥接文件中，LESS 提供了一个我们很熟悉的功能— Importing。我们可以通过这个关键字引入我们需要的.less 或.css 文件。 如：
@import “variables.less”;
.less 文件也可以省略后缀名，像这样：
@import “variables”;
引入 CSS 同 LESS 文件一样，只是.css 后缀名不能省略。

#### 使用编译生成的静态 CSS 文件
我们可以通过 LESS 的编译器，将 LESS 文件编译成为 CSS 文件，在 HTML 文章中引入使用。这里要强调的一点，LESS 是完全兼容 CSS 语法的，也就是说，我们可以将标准的 CSS 文件直接改成.less 格式，LESS 编译器可以完全识别。
## 变量
LESS 允许开发者自定义变量，变量可以在全局样式中使用，变量使得样式修改起来更加简单。
我们可以从下面的代码了解变量的使用及作用：
##### LESS 文件
```
@border-color :#b5bcc7;
.mythemes tableBorder{
	border : 1px solid @border-color;
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
.mythemes tableBorder {
	border: 1px solid#b5bcc7;
}
```
从上面的代码中我们可以看出，变量是 VALUE（值）级别的复用，可以将相同的值定义成变量统一管理起来。
该特性适用于定义主题，我们可以将背景颜色、字体颜色、边框属性等常规样式进行统一定义，这样不同的主题只需要定义不同的变量文件就可以了。当然该特性也同样适用于 CSS RESET（重置样式表），在 Web 开发中，我们往往需要屏蔽浏览器默认的样式行为而需要重新定义样式表来覆盖浏览器的默认行为，这里可以使用 LESS 的变量特性，这样就可以在不同的项目间重用样式表，我们仅需要在不同的项目样式表中，根据需求重新给变量赋值即可。
LESS 中的变量和其他编程语言一样，可以实现值的复用，同样它也有生命周期，也就是 Scope（变量范围，开发人员惯称之为作用域），简单的讲就是局部变量还是全局变量的概念，查找变量的顺序是先在局部定义中找，如果找不到，则查找上级定义，直至全局。下面我们通过一个简单的例子来解释 Scope。
##### LESS 文件
```
@width : 20px;
#homeDiv {
	@width : 30px;
 	#centerDiv{
        width : @width;  // 此处应该取最近定义的变量 width 的值 30px 
    } 
} 
#leftDiv {
	width : @width;	  // 此处应该取最上面定义的变量 width 的值 20px 
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件

```
#homeDiv#centerDiv {
	width: 30px;
} 
#leftDiv {
	width: 20px;
}
```
## Mixins（混入）
Mixins（混入）功能对用开发者来说并不陌生，很多动态语言都支持 Mixins（混入）特性，这里很像C语言的宏（macro），是可以重用的代码块。
我们先简单看一下 Mixins 在 LESS 中的使用：
##### LESS 文件
```
// 定义一个样式选择器
.roundedCorners(@radius:5px) {
	-moz-border-radius: @radius;
	-webkit-border-radius: @radius;
	border-radius: @radius;
} 
 // 在另外的样式选择器中使用
#header {
	.roundedCorners;
} 
#footer {
	.roundedCorners(10px);
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
#header {
	-moz-border-radius:5px;
	-webkit-border-radius:5px;
	border-radius:5px;
} 
#footer {
	-moz-border-radius:10px;
	-webkit-border-radius:10px;
	border-radius:10px;
}
```
从上面的代码我们可以看出：Mixins 其实是一种嵌套，它允许将一个类嵌入到另外一个类中使用，被嵌入的类也可以称作变量，简单的讲，Mixins 其实是规则级别的复用。
Mixins 还有一种形式叫做 Parametric Mixins（混入参数），LESS mixin的强大之处，在于可以指定参数和缺省值。
##### LESS 文件
```
// 定义一个样式选择器
.borderRadius(@radius){
	-moz-border-radius: @radius;
	-webkit-border-radius: @radius;
	border-radius: @radius;
} 
 // 使用已定义的样式选择器
#header {
	.borderRadius(10px);  // 把 10px 作为参数传递给样式选择器
} 
.btn {
	.borderRadius(3px); // // 把 3px 作为参数传递给样式选择器
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
#header {
	-moz-border-radius: 10px;
	-webkit-border-radius: 10px;
	border-radius: 10px;
} 
.btn {
	-moz-border-radius: 3px;
	-webkit-border-radius: 3px;
	border-radius: 3px;
}
```
我们还可以给 Mixins 的参数定义一人默认值，如
##### LESS 文件
```
.borderRadius(@radius:5px){
	-moz-border-radius: @radius;
	-webkit-border-radius: @radius;
	border-radius: @radius;
} 
.btn {
	.borderRadius;
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
.btn {
	-moz-border-radius: 5px;
	-webkit-border-radius: 5px;
	border-radius: 5px;
}
```
像 JavaScript 中 arguments一样，Mixins 也有这样一个变量：@arguments。@arguments 在 Mixins 中具是一个很特别的参数，当 Mixins 引用这个参数时，该参数表示所有的变量，很多情况下，这个参数可以省去你很多代码。
##### LESS 文件
```
.boxShadow(@x:0,@y:0,@blur:1px,@color:#000){
	-moz-box-shadow: @arguments;
	-webkit-box-shadow: @arguments;
	box-shadow: @arguments;
} 
#header {
	.boxShadow(2px,2px,3px,#f36);
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
#header {
	-moz-box-shadow: 2px 2px 3px#FF36;
	-webkit-box-shadow: 2px 2px 3px#FF36;
	box-shadow: 2px 2px 3px#FF36;
}
```
Mixins 是 LESS 中很重要的特性之一，我们这里也写了很多例子，看到这些例子你是否会有这样的疑问：当我们拥有了大量选择器的时候，特别是团队协同开发时，如何保证选择器之间重名问题？如果你是 java 程序员或 C++ 程序员，我猜你肯定会想到命名空间 Namespaces，LESS 也采用了命名空间的方法来避免重名问题，于是乎 LESS 在 mixins 的基础上扩展了一下，看下面这样一段代码：
##### LESS 文件
```
#mynamespace {
    .home {
   		...
    } 
    .user {
    	...
    } 
}
```
这样我们就定义了一个名为 mynamespace 的命名空间，如果我们要复用 user 这个选择器的时候，我们只需要在需要混入这个选择器的地方这样使用就可以了。#mynamespace >.user。
## 嵌套
在我们书写标准 CSS 的时候，遇到多层的元素嵌套这种情况时，我们要么采用从外到内的选择器嵌套定义，要么采用给特定元素加 CLASS 或 ID 的方式。在 LESS 中我们可以这样写：
##### HTML 片段
```
 <div id="home"> 
     <div id="top">top</div> 
     <div id="center"> 
         <div id="left">left</div> 
         <div id="right">right</div> 
     </div> 
 </div>
```
##### LESS 文件
```
#home{
	color : blue;
	width : 600px;
	height : 500px;
	border:outset;
 	#top{
        border:outset;
        width : 90%;
    } 
 	#center{
        border:outset;
        height : 300px;
        width : 90%;
            #left{
            border:outset;
            float : left;
            width : 40%;
        } 
            #right{
            border:outset;
            float : left;
            width : 40%;
        } 
    } 
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
#home {
	color: blue;
	width: 600px;
	height: 500px;
	border: outset;
} 
#home#top {
	border: outset;
	width: 90%;
} 
#home#center {
	border: outset;
	height: 300px;
	width: 90%;
} 
#home#center#left {
	border: outset;
	float: left;
	width: 40%;
} 
#home#center#right {
	border: outset;
	float: left;
	width: 40%;
}
```
从上面的代码中我们可以看出，LESS 的嵌套规则的写法是 HTML 中的 DOM 结构相对应的，这样使我们的样式表书写更加简洁和更好的可读性。同时，嵌套规则使得对伪元素的操作更为方便。
##### LESS 文件
```
a {
	color: red;
	text-decoration: none;
    &:hover { // 有 & 时解析的是同一个元素或此元素的伪类，没有 & 解析是后代元素
        color: black;
        text-decoration: underline;
    } 
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
 a {
	color: red;
	text-decoration: none;
} 
a:hover {
    color: black;
    text-decoration: underline;
}
```
## 运算及函数
在我们的 CSS 中充斥着大量的数值型的 value，比如 color、padding、margin 等，这些数值之间在某些情况下是有着一定关系的，那么我们怎样利用 LESS 来组织我们这些数值之间的关系呢？我们来看这段代码：
##### LESS 文件
```
@init:#111111;
@transition: @init*2;
.switchColor {
	color: @transition;
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
.switchColor {
	color:#222222;
}
```
上面的例子中使用 LESS 的 operation 是 特性，其实简单的讲，就是对数值型的 value（数字、颜色、变量等）进行加减乘除四则运算。同时 LESS 还有一个专门针对 color 的操作提供一组函数。下面是 LESS 提供的针对颜色操作的函数列表：
```
lighten(@color, 10%);// return a color which is 10% *lighter* than @color 
darken(@color, 10%);// return a color which is 10% *darker* than @color 
saturate(@color, 10%);// return a color 10% *more* saturated than @color 
desaturate(@color, 10%);// return a color 10% *less* saturated than @color 
fadein(@color, 10%);// return a color 10% *less* transparent than @color 
fadeout(@color, 10%);// return a color 10% *more* transparent than @color 
spin(@color, 10);// return a color with a 10 degree larger in hue than @color 
spin(@color, -10);// return a color with a 10 degree smaller hue than @color
```
PS: 上述代码引自 LESS CSS 官方网站
使用这些函数和 JavaScript 中使用函数一样。

##### LESS 文件

```
init:#f04615;
#body {
	background-color: fadein(@init, 10%);
}
```
经过编译生成的 CSS 文件如下：
##### CSS 文件
```
#body {
	background-color:#f04615;
}
```
从上面的例子我们可以发现，这组函数像极了 JavaScript 中的函数，它可以被调用和传递参数。这些函数的主要作用是提供颜色变换的功能，先把颜色转换成 HSL 色，然后在此基础上进行操作，LESS 还提供了获取颜色值的方法，在这里就不举例说明了。
LESS 提供的运算及函数特性适用于实现页面组件特性，比如组件切换时的渐入渐出。
## Comments（注释）

适当的注释是保证代码可读性的必要手段，LESS 对注释也提供了支持，主要有两种方式：单行注释和多行注释，这与 JavaScript 中的注释方法一样，我们这里不做详细的说明，只强调一点：LESS 中单行注释 (// 单行注释 ) 是不能显示在编译后的 CSS 中，所以如果你的注释是针对样式说明的请使用多行注释。
## 条件判断
 在上述“函数的使用”里面，我们看到Less支持“等于”的匹配方式，除此之外，Less里面还支持大于、小于等条件判断的语法，此之所谓“导引混合”。先来看看它的语法：
首先定义几个条件判断的“方法”
```js
.mixin (@a) when (lightness(@a) >= 50%) {
	background-color: black;
} 
.mixin (@a) when (lightness(@a) < 50%) {
	background-color: white;
} 
.mixin (@a) {
	color: @a;
}
```
然后调用该“方法”
```js
.class1 {
	.mixin(#ddd) 
} 
.class2 {
	.mixin(#555) 
}
```
编译结果如下：
```js
.class1 {
	background-color: black;
	color:#ddd;
} 
.class2 {
	background-color: white;
	color:#555;
}
```
**原理解析：when的语法不难理解，就是一个条件判断，关键是下面的color从哪里来的。原来在Less里面是一种混合调用的方式，也就是说，如果定义了三个函数mixin，分别对应有三个不同的条件，那么我们调用mixin函数的时候如果三个的条件都满足，那么它三个的结果都会得到。这就是为什么我们class1和class2得到如上结果。在Less里面所有的运算符有： >、 >=、 =、 =<、 <，除了这5个运算符，Less还提供了基于值类型进行判断的方法：iscolor()、isnumber()、isstring()、iskeyword()、isurl()等。用法如下：**
```js
.mixin (@a, @b: 0) when (isnumber(@b)) {
	... 
} 
.mixin (@a, @b: black) when (iscolor(@b)) {
	... 
}
```
除了上述条件表达式以外，Less还提供了and、not等逻辑表达式。基础用法如：
```js
.mixin (@b) when not (@b > 0) {
	background-color:blue;
}
```
## 导入(Importing)
less里面使用import将外部的less引入到本地less文件里面来。比如A.less里面定义了一个变量@aaa:red，而B.less文件里面也需要使用@aaa这个变量，这个时候怎么办呢？import派上用场了。
A.less内容如下：

```
@aaa:red;
```
B.less内容如下：
```
@import ‘A.less‘;
div{
	color:@aaa;
}
```
然后再html页面引入B.less文件，编译最终可以得到如下结果
```
div{
	color:@aaa;
}
```
有人可能要说，不就是引用其他less文件里面的变量吗，没啥用。可是你想过没有，由于项目里面模块很多，每个模块都有自己的less文件，如果没有import，怎么去统一调度呢。这点从bootstrap就可以看出来，当我们下载bootstrap3的源码，你会发现有很多的less文件，放在less文件夹里面，这些less文件分别对应着各个模块的样式。形如
![技术分享](http://www.ybao.org/data/upload/201801/f_31b53b2caea9f869d72f2301c4dc22a4.png)
各个模块的样式写完后，会有一个bootstrap.less文件，将其他所有的less文件都import进来，其内容如下：
```
// Core variables and mixins
@import "variables.less";
@import "mixins.less";
// Reset and dependencies
@import "normalize.less";
@import "print.less";
@import "glyphicons.less";
// Core CSS
@import "scaffolding.less";
@import "type.less";
@import "code.less";
@import "grid.less";
@import "tables.less";
@import "forms.less";
@import "buttons.less";
// Components
@import "component-animations.less";
@import "dropdowns.less";
@import "button-groups.less";
@import "input-groups.less";
@import "navs.less";
@import "navbar.less";
@import "breadcrumbs.less";
@import "pagination.less";
@import "pager.less";
@import "labels.less";
@import "badges.less";
@import "jumbotron.less";
@import "thumbnails.less";
@import "alerts.less";
@import "progress-bars.less";
@import "media.less";
@import "list-group.less";
@import "panels.less";
@import "responsive-embed.less";
@import "wells.less";
@import "close.less";
// Components w/ JavaScript
@import "modals.less";
@import "tooltip.less";
@import "popovers.less";
@import "carousel.less";
// Utility classes
@import "utilities.less";
@import "responsive-utilities.less";
```
然后我们编译bootstrap.less，就能将所有模块的less文件引入进来。
为了证明这点，我们来测试一把，在A.less里面加入如下内容：
```
@aaa:red;
@widthtest:200px;
.class2{
	background-color:green;
	border:5px solid red;
}
```
B.less内容如下：
```
@import ‘A.less‘;
div{
	color:@aaa;
	width:@widthtest;
	height:50px;
}
```
然后编译B.less得到的B.css文件内容如下：
```
.class2 {
	background-color: green;
	border: 5px solid red;
} 
div {
	color:#ff0000;
	width: 200px;
	height: 50px;
}
```
另外，import指令还包含了多种参数类型：

1.  @import (reference) "文件路径";
	​	将引入的文件作为样式库使用，因此文件中样式不会被直接编译为css样式规则。当前样式文件通过extend和mixins的方式引用样式库的内容。
2.  @import (inline) "文件路径";
	用于引入与less不兼容的css文件，通过inline配置告知编译器不对引入的文件进行编译处理，直接输出到最终输出。
3.  @import (less) "文件路径";
	 	默认使用该配置项，表示引入的文件为less文件。
4. @import (css) "文件路径";
	​	表示当前操作为CSS中的@import操作。当前文件会输出一个样式文件，而被引入的文件自身为一个独立的样式文件
5. @import (once) "文件路径";
	 	默认使用该配置项，表示对同一个资源仅引入一次。
6. @import (multiple) "文件路径";
	 	表示对同一资源可引入多次。

## 命名空间和访问器
有时候，出于组织的目的，或者为了提供一些封装，你会希望将你的mixins 组合在一起。在 Less 中做到这一点非常直观，假设你想在#bundle 下捆绑一些 mixins 和变量，以便稍候复用或者分发：
```js
#bundle {
 	.button {
        display: block;
        border: 1px solid black;
        background-color: grey;
        &:hover {
			background-color: white
        }
	}
    .tab {
        color:red;
    }
    .citation {
        color:blue;
    }
} 
```
现在如果我们想在#header a 中混合.button 类，那么我们可以这样做：
```js
#header a {
	color: orange;
	#bundle >.button;
}
```
## 循环
在 Less 中，mixin 可以被自己调用。当这种递归形式的 mixin 与 [Guard Expressions](http://less.bootcss.com/features/#mixin-guards-feature) 和 [Pattern Matching](http://less.bootcss.com/features/#mixins-parametric-feature-pattern-matching) 一起联合使用的话，就可以创造出各种迭代/循环结构。
案例：
```js
.loop(@counter) when (@counter > 0) {
	.loop((@counter - 1)); 	 	// next iteration
	width: (10px * @counter); 	 // code for each iteration
}
div {
	.loop(5); 	 // launch the loop
}
```
输出：
```js
div {
	width: 10px;
	width: 20px;
	width: 30px;
	width: 40px;
	width: 50px;
}
```
下面就是一个用于生成 CSS 栅格类的递归循环的实例：
```js
.generate-columns(4);
.generate-columns(@n, @i: 1) when (@i =< @n) {
  .column-@{i} {
    width: (@i * 100% / @n);
  }
  .generate-columns(@n, (@i + 1));
}
```
输出：
```js
.column-1 {
	width: 25%;
}
.column-2 {
	width: 50%;
}
.column-3 {
	width: 75%;
}
.column-4 {
	width: 100%;
}
```
## 合并
merge 特性能够聚合多个属性从而形成一个用逗号分隔的单一属性。merge 对于像 background 和 transform 这类属性非常有用。
案例：

```js
.mixin() {
	box-shadow+: inset 0 0 10px #555;
} 
.myclass {
	.mixin();
	box-shadow+: 0 0 20px black;
}
```
输出为
```js
.myclass {
	box-shadow: inset 0 0 10px #555, 0 0 20px black;
} 
```
为了避免意外的合并，merge 需要在每个需要合并的属性名后面添加一个 + 以作标示。
## 父选择符
```
a {
	color: blue;
	&:hover {
		color: green;
	}
}
```
results in:
```
a {
	color: blue;
} 
a:hover {
	color: green;
} 
```
另一个案例：
```js
.button {
 	&-ok {
        background-image: url("ok.png");
    }
 	&-cancel {
        background-image: url("cancel.png");
    }
 	&-custom {
        background-image: url("custom.png");
    }
}
```
输出:
```css
.button-ok {
	background-image: url("ok.png");
}
.button-cancel {
	background-image: url("cancel.png");
}
.button-custom {
	background-image: url("custom.png");
}
```