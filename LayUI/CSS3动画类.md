# CSS3动画类

>   在实用价值的前提之下，我们并没有内置过多花俏的动画。而他们同样在 layui 的许多交互元素中，发挥着重要的作用。layui 的动画全部采用 CSS3，因此不支持ie8和部分不支持ie9（即ie8/9无动画）

动画的使用非常简单，直接对元素赋值动画特定的 class 类名即可。如：

```
其中 layui-anim 是必须的，后面跟着的即是不同的动画类
<div class="layui-anim layui-anim-up"></div>
 
循环动画，追加：layui-anim-loop
<div class="layui-anim layui-anim-up layui-anim-loop"></div>
```

内置CSS3动画一览表

下面是不同的动画类名，数量可能有点少的样子？但正如开头所讲的，拒绝冗余花俏，拥抱精简实用。*点击下述绿色块，可直接预览动画*

-   从最底部往上滑入

    layui-anim-up

-    

-   微微往上滑入

    layui-anim-upbit

-    

-   平滑放大

    layui-anim-scale

-    

-   弹簧式放大

    layui-anim-scaleSpring

-   渐现

    layui-anim-fadein

-    

-   渐隐

    layui-anim-fadeout

-    

-   360度旋转

    layui-anim-rotate

-    

-   循环动画

    追加：layui-anim-loop