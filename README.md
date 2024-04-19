#### 说一说 HTML 语义化

```
使用语义化标签的意义：

对于开发者：语义化标签有着更好的页面结构，有利于个人代码的编写。
对于团队：有利于代码的开发及后期的维护。
对于用户：当页面卡顿时有着良好的页面结构，有利于增加用户体验。
对于爬虫：有利于搜索引擎的SEO优化，有利于网站更靠前的排名。

语义化标签都有哪些：

header、nav、article（独立的、完整的文章或内容块）、aside、main、footer、h1~h6、ul、ol、li等标签。
```

####  说一说 CSS 的盒子模型

```
在 HTML 页面中所有的元素都可以看成是一个盒子。
盒子的组成：内容 content、内边距 padding、边框 border、外边距 margin。

盒模型的类型：
- 标准盒模型：width = content
- IE 盒模型（怪异盒模型）：width = content + padding + border

控制盒模型的模式：box-sizing: content-box(默认值，标准盒模型)、border-box(IE 盒模型)。
```

#### 说一说样式优先级的规则是什么？

```
css 样式优先级应该分为五大类：

第一类：!important，它的优先级始终是最高的。

第二类：引入方式，行内样式的优先级高于嵌入和外链，嵌入和外链如果使用的选择器相同就看它们在页面中插入的顺序，在		 后面的会覆盖前面的。（行内样式、嵌入样式、外链样式）

第三类：选择器,优先级：id 选择器 > (类选择器 | 伪类选择器 | 属性选择器) > (后代选择器 | 伪元素选择器) > 		(子选择器 | 相邻选择器) > 通配符选择器。

第四类：继承样式，是所有样式中优先级比较低的。

第五类：浏览器默认样式优先级最低。

能尽量不适用 !important 就不用，特别是在自己封装的组件中。
```

#### 说一说 CSS 尺寸设置的单位

````
px：绝对长度单位，它的大小取决于屏幕分辨率，是网页开发中常用的单位。

em：相对长度单位，在 font-size 中使用是相对于父元素的字体大小，其他属性中使用是相对于自身的字体大小，如 width。如果当前元素的字体大小为设置，由于字体可继承的原因，则会逐级向上查找，最终找不到则相对于浏览器默认字体大小。

rem：相对长度单位，相对于根元素的字体大小，如果根元素大小未设置，使用浏览器默认字体大小。

vw：相对长度单位，相对与视口宽度的1%。
vh：相对长度单位，相对于视口高度的1%。
````

#### 说一说浮动

```
浮动最早是用来实现文字环绕图片的效果的，后来发现浮动属性在布局上使用有着优势，所以现有很多页面采用浮动来解决布局问题。

开启浮动的属性 float: left / right。
设置了浮动的元素会脱离普通流，而普通流内的元素在计算自身高度时不会去计算浮动元素的高度，这时就有可能会发现父元素高度塌陷的问题，进而影响到父元素后续兄弟元素的排版问题。

解决高度塌陷问题：
1. 清除浮动
主要是为了清除浮动后造成的影响，而不是清除浮动。
 - 添加额外标签设置clear：both;属性。 <br style="clear: both" />
 - 伪元素设置clear属性。
2. 父元素设置bfc。
bfc 元素的高度计算会将浮动元素的高度也计算在内。所以也可以解决高度塌陷的问题。
bfc 是一个完全独立的容器，内部元素不会影响到外面。
 - overflow 不为 visible， 内容溢出容易造成被裁剪的问题。
 - flex 
 - grid 
 - table 容易集成表格的各种难处理的样式问题。不推荐
 - html 本身就是一个bfc容器，但这不现实
 - 父元素设置高度。写死高度不推荐。
```

#### 说一说 BFC 

```
BFC 即 Block Formatting Contexts（块级格式化上下文）。

具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素在布局上不会影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。

可以认为 BFC 是一个封闭的盒子，内部元素的变化，不会影响到外面。

触发 BFC 的条件：
- 根元素（HTML 元素，自身就是一个 BFC）
- 浮动元素：float 属性值设置了 right / left
- 绝对定位元素：设置了 position 属性值：absolute / fixed，绝对定位或者固定定位。
- overflow 属性：overflow 属性值不为：visible 时，即指定了 auto、scroll、hidden 等的元素
- display 属性：display 属性值为 inline-block、table-cell、flex、grid 等的元素。

特点：
- 同一个 BFC 下兄弟元素间外边距会发生重叠
	将其放入到不同的 BFC 容器中。
- 清除浮动，解决高度塌陷
	浮动的元素会脱离文档流，如果他的父元素没有设置高度，就会导致父元素出现高度塌陷的问题。
	原因是浮动元素不会参与普通流父元素的高度计算。
	而 BFC 容器的高度会计算浮动元素的高度。
```

