.. _articles1761:

Go语言源码的一个改动
====================

2009年11月12日 `陈皓 <http://coolshell.cn/articles/author/haoel>`__

2009年11月11日，光棍节，\ `Google发布了Go语言 <http://coolshell.cn/articles/1751.html>`__\ ，马上，就有网友在\ `http://code.google.com/p/go/ <http://code.google.com/p/go/>`__\ 上找到了一个Go语言包文件操作源码/src/pkg/os/file.go文件的一个最新改动。这个改动的作者就是那个大名鼎鼎的Unix之父\ `Ken
Thompson <http://en.wikiquote.org/wiki/Kenneth_Thompson>`__\ （看看人家，都这么老了，还在写程序，佩服佩服，真是顶级程序员啊——《\ `程序员的八个级别 <http://coolshell.cn/articles/343.html>`__\ 》），而这个改动的\ `Log
Message <http://code.google.com/p/go/source/detail?r=4a3f6bbb5f0c6021279ccb3c23558b3c480d995f>`__\ 如下所示（把屏抓下来，以免以后某日被放到墙外或是google.com数据丢失或是Google公司倒闭）

| Spell it with an “e”
| |spell it with an e|

 

这是一个很著名的典故，要知道这个典故，你需要知道两件事，一个是Ken
Thompson的经典语录，一个是Unix的系统调用。

关于Ken Thompson的经典语录，你可以在wikipdia上的\ `Ken
Thompson <http://en.wikiquote.org/wiki/Kenneth_Thompson>`__\ 词条中找到，这个事情是这样的。

    Ken Thompson was once asked what he would do differently if he were
    redesigning the UNIX system. His reply: “\ **I’d spell creat with an
    e.**\ ” （Ken
    Thompson有一次在被问到——如果他可以重新设计Unix系统，他会做些什么不同的事？而他回答到：“我会把“creat”多拼一个e”）

“I’d spell creat with an
e”，也就是说，他会把creat这个单词拼成\ **creat**\ **e**\ ，而不是creat。为什么是creat呢，这需要我们来看一下creat这个系统调用，你可以在Unix或Linux下简单地\ `man
creat <http://linux.die.net/man/2/creat>`__\ 你就可以知道，这个系统调用连带其某些参数，如：\ **O\_CREAT**\ ，都是一个少了“e”的create。（Unix下的有很多东西都是简写，如：usr，gp，ls，mv，ps，满大街的都是缩写）

看看这个改动的\ `diff <http://code.google.com/p/go/source/diff?spec=svn1f0a01c93d305f1ab636c68b67346659c5b957f7&r=4a3f6bbb5f0c6021279ccb3c23558b3c480d995f&format=side&path=/src/pkg/os/file.go&old_path=/src/pkg/os/file.go&old=50a1ee94151635c25ad76816044252af417a45b8>`__——这个diff只有一行，第65行，抓屏如下（理由同上）

|spell it with e diff|

40年后的今天，Ken
Thompson参与Go语言设计，于是，他提交了这个改动，也算是圆了他的愿望，从这点看来，Ken
Thompson把Go语言看得和Unix一样重啊。难道Go语言也会像Unix一样成为另一个传奇？（Unix传奇 \ `上篇 <http://blog.csdn.net/haoel/archive/2007/03/27/1542340.aspx>`__\ ，\ `下篇 <http://blog.csdn.net/haoel/archive/2007/03/27/1542353.aspx>`__\ ）

（全文完）

.. |spell it with an e| image:: /coolshell/static/20140921000229638000.jpg
.. |spell it with e diff| image:: /coolshell/static/20140921000229688000.jpg
.. |image8| image:: /coolshell/static/20140921000229748000.jpg

.. note::
    原文地址: http://coolshell.cn/articles/1761.html 
    作者: 陈皓 

    编辑: 木书架 http://www.me115.com