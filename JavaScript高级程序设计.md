# JavaScript高级程序设计——

## 一、JavaScript简介

简单的输入验证器➖一门强大的编程语言

Netscape的JavaScript(LiveScipt)，微软的Jscipt，通过ECMA（欧洲计算机制造商协会的标准）形成了最终的JavaScript。

- JavaScript的核心组成部分

  核心ECMAScript

  > ECMAScript只是基础的脚本语言，需要依靠宿主环境及其提供的语言扩展，才能实现，以及让语言和环境进行对接交互。

  文档对象模型（DOM）

  > DOM是针对XML单经过扩展用于HTML的API，将页面映射为树形图
  >
  > DOM不只是针对JavaScript的， 很多语言也都实现了DOM

  浏览器对象模型（BOM）

  > 没有标准，每个浏览器都有自己的实现，如window、navigator等

## 二、在HTML中使用JavaScript

在页面中嵌入，或者在外部引用

> 如果引用文件放在head部分，则必须在JS文件加载完成之后，才会呈现body中的内容，会导致浏览器呈现页面出现延迟。

XHTML（Extensible HyperText Markup Language），可扩展超文本标记语言

**将页面的MIME类型制定为“application/xhtml+html”才会触发XHTML模式**

```javascript
<script> <![CDATA[
function compare(a,b){
  if(a<b){
  alert("A is less than B");
}else if(a>b){
  alert("A is greater than B");
}else{
  alert("A is equal to B");
}
}
]]></script>
//兼容XHTML的浏览器，不兼容的需要讲CData标记注释掉
```

- 文档模式

  通过使用**文档类型**（doctype）切换实现的。

  > 混杂模式（quirks mode）
  >
  > 标准模式（standards mode）



## 三、JavaScript基本概念

任何语言的核心都是其最基本的工作原理，而描述的内容通常都要涉及这门语言的**语法**、**操作符**、**数据类型**、**内置功能**等。

- ## 语法

  1. 区分大小写；

  2. 标识符：指变量、函数、属性的名字或者函数的参数

     第一个字符必须是一个字母或_或$ ，其它字符可是是这些和数字

     一般采用驼峰格式；

  3. 注释：//

  4. 严格模式：ECMAScript5引入严格模式（strict mode）概念

     “use strict”;

  5. 语句：

- 关键字和保留字

  使用关键字会导致“Identifier Expected”错误❌

- 变量

  ECMAScript的变量属于松散类型的，可以保存任何类型的数据

  定义变量需要用var操作符

  如果在函数中使用var定义变量，这个变量将在函数推出后被销毁（局部变量）

  如果在函数中未使用var定义变量，这个变量将变成全局变量，但不推荐，不以维护

- 数据类型

  1. typeof操作符（**检测数据类型**）

             返回信息为:"undefined"、"boolean"、"string"、"number"、"object"、"function"
             
             以上就是所有的数据类型

  2. Undefined类型

     **只有一个值就是undefined**，使用var声明变量但未赋值时，该变量的值就是undefined

  3. Null类型

     **只有一个值就是null**，null值表示一个空对象指针，用typeof检测返回的值为"object"

  4. Boolean类型

     true或者false

  5. Number类型

     八进制：第一位为0，然后是八进制数字序列（0～7）070=56

     十六进制：前两位为0x，然收是（0～9和A～F），可小可大写

     数值范围：［5e－324，1.7976931348623157e＋308］

     －Infinity负无穷 , Infinity正无穷，使用isFinite（）函数确定数值是否有穷

     NaN类型

     NaN与任何值都不相等，包括自己

     ECMAScript定义函数isNaN（），会尝试将括号中的数据类型转换为数值，能够转换的返回false，不能转换的返回true

     **数值转换**

     有三个函数可以把非数值转换为数值：

     - Number（）

       用于任何数据类型：

       > Boolean：true返回1，false返回0；
       >
       > Number：简单的传入返回；
       >
       > Null：返回0；
       >
       > Undefined：返回NaN；
       >
       > String：只包含数字的，回忽略前导的0，浮点或其他进制都会返回十进制数值；字符串是空的，会返回0；以上都不是的字符串，返回NaN
       >
       > Object：调用对象的valueOf（）方法，然后依照前面的规则返回值，如果是NaN，则调用对象的toString（）方法，然后按照前面的规则返回字符串值

     - parseInt（）

       经常用于处理整数，直至找到第一个非空格字符，如果第一个字符不是数字字符或者负号，则返回NaN，也就是说从解析到第一个数字字符开始，依次向下解析数字字符，直到遇到一个非数字字符，因此字符串中的非数字字符都会被忽略。

       在ECMAScript5中，对于八进制解析存在问题，需要添加基数

       ```javascript
       var num = parseInt("0xAF", 16);
       ```

     - parseFloat（）

       以第一个小数点为有效，并停止解析，**只解析十进制数值**

  6. String类型

     用于表示由0或多个16位Unicode 字符组成的字符串

     - 字符字面量

       \

     - 字符串的特点

       不可变，重新赋值后，导致之前的直接销毁

     - 转换为字符串

       **a、toString（）方法，数据类型中（除undefined、null）都有此方法**

       **一般不传参数，对于数值可以传递基数，用于解析进制转换**

       **b、String（）方法，用于不知道要转换的值是否为undefined或者null**

  7. object类型

     ECMAScript中的对象其实就是一组数据和功能的集合