#### 说几个未知宽高水平垂直居中的方法

```
1. absolute + translate
2. absolute + margin
3. flex
4. grid 
5. table-cell
```

#### 说一下三栏布局的实现方案

```
- float + margin-left + margin-right
- float + margin + position
- flex布局 + order 
结构：
  <div class="header"></div>
  <div class="content clearfix">
    <div class="center"></div>
    <div class="left"></div>
    <div class="right"></div>
  </div>
  <div class="footer"></div>
```

#### 说一说 JS 数据类型有哪些，区别是什么？

```
js 主要有两种数据类型：基本数据类型 和 复杂数据类型。
基本数据类型存储在栈中，存储的是基本数据的原始值，所以也叫做原始数据类型。
复杂数据类型存储在堆中，存储的是复杂数据类型的地址引用，所有也叫做引用数据类型。

基本数据类型：
在 ES6 之前，基本数据类型有五种：string、number、boolean、undefined、null。以及 ES6 新增的 Symbol，ES10 新增的 BigInt。
Symbol 它表示创建一个独一无二的值，我认为它的出现主要是为了解决可能存在的变量命名重复问题。
BigInt 是一种数字类型的数据，它可以表示任意精度格式的整数，使用 BigInt 可以安全的存储和操作大整数，常用在超出 Number 能够表示的安全整数的情况。
Symbol 和 BigInt 都不是构造函数，所以不能被 new。

引用数据类型：
主要是指 Object 类型，Array、Math、Date 等都属于 Object 的子类。

栈和堆的区别：
栈是一种先入后出的数据结构，而堆没有什么规律，它只用一块足够大的空间来存储变量。
栈区内存由编译器自动释放，程序员不需要关心，存放函数的参数值，局部变量的值等。
堆区内存一般由程序员手动释放，如果程序员不释放，程序结束时可能由垃圾回收机制回收。
```

#### 说一说 null 和 undefined 的区别，如何让一个属性变成 null

```
undefined 是未定义的意思，表示变量声明了但是还没赋值，null 常用于为变量赋值为对象的初始值，也就是表示这个变量后续要作为一个对象来使用。直接将变量设置为 null 也常用于释放对象所占据的内存。

null 属于 Null 类型，undefined 属于 Undefined 类型。
typeof undefined === 'undefined'; typeof null === 'object';
null 的 typeof 值为 “object”，这是一个历史遗留问题。

undefined 是 全局对象的一个属性，window.undefined === 'undefined'。当一个变量没有被赋值或者一个函数没有返回值或者访问某个对象内没有的属性或者函数定义了形参但是没有传递实参，这时候都是 undefined。

undefined 不是一个关键字。这意味着我们可以将其当做变量来使用，如：let undefined = 10; 这会影响我们对undefined 值的判断，实际开发中应避免这样使用。

null 是一个关键字。

直接将属性赋值为 null 就可以实现让一个属性变成 null。
```

#### 说几种 JS 判断数据类型的方法

```
1. typeof 只能判断基本数据类型，typeof null === 'object', 其他基本数据类型都正常。对于引用数据类型，都是 'object'。
2. instanceof 只能判断引用数据类型，左边实例对象，右边构造函数，基本原理是判断实例对象的 __proto__ 属性是否指向构造函数的 prototype，如果不相等，则查询实例对象的 __proto__.__proto__ 依次在原型链上查找，直到找到构造函数的 prototype，如果查找失败，则会返回 false。
3. Object.prototype.toString.call() 推荐使用的方式，返回格式如下：“[object Undefined]“。
```

#### 说几种数据去重的方法

```
1. [...new Set(arr)]
2. Array.from(new set(arr))
3. filter + indexOf
4. for + indexof 或 for + includes
```

#### 说一说伪数组和数组的区别？

```
伪数组：我们可以理解为类似数组的一个集合，他们与数组一样，具有索引(下标)和 length 属性。可以通过 for in 循环。

常见的伪数组：
1. document.getElementsByClassName('right')
2. arguments

伪数组的类型是 Object，数组的类型是 Array

判断是否是数组：Array.isArray()

伪数组转化为数组：
1. [].slice.call 或者 Array.prototype.slice.call
2. Array.from 
3. [...arguments]
索引不连续时转化结果是连续的，会自动补位。
```

