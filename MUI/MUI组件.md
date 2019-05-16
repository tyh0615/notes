# MUI组件

## accordion（折叠面板）

代码块激活字符:    <kbd>maccordion</kbd>

折叠面板从二级列表中演化而来，dom结构和二级列表类似，如下：

```
<div class="mui-content">
		<ul class="mui-table-view">
			<li class="mui-table-view-cell mui-collapse mui-active">
				<a class="mui-navigate-right" href="#">表单</a>
				<div class="mui-collapse-content">
					<form class="mui-input-group">
						<div class="mui-input-row">
							<label>input</label>
							<input type="text" placeholder="普通输入框">
						</div>
						<div class="mui-input-row">
							<label>input</label>
							<input type="text" class="mui-input-clear" placeholder="带清除按钮的输入">
						</div>
						<div class="mui-button-row">
							<button type="button" class="mui-btn mui-btn-primary">确认</button>
							<button type="button" class="mui-btn mui-btn-primary">取消</button>
						</div>
					</form>
				</div>
			</li>
			<li class="mui-table-view-cell mui-collapse">
				<a class="mui-navigate-right" href="#">面板2</a>
					<div class="mui-collapse-content">
					<p>面板2子内容</p>
				</div>
			</li>
			
		</ul>
	</div>
```

可以在折叠面板中放置任何内容；折叠面板默认收缩，若希望某个面板默认展开，只需要在包含`.mui-collapse`类的`li`节点上，增加`.mui-active`类即可；mui官网中的方法说明，使用的就是折叠面板控件。

## actionsheet（操作表）

代码块激活字符:    <kbd>mactionsheet</kbd>

