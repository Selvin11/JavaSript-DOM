#JavaScript DOM (vesion2.0)

>some note 

# 一、历史

* JavaScript（Netscape Navigator）&VBScript(IE),伴随ECMA的标准化，实现一统。紧接着，浏览器在W3C的标准化下结束DOM战争.。

 在JS和DOM双双标准化之后，迎来了Web开发的高并发时代，各大浏览器也纷纷实现标准，以Webkit为引擎内核的有Safari&Chrome,以及以Webkit&Gecko为代表的开源引擎Firefox，剩下的就是以Trident为核心的IE浏览器。

#二、语法

* 语句（statement）;
* 注释（comment）//
* 变量（variable）var 函数内部也要var，否则会成为全局变量，污染全局

#####数据类型：
1.字符串（""）
2.数值（number）
3.布尔值（true&false）
4.数组（Array）

声明数组（）var person = Array[];

填充数组（populating） Array[index] = element;   <br>(下标:index)

合并 var person = Array[element...];

数组叠加、关联数组



5.对象（object）

>属性（property）&方法（method）

  用户定义对象（user-defined-object）&   内建对象（native object）
  >内建对象：Array 、Math、Date...



 >宿主对象：由浏览器提供（host object），Form、Image、Element还有document对象、window对象

var person = object();
object.property;
object.method()
假设创建一个person对象，首先需要创建一个person对象的实例（instance）,也就是对象的具体个体。（如同大圆里面画小圆）

  用对象来代替传统数组的做法,意味着可以通过对象属性名引用，而不再是单一的数字了。


#####操作：
算术操作符：＋ － * /
+:可以连接任意类型数据

比较操作符：> ,<, <= ,>= ,==,===

逻辑操作符：&&，｜｜，！＝

#####条件语句
* if 语句
  ​

  ```javascript
  if(condition){

   statements;

  }else{

   statements;

  }

  ```

* while循环语句
  ​

  ```javascript
  while(condition){

   statements

  }
  ```

  ```javascript
  do{

   statements

  }while(conditions) 至少执行一次
  ```

​       

* for循环
  ​

  ```javascript
  for(initial condition; test condition; alter condition){

  }

  ```

#####函数
* ```javascript
  function name(arguments){

   statements

  }

  ```

  ​
  可以传递任意参数！！！
  自建函数和JS内建函数（alert...）
  我们完全可以创建一个函数并让它返回（return）任意我们需要的，只需调用即可。

#####变量作用域(variable scope)
>局部(local variable)&全局(global variable)

#三、DOM
>Document Object Model

文档对象模型，以树的概念，讲文档结构具象化。
#####节点
>node

如同数据类型，也有节点类型
* 元素节点（element node）
  <body> <...> ...
* 文本节点（text node）
  行内文本...
* 属性节点 （attribute node）
  id class title...

>获取元素

1.document.getElementById(id)

2.document.getElementByTagName(tag)

3.document.getElementByClassName()
HTML5 DOM 
实现方式
```javascript
  getElementByClassName(node,classname){
    if(node.getElementByClassName!=null){
    return  node.getElementByClassName(classname);
}else{
  var results = new Array();
  var elems = node.getElementByTagName('*');
  for(var i = 0;i<elems.length;i++){
  if(elems[i].className.indexOf(classname) != -1){
  results[results] = elems[i];
  }
  }
  return results;
}
}
```
>获取和设置属性



> 当我们获取到元素之后，我们就可以对元素的属性进行操作了。
> getAttribute&setAttribute函数，不属于document对象，只能通过元素节点调用！所以应该<b>首先获取到元素！</b>
> object.getAttribute(attribute);
> object.setAttribute(attribute , value);
>

* DOM工作模式：现价在静态资源，再动态刷新，并且不影响文档的静态内容，当用setAttribute改变了文档中某个元素的属性时，当在浏览器中查看HTTML时，不会有变化，只会动态刷新页面内容！

#四、JavaScript图片库

