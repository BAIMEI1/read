.. _articles6668:

再谈javascript面向对象编程
==========================

2012年2月27日 `Neo <http://coolshell.cn/articles/author/neo>`__

**前言:**\ 虽有陈皓\ `《Javascript
面向对象编程》 <http://coolshell.cn/articles/6441.html>`__\ 珠玉在前，但是我还是忍不住再画蛇添足的补上一篇文章，主要是因为javascript这门语言魅力。另外这篇文章是一篇入门文章，我也是才开始学习Javascript，有一点心得，才想写一篇这样文章，文章中难免有错误的地方，还请各位不吝吐槽指正

**吐槽Javascript**
^^^^^^^^^^^^^^^^^^

| 初次接触Javascript，这门语言的确会让很多正规军感到诸多的不适，这种不适来自于Javascript的语法的简练和不严谨，这种不适也来自Javascript这个悲催的名称，我在想网景公司的Javascript设计者在给他起名称那天一定是脑壳进水了,让Javascript这么多年来受了这么多不白之冤，人们都认为他是Java的附属物，一个WEB玩具语言。因此才会有些人会对Javascript不屑，认为Javascript不是一门真正的语言，但是这此他们真的错了。Javascript不仅是一门语言，是一门真真正正的语言，而且他还是一门里程碑式的语言，他独创多种新的编程模式原型继承，闭包（\ **作者注：闭包不是JS首创，应该Scheme首创，prototypal
inheritance 和 dynamic objects
是self语言首创，Javascript的首创并不精彩,谢谢网友的指正。**\ ），对后来的动态语言产生了巨大的影响。做为当今最流行的语言（没有之一），看看git上提交的最多的语言类型就能明白。随着HTML5的登场，浏览器将在个人电脑上将大显身手，完全有替换OS的趋势的时候，Javascript做为浏览器上的一门唯一真真的语言，如同C之于
unix/linux，java之于JVM，Cobol之于MainFrame，我们也需要来重新的认真地认识和审视这门语言。另外Javascript的正式名称是：ECMAScript，这个名字明显比Javascript帅太多了！
| 
言归正传，我们切入主题——Javascript的面向对象编程。要谈Javascript的面向对象编程，我们第一步要做的事情就是忘记我们所学的面向对象编程。传统C++或Java的面向对象思维来学习Javascript的面向对象会给你带来不少困惑，让我们先忘记我们所学的，从新开始学习这门特殊的面向对象编程。既然是OO编程，要如何来理解OO编程呢，记得以前学C++，学了很久都不入门，后来有幸读了《Inside
The C++ Object
Model》这本大作，顿时豁然开朗，因此本文也将以对象模型的方式来探讨的Javascript的OO编程。因为Javascript
对象模型的特殊性，所以使得Javascript的继承和传统的继承非常不一样，同时也因为Javascript里面没有类，这意味着Javascript里面没有extends,implements。那么Javascript到底是如何来实现OO编程的呢？好吧，让我们开始吧，一起在Javascript的OO世界里来一次漫游

首先，我们需要先看看Javascript如何定义一个对象。下面是我们的一个对象定义：

::

    var o = {};

还可以这样定义一个对象

::

    function f() {
    }

| 对，你们没有看错，在Javascript里面，函数也是对象。
|  当然还可以

::

    var array1= [ 1,2,3];

| 数组也是一个对象。
|  其他关于对象的基本的概念的描述，还是请各位亲们参见陈皓\ `《Javascript
面向对象编程》 <http://coolshell.cn/articles/6441.html>`__\ 文章。
| 
对象都有了，唯一没有的就是class，因为在Javascript里面是没有class关键字的，算好还有function，function的存在让我们可以变通的定义类，在扩展这个主题前，我们还需要了解一个Javascript对象最重要的属性，\ **\_\_proto\_\_**\ 成员。

**\_\_proto\_\_成员**
^^^^^^^^^^^^^^^^^^^^^

