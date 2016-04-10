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
* 声明数组（）var person = Array[];
* 填充数组（populating） Array[index] = element;   <br>(下标:index)
* 合并 var person = Array[element...];
* 数组叠加、关联数组

  5.对象（object）
>属性（property）&方法（method）

  用户定义对象（user-defined-object）&   内建对象（native object）
  >内建对象：Array 、Date...



 >宿主对象：由浏览器提供（host object）

  var person = object();
object.property;
object.method()
假设创建一个person对象，首先需要创建一个person对象的实例（instance）,也就是对象的具体个体。（如同大圆里面画小圆）

  用对像来代替传统数组的做法,意味着可以通过对象属性名引用，而不再是单一的数字了。


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

 do{
 statements
}while(conditions) 至少执行一次

* for循环
  for(initial condition; test condition; alter condition){
  }

#####函数
* function name(arguments){
   statements
  }
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
```
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
```javascript
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

将新创建的节点插入文档中，最方便快捷就是让它成为现有节点的字节点
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






