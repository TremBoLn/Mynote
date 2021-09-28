# Web前端笔记

## 一、HTML5

---

### 1.1 HTML5新特性

---

### 1.2 HTML input标签（常用）

|       type        |                     功能                     |
| :---------------: | :------------------------------------------: |
|      button       |         定义可点击的按钮，配合Js使用         |
|     checkbox      |    一个勾选框，如，我已阅读并同意用户协议    |
|      coloar       |            拾色器，开发中没什么用            |
| date、month、time |               日期/时间选择器                |
|       file        |    定义文件路径框和浏览按钮，用于上传文件    |
|     password      |                    密码框                    |
|       text        |                    文本框                    |
|       radio       |  单选按钮，多个radio的name不同才能实现单选   |
|      submit       | 提交按钮，将一个form中的内容全部提交给服务器 |

---

## 二、 CSS

---

### 2.1 字体属性复合写法(必须按顺序）

​	font：font-style(斜体之类的）	font-weight(400普通，700加粗)	font-size/line-height	font-family 

---

### 2.2 文本属性

|      属性       |   表示   |          注意点           |
| :-------------: | :------: | :-----------------------: |
|      color      | 文本颜色 |      通常用十六进制       |
|   text-align    | 文本对齐 |     定义文字对齐方式      |
|   text-indent   | 文本缩进 | 可用于段落首行缩进两个2em |
| text-decoration | 文本修饰 |     underline、none等     |
|   line-height   |   行高   |          行间距           |

---

### 2.3 背景属性

|         属性          |   作用   |                   值                    |
| :-------------------: | :------: | :-------------------------------------: |
|   background-color    | 背景颜色 |           十六进制、英文、RGB           |
|   background-image    | 背景图片 |                图片路径                 |
|   background-repeat   | 是否平铺 |            repeat、norepeat             |
|  backgroud-position   | 背景位置 |              多用于精灵图               |
| background-attachment | 背景附着 | scroll背景不会跟随可视区滚动，fixed相反 |

背景属性复合写法

​	background：url	平铺方式	附着方式	水平位置	竖直位置

---

### 2.4 选择器优先级

|       选择器       | 选择器权重 |
| :----------------: | :--------: |
|   继承或通配符*    |    0000    |
| 元素（标签）选择器 |    0001    |
|      类选择器      |    0010    |
|      ID选择器      |    0100    |
|  行内样式 style=   |    1000    |
|    ！important     |     ∞      |

---

### 2.5 元素显示模式（行、块、行内块）

|   显示模式   | 标签                                   | 特点                                                         |
| :----------: | :------------------------------------- | :----------------------------------------------------------- |
|    block     | <h>、<p>、<div>、<ul>、<ol>、<li>      | 1、自己独占一行<br>2、高度、宽度、外边距和内边距都可改变<br>3、宽度默认是父级元素的100%<br> |
|    inline    | <a>、<strong>、<span>、<label>、<em>等 | 1、一行可以显示多个<br>2、高宽设置无效<br>3、默认宽度是内容本身的大小<br>4、行内元素只能容纳文本和其他行内元素 |
| block-inline | <img>、<td>、<input>                   | 1、一行可以显示多个，但是相邻之间会有间隙<br />2、默认宽度是它本身内容的宽度<br />3、可改变大小 |

---

### 2.6 盒子模型

**盒子模型**：内边距、边框、外边距、内容

**CSS boder-box**: 在盒子设置了宽和高后，边框都是往里长

**W3C标准模型**：总宽 = width+padding+margin+border

**边框属性复合写法**：border：border-weight	border-style	border-color

**盒子阴影**：box-shadow: h-shadow	v-shadow	blur(模糊距离)	spread(阴影尺寸)	color

**外边距塌陷**：

​	1.两个同级盒子上限或左右排列，分别给他们的邻边加margin，会取最大值，解决方法，只给一边加margin

​	2.父子级盒子，上边框会合并，子盒子想加margin-top，会导致父盒子加上边距，解决方法：

​			可为父元素定义上边框

​			可为父元素定义上边距

​			可为父元素添加overflow：hidden

---

### 2.7. 浮动

浮动将元素排除在标准流之外，俗称脱标，浮动元素不占用空间，浮动元素碰到自己的边框或其他浮动元素的边框会停留。

其主要目的是为了使没有定义高或宽的父元素可以随内容增加而增大

清除浮动方法：

​	1.父元素overflow：hidden

​	2.

~~~css
.clearfix:after {
            content: "";
            display: block;
            height: 0;
            clear: both;
            visibility: hidden;
        }

        .clearfix {
            *zoom: 1;
        }
~~~

---

### 2.8 定位

| 定位方式          | 特点                                                         |
| ----------------- | ------------------------------------------------------------ |
| static            | 默认值，和标准流一样                                         |
| 绝对定位 absolute | 1.以父级元素为参照对象，父级元素必须要有定位属性<br />2.会脱离标准流，不再占用空间，左右margin:auto会失效，通过top、left、right、bottom调整位置 |
| 相对定位 relative | 1.以自己为参照<br />2.不会脱标                               |
| 固定定位fixed     | 元素在可视板块的固定位置，不会随着滚轮滚动而滚动，脱离文档流 |

---

### 2.9 display、visibility、overflow显示隐藏元素的区别

| 隐藏方式   | 特点                                                         |
| ---------- | ------------------------------------------------------------ |
| display    | 1.通过属性none和block显示、隐藏元素<br />2.隐藏后不占用空间  |
| visibility | 1.通过visible和hidden显示、隐藏元素<br />2.隐藏后仍占据空间  |
| overflow   | 1.visible全部显示，会超出，不剪切内容也不添加滚动条<br />2.hidden不超出内容显示，超出部分隐藏<br />3.scroll不管是否超出，总是显示滚动条<br />4.auto，超出显示滚动条，不超出不显示 |

---

## 三. Js基础

---

​	**Js的同步和异步**：

​		Js是典型的单线程语言，为了实现高并发，所有的同步任务都放在一个执行栈中，异步任务放在任务队列中，放入的主要是回调函数，如普通事件、定时器等

### 3.1 基本数据类型

| 简单数据类型 | 说明                         | 默认值    |
| ------------ | ---------------------------- | --------- |
| Number       | 数字型                       | 0         |
| Boolean      | 布尔类型                     | false     |
| String       | 字符串                       | “”        |
| Undefined    | var a 声明了变量但没有赋值   | Undefined |
| Null         | var a=null 声明了变量a为空值 | null      |

---

### 3.2 数据类型转换

| 转换类型         | 方式                                             |
| ---------------- | ------------------------------------------------ |
| 转换为字符串     | toString()、String()、+拼接                      |
| 字符串转为数字型 | parseInt、parseFloat、Number()、算术运算隐式转换 |
| 转化为布尔型     | Boolean()                                        |

---

### 3.3 Js预解析

​	预解析分为两步：

​		（1）预解析会把所有的var和function提升到当前作用于的最前面，但是只声明不赋值

​		（2）按照顺序执行代码

---

### 3.4 Js对象的创建及调用

​	1.直接创建

```js
	var obj = {
  name: "小明",
  age: 14,
  sayHello: function () {
    console.log("Hello!");
  },
};
console.log(obj.name);
obj.sayHello();
```

​	2.利用new创建

```js
var obj = new Object();
obj.name = "xiaoming";
obj.age = 13;
obj.sayHello = function () {
  console.log("Hello");
};
obj.sayHello();
```

​	3.构造函数

```Js
function People(name, age) {
  this.name = name;
  this.age = age;
  this.sing = function () {
    console.log("冰雨");
  };
}
var xiaoming = new People("xiaoming", 18);
console.log(xiaoming.age);
xiaoming.sing();
```

​	4.遍历对象属性

```js
for (var k in xiaoming) {
  console.log(xiaoming[k]);
}
```

---

### 3.5 Js内置对象

https://developer.mozilla.org/zh-CN

#### 3.5.1 Math

| 常用方法（属性） | 作用                                           |
| ---------------- | ---------------------------------------------- |
| Math.PI          | 圆周率                                         |
| Math.floor()     | 向下取整                                       |
| Math.ceil()      | 向上取整                                       |
| Math.round()     | 四舍五入，负数向数轴正方向                     |
| Math.abs()       | 绝对值                                         |
| Math.max()/min() | 最大值和最小值                                 |
| Math.random()    | 生成0≤x＜1的随机数，生成其他范围的随机数看文档 |

---

#### 3.5.2 Date

​	格式化时间和日期

```js
var date = new Date();
var year = date.getFullYear();
var month = date.getMonth() + 1;
var dates = date.getDate();
var dayarr = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六",
];
var hour = date.getHours();
hour = hour < 10 ? "0" + hour : hour;
var minutes = date.getMinutes();
minutes = minutes < 10 ? "0" + minutes : minutes;
var seconds = date.getSeconds();
seconds = seconds < 10 ? "0" + seconds : seconds;
var day = dayarr[date.getDay()];
console.log(year +" " +month +" " +dates +" " +day +" " +hour +":" +minutes +":" +seconds
);

```

​	**时间戳（距离1970 1月1日过去的毫秒数常用两种方法）**

```js
console.log(Date.now());

var date1 = +new Date();
console.log(date1);
```

​	**倒计时**

```js
function countDown(time) {
  var nowTime = +new Date();
  var inputTime = +new Date(time);
  var times = (inputTime - nowTime) / 1000;
  var d = parseInt(times / 60 / 60 / 24);
  var h = parseInt((times / 60 / 60) % 24);
  var m = parseInt((times / 60) % 60);
  var s = parseInt(times % 60);
  console.log(d + "天" + h + "时" + m + "分" + "秒");
}
countDown("2021-9-10 8:00:00");
```

---

#### 3.5.3 Array

| 常用API                         | 作用                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Array.isArray(obj)              | 判断是否是数组                                               |
| Array.push()                    | 后插                                                         |
| Array.unshift()                 | 头插                                                         |
| Array.pop()                     | 尾删                                                         |
| Array.shift()                   | 头删                                                         |
| Array.reverse()                 | 翻转                                                         |
| Array.sort()                    | 默认按照ASIC排序，Array.sort(function(a,b){<br />      return a-b;<br />})；升序 |
| Array.indexOf(value)            | 返回value下标，找不到返回0                                   |
| Array.toString()                | 数组转换为字符串，保留逗号                                   |
| Array.join(’分隔符‘)            | 数组转换为字符串，传参符分割                                 |
| Array.splice(index,length)      | 从index开始删length个                                        |
| Array.from(obj,()=>{})          | 将任何集合类对象转化为数组对象                               |
| Array.of(,,,,,,,)               | 将所有参数放在同个数组中返回                                 |
| Array.includes()                | 数组中是否包含                                               |
| Array.keys()/values()/entries() | 返回迭代器用于遍历                                           |

```js
let arr = new Array("a", "b", "c");
console.log(arr);
for (let index of arr.keys()) {
  console.log(index);
}
for (let val of arr.values()) {
  console.log(val);
}
for (let [key, value] of arr.entries()) {
  console.log(key, value);
}
```



---

#### 3.5.4 String

​	字符串是不可变类型，每次赋值或修改都会开辟新的内存。

| 常用API                   | 作用                             |
| ------------------------- | -------------------------------- |
| indexOf(value,int)        | 返回value下标,从int下标开始查找  |
| CharAt(index)、str[index] | 返回字符串下标的字符             |
| CharCodeAt(index)         | 返回该索引指向字符的ASCII        |
| substr(start,length)      | 从start开始，截取length长度      |
| slice(start,end)          | 从start开始，截取到end之前的位置 |
| replace(a,b)              | 把str中的第一个a替换为b          |
| split(分隔符)             | 以分隔符为间隔把字符串转换为数组 |

​	统计字符串出现频率最多的字符

```js
function maxFreq(str) {
  var t = {};
  for (var i = 0; i < str.length; i++) {
    if (t[str[i]]) {
      t[str[i]]++;
    } else {
      t[str[i]] = 1;
    }
  }
  var max = 0;
  var result = "";
  for (var k in t) {
    if (t[k] > max) {
      max = t[k];
      result = k;
    } else {
      continue;
    }
  }
  console.log(result + ":" + max);
}
maxFreq("aabbbcccc");

```

---

### 3.6 立即执行函数

```js
(function getSum(a, b) {
  console.log(a + b);
})(1, 2);

```



## 四.WebAPI

### 4.1 DOM(document object model)

---

#### 4.1.1 获取元素

| API                                             | 作用                           |
| ----------------------------------------------- | ------------------------------ |
| document.getElementById()                       | 返回指定ID的元素对象           |
| document.getElementsByTagName()                 | 返回指定标签名元素的集合       |
| document.getElementsByClassName()               | 返回指定类名元素的集合         |
| document.querySelector()                        | 返回制定选择器元素的第一个对象 |
| document.querySelectorAll()                     | 返回指定选择器元素的集合       |
| document.documentElement                        | 返回文档中的html对象           |
| document.body                                   | 返回文档中的body               |
| element.parentNode                              | 获取当前节点最近的父节点       |
| element.chidren                                 | 获取当前元素所有的子节点       |
| element.firstElementChild 可能有兼容性问题      | 获取当前节点的第一个子节点     |
| element.lastElementChild 可能有兼容性问题       | 获取当前节点的最后一个子节点   |
| element.nextElementSibling 可能有兼容性问题     | 获取下一个兄弟节点             |
| element.previousElementSibling 可能有兼容性问题 | 获取上一个兄弟节点             |
| element.appendChild(child)                      | 在当前节点末尾添加一个子节点   |
| element.insertBefore(chilid)                    | 在当前节点最前面添加一个子节点 |

---

#### 4.1.2 常用事件以及注册、删除事件方法

1. object.event_name = function(){}，如果定义两个相同的事件，前面的会覆盖后面的

   解绑方式

   ```js
   object.eventName = function(){
     事件内容；
     this.onclick = null;
   }
   ```

   

2. Object.addEventListener("event_name",function(){}a)，事件名不加on，相同事件名按照顺序先后执行

   解绑当时

   ```js
   var btn = document.querySelector("button");
   btn.addEventListener("click", fn);
   function fn() {
     alert("22");
     btn.removeEventListener("click", fn);
   }
   ```

   

|                           | 效果                                                       |
| ------------------------- | ---------------------------------------------------------- |
| onclick                   | 点击                                                       |
| onfocus                   | 光标定位                                                   |
| onblur                    | 光标离开                                                   |
| onmouseover、onmouseenter | 鼠标经过，前者经过子元素也会触发，后者不会，因为不触发冒泡 |
| onmouseout                | 鼠标离开                                                   |
| omousemove                | 鼠标移动                                                   |
| onkeyup                   | 某个键松开时触发，不区分大小写                             |
| onkeydonw                 | 某个键按下时触发，不区分大小写                             |
| onkeypress                | 某个键按下时触发，不识别键盘功能键                         |
| onmousedown               | 鼠标按下                                                   |
| onmousedown               | 鼠标移动                                                   |

---

#### 4.1.3 操作元素

| API                                        | 作用                                                         |
| ------------------------------------------ | ------------------------------------------------------------ |
| element.innerText                          | 返回元素内的内容，但不识别html标签，空格和换行也会消除       |
| element.innerHTML                          | 返回元素内的内容，包括html标签，保留空格和换行               |
| element.style.somestyle                    | 修改style属性                                                |
| element.className                          | 为元素增加类名，会覆盖原来的类名(完成属性修改)，解决方法：<br />element.className = "prename aftername" |
| element.内置属性                           | 获取元素本身内置属性，如id，class等                          |
| element.getAttribute()                     | 获取自定属性值                                               |
| element.setAttribute("key"，"value")       | 设置key属性的值                                              |
| element.removeChild()                      | 删除指定子节点                                               |
| element.cloneNode(true or false) 默认false | 克隆当前节点，默认只复制标签，true时能复制其他样式           |

---

#### 4.1.4 H5自定义属性

​	要求程序员在标签内定义自定义属性时格式统一为data-属性名 = ""

​	可通过 标签名.dataset.自定义属性名来获取

```js
<div data-name="小明"></div>
var div = document.querySelector("div");
console.log(div.dataset.name);
```

---

#### 4.1.6 DOM事件流与事件对象

**事件对象**：

​	在事件函数function(“event”)中添加event就创建了一个事件对象，可通过event.sth调用相应的事件属性或方法。其中：

​	event.target是获取触发事件的对象，this获取的是绑定事件的对象

**DOM事件流分为三个阶段**：捕获阶段、当前目标阶段、冒泡阶段

​	捕获阶段：从document->html->element.father->element.son查看是否有规定的事件，有则执行

​	当前目标阶段：执行事件

​	冒泡阶段：从element.son->element.father->html->document查看是否有规定的事件，有则执行，开发中常用冒泡阶段。

```js
var father = document.querySelector(".father");
var son = document.querySelector(".son");

son.addEventListener("click", function () {
  alert("son");
});
father.addEventListener("click", function () {
  alert("father");
});
```

​	**阻止冒泡**

```js
son.addEventListener("click", function (event) {
  alert("son");
  event.stopPropagation();
});
father.addEventListener("click", function () {
  alert("father");
});
```

---

​	**事件委托：**

​		不设置每个子节点的单独事件，而是将监听器设置在父节点上，然后利用冒泡原理影响每个子节点

---

### 4.2 BOM(浏览器对象模型)

#### 4.2.1 BOM常用事件（window）

|                    | 作用                                                |
| ------------------ | --------------------------------------------------- |
| onload             | 等待DOM、CSS、图片、flash等加载完毕                 |
| onDOMContentLoaded | onDOMContentLoaded，仅等待DOM(document标签)加载完毕 |

---

#### 4.2.2 两种定时器

​	**setTimeout**：过一段时间启动回调函数

```js
var timer = setTimeout(function(){},time); //创造定时器
clearTimeout(timer); //停止定时器
```

​	**setInterval**：间隔一段时前调用回调函数

​	**倒计时案例**：

```js
var curTime;
var tarTime = +new Date("2021-9-10 00:00:00");
var difTime = (tarTime - curTime) / 1000;
var li = document.querySelectorAll("li");

var day;
var hour;
var min;
var sec;

function countDown() {
  curTime = +new Date();
  difTime = parseInt((tarTime - curTime) / 1000);
  day = parseInt(difTime / 3600 / 24);
  day = day < 10 ? "0" + day : day;
  li[0].innerHTML = day;
  hour = parseInt(difTime / 3600) % 24;
  hour = hour < 10 ? "0" + hour : hour;
  li[2].innerHTML = hour;
  min = parseInt(difTime / 60) % 60;
  min = min < 10 ? "0" + mim : min;
  li[4].innerHTML = min;
  sec = difTime % 60;
  sec = sec < 10 ? "0" + sec : sec;
  li[6].innerHTML = sec;
}

setInterval(countDown, 1000);
```

---

#### 4.2.3 location对象

​	**统一资源定位符URL**

​		protocol：//host[:port]/path/[?query]#fragment

​		http://localhost:8080/%E9%A1%B5%E9%9D%A2%E8%B7%B3%E8%BD%AC%E4%BC%A0%E9%80%92%E5%8F%82%E6%95%B0/index.html?uname=123

| 组成     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| protocol | 通信协议，http                                               |
| host     | 域名，上面是本地域名localhost                                |
| port     | 通信端口号，默认80                                           |
| path     | 路径，上面乱码是因为中文                                     |
| query    | 参数，通过表单在两个html中传递参数，以键值对=的方式存在，多个键值对用&分割 |
| fragment | 片段 #后面的内容，常见于连接，上面没有                       |

---

​	**location属性**:

| 属性     | 返回值         |
| -------- | -------------- |
| href     | 获取整个URL    |
| host     | 返回主机或域名 |
| port     | 返回端口号     |
| pathname | 返回路径       |
| search   | 返回参数       |
| hash     | 返回片段       |

​	**location方法**：

| 方法           | 返回值                 |
| -------------- | ---------------------- |
| assign(“url”)  | 跳转到某页面           |
| replace("url") | 替换当前页面，不可倒退 |
| .reload()      | 刷新页面               |

---

#### 4.2.4 navigator对象

​	常用navigator.userAgent属性，当前浏览器信息

```js
if(navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone|/i))){
  window.location.href = "移动端连接";//跳转到移动端页面
}else{
  window.location.href = "PC端连接";//跳转到PC端页面
}
```

---

#### 4.2.5 history对象

与浏览器历史记录进行交互

| 常用方法  | 作用                                        |
| --------- | ------------------------------------------- |
| back()    | 后退                                        |
| forword() | 前进                                        |
| go(参数)  | 前进后退功能，1前进一个页面，-1后退一个页面 |

---

### 4.3 PC端网页特效

#### 	4.3.1 offset

​			**常用属性**

| 属性                 | 作用                                                       |
| -------------------- | ---------------------------------------------------------- |
| element.offsetParent | 返回该元素带有定位的父级元素，如果父级元素都没有则返回body |
| element.offsetTop    | 返回元素与上方离带有定位的父级元素的距离                   |
| element.offsetLeft   | 返回元素左边距带有定位的父级元素的距离                     |
| element.offsetWidth  | 返回自身包括padding、边框、内容区的宽度，你不带单位        |
| element.offsetHeight | 返回自身包括padding、边框、内容区的高度，你不带单位        |

​	**offset和style的区别**

​		1.offset可以得到任意样式表中的杨是值，style只能得到行内样式表中的样式值

​		2.offset没有单位，style有单位

​		3.style获得的width和height不包含padding和border

​		4.offset获取的宽高只读

**鼠标移动元素案例**

```js
title.addEventListener("mousedown", function (e) {
  var x = e.pageX - login.offsetLeft;
  var y = e.pageY - login.offsetTop;

  document.addEventListener("mousemove", move);

  function move(e) {
    login.style.marginLeft = "0"; // 为了水平居中的bug
    login.style.left = e.pageX - x + "px";
    login.style.top = e.pageY - y + "px";
  }

  document.addEventListener("mouseup", function () {
    this.removeEventListener("mousemove", move);
  });
});
```

---

#### 4.3.2 元素可视区client

| 属性                 | 作用                                                         |
| -------------------- | ------------------------------------------------------------ |
| Element.clientTop    | 返回元素上边框的大小                                         |
| element.clientLeft   | 返回元素左边框的大小                                         |
| element.clientWidht  | 返回自身包括padding、内容区的宽度，不含边框，不带单位，如果内容超出，则把超出部分也算上 |
| element.clientHeight | 放回包括自身padding、内容区的高度，不含边框、不带单位，如果内容超出，则把超出部分也算上 |

---

#### 4.3.3 元素scroll系列属性

| 属性                | 作用                                   |
| ------------------- | -------------------------------------- |
| element.scrollTop   | 返回被滚动条卷上去的高度，不带单位     |
| element.scrollLeft  | 返回被卷去的左侧距离，返回数值不带单位 |
| Element.scrollWidth | 返回自身宽度，不含边框，不带单位       |
| element.srollHeight | 返回自身高度，不含边框，不带单位       |

---

#### 4.3.4 缓动动画

```js
var father = document.querySelector(".father");

var animation = function (obj, target) {
  // clearInterval(obj.timer);
  obj.timer = setInterval(function () {
    var step = Math.ceil((target - obj.offsetLeft) / 50); 
    step > 0 ? Math.ceil(step) : Math.floor(step);//正的向上取证，负的向下取证
    if (obj.offsetLeft >= target) {
      clearInterval(obj.timer);
    }
    obj.style.left = obj.offsetLeft + step + "px";
  }, 15);
};

father.onclick = function () {
  animation(father, 800);
};

// father.addEventListener("click", animation(father, 800)); 这个没用。。

```

---

### 4.4 本地存储

#### 	4.4.1 window.sessionStorage

​		1.生命周期为关闭浏览器窗口

​		2.同一个窗口下可以共享

​		3.以键值对的形式存储

```js
var input = document.querySelector("input");
var set = document.querySelector(".set");
var get = document.querySelector(".get");
var remove = document.querySelector(".delete");

//添加数据
set.addEventListener("click", function () {
  sessionStorage.setItem("name", input.value);
});


//获取数据
get.addEventListener("click", function () {
  var val = sessionStorage.getItem("name");
  input.value = val;
});


//删除数据，删除所有数据sessionStorage.clear()
remove.addEventListener("click", function () {
  sessionStorage.removeItem("name");
});

```

---

#### 4.4.2 window.localStorage

 	1. 生命周期永久，需要手动删除
 	2. 以键值对方式存储
 	3. 可多窗口存储
 	4.只能存储字符串

使用方法和上述相同

---

## 五、JQuery

### 5.1 Jquery和DOM对象的区别以及转换

​		1.jquery获取对象$("选择器")，获取的对象是封装后的DOM对象，以伪数组的方式存储

​		2.不能使用DOM的属性和方法，只能使用jquery封装的属性和方法

```js
var son = document.querySelector(".father .son");
var father = document.querySelector(".father");
$(".son").hide();
$(".son")[0].style.display = "block";//Jquery转DOM
$(father).hide();//DOM对象转JQuery对象

```

---

### 5.2 JQuery筛选选择器以及修改样式

​		**链式编程：**$("选择器").css(需要修改的样式，值).选择器.css(需要修改的样式，值)；

​		如果需要修改多组样式：.css({k1:v1,k2:v2})

​		因为JQuery获取对象以伪数组方式存储，因此修改样式时会进行隐式迭代，将数组中的所有对象修改样式	

| 语法       | 描述                   |
| ---------- | ---------------------- |
| :first     | 获取伪数组中的第一个   |
| :last      | 获取伪数组中的最后一个 |
| :eq(index) | 按索引号获取           |
| :odd       | 获取索引号为奇数的元素 |
| :even      | 获取索引号为偶数的元素 |

| 筛选方法             | 描述                           |
| -------------------- | ------------------------------ |
| .parent()            | 查找父级                       |
| .children(selector)  | 查找最近子级选择器的对象       |
| .find(selector)      | 查找所有子级选择器的对象       |
| .siblings(selector)  | 查找对应选择器的兄弟元素       |
| .nextAll()           | 查找当前元素之后所有同辈元素   |
| .prevAll()           | 查找当前元素之前所有的同辈元素 |
| .hasClass(className) | 查找当前元素是否有该类名       |
| .eq(index)           | 等价于:eq(index)               |

---

其它常用API，原生Js会覆盖类名，而jquery又多种API可供使用

| API                         | 作用                                                   |
| --------------------------- | ------------------------------------------------------ |
| .addClass(className)        | 添加类名                                               |
| .removeClass(className)     | 移除类                                                 |
| .toggleClass(className)     | 切换类                                                 |
| .hover(fn1,fn2)or.hover(fn) | 鼠标经过执行fn1，鼠标离开执行fn2，鼠标经过离开都执行fn |

---

### 5.3 动画

| API                                  | 使用方法                                                     |
| ------------------------------------ | ------------------------------------------------------------ |
| .show(speed,way)                     | speed为出现速度，可以用slow，normal和fast也可自定义事件，way为出现方式，又linear和swing，默认swing |
| .hide(speed,way)                     | 同上                                                         |
| .toggle(speed,way)                   | 同上，出现消失来回切换                                       |
| .slideUp(speed)                      | 上拉，方法同上                                               |
| .sildeDown(speed)                    | 下拉，方法同上                                               |
| .slideToggle(speed)                  | 切换，方法同上                                               |
| .fadeIn(speed)                       | 淡入，方法同上                                               |
| .fadeOut(speed)                      | 淡出，方法同上                                               |
| .fadeToggle(speed)                   | 切换，方法同上                                               |
| .fadeTo(speed,opacity)               | 按速度调整透明度                                             |
| .animate({自定义动画样式},speed,way) | {height:,width:,left:,top:}                                  |

---

### 5.4 获取元素属性

| API                      | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| .prop("属性名","修改值") | 获取/修改元素自带属性，参数只有属性名时获取，两个修改        |
| .attr("属性名","修改值") | 获取/修改自定义属性                                          |
| .data("属性名","修改值") | 获取/修改自定义属性，此属性不会添加在DOM中，而是添加在内存中，当自定义属性data-时，获取不用加data- |
| .html(内容)              | 相当于innerHtml，当有参数时修改                              |
| .text(内容)              | 相当于innerText                                              |
| input.val(内容)          | input标签内的value                                           |

---

### 5.5 元素操作

| 操作         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| 遍历1        | $().each(function(index,domEle){})<br />index为索引号，domEle是返回该下标元素的DOM对象 |
| 遍历2        | $.each($(),function(index,ele))                              |
| 创建元素     | $("<></>") 内填标签名                                        |
| 添加子元素   | $().append()尾插、$().prepend()头插、                        |
| 添加兄弟元素 | $().after、$().before()                                      |
| 删除         | $().remove()删除元素本身、$().empty()删除子元素              |

---

### 5.6 尺寸、位置操作

| API                                   | 描述                                                  |
| ------------------------------------- | ----------------------------------------------------- |
| .width().height()                     | 返回width和height                                     |
| .innerWidth()/.innerHeight            | 返回高度和宽度，包含padding                           |
| .outerWidth()/.outHeight()            | 返回高度和宽度，包含padding和border                   |
| .outerIwidth(true)/.outerHeight()     | 返回高度和宽度，包含padding、border、margin           |
| .offset()/.offset((top:200,left:200)) | 不带参数时获取元素相对文档的left和top，带参数时为设置 |
| .position()                           | 返回元素相对带有定位的父级元素的left和top，不能设置   |
| .scrollTop()/.scrollLeft()            | 返回被卷去的值                                        |

---

### 5.7 JQuery事件

#### 	5.7.1 注册/解绑事件

​		.on("事件"，“子元素(用来实现事件委托，可选)”，function)

​		.off("已绑事件"，“子元素”)

```js
$(".father").on({
  click: function () {
    $(".father").css("background-color", "red");
  },
  mouseenter: function () {
    $(".father").css("background-color", "green");
  },
});

```

​	.on("事件"，“子元素(用来实现事件委托，可选)”，function(event))

​	阻止冒泡：event.stopPropagation()

​	组织默认行为: return false 或 event.preventDefault()		

---

### 5.7 JQuery的深浅拷贝

​	$.extend(trueOrfalse,target,object)

​	1.true为深拷贝，false为浅拷贝

​	2.复制object的内容到target

​	3.浅拷贝是把拷贝的对象复杂数据类型（对象）中的地址拷贝给目标对象，两个对象共用一个存储空间，修改目标对象会影响原对象

​	4.深拷贝会另外开辟存储空间存放拷贝的数据，修改时不会影响原数据

---

### 5.8 多库共存

​	此时$等价于x，防止别的库中$发生冲突

```js
var x = $.noConflict();
console.log(x(".father"));
```

---

## 六、ES6

### 6.1 类的创建和使用

#### 6.1.1 类的创建

```js
class People {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
}

var p1 = new People("小明");
console.log(p1.getName());
```

---

#### 6.1.2 类的继承

```js
class Father {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
  say() {
    return "我是爸爸";
  }
}

class Son extends Father {
  constructor(name) {
    super();	//子类如果想使用父类的方法，需要在this之前调用super()
    this.name = name;
  }
  say() {
    console.log(super.say() + "的儿子");
  }
}

var son = new Son("小明");
console.log(son.getName());
son.say();

```

---

### 6.2 ES5构造函数原型

​	如果通过构造函数创建对象，如果所有对象有一个完全相同的方法，每次创建一个实例对象时都会new一个新的内存空间存放这个方法，因此在实现此类方法时将此类方法存储到构造函数的内置属性prototype类(构造函数原型)中来共享方法,构造函数prototype属性也即实例对象的\__proto__属性(对象原型,本质也是一个类)

```js
function People(name) {
  this.name = name;
}
People.prototype.Skill = function () {
  console.log("我会唱歌");
};

var p1 = new People("小明");
var p2 = new People("小红");
console.log(p1.Skill());
console.log(p2.Skill());
console.log(p1.__proto__);
console.log(People.prototype);

```

![image-20210918132451106](/Users/lunan/Library/Application Support/typora-user-images/image-20210918132451106.png)

---

### 6.3 函数高级方法

#### 	6.3.1 改变函数内部this指向

​		**call：**

```js
class People {
  constructor(name) {
    this.name = name;
  }
}

var test = function () {
  console.log(this);
};

test.call(); //global
test.call(People);//People

```

---

​		**applay:**

​		第一个参数也为this指向对象，第二个参数必须为数组

```js
var nums = [66, 12, 24, 40, 100];
console.log(Math.max.apply(null, nums));
```

---

​		**bind:**

​		在不调用原来函数的情况下改变原来函数内部的this指向，返回的是一个改变this之后的新函数

```js
var People = function (name) {
  this.name = name;
};

var test = function () {
  console.log(this);
};

var People_test = test.bind(People);
People_test();

```

### 	6.4 闭包

​		闭包指有权访问另一个函数作用域中变量的函数

```js
var lis = document.querySelectorAll("ul li");
console.log(lis);
for (var i = 0; i < lis.length; i++) {
  console.log(1);
  (function (i) {
    lis[i].addEventListener("click", function () {
      console.log(i);
    });
  })(i);
}
```

---

### 	6.5 正则表达式

```js
var reg = /^[^abc]$/;
console.log(reg.test("1"));
```

| 符号                                | 描述                                         |
| ----------------------------------- | -------------------------------------------- |
| /^abc/                              | 必须以abc开头                                |
| /abc$/                              | 必须以abc结尾                                |
| /^abc$/                             | 只能为abc                                    |
| /abc/                               | 含abc就可                                    |
| /[abc]/                             | 含a或b或c就可                                |
| /^[abc]$/                           | 只能为a，b，c中的一个                        |
| /^[a-z]$/                           | 只能为一个英文字母                           |
| /^[a-zA-Z0-9]$/                     | 只能为一个英文字母或数字                     |
| /^\[^a-zA-Z0-9]$/                   | 里面的^为取反的意思，不能为英文和数字        |
| /^a*$/                              | a可出现0次以上                               |
| /^a+$/                              | a出现1次以上                                 |
| /^a?$/                              | a可出现0次或1次                              |
| /^a{3,10}$/                         | a出现3~10次                                  |
| /^\[^a-zA-Z0-9]{8,16}$/             | 8-16位的[]内字符                             |
| /^\[^a-zA-Z0-9]{8,16}$/g or i or gi | g为全局匹配，i忽略大小写，gi全局且忽略大小写 |

 	1. 中括号内表示字符集合，人已匹配中括号内容中的一个
 	2. 大括号里面表示重复次数
 	3. 小括号代表优先级

| 预定义类 | 说明                                  |
| -------- | ------------------------------------- |
| \d       | [0-9]                                 |
| \D       | [^0-9]                                |
| \w       | [A-Za-z0-9_]                          |
| \W       | [^A-Za-z0-9_]                         |
| \s       | [\t\r\n\v\f] 匹配换行、制表、空格符等 |
| \S       | [^\t\r\n\v\f]                         |

```js
// 全国座机号格式 010-12345678 或 0530-1234567
var reg = /\d{3,4}-\d{7,8}/;
console.log(reg.test("010-1234567"));
```

```js
var str = "!imba667788!";
var reg = /\w/g;
var new_str = str.replace(reg, "*");
console.log(new_str);
console.log(str);
```

---

### 6.6 const、let和var

​	**let：**

​		1.不会变量提升，只能先声明再使用

​		2.let声明只能再块级作用域中使用

​		3.let声明的变量不能重复声明

​	**const:**

​		1.不会变量提升，只能先声明再使用

​		2.let声明只能再块级作用域中使用

​		3.let声明的变量不能重复声明

​		4.一旦被声明，无法被修改

​		5.可以声明对象，且能修改对象中的属性		

---

### 6.7 模板字符串

```js
const test = document.querySelector(".other");
let html_str = (test.innerHTML = `<ul>
<li id=${"sb"}>${"大帅逼"}</li>
</ul>`);

test.innerHTML = html_str;
```

---

### 6.8 函数剩余参数

```js
let book = {
  name: "十万个为什么",
  athor: "不知道",
  price: 20,
};

function getData(obj, ...keys) {
  let result = {};
  for (let i = 0; i < keys.length; i++) {
    result[keys[i]] = obj[keys[i]];
  }
  return result;
}

console.log(getData(book, "name", "athor", "price"));
```

---

### 6.9 箭头函数

​	()=>{} 等价于function(){}，函数内容只有一行时可以不加{}

​	箭头函数没有内部this指向，此时箭头函数内部的this会根据链式查找其所指明的this对象

​	箭头函数不能用new来实例化对象

```js
let add = (a, b) => a + b;
console.log(add(10, 20));
```

---

### 6.10 解构赋值

```js
let Students = {
  s1: {
    name: "张三",
    age: 14,
  },
  s2: {
    name: "李四",
    age: 15,
  },
  s3: {
    name: "王五",
    age: 16,
  },
};

const { s1, ...others } = Students;
console.log(others);
```

---

### 6.11 Symbol变量（xxx搞不懂）

​	原始数据类型Symbol，它表示是独一无二的变量

​	最大的用途：用来定义对象的私有变量

---

### 6.12 Set(集合)

​	无重复值的有序列表

| 方法      | 描述       |
| --------- | ---------- |
| .add()    | 添加元素   |
| .delete() | 删除元素   |
| .has()    | 是否含元素 |
| .size     | 长度       |

```js
var myset = new Set([1, 2, 2, 3, 3, 3, 5]);
console.log(myset);
var arr = Array.from(myset);
console.log(arr);
```

---

### 6.13 Map

​	键值对的有序列表，键和值是任意类型

| 方法            | 描述               |
| --------------- | ------------------ |
| .set(key,value) | 添加键值对         |
| .get(key)       | 得到对应key的value |
| .has(key)       | 是否存在键值对     |
| .delete('key')  | 删除对应键值对     |
| .clear          | 清空map            |

---

### 6.14 Promise对象(先这样，后面再加)

​	**回调地狱：**

​		代码耦合性高，牵一发而动全身，难以维护

​		大量冗余代码相互嵌套，可读性差

```js
setTimeout(function () {
  console.log("我是第一层");
  setTimeout(function () {
    console.log("我是第二层");
    setTimeout(function () {
      console.log("我是第三层");
    }, 3000);
  }, 2000);
}, 1000);

```

---

​	**promise:**

​		1.Promise是个构造函数，new出来的是一个实例对象，代表一个异步操作

​		2.then()方法用来预先指定成功和失败的回调函数

​				p.then(success=>(), error=>())

```js
let random_Promise = function () {
  let p = new Promise(function (resolve, reject) {
    setTimeout(() => {
      var num = Math.ceil(Math.random() * 10);
      if (num > 5) {
        resolve(num);
      } else {
        rejecte(num + "不够大");
      }
    }, 2000);
  });
  return p;
};

random_Promise().then(
  (data) => console.log("成功接收到data:", data),
  (reason) => console.log("接受失败" + reason)
);
```

---

​	**promise异步读取文件:**

```js
//npm install then-fs本地安装包
import thenFs from "then-fs";
// then-fs的readFile()返回一个Promise对象，因此可以调用then方法

thenFs.readFile("./test1.txt", "utf8").then((r1) => {
  console.log(r1);
  return thenFs.readFile("./test2.txt", "utf8").then((r2) => {
    console.log(r2);
    return thenFs.readFile("./test3.txt", "utf8").then((r3) => {
      console.log(r3);
    });
  });
});
--------------------------------------------------------------------
//如果将.catch()放在中间，则不会影响后续的执行步骤，若将.catch放在最后，则捕获所有err，出现一个err就终止
.readFile("./testx.txt", "utf8")
  .catch((err) => {
    console.log(err.message);
  })
  .then((r1) => {
    console.log(r1);
    return thenFs.readFile("./test2.txt", "utf8").then((r2) => {
      console.log(r2);
      return thenFs.readFile("./test3.txt", "utf8").then((r3) => {
        console.log(r3);
      });
    });
  });
```

---

​	**all()和race():**

```js
import thenFs from "then-fs";
// then-fs的readFile()返回一个Promise对象，因此可以调用then方法

let promiseArr = [
  thenFs.readFile("./test1.txt", "utf8"),
  thenFs.readFile("./test2.txt", "utf8"),
  thenFs.readFile("./test3.txt", "utf8"),
];

//等待所有的promise异步操作执行完后进行then操作
Promise.all(promiseArr).then((result) => {
  console.log(result);
});

//只要任何一个异步操作完成，就执行下一步的then操作
Promise.race(promiseArr).then((result) => {
  console.log(result);
});

先输出111，再输出[111,222,333]
```

---

### 6.15 ES6 模块化

​	在当前目录下的终端中输入nmp init -y 生成package.json文件，在最上面添加"type":"module",

#### 	6.15.1 默认导入导出

​		默认导入导出只能在文件执行一次

​		默认导出的名称可以任意

```js
class People {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
let p1 = new People("小明", 14);
export default {
  p1,
  People,
};
----------------

import sth from "./test.js";
console.log(sth.p1);
```

---

#### 	6.15.2 按需导出

​		1.每个模块中可以使用多次按需导出

​		2.按需导入的成员名称必须和按需导出的名称一致

​		3.导入时可以用as重命名

​		4.按需导入可以和默认导入一起使用

```js
class People {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

export let p1 = new People("小明", 14);
export let add = (a, b) => a + b;
----------------------------------------------
import { p1, add } from "./test.js";
console.log(p1);
console.log(add(1, 2));

```

---

#### 	6.15.3 直接导入并执行模块中的代码

```js
let add = (a, b) => a + b;
console.log(add(1, 2));
--------------------------------
import "./test.js";
```

---

### 6.16 async和await

​	1.如果在function中使用了await，则function必须被async修饰

​	2.在async方法中，第一个await之前的代码都同步执行，await之后的代码会加入异步队列，因此先会执行console.log("C")

```js
import thenFs from "then-fs";
// then-fs的readFile()返回一个Promise对象，因此可以调用then方法

console.log("A");
async function getAllFile() {
  console.log("B");
  const r1 = await thenFs.readFile("./test1.txt", "utf8");
  const r2 = await thenFs.readFile("./test2.txt", "utf8");
  const r3 = await thenFs.readFile("./test3.txt", "utf8");
  console.log(r1, r2, r3);
  console.log("D");
}

getAllFile();
console.log("C");
```

---

### 6.17 EventLoop

​	JavaScript是单线程语言，为了防止某个耗时任务导致程序假死，js把待执行任务分为了两类：

​		**同步任务：**

​			非耗时任务，指的是在主线程上排队执行的那些任务

​			只有前一个任务执行完毕，才能执行后一个任务

​		**异步任务：**

​			耗时任务，异步任务由js委托给宿主环境进行执行

​			当异步任务执行完成后，会通知js主线程执行异步任务的回调函数

---

### 6.18 宏任务和微任务

​	Js把异步任务又分为宏任务和微任务

​		**宏任务:**

​			异步ajax请求

​			setTimeout、setInterval

​			文件操作

​			其他宏任务

​	**微任务：**

​			Promise.then .catch .finally

​			Process.nextTick

​			其他微任务

![image-20210926154322399](/Users/lunan/Library/Application Support/typora-user-images/image-20210926154322399.png)

---

## 七、WebPack

### 	7.1 手动配置WebPack

​		1.在工作目录终端输入npm init -y生成package.json

​		2.新建src文件，在内新建index.html和index.js

​		3.装jquery，npm install jquery -S，import $ from "jquery"

​		4.npm install webpack -D，npm install webpack-cli -D

​		5.新建webpack-config.js文件，添加：

​				module.export = {

​					mode:"development" or "production"

​				}

​		6.修改package.json中的script:{}中的内容，改为"dev":"webpack",dev为任意名

​		7.运行 npm run dev或者自己取得其他名，生成disc文件以及内部的main.js

​		8.在html文件中引入main.js

```js
entry: path.join(__dirname, "./src/index.js"), //修改src中.js文件名，否则不是index.js就会报错
  output: {
    path: path.join(__dirname, "./dist"), //打包后生成dist文件,可改名
    filename: "js/main.js", //改名生成.js文件,存放在dist下的js文件夹中
  },
```



---

### 7.2 安装Webpack插件

​		**web-dev-server脚本安装与使用:**

​			1.npm install web-dev-server@3.11.2 -D

​			2.在package.json文件中script添加dev: "webpack serve"

​			3.index.html引入	/main.js

​			3.npm run dev，打开localhost:8080，点击src自动进入index.html，ctrl+s保存自动显示

​			4.想要运行后直接打开，在module.exports中添加：

```js
devServer: {
    open: true,
    // port:80,如果端口号是80，直接localhost就可打开
    // host: "127.0.0.1",打开路径
  },
```

---

​		**html-webpack-plugin插件安装与使用（localhost:8080/直接打开index.html）:**

​			1.pm install html-webpack-plugin@5.3.2 -D

​			2.webpack.config.js文件中添加

```js
const HtmlPlugin = require("html-webpack-plugin");

const htmlPlugin = new HtmlPlugin({
  template: "./src/index.html",	//拷贝文件目录
  filename: "./index.html",	//将文件拷贝目录
});

module.exports = {
  mode: "development",
  plugins: [htmlPlugin],//HtmlPlugin脚本数组
};

```

​	**每次保存dev-server自动覆盖原来的dist文件：**

​		npm install --save-dev clean-webpack-plugin

```js
const { CleanWEbpackPlugin } = require("clean-webpack-plugin
                                       
plugins: [htmlPlugin, new CleanWEbpackPlugin()],
```

---

### 7.2 WebPack中的loader加载器

​	Webpack只能处理.js模块的文件，.css、.less则需要调用loader处理

​	**配置loader加载css文件：**

​		需要在index.js中导入 import 'css文件路径名'

​		npm i style-loader@3.0.0 css-loader@5.2.6 -D

​		webpack.config.js文件配置

```js
module: {
    rules: [
      //定义了不同模块对应的loader
      { test: /\.css$/, use: ["style-loader", "css-loader"] },
    ],
  },
```

​	**配置loader加载less文件**

​		导入.less文件

​		npm i less-loader@10.0.1 less@4.1.1 -D

​		webpack.config.js文件配置		

```js
module: {
    rules: [
      //定义了不同模块对应的loader
      { test: /\.css$/, use: ["style-loader", "css-loader"] },
      { test: /\.less$/, use: ["style-loader", "css-loader", "less-loader"] },
    ],
  },
```

​	**配置loader加载图片**

​		导入图片文件 import 自定义名 from 图片路径	(自定义名代表64位字符串)

​		npm i url-loader@4.1.1 file-loader@6.2.0 -D

```js
module: {
    rules: [
      //定义了不同模块对应的loader
      { test: /\.css$/, use: ["style-loader", "css-loader"] },
      { test: /\.less$/, use: ["style-loader", "css-loader", "less-loader"] },
      {
        test: /\.jpg|png|gif$/,
        use: "url-loader?limit=22229&outputPath=images",
      },//只有图片大小<22229B才会转化为64base,打包后的存放路径为dist下的image文件夹中
    ],
  },
```

​	**配置loader加载Js高级语法（还没学先不用）**

---

### 7.3 项目打包发布

​	在webpack.config.js文件下的scripts模块下添加"build":"webpack --mode production"

​	webpack.config.js的所有配置:

```js
const path = require("path"); //导入修改打包路径的模块

const HtmlPlugin = require("html-webpack-plugin");

const htmlPlugin = new HtmlPlugin({
  template: "./src/index.html",
  filename: "./index.html",
});

const { CleanWebpackPlugin } = require("clean-webpack-plugin");

module.exports = {
  //development or production
  mode: "development",
	
  devtool: "eval-source-map",//配置SourceMap
  
  //打包入口出口配合第一个const使用
  entry: path.join(__dirname, "./src/index.js"), //修改src中.js文件名，否则不是index.js就会报错
  output: {
    path: path.join(__dirname, "./dist"), //打包后生成dist文件,可改名
    filename: "js/main.js", //改名生成.js文件
  },

  //plugin插件配合后面三个个const使用
  plugins: [htmlPlugin, new CleanWebpackPlugin()],

  //webpack-dev-server插件的配置
  devServer: {
    open: true,
    // port:80,如果端口号是80，直接localhost就可打开
    // host: "127.0.0.1",打开路径
  },

  //不同的loader
  module: {
    rules: [
      //定义了不同模块对应的loader
      { test: /\.css$/, use: ["style-loader", "css-loader"] },
      { test: /\.less$/, use: ["style-loader", "css-loader", "less-loader"] },
      {
        test: /\.jpg|png|gif$/,
        use: "url-loader?limit=22229&outputPath=images",
      },
    ],
  },
};

```

---

### 7.4 SourceMap

​	如果.js文件中有语法错误或其他错误，浏览器中会显示出错的文件与行号，但是行号是打包后.js文件的行号，不对应，因此需要配置SourceMap

​	webpack.config.js文件中配置

​			devtool: "eval-source-map",

注：配置后，有错修正后ctrl+s保存不会自动刷新，且项目打包发布时简易关闭devtool