| 严格的说这个成员不应该叫这个名字，\_\_proto\_\_是Firefox中的称呼，\_\_proto\_\_只有在Firefox浏览器中才能被访问到。\ **做为一个对象，当你访问其中的一个成员或方法的时候，如果这个对象中没有这个方法或成员，那么Javascript引擎将会访问这个对象的\_\_proto\_\_成员所指向的另外的一个对象，并在那个对象中查找指定的方法或成员，如果不能找到，那就会继续通过那个对象的\_\_proto\_\_成员指向的对象进行递归查找，直到这个链表结束**\ 。
好了，让我们举一个例子。
| 
比如上上面定义的数组对象array1。当我们创建出array1这个对象的时候，array1实际在Javascript引擎中的对象模型如下：
| |image0|
| 
array1对象具有一个length属性值为3，但是我们可以通过如下的方法来为array1增加元素：

::

    array1.push(4);

push这个方法来自于array1的\_\_proto\_\_成员指向对象的一个方法(Array.prototye.push())。正是因为所有的数组对象（通过[]来创建的）都包含有一个指向同一个具有push,reverse等方法对象(Array.prototype)的\_\_proto\_\_成员，才使得这些数组对象可以使用push,reverse等方法。

那么这个\_\_proto\_\_这个属性就相当于面向对象中的”has
a”关系，这样的的话，只要我们有一个模板对象比如Array.prototype这个对象，然后把其他的对象\_\_proto\_\_属性指向这个对象的话就完成了一种继承的模式。不错！我们完全可以这么干。但是别高兴的太早，这个属性只在FireFox中有效，其他的浏览器虽然也有属性，但是不能通过\_\_proto\_\_来访问，只能通过getPrototypeOf方法进行访问，而且这个属性是只读的。看来我们要在Javascript实现继承并不是很容易的事情啊。

**函数对象prototype成员**
^^^^^^^^^^^^^^^^^^^^^^^^^

首先我们先来看一段函数prototype成员的定义，

    | **When a function object is created, it is given a prototype
    member which is an object containing a constructor member which is a
    reference to the function object**
    | 
    当一个函数对象被创建时，这个函数对象就具有一个prototype成员，这个成员是一个对象，这个对象包含了一个构造子成员，这个构造子成员会指向这个函数对象。

例如：

::

    function Base() {
        this.id = "base"
    }

Base这个函数对象就具有一个prototype成员，关于构造子其实Base函数对象自身，为什么我们将这类函数称为构造子呢？原因是因为这类函数设计来和new
操作符一起使用的。为了和一般的函数对象有所区别，这类函数的首字母一般都大写。构造子的主要作用就是来创建一类相似的对象。

| 上面这段代码在Javascript引擎的对象模型是这样的
| |image1|

**new 操作符**
^^^^^^^^^^^^^^

| 在有上面的基础概念的介绍之后，在加上new操作符，我们就能完成传统面向对象的class
+ new的方式创建对象，在Javascript中，我们将这类方式成为Pseudoclassical。
|  基于上面的例子，我们执行如下代码

::

    var obj = new Base();

| 这样代码的结果是什么，我们在Javascript引擎中看到的对象模型是：
| |image2|

new操作符具体干了什么呢?其实很简单，就干了三件事情。

::

    var obj  = {};
    obj.__proto__ = Base.prototype;
    Base.call(obj);

| 第一行，我们创建了一个空对象obj
| 
第二行，我们将这个空对象的\_\_proto\_\_成员指向了Base函数对象prototype成员对象
| 
第三行，我们将Base函数对象的this指针替换成obj，然后再调用Base函数，于是我们就给obj对象赋值了一个id成员变量，这个成员变量的值是”base”，关于call函数的用法，请参看陈皓\ `《Javascript
面向对象编程》 <http://coolshell.cn/articles/6441.html>`__\ 文章
|  如果我们给Base.prototype的对象添加一些函数会有什么效果呢？
|  例如代码如下：

::

    Base.prototype.toString = function() {
        return this.id;
    }

| 那么当我们使用new创建一个新对象的时候，根据\_\_proto\_\_的特性，toString这个方法也可以做新对象的方法被访问到。于是我们看到了：
| **构造子中，我们来设置‘类’的成员变量（例如：例子中的id），构造子对象prototype中我们来设置‘类’的公共方法。于是通过函数对象和Javascript特有的\_\_proto\_\_与prototype成员及new操作符，模拟出类和类实例化的效果。**