- ## 操作符

  1. 一元操作符：只能操作一个值的操作符

             ＋＋  、 —— 、 ＋ 、 －

  2. 位操作符

     最低层的数据存储，按内存中表示数值的位来操作数值，但不是直接操作64位的值，而是先转换为32位的整数，然后进行操作，最后再将结果转换回64位。

     数字以二进制码存储，负数使用二进制补码，将绝对值进行二进制反码，0变1，1变0，最后加1就得到了

     > 按位非：～，即返回数值的反码
     >
     > 按位与：&，对应位均为1，则为1，其余均为0
     >
     > 按位或：｜，除去对应为均为0的，其它均为1
     >
     > 按位异：^，对应位均为1或0，则为1，其余为0
     >
     > 左移：<<，左移数字并以0填充空位
     >
     > 有符号的右移：>>，右移并以0填充空位
     >
     > 无符号的右移：>>>，正数与有符号的右移相同，负数，进行无符号右移，结果会非常之大

  3. 布尔操作符

     true  ，  false

     > 逻辑非：！
     >
     > 逻辑与：&
     >
     > 逻辑或：｜

  4. 乘性操作符

     ＊，％，／

  5. 加性操作符

     > **两个操作数均为字符串时，进行拼接**
     >
     > **只有一个是字符串，将另一个转换为字符串进行拼接**

  6. 关系操作符

     <  ，>， <=，>=

  7. 相等操作符

  8. 条件操作符

     var max = (num1 > num2) ? num1  : num2 ;

     num1>num2为true，则max = num1 , 否则max ＝ num2

  9. 赋值操作符

  10. 逗号操作符

- ## 语句(流控制语句)

  1. if语句

  2. do－while语句

  3. while语句

  4. for 语句

  5. for－in语句

     > 精准的迭代语句，用于枚举对象的属性

  6. label语句

  7. break和continue语句

  8. with语句

  9. switch语句

- ## 函数

  ```javascript
  function functionName(arg0,arg1...){
       statements
  }

  ```

  可以通过return语句来实现返回值，如果return后面不带任何返回值，则返回undefined

  1. 理解参数

             参数个数与类型无要求，在内部是以数组来表示的
             
             可以通过arguments对象来访问这个参数数组

     ```javascript
             function sayHi(name,message){
               alert("Hello"+name+","+message);
             }
             //两个函数的功能是一样的
             function sayHi(){
                alert("Hello"+arguments[0]+","+arguments[1]);
             }
             arguments对象和参数之间有一一对应的关系，不仅参数可以不必须，而且两者间可以一起使用（arguments.length属性）
     ```

  2.没有重载

   在ECMAScript中，函数名相同的函数，会被后面的函数覆盖掉，前面的函数直接没有意义

  ​

## 四、变量、作用域和内存问题

- 变量可能包含两种不同数据类型的值：**基本类型值**和**引用类型值**

基本类型值：5中基本数据类型（undefined、null、number、string、boolean）

引用类型值：保存在内存中的对象，与其他语言不通，javascript不允许直接访问内存中的位置，在操作对象时，实际上是**操作对象的引用**而不是实际的对象

1. 动态的属性

可以给对象添加属性，只要对象不被销毁或者属性不被删除，将会一直存在

但不能给基本类型的值添加属性，这样会返回undefined

2.复制变量值

基本类型值复制：两个值相互独立，不影响

引用类型值复制：复制后的两个值实际上引用同一个对象

3.传递参数

ECMAScript的所有函数的参数都是**按值传递的**

跟复制变量值类比，区别是一样的

4.检测类型

> 基本类型值用typeof操作符
>
> 引用类型用instanceof操作符



