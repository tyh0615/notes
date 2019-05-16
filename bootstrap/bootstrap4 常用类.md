## bootstrap4 常用类

### 字体类

```
.lead {
    font-size: 1.25rem;
    font-weight: 300;
}
.display-1 {
    font-size: 6rem;
    font-weight: 300;
    line-height: 1.2;
}
.display-2 {
    font-size: 5.5rem;
    font-weight: 300;
    line-height: 1.2;
}
.display-3 {
    font-size: 4.5rem;
    font-weight: 300;
    line-height: 1.2;
}
.display-4 {
    font-size: 3.5rem;
    font-weight: 300;
    line-height: 1.2;
}
small,.small {
    font-size: 80%;
    font-weight: 400;
}
.initialism {
    font-size: 90%;
    text-transform: uppercase;
}
.align-baseline {
    vertical-align: baseline !important;
}
.align-top {
    vertical-align: top !important;
}
.align-middle {
    vertical-align: middle !important;
}
.align-bottom {
    vertical-align: bottom !important;
}
.align-text-bottom {
    vertical-align: text-bottom !important;
}
.align-text-top {
    vertical-align: text-top !important;
}
```
### 文字类 

```
.text-justify {
    text-align: justify !important;
}
.text-nowrap {
    white-space: nowrap !important;
}
.text-truncate {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
.text-left {
    text-align: left !important;
}
.text-right {
    text-align: right !important;
}
.text-center {
    text-align: center !important;
}
.text-lowercase {
    text-transform: lowercase !important;
}
.text-uppercase {
    text-transform: uppercase !important;
}
.text-capitalize {
    text-transform: capitalize !important;
}
.font-weight-light {
    font-weight: 300 !important;
}
.font-weight-normal {
    font-weight: 400 !important;
}
.font-weight-bold {
    font-weight: 700 !important;
}
.font-italic {
    font-style: italic !important;
}
.text-white {
    color: #fff !important;
}
.text-primary {
    color: #007bff !important;
}
.text-dark {
    color: #343a40 !important;
}
a.text-dark:hover,
a.text-dark:focus {
    color: #1d2124 !important;
}
.text-muted {
    color: #6c757d !important;
}
.text-hide {
    font: 0/0 a;
    color: transparent;
    text-shadow: none;
    background-color: transparent;
    border: 0;
}
```

### 列表类 

```
.list-unstyled {
    padding-left: 0;
    list-style: none;
}
.list-inline {
    padding-left: 0;
    list-style: none;
}
.list-inline-item {
    display: inline-block;
}
.list-inline-item:not(:last-child) {
    margin-right: 0.5rem;
}
```

### 图片类

