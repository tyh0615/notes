# ECMAScript 6

## 介绍

ECMAScript 6，也称为ECMAScript 2015，是ECMAScript标准的最新版本。

ES6包括以下新功能：

[TOC]



## ECMAScript 6功能

### arrows 箭头

箭头是使用`=>`语法的函数简写。它们在语法上类似于C＃，Java 8和CoffeeScript中的相关功能。它们支持语句块体以及返回表达式值的表达式体。与函数不同，箭头`this`与其周围代码共享相同的词汇。

```
// Expression bodies
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + i);
var pairs = evens.map(v => ({even: v, odd: v + 1}));

// Statement bodies
nums.forEach(v => {
  if (v % 5 === 0)
    fives.push(v);
});

// Lexical this
var bob = {
  _name: "Bob",
  _friends: [],
  printFriends() {
    this._friends.forEach(f =>
      console.log(this._name + " knows " + f));
  }
}
```


### classes 类

ES6类比基于原型的OO模式简单。拥有一个方便的声明形式使类模式更易于使用，并鼓励互操作性。类支持基于原型的继承，超级调用，实例和静态方法以及构造函数。

```
 class SkinnedMesh extends THREE.Mesh {
  constructor(geometry, materials) {
    super(geometry, materials);

    this.idMatrix = SkinnedMesh.defaultMatrix();
    this.bones = [];
    this.boneMatrices = [];
    //...
  }
  update(camera) {
    //...
    super.update();
  }
  get boneCount() {
    return this.bones.length;
  }
  set matrixType(matrixType) {
    this.idMatrix = SkinnedMesh[matrixType]();
  }
  static defaultMatrix() {
    return new THREE.Matrix4();
  }
}
```


### enhanced object literals 增强的对象文字

扩展了对象文字以支持在构造时设置原型，为`foo: foo`赋值设置简写，定义方法，进行超级调用以及使用表达式计算属性名称。它们一起使对象文字和类声明更加紧密，让基于对象的设计从一些相同的便利中受益。

```
var obj = {
    // __proto__
    __proto__: theProtoObj,
    // Shorthand for ‘handler: handler’
    handler,
    // Methods
    toString() {
     // Super calls
     return "d " + super.toString();
    },
    // Computed (dynamic) property names
    [ 'prop_' + (() => 42)() ]: 42
};
```

### template strings 模板字符串

模板字符串为构造字符串提供语法糖。这类似于Perl，Python等中的字符串插值功能。可选地，可以添加标签以允许定制字符串构造，避免注入攻击或从字符串内容构造更高级别的数据结构。

```
// Basic literal string creation
`In JavaScript '\n' is a line-feed.`

// Multiline strings
`In JavaScript this is
 not legal.`

// String interpolation
var name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`

// Construct an HTTP request prefix is used to interpret the replacements and construction
POST`http://foo.org/bar?a=${a}&b=${b}
     Content-Type: application/json
     X-Credentials: ${credentials}
     { "foo": ${foo},
       "bar": ${bar}}`(myOnReadyStateChangeHandler);
```


### destructuring 解构

解构允许使用模式匹配进行绑定，并支持匹配数组和对象。解构是失败 - 软，类似于标准对象查找`foo["bar"]`，`undefined`在未找到时生成值。

```
// list matching
var [a, , b] = [1,2,3];

// object matching
var { op: a, lhs: { op: b }, rhs: c }
       = getASTNode()

// object matching shorthand
// binds `op`, `lhs` and `rhs` in scope
var {op, lhs, rhs} = getASTNode()

// Can be used in parameter position
function g({name: x}) {
  console.log(x);
}
g({name: 5})

// Fail-soft destructuring
var [a] = [];
a === undefined;

// Fail-soft destructuring with defaults
var [a = 1] = [];
a === 1;
```


### default + rest + spread 默认+休息+点差

被调用者评估的默认参数值。在函数调用中将数组转换为连续的参数。将尾随参数绑定到数组。Rest `arguments`更直接地替换了对常见情况的需求和解决。

```
function f(x, y=12) {
  // y is 12 if not passed (or passed as undefined)
  return x + y;
}
f(3) == 15

function f(x, ...y) {
  // y is an Array
  return x * y.length;
}
f(3, "hello", true) == 6

function f(x, y, z) {
  return x + y + z;
}
// Pass each elem of array as argument
f(...[1,2,3]) == 6
```

更多MDN信息：[默认参数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)，[Rest参数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)，[Spread Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

### let + const 让+ Const

块范围的绑定构造。 `let`是新的`var`。 `const`是单一任务。静态限制在分配之前阻止使用。

```
function f() {
  {
    let x;
    {
      // okay, block scoped name
      const x = "sneaky";
      // error, const
      x = "foo";
    }
    // error, already declared in block
    let x = "inner";
  }
}
```

更多MDN信息：[let语句](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)，[const语句](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

### iterators + for..of 迭代器+ For..Of

Iterator对象支持自定义迭代，如CLR IEnumerable或Java Iterable。使用通用`for..in`到基于自定义迭代器的迭代`for..of`。不需要实现数组，启用LINQ等惰性设计模式。

```
let fibonacci = {
  [Symbol.iterator]() {
    let pre = 0, cur = 1;
    return {
      next() {
        [pre, cur] = [cur, pre + cur];
        return { done: false, value: cur }
      }
    }
  }
}