- 执行环境及作用域

   执行环境：全局环境、局部环境

  作用域链：当代码在一个环境中执行时，会创建变量对象的一个作用域链。

  作用域链的用途是保证对执行环境有权访问的所有变量和函数的有序访问。

- JavaScript没有块级作用域

  if语句中定义的变量，会被添加到当前的执行环境中，这里的执行环境为全局环境，所以能够访问到color变量（if语句不是函数哦）

  在函数中使用var进行变量声明，将只会存在于函数的局部环境中，在外部的环境中将不会被访问到

  ```javascript
  if(true){
    var color = "blue";
  }
  alert(color);   //"blue"
  ```


- 查询标识符

  alert（function();   从前端（当前执行环境开始搜索函数的变量对象），如果有，则不会去父级环境搜索，直接停止（也就是不会沿作用域链向上搜索了）

- 垃圾收集

  局部变量只在函数执行的过程中存在。



## 五、引用类型

**引用类型的值（对象）是引用类型的一个实例。**

新对象是new＋构造函数创建的（var person = new object()），object()为构造函数，创建了object引用类型的一个新实例。

1. object类型

         目前，大多是引用类型值都是object类型的实例，创建方式为：
         
         > 方式一（如上）：var person = new ＋ object（）
         >
         > 方式二（对象字面量表示法）：var person = {}

2. Array类型

   ECMAScript数组和其他语言的数组一样都是有序列表，但是它每一项都可以保存任意类型的数据

   创建方式：

   > var colors = new Array()  ||  var colors = Array()
   >
   > 数组字面量表示法：var colors = Array[ ]

   数组下标从0～ele.length-1

   - 检测数组

     对于全局作用域而言，使用instanceof操作符：

     ECMAScript5:新增Array.isArray()方法，不用考虑执行环境了

   - 转换方法

     toString（）方法，会让数组中的数据以字符串和逗号进行拼接

     valueOf（）方法，返回的还是数组

   - 栈方法

     栈是一种LIFO(Last-In-First_Out)的数据结构，只发生在栈的顶部位置

     ECMAScript提供了push（），接受参数添加到数组末尾和pop（）方法，从数组末尾移除最后一项并返回该项

   - 队列方法

     队列数据结构的访问规则是FIFO（First-In-First-Out），shift（）方法，移除数组中第一项并返回该项，以及上面的push（）方法

   - 重排序方法

     reverse（）方法，反转数组项的顺序

     sort（）方法，按升序排列数组项，最小值在最前面

   - 操作方法

     concat（）方法，创建数组副本，不影响原数组

     slice（）方法，通过参数，选择原数组中的项，不影响原数组

     **splice（）方法，向数组的中部插入项，强大的功能**

     > splice（0，2），删除前两项
     >
     > splice（2，0，“red”）从第二项插入“red”
     >
     > splice（2，1，“red”，“blue”）删除第二项，并插入这两个参数
     >
     > splice（）方法始终会返回一个数组，包含的是删除项

   - 位置方法

     ECMAScript5为数组添加了indexOf（）和lastIndexOf（）方法

     两个方法都接受两个参数，要查找的项和查找位置的索引（可选参数）

     > indexOf（）方法从数组的开头开始向后查找
     >
     > lastIndexOf（）方法从数组末尾开始向前查找

   - 迭代方法（类比for 循环遍历，也可以叫循环迭代）

     ```javascript
     ele.method（function（item，index，array））｛
          statements
     ｝
     ```

     > every（）方法，所有项满足条件都为true，返回true
     >
     > filter（）方法，返回满足条件为 true的数组
     >
     > forEach（）方法，无返回值
     >
     > map（）方法，返回执行条件后一一对应的数组
     >
     > some（）方法，任意一项满足条件为true，均返回true

   - 归并方法

     reduce（）方法和reduceRright（）方法，迭代所有项然后构建一个返回值

     > reduce（）方法，从数组第一项开始，向后遍历
     >
     > reduceRright（）方法，从数组最后一项开始，向前遍历

3. Date类型

   创建日期对象：

   var now＝ new Date（）

   Date.parse（）方法接收表示日期的字符串

   ECMAScript5新增Date.now（） 方法，获取当前时间