**Pseudoclassical 继承**
^^^^^^^^^^^^^^^^^^^^^^^^

我们模拟类，那么继承又该怎么做呢？其实很简单，我们只要将构造子的prototype指向父类即可。例如我们设计一个Derive
类。如下

::

    function Derive(id) {
        this.id = id;
    }
    Derive.prototype = new Base();
    Derive.prototype.test = function(id){
    Derive.prototype.test = function(id){
        return this.id === id;
    }
    var newObj = new Derive("derive");

| 这段代码执行后的对象模型又是怎么样的呢？根据之前的推导，应该是如下的对象模型
| |image3|
| 
这样我们的newObj也继承了基类Base的toString方法，并且具有自身的成员id。关于这个对象模型是如何被推导出来的就留给各位同学了，参照前面的描述，推导这个对象模型应该不难。
| 
Pseudoclassical继承会让学过C++/Java的同学略微的感受到一点舒服，特别是new关键字，看到都特亲切，不过两者虽然相似，但是机理完全不同。当然不关什么样继承都是不能离不开\_\_proto\_\_成员的。

**Prototypal继承**
^^^^^^^^^^^^^^^^^^

这是Javascript的另外一种继承方式，这个继承也就是之前陈皓文章《Javascript
面向对象编程》中create函数，非常可惜的是这个是ECMAScript
V5的标准，支持V5的浏览器目前看来也就是IE9，Chrome最新版本和Firefox。虽然看着多，但是做为IE6的重灾区的中国，我建议各位还是避免使用create函数。好在没有create函数之前，Javascript的使用者已经设计出了等同于这个函数的。例如：我们看看Douglas
Crockford的object函数。

::

    function object(old) {
       function F() {};
       F.prototype = old;
       return new F();
    }
    var newObj = object(oldObject);

例如如下代码段

::

    var base ={
      id:"base",
      toString:function(){
              return this.id;
      }
    };
    var derive = object(base);

| 上面函数的执行后的对象模型是：
| |image4|
如何形成这样的对象模型，原理也很简单，只要把object这个函数扩展一下，就能画出这个模型，怎么画留给读者自己去画吧。
| 
这样的继承方式被称为原型继承。相对来说要比Pseudoclassical继承来的简单方便。ECMAScript
V5正是因为这原因也才增加create函数，让开发者可以快速的实现原型继承。
| 
上述两种继承方式是Javascript中最常用的继承方式。通过本文的讲解，你应该对Javascript的OO编程有了一些‘原理’级的了解了吧

**参考:**
^^^^^^^^^

| `《Prototypes and Inheritance in JavaScript Prototypes and Inheritance
in
JavaScript》 <http://msdn.microsoft.com/en-us/scriptjunkie/ff852808>`__
| `Advance
Javascript <http://yuiblog.com/blog/2006/11/27/video-crockford-advjs/>`__
（Douglas Crockford 大神的视频，一定要看啊）

**题外话：**
^^^^^^^^^^^^

web2.0后，web应用可谓飞速发展，如今在HTML5发布之际，浏览器的功能被大大强化，我感觉Browser远远在不是一个Browser那么简单了。记得C++之父曾经这样说过JAVA，JAVA不是跨平台，JAVA本身就是一个平台。如今的Browser也本身就是一个平台了，好在这个平台是基于标准的。如果Browser是平台，由于Browser安全沙箱的限制，个人电脑的资源被使用的很少，感觉Browser就是一个NC（Network
Computer）？我们居然又回到了Sun最初提出的构想，Sun是不是太强大了些？

.. |image0| image:: /coolshell/static/20140922103118931000.png
.. |image1| image:: /coolshell/static/20140922103119007000.png
.. |image2| image:: /coolshell/static/20140922103119071000.png
.. |image3| image:: /coolshell/static/20140922103119133000.png
.. |image4| image:: /coolshell/static/20140922103119199000.png
.. |image11| image:: /coolshell/static/20140922103119247000.jpg

.. note::
    原文地址: http://coolshell.cn/articles/6668.html 
    作者: 陈皓 

    编辑: 木书架 http://www.me115.com