.. _articles1432:

编译vim解决中文支持
===================

2009年9月19日
`free.wang <http://coolshell.cn/articles/author/free-wang>`__

最近开始抛弃Ubuntu折腾CentOS
5.3(注：无意挑起OS之争)，每当换一个OS，第一个配置的就是VIM。

介于以前在MacOSX的编译经验，直接三部曲

    ./configue && sudo make && sudo make install

解决的问题。  但在CentOS之后发现无论如何都不支持中文。

通过文档的翻阅和google的搜索，发现了问题出现在编译上。vim支持中文需要2个基本feature：multi\_byte和iconv。

在vim中输入 :version  发现这2个feature都是  – multi\_byte 和 –
iconv。看来编译的时候参数没有配置对。

于是重新执行以下代码

    | ./configure –prefix=/usr –with-features=huge
    |  sudo make
    |  sudo make install

问题就解决了。

另外vim配置文件从第一行(我是unicode的统一论者)，加上

    | set enc=utf-8 set tenc=utf-8
    |  set fenc=utf-8
    |  set fencs=utf-8,usc-bom

其实整个问题都很简单。 但是我发现搜索引擎里的资料
不是通过直观的关键字搜出来的。
所以这里做下一个记录，希望对以后的朋友有所帮助。

.. |image6| image:: /coolshell/static/20140922102130331000.jpg

.. note::
    原文地址: http://coolshell.cn/articles/1432.html 
    作者: 陈皓 

    编辑: 木书架 http://www.me115.com