#### 说一说 map 和 forEach 的区别？

```
map 和 forEach 都是es6新增的高阶函数，都是数组的方法，都有三个参数，用于数组遍历。
map 和 forEach 默认都不会改变原数组（不是绝对的，可以直接修改）。
map 会在内存中开辟一块新的空间，用来返回一个新的数组。forEach 返回值为 undefined。

性能方面：for > forEach > map，因为 map 的返回值是一个等长的全新的数组，数组创建和赋值产生的性能开销很大。
```

#### 说一说 ES6 中的箭头函数

```
1. 箭头函数没有 this，它内部的 this 指向的是上级作用域中的 this。
2. 它的写法简单。return 可以省略。
3. 不能作为构造函数，所以不能被 new。
4. 每一个函数都有 prototype 属性，但是箭头函数没有。
```

#### 扩展运算符使用场景

```
1. 伪数组转数组 [...arguments]
2. 合并剩余属性 const { name, age. ...rest } = record
3. 整合形参 function(...args) {}
4. 展开对象 const { name, age, ...record }
5. set 转数组 [...new Set(arr)]
```

#### 说一说你对闭包的理解

```
形成条件：函数嵌套，内部函数引用外部函数的（变量或函数）。
解决的问题：内部的（变量或函数）会一直存在于内存中，直到内部函数成为垃圾对象才会被销毁，用于保存变量。
存在的问题：容易造成内初泄露。
闭包的应用：
-定义 js 模块：
`- 具有特定功能的js模块`
`- 将所有的数据和方法都封装到一个函数的内部（私有的）`
`- 只向外部暴露一个包含n个方法的对象或函数`
`- 模块的使用者，只需要通过模块导出的对象调用方法来实现对应的功能。`
- 防抖和节流
```

#### 说一说变量提升

```
变量提升指的是 JS 的变量和函数声明会在代码编译期间，提升到代码的最前面。
是有使用 var 声明的变量才会存在变量提升，只有声明提升，赋值不会提升，在 JS 中函数是一等公民，所以函数提升要优先于变量提升。
变量提升可以在变量初始化之前访问该变量，返回的是 undefined。在函数声明前可以提前调用该函数。

使用 let 和 const 声明的变量不会提升，形成暂时性死区，在初始化之前访问 变量会报错。

ES6规定，let/const 命令会使区块形成封闭的作用域。若在声明之前使用变量，就会报错。
总之，在代码块内，使用 let 命令声明变量之前，该变量都是不可用的。
这在语法上，称为 “暂时性死区”（ temporal dead zone，简称 TDZ）。
```

#### 说一说 this 指向？（普通函数、箭头函数）

```
普通函数的 this 永远指向调用它的对象。
箭头函数：没有 this，它内部的 this 值指向上层作用域中的 this。

- fn()：window 严格模式下 undefined。
- obj.fn(): 普通函数是 obj, 箭头函数是 window 或 undefined （看是否是严格模式）。
- var p = new Fu(): 普通函数是 p, 箭头函数不能被 new，直接报错。
- fn.call(obj)：普通函数是 obj, 箭头函数是 window 或 undefined （看是否是严格模式）。
```

#### 说一说 call apply bind 的作用和区别？

```
三者的作用都是改变函数执行时的 this 指向。
call 立即执行，参数（实际调用函数的实例对象，函数的参数...）
apply 立即执行，参数（实际调用函数的实例对象，函数的参数集合）
bind 返回一个新的函数，参数（实际调用函数的实例对象，函数的参数...）

bind 在 vue 与 react 框架中使用的较多，常用来改变函数运行时的 this 指向。

call 与 apply 在编写一些工具函数，如 防抖、节流中使用较多。
```

#### 说一说 js 继承的方法和优缺点？

#### 说一说 new 会发生什么？

```
// 1. 创建一个空对象
const obj = {}
// 2. 设置原型链
obj.__proto__ = constrcutor.prototype
// 3. 将构造函数作为对象的一个属性并执行获取结果
const key = Symbol()
obj[key] = constrcutor
const result = obj[key](...args)
// 4. 删除 obj 上的 函数
delete obj[key]
// 将结果返回
return typeof result === 'object' ? result : obj
```

