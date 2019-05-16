# Swiper4

## 一、Swiper4.x的全部配置选项、方法、函数

### 1. Basic(swiper一般选项)
#### 1.1 initialSlide设定初始化时slide的索引。设置为1后，Swiper初始化时默认显示第2个轮播图
#### 1.2 direction设置Slides的滑动方向，可设置水平(horizontal)或垂直(vertical)。horizontal：横向切换 ，vertical：竖向切换。

#### 1.3 speed切换速度，即slider自动滑动开始到结束的时间（单位ms），也是触摸滑动时释放至贴合的时间。
#### 1.4 grabCursor设置为true时，鼠标覆盖Swiper时指针会变成手掌形状，拖动时指针会变成抓手形状。（根据浏览器形状有所不同）
#### 1.5 parallax设置为true开启视差效果。
效果可以应用于container或slide的子元素。当应用于container的子元素（常用于视差背景图），每次切换时视差效果仅有设定值的slide个数-1分之1
视差位移变化
在所需要的元素上增加data-swiper-parallax属性（与Swiper切换方向相同）或data-swiper-parallax-x （x方向） data-swiper-parallax-y（y方向）
data-swiper-parallax接受两种类型的参数。
          number（单位：px），如-300，从右边300px进入左边出去。
          percentage（百分比），移动距离=该元素宽度 * percentage。
          视差透明度变化
