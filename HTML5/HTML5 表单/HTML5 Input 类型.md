# HTML5 新的 Input 类型

HTML5 拥有多个新的表单输入类型。这些新特性提供了更好的输入控制和验证。

本章全面介绍这些新的输入类型：

[TOC]

## Input 类型 - email

email 类型用于应该包含 e-mail 地址的输入域。

在提交表单时，会自动验证 email 域的值。

```
E-mail: <input type="email" name="user_email" />
```

**提示：**iPhone 中的 Safari 浏览器支持 email 输入类型，并通过改变触摸屏键盘来配合它（添加 @ 和 .com 选项）。

## Input 类型 - url

url 类型用于应该包含 URL 地址的输入域。

在提交表单时，会自动验证 url 域的值。

```
Homepage: <input type="url" name="user_url" />
```

**提示：**iPhone 中的 Safari 浏览器支持 url 输入类型，并通过改变触摸屏键盘来配合它（添加 .com 选项）。

## Input 类型 - number

number 类型用于应该包含数值的输入域。

您还能够设定对所接受的数字的限定：

```
Points: <input type="number" name="points" min="1" max="10" />
```

请使用下面的属性来规定对数字类型的限定：

| 属性  | 值       | 描述                                                         |
| :---- | :------- | :----------------------------------------------------------- |
| max   | *number* | 规定允许的最大值                                             |
| min   | *number* | 规定允许的最小值                                             |
| step  | *number* | 规定合法的数字间隔（如果 step="3"，则合法的数是 -3,0,3,6 等） |
| value | *number* | 规定默认值                                                   |

**提示：**iPhone 中的 Safari 浏览器支持 number 输入类型，并通过改变触摸屏键盘来配合它（显示数字）。

## Input 类型 - range

range 类型用于应该包含一定范围内数字值的输入域。

range 类型显示为滑动条。

您还能够设定对所接受的数字的限定：

```
<input type="range" name="points" min="1" max="10" />
```

请使用下面的属性来规定对数字类型的限定：

| 属性  | 值       | 描述                                                         |
| :---- | :------- | :----------------------------------------------------------- |
| max   | *number* | 规定允许的最大值                                             |
| min   | *number* | 规定允许的最小值                                             |
| step  | *number* | 规定合法的数字间隔（如果 step="3"，则合法的数是 -3,0,3,6 等） |
| value | *number* | 规定默认值                                                   |

## Input 类型 - Date

HTML5 拥有多个可供选取日期和时间的新输入类型：

-   date - 选取日、月、年
-   month - 选取月、年
-   week - 选取周和年
-   time - 选取时间（小时和分钟）
-   datetime - 选取时间、日、月、年（UTC 时间）
-   datetime-local - 选取时间、日、月、年（本地时间）

## Input 类型 - search

search 类型用于搜索域，比如站点搜索或 Google 搜索。

search 域显示为常规的文本域。

```
<input type="search">
<!--input的search类型在输入文字后会出现清除按钮,而且只有在获得焦点时才出现-->
```

## Input 类型 - color

HTML5之input的类型color，通过input：color来改变背景颜色或者字体颜色

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>CSS Variables</title>
    <link rel="stylesheet" href="style.css">
    <style>
        :root{
	        --color:#ffc600;
		}
        .artical{
            color:var(--color);
        }
    </style>
 
</head>
<body>
    <div class="demo">
        当前值：<br/>
        <input type="range" id="range" min="0" max="200" value="0" onchange="change()">
        <input type="text" class="num" >
        <br/>
        选择文本字体颜色：<br/>
        <input type="color" id="color" value="#ffc600" onchange="colorchange()">
        <p class="artical">背景颜色展示</p>
    </div>
    <script>
        // var Color=document.querySelector("#color");
        // Color.addEventListener("change",colorchange,false);
        function change(){
            var Range=document.querySelector("#range");
            var Num=document.querySelector(".num");
            Num.value=Range.value;    
        }
        function colorchange(){
            //alert("fff");在选择完颜色之后，点击了确认按钮后才出发change事件。
            var Color=document.querySelector("#color");
	    document.body.style.setProperty("--color",Color.value);
              //var Artical=document.querySelector(".artical");
			 // Color.click();  //出现问题处
            //Artical.style.color=Color.value;
        }
    </script>
</body>
</html>
```