for (var n of fibonacci) {
  // truncate the sequence at 1000
  if (n > 1000)
    break;
  console.log(n);
}
```

迭代基于这些duck-typed接口（仅使用[TypeScript](http://typescriptlang.org/)类型语法进行展示）：

```
interface IteratorResult {
  done: boolean;
  value: any;
}
interface Iterator {
  next(): IteratorResult;
}
interface Iterable {
  [Symbol.iterator](): Iterator
}
```


### generators 发电机

生成器使用`function*`和简化迭代器创作`yield`。声明为function *的函数返回Generator实例。生成器是迭代器的子类型，包括额外的 `next`和`throw`。这些使得值能够流回到生成器中，因此`yield`返回值（或抛出）的表达式形式也是如此。

注意：也可用于启用'await'式异步编程，另请参阅ES7 `await`提议。

```
var fibonacci = {
  [Symbol.iterator]: function*() {
    var pre = 0, cur = 1;
    for (;;) {
      var temp = pre;
      pre = cur;
      cur += temp;
      yield cur;
    }
  }
}

for (var n of fibonacci) {
  // truncate the sequence at 1000
  if (n > 1000)
    break;
  console.log(n);
}
```

生成器接口是（仅使用[TypeScript](http://typescriptlang.org/)类型语法进行展示）：

```
interface Generator extends Iterator {
    next(value?: any): IteratorResult;
    throw(exception: any);
}
```


### unicode 统一

支持完整Unicode的非破坏性添加，包括字符串中的新Unicode文字形式和`u`处理代码点的新RegExp 模式，以及用于处理21位代码点级别的字符串的新API。这些新增功能支持在JavaScript中构建全局应用程序。

```
// same as ES5.1
"𠮷".length == 2

// new RegExp behaviour, opt-in ‘u’
"𠮷".match(/./u)[0].length == 2

// new form
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"

// new String ops
"𠮷".codePointAt(0) == 0x20BB7

// for-of iterates code points
for(var c of "𠮷") {
  console.log(c);
}
```


### modules 模块

用于组件定义的模块的语言级支持。从流行的JavaScript模块加载器（AMD，CommonJS）中复制模式。由主机定义的默认加载程序定义的运行时行为。隐式异步模型 - 在请求的模块可用和处理之前，代码不会执行。

```
// lib/math.js
export function sum(x, y) {
  return x + y;
}
export var pi = 3.141593;

// app.js
import * as math from "lib/math";
alert("2π = " + math.sum(math.pi, math.pi));

// otherApp.js
import {sum, pi} from "lib/math";
alert("2π = " + sum(pi, pi));  
```

一些其他功能包括`export default`和`export *`：

```
// lib/mathplusplus.js
export * from "lib/math";
export var e = 2.71828182846;
export default function(x) {
    return Math.log(x);
}

// app.js
import ln, {pi, e} from "lib/mathplusplus";
alert("2π = " + ln(e)*pi*2);
```

更多MDN信息：[import语句](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)，[导出语句](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

### module loaders 模块装载机

模块加载器支持：

-   动态加载
-   国家隔离
-   全局命名空间隔离
-   编译钩子
-   嵌套虚拟化

可以配置默认模块加载器，并且可以构造新的加载器以在隔离或受约束的上下文中评估和加载代码。

```
// Dynamic loading – ‘System’ is default loader
System.import('lib/math').then(function(m) {
  alert("2π = " + m.sum(m.pi, m.pi));
});

// Create execution sandboxes – new Loaders
var loader = new Loader({
  global: fixup(window) // replace ‘console.log’
});
loader.eval("console.log('hello world!');");

// Directly manipulate module cache
System.get('jquery');
System.set('jquery', Module({$: $})); // WARNING: not yet finalized
```

### map + set + weakmap + weakset Map + Set + WeakMap + WeakSet

常用算法的高效数据结构。WeakMaps提供无泄漏的对象密钥边表。

```
// Sets
var s = new Set();
s.add("hello").add("goodbye").add("hello");
s.size === 2;
s.has("hello") === true;

// Maps
var m = new Map();
m.set("hello", 42);
m.set(s, 34);
m.get(s) == 34;

// Weak Maps
var wm = new WeakMap();
wm.set(s, { extra: 42 });
wm.size === undefined

// Weak Sets
var ws = new WeakSet();
ws.add({ data: 42 });
// Because the added object has no other references, it will not be held in the set
```

更多MDN信息：[Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)，[Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)，[WeakMap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)，[WeakSet](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)

### proxies 代理

代理可以创建具有主机对象可用的全部行为的对象。可用于拦截，对象虚拟化，日志记录/分析等。

```
// Proxying a normal object
var target = {};
var handler = {
  get: function (receiver, name) {
    return `Hello, ${name}!`;
  }
};