``` 
.img-fluid {
    //以前是.img-responsive
    max-width: 100%;
    height: auto;
}
.img-thumbnail {
    //不是说移除了吗，怎么还有.之前是.thumbnail
    padding: 0.25rem;
    background-color: #fff;
    border: 1px solid #dee2e6;
    border-radius: 0.25rem;
    max-width: 100%;
    height: auto;
}
.figure {
    display: inline-block;
}
```
### 容器类 
``` 
.container {
    width: 100%;
    padding-right: 15px;
    padding-left: 15px;
    margin-right: auto;
    margin-left: auto;
}
@media (min-width: 576px) {
    .container {
        max-width: 540px;
    }
}
@media (min-width: 768px) {
    .container {
        max-width: 720px;
    }
}
@media (min-width: 992px) {
    .container {
        max-width: 960px;
    }
}
@media (min-width: 1200px) {
    .container {
        max-width: 1140px;
    }
}
.container-fluid {
    width: 100%;
    padding-right: 15px;
    padding-left: 15px;
    margin-right: auto;
    margin-left: auto;
}
.order-12 {
    //flex 方式order属性用于更改在主轴方向上排列顺序。
    //order数值越小，排列越靠前，默认为0，可以为负数
    -webkit-box-ordinal-group: 13;
    -ms-flex-order: 12;
    order: 12;
}
.offset-1 {
    //margin方式
    margin-left: 8.333333%;
}
```
### table类 
``` 
//表格可以写入的类  *-active *-default *-primary secondary success danger warning
//info light dark
//响应式表格.table-responsive，使 Viewport 符合任何表格。或者 .table 中加 .table-responsive{-sm|-md|-lg|-xl}
.table-responsive {
    display: block;
    width: 100%;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    -ms-overflow-style: -ms-autohiding-scrollbar;
}
.table-responsive>.table-bordered {
    border: 0;
}
```
### border类 
``` 
.border {
    border: 1px solid #dee2e6 !important;
}
.border-top {
    border-top: 1px solid #dee2e6 !important;
}
.border-right {
    border-right: 1px solid #dee2e6 !important;
}
.border-bottom {
    border-bottom: 1px solid #dee2e6 !important;
}
.border-left {
    border-left: 1px solid #dee2e6 !important;
}
.border-0 {
    border: 0 !important;
}
.border-top-0 {
    border-top: 0 !important;
}
.border-right-0 {
    border-right: 0 !important;
}
.border-bottom-0 {
    border-bottom: 0 !important;
}
.border-left-0 {
    border-left: 0 !important;
}
```
### 边框颜色 
``` 
.border-primary {
    border-color: #007bff !important;
}
.border-secondary {
    border-color: #6c757d !important;
}
.border-success {
    border-color: #28a745 !important;
}
.border-info {
    border-color: #17a2b8 !important;
}
.border-warning {
    border-color: #ffc107 !important;
}
.border-danger {
    border-color: #dc3545 !important;
}
.border-light {
    border-color: #f8f9fa !important;
}
.border-dark {
    border-color: #343a40 !important;
}
.border-white {
    border-color: #fff !important;
}
```
### 边框圆角 
``` 
.rounded {
    border-radius: 0.25rem !important;
}
.rounded-top {
    border-top-left-radius: 0.25rem !important;
    border-top-right-radius: 0.25rem !important;
}
.rounded-right {
    border-top-right-radius: 0.25rem !important;
    border-bottom-right-radius: 0.25rem !important;
}
.rounded-bottom {
    border-bottom-right-radius: 0.25rem !important;
    border-bottom-left-radius: 0.25rem !important;
}
.rounded-left {
    border-top-left-radius: 0.25rem !important;
    border-bottom-left-radius: 0.25rem !important;
}
.rounded-circle {
    border-radius: 50% !important;
}
.rounded-0 {
    border-radius: 0 !important;
}
```
### 显示状态类 
``` 
.d-none {
    display: none !important;
}
.d-inline {
    display: inline !important;
}
.d-inline-block {
    display: inline-block !important;
}
.d-block {
    display: block !important;
}
.d-table {
    display: table !important;
}
.d-table-row {
    display: table-row !important;
}
.d-table-cell {
    display: table-cell !important;
}
.d-flex {
    display: -webkit-box !important;
    display: -ms-flexbox !important;
    display: flex !important;
}
.d-inline-flex {
    display: -webkit-inline-box !important;
    display: -ms-inline-flexbox !important;
    display: inline-flex !important;
}
在固定大小显示隐藏 
.d-sm-none {
    //只提供一个例子
    display: none !important;
}
```
### 浮动类 
``` 
.float-left {
    float: left !important;
}
.float-right {
    float: right !important;
}
.float-none {
    float: none !important;
}
.float-xl-none {
    float: none !important;
}
```
### 定位类 
``` 
.position-static {
    position: static !important;
}
.position-relative {
    position: relative !important;
}
.position-absolute {
    position: absolute !important;
}
.position-fixed {
    position: fixed !important;
}
.position-sticky {
    position: -webkit-sticky !important;
    position: sticky !important;
}
.fixed-top {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    z-index: 1030;
}
.fixed-bottom {
    position: fixed;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1030;
}
```
### 判断浏览器是否支持 
``` 
@supports ((position: -webkit-sticky) or (position: sticky)) {
    .sticky-top {
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        z-index: 1020;
    }
}
```
### 其他类 
``` 
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    -webkit-clip-path: inset(50%);
    clip-path: inset(50%);
    border: 0;
}
.w-25 {
    width: 25% !important;
}
.w-50 {
    width: 50% !important;
}
.w-75 {
    width: 75% !important;
}
.w-100 {
    width: 100% !important;
}
.h-25 {
    height: 25% !important;
}
.h-50 {
    height: 50% !important;
}
.h-75 {
    height: 75% !important;
}
.h-100 {
    height: 100% !important;
}
.mw-100 {
    max-width: 100% !important;
}
.mh-100 {
    max-height: 100% !important;
}
.m-0 {
    margin: 0 !important;
}
.mt-0,.my-0 {
    margin-top: 0 !important;
}
.mr-0,.mx-0 {
    margin-right: 0 !important;
}
.mb-0,.my-0 {
    margin-bottom: 0 !important;
}
.ml-0,.mx-0 {
    margin-left: 0 !important;
}
.m-1 {
    margin: 0.25rem !important;
}
.mt-1,.my-1 {
    margin-top: 0.25rem !important;
}
.mr-1,.mx-1 {
    margin-right: 0.25rem !important;
}
.mb-1,.my-1 {
    margin-bottom: 0.25rem !important;
}
.ml-1,.mx-1 {
    margin-left: 0.25rem !important;
}
.m-2 {
    margin: 0.5rem !important;
}
.p-0 {
    padding: 0 !important;
}
.pt-0,.py-0 {
    padding-top: 0 !important;
}
.pr-0,.px-0 {
    padding-right: 0 !important;
}
.pb-0,.py-0 {
    padding-bottom: 0 !important;
}
.pl-0,.px-0 {
    padding-left: 0 !important;
}
.p-1 {
    padding: 0.25rem !important;
}
.pt-1,.py-1 {
    padding-top: 0.25rem !important;
}
.pr-1,.px-1 {
    padding-right: 0.25rem !important;
}
.m-sm-0 {
    margin: 0 !important;
}
.m-auto {
    margin: auto !important;
}
```
### 显示与隐藏 
``` 
.visible {
    visibility: visible !important;
}
.invisible {
    visibility: hidden !important;
}
```