#### 说一说 defer 和 async 的 区别？

```
当浏览器碰到 script 脚本时：
- 不加 defer 或 async，浏览器会立即加载并执行脚本，不会等待后续文档的加载。
- async 加载和渲染后续文档的过程将和脚本的加载与执行并行进行（异步）。谁快谁慢不确定。
- defer 加载后续文档的过程和脚本的加载并行进行（异步），但是脚本的执行要在所有的元素解析完成之后。

defer 与 async的区别是：
前者要等到整个页面正常渲染结束，才会执行；后者一旦下载完，渲染引擎就会中断渲染，执行这个脚本以后，再继续渲染。一句话，defer 是“渲染完再执行”，async 是“下载完就执行”。另外，如果有多个 defer 脚本，会按照它们在页面出现的顺序加载，而多个async脚本是不能保证加载顺序的。
```

#### 说一说promise是什么与使用方法？

```
Promise 是一种异步编程的一种解决方案。支持 .then() 的链式调用，主要解决了异步编程所引起的回调地狱的问题。

Promise 是一个构造函数，接收一个函数作为参数，返回一个 Promise 实例。一个 Promise 实例有三种状态，分别是 pending、resolved 和 rejected，分别代表了进行中、已成功和已失败。实例的状态只能由 pending 转变 resolved 或者 rejected 状态，并且状态一经改变，无法再被改变了。状态的改变是通过 resolve() 和 reject() 函数来实现的，我们可以在异步操作结束后调用这两个函数改变 Promise 实例的状态，它的原型上定义了一个 then 方法，使用这个 then 方法可以为两个状态的改变注册回调函数。这个回调函数属于微任务，会在本轮事件循环的末尾执行。
```

#### 说一说 js 实现异步的方法?

```
回调函数、事件监听、setTimeout、Promise、生成器Generator、async/await。
```

#### 说一说cookie sessionStorage localStorage 区别？
```
一、存储的时间有效期不同
1、cookie 的有效期是可以设置的，默认的情况下是关闭浏览器后失效。
2、sessionStorage 的有效期是仅保持在当前页面，关闭当前会话页或者浏览器后就会失效。如果用户在浏览器中打开新的标签页或窗口，那么新的页面将无法访问 sessionStorage 中的数据。
3、localStorage 的有效期是在不进行手动删除的情况下是一直有效的。localStorage 中的数据可以在同一浏览器的所有标签页和窗口中共享。

二、存储的大小不同
1、cookie 的存储是4kb左右，存储量较小，一般页面最多存储20条左右信息。
2、localStorage 和 sessionStorage 的存储容量是5Mb(官方介绍，可能和浏览器有部分差异性)。

三、与服务端的通信
1、cookie 会参与到与服务端的通信中，一般会携带在 http 请求的头部中。
2、localStorage 和 sessionStorage 是单纯的前端存储，不参与与服务端的通信。

四、读写操作的便捷程度 
cookie 由于出现的比较早，读写设计的并不很合理。不如后两者方便。
1、cookie 创建
// 您还可以为 cookie 添加一个过期时间（以 UTC 或 GMT 时间）。默认情况下，cookie 在浏览器关闭时删除：
// 您可以使用 path 参数告诉浏览器 cookie 的路径。默认情况下，cookie 属于当前页面。
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT; path=/";
2、cookie的读取
var x = document.cookie;
3、cookie的删除
// 删除 cookie 非常简单。您只需要设置 expires 参数为以前的时间即可，如下所示，设置为 Thu, 01 Jan 1970 00:00:00 GMT:
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 GMT";
```

#### 说一说如何实现一个可过期的 localStorage 数据。
```
惰性删除：
特点：键值对过期后不会立马删除，下次使用时检查到过期才得到删除。
缺点：如果一个key一直没有被用到，即使它已经过期了也永远存放在 localStorage。

定时删除：
特点：每隔一段时间执行一次删除操作。
缺点：循环定时器会一直占据内存。

实现过程：
每隔一秒执行一次定时删除，操作如下：
1、随机测试20个设置了过期时间的key。使用正则匹配。
2、删除所有发现的已过期的key。
3、若删除的key超过5个则重复步骤1，直至重复500次。
```

#### 说一下 token 能放在 cookie 中吗？