var p = new Proxy(target, handler);
p.world === 'Hello, world!';
// Proxying a function object
var target = function () { return 'I am the target'; };
var handler = {
  apply: function (receiver, ...args) {
    return 'I am the proxy';
  }
};

var p = new Proxy(target, handler);
p() === 'I am the proxy';
```

所有运行时级元操作都有可用的陷阱：

```
var handler =
{
  get:...,
  set:...,
  has:...,
  deleteProperty:...,
  apply:...,
  construct:...,
  getOwnPropertyDescriptor:...,
  defineProperty:...,
  getPrototypeOf:...,
  setPrototypeOf:...,
  enumerate:...,
  ownKeys:...,
  preventExtensions:...,
  isExtensible:...
}
```


### symbols 符号

符号启用对象状态的访问控制。符号允许属性被键入`string`（如在ES5中）或`symbol`。符号是一种新的原始类型。`description`调试中使用的可选参数 - 但不是标识的一部分。符号是独一无二的（如gensym），但不是私有的，因为它们通过反射功能暴露出来`Object.getOwnPropertySymbols`。

```
var MyClass = (function() {

  // module scoped symbol
  var key = Symbol("key");

  function MyClass(privateData) {
    this[key] = privateData;
  }

  MyClass.prototype = {
    doStuff: function() {
      ... this[key] ...
    }
  };

  return MyClass;
})();

var c = new MyClass("hello")
c["key"] === undefined
```


### subclassable built-ins 子类可内置

在ES6，内置插件一样`Array`，`Date`和DOM `Element`S可被继承。

名为`Ctor`now 的函数的对象构造使用两个阶段（都是虚拟调度的）：

-   调用`Ctor[@@create]`分配对象，安装任何特殊行为
-   在新实例上调用构造函数以进行初始化

已知`@@create`符号可通过`Symbol.create`。内置插件现在`@@create`明确暴露它们。

```
// Pseudo-code of Array
class Array {
    constructor(...args) { /* ... */ }
    static [Symbol.create]() {
        // Install special [[DefineOwnProperty]]
        // to magically update 'length'
    }
}

// User code of Array subclass
class MyArray extends Array {
    constructor(...args) { super(...args); }
}

// Two-phase 'new':
// 1) Call @@create to allocate object
// 2) Invoke constructor on new instance
var arr = new MyArray();
arr[1] = 12;
arr.length == 2
```

### promises 数学+数字+字符串+数组+对象API

许多新的库添加，包括核心数学库，数组转换助手，字符串助手和用于复制的Object.assign。

```
Number.EPSILON
Number.isInteger(Infinity) // false
Number.isNaN("NaN") // false

Math.acosh(3) // 1.762747174039086
Math.hypot(3, 4) // 5
Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2) // 2

"abcde".includes("cd") // true
"abc".repeat(3) // "abcabcabc"

Array.from(document.querySelectorAll('*')) // Returns a real Array
Array.of(1, 2, 3) // Similar to new Array(...), but without special one-arg behavior
[0, 0, 0].fill(7, 1) // [0,7,7]
[1, 2, 3].find(x => x == 3) // 3
[1, 2, 3].findIndex(x => x == 2) // 1
[1, 2, 3, 4, 5].copyWithin(3, 0) // [1, 2, 3, 1, 2]
["a", "b", "c"].entries() // iterator [0, "a"], [1,"b"], [2,"c"]
["a", "b", "c"].keys() // iterator 0, 1, 2
["a", "b", "c"].values() // iterator "a", "b", "c"

Object.assign(Point, { origin: new Point(0,0) })
```

更多MDN信息：[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)，[Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)，[Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)，[Array.of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)，[Array.prototype.copyWithin](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)，[Object.assign](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

### math + number + string + array + object APIs 二进制和八进制文字

为binary（`b`）和octal（`o`）添加了两个新的数字文字形式。

```
0b111110111 === 503 // true
0o767 === 503 // true
```

### binary and octal literals 承诺

Promises是异步编程的库。Promise是可以在将来提供的值的第一类表示。Promise在许多现有的JavaScript库中使用。

```
function timeout(duration = 0) {
    return new Promise((resolve, reject) => {
        setTimeout(resolve, duration);
    })
}

var p = timeout(1000).then(() => {
    return timeout(2000);
}).then(() => {
    throw new Error("hmm");
}).catch(err => {
    return Promise.all([timeout(100), timeout(200)]);
})
```


### reflect api 反映API

全反射API公开对象的运行时级元操作。这实际上是Proxy API的反转，并允许进行与代理陷阱相同的元操作的调用。特别适用于实现代理。

```
//还没有样品
```


### tail calls 尾巴召唤

保证尾部位置的调用不会无限制地增加堆栈。在无界输入的情况下使递归算法安全。

```
function factorial(n, acc = 1) {
    'use strict';
    if (n <= 1) return acc;
    return factorial(n - 1, n * acc);
}

// Stack overflow in most implementations today,
// but safe on arbitrary inputs in ES6
factorial(100000)
```