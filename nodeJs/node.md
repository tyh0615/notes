# Node.js

## 准备Node.js

使用nvm来安装并维护多个Nodejs的版本
1、项目地址：
https://github.com/creationix/nvm/blob/master/README.md
2、配置加速镜像
export NVM NODEJS ORG MIRROR-https://npm.taobao.org/mirrors/node

1.  验证nvm是否安装成功：在cmd输入nvm version，有提示nvm版本信息，即安装 成功
2.  然后输入nvm root，查看到nvm的路径信息，我的是[C:](https://www.baidu.com/s?wd=C%3A&tn=24004469_oem_dg&rsv_dl=gh_pl_sl_csd)\Users\Administrator\AppData\Roaming\nvm，所以在资源管理器上打开这个路径，找到里面的settings.txt，并打开
3.  在文本的最后一行中加入这两行代码
    node_mirror: <https://npm.taobao.org/mirrors/node/>
    npm_mirror: <https://npm.taobao.org/mirrors/npm/>
    然后保存
4.  保存文件之后，关掉cmd，再重新打开cmd，输入：nvm install [version]，就会启用淘宝镜像自动下载安装对应的node和npm版本。
5.  Node Version Manager(Node版本管理器)
    1.  nvm(Linux,Unix,os x）
        1.   https://github.com/creationix/nvm
        2.  产用命令:nvm-install node.(安装最新版本的node)
            1.  nvm-use-node.(使用指定版本的node)
    2.  nvm-windows.(Windows)
        1.  https://github.com/coreybutler/nvm-windows常用命令
            1.  nvm-version 
            2.  nvm-install latest 
            3.  nvm-install-版本号
            4.  nvm-uninstall.版本号
            5.  nvm list 
            6.  nvm use.版本号

## 命令行中的体验

$ node进入命令行
1、在浏览器和node命令行中运行代码

```
function add(x,y){
console.log(x+y)
}
add(3,4)
```


2、在浏览器和node命令行里调用window,process两个对象

## 执行.js文件

1、编写indexjs文件

```
console.log(hello);
function add(xy){
	console.log(x+y)
};
add(6,7);
```

2、node indexjs执行代码

3、安装nodemon实时侦测文件的变化

## 模块/包与CommonJS

![1550129783599](node.assets/1550129783599.png)

![1550129829196](node.assets/1550129829196.png)

http://www.commonjs.org

##  Node.js常用模块介绍

1.  URL

```
url.parse(urlString[, parseQueryString[,slashesDenoteHost]])
url.format(urlObject) 
url.resolve(from, to)
```

# 在node.js上编写程序

## REPL介绍

1. REPL全称:Read-Eval-Print-Loop(交互式解释器)
  R读取-读取用户输入,解析输入了Javascript数据结构并存储在内存中.
  E执行-执行输入的数据结构
  P打印-输出结果
  L循环-循环操作以上步骤直到用户两次按下ctrl-c按钮退出.

2. 在REPL中编写程序(类似于浏览器开发人员工具中的控制台功能)
  直接在控制台输入`node`命令进入REPL环境

3. 按两次Control +C退出REPL界面或者输入`.exit`退出REPL界面,

    按住control键不要放开,然后按两下c键 T

```
//---输出一个三角形---
//循环有多少行
for(var i 0;i  10;i++){
//每行要输出多少个*
for(var j=0;j <=i;j+){
//每行输出的*不能换行
process.stdout.write('*);
}
//当每行的所有*都输出完毕后,需要输出一个换行
console.log();
}
```

// process模块在使用的时候无需通过require()函数来加载该模块,可以直接使用.
// fs模块,在使用的时候,必须通过require()函数来加载该模块,方可使用.var fs = require("fs');
// 原因:process模块是全局的模块,而fs模块不是全局模块.全局棋块可以直接使用,而非全局模块需要先通过require(")加载该模块

### fs-文件系统

1.  fs.writeFile(file, data[, options], callback)

    ```
    var fs = require('fs');
    var msg = 'Dawn hello';
    fs.writeFile('./Dawn.txt',msg,function (err) {
        if (err){
            console.log('写文件出错啦！具体错误：' + err);
        }else{
            console.log('写文件成功啦！')
        }
    });
    ```

2.  fs.readFile(path[, options], callback)

    ```
    var fs = require('fs');
    fs.readFile('./Dawn.txt','utf8',function (err,data) {
        if (err) throw err;
        // data参数的数据类型是一个Buffer对象，里面保存的就是一个一个的字节（理解为字节数组
        //把buffer对象转换为字符串，调用toString（）方法
        console.log(data.toString())
    });
    ```







