```
可以，cookie不设置过期时间就行，但是不推荐，因为无法防范 CSRF 攻击，并且 token 本身就有用于防范 CSRF 攻击的目的。

token 一般是用来判断用户是否登录的，它内部包含的信息有：uid(用户唯一的身份标识)、time(当前时间的时间戳)、sign（签名，token 的前几位以哈希算法压缩成的一定长度的十六进制字符串） token可以存放在Cookie中，token 是否过期，应该由后端来判断，不该前端来判断，所以token 存储在 cookie 中只要不设置 cookie 的过期时间就 ok 了，如果 token 失效，就让后端在接口中返回固定的状态表示token 失效，需要重新登录，再重新登录的时候，重新设置 cookie 中的 token 就行。

token认证流程:
1. 客户端使用用户名跟密码请求登录 
2. 服务端收到请求，去验证用户名与密码 
3. 验证成功后，服务端签发一个 token ，并把它发送给客户端 
4. 客户端接收 token 以后会把它存储起来，比如放在 cookie 里或者 localStorage 里 
5. 客户端每次发送请求时都需要带着服务端签发的 token（把 token 放到 HTTP 的 Header 里） 
6. 服务端收到请求后，需要验证请求里带有的 token ，如验证成功则返回对应的数据
```







#### CSS 选择器有哪些？---------------

```
（1）id选择器（#app）
（2）类选择器（.box）
（3）标签选择器（div,h1,p）
（4）属性选择器（a[rel="external"]）
（5）伪类选择器（a:hover,li:nth-child）
（6）后代选择器（h1 p）
（7）相邻后代选择器（子）选择器（ul>li）
（8）兄弟选择器（li~a）
（9）相邻兄弟选择器（li+a）
（10）伪元素选择器（::before、::after）
（11）通配符选择器（*）
```

#### CSS 中哪些属性可以继承?

```
CSS 每一个属性在定义中都给出了这个属性是否具有继承性，一个具有继承性的属性会在没有指定值的时候，会使用父元素的同属性的值来作为自己的值。

一般具有继承性的属性有，字体相关的属性，font-size和font-weight等。文本相关的属性，color和text-align等。
表格的一些布局属性、列表属性如list-style等。还有光标属性cursor、元素可见性visibility。

当一个属性不是继承属性的时候，我们也可以通过将它的值设置为 inherit 来使它从父元素那获取同名的属性值来继承。
```

#### 实现元素水平垂直居中

```
1. flex
2. absolute + margin
3. absolute + top + left + transform
4. gird
5. table
```

#### display 有哪些值？说明他们的作用。

```
block	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
none	元素不显示，并从文档流中移除。
inline	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
inline-block 默认宽度为内容宽度，可以设置宽高，同行显示。
list-item	像块类型元素一样显示，并添加样式列表标记。
table	此元素会作为块级表格来显示。
inherit	规定应该从父元素继承display属性的值。
```

#### relative 和 absolute 定位原点是？

```
relative：自身位置
absolute：离自己最近设置了（绝对定位、相对定位、固定定位）的父元素。广义的父元素，一层层向上找祖先元素。
```

#### CSS3 有哪些新特性？（根据项目回答）

```
新增各种CSS选择器	（:not(.input)：所有class不是“input”的节点）
圆角		（border-radius:8px）
多列布局	（multi-column layout）
阴影和反射	（Shadow\Reflect）
文字特效		（text-shadow）
文字渲染		（Text-decoration）
线性渐变		（gradient）
旋转			（transform）
缩放，定位，倾斜，动画，多背景
例如：transform:\scale(0.85,0.90)\translate(0px,-30px)\skew(-9deg,0deg)\Animation:
```

#### 请解释一下 CSS3 的 Flex box（弹性盒布局模型），以及适用场景？

相关知识点：

```
Flex是FlexibleBox的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。

任何一个容器都可以指定为Flex布局。行内元素也可以使用Flex布局。注意，设为Flex布局以后，子元素的float、cl
ear和vertical-align属性将失效。

采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为Flex
项目（flex item），简称"项目"。

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis），项目默认沿主轴排列。


以下6个属性设置在容器上。

flex-direction属性决定主轴的方向（即项目的排列方向）。row（默认值）、 column

flex-wrap属性定义，如果一条轴线排不下，如何换行。

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

justify-content属性定义了项目在主轴上的对齐方式。

align-items属性定义项目在交叉轴上如何对齐。

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。


以下6个属性设置在项目上。

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

flex属性是flex-grow，flex-shrink和flex-basis的简写，默认值为0 1 auto。

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父
元素的align-items属性，如果没有父元素，则等同于stretch。
```