actionsheet一般从底部弹出，显示一系列可供用户选择的操作按钮； actionsheet是从[popover](http://dev.dcloud.net.cn/mui/ui/#ui_popover)控件基础上演变而来，实际上就是一个固定从底部弹出的popover，故DOM结构和popove类似，只是需要在含`.mui-popover`类的节点上增加`.mui-popover-bottom`、`.mui-popover-action`类；
```
<div class="mui-content">
	<div id="sheet" class="mui-popover mui-popover-bottom mui-popover-action ">
		<!-- 可选择菜单 -->
		<ul class="mui-table-view">
		  <li class="mui-table-view-cell">
			<a href="#">菜单1</a>
		  </li>
		  <li class="mui-table-view-cell">
			<a href="#">菜单2</a>
		  </li>
		</ul>
		<!-- 取消菜单 -->
		<ul class="mui-table-view">
		  <li class="mui-table-view-cell">
			<a href="#sheet1"><b>取消</b></a>
		  </li>
		</ul>
	</div>
	<a href="#sheet" id="openSheet" class="mui-btn mui-btn-primary mui-btn-block">打开操作表</a>
</div>
```
>   //传入toggle参数，用户无需关心当前是显示还是隐藏状态，mui会自动识别处理；
>   mui('#sheet1').popover('toggle');

## badge（数字角标）

<kbd>mbadge</kbd>

数字角标一般和其它控件（列表、9宫格、选项卡等）配合使用，用于进行数量提示。 角标的核心类是`.mui-badge`，默认为实心灰色背景；同时，mui还内置了蓝色（blue）、绿色(green)、黄色(yellow)、红色(red)、紫色(purple)五种色系的数字角标，如下：


	<ul class="mui-table-view">
		<li class="mui-table-view-cell">
			<a class="mui-navigate-right">
				 Item 1
			</a>
			<span class="mui-badge mui-badge-primary">12</span>
		</li>
		<li class="mui-table-view-cell">
			<a class="mui-navigate-right">
				 Item 2
			</a>
			<span class="mui-badge mui-badge-success">123</span>
		</li>
		<li class="mui-table-view-cell">
			<a class="mui-navigate-right">
				Item 3
			</a>
			<span class="mui-badge mui-badge-warning">3</span>
		</li>
		<li class="mui-table-view-cell">
			<a class="mui-navigate-right">
				Item 4
			</a>
			<span class="mui-badge mui-badge-danger">45</span>
		</li>
		<li class="mui-table-view-cell">
			<a class="mui-navigate-right">
				Item 5
			</a>
			<span class="mui-badge mui-badge-purple">456</span>
		</li>
	</ul>

若无需底色，则增加`.mui-badge-inverted`类即可，如下：

```
<ul class="mui-table-view">
	<li class="mui-table-view-cell">
		<a class="mui-navigate-right">
			Item 1
		</a>
		<span class="mui-badge mui-badge-primary mui-badge-inverted">12</span>
	</li>
	<li class="mui-table-view-cell">
		<a class="mui-navigate-right">
			Item 2
		</a>
		<span class="mui-badge mui-badge-success mui-badge-inverted">123</span>
	</li>
</ul>
```

## button（按钮）

代码块激活字符:     <kbd>mbutton</kbd>

mui默认按钮为灰色，另外还提供了蓝色（blue）、绿色(green)、黄色(yellow)、红色(red)、紫色(purple)五种色系的按钮，五种色系对应五种场景，分别为primary、success、warning、danger、royal；使用`.mui-btn`类即可生成一个默认按钮，继续添加`.mui-btn-颜色值`或`.mui-btn-场景`可生成对应色系的按钮，例如：通过`.mui-btn-blue`或`.mui-btn-primary`均可生成蓝色按钮；

### 普通按钮

在button节点上增加`.mui-btn`类，即可生成默认按钮；若需要其他颜色的按钮，则继续增加对应class即可，比如`.mui-btn-blue`即可变成蓝色按钮

```
<button type="button" class="mui-btn">默认</button>
<button type="button" class="mui-btn mui-btn-primary">蓝色</button>
<button type="button" class="mui-btn mui-btn-success">绿色</button>
<button type="button" class="mui-btn mui-btn-warning">黄色</button>
<button type="button" class="mui-btn mui-btn-danger">红色</button>
<button type="button" class="mui-btn mui-btn-royal">紫色</button> 
```

若希望无底色、有边框的按钮，仅需增加`.mui-btn-outlined`类即可，代码如下：

	<button type="button" class="mui-btn mui-btn-primary mui-btn-outlined">蓝色</button>
	<button type="button" class="mui-btn mui-btn-success mui-btn-outlined">绿色</button>
	<button type="button" class="mui-btn mui-btn-warning mui-btn-outlined">黄色</button>
### 加载中按钮

[mui v3.4 ](https://github.com/dcloudio/mui)版新增加载中按钮样式,目前提供通过 `JS API `切换 loading和reset状态,可以灵活操作适应多种场景

| 属性名                     | 作用                                                         |
| -------------------------- | ------------------------------------------------------------ |
| data-loading-text          | loading 状态显示的文案,默认为: `loading`                     |
| data-loading-icon          | loading 状态显示的icon,默认为`mui-spinner`或`mui-spinner mui-spinner-white`（根据按钮样式自动识别），为空表示不使用icon |
| data-loading-icon-position | loading 状态显示的icon的位置,支持left/right默认left          |

```
<button type="button" data-loading-icon="mui-spinner mui-spinner-custom" class="mui-btn mui-btn-primary">确认</button>
<button type="button" data-loading-text="提交中" class="mui-btn">确认</button>
<button type="button" data-loading-icon-position="right" class="mui-btn">确认</button>
```

### js api

```
mui(btnElem).button('loading');//切换为loading状态

mui(btnElem).button('reset');//切换为reset状态(即重置为原始的button)
```

```
<button type="button" data-loading-icon="mui-spinner mui-spinner-custom" class="mui-btn mui-btn-primary">确认</button>
<script type="text/javascript">
    mui(document.body).on('tap', '.mui-btn', function(e) {
        mui(this).button('loading');
        setTimeout(function() {
            mui(this).button('reset');
        }.bind(this), 2000);
    });
</script>
```

## cardview（卡片视图）

卡片视图常用于展现一段完整独立的信息，比如一篇文章的预览图、作者信息、点赞数量等，如下是一个卡片demo示例；

![1537240937975](F:\MUI study\img\1537240937975.png)

使用`mui-card`类即可生成一个卡片容器，卡片视图主要有页眉、内容区、页脚三部分组成，结构如下：

```
<div class="mui-card">
	<!--页眉，放置标题-->
	<div class="mui-card-header">页眉</div>
	<!--内容区-->
	<div class="mui-card-content">内容区</div>
	<!--页脚，放置补充信息或支持的操作-->
	<div class="mui-card-footer">页脚</div>
</div>
```

卡片页眉及内容区，均支持放置图片； 页眉放置图片的话，需要在`.mui-card-header`节点上增加`.mui-card-media`类，然后设置一张图片做背景图即可，代码如下：

```
<div class="mui-card-header mui-card-media" style="height:40vw;background-image:url(../images/cbd.jpg)"></div>
```

若希望在页眉放置更丰富的信息，比如头像、主标题、副标题，则需使用`.mui-media-body`类，示例代码如下：

```
<div class="mui-card">
	<div class="mui-card-header mui-card-media">页眉<br>
		<img src="img/1537242306153.png" >
		<div class="mui-media-body">
			Dawn
			<p>发表于 2018-06-30 15:30</p>
		</div>
	</div>
	<div class="mui-card-content">内容区<br>
		<img src="img/1537240937975.png" >
	</div>
	<div class="mui-card-footer">页脚
	<br>
	<img src="img/1537242306153.png" >
	<div class="mui-media-body">
		Dawn
		<p>发表于 2018-06-30 15:30</p>
	</div>
	</div>
</div>

```

## checkbox（复选框）

代码块激活字符: <kbd>mckeckbox</kbd>

checkbox常用于多选的情况，比如批量删除、添加群聊等；默认checkbox在右侧显示，若希望在左侧显示，只需增加`.mui-left`类即可;若要禁用checkbox，只需在checkbox上增加disabled属性即可；

**DOM结构**

```
<div class="mui-input-row mui-checkbox ">
	<label>Checkbox</label>
	<input name="Checkbox" type="checkbox" checked>
</div>
<div class="mui-input-row mui-checkbox ">
	<label>Checkbox</label>
	<input name="Checkbox" type="checkbox" checked>
</div>
<div class="mui-input-row mui-checkbox mui-disabled">
	<label>disabled checkbox</label>
	<input name="checkbox" type="checkbox" disabled="disabled">
</div>
<div class="mui-input-row mui-checkbox mui-left">
  <label>checkbox</label>
  <input name="checkbox1" type="checkbox" checked >
</div>
```

## dialog（对话框）

代码块激活字符:     <kbd>mdalert</kbd><kbd>mdconfirm</kbd><kbd>mdprompt</kbd><kbd>mdtoast</kbd><kbd>mdclosepopup</kbd><kbd>mdclosepopups</kbd>

创建并显示对话框，弹出的对话框为`非阻塞模式`，用户点击对话框上的按钮后关闭( h5模式的对话框也可通过 closepopup关闭 )，并通过callback函数返回用户点击按钮的索引值或输入框中的值。

### Dialog 组件包含:

| 组件名  | 作用       |
| ------- | ---------- |
| alert   | 警告框     |
| confirm | 确认框     |
| prompt  | 输入对话框 |
| toast   | 消息提示框 |

mui会根据`ua`判断,弹出原生对话框还是h5绘制的对话框,在基座中默认会弹出原生对话框,可以配置type属性,使得弹出h5模式对话框

**两者区别:**

1.  原生对话框可以跨webview
2.  h5对话框样式统一而且可以修改对话框属性或样式

mui v3.0 版本(含)以上的dialog控件支持换行（\n）显示

**A		.alert( message, title, btnValue, callback [, type] )**

**B		.confirm( message, title, btnValue, callback [, type])**

**C		.prompt( message, placeholder, title, btnValue, callback[, type] )**

-   **message**

    Type: String

    提示对话框上显示的内容

-   **title**

    Type: String

    提示对话框上显示的标题

-   **btnValue**

    Type: String

    提示对话框上按钮显示的内容

-   **callback**

    Type: Function

    提示对话框上关闭后的回调函数

-   **type**

    Value: 'div'

    是否使用h5绘制的对话框



如果有定制对话框样式的需求( [只能修改h5模式对话框](javascript:void(0);))可以在mui.css中修改`.mui-popup`类下的样式

如果需要修改`DOM`结构可以按照以下方式处理.

```
//修改弹出框默认input类型为password 
mui.prompt('text','deftext','title',['true','false'],null,'div') 
document.querySelector('.mui-popup-input input').type='password' 
```

**D		.toast( message [,options])**

message:`'String' - 消息框显示的文字内容`

  options:` {JSON}  - 提示消息的参数`

**options 参数需要mui v3.5+支持**

| 参数     | 说明                                | 说明                                                         |
| -------- | ----------------------------------- | ------------------------------------------------------------ |
| duration | 持续显示时间,默认值 `short`(2000ms) | 支持 **整数值** 和 **String** , String可选: `long`(3500ms),`short`(2000ms) |
| type     | 强制使用mui消息框(div模式)          | `'div'`                                                      |

```
 mui.toast('登陆成功',{ duration:'long', type:'div' }) 
```

**E		.closePopup()(只能关闭h5模式的对话框)	**			关闭最后一次弹出的对话框
**F		.closePopups()(只能关闭h5模式的对话框)**			关闭所有对话框

## gallery（图片轮播）

代码块激活字符:    <kbd>mslider</kbd>

图片轮播继承自[slide插件](http://dev.dcloud.net.cn/mui/ui/#slide)，因此其DOM结构、事件均和slide插件相同；

**DOM结构**

默认不支持循环播放，DOM结构如下：

```
<div class="mui-slider">
  <div class="mui-slider-group">
    <div class="mui-slider-item"><a href="#"><img src="1.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="2.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="3.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="4.jpg" /></a></div>
  </div>
</div>
```

假设当前图片轮播中有1、2、3、4四张图片，从第1张图片起，依次向左滑动切换图片，当切换到第4张图片时，继续向左滑动，接下来会有两种效果：

-   支持循环：左滑，直接切换到第1张图片；
-   不支持循环：左滑，无反应，继续显示第4张图片，用户若要显示第1张图片，必须连续向右滑动切换到第1张图片；

当显示第1张图片时，继续右滑是否显示第4张图片，是同样问题；这个问题的实现需要通过

```
.mui-slider-loop
```

类及DOM节点来控制；

若要支持循环，则需要在`.mui-slider-group`节点上增加`.mui-slider-loop`类，同时需要重复增加2张图片，图片顺序变为：4、1、2、3、4、1，代码示例如下：

```
<div class="mui-slider">
  <div class="mui-slider-group mui-slider-loop">
    <!--支持循环，需要重复图片节点-->
    <div class="mui-slider-item mui-slider-item-duplicate"><a href="#"><img src="4.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="1.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="2.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="3.jpg" /></a></div>
    <div class="mui-slider-item"><a href="#"><img src="4.jpg" /></a></div>
    <!--支持循环，需要重复图片节点-->
    <div class="mui-slider-item mui-slider-item-duplicate"><a href="#"><img src="1.jpg" /></a></div>
  </div>
</div>
```

 **JS Method**

mui框架内置了图片轮播插件，通过该插件封装的JS API，用户可以设定是否自动轮播及轮播周期，如下为代码示例：

```
//获得slider插件对象
var gallery = mui('.mui-slider');
gallery.slider({
  interval:5000//自动轮播周期，若为0则不自动播放，默认为0；
});
```

因此若希望图片轮播不要自动播放，而是用户手动滑动才切换，只需要通过如上方法，将interval参数设为0即可。

若要跳转到第x张图片，则可以使用图片轮播插件的gotoItem方法，例如：

```
//获得slider插件对象
var gallery = mui('.mui-slider');
gallery.slider().gotoItem(index);//跳转到第index张图片，index从0开始；
```

**注意：**mui框架会默认初始化当前页面的图片轮播组件；若轮播组件内容为js动态生成时（比如通过ajax动态获取的营销信息），则需要在[动态生成完整DOM](jabascript:void(0);) (包含`mui-slider`下所有DOM结构) 后，手动调用图片轮播的初始化方法；代码如下：

```
//获得slider插件对象
var gallery = mui('.mui-slider');
gallery.slider({
  interval:5000//自动轮播周期，若为0则不自动播放，默认为0；
});
```



## grid（栅格）

代码块激活字符:   <kbd>row</kbd><kbd>mcolsm</kbd><kbd>mcolxs</kbd>

**栅格系统简介：**

MUI 提供了非常简单实用的`12`列响应式栅格系统。使用时只需在外围容器上添加`.mui-row`，在列上添加 `.mui-col-[sm|xs]-[1-12]`，即可

**栅格参数:**

| 尺寸           | 超小屏幕(<400px)(Extrasmall) | 小屏幕(≥400px) Small |
| -------------- | ---------------------------- | -------------------- |
| 类前缀         | `.mui-col-xs-[1-12]`         | `.mui-col-sm-[1-12]` |
| 列（column）数 | 12                           |                      |
| 可嵌套         | 是                           |                      |

**实例:**

左侧:通过定义`.mui-col-sm-6`类在大屏(≥400px)设备上会展现为并排的两列,而`.mui-col-xs-12`在小屏(＜400px)设备上会覆盖之前定义的类展现为水平排列

```
<div class="mui-content">
    <div class="mui-row">
        <div class="mui-col-sm-6 mui-col-xs-12">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1    
                </a>
            </li>
        </div>
        <div class="mui-col-sm-6 mui-col-xs-12">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1
                </a>
            </li>
        </div>
    </div>
</div>
```

**实例:多余的列将会另起一行排列**

左侧:如果在一个`.mui-row`内包含的列（column）大于12个,包含多余列（column）的元素将作为一个整体单元被另起一行排列。

右侧:如果不足12个列将不会撑满整个`.mui-row`容器

```
<div class="mui-content">
    <div class="mui-row">
        <div class="mui-col-sm-8">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1    
                </a>
            </li>
        </div>
        <div class="mui-col-sm-6">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1
                </a>
            </li>
        </div>
    </div>
</div>
```

 **实例:通过为`列`设置`padding` 属性，从而创建列与列之间的间隔**

两列之间白色区域为左侧列的`padding`

```
<div class="mui-content">
    <div class="mui-row">
        <div class="mui-col-sm-6" style="padding-right: 20px;">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1    
                </a>
            </li>
        </div>
        <div class="mui-col-sm-6">
            <li class="mui-table-view-cell">
                <a class="mui-navigate-right">
                    Item 1
                </a>
            </li>
        </div>
    </div>
</div>
```

## icon(图标)

代码块激活字符:   <kbd>micon</kbd>

用时，只需要在`span`节点上分别增加`.mui-icon`、`.mui-icon-name`两个类即可（name为图标名称，例如：weixin、weibo等），如下代码即可显示一个微信图标：

```
<span class="mui-icon mui-icon-weixin"></span>
```

## ipnut (表单)

**基本说明:**

所有包裹在`.mui-input-row` 类中的 input、textarea等元素都将被默认设置宽度属性为`width: 100%;` 。 将 label 元素和上述控件控件包裹在`.mui-input-group`中可以获得最好的排列。

```
<form class="mui-input-group">
    <div class="mui-input-row">
        <label>用户名</label>
    <input type="text" class="mui-input-clear" placeholder="请输入用户名">
    </div>
    <div class="mui-input-row">
        <label>密码</label>
        <input type="password" class="mui-input-password" placeholder="请输入密码">
    </div>
    <div class="mui-button-row">
        <button type="button" class="mui-btn mui-btn-primary" >确认</button>
        <button type="button" class="mui-btn mui-btn-danger" >取消</button>
    </div>
</form>
```

**输入增强:**

mui目前提供的输入增强包括：**快速删除**、**语音输入** *5+ only 和**密码框显示隐藏密码。**

-   快速删除：只需要在input控件上添加`.mui-input-clear`类，当input 控件中有内容时，右侧会有一个删除图标，点击会清空当前input的内容；

```
<form class="mui-input-group">
    <div class="mui-input-row">
        <label>快速删除</label>
        <input type="text" class="mui-input-clear" placeholder="请输入内容">
    </div>
</form>
```

-   搜索框：在`.mui-input-row`同级添加`.mui-input-search` 类，就可以使用search控件

```
<div class="mui-input-row mui-search">
    <input type="search" class="mui-input-clear" placeholder="">
</div>
```

-   语音输入[*5+ only](javascript:void(0);)：为了方便快速输入，mui集成了 [HTML5+的语音输入](http://www.html5plus.org/doc/zh_cn/speech.html)，只需要在对应input控件上添加`.mui-input-speech` 类，就可以在5+环境下使用语音输入

    ```
    <div class="mui-input-row">
    	<label>Input</label>
    	<input type="text" class="mui-input-speech mui-input-clear" placeholder="语音输入">
    </div>
    ```

-   密码框：给input元素添加`.mui-input-password`类即可使用

    ```
    <div class="mui-input-row">
        <label>密码</label>
        <input type="password" class="mui-input-password" placeholder="请输入密码">
    </div>
    ```

**初始化：**

mui在mui.init()中会自动初始化基本控件,但是动态添加的Input组件需要重新进行初始化

## list（列表）

代码块激活字符:    <kbd>mlist</kbd>

**普通列表**

列表是常用的UI控件，mui封装的列表组件比较简单，只需要在`ul`节点上添加`.mui-table-view`类、在`li`节点上添加`.mui-table-view-cell`类即可，如下为示例代码

```
<ul class="mui-table-view">
    <li class="mui-table-view-cell">Item 1</li>
    <li class="mui-table-view-cell">Item 2</li>
    <li class="mui-table-view-cell">Item 3</li>
</ul>
```

**自定义列表高亮颜色**

点击列表，对应列表项显示灰色高亮，若想自定义高亮颜色，只需要重写`.mui-table-view-cell.mui-active`即可，如下：

```
/*点击变蓝色高亮*/
.mui-table-view-cell.mui-active{
	background-color: #0062CC;
	color:white;
}
```

**右侧添加导航箭头**

若右侧需要增加导航箭头，变成导航链接，则只需在`li`节点下增加`a`子节点，并为该`a`节点增加`.mui-navigate-right`类即可，如下：

```
<ul class="mui-table-view">
    <li class="mui-table-view-cell">
        <a class="mui-navigate-right">Item 1</a>
    </li>
    <li class="mui-table-view-cell">
        <a class="mui-navigate-right">Item 2</a>
    </li>
    <li class="mui-table-view-cell">
        <a class="mui-navigate-right">Item 3</a>
    </li>
</ul>
```

**右侧添加数字角标等控件**

mui支持将数字角标、按钮、开关等控件放在列表中；mui默认将数字角标放在列表右侧显示，代码如下：

```
<ul class="mui-table-view">
    <li class="mui-table-view-cell">Item 1 
        <span class="mui-badge mui-badge-primary">11</span>
    </li>
    <li class="mui-table-view-cell">Item 2 
        <span class="mui-badge mui-badge-success">22</span>
    </li>
    <li class="mui-table-view-cell">Item 3 
        <span class="mui-badge">33</span>
    </li>
</ul>
```

**media list（图文列表）**

图文列表继承自列表组件，主要添加了`.mui-media`、`.mui-media-object`、`.mui-media-body`、`.mui-pull-left/right`几个类，如下为示例代码

```
<ul class="mui-table-view">
    <li class="mui-table-view-cell mui-media">
        <a href="javascript:;">
            <img class="mui-media-object mui-pull-left" src="../images/shuijiao.jpg">
            <div class="mui-media-body">
                幸福
                <p class='mui-ellipsis'>能和心爱的人一起睡觉，是件幸福的事情；可是，打呼噜怎么办？</p>
            </div>
        </a>
    </li>
    <li class="mui-table-view-cell mui-media">
        <a href="javascript:;">
            <img class="mui-media-object mui-pull-left" src="../images/muwu.jpg">
            <div class="mui-media-body">
                木屋
                <p class='mui-ellipsis'>想要这样一间小木屋，夏天挫冰吃瓜，冬天围炉取暖.</p>
            </div>
        </a>
    </li>
    <li class="mui-table-view-cell mui-media">
        <a href="javascript:;">
            <img class="mui-media-object mui-pull-left" src="../images/cbd.jpg">
            <div class="mui-media-body">
                CBD
                <p class='mui-ellipsis'>烤炉模式的城，到黄昏，如同打翻的调色盘一般.</p>
            </div>
        </a>
    </li>
</ul>
```

## mask(遮罩蒙版)

代码块激活字符:    <kbd>mmask</kbd>

在popover、侧滑菜单等界面，经常会用到蒙版遮罩；比如popover弹出后，除popover控件外的其它区域都会遮罩一层蒙版，用户点击蒙版不会触发蒙版下方的逻辑，而会关闭popover同时关闭蒙版；再比如侧滑菜单界面，菜单划出后，除侧滑菜单之外的其它区域都会遮罩一层蒙版，用户点击蒙版会关闭侧滑菜单同时关闭蒙版。

遮罩蒙版常用的操作包括：创建、显示、关闭，如下代码：

```
var mask = mui.createMask(callback);//callback为用户点击蒙版时自动执行的回调；
mask.show();//显示遮罩
mask.close();//关闭遮罩
```

**注意：**关闭遮罩仅会关闭，不会销毁；关闭之后可以再次调用`mask.show();`打开遮罩；

mui默认的蒙版遮罩使用`.mui-backdrop`类定义（如下代码），若需自定义遮罩效果，只需覆盖定义`.mui-backdrop`即可；

```
.mui-backdrop {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 998;
    background-color: rgba(0,0,0,.3);
}
```

## numbox(数字输入框)

代码块激活字符:    <kbd>mnumbox</kbd>

mui提供了数字输入框控件，可直接输入数字，也可以点击“+”、“-”按钮变换当前数值；默认numbox控件dom结构比较简单，如下：

```
<div class="mui-numbox">
  <!-- "-"按钮，点击可减小当前数值 -->
  <button class="mui-btn mui-numbox-btn-minus" type="button">-</button>
  <input class="mui-numbox-input" type="number" />
  <!-- "+"按钮，点击可增大当前数值 -->
  <button class="mui-btn mui-numbox-btn-plus" type="button">+</button>
</div>
```

可通过`data-numbox*`自定义属性设置数字输入框的参数，如下：

**Data API**

| 属性名           | 作用                                        |
| ---------------- | ------------------------------------------- |
| data-numbox-min  | 输入框允许使用的最小值，默认无限制          |
| data-numbox-max  | 输入框允许使用的最大值，默认无限制          |
| data-numbox-step | 每次点击“+”、“-”按钮变化的步长，默认步长为1 |

**示例：**设置取值范围为0~100，每次变化步长为10，则代码如下
```
<div class="mui-numbox" data-numbox-step='10' data-numbox-min='0' data-numbox-max='100'>
  <button class="mui-btn mui-numbox-btn-minus" type="button">-</button>
  <input class="mui-numbox-input" type="number" />
  <button class="mui-btn mui-numbox-btn-plus" type="button">+</button>
</div>
```

**JS API**

| 方法名               | 作用                                               | 示例                                                         |
| -------------------- | -------------------------------------------------- | ------------------------------------------------------------ |
| `getValue()`         | 获取当前值                                         | [getValue()](http://dev.dcloud.net.cn/mui/ui/#getValue)      |
| `setValue(Value)`    | 动态设置新值 `Int`                                 | [setValue(Value)](http://dev.dcloud.net.cn/mui/ui/#setValue) |
| `setOption(options)` | 更新选项,可取值: `min(Int)`,`step(Int)`,`max(Int)` | [setOption(options)](http://dev.dcloud.net.cn/mui/ui/#setOption) |

示例:getValue()

```
mui(Selector).numbox().getValue()
```

示例: setValue()

```
mui(Selector).numbox().setValue(5)
```

示例: setOption()		设置步长(step)为5

```
mui(Selector).numbox().setOption('step',5)
```

初始化：
mui在mui.init()中会自动初始化基本控件,但是 **动态添加的Numbox组件需要手动初始化**

初始化：
mui在mui.init()中会自动初始化基本控件,但是 动态添加的Numbox组件需要手动初始化

mui(Selector).numbox()

## offcanvas(侧滑导航)

代码块激活字符:    <kbd>moffcanvas</kbd>

mui提供了两种侧滑导航实现：webview模式和div模式，两种模式各有优劣，适用于不同的场景。

### webview模式

主页面和菜单内容在不同的webview中，两个页面根据内容需求分别组织DOM结构，mui对其DOM结构无特殊要求，故其有如下优点：

-   菜单内容是单独的webview，故可被多个页面复用；
-   菜单内容在单独的webview中，菜单区域的滚动不影响主界面，故可使用原生滚动，滚动更为流畅；

另一方面，webview模式也有其缺点：

-   不支持拖动手势（跟手拖动）；
-   主页面、菜单不同webview实现，因此若需交互（如：点击菜单触发主页面内容变化），需使用[自定义事件](http://dev.dcloud.net.cn/mui/ui/#customevent)实现跨webview通讯；

### div模式

主页面和菜单内容在同一个webview下，嵌套在特定结构的div中，通过div的移动动画模拟菜单移动；故该模式有如下优点：

-   支持拖动手势（跟手拖动）；
-   主页面、菜单在一个页面中，可通过JS轻松实现两者交互（如：点击菜单触发主页面内容变化），没有跨webview通讯的烦恼；

另一方面，div模式也有其缺点：

-   不支持菜单内容在多页面的复用，需每个页面都生成对应的菜单节点；
-   主界面和菜单内容的滚动互不影响，因此会使用div区域滚动，在低端Android手机且滚动内容较多时，可能会稍显卡顿；

div模式支持不同的动画效果，每种动画效果需遵从不同的DOM构造；下面我们以右滑菜单为例（左滑菜单仅需将菜单父节点上的`mui-off-canvas-left`换成`mui-off-canvas-right`即可），说明每种动画对应的DOM结构。

**动画1：主界面移动、菜单不动**

```
<!-- 侧滑导航根容器 -->
<div class="mui-off-canvas-wrap mui-draggable">
  <!-- 菜单容器 -->
  <aside class="mui-off-canvas-left">
    <div class="mui-scroll-wrapper">
      <div class="mui-scroll">
        <!-- 菜单具体展示内容 -->
        ...
      </div>
    </div>
  </aside>
  <!-- 主页面容器 -->
  <div class="mui-inner-wrap">
    <!-- 主页面标题 -->
    <header class="mui-bar mui-bar-nav">
      <a class="mui-icon mui-action-menu mui-icon-bars mui-pull-left"></a>
      <h1 class="mui-title">标题</h1>
    </header>
    <div class="mui-content mui-scroll-wrapper">
      <div class="mui-scroll">
        <!-- 主界面具体展示内容 -->
        ...
      </div>
    </div>  
  </div>
</div>
```

**动画2：缩放式侧滑（类手机QQ）**

该种动画要求的DOM结构和动画1的DOM结构基本相同，唯一差别就是需在侧滑导航根容器class上增加一个`mui-scalable`类

**动画3：主界面不动、菜单移动**

该种动画要求的DOM结构和动画1的DOM结构基本相同，唯一差别就是需在侧滑导航根容器class上增加一个`mui-slide-in`类

**动画4：主界面、菜单同时移动**

该种动画要求的DOM结构较特殊，需将菜单容器放在主页面容器之下

```
<!-- 侧滑导航根容器 -->
<div class="mui-off-canvas-wrap mui-draggable">
  <!-- 主页面容器 -->
  <div class="mui-inner-wrap">
     <!-- 菜单容器 -->
    <aside class="mui-off-canvas-left">
      <div class="mui-scroll-wrapper">
        <div class="mui-scroll">
          <!-- 菜单具体展示内容 -->
          ...
        </div>
      </div>
    </aside>
    <!-- 主页面标题 -->
    <header class="mui-bar mui-bar-nav">
      <a class="mui-icon mui-action-menu mui-icon-bars mui-pull-left"></a>
      <h1 class="mui-title">标题</h1>
    </header>
    <!-- 主页面内容容器 -->
    <div class="mui-content mui-scroll-wrapper">
      <div class="mui-scroll">
        <!-- 主界面具体展示内容 -->
        ...
      </div>
    </div>  
  </div>
</div>
```

### JS API

mui支持多种方式操作div模式的侧滑菜单：

-   1、在界面上拖动操作（drag）；
-   2、点击含有`mui-action-menu`类的控件；
-   3、Android手机按menu键；
-   4、通过JS API触发，

如下：

可以有两种调用方式`mui('.mui-off-canvas-wrap').offCanvas('show');`

或`mui('.mui-off-canvas-wrap').offCanvas().show();`

以下方法皆支持上述两种调用方式

| 方法名   | 作用 |
| -------- | ---- |
| show()   | 显示 |
| close()  | 隐藏 |
| toggle() | 切换 |

### 事件监听

你可以通过一下方式监听侧滑菜单显示隐藏

| 事件名 | 作用 |
| ------ | ---- |
| shown  | 显示 |
| hidden | 隐藏 |

```
document.querySelector('.mui-off-canvas-wrap').addEventListener('shown',function (event) {
    //...
})
```

也可以通过`isShown()`方法判断是否为显示状态

```
mui('.mui-off-canvas-wrap').offCanvas().isShown();
```

`isShown()` 方法也可以传递 `direction(方向)` 参数([非必选!!](javascript:void(0);))进而可以判断左右侧滑

```
mui('.mui-off-canvas-wrap').offCanvas().isShown('left');//true
```

## popover(弹出菜单)

代码块激活字符:    <kbd>mpopover</kbd>

mui框架内置了弹出菜单插件，弹出菜单显示内容不限，但必须包裹在一个含`.mui-popover`类的div中，如下即为一个弹出菜单内容：

```
<div id="popover" class="mui-popover">
  <ul class="mui-table-view">
    <li class="mui-table-view-cell"><a href="#">Item1</a></li>
    <li class="mui-table-view-cell"><a href="#">Item2</a></li>
    <li class="mui-table-view-cell"><a href="#">Item3</a></li>
    <li class="mui-table-view-cell"><a href="#">Item4</a></li>
    <li class="mui-table-view-cell"><a href="#">Item5</a></li>
  </ul>
</div>
```

要显示、隐藏如上菜单，mui推荐使用锚点方式，例如：

```
<a href="#popover" id="openPopover" class="mui-btn mui-btn-primary mui-btn-block">打开弹出菜单</a>
```

点击如上定义的按钮，即可显示弹出菜单，再次点击弹出菜单之外的其他区域，均可关闭弹出菜单；这种使用方式最为简洁。

若希望通过js的方式控制弹出菜单，则通过如下一个方法即可：

```
mui('.bottomPopover').popover(status[,anchor]);
```

**status**

-   **'show'**		显示popover
-   **'hide'**		隐藏popover
-   **'toggle'**		自动识别处理显示隐藏状态

```js
mui('.bottomPopover').popover('toggle');//show hide toggle
```

**[anchor]**

-   **anchorElement**			锚点元素

```
//传入toggle参数，用户也无需关心当前是显示还是隐藏状态，mui会自动识别处理；
mui('.mui-popover').popover('toggle',document.getElementById("openPopover"));
```

## picker（选择器）

代码块激活字符:     <kbd>mpoppicker</kbd><kbd>mdtpicker</kbd>

mui框架扩展了pipcker组件,可用于弹出选择器,在各平台上都有统一表现.poppicker和dtpicker是对picker的具体实现

[*](javascript:void(0);)poppicker组件依赖`mui.picker.js/.css` `mui.poppicker.js/.css`请务必在mui.js/css后中引用,也可统一引用 压缩版本:`mui.picker.min.js`

### popPicker

适用于弹出单级或多级选择器

**快速体验**

**通过new mui.PopPicker()初始化popPicker组件**

```
 var picker = new mui.PopPicker(); 
```

**给picker对象添加数据**

setData() 支持数据格式为: 

数组

```
 picker.setData([{value:'zz',text:'智子'}]); 
```

**显示picker**

```
 picker.show( SelectedItemsCallback ) 
```

**实例**

```
 var picker = new mui.PopPicker();
 picker.setData([{value:'zz',text:'智子'}]);
 picker.show(function (selectItems) {
    console.log(selectItems[0].text);//智子
    console.log(selectItems[0].value);//zz 
  })
```

**API详解**

-   new PopPicker({PopPicker.options}})

    -   **layer**

        Type: [Int](javascript:void(0);)

        picker显示列数

    -   **buttons**

        Type: [Array](javascript:void(0);)

        picker显示按钮

        如:`new mui.PopPicker({buttons:['cancle','ok']})`

-   setData([data])

    -   参数:**data**

        Type: [Array](javascript:void(0);)

        填充数据

        如:`picker.setData([{value:'zz',text:'智子'}])`

        data格式

### 设置默认值

`PopPicker `创建实例并填充数据后，可以设定每个层级的选中项，因为 PopPicker 是支持多层级联的，所以，可通过` instance.pickers[index] `拿到指定层级的实例，然后通过`setSelectedIndex()`和`setSelectedValue()`两个方法,设定指定层级的选中项，如下代码供参考:



```
var picker = new mui.PopPicker();
picker.setData([{
    value: "first",
    text: "第一项"
}, {
    value: "second",
    text: "第一项"
}, {
    value: "third",
    text: "第三项"
}, {
    value: "fourth",
    text: "第四项"
}, {
    value: "fifth",
    text: "第五项"
}])
//picker.pickers[0].setSelectedIndex(4, 2000);
picker.pickers[0].setSelectedValue('fourth', 2000);
picker.show(function(SelectedItem) {
	console.log(SelectedItem);
})
```

 **[*](javascript:void(0);)如果设置多级默认值可依次获取每一层级Picker对象并设置默认值,如下:**

```
var picker = new mui.PopPicker({
    layer: 2
});
    picker.setData([{
        value: '110000',
        text: '北京市',
        children: [{
                value: "110101",
                text: "东城区"
        }]
    }, {
        value: '120000',
        text: '天津市',
        children: [{
	        value: "120101",
            text: "和平区"
        }, {
            value: "120102",
            text: "河东区"
        }, {
            value: "120104",
            text: "南开区"
        }
        ]
    }])
picker.pickers[0].setSelectedIndex(1);
picker.pickers[1].setSelectedIndex(1);
picker.show(function(SelectedItem) {
	console.log(SelectedItem);
})
```

-   setSelectedIndex(index[, duration, callback])

    -   参数:**index**

        Type: [Number](javascript:void(0);)

        指定列表选中项

        如:`picker.pickers[0].setSelectedIndex(4)`

    -   参数:**duration**

        Type: [Number](javascript:void(0);)

        过渡效果持续时间(` ms `)

        如:`picker.pickers[0].setSelectedIndex(4,200)`

    -   参数:**callback**

        Type: [FUnction](javascript:void(0);)

        设置成功回调

        如:`picker.pickers[0].setSelectedIndex(4,200,function(){})`



        var picker = new mui.PopPicker();
        picker.setData([{
            value: "first",
            text: "第一项",
        }, {
            value: "second",
            text: "第一项"
        }, {
            value: "third",
            text: "第三项"
        }, {
            value: "fourth",
            text: "第四项"
        }, {
            value: "fifth",
            text: "第五项"
        }])
        picker.pickers[0].setSelectedIndex(4, 2000);
        picker.show(function(SelectedItem) {
            console.log(SelectedItem);
        })

-   setSelectedValue(value[, duration, callback])

    -   参数:**value**

        Type: [String](javascript:void(0);)

        指定列表选中项

        如:`picker.pickers[0].setSelectedValue('fourth')`

    -   参数:**duration**

        Type: [Number](javascript:void(0);)

        渡效果持续时间(` ms `)

        如:`picker.pickers[0].setSelectedValue('fourth',200)`

    -   参数:**callback**

        Type: [FUnction](javascript:void(0);)

        设置成功回调

        如:`picker.pickers[0].setSelectedValue('fourth', 200, function(){})`



        var picker = new mui.PopPicker();
        picker.setData([{
            value: "first",
            text: "第一项",
        }, {
            value: "second",
            text: "第一项"
        }, {
            value: "third",
            text: "第三项"
        }, {
            value: "fourth",
            text: "第四项"
        }, {
            value: "fifth",
            text: "第五项"
        }])
        picker.pickers[0].setSelectedIndex(4, 2000);
        picker.show(function(SelectedItem) {
            console.log(SelectedItem);
        })

-   getSelectedItems()

    -   返回值**[data]**

        Type: [Array](javascript:void(0);)

        获取选中的项（数组）

        如:`picker.getSelectedItems()`

-   show( getSelectedItems )

    -   返回值:**[data]**

        Type: [Array](javascript:void(0);)

        获取选中的项（数组）

        如:

        ```
        picker.show(function(getSelectedItems){
            console.log(getSelectedItems)
        }) 
        ```

        *

        ```
        return false; 
        ```

        可以阻止选择框的关闭

-   hide()

    隐藏picker

    如:`picker.hide()`

-   dispose()

    -   **释放组件资源(释放后将将不能再操作组件)**

        如:`picker.dispose()`

        [*](javascript:void(0);) 通常情况下，不需要释放组件资源，初始化之后，可以一直使用。
        [*](javascript:void(0);) 当内容较多，如不释放组件资源，在某些设备上可能会卡顿。
        [*](javascript:void(0);) 所以每次用完便立即调用 dispose() 进行释放,下次用时再创建新实例。

### dtpicker

dtpicker组件适用于弹出日期选择器

**快速体验**

**通过new mui.DtPicker()初始化DtPicker组件**

```
	 var dtPicker = new mui.DtPicker(options); 	 
```

**显示picker**

```
	dtPicker.show( SelectedItemsCallback ) 	
```

**实例**

```
    var dtPicker = new mui.DtPicker(); 
    dtPicker.show(function (selectItems) { 
        console.log(selectItems.y);//{text: "2016",value: 2016} 
        console.log(selectItems.m);//{text: "05",value: "05"} 
    })
```

**API详解**

-   new DtPicker({options}})

    -   1.  参数:**type**

        Type: [JSON](javascript:void(0);)

        设置日历初始视图模式，

        支持的值:

        | 可选值     | 视图模式                 |
        | ---------- | ------------------------ |
        | 'datetime' | 完整日期视图(年月日时分) |
        | 'date'     | 年视图(年月日)           |
        | 'time'     | 时间视图(时分)           |
        | 'month'    | 月视图(年月)             |
        | 'hour'     | 时视图(年月日时)         |

        *若需要指定其他显示视图,则需要通过css来控制显示项,通过js获取对应选择项.如 [设置月日时](javascript:void(0);),需要在`mui.dtpicker.css`中设置显示视图宽度,隐藏不需要的视图

        ```
        /*月日时*/
        [data-type="day"] .mui-picker,
        [data-type="day"] .mui-dtpicker-title h5 {
            width: 33.3%;
        }
        [data-type="day"][data-id="picker-i"],
        [data-type="day"][data-id="title-i"],[data-type="day"][data-id="picker-y"],
        [data-type="day"][data-id="title-y"]  {
            display: none;
        }
        ```

        在`mui.dtpicker.js`中`getSelected()`方法下添加`selected`对象值
        ```
        case 'day':
            selected.value = selected.m.value + '-' + selected.d.value + ' ' + selected.h.value;
            selected.text = selected.m.text + '-' + selected.d.text + ' ' + selected.h.text;
          break;
        ```

    -   2.  参数:**customData**

        Type: [JSON](javascript:void(0);)

        设置时间/日期别名

        设置格式:

        ```
        "customData":{
            "date":[ 
                {value:"",text:""}
            ] 
        }
        ```

        **示例:**

        ```
        var dtpicker = new mui.DtPicker({ 
            "type": "time",
            "customData": {
                "h": [ 
                    { value: "am", text: "上午" },
                    { value: "pm", text: "下午" },
                ]
            } 
        })
        dtpicker.show(function(e) { 
            console.log(e); 
        })
        ```

        支持的值:

        | 可选值 | 视图模式                             |
        | ------ | ------------------------------------ |
        | 'y'    | 可设置 [年](javascript:void(0);)别名 |
        | 'm'    | 可设置 [月](javascript:void(0);)别名 |
        | 'd'    | 可设置 [日](javascript:void(0);)别名 |
        | 'h'    | 可设置 [时](javascript:void(0);)别名 |
        | 'i'    | 可设置 [分](javascript:void(0);)别名 |

        [*](javascript:void(0);)`customData`值生效的前提需要有指定的日期视图,如设置'y',需要在视图使用'年'视图

    -   3.   参数:**labels**

            Type: [Array](javascript:void(0);)

            设置默认标签区域提示语

            可设置`["年", "月", "日", "时", "分"]`这五个字段,
            可以根据视图模式选择设置个别标签,也可以设置所有标签,
            `dtpicker`显示的时候只会根据当前视图显示设置项,
            [*](javascript:void(0);)建议不要设置空字符串,会影响美观哦

    -   4.  参数:**beginDate**

            Type: [Date](javascript:void(0);)

            设置可选择日期最小范围

            可单独设置最小年范围, 如: `beginYear:2015`, 
            其他日期支持Date格式,如:`new Date(2016,5)`可指定最小月份6月

    -   5.  参数:**endDate**

            Type: [Date](javascript:void(0);)

            设置可选择日期最大范围

            可单独设置最大年范围, 如: `endYear:2017`, 
            其他日期支持Date格式,如:`new Date(2016,10)`可指定最大月份11月

    -   完整示例:

        ```
        var dtpicker = new mui.DtPicker({
            type: "datetime",//设置日历初始视图模式 
            beginDate: new Date(2015, 04, 25),//设置开始日期 
            endDate: new Date(2016, 04, 25),//设置结束日期 
            labels: ['Year', 'Mon', 'Day', 'Hour', 'min'],//设置默认标签区域提示语 
            customData: { 
                h: [
                    { value: 'AM', text: 'AM' },
                    { value: 'PM', text: 'PM' }
                ] 
            }//时间/日期别名 
        }) 
        dtpicker.show(function(e) {
            console.log(e);
        }) 
        ```

-   getSelectedItems()

    -   返回值**Date**

        Type: [Date](javascript:void(0);)

        获取选中的项

        如: `var iTems = dtPicker.getSelectedItems()`

        返回值:

        如:

        ```
        /* * iTems.value 拼合后的 value * iTems.text 
         * 拼合后的 text
         * iTems.y 年，可以通过 rs.y.vaue 和 rs.y.text 获取值和文本
         * iTems.m 月，用法同年 
         * iTems.d 日，用法同年 
         * iTems.h 时，用法同年 
         * iTems.i 分（minutes 的第二个字母），用法同年 
         */
         
        ```

-   show( getSelectedItems )

    -   返回值:**[data]**

        Type: [Array](javascript:void(0);)

        获取选中的项（数组）

        如:

        ```
        dtpicker.show(function(items) { 
            /* * items.value 拼合后的 value 
            * items.text 拼合后的 text 
            * items.y 年，可以通过 rs.y.vaue 和 rs.y.text 获取值和文本 
            * items.m 月，用法同年 
            * items.d 日，用法同年 
            * items.h 时，用法同年 
            * items.i 分（minutes 的第二个字母），用法同年 
            */ 
            console.log(items); 
        }) 
        ```

        [*](javascript:void(0);)`return false; `可以阻止选择框的关闭

-   hide()

    隐藏dtPicker

    如:dtPicker.hide()

-   dispose()

    -   **释放组件资源(释放后将将不能再操作组件)**

        如:dtPicker.dispose()

        [*](javascript:void(0);) 通常情况下，不需要释放组件资源，初始化之后，可以一直使用。
        [*](javascript:void(0);) 当内容较多，如不释放组件资源，在某些设备上可能会卡顿。
        [*](javascript:void(0);) 所以每次用完便立即调用 dispose() 进行释放,下次用时再创建新实例。

## progressbar（进度条）

代码块激活字符:     <kbd>mprogressbar</kbd>

**有准确值的进度条**

-   有准确值的进度条会显示当前进度正处于整体进度的占比位置，用户可以更直观的预期完成时间；
-   使用进度条控件，需要一个进度条控件容器，mui会自动识别该容器下是否有进度条控件，若没有，则自动创建。

**进度条控件DOM结构：**

```
<div id="demo1" class="mui-progressbar">
	<span></span>
</div>
```

**初始化:**

```
	mui(container).progressbar({progress:20}).show();
```

例如:

```
	mui("#demo1").progressbar({progress:20}).show();
```

**progressbar初始化逻辑：**

检查当前容器(container控件)自身是否包含`.mui-progressbar`类：

-   当前容器包含`.mui-progressbar`类，则以当前容器为目标控件，直接显示进度；
-   否则，检查当前容器的直接孩子节点是否包含`.mui-progressbar`类，若存在，则以遍历到的第一个含有`.mui-progressbar`类的孩子节点为目标控件，显示进度；
-   若当前容器的直接孩子节点，均不含.mui-progressbar类,则自动创建进度条控件；

**更改显示进度条:**

```
	mui(container).progressbar().setProgress(50);
```

**关闭进度条:**

```
	mui(container).progressbar().hide();
```

备注：关闭进度条一般用于动态创建（DOM中预先未定义）的进度条，调用hide方法后，会直接删掉对应的DOM节点；若已提前创建好DOM节点的进度条，调用hide方法无效；

**无限循环进度条:**

若无法准确提供当前进度，可以提供无限循环进度条（无限循环进度条类似于waiting等待框

无限循环进度条和准确值的进度条的用法基本相同，有如下差异：

进度条控件DOM结构（多了`.mui-progressbar-infinite`）：

```
<div id="demo1" class="mui-progressbar mui-progressbar-infinite">
	<span></span>
</div>
```

**初始化**

```
	mui("#demo1").progressbar().show();
```

注意：无限循环进度条不显示具体进度，因此初始化时，不能传入progress参数；mui框架也是根据progressbar构造方法中是否包含progress参数来区分当前进度条为有准确值的进度条还是无限循环进度条；

同样因为不显示具体进度的原因，无限循环进度条调用setProgress()方法无效。

**关闭进度条**

```
	mui("#demo1").progressbar().hide();
```

>   #### 页面顶部进度条
>
>   页面顶部进度条类似浏览器进度条，固定显示在页面顶部（标题导航控件下方）； 因此，若当前页面使用父子双webview模式，子页面没有标题导航组件，则需通过自定义css的方式，重定义顶部进度条的位置，示例代码如下：
>
>   ```
>   body>.mui-progressbar{
>   	top:0
>   }
>   ```
>
>   使用页面顶部进度条时，无需编写DOM结构，使用如下代码即可自动创建（顶部无限循环进度条同理）：
>
>   ```
>   mui('body').progressbar({
>   	progress: 20
>   }).show();
>   ```

### radio（单选框）

radio用于单选的情况

代码块激活字符:    <kbd>mradio</kbd>

**DOM结构**

```
<div class="mui-input-row mui-radio">
	<label>radio</label>
	<input name="radio1" type="radio">
</div>
```

默认radio在右侧显示，若希望在左侧显示，只需增加`.mui-left`类即可，如下：

```
<div class="mui-input-row mui-radio mui-left">
	<label>radio</label>
	<input name="radio1" type="radio">
</div> 
```

若要禁用radio，只需在radio上增加disabled属性即可；

mui基于列表控件，提供了列表式单选实现；在列表根节点上增加`.mui-table-view-radio`类即可，若要默认选中某项，只需要在对应`li`节点上增加`.mui-selected`类即可，dom结构如下：

```
<ul class="mui-table-view mui-table-view-radio">
	<li class="mui-table-view-cell">
		<a class="mui-navigate-right">Item 1</a>
	</li>
	<li class="mui-table-view-cell mui-selected">
		<a class="mui-navigate-right">Item 2</a>
	</li>
	<li class="mui-table-view-cell">
		<a class="mui-navigate-right">Item 3</a>
	</li>
</ul>
```

列表式单选在切换选中项时会触发selected事件，在事件参数（`e.detail.el`）中可以获得当前选中的dom节点，如下代码打印当前选中项的innerHTML：

```
var list = document.querySelector('.mui-table-view.mui-table-view-radio');
list.addEventListener('selected',function(e){
	console.log("当前选中的为："+e.detail.el.innerText);
});
```

## range（滑块）

代码块激活字符:    <kbd>mrange<kbd>

滑块常用于区间数字选择

**DOM结构**

```
<div class="mui-input-row mui-input-range">
	<label>Range</label>
	<input type="range" min="0" max="100">
</div>
```

## scroll(区域滚动)

代码块激活字符:    <kbd>mscroll</kbd><kbd>mscrollsegmented</kbd>

在App开发中，div区域滚动的需求是普遍存在的，但系统默认实现又有如下问题：

-   Android平台4.0以下不支持div滚动
-   Android平台4.0以上支持div滚动，但不显示滚动条
-   弹出层的div滚动在iOS平台存在事件透传的问题

因此，mui额外提供了区域滚动组件，使用时需要遵循如下DOM结构

```
<div class="mui-scroll-wrapper">
	<div class="mui-scroll">
		<!--这里放置真实显示的DOM内容-->
	</div>
</div>
```

区域滚动组件默认为absolute定位，全屏显示；在实际使用过程中，需要手动设置滚动区域的位置（top和height）

若使用区域滚动组件，需手动初始化scroll控件

[*](javascript:void(0);)常用配置项:

### scroll.options

```
options = {
 scrollY: true, //是否竖向滚动
 scrollX: false, //是否横向滚动
 startX: 0, //初始化时滚动至x
 startY: 0, //初始化时滚动至y
 indicators: true, //是否显示滚动条
 deceleration:0.0006, //阻尼系数,系数越小滑动越灵敏
 bounce: true //是否启用回弹
}
```

示例：初始化scroll控件：

```
mui('.mui-scroll-wrapper').scroll({
	deceleration: 0.0005 //flick 减速系数，系数越大，滚动速度越慢，滚动距离越小，默认值0.0006
});
```

mui中iOS平台的下拉刷新（Android平台的下拉刷新使用的是双webview+原生滚动方案）、popover、可拖动式选项卡均使用了scroll组件。 为方便大家使用，mui还额外为scroll插件封装了部分方法。

### 滚动到特定位置

-   scrollTo( xpos , ypos [, duration] )

    -   **xpos**

        Type: [Integer](http://dev.dcloud.net.cn/mui/ui/)

        要在窗口文档显示区左上角显示的文档的 x 坐标

    -   **ypos**

        Type: [Integer](http://dev.dcloud.net.cn/mui/ui/)

        要在窗口文档显示区左上角显示的文档的 y 坐标

    -   **duration**

        Type: [Integer](http://dev.dcloud.net.cn/mui/ui/)

        滚动时间周期，单位是毫秒

示例：快速回滚到该区域顶部，代码如下：

```
mui('.mui-scroll-wrapper').scroll().scrollTo(0,0,100);//100毫秒滚动到顶
```

### 滚动到底部位置

滚动到顶部的代码比较容易实现,坐标值设为0、0即可；但滚动到底部，需要计算该区域的实际高度，因此mui封装了scrollToBottom方法。

-   scrollToBottom(duration)

### 横向滚动

横向滚动只需在scroll组件基础上添加`mui-slider-indicatorcode` `mui-segmented-control` `mui-segmented-control-inverted`这三个class即可.(给子元素添加`mui-control-item`可加大文字间距增强体验
如:)

```
<div class="mui-scroll-wrapper mui-slider-indicator mui-segmented-control mui-segmented-control-inverted">
    <div class="mui-scroll">
        <a class="mui-control-item mui-active"> 推荐 </a>
        <a class="mui-control-item"> 热点 </a>
        <a class="mui-control-item"> 北京 </a>
        <a class="mui-control-item"> 社会 </a>
        <a class="mui-control-item"> 娱乐 </a>
        <a class="mui-control-item"> 科技 </a>
        <a class="mui-control-item"> 热点 </a>
        <a class="mui-control-item"> 北京 </a>
        <a class="mui-control-item"> 社会 </a>
        <a class="mui-control-item"> 娱乐 </a>
        <a class="mui-control-item"> 科技 </a>
    </div>
</div>
```

## slide（轮播组件）

代码块激活字符:    <kbd>mslider</kbd>

轮播组件是mui提供的一个核心组件，在该核心组件基础上，衍生出了图片轮播、可拖动式图文表格、可拖动式选项卡、左右滑动9宫格等组件，这些组件有较多共同点。首先，Dom构造基本相同，如下：

```
<div class="mui-slider">
  <div class="mui-slider-group">
    <!--第一个内容区容器-->
    <div class="mui-slider-item">
      <!-- 具体内容 -->
    </div>
    <!--第二个内容区-->
    <div class="mui-slider-item">
      <!-- 具体内容 -->
    </div>
  </div>
</div>
```

当拖动切换显示内容时，会触发slide事件，通过该事件的detail.slideNumber参数可以获得当前显示项的索引（第一项索引为0，第二项为1，以此类推），利用该事件，可在显示内容切换时，动态处理一些业务逻辑。

如下为一个可拖动式选项卡示例，为提高页面加载速度，页面加载时，仅显示第一个选项卡的内容，第二、第三选项卡内容为空。

当切换到第二、第三个选项卡时，再动态获取相应内容进行显示：

```
var item2Show = false,item3Show = false;//子选项卡是否显示标志
document.querySelector('.mui-slider').addEventListener('slide', function(event) {
  if (event.detail.slideNumber === 1&&!item2Show) {
    //切换到第二个选项卡
    //根据具体业务，动态获得第二个选项卡内容；
    var content = ....
    //显示内容
    document.getElementById("item2").innerHTML = content;
    //改变标志位，下次直接显示
    item2Show = true;
  } else if (event.detail.slideNumber === 2&&!item3Show) {
    //切换到第三个选项卡
    //根据具体业务，动态获得第三个选项卡内容；
    var content = ....
    //显示内容
    document.getElementById("item3").innerHTML = content;
    //改变标志位，下次直接显示
    item3Show = true;
  }
});
```

图片轮播、可拖动式图文表格等均可按照同样方式监听内容变化，比如我们可以在图片轮播界面显示当前正在看的是第几张图片：

```
document.querySelector('.mui-slider').addEventListener('slide', function(event) {
  //注意slideNumber是从0开始的；
  document.getElementById("info").innerText = "你正在看第"+(event.detail.slideNumber+1)+"张图片";
});
```

## switch(开关)

代码块激活字符:    <kbd>mswitch</kbd>

mui提供了开关控件，点击滑动两种手势都可以对开关控件进行操作,UI如下：

![](F:\notes\img\tianruo_2018-9-19-636729749961939749.png)

默认开关控件,带on/off文字提示，打开时为绿色背景，基本class类为`.mui-switch`、`.mui-switch-handle`，DOM结构如下：

```
<div class="mui-switch">
  <div class="mui-switch-handle"></div>
</div>
```

若希望开关默认为打开状态，只需要在`.mui-switch`节点上增加`.mui-active`类即可，如下：

```
<!-- 开关打开状态，多了一个.mui-active类 -->
<div class="mui-switch mui-active">
  <div class="mui-switch-handle"></div>
</div>
```

若希望隐藏on/off文字提示，变成简洁模式，需要在`.mui-switch`节点上增加`.mui-switch-mini`类，如下：

```
<!-- 简洁模式开关关闭状态 -->
<div class="mui-switch mui-switch-mini">
  <div class="mui-switch-handle"></div>
</div>
<!-- 简洁模式开关打开状态 -->
<div class="mui-switch mui-switch-mini mui-active">
  <div class="mui-switch-handle"></div>
</div>
```

mui默认还提供了蓝色开关控件，只需在`.mui-switch`节点上增加`.mui-switch-blue`类即可，如下：

```
<!-- 蓝色开关关闭状态 -->
<div class="mui-switch mui-switch-blue">
  <div class="mui-switch-handle"></div>
</div>
<!-- 蓝色开关打开状态 -->
<div class="mui-switch mui-switch-blue mui-active">
  <div class="mui-switch-handle"></div>
</div>
```

蓝色开关上增加`.mui-switch-mini`即可变成无文字的简洁模式

### 方法

若要获得当前开关状态，可通过判断当前开关控件是否包含`.mui-active`类来实现，若包含，则为打开状态，否则即为关闭状态；如下为代码示例：

```
var isActive = document.getElementById("mySwitch").classList.contains("mui-active");
if(isActive){
  console.log("打开状态");
}else{
  console.log("关闭状态");  
}
```

若使用js打开、关闭开关控件，可使用switch插件的`toggle()`方法，如下为示例代码：

```
mui("#mySwitch").switch().toggle();
```

### 事件

开关控件在打开/关闭两种状态之间进行切换时，会触发toggle事件,通过事件的detail.isActive属性可以判断当前开关状态。可通过监听toggle事件，可以在开关切换时执行特定业务逻辑。如下为使用示例：

```
document.getElementById("mySwitch").addEventListener("toggle",function(event){
  if(event.detail.isActive){
    console.log("你启动了开关");
  }else{
    console.log("你关闭了开关");  
  }
})
```

初始化：

mui在mui.init()中会自动初始化基本控件,但是 [动态添加的 Switch 组件需要手动初始化](javascript:void(0);)

```
mui('.mui-switch')['switch']()
```