> [可以参考](http://htmlpreview.github.io/?https://github.com/Selvin11/-website/blob/master/%E7%82%B9%E5%87%BB%E4%BA%A4%E4%BA%92/index.html)

案例思路

点击a标签显示对应图片，并且增加描述

* “占位符”概念：预留图片展示空间；
  拦截点击href的网页默认跳转行为；
  在点击链接的同时，更换“占位符”处的图片.

* 改变描述
  运用getAttribute&setAttribute,改变元素中的title值
  nodeValue属性，

定义函数➖绑定事件处理函数（将图片链接绑定到a标签链接，并将title赋值给指定“占位文本”）➖共享onload事件

>一些会用到的属性

* childNodes属性
  获取任何一个元素的所有子元素（element.childNodes）,这也是一个函数，需要先用get方法获取元素，再进行操作.
  firstChild&lastChild属性
  node.childNodes[0] = node.firstChild

* nodeType属性
>根据不同节点属性值不同，可以选择特定类型节点

 文档（document）中几乎每一样都是节点，就连空格和换行.
node.nodeType
nodeType的值是数字：
元素节点属性值为1；
属性节点属性值为2；
文本节点属性值为3.

* nodeValue属性
  node.nodeValue用来获取节点属性值和设置其属性值

* nodeName属性
  总是返回一个全大写字母的值
#五、最佳实践
描述了JavaScript&DOM遭到人们的乱用，胡乱的广告弹窗等，类比flash的遭遇，表明语言没有问题，只是使用的方式方法.
>谨慎使用，平稳退化，向CSS学习，行为与结构进行分离

BOM中的window对象
* window对象的open()方法
  window.open(url, name , features)
  分别为打开的链接地址，新窗口的名字，新窗口的各种属性（宽，高等）

>"javascript:"伪协议 如果浏览器禁用JS,会无作为

<b>什么是平稳退化？</b>
当人们选择禁用JS之后，还得让他们能够顺利访问你网站的主题内容！

<b>什么是渐进增强？</b>
<blockquote>"标记良好的内容就是一切"</blockquote>

<b>对JavaScript进行分离</b>

>将事件添加到HTML文档中的某个元素上

<b>向后兼容&性能考虑</b>
>不要彻底抛弃古老的浏览器版本，还有很大占比的人在使用，我朝从不缺人
>存在即合理，不存在请return false,一种方式，两手准备
>尽量减少访问DOM次数（将get方法封装函数，随时调用）
>合并压缩脚本，可以压缩很多K哦

#六、图片库改进版
* 详情继续看第四章，一揽子计划
  ​

  <b>源文件</b>
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title>Image Gallery</title>
  <script type="text/javascript" src="scripts/showPic.js"></script>
  <link rel="stylesheet" href="styles/layout.css" type="text/css" media="screen" />
</head>
<body>
  <h1>Snapshots</h1>
  <ul id="imagegallery">
    <li>
      <a href="images/fireworks.jpg" title="A fireworks display">
        <img src="images/thumbnail_fireworks.jpg" alt="Fireworks" />
      </a>
    </li>
    <li>
      <a href="images/coffee.jpg" title="A cup of black coffee" >
        <img src="images/thumbnail_coffee.jpg" alt="Coffee" />
      </a>
    </li>
    <li>
      <a href="images/rose.jpg" title="A red, red rose">
        <img src="images/thumbnail_rose.jpg" alt="Rose" />
      </a>
    </li>
    <li>
      <a href="images/bigben.jpg" title="The famous clock">
        <img src="images/thumbnail_bigben.jpg" alt="Big Ben" />
      </a>
    </li>
  </ul>
  <img id="placeholder" src="images/placeholder.gif" alt="my image gallery" />
  <p id="description">Choose an image.</p>
</body>
</html>

<script> 
function addLoadEvent(func) {
  var oldonload = window.onload;
  if (typeof window.onload != 'function') {
    window.onload = func;
  } else {
    window.onload = function() {
      oldonload();
      func();
    }
  }
}

function insertAfter(newElement,targetElement) {
  var parent = targetElement.parentNode;
  if (parent.lastChild == targetElement) {
    parent.appendChild(newElement);
  } else {
    parent.insertBefore(newElement,targetElement.nextSibling);
  }
}

function preparePlaceholder() {
  if (!document.createElement) return false;
  if (!document.createTextNode) return false;
  if (!document.getElementById) return false;
  if (!document.getElementById("imagegallery")) return false;
  var placeholder = document.createElement("img");
  placeholder.setAttribute("id","placeholder");
  placeholder.setAttribute("src","images/placeholder.gif");
  placeholder.setAttribute("alt","my image gallery");
  var description = document.createElement("p");
  description.setAttribute("id","description");
  var desctext = document.createTextNode("Choose an image");
  description.appendChild(desctext);
  var gallery = document.getElementById("imagegallery");
  insertAfter(placeholder,gallery);
  insertAfter(description,placeholder);
}

function prepareGallery() {
  if (!document.getElementsByTagName) return false;
  if (!document.getElementById) return false;
  if (!document.getElementById("imagegallery")) return false;
  var gallery = document.getElementById("imagegallery");
  var links = gallery.getElementsByTagName("a");
  for ( var i=0; i < links.length; i++) {
    links[i].onclick = function() {
      return showPic(this);
  }
    links[i].onkeypress = links[i].onclick;
  }
}

function showPic(whichpic) {
  if (!document.getElementById("placeholder")) return true;
  var source = whichpic.getAttribute("href");
  var placeholder = document.getElementById("placeholder");
  placeholder.setAttribute("src",source);
  if (!document.getElementById("description")) return false;
  if (whichpic.getAttribute("title")) {
    var text = whichpic.getAttribute("title");
  } else {
    var text = "";
  }
  var description = document.getElementById("description");
  if (description.firstChild.nodeType == 3) {
    description.firstChild.nodeValue = text;
  }
  return false;
}

addLoadEvent(preparePlaceholder);
addLoadEvent(prepareGallery);
</script>
```

>HTML－DOM & DOM Core

document.getElementByTagName('form')
可以简化为：
document.form

还有：element.getAttribute("src")
可以简化为：element.src

#七、动态创建标记
>document.write & innerHTML 渐退

DOM方法

```html
<div id="testdiv">

<p>This is <em>my</em> content.</p>

</div>

```


透彻理解DOM节点,div有<b>属性节点“id='testdiv'”</b>、元素节点p等等

* createElement方法
  document.createElement(nodeName)
  一般在创建新的元素节点之后，应该予以var进行变量赋值
  此后，变量成为一个孤立的对象，被称为文档碎片（document frament）

* appendChild方法
>在案例中发现同为兄弟节点的文本节点，是依照文本书写顺序来插入的
```javascript
window.onload = function() {
  var para = document.createElement("p");
  var txt1 = document.createTextNode("I inserted ");
  var emphasis = document.createElement("em");
  var txt2 = document.createTextNode("this");
  var txt3 = document.createTextNode(" content.");
  para.appendChild(txt1);
  emphasis.appendChild(txt2);
  para.appendChild(emphasis);
  para.appendChild(txt3);
  var testdiv = document.getElementById("testdiv");
  testdiv.appendChild(para);
}
```

输出结果：I inserted  *this* content.
修改后

```javascript
window.onload = function() {
  var para = document.createElement("p");
  var txt1 = document.createTextNode("I inserted ");
  var emphasis = document.createElement("em");
  var txt2 = document.createTextNode("this");
  var txt3 = document.createTextNode(" content.");
  para.appendChild(txt1);
  emphasis.appendChild(txt2);
  //修改顺序
  para.appendChild(txt3);
  para.appendChild(emphasis);
  var testdiv = document.getElementById("testdiv");
  testdiv.appendChild(para);
}
```
输出结果：I inserted content.*this*

**将新创建的节点插入文档中，最方便快捷就是让它成为现有节点的子节点**
parent.appendChild(child)
用get方法取到父节点，并声明变量，然后将新建子节点变量插入


* createTextNode方法
  以上成功之后，获得的只是一个内容为空的节点
  document.createTextNode(text)
>针对第四节的图片库案例，进行改进，删除掉我们的“占位符”，自己动手，创建新的空节点

首先创建img(id,src,alt)的各项属性，然后创建p(id)和一个文本节点，再将文本节点追加到p上，将p和img插入到文档中.

```javascript
var palceholder = document.createElement("img");
palceholder.setAttribute("id","palceholder");
palceholder.setAttribute("src","images/palceholder.gif");
palceholder.setAttribute("alt","my image gallery");
var description = document.createElement("p");
description.setAttribute("id","description");
var desctext = document.createTextNode("choose an image");

//使用appendChild方法
description.appendChild(desctext);
```

> 怎样将一个全新的节点插入文档中呢？前面的插入都是在原有的文档基础上进行插入的
>

- insertBefore方法
  1. 新元素：你想插入的新元素
  2. 目标元素：你想插入哪个元素之前
  3. 父元素：目标元素的父元素

​      parentElement.inserBefore ( newElement , targetElement )

首先有个知识点：我们都知道节点有元素节点、属性节点、文本节点，而且其属性值依次➖1；

> 在这个前提下，我们需要知道在DOM中，元素节点的父元素必须是元素节点，因为属性节点和文本节点的子元素是不允许有元素节点的

我们不必搞清楚who is parentElement , 因为targetElement的parentNode属性值就是这个parentElement;

这句话怎么理解呢？很简单，目标元素的父节点属性值就是父元素的属性值，这两个所指向的对象是一致的，不影响对应关系，我们要做的就是将新元素插入目标元素前面，同时设置目标元素的父元素，这里都满足.

但是我们的目标是插入在目标元素的后面呢！就会想到用insertBehind（）方法，但实质上DOM并没有提供

> 应该多在[mozila]https://developer.mozilla.org/zh-CN/ 了解更多的API，函数，方法都很齐全

- insertAfter方法

  ```javascript
  function insertAfter(newElement,targetElement) {
    var parent = targetElement.parentNode;
    if (parent.lastChild == targetElement) {
      parent.appendChild(newElement);
    } else {
      parent.insertBefore(newElement,targetElement.nextSibling);
    }
  }
  ```


- Ajax

  核心：XMLHttpRequest对象，浏览器和服务器的中间人。

# 八、充实文档内容

根据上一章节，我们学会了在文档中增加内容，但是这不是JS所主张的做法，要实现结构、表现和行为分离的话，这种行为应该是尽量避免面的。

这里的充实文档内容，主要是指标示、注释、解释等一些不是特别重要的内容，主要内容还是得在结构中写好！

html源文件：

```html
<body>
    <h1>What is the Document Object Model?</h1>
    <p>
The <abbr title="World Wide Web Consortium">W3C</abbr> defines
 the <abbr title="Document Object Model">DOM</abbr> as:
    </p>
    <blockquote cite="http://www.w3.org/DOM/">
      <p>
A platform- and language-neutral interface that will allow programs and scripts to dynamically access and update the
 content, structure and style of documents.
      </p>
    </blockquote>
    <p>
It is an <abbr title="Application Programming Interface">API</abbr>
 that can be used to navigate <abbr title="HyperText Markup Language">
HTML</abbr> and <abbr title="eXtensible Markup Language">XML
</abbr> documents.
    </p>
  </body>
```

> 做什么：1.根据缩略语，增加一个缩略语列表

```javascript
function displayAbbreviations() {
  if (!document.getElementsByTagName || !document.createElement || !document.createTextNode) return false;
// get all the abbreviations
  var abbreviations = document.getElementsByTagName("abbr");
  if (abbreviations.length < 1) return false;
  var defs = new Array();
// loop through the abbreviations
  for (var i=0; i<abbreviations.length; i++) {
    var current_abbr = abbreviations[i];
    if (current_abbr.childNodes.length < 1) continue;
    var definition = current_abbr.getAttribute("title");
    var key = current_abbr.lastChild.nodeValue;
    defs[key] = definition;
  }
// create the definition list
  var dlist = document.createElement("dl");
// loop through the definitions
  for (key in defs) {
    var definition = defs[key];
// create the definition title
    var dtitle = document.createElement("dt");
    var dtitle_text = document.createTextNode(key);
    dtitle.appendChild(dtitle_text);
// create the definition description
    var ddesc = document.createElement("dd");
    var ddesc_text = document.createTextNode(definition);
    ddesc.appendChild(ddesc_text);
// add them to the definition list
    dlist.appendChild(dtitle);
    dlist.appendChild(ddesc);
  }
  if (dlist.childNodes.length < 1) return false;
// create a headline
  var header = document.createElement("h2");
  var header_text = document.createTextNode("Abbreviations");
  header.appendChild(header_text);
// add the headline to the body
  document.body.appendChild(header);
// add the definition list to the body
  document.body.appendChild(dlist);
}
addLoadEvent(displayAbbreviations);
```

```javascript
//IE在统计abbr数量时，总会返回错误值0，因此这条语句直接让代码停止
if (current_abbr.childNodes.length < 1) continue;
//上面这条代码导致没有dl任何数据，因此会导致推出函数displayAbbreviations
if (dlist.childNodes.length < 1) return false;
```

> for ie6, abbr 标签在ie7之后才被支持



> 接下来：2.显示文献来源链接表

```javascript
function displayCitations() {
  if (!document.getElementsByTagName || !document.createElement || !document.createTextNode) return false;
// get all the blockquotes
  var quotes = document.getElementsByTagName("blockquote");
// loop through all the blockquotes
  for (var i=0; i<quotes.length; i++) {
// if there is no cite attribute, continue the loop
    if (!quotes[i].hasAttribute("cite")) continue;
// store the cite attribute
    var url = quotes[i].getAttribute("cite");
// get all the element nodes in the blockquote
    var quoteChildren = quotes[i].getElementsByTagName('*');
// if there are no element nodes, continue the loop
    if (quoteChildren.length < 1) continue;
// get the last element node in the blockquote
    var elem = quoteChildren[quoteChildren.length - 1];
// create the markup
    var link = document.createElement("a");
    var link_text = document.createTextNode("source");
    link.appendChild(link_text);
    link.setAttribute("href",url);
    var superscript = document.createElement("sup");
    superscript.appendChild(link);
// add the markup to the last element node in the blockquote
    elem.appendChild(superscript);
  }
}
addLoadEvent(displayCitations);
```

主要内容及目的：

1. 信息检索时，最有效的DOM方法有：getElementById、getElementByTagName、getAttribute
2. 将信息添加进文档时，最有效的DOM方法有：createElement、createTextNode、appendChild、insertBefore、setAttribute
3. 以上DOM方法的组合要深入理解并使用

# 九、CSS－DOM

> - 结构层（structural layer）
> - 表示层（presentation layer）
> - 行为层（behavior layer）

前言：文档中的每个元素节点都是一个对象，每个对象有各式各样的属性。位置属性：parentNode、nextSibling、previousSibling、childNodes、firstChlid、lastChild（这些属性都可以用来获取位置信息，但不能进行更新）等，还有nodeType、**nodeName(如“p”之类的字符串)**等等。

除此之外，文档中每个元素节点都有style属性。

> element.style.property**（eg: elment.style.color）**

**style属性是一个对象，使用typeof操作符可以得出结果。**

在外部样式表里声明的样式不会进入style对象，也就是不能被DOM检索出来。

意义：我们不是用DOM来破坏行为和样式分离，而是在某些情况下，通过CSS设定特殊元素（无法通过选择器简单操作）产生困难时，这时候通过DOM来进行样式设定，就变得非常简单了。（能够精确找到DOM上的任何一个节点，酷不酷👏）

> 有人说加个class或者id不久解决了，也是，具体问题具体分析嘛，两手准备，咱不愁。

- getNextElement函数

```javascript
function getNextElement(node) {
  if(node.nodeType == 1) {
  return node;
  }
  if (node.nextSibling) {
    return getNextElement(node.nextSibling);
  }
  return null;
}
```



- 表格的斑马线高亮实现方式（JS特别擅长处理重复性任务）

  先遍历table元素，然后遍历table中的每一数据行，并设置初始值为false；

  接着添加if循环，为true变背景色，为false不变并且将值变为true，因此，偶数行返回值就始终是true，就会变换背景色。

  （代码在执行中一定会返回值，一般是true、false、null等，要抓住根本来解决问题！）



- DOM处理鼠标事件相对CSS伪类，有更广泛及稳定的支持（适配绝大多数浏览器）

  ```javascript
  function highlightRows() {
    if(!document.getElementsByTagName) return false;
    var rows = document.getElementsByTagName("tr");
    for (var i=0; i<rows.length; i++) {
      rows[i].onmouseover = function() {
        this.style.fontWeight = "bold";
      }
      rows[i].onmouseout = function() {
        this.style.fontWeight = "normal";
      }
    }
  }
  ```



- 一直迷惑的className属性（可读写，凡是节点元素均有此属性）

  不知怎么回事，它总是突然出现，然后让我有些懵逼。（**主要是和nodeName弄混淆了，className会真的返回“p”标签中的class叫什么，而nodeName返回的就是“p”字符串！**）

  接下来讲讲另外一种思路，以上几个实例，无论图片库，还是充实文档内容，都让DOM和JS这种行为层干了CSS样式层的所有工作，不免放在现在看，有些不必要和累赘，更破坏了分离结构、样式、行为的初衷，虽然有些是DOM处理更简单些。

  **思路：将已经设定好的CSS样式，通过DOM和JS，直接绑定到你需要改变样式的任意节点上面，这样已经将JS中的style全部移除了。**

  ```javascript
  function styleHeaderSiblings() {
    if (!document.getElementsByTagName) return false;
    var headers = document.getElementsByTagName("h1");
    for (var i=0; i<headers.length; i++) {
      var elem = getNextElement(headers[i].nextSibling);
      addClass(elem,"intro");
    }
  }
  //直接更改className的value值，会导致直接替换掉，所以使用此函数
  function addClass(element,value) {
    if (!element.className) {
      element.className = value;
    } else {
      element.className+= " ";
      element.className+= value;
    }
  }
  function getNextElement(node) {
    if(node.nodeType == 1) {
    return node;
    }
    if (node.nextSibling) {
      return getNextElement(node.nextSibling);
    }
    return null;
  }
  ```


> 对函数进行抽象

将非常具体的东西改进为较为通用的东西的过程叫做*抽象*（真的好抽象呢🌝）

```javascript
function styleHeaderSiblings() {
  if (!document.getElementsByTagName) return false;
  var headers = document.getElementsByTagName("h1");
  for (var i=0; i<headers.length; i++) {
    var elem = getNextElement(headers[i].nextSibling);
    addClass(elem,"intro");
  }
}
//完美
function styleHeaderSiblings(tag,theclass) {
  if (!document.getElementsByTagName) return false;
  var headers = document.getElementsByTagName("tag");
  for (var i=0; i<headers.length; i++) {
    var elem = getNextElement(headers[i].nextSibling);
    addClass(elem,"theclass");
  }
}
```



# 十、用JavaScript实现动画效果

> 激动中：动画什么的最喜欢了

动画就是让元素的位置随着时间而不断地发生变化。what，are you kidding me~

- setTimeout函数（JS）

  setTimeout("function" , interval)

  绝大多数时候，会把这个函数赋值给一个变量。

- clearTimeout函数

  clearTimeout(variable)

  取消执行函数

- 运用style.top&style.left等位置属性确认元素当前位置

- parseInt函数（JS）

  parseInt(string)

  parseInt("39 steps")➤39

  可以将字符串里的数值信息提取出来,通常都是整数

  有小数点的数值使用parseFloat函数



# 十一、HTML5

- canvas、vedio、audio、form...