回答：

```
flex布局是CSS3新增的一种布局方式，我们可以通过将一个元素的display属性值设置为flex从而使它成为一个flex
容器，它的所有子元素都会成为它的项目。

一个容器默认有两条轴，一个是水平的主轴，一个是与主轴垂直的交叉轴。我们可以使用flex-direction来指定主轴的方向。
我们可以使用justify-content来指定元素在主轴上的排列方式，使用align-items来指定元素在交叉轴上的排列方式。还可以使用flex-wrap来规定当一行排列不下时的换行方式。

对于容器中的项目，我们可以使用order属性来指定项目的排列顺序，还可以使用flex-grow来指定当排列空间有剩余的时候，项目的放大比例。还可以使用flex-shrink来指定当排列空间不足时，项目的缩小比例。
```

#### 实现一个三角形

border 实现

```css
.box {
  width: 0;
  height: 0;
  border-top: 50px solid skyblue;
  border-right: 50px solid transparent;
  border-left: 50px solid transparent;
}
```

clip-path 实现

```css
.box {
  width: 160px;
  height: 200px;
  background-color: aquamarine;
  clip-path: polygon(0 0, 0% 100%, 100% 50%);
}

/* polygon 多边形 */

clip-path 就是使用它来绘制多边形（或圆形、椭圆形等）并将其定位在元素内。实际上，浏览器不会绘制 clip-path 之外的任何区域，因此我们看到的是 clip-path 的边界。
使用 clip-path 可以为沿路径放置的每个点定义坐标。在这种情况下，就定义了`三个点`：`top-left (0 0)、bottom-left (0% 100%)、right-center (100% 50%)`。

超出这三个点所绘制的区域的内容都会被裁剪掉。
```

#### IFC 是什么？

```
IFC指的是行级格式化上下文，它有这样的一些布局规则：

（1）行级上下文内部的盒子会在水平方向，一个接一个地放置。
（2）当一行不够的时候会自动切换到下一行。
（3）行级上下文的高度由内部最高的内联盒子的高度决定。
```

#### 请解释一下为什么需要清除浮动？清除浮动的方式

```
浮动元素可以左右移动，直到遇到另一个浮动元素或者遇到它外边缘的包含框。浮动框不属于文档流中的普通流，当元素浮动之后，不会影响块级元素的布局，只会影响内联元素布局。此时文档流中的普通流就会表现得该浮动框不存在一样的布局模式。当包含框的高度小于浮动框的时候，此时就会出现“高度塌陷”。

清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示。

清除浮动的方式

（1）使用clear属性清除浮动。

（2）使用BFC块级格式化上下文来清除浮动。

因为BFC元素不会影响外部元素的特点，所以BFC元素也可以用来清除浮动的影响，因为如果不清除，子元素浮动则父元
素高度塌陷，必然会影响后面元素布局和定位，这显然有违BFC元素的子元素不会影响外部元素的设定。
```

#### 使用 clear 属性清除浮动的原理？

```
使用clear属性清除浮动，其语法如下：

clear:none|left|right|both

如果单看字面意思，clear:left应该是“清除左浮动”，clear:right应该是“清除右浮动”的意思，实际上，这种解释是有问题的，因为浮动一直还在，并没有清除。

官方对clear属性的解释是：“元素盒子的边不能和前面的浮动元素相邻。”，我们对元素设置clear属性是为了避免浮动元素
对该元素的影响，而不是清除掉浮动。

还需要注意的一点是clear属性指的是元素盒子的边不能和前面的浮动元素相邻，注意这里“前面的”3个字，也就是clear属
性对“后面的”浮动元素是不闻不问的。考虑到float属性要么是left，要么是right，不可能同时存在，同时由于clear
属性对“后面的”浮动元素不闻不问，因此，当clear:left有效的时候，clear:right必定无效，也就是此时clear:left
等同于设置clear:both；同样地，clear:right如果有效也是等同于设置clear:both。由此可见，clear:left和cle
ar:right这两个声明就没有任何使用的价值，至少在CSS世界中是如此，直接使用clear:both吧。

一般使用伪元素的方式清除浮动

.clear::after{
    content:'';
    display:table;//也可以是'block'，或者是'list-item'
    clear:both;
}

clear属性只有块级元素才有效的，而::after等伪元素默认都是内联水平，这就是借助伪元素清除浮动影响时需要设置display属性值的原因。
```

#### 