4. RegExp类型

   ECMAScript通过RegExp类型来支持正则表达式（**匹配符合条件的字符串**，**捕获匹配项**）

   var expression = / pattern / flags

   模式（parttern）部分是任何正则表达式，每个正则表达式可以带一或多个标志（falgs），用以表明正则表达式的行为，犹如下三个标志

   > g：表示全局（global），应用于所有字符串，发现匹配项立即停止
   >
   > i：表示不区分大小写（case－insensitive）
   >
   > m：表示多行（multiline）

   正则表达式字面量&使用RegExp构造函数创建的正则表达式

   > 正则表达式字面量：只是创建了一个RegExp实例，无法重复调用
   >
   > 构造函数正则表达式：每次迭代都会创建RegExp新实例，可以重复调用

   - RegExp实例属性

     > global：是否设置g标志
     >
     > ignoreCase：是否设置i标志
     >
     > lastIndex：整数，从0开始搜索下一个匹配项的字符位置
     >
     > multiline：是否设置了m标志
     >
     > source：正则表达式的字符串表示

   - RegExp实例方法：exec（）返回一个匹配项信息的数组

5. Function类型

   函数实际上是对象，每个函数都是Function类型的实例。

   由于函数是对象，函数名实际上是一个指向函数对象的指针。

   （指针，一个实例指向对象的箭头，有多个但互不影响，没有交叉点）

   - 没有重载，指针被重新声明，就被替换了，就无法同时响应了

   - 函数声明与函数表达式

     解析器会率先读取函数声明，并使其在执行任何代码之前可以访问

     （因为有函数声明提升这么个东东）

     > 函数声明：function sum（）｛｝
     >
     > 函数表达式：var sum = function（）｛｝

   - 作为值的函数

     函数名本身就是变量，所以也可以作为值来使用，可以将函数像参数一样传递

   - 函数内部属性

     函数内部，有两个特殊对象：this和arguments（有callee属性）

     该属性可以消除函数体内的代码和函数名耦合现象，使用arguments.callee（arg－1）替代functionName

     > this引用的是函数当前执行的环境对象

   - 函数属性和方法

     每个函数都包含length（接收参数个数）和prototype（实例原型）两个属性

     每个函数都包含非继承的方法：apply（）和call（），主要是设置函数体内this对象的值，扩充函数的作用域

6. 基本包装类型

   事实上，每当读取一个基本类型值，后台就会创建一个对应的基本包装类型对象（）

7. 单体内置对象

   内置对象：**由ECMAScript实现提供的、不依赖宿主环境的对象，这些对象在ECMAScript程序执行之前就存在了。**

   - Global对象

     全局对象，**不属于任何其他对象的属性和方法，都是Global对象的属性和方法；所有在全局作用域定义的属性和函数，都是Global对象的属性。**

     1. URI编码方法

          encodeURI（）方法：只转换空格

          encodeURIComponent（）方法：转换所有非数字字母字符

          解码方法：

          decodeURI（）方法：只解码空格

          decodeURIComponent（）方法：解码所有

     2. **eval（）方法**

        就像是一个完整的ECMAScript解析器

     3. Global对象的属性

        所有的类型属性

     4. window对象

        Web浏览器将Global全局对象作为Window对象的一部分加以实现

        因此全局作用域中声明的所有变量和函数，就都成为了window对象的属性

   - Math对象

     min（）和max（）方法

     random（）方法：返回>=0和<1的随机数

     ​


## 六、面向对象的程序设计

ECMA-262把对象定义为：无序属性的集合，其属性可以包含基本值、对象或者函数。

将**ECMAscript想象成散列表，无非都是一组名值对，其中值为数据或函数！**

1. 理解对象

   - 属性类型

     数据属性：

     访问器属性：

2. 创建对象

   工厂模式：用函数封装以特定借口创建对象的细节（可以创建多个相似对象，但无法对其进行识别）

   **构造函数模式**：没有显示地创建对象，直接将属性和方法赋给了this对象

   新实例（对象指针，必须使用new）都有construtor（构造函数）属性

   **原型模式**：我们创建的每一个函数都有prototype（原型）属性，这个属性是一个指针，指向一个对象（原型对象），可以调用所有实例的属性和方法。

   储存在原型对象中的属性和方法会一直存在，在外部新建实例，只是导致搜索首先发现新实例的属性，而不再继续向原型搜索，但是原型中的属性一直都存在，不会被改变。

   > in操作符（检测属性 in 检测对象）：只要对象能够访问到相关属性，就返回true
   >
   > instanceof操作符（检测对象 instanceof 构造函数对象 ）

   构造函数模式＋原型模式：使用最广泛的创建自定义类型的方法

3. 继承

   ECMAScript只支持实现继承，依靠原型链实现。

   - 原型链：利用原型让一个引用类型继承另一个引用类型的属性和方法

   ​

   ​

   ​

   ​



