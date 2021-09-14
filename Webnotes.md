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

| 常用API                    | 作用                                                         |
| -------------------------- | ------------------------------------------------------------ |
| Array.isArray(obj)         | 判断是否是数组                                               |
| Array.push()               | 后插                                                         |
| Array.unshift()            | 头插                                                         |
| Array.pop()                | 尾删                                                         |
| Array.shift()              | 头删                                                         |
| Array.reverse()            | 翻转                                                         |
| Array.sort()               | 默认按照ASIC排序，Array.sort(function(a,b){<br />      return a-b;<br />})；升序 |
| Array.indexOf(value)       | 返回value下标，找不到返回0                                   |
| Array.toString()           | 数组转换为字符串，保留逗号                                   |
| Array.join(’分隔符‘)       | 数组转换为字符串，传参符分割                                 |
| Array.splice(index,length) | 从index开始删length个                                        |

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

