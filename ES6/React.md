# 搭建React开发环境

1.  安装官方脚手架
    npm install-g create-react-app
2.  创建工程
    create-react-app my-app
3.  进入工程目录
    cd my-app
4.  启动工程
	npm start

## JSX语法的由来

-   React为方便View层组件化，承载了构建HTML结构化页面的职责。从这点上来看，React 与其他JavaScript模板语言有着许多异曲同工之处，但不同之处在于React是通过创建与更新虚拟元素（virtual element）来管理整个Virtual DOM的。
-   JSX将HTML语法直接加入到JavaScript代码中，再通过翻译器转换到纯JavaScript后由浏览器执行。在实际开发中，JSX在产品打包阶段都已经编译成纯JavaScript，不会带来任何副作用，反而会让代码更加直观并易于维护。
-   编译过程由Babe的JSX编译器实现。

### JSX基本语法

1.  XML基本语法
    **定义标签时,只允许被一个标签包裹.标签一定要闭合.**

    ```
    const List=()=>(
        <div>
            <Title>This is title</Title>
            <ul>
                <li>list item</li>
                <li>list item</li>
                <li>list item</li>
            </ul>
        </div>
    )；
    ```

2.  元素类型 
    小写首字母对应DOM元素
    大写首字母对应组件元素自然
    注释使用js注释方法

3.  元素属性
    class 属性改为className
    for属性改为htmlFor
    Boolean属性：省略Boolean属性值会导致JSX认为bool值设为了true

4.  JavaScript属性表达式
    属性值要使用表达式，只要用{}替换“”即可
    <input type="text" value={val?val:""}/>

5.  HTML转义
    React会将所有要显示到DOM的字符串转义，防止XSS。
    后台传过来的数据带页面标签的是不能直接转义的，具体转义的写法如下：

    ```
    var content='<strong>content</strong>'；
    React.render（
    	<div dangerouslySetlnnerHTML={{__html:content]}></div>，
    	document.body
    ）；
    ```

6.  ReactDOM.render
    作用：描画dom
    参数1：dom对象
    参数2：注入点

    ```
    ReactDOM.render（
    	<div>Hello World！</div>，
    	document.querySelector（"#wrapper'）
    ）；
    ```
    **组件的声明(ES5):**

    ```
    var Hello=React.createClass{
        render:function(){
            return(
                <div>Hello World!</div>
            )
    	}
    );
    ```

    **组件的声明(ES6):**

    ```
    class Wello extends React.Component{
        render(){
       		return(
    			<div>Hello World!</div>
    		)
    	}
    )
    ```

### 状态

React 把组件看成是一个状态机（State Machines）。通过与用户的交互，实现不同状态，然后渲染UI，让用户界面和数据保持一致。
React里，只需更新组件的state，然后根据新的state重新渲染用户界面（不要操作DOM）。

重要的方法：

-   getlnitialstate：定义初始状态（ES6中已不再使用，改成在constructor中设定）
-   this.state：读取状态
-   this.setState：更新组件的状态

**ES6中state的初始化**

```
constructor（props）{
	super（props）；
	this.state={items:[]，text:''}；
}
```

### 事件

1.  事件-使用发生在组件上的事件
    事件绑定写法onClick，注意：必须写成驼峰形式，即事件的首字母要大写。
2.  得到在浏览器上显示的元素-**refs**