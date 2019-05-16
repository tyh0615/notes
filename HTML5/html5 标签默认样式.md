# html5 标签默认样式

## css 通用默认样式

```
@charset "utf-8";
*{box-sizing:content-box;}
a:hover, a:focus{text-decoration:none;}
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,p,blockquote,th,td{margin:0;padding:0;}
table{border-collapse:collapse;border-spacing:0;}
body{max-width: 1920px;-webkit-text-size-adjust:none;}
fieldset,img{border:0;}
img{ vertical-align: top; max-width: 100%; }
address,caption,cite,code,dfn,em,th,var{font-style:normal;font-weight:normal;}
ol,ul{list-style:none;}
caption,th{text-align:left;}
h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal;}
q:before,q:after{content:'';}
abbr,acronym {border:0;}
.clearfix:after{visibility:hidden;display: block;font-size:0;content:" ";clear:both;height:0;}
* html .clearfix{ zoom: 1; } /* IE6 */
*:first-child+html .clearfix { zoom: 1; } /* IE7 */
.cli{ clear:both; font-size:0; height:0; overflow:hidden;display:block;}
.lclear{clear:left;font-size:0;height:0;overflow:hidden;}	
.fl{float:left;}
.fr{float:right;}
div{word-wrap: break-word;word-break: normal;}  
p{text-align:justify; text-justify:inter-ideograph;}
body{font-size:12px;font-family:'微软雅黑',"宋体","Arial Narrow",Helvetica,sans-serif;color:#000;line-height:1.2;text-align:left;}
a{color:#333;text-decoration:none;}
```

css 通用默认样式

```
@charset "utf-8";

* {
    box-sizing: content-box;
}

a:hover,
a:focus {
    text-decoration: none;
}

body,
div,
dl,
dt,
dd,
ul,
ol,
li,
h1,
h2,
h3,
h4,
h5,
h6,
pre,
form,
fieldset,
input,
textarea,
p,
blockquote,
th,
td {
    margin: 0;
    padding: 0;
}

table {
    border-collapse: collapse;
    border-spacing: 0;
}

body {
    max-width: 1920px;
    -webkit-text-size-adjust: none;
}

fieldset,
img {
    border: 0;
}

img {
    vertical-align: top;
    max-width: 100%;
}

address,
caption,
cite,
code,
dfn,
em,
th,
var {
    font-style: normal;
    font-weight: normal;
}

ol,
ul {
    list-style: none;
}

caption,
th {
    text-align: left;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-size: 100%;
    font-weight: normal;
}

q:before,
q:after {
    content: '';
}

abbr,
acronym {
    border: 0;
}

.clearfix:after {
    visibility: hidden;
    display: block;
    font-size: 0;
    content: " ";
    clear: both;
    height: 0;
}

* html .clearfix {
    zoom: 1;
}

/* IE6 */
*:first-child+html .clearfix {
    zoom: 1;
}

/* IE7 */
.cli {
    clear: both;
    font-size: 0;
    height: 0;
    overflow: hidden;
    display: block;
}

.lclear {
    clear: left;
    font-size: 0;
    height: 0;
    overflow: hidden;
}

.fl {
    float: left;
}

.fr {
    float: right;
}

div {
    word-wrap: break-word;
    word-break: normal;
}

p {
    text-align: justify;
    text-justify: inter-ideograph;
}

body {
    font-size: 12px;
    font-family: '微软雅黑', "宋体", "Arial Narrow", Helvetica, sans-serif;
    color: #000;
    line-height: 1.2;
    text-align: left;
}

a {
    color: #333;
    text-decoration: none;
}
```

### <details><summary>标签

```
::-webkit-details-marker {
	display: none;
}
```

>   eq:
>   
>   
>   ```
>   <!DOCTYPE html>
>   <html>
>   <head>
>     <meta charset="utf-8">
>      <style type="text/css">
>          ::-webkit-details-marker {
>              display: none;
>          }
>          ::-moz-list-bullet {
>              font-size: 0;
>              float: left;
>          }
>          summary {
>              user-select: none;
>              outline: 0;
>          }
>          .more {
>              display: none;
>          }
>          [open] .more {
>              display: block;
>          }
>          [open] summary a {
>              font-size: 0;
>          }
>          [open] summary a::before {
>              content: '收起 ^';
>              font-size: 16px;
>          }
>    
>     </style>
>    </head>
>   
>   <body>
>     <details>
>          <summary>
>              <span>据台媒报道，大...青睐。</span>
>              <a>更多 ></a>
>              <div class="more">
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>              </div>
>          </summary> 
>      </details>
>      <details>
>          <summary>
>              <span>据台媒报道，大...青睐。</span>
>              <a>更多 ></a>
>              <div class="more">
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>              </div>
>          </summary> 
>      </details>
>      <details>
>          <summary>
>              <span>据台媒报道，大...青睐。</span>
>              <a>更多 ></a>
>              <div class="more">
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>              </div>
>          </summary> 
>      </details>
>      <details>
>          <summary>
>              <span>据台媒报道，大...青睐。</span>
>              <a>更多 ></a>
>              <div class="more">
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>                  <p>其他几首歌曲...</p>
>              </div>
>          </summary> 
>      </details>
>    </body>
>   </html>
>   ```
>   