在所需要的元素上增加data-swiper-parallax-opacity属性。可选值0-1，如0.5，从半透明进入半透明出去
视差缩放变化
在所需要的元素上增加data-swiper-parallax-scale属性。可选值如0.5，从一半大小进入一半大小出去
还可通过data-swiper-parallax-duration设定视差动画持续时间（ms）。默认值是Swiper的speed，与切换时间同步。
*设定透明度或缩放必须同时设定位移，否则无效(4.0.5) 
```
<div data-swiper-parallax="0" data-swiper-parallax-opacity="0.5" >透明度变化</div>
<div class="swiper-container">
<div style="background-image:url(/img/Parallax.jpg)" data-swiper-parallax="-23%" data-swiper-parallax-duration="3000"></div>
    <div class="swiper-wrapper">
       <div class="swiper-slide">
            <div class="title" data-swiper-parallax="-100">从右边100px开始进入</div>
            <div class="subtitle" data-swiper-parallax="-200">从右边200px开始进入</div>
            <div class="text" data-swiper-parallax="-300" data-swiper-parallax-duration="600">
              <p>从右边300px开始进入，时间600ms</p>
            </div>
            <div data-swiper-parallax="0" data-swiper-parallax-opacity="0.5" >透明度变化</div>
            <div data-swiper-parallax-scale="0.15" >缩放变化</div>
        </div>
    </div>
    </div>
<script language="javascript"> 
    var mySwiper = new Swiper('.swiper-container',{
            parallax : true,
    })
    </script>
       <div data-swiper-parallax="0" data-swiper-parallax-opacity="0.5" >透明度变化</div>
            <div data-swiper-parallax-scale="0.15" >缩放变化</div>
        </div>
    </div>
    </div>
<script language="javascript"> 
    var mySwiper = new Swiper('.swiper-container',{
            parallax : true,
    })
    </script>
```
#### 1.6 setWrapperSize
Swiper使用flexbox布局(display: flex)，开启这个设定会在Wrapper上添加等于slides相加的宽或高，在对flexbox布局的支持不是很好的浏览器中可能需要用到。
#### 1.7 virtualTranslate
虚拟的位移。当你启用这个参数，Slide不会移动，但是Swiper还是在运行，例如progress，active-slide，各种回调等。当你想自定义一些slide切换效果时可以用。例如配合上progress。
启用这个选项时slideChange和transition等事件有效（与Swiper3.x不同）。可以用来使Swiper的滑动停止（锁定）。
#### 1.8 a11y
辅助，无障碍阅读。开启本参数为屏幕阅读器添加语音提示等信息，方便视觉障碍者。基于ARIA标准。
prevSlideMessage    类型：string  默认：'Previous slide'    在屏幕阅读器为上一页按钮添加信息。
nextSlideMessage    类型：string  默认： 'Next slide'     在屏幕阅读器为下一页按钮添加信息。
firstSlideMessage    类型：string  默认： 'This is the first slide'    在屏幕阅读器当处于第一个slide为上一页按钮添加信息。
lastSlideMessage    类型：string  默认： 'This is the last slide'    在屏幕阅读器当处于最后一个slide为下一页按钮添加信息。
paginationBulletMessage    类型：string  默认： 'Go to slide {{index}}'    在屏幕阅读器为分页器小点添加信息。
notificationClass    类型：string  默认：'swiper-notification'   A11y公告部分的类名。
```
<script language="javascript"> 
  var mySwiper = new Swiper('.swiper-container',{
    navigation: {
      nextEl: '.swiper-button-next',
      prevEl: '.swiper-button-prev',
    },
    pagination: {
      el: '.swiper-pagination',
    },
    a11y : {
      prevSlideMessage: 'Previous slide',
      nextSlideMessage: 'Next slide',
      firstSlideMessage: 'This is the first slide',
      lastSlideMessage: 'This is the last slide',
      paginationBulletMessage: 'Go to slide {{index}}',
      notificationClass: 'swiper-notification',
    },
  }) 
  </script>
```
#### 1.9 width
强制Swiper的宽度(px)，当你的Swiper在隐藏状态下初始化时才用得上。这个参数会使自适应失效。
#### 1.10 height
强制Swiper的高度(px)，当你的Swiper在隐藏状态下初始化时且切换方向为垂直才用得上。这个参数会使自适应失效。
#### 1.11 roundLengths
设定为true将slide的宽和高取整(四舍五入)以防止某些分辨率的屏幕上文字或边界(border)模糊。
例如在1440宽度设备上，当你设定slide宽为76%时，则计算出来结果为1094.4，开启后宽度取整数1094。
#### 1.12 breakpoints
断点设定：根据屏幕宽度设置某参数为不同的值，类似于响应式布局的media screen。
只有部分不需要变换布局方式和逻辑结构的参数支持断点设定，如slidesPerView、slidesPerGroup、 spaceBetween，而像slidesPerColumn、loop、direction、effect等则无效。
```
<script>
var swiper = new Swiper('.swiper-container', {
  slidesPerView: 4,
  spaceBetween: 40,
  breakpoints: { 
    //当宽度小于等于320
    320: {
      slidesPerView: 1,
      spaceBetween: 10
    },
   //当宽度小于等于480
    480: { 
      slidesPerView: 2,
      spaceBetween: 20
    },
    //当宽度小于等于640
    640: {
      slidesPerView: 3,
      spaceBetween: 30
    }
  }
  })
</script>
```
#### 1.13 autoHeight
自动高度。设置为true时，wrapper和container会随着当前slide的高度而发生变化。
#### 1.14 uniqueNavElements
独立分页元素，当启用（默认）并且分页元素的传入值为字符串时，swiper会优先查找子元素匹配这些元素。可应用于分页器，按钮和滚动条（pagination, prev/next buttons and scrollbar elements）。
当你的控制组件放在container外面的时候，需要用到。
效果演示
```
<script language="javascript"> 
var mySwiper = new Swiper('.swiper-container',{
  pagination: {
    el: '.swiper-pagination',
  },
  uniqueNavElements: false,
  })
</script>
```
#### 1.15 nested
用于嵌套相同方向的swiper时，当切换到子swiper时停止父swiper的切换。
请将子swiper的nested设置为true。
由于需要在slideChangeEnd时判断作用块，因此快速滑动时这个选项无效。
```
<script> 
var mySwiper = new Swiper('#swiper-container1')//父swiper
var mySwiper2 = new Swiper('#swiper-container2',{//子swiper
  nested:true,
  resistanceRatio: 0,
  })
</script>
```
#### 1.16 runCallbacksOnInit
如果你的初始化slide不是第一个(例initialSlide:2)或者设置了loop: true，那么初始化时会触发一次 [Transition/SlideChange] [Start/End] 回调函数，如果不想触发，设置为false。
#### 1.17 watchOverflow
当没有足够的slide切换时，例如只有1个slide（非loop），swiper会失效且隐藏导航等。默认不开启这个功能。
```
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide blue-slide">
      slider1</div>
  </div>
  <div class="swiper-pagination"></div>
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>
  <div class="swiper-scrollbar"></div>
  </div>
<script> 
var mySwiper = new Swiper('.swiper-container',{
  watchOverflow: true,//因为仅有1个slide，swiper无效
  navigation: {
    nextEl: '.swiper-button-next',//自动隐藏
    prevEl: '.swiper-button-prev',//自动隐藏
  },
  pagination: {
    el: '.swiper-pagination',//自动隐藏
  },
  scrollbar: {
    el: '.swiper-scrollbar',//自动隐藏
  },
  })
</script>
```
#### 1.18 on
注册事件，Swiper4.0开始使用关键词this指代Swiper实例。
```
<script language="javascript"> 
var mySwiper = new Swiper('.swiper-container', {
  on: {
    slideChange: function () {
      console.log(this.activeIndex);
    },
  },
  };
//或者
var mySwiper = new Swiper('.swiper-container');
mySwiper.on('slideChange', function () {
  //...
  });
</script>
```
#### 1.19 init
当你创建一个Swiper实例时是否立即初始化。
如果禁止了，可以稍后使用mySwiper.init()来初始化。
```
<script language="javascript"> 
var mySwiper = new Swiper('.swiper-container',{
  init: false,
  })
mySwiper.init();//现在才初始化
</script>
```
#### 1.20preloadImages
默认为true，Swiper会强制加载所有图片。
#### 1.21updateOnImagesReady
当所有的内嵌图像（img标签）加载完成后Swiper会重新初始化。使用此选项需要先开启preloadImages: true
### 2. Slides grid(网格分布)
#### 2.1 centeredSlides
设定为true时，active slide会居中，而不是默认状态下的居左。
#### 2.2 slidesPerView
设置slider容器能够同时显示的slides数量(carousel模式)。
可以设置为数字（可为小数，小数不可loop），或者 'auto'则自动根据slides的宽度来设定数量。
loop模式下如果设置为'auto'还需要设置另外一个参数loopedSlides。
#### 2.3 slidesPerGroup
在carousel mode下定义slides的数量多少为一组。
#### 2.4 spaceBetween
在slide之间设置距离（单位px）。
#### 2.5 slidesPerColumn
多行布局里面每列的slide数量。设置显示几行
#### 2.6 slidesPerColumnFill
多行布局中以什么形式填充：（数字代表第几张轮播图）
'column'（列）
1    3    5
2    4    6
'row'（行）。
1    2    3
4    5    6
#### 2.7 slidesOffsetBefore
设定slide与左边框的预设偏移量（单位px）。
#### 2.8 slidesOffsetAfter
设定slide与右边框的预设偏移量（单位px）。
#### 2.9 normalizeSlideIndex
使你的活动块指示为最左边的那个slide（没开启centeredSlides时）
### 3. Free Mode（free模式/抵抗反弹）
#### 3.1 freeMode
默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动可能不止一格且不会贴合。
#### 3.2 freeModeMomentum
free模式动量。free模式下，若设置为false则关闭动量，释放slide之后立即停止不会滑动。
#### 3.3 freeModeMomentumRatio
free模式动量值（移动惯量）。设置的值越大，当释放slide时的滑动时间越长。默认1s。
#### 3.4 freeModeMomentumVelocityRatio
free模式惯性速度，设置越大，释放后滑得越快。
#### 3.5 freeModeMomentumBounce
动量反弹。false时禁用free模式下的动量反弹，slides通过惯性滑动到边缘时，无法反弹。注意与[resistance](https://www.swiper.com.cn/api/touch/resistance.html)（手动抵抗）区分。
#### 3.6 freeModeMomentumBounceRatio
值越大产生的边界反弹效果越明显，反弹距离越大。
#### 3.7 freeModeSticky
使得freeMode也能自动贴合。
#### 3.8 freeModeMinimumVelocity
触发FreeMode惯性的最小触摸速度（px/ms），低于这个值不会惯性滑动  
### 4. LOOP(环路)
#### 4.1 loop
设置为true 则开启loop模式。loop模式：会在原本slide前后复制若干个slide(默认一个)并在合适的时候切换，让Swiper看起来是循环的。 
loop模式在与free模式同用时会产生抖动，因为free模式下没有复制slide的时间点。
#### 4.2 loopAdditionalSlides
loop模式下会在slides前后复制若干个slide,，前后复制的个数不会大于原总个数。
默认为0，前后各复制1个。0,1,2 --> 2,0,1,2,0
例：取值为1，0,1,2 --> 1,2,0,1,2,0,1
例：取值为2或以上，0,1,2 --> 0,1,2,0,1,2,0,1,2
#### 4.3 loopedSlides
在loop模式下使用slidesPerview:'auto'，还需使用该参数设置所要用到的loop个数(一般设置为本来slide的个数)。
#### 4.4 loopFillGroupWithBlank
在loop模式下，为group填充空白slide
### 5. Progress（进度）
#### 5.1 watchSlidesProgress
开启这个参数来计算每个slide的progress(进度、进程)，Swiper的progress无需设置即开启。
#### 5.2 watchSlidesVisibility
开启watchSlidesVisibility选项前需要先开启watchSlidesProgress，如果开启了watchSlidesVisibility，则会在每个可见slide增加一个classname，默认为'swiper-slide-visible'。
### 6. Clicks(点击)
#### 6.1 slideToClickedSlide
设置为true则点击slide会过渡到这个slide。
#### 6.1 touchRatio
触摸比例。触摸距离与slide滑动距离的比率。设置为0.5后slide滑动距离只有触摸距离的一半，变得难以滑动。设置为-1后与拖动方向相反的Swiper
#### 6.2 preventClicksPropagation
阻止click冒泡。拖动Swiper时阻止click事件。
### 7. TOUCHES(触发条件)
#### 7.1 touchRatio
触摸比例。触摸距离与slide滑动距离的比率。
默认为1，按照1:1的触摸比例滑动。设置为0时，完全无法滑动
#### 7.2 simulateTouch
鼠标模拟手机触摸。默认为true，Swiper接受鼠标点击、拖动。
#### 7.3 allowTouchMove
允许触摸滑动。设为false时，slide无法滑动，只能使用扩展API函数例如[slideNext() ](https://www.swiper.com.cn/api/methods/107.html)或[slidePrev()](https://www.swiper.com.cn/api/methods/108.html)或[slideTo()](https://www.swiper.com.cn/api/methods/109.html)等改变slides滑动。等同于Swiper3.x 的 onlyExternal。
#### 7.4 followFinger
跟随手指。如设置为false，手指滑动时slide不会动，当你释放时slide才会切换。
#### 7.5 shortSwipes
默认允许短切换。设置为false时，只能长切换，进行快速且短距离的滑动无法触发切换。
#### 7.6 longSwipes
设置为false时，进行长时间长距离的拖动无法触发Swiper。
#### 7.7 longSwipesMs
定义longSwipes的时间（单位ms），超过则属于longSwipes。
#### 7.8 longSwipesRatio
进行longSwipes时触发swiper所需要的最小拖动距离比例，即定义longSwipes距离比例。值越大触发Swiper所需距离越大。最大值0.5。
#### 7.9 threshold
拖动的临界值（单位为px），如果触摸距离小于该值滑块不会被拖动。
#### 7.10 touchAngle
允许触发拖动的角度值。默认45度，即使触摸方向不是完全水平也能拖动slide。
#### 7.11 touchStartPreventDefault
阻止`touchstart` (`mousedown`)的默认事件，设置为false则不阻止。
#### 7.12 touchStartForcePreventDefault
是否强制阻止`touchstart` (`mousedown`)的默认事件，即使Swiper不允许滑动(allowTouchMove:false)。
#### 7.13 ouchMoveStopPropagation
true时阻止touchmove冒泡事件。
#### 7.14 resistance
边缘抵抗。当swiper已经处于第一个或最后一个slide时，继续拖动Swiper会离开边界，释放后弹回。边缘抵抗就是拖离边界时的抵抗力。值为false时禁用，将slide拖离边缘时完全没有抗力。
#### 7.15 resistanceRatio
抵抗率。边缘抵抗力的大小比例。值越小抵抗越大越难将slide拖离边缘，0时完全无法拖离。
#### 7.16 iOSEdgeSwipeDetection
设置为true开启IOS的UIWebView环境下的边缘探测。如果拖动是从屏幕边缘开始则不触发swiper。
这样当你在屏幕边缘滑动Swiper时，则可以返回上一页（history.back）或切换至下一页
#### 7.17 iOSEdgeSwipeThreshold / edgeSwipeThreshold
IOS的UIWebView环境下的边缘探测距离。如果拖动小于边缘探测距离则不触发swiper。
4.3.5版本以后改名为edgeSwipeThreshold，原命名iOSEdgeSwipeThreshold仍然可用。
#### 7.18 passiveListeners
用来提升swiper在移动设备的中的scroll表现（Passive Event Listeners），但是会和e.preventDefault冲突，所以有时候你需要关掉它。
#### 7.19 touchReleaseOnEdges
当滑动到Swiper的边缘时释放滑动，可以用于同向Swiper的嵌套（移动端触摸有效）。
#### 7.20 touchEventsTarget
接受touch事件的目标，可以设为container或者wrapper。
### 8. Swiping/No swiping（禁止切换）
#### 8.1 preventInteractionOnTransition
如果开启这个选项，当你的Swiper在过渡时将无法滑动
#### 8.2 noSwiping
设为true时，可以在slide上（或其他元素）增加类名'swiper-no-swiping'，使该slide无法拖动，希望文字被选中时可以考虑使用。
该类名可通过[noSwipingClass](https://www.swiper.com.cn/api/Swiping/2014/1217/77.html)修改。
#### 8.3 noSwipingSelector
设置不可触摸滑动的元素，例如input
#### 8.4 noSwipingClass
不可拖动块的类名，当[noSwiping](https://www.swiper.com.cn/api/Swiping/2014/1217/39.html)设置为true时，并且在slide（或其他元素）加上此类名，目标将无法触摸拖动。
#### 8.5 allowSlideNext
设置为false可禁止向右或下滑动。
#### 8.6 allowSlidePrev
设为false可禁止向左或上滑动。
#### 8.7 swipeHandler
CSS选择器或者HTML元素。你只能拖动它进行swiping。
### 9. observer（监视器）
#### 9.1 observer
启动动态检查器(OB/观众/观看者)，当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper。
默认false，不开启，可以使用[update()](https://www.swiper.com.cn/api/methods/257.html)方法更新。
#### 9.2 observeParents
将observe应用于Swiper的父元素。当Swiper的父元素变化时，例如window.resize，Swiper更新。
#### 9.3 observeSlideChildren
子slide更新时，swiper是否更新。默认为false不更新。
### 10. Namespace（命名空间）
#### 10.1 wrapperClass
设置wrapper的css类名。
#### 10.2 slideClass
设置slide的类名。
#### 10.3 slideActiveClass
设置活动块的类名。
#### 10.4 slideVisibleClass
设置可视块的类名。
#### 10.5 slideDuplicateClass
loop模式下被复制的slide的类名。
#### 10.6 slideNextClass
active slide的下一个slide的类名。
#### 10.7 slidePrevClass
active slide的前一个slide的类名。
#### 10.8 slideDuplicatedActiveClass
loop模式下活动块对应复制块的类名，或者相反。
#### 10.9 slideDuplicatedNextClass
loop模式下，下一个slide对应复制块的类名，或者相反。
#### 10.10 slideDuplicatedPrevClass
loop下，前一个slide对应复制块的类名，或者相反。
#### 10.11 containerModifierClass
可以修改某些以swiper-container-为开头的类名。
### 11. Callbacks（回调函数）
#### 11.1 init
回调函数，初始化后执行。
#### 11.2 touchStart(event)
回调函数，当碰触到slider时执行。可选touchstart事件作为参数。
#### 11.3 touchMove(event)
手指触碰Swiper并滑动（手指）时执行，接受touchmove事件作为参数。此时slide不一定会发生移动，比如你手指的移动方向和swiper的切换方向垂直时。对比[sliderMove](https://www.swiper.com.cn/api/event/224.html)。
#### 11.4 touchEnd(event)
回调函数，触摸释放时执行，接受 touchend事件作为参数。（释放即执行）
#### 11.5 slideChangeTransitionStart
回调函数，swiper从当前slide开始过渡到另一个slide时执行。
与 Swiper3.x版本中的onSlideChangeStart(swiper)不同的是，即使释放slide时没有达到过渡条件而回弹也会触发这个函数。
输出的activeIndex是过渡后的slide索引。
#### 11.6 slideChangeTransitionEnd
回调函数，swiper从一个slide过渡到另一个slide结束时执行。
#### 11.7 imagesReady
回调函数，所有内置图像加载完成后执行，同时“updateOnImagesReady”需设置为“true’。
#### 11.8 ransitionStart
回调函数，过渡开始时触发。
**Swiper运作原理**
Swiper常用运作方式有两种：手动触摸切换或者导航切换（前进后退按钮，键盘控制，分页器，内置方法slideTo等）
\1. 手动触摸切换拖动阶段Swiper根据手势位置实时设定wrapper的位移（setTranslate），释放拖动时Swiper会设定一次wrapper自由过渡（setTranslate、setTransition、transitionStart、slideChangeTransitionStart）。速度为speed直到过渡结束（transitionEnd、slideChangeTransitionEnd）。
\2. 导航切换可参考手动触摸释放阶段
#### 11.9 transitionEnd
回调函数，过渡结束时触发。
如果你使用setWrapperTranslate和setWrapperTransition来设定wrapper移动，这个函数不会触发，你可以使用原生transitionEnd事件。
人为中断过渡不会触发这个函数
#### 11.10 touchMoveOpposite(event)
回调函数。当手指触碰Swiper并且没有按照[direction](https://www.swiper.com.cn/api/parameters/direction.html)设定的方向移动时执行。此时slide没有被拖动，这与sliderMove事件相反。可选touchmove事件作为参数。
#### 11.11 sliderMove(event)
回调函数，手指触碰Swiper并拖动slide时执行。接受touchmove事件作为参数。
#### 11.12 click(event)
回调函数，当你点击或轻触Swiper 300ms后执行。
接受touchend事件作为参数。
**触发时机**
如果没有触发[touchMove()](https://www.swiper.com.cn/api/event/touchMove.html)，则释放触摸/鼠标时：
1.立即执行[tap()](https://www.swiper.com.cn/api/event/tap.html)
2.如果触摸/鼠标按压时间小于300ms，并且两次触摸/点击间隔大于300ms，延迟300ms执行onClick
3.如果触摸/鼠标按压时间小于300ms，并且两次触摸/点击间隔小于300ms，立即执行[doubleTap](https://www.swiper.com.cn/api/event/doubleTap.html)
#### 11.13 tap(event)
回调函数，当你轻触(tap)Swiper后执行。在移动端，click会有 200~300 ms延迟，所以请用tap代替click作为点击事件。
接受touchend事件作为参数
#### 11.14 doubleTap(event)
回调函数，当你两次轻触Swiper 时执行，类似于双击。
接受touchend事件作为参数。
#### 11.15 progress(progress)
回调函数，当Swiper的progress被改变时执行。接受Swiper的progress作为参数（0-1）。
#### 11.16 reachBeginning()
回调函数，Swiper切换到初始化位置时执行。
#### 11.17 reachEnd()
回调函数，当Swiper切换到最后一个Slide时执行。
#### 11.18 beforeDestroy()
回调函数，销毁Swiper时执行。
#### 11.19 setTransition(transition)
回调函数，每当设置Swiper开始过渡动画时执行。transtion获取到的是Swiper的[speed](https://www.swiper.com.cn/api/parameters/speed.html)值。
#### 11.20 resize()
当你的浏览器尺寸发生变化时执行。
#### 11.21 setTranslate(translate)
回调函数。当设置wrapper的偏移量时执行。可选swiper对象和wrapper的偏移量作为参数。
当触摸切换Swiper时Swiper分两步骤执行：
\1. 接触期间根据触摸位置实时设置Wrapper的translate，此时实时执行setTranslate。
\2. 手指放开时设定一次translate和transition，此时执行一次setTranslate和[setTransition](https://www.swiper.com.cn/api/event/setTransition.html)、[transitionStart](https://www.swiper.com.cn/api/event/transitionStart.html)。切换结束时执行[transitionEnd](https://www.swiper.com.cn/api/event/transitionEnd.html)一次。
#### 11.22 slideNextTransitionStart
回调函数，滑块释放时如果触发slider向前(右、下)切换则执行。类似于slideChangeTransitionStart，但规定了方向。
#### 11.23 slideNextTransitionEnd
回调函数，slider向前(右、下)切换结束时执行。类似于slideChangeTransitionEnd，但规定了方向。
#### 11.24 slidePrevTransitionStart
回调函数，滑块释放时如果触发slider向后(左、上)切换则执行。类似于slideChangeTransitionStart，但规定了方向。
#### 11.25 slidePrevTransitionEnd
回调函数，slider向后(左、上)切换结束时执行。类似于slideChangeTransitionEnd，但规定了方向。
#### 11.26 fromEdge
当Swiper是从第一个或最后一个Slide切换时执行
#### 11.27 slideChange
当当前Slide切换时执行(activeIndex发生改变)
#### 11.28 autoplayStart
回调函数，自动切换开始时执行(由不自动切换进入到自动切换)。
#### 11.29 autoplayStop
回调函数，自动切换结束时执行（由自动切换进入到不自动切换）。
#### 11.30 autoplay
回调函数，在slide自动切换开始时执行。
### 12. Properties（Swiper 性）
#### 12.1 mySwiper.activeIndex
返回当前活动块(激活块)的索引。loop模式下注意该值会被加上复制的slide数。
#### 12.2 mySwiper.realIndex
当前活动块的索引，与activeIndex不同的是，在loop模式下不会将[复制的块](https://www.swiper.com.cn/api/Loop/2014/1215/23.html)的数量计算在内。
#### 12.3 mySwiper.previousIndex
返回上一个活动块的索引，切换前的索引。
#### 12.4 mySwiper.width
获取swiper容器的宽度。
#### 12.5 mySwiper.height
获取swiper容器的高度。
#### 12.6 mySwiper.touches
返回包含触控信息的对象数组，就是这5个。
mySwiper.touches.startX    触摸开始点的X值
mySwiper.touches.startY    触摸开始点的Y值
mySwiper.touches.currentX    触摸当前点的X值
mySwiper.touches.currentY    触摸当前点的Y值
mySwiper.touches.diff    当前滑动方向的触摸滑动距离
#### 12.7 mySwiper.params
重要参数，获取Swiper对象初始化参数，或者重写该参数，如： mySwiper.params.speed = 200。
*不是所有参数都可以重写。
#### 12.8 mySwiper.$el
swiper的container的[Dom7/jQuery对象](https://www.swiper.com.cn/usage/dom7/)。可以通过mySwiper.el得到container的HTML元素。
#### 12.9 mySwiper.$wrapperEl
获取swiper的wrapper的[Dom7](https://www.swiper.com.cn/usage/dom7/)对象。可以通过mySwiper.wrapperEl得到wrapper的HTML元素。
如需拿到slides的总宽度，需要设置wrapper的[setWrapperSize](https://www.swiper.com.cn/api/parameters/263.html)
#### 12.10 mySwiper.slides
获取Swiper的slides的[Dom7/jQuery对象](https://www.swiper.com.cn/usage/dom7/)。通过mySwiper.slides[1]获取特定的slide。
如需拿到slides的总宽度，需要设置wrapper的[setWrapperSize](https://www.swiper.com.cn/api/parameters/263.html)
#### 12.11 mySwiper.translate
这个属性可以获取到wrapper的位移，过渡中得到的则是过渡完成时的位移。如需实时位移可以使用 [swiper.getTranslate()](https://www.swiper.com.cn/api/methods/116.html)
#### 12.12 mySwiper.progress
获取Swiper的progress值。
对于swiper的progress属性，活动的slide在最左（上）边时为0，活动的slide在最右（下）边时为1，其他情况平分。例：有6个slide，当活动的是第三个时swiper的progress属性是0.4，当活动的是第五个时swiper的progress属性是0.8。
如果想通过progress来控制swiper的切换，可以配合[swiper.setTranslate()](https://www.swiper.com.cn/api/methods/117.html)方法，该方法需要将progress乘以swiper的(总)宽度
-progress*swiper.width*(swiper.slides.length-1) 
#### 12.13 mySwiper.isBeginning
如果Swiper位于最左/上，这个值为true。
#### 12.14 mySwiper.isEnd
如果Swiper位于最右/下，这个值为true。
#### 12.15 mySwiper.animating
如果Swiper正在过渡（自由滑动），这个值为true。
#### 12.16 mySwiper.clickedIndex
返回最后点击Slide的索引。(click)
#### 12.17 mySwiper.clickedSlide
返回最后点击（非拖动）的Slide的HTML元素。
#### 12.18 mySwiper.allowSlideNext
提示或设置是否允许切换至下一个slide。
#### 12.19 mySwiper.allowSlidePrev
设置/提示是否允许切换至前一个slide
#### 12.20 mySwiper.allowTouchMove
设置/查看是否禁止触摸滑动。
### 13. Methods（Swiper方法）
#### 13.1 mySwiper.slideNext(speed, runCallbacks)
滑动到下一个滑块。
speed：可选，切换速度
runCallbacks：可选，设为false不触发transition回调函数
#### 13.2 mySwiper.slidePrev(speed,runCallbacks)
滑动到前一个滑块。
speed：可选，切换速度
runCallbacks：可选，设为false不触发transition回调函数
#### 13.3 mySwiper.slideTo(index, speed, runCallbacks)
Swiper切换到指定slide。
index:必选，num，指定将要切换到的slide的索引。
speed:可选，num(单位ms)，切换速度
runCallbacks: 可选，boolean，设置为false时不会触发transition回调函数。
#### 13.4 mySwiper.slideToLoop(index, speed, runCallbacks)
在Loop模式下Swiper切换到指定slide。切换到的是slide索引是**realIndex**
index:必选，num，指定将要切换到的slide的索引。
speed:可选，num(单位ms)，切换速度
runCallbacks: 可选，boolean，设置为false时不会触发transition回调函数。
#### 13.5 mySwiper.destroy(deleteInstance, cleanupStyles)
销毁Swiper。销毁所有绑定的监听事件，移除鼠标键盘事件，释放浏览器内存。
deleteInstance:可选，设为false则不销毁Swiper对象，默认为true。
cleanupStyles:可选，设为true则清除所有swiper设定选项和样式，比如direction等，默认为false。
#### 13.6 mySwiper.getTranslate()
返回实时的wrapper位移（translate）。
这与通过属性[mySwiper.translate](https://www.swiper.com.cn/api/properties/translate.html) 获取到的数值稍有不同，即使是在过渡时（[animating](https://www.swiper.com.cn/api/properties/animating.html)）也能获取到，而后者精度较高
#### 13.7 mySwiper.setTranslate(translate)
手动设置wrapper的位移。在其他非位移的切换时则表现为相应的效果，例如3D切换时改变的是角度。
translate：必选，位移值（单位px）。
例：swiper宽度为500，设置translate为-250。在默认的effect: slide时，swiper会向左滑动250px，如果设置了切换效果effect: cube，swiper会旋转45度。
#### 13.8 mySwiper.updateSize()
这个方法会重新计算Swiper的尺寸。
#### 13.9 mySwiper.updateSlides()
这个方法会重新计算Slides的数量，当你使用js来删除slide时可能会用到。使用[mySwiper.removeSlide](https://www.swiper.com.cn/api/methods/removeSlide.html)来删除slide则会自动计算，无需使用此方法。
#### 13.10 mySwiper.updateProgress()
这个方法会重新计算Swiper的progress值。
#### 13.11 mySwiper.updateSlidesClasses()
更新slides和bullets的active/prev/next 类名。
#### 13.12 mySwiper.update(updateTranslate)
更新Swiper，这个方法包含了updateContainerSize，updateSlidesSize，updateProgress，updateClasses方法。
可选参数：updateTranslate，默认false，设置为true则重新计算Wrapper的位移。
#### 13.13 mySwiper.detachEvents()
移除所有监听事件。
#### 13.14 mySwiper.attachEvents()
重新绑定所有监听事件。
#### 13.15 mySwiper.appendSlide(slides)
添加slide到slides的结尾。可以是HTML元素或slide数组，例
```
mySwiper.appendSlide('<div class="swiper-slide">Slide 10</div>')
mySwiper.appendSlide([ '<div class="swiper-slide">Slide 10</div>', '<div class="swiper-slide">Slide 11</div>' ]);
```
#### 13.16 mySwiper.prependSlide(slides)
添加slide到slides的第一个位置。可以是HTML元素或slide数组，例
```
mySwiper.prependSlide('<div class="swiper-slide">Slide 0</div>')
mySwiper.prependSlide([ '<div class="swiper-slide">Slide 1</div>', '<div class="swiper-slide">Slide 2</div>' ]);
```
#### 13.17 mySwiper.addSlide(index, slides);
在指定位置增加slide。可以是HTML元素或slide数组，例
```
mySwiper.addSlide(1, '<div class="swiper-slide">Slide 10"</div>')
mySwiper.addSlide(1, [ '<div class="swiper-slide">Slide 10"</div>', '<div class="swiper-slide">Slide 11"</div>' ]);
```
#### 13.18 mySwiper.removeSlide(index)
移除索引为index的slide。例如：
mySwiper.removeSlide(0); //移除第一个
mySwiper.removeSlide([0, 1]); //移除第一个和第二个
#### 13.19 mySwiper.removeAllSlides()
移除所有slides。
#### 13.20 mySwiper.on(event,handler)
添加回调函数或者事件句柄。
```
var mySwiper = new Swiper( '.swiper-container')
mySwiper.on('click', function(){
  //some code
})
等同于
var mySwiper = new Swiper( '.swiper-container', {
  on:{
    click: function(){
      //some code
    }
  }
})
或
$('.swiper-container').on('click mousedown', function(e) {
  //some code
})
```
#### 13.21 mySwiper.once(event,handler)
添加回调函数或者事件句柄，这些事件只会执行一次。
#### 13.22 mySwiper.off(event)
移除事件的所有句柄
#### 13.23 mySwiper.off(event, handler)
移除某个回调/事件。
#### 13.24 mySwiper.setGrabCursor()
开启鼠标的抓手形状，相当于开启[grabCursor](https://www.swiper.com.cn/api/parameters/grabCursor.html)。
#### 13.25 mySwiper.unsetGrabCursor()
关闭鼠标的抓手形状。
#### 13.26 mySwiper.updateAutoHeight(speed)
当autoHeight为启用状态，设置更新swiper高度的时间。
speed:number 速度ms(可选)
#### 13.27 mySwiper.slideToClosest(speed, runCallbacks);
使得Swiper贴合边缘，当你使用freeMode时可能会需要。
speed:number 贴合速度ms(可选)
runCallbacks:boolean 贴合时是否产生transition事件，默认true
## 二、组件. Autoplay自动切换
### 1. Autoplay（自动切换）
#### 1.1 autoplay
设置为true启动自动切换，并使用默认的切换设置。
要注意Swiper4.x与Swiper3.x的写法不同导致的超快速切换。
#### 1.2 delay
自动切换的时间间隔，单位ms
你还可以在某个slide上设置单独的停留时间，例
`<div class="swiper-slide" data-swiper-autoplay="2000">`
#### 1.3 stopOnLastSlide
如果设置为true，当切换到最后一个slide时停止自动切换。（loop模式下无效）。
#### 1.4 disableOnInteraction
用户操作swiper之后，是否禁止[autoplay](https://www.swiper.com.cn/api/basic/2014/1213/16.html)。默认为true：停止。
如果设置为false，用户操作swiper之后自动切换不会停止，每次都会重新启动autoplay。
操作包括触碰，拖动，点击pagination等。
#### 1.5 reverseDirection
开启反向自动轮播。
#### 1.6 waitForTransition
等待过渡完毕。自动切换会在slide过渡完毕后才开始计时。
虚拟位移状态下自动切换（[virtualTranslate](https://www.swiper.com.cn/api/parameters/264.html)）可能需要关闭此选项。
#### 1.7 mySwiper.autoplay.running
如果Swiper开启了autoplay，这个值为true。
#### 1.8 mySwiper.autoplay.start()
开始自动切换。一般用来做“Play”按钮。
#### 1.9 mySwiper.autoplay.stop()
停止自动切换。一般用来制作“pause”按钮。
### 2. Effects（切换效果）
#### 2.1 effect
slide的切换效果，默认为"slide"（位移切换），可设置为'slide'（普通切换、默认）,"fade"（淡入）"cube"（方块）"coverflow"（3d流）"flip"（3d翻转）。
#### 2.2 fadeEffect
fade效果参数。可选参数：crossFade。
默认：false。关闭淡出。过渡时，原slide透明度为1（不淡出），过渡中的slide透明度从0->1（淡入），其他slide透明度0。
可选值：true。开启淡出。过渡时，原slide透明度从1->0（淡出），过渡中的slide透明度从0->1（淡入），其他slide透明度0。
当你的slide中图片大小不同时可以用到。
#### 2.3 cubeEffect
cube效果参数，可选值：
slideShadows：开启slide阴影。默认 true。
shadow： 开启投影。默认 true。
shadowOffset：投影距离。默认 20，单位px。
shadowScale： 投影缩放比例。默认0.94。
#### 2.4 coverflowEffect
cover flow是类似于苹果将多首歌曲的封面以3D界面的形式显示出来的方式。coverflow效果参数，可选值：
rotate：slide做3d旋转时Y轴的旋转角度。默认50。
stretch：每个slide之间的拉伸值，越大slide靠得越紧。 默认0。
depth：slide的位置深度。值越大z轴距离越远，看起来越小。 默认100。
modifier：depth和rotate和stretch的倍率，相当于depth*modifier、rotate*modifier、stretch*modifier，值越大这三个参数的效果越明显。默认1。
slideShadows：开启slide阴影。默认 true。
#### 2.5 flipEffect
3d翻转有两个参数可设置。
slideShadows：slides的阴影。默认true。
limitRotation：限制最大旋转角度为180度，默认true。
### 3. Pagination（分页器）
#### 3.1 pagination
使用分页导航。
#### 3.2 el
分页器容器的css选择器或HTML标签。分页器等组件可以置于container之外，不同Swiper的组件应该有所区分，如#pagination1，#pagination2。
#### 3.3 type
分页器样式类型，可选
‘bullets’  圆点（默认）
‘fraction’  分式 
‘progressbar’  进度条
‘custom’ 自定义
#### 3.4 bulletElement
设定分页器指示器（小点）的HTML标签。
#### 3.5 progressbarOpposite
使进度条分页器与Swiper的direction参数相反，也就是说水平方向切换的swiper显示的是垂直进度条而垂直方向切换的swiper显示水平进度条
#### 3.6 dynamicMainBullets
动态分页器的主指示点的数量
#### 3.7 dynamicBullets
动态分页器，当你的slide很多时，开启后，分页器小点的数量会部分隐藏。
#### 3.8 hideOnClick
默认分页器会一直显示。这个选项设置为true时点击Swiper会隐藏/显示分页器。
#### 3.9 clickable
此参数设置为true时，点击分页器的指示点分页器会控制Swiper切换。
#### 3.10 renderBullet(index, className)
渲染分页器小点。这个参数允许完全自定义分页器的指示点。接受指示点索引和指示点类名作为参数。
#### 3.11 renderFraction()
自定义分式类型分页器，当分页器类型设置为分式时可用。
#### 3.12 renderProgressbar()
自定义进度条类型分页器，当分页器类型设置为进度条时可用。
#### 3.13 renderCustom()
自定义特殊类型分页器，当分页器类型设置为自定义时可用。
#### 3.14 formatFractionCurrent
格式化分式分页器的当前指示数值，接受当前数值作为参数，必须返回一个自定义的数值。
#### 3.15 formatFractionTotal
格式化分式分页器的总指示数值，接受总数值作为参数，必须返回一个自定义的数值。
#### 3.16 bulletClass
pagination分页器内元素的类名。
#### 3.17 bulletActiveClass
pagination分页器内活动(active)元素的类名。
#### 3.18 modifierClass
修改以swiper-pagination-为前缀的类名。
#### 3.19 currentClass
分式类型分页器的当前索引的类名
#### 3.20 totalClass
分式类型分页器总数的类名
#### 3.21 hiddenClass
分页器隐藏时的类名。
#### 3.22 progressbarFillClass
进度条型分页器的指示条的类名
#### 3.23 clickableClass
可点击的pagination的类名。
#### 3.24 mySwiper.pagination.el
获取分页器导航的容器元素。
#### 3.25 mySwiper.pagination.bullets
获取Swiper的分页器的小点bullets的[Dom7对象](https://www.swiper.com.cn/usage/dom7/)数组。通过类似mySwiper.pagination.bullets[1]获取其中某个。
#### 3.26 mySwiper.pagination.render()
渲染分页器。
#### 3.27 mySwiper.pagination.update()
更新分页器。
### 4. Navigation Buttons（前进后退按钮）
#### 4.1 navigation
使用前进后退按钮来控制Swiper切换。
有时你的按钮不想放在container之内，点击时可能会有蓝色的边框，加上样式**outline: none** 可以去除。
#### 4.2 nextEl
前进按钮的css选择器或HTML元素。
#### 4.3 prevEl
后退按钮的css选择器或HTML元素。
#### 4.4 hideOnClick
点击slide时显示/隐藏按钮。
BUG处理：如果遇到无效，可增加样式
`.swiper-container .swiper-button-hidden{ opacity : 0; }`
#### 4.5 disabledClass
前进后退按钮不可用时的类名。
#### 4.6 hiddenClass
按钮隐藏时的Class
#### 4.7 mySwiper.navigation.nextEl
获取前进按钮的HTML元素
#### 4.8 mySwiper.navigation.prevEl
获取后退按钮的HTML元素。通过$prevEl获取DOM7。
#### 4.9 mySwiper.navigation.update()
更新前进后退导航按钮。
### 5. Scollbar（滚动条）
#### 5.1 scrollbar
为Swiper增加滚动条。
#### 5.2 el
Scrollbar容器的css选择器或HTML元素。
#### 5.3 hide
滚动条是否自动隐藏。默认：false，不会自动隐藏。
#### 5.4 draggable
该参数设置为true时允许拖动滚动条。
#### 5.5 snapOnRelease
如果设置为false，释放滚动条时slide不会自动贴合。
#### 5.6 dragSize
设置滚动条指示的尺寸。默认'auto': 自动，或者设置num(px)。
#### 5.7 mySwiper.scrollbar.el
获取滚动条的HTML元素，还可通过$el获取DOM7。
#### 5.8 mySwiper.scrollbar.updateSize()
更新滚动条
#### 5.9 mySwiper.scrollbar.dragEl
获取滚动条指示条的HTML元素，还可通过$dragEl获取DOM7。
### 6. Scollbar（滚动条）
#### 6.1 keyboard
是否开启键盘控制Swiper切换。
设置为true时，能使用键盘的方向键控制slide切换。
#### 6.2 enabled
开启后可以使用键盘切换
#### 6.3 onlyInViewport
默认仅控制当前窗口内的swiper切换。当swiper离开可视区域则无法切换。
#### 6.4 mySwiper.keyboard.enabled
获取键盘状态
#### 6.5 mySwiper.keyboard.enable()
开启键盘控制。
#### 6.6 mySwiper.keyboard.disable()
禁止键盘控制。
#### 6.7 keyPress()
回调函数。在允许键盘控制状态下，按键盘时会触发这个函数。
### 7. Mousewheel（鼠标）
#### 7.1 mousewheel
开启鼠标滚轮控制Swiper切换。可设置鼠标选项，或true使用默认值。
#### 7.2 forceToAxis
当值为true让鼠标滚轮固定于轴向。当水平mode时的鼠标滚轮只有水平滚动才会起效，当垂直mode时的鼠标滚轮只有垂直滚动才会起效。
普通家用鼠标只有垂直方向的滚动。
#### 7.3 releaseOnEdges
如果开启这个参数，当Swiper处于边缘位置时（第一个或最后一个slide），Swiper释放鼠标滚轮事件，鼠标可以控制页面滚动。
#### 7.4 invert
这个参数会使鼠标滚轮控制方向反转。
#### 7.5 sensitivity
鼠标滚轮的灵敏度，值越大鼠标滚轮滚动时swiper位移越大。
#### 7.6 eventsTarged
鼠标滚轮事件的接收目标(handle)，可以是css选择器或者HTML元素
#### 7.7 mySwiper.mousewheel.enabled
获取鼠标控制状态，true/false。
#### 7.8 mySwiper.mousewheel.enable()
开启鼠标滑轮控制。
#### 7.9 mySwiper.mousewheel.disable()
禁止鼠标滑轮控制。
### 8. Lazy Loading（延迟加载）
#### 8.1 lazy
设为true开启图片延迟加载默认值，使preloadImages无效。或者设置延迟加载选项。
图片延迟加载：需要将图片img标签的src改写成data-src，并且增加类名swiper-lazy。
背景图延迟加载：载体增加属性data-background，并且增加类名swiper-lazy。
还可以加一个预加载，<**div** class="swiper-lazy-preloader"></**div**>
或者白色的<**div** class="swiper-lazy-preloader swiper-lazy-preloader-white"></**div**>
当你设置了slidesPerView:'auto' 或者 slidesPerView > 1，还需要开启watchSlidesVisibility。
#### 8.2 loadPrevNext
设置为true允许将延迟加载应用到最接近的slide的图片（前一个和后一个slide）。
#### 8.3 loadPrevNextAmount
设置在延迟加载图片时提前多少个slide。个数不可少于[slidesPerView](https://www.swiper.com.cn/api/Slides_grid/2014/1215/24.html)的数量。
默认为1，提前1个slide加载图片，例如切换到第三个slide时加载第四个slide里面的图片。
#### 8.4 loadOnTransitionStart
默认当过渡到slide后开始加载图片，如果你想在过渡一开始就加载，设置为true
#### 8.5 elementClass
延迟加载的图片的类名。
#### 8.6 loadingClass
正在进行懒加载的元素的类名。
#### 8.7 loadedClass
懒加载完成的元素的类名。
#### 8.8 preloaderClass
延时加载时预加载元素（preloader）的类名。
#### 8.9 mySwiper.lazy.load()
加载可视区域内（或前后）的图片。
swiper在初始化、切换、拖动滚动条时会自动使用这个方法来加载图片。但是有时候你可能需要手动运行这个方法，例如你自定义了一个奇异的切换方式。
#### 8.10 mySwiper.lazy.loadInSlide(index)
根据slide的索引加载图片。
#### 8.11 lazyImageLoad(slideEl, imageEl)
回调函数，图片延迟加载开始时执行。slide中每有一张图片被延迟加载就执行一次。接受延迟加载的slide，延迟加载的img作为参数（可选）。
#### 8.12 lazyImageReady(slideEl, imageEl)
回调函数，图片延迟加载结束时执行。slide中每有一张图片被延迟加载就执行一次。接受延迟加载的slide，延迟加载的img作为参数（可选）。
### 9. Zoom（调焦）
#### 9.1 zoom
开启焦距功能：双击slide会放大/缩小，并且在手机端可双指触摸缩放。可设置缩放选项或设为true使用默认值。
需要在slide中增加类名**swiper-zoom-container**，结构如下：
`<div class="swiper-slide"> <div class="swiper-zoom-container"> <img src="path/to/image"> </div> </div>`
#### 9.2 maxRatio
最大缩放焦距（放大倍率）。
如果要在单个slide上设置，可以使用data-swiper-zoom。
#### 9.3 minRatio
最小缩放焦距（缩小倍率）。
#### 9.4 toggle
是否允许双击缩放。
设置为false，不允许双击缩放，只允许手机端触摸缩放。
#### 9.5 containerClass
zoom container的类名。
#### 9.6 mySwiper.zoom.enabled
判断zoom是否开启。
#### 9.7 mySwiper.zoom.scale
获取当前缩放的图片的比例。
#### 9.8 mySwiper.zoom.enable()
开启zoom
#### 9.9 mySwiper.zoom.disable()
禁止zoom模式。
#### 9.10 mySwiper.zoom.toggle()
zoom模式下，当前的图片放大/缩小。
#### 9.11 mySwiper.zoom.in()
zoom模式下，当前的图片放大。
#### 9.12 mySwiper.zoom.out()
zoom模式下，当前的图片缩小。
#### 9.13 zoomChange
当zoom变化时，触发此回调函数，接受scale, imageEl 和slideEl作为参数。
scale：缩放的倍数
imageEl：缩放的图片的HTML
slideEl：缩放的slide的HTML
### 10. Controller（双向控制）
#### 10.1 controller
设置双向控制的参数，或者true使用默认设置
还需要设置control为swiper实例，控制该swiper，而不是被该swiper控制
#### 10.2 control
设置为另外一个Swiper实例开始控制该Swiper。
#### 10.3 inverse
设置为true时控制方向倒转。
#### 10.4 By
设定Swiper相互控制时的控制方式。当两个swiper的slide数量不一致时可用。
默认为'slide'，自身切换一个slide时，被控制方也切换一个slide。
可选：'container'，按自身slide在container中的位置比例进行控制。
例：有4个slide的swiper1控制有7个slide的swiper2，
设定'slide', swiper1的1, 2, 3, 4对应控制的swiper2为1, 2, 3, 7。
设定by: 'container'，swiper1的1, 2, 3, 4对应控制的swiper2为1, 3, 5, 7。
### 11. Thumbs（缩略图）
#### 11.1 thumbs
thumbs组件专门用于制作带缩略图的swiper，比使用controller组件更为简便。
#### 11.2 swiper
设置作为缩略图的swiper对象。有两种方式：
1.先初始化缩略图Swiper，再初始化banner Swiper
```
var thumbsSwiper = new Swiper('.swiper-container-thumbs', {
  slidesPerView: 5,
});
var mySwiper = new Swiper('.swiper-container', {
  ...
  thumbs: {
    swiper: thumbsSwiper
  }
});
```
2.初始化banner Swiper的时候初始化缩略图Swiper
```
var mySwiper = new Swiper('.swiper-container', {
  ...
  thumbs: {
    swiper: {
      el: '.swiper-container-thumbs',
      slidesPerView: 5,
      ...
    }
  }
});
```
#### 11.3 slideThumbActiveClass
设置缩略图Swiper的活动块的附加类名。
banner Swiper切换时，缩略图Swiper的原活动块类名swiper-slide-active不会切换，而缩略图Swiper的附加类名swiper-slide-thumb-active会切换。
#### 11.4 thumbsContainerClass
设置缩略图Swiper的container的附加类名
#### 11.5 mySwiper.thumbs.swiper
获取缩略图Swiper的实例
### 12. Virtual slides（虚拟slide）
#### 12.1 virtual
开启虚拟Slide功能，可设置选项或设置为true则使用默认值。
虚拟Slide会在Dom结构中保持尽量少的Slide，只渲染当前可见的slide和前后的slide，而隐藏其他不可见的Slide，每次切换时就渲染新的Slide。当你的Slide很多的时候，尤其是Slide中有复杂的Dom树结构时，性能会有很大的提升。
#### 12.2 slides
需要添加的虚拟slide的内容
#### 12.3 cache
开启虚拟Slide的DOM缓存（默认值）。虚拟的Slide被渲染后，会存入到缓存中，也可以从缓存中重新获得该Slide。
#### 12.4 renderSlide
此函数设置以何种形式渲染虚拟Slide，接受当前渲染Slide的内容和Index作为参数。必须返回一个slide的HTML结构。即必须包含
`<div class="swiper-slide"></div>`
#### 12.5 renderExternal
外部渲染函数（比如你使用了其他库，vue或react等），这个函数接受以下四个参数
-   `offset` - Slides左/上的偏移量
-   `from` - 第一个需要渲染的Slide的索引
-   `to` - 最后一个需要渲染的Slide的索引
-   `slides` - 被渲染的Slide数组
#### 12.6 addSlidesBefore
一般情况下，virtual swiper只会提前渲染可见slide前后一个（组）slide，如果你想提前渲染前面多个slide，可以设置这个选项。
#### 12.7 addSlidesAfter
一般情况下，virtual swiper只会提前渲染可见slide前后一个（组）slide，如果你想提前渲染后面多个slide，可以设置这个选项。
#### 12.8 mySwiper.virtual.cache
获取或设置缓存的（已经渲染的）Slide的HTML。
#### 12.9 mySwiper.virtual.from
获取正在渲染的第一个虚拟Slide的序号。
#### 12.10 mySwiper.virtual.to

获取正在渲染的最后一个虚拟Slide的序号。
#### 12.11 mySwiper.virtual.slides
获取全部的虚拟slide数组无论其是否被渲染了。
或设置虚拟slide。
#### 12.12 mySwiper.virtual.appendSlide(slide)
在全部虚拟Slide的后面插入Slide。
#### 12.13 mySwiper.virtual.prependSlide(slide)
在虚拟Slide的前面添加新的Slide。
#### 12.14 mySwiper.virtual.update()
更新虚拟Slide的状态。
### 13. Hash Navigation（锚导航）
#### 13.1 hashNavigation
设置散列导航选项，或true使用默认值。为每个slide增加散列导航（有点像锚链接）。
还需要在每个slide处增加data-hash属性。
这样当你的swiper切换时你的页面url就会加上这个属性的值了，你也可以通过进入页面时修改页面url让swiper在初始化时切换到指定的slide。
你可以直接跳转到指定的slide。比如这样：[直接跳到第三个slide。](https://www.swiper.com.cn/api/hash/211.html#slide3)
如果需要浏览器的前进后退按钮配合控制，需要加上[watchState](https://www.swiper.com.cn/api/hash/watchState.html)
#### 13.2 watchState
开启后观察浏览器窗口的的hashchange状态变化。可通过浏览器历史记录（页面前进后退按钮）或者URL的锚链接改变控制slide切换。
#### 13.3 replaceState
使用replaceState（window.history.replaceState）代替hashnav的hash（document.location.hash）。
### 14. History Navigation（历史导航）
#### 14.1 history
设为history导航选项，或者true使用默认值，开启history导航。
在slide切换时无刷新更换URL和浏览器的history.state(pushState)。这样每个slide都会拥有一个自己的URL。
使用history还必需在slide上增加一个属性**data-history**，例`<div class="swiper-slide" data-history="slide1"></div>`
开启history会取消hashnav。
#### 14.2 replaceState
使用history.replaceState方法替换history.pushState方法
#### 14.3 key
URL中的接续词