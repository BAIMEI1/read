.. _articles8767:

Web工程师的工具箱
=================

2012年12月19日 `陈皓 <http://coolshell.cn/articles/author/haoel>`__

本文出自\ `Ivan Zuzak <http://ivanzuzak.info/>`__ 的《`The Web
engineer’s online
toolbox <http://ivanzuzak.info/2012/11/18/the-web-engineers-online-toolbox.html>`__\ 》，作者给了一个各种可以用来进行开发、测试、调试以及文档编排的在线工具集。（注：我发现CSDN上已经有了这篇文章《\ `Web工程师必备的18款工具 <http://www.csdn.net/article/2012-11-19/2811992>`__\ 》，但可惜的是这篇文章并不全（原文后来被更新到了33个工具），而且其中并没有包括原文评论中出现的所有工具，所以，我一并补全了更出来，一共40多个工具）

**Web工程师在线工具箱**
^^^^^^^^^^^^^^^^^^^^^^^

-  `**RequestBin** <http://requestb.in/>`__\ **：**\ 允许你创建一个URL，利用这款工具进行收集请求，然后通过个性化方式进行检查。

-  `**Hurl** <http://hurl.it/>`__\ **：**\ 发出HTTP请求，输入URL，设置标题，查看响应，最后分享给其他人。类似的工具有：\ `REST
   test test <http://resttesttest.com/>`__, \ `Apigee
   console <https://apigee.com/console/others>`__.。

-  `**Httpbin** <http://httpbin.org/>`__\ **：**\ HTTP请求&响应服务，涵盖所有的HTTP方案（例如不同的HTTP
   verbs、状态代码和重定向）。类似工具：\ `UrlEcho <http://ivanzuzak.info/urlecho/>`__\ 。

-  `**REDbot** <http://redbot.org/>`__\ **：**\ 这是一个机器人工具，帮助用户检查HTTP资源，可查看它的操作情况，指出常见的问题并提出改进。类似工具：\ `HTTP
   lint <http://zamez.org/httplint>`__\ 。

-  `**WebGun** <http://webgun.io/>`__\ **：**\ 用于创建webhooks模板的API。类似工具：\ `UrlReq <https://github.com/izuzak/urlreq>`__\ 。

-  **`Webscript <https://www.webscript.io/>`__ ** 自选一个url，填一段Lua代码，就能对访问做各种respond，还可以主动运行任务，cron
   job等等…

-  **`ClickHooks <http://www.clickhooks.com/>`__ **\ 这是一个短网址服务，
   当用户访问了你的这个短网址跳转链接，服务器会通过HTTP
   POST的方式回调你的一个URL。这也是一种WebHooks方式。（陈皓注：所谓WebHooks，你可以理解为一种trigger，或是一种handler，比如当你你提交了代码，会调用某个URL链接以POST的方式告诉那个网站你提交了代码（如：发一个twitter
   之类的，或是通知某个bug tracker系统））

-  **`MailHooks <http://mailhooks2.appspot.com/>`__ **\ 让你可以通过HTTP
   POST方法收电子邮件（又叫WebHooks），你可以为你的一个邮件地址创建N多的hooks，当一个邮件收到了，可以把这个邮件以POST的方式发到你的某个URL上去。

-  **`Quilla <http://a.quil.la/>`__ **\ 提供一个人们可以找到你的短网站服务，在那里，当人们提交到你的短网址上的请求会给你发邮件。好像是一种HTTP到SMTP的代理服务。

-  `**Apify** <http://apify.heroku.com/resources>`__\ **：**\ 公开锁定在HTML文档没有任何API数据集。APIfy从结构标记中提取数据，并将其转换为JSON
   APIs。

-  `**Unicorn** <http://validator.w3.org/unicorn/>`__\ **：**\ W3C统一的验证程序，可在各种流行的HTML和CSS验证器中执行各种检查。类似工具：\ `HTML
   lint <http://lint.brihten.com/html/>`__\ 。

-  **`JSONLint <http://jsonlint.com/>`__ **\ JSON 格式验证程序

-  `**Feed
   validator** <http://validator.w3.org/feed/>`__\ **：**\ 支持W3C验证，为RSS和ATOM提供阅读源。

-  `**Link
   checker** <http://validator.w3.org/checklink>`__\ **：**\ 从网站中提取链接（递归）并确保没有链接被定义为两次（重复定义），所有的链接被引用并警告HTTP重新定向。

-  `**Host
   tracker** <http://www.host-tracker.com/>`__\ **：**\ 通过分布式ping/跟踪检查、定期监测、邮件/SMS
   /IM通知和统计进行网站检测性服务。类似工具有：`Down for everyone or
   just me <http://www.downforeveryoneorjustme.com/>`__, \ `Pimgdom ping
   service <http://tools.pingdom.com/ping/>`__

-  **`ViewDNS <http://www.viewdns.info/>`__ **\ 一组 DNS
   和网络工具，如：反向IP解析，DNS记录查询或traceroute之类的。

-  **`Necrohost <http://www.necrohost.com/>`__  **\ 一个URL列表来模拟不同网络链接的问题，如：响应慢，无法解析DNS，或是404什么的。

-  **`Mirrorrr <https://code.google.com/p/mirrorrr/>`__ **\ 一个可以用来镜像某网页的应用（经常被国人用来搞Web
   代理来翻墙）。

-  **`SSL Checker <http://certlogik.com/ssl-checker/>`__ **\ 测试SSL认证

-  **`CSR/Cert
   decoder <http://certlogik.com/decoder/>`__ **\ 对你的CSR和SSL认证decode检查。

-  **`Loadzen <http://loadzen.com/>`__ **\ Web压力测试工具（注：以前酷壳介绍过《\ `十个Web压力测试工具 <http://coolshell.cn/articles/2589.html>`__\ 》）

-  `**Pingdom Full page
   test** <http://tools.pingdom.com/fpt/>`__\ **：**\ 允许用户测试网页记载时间、分析、监控，发现瓶颈并导出HAR格式的结果。类似工具：\ `Web
   page test <http://www.webpagetest.org/>`__\ 。

-  **`Google PageSpeed
   Insights <https://developers.google.com/speed/pagespeed/insights>`__ **\ Analyzes
   the content of a web page, then generates suggestions to make that
   page faster.

-  `**HAR
   viewer** <http://www.softwareishard.com/har/viewer/>`__\ **：**\ 通过
   HTTP 追踪工具创建可视化的HTTP Archive (HAR)日志文件。

-  `**CORS
   proxy** <http://www.corsproxy.com/>`__\ **：**\ 通常会由于相同的域而被阻止，而这款工具在网站上允许JavaScript代码访问其他域上的资源，

-  `**Browserling** <https://browserling.com/>`__\ **：**\ 支持使用所有主要浏览器以及各种版本进行交互式跨浏览器测试。

-  `**WebSocket Echo
   Test** <http://www.websocket.org/echo.html>`__\ **:** 从浏览器定向到WebSocket
   echo服务器进行WebSocket连接测试。

-  `**YQL** <http://developer.yahoo.com/yql/>`__\ **：**\ 极富表现力类似于SQL的语言，允许您查询、筛选和联接数据跨Web服务。

-  **`Webshell <http://webshell.io/>`__ **\ 使用命令行脚本的方式来调用一些Web
   API。

-  `**Yahoo
   Pipes** <http://pipes.yahoo.com/pipes/>`__\ **：**\ 一个图形化的用户界面，用于创建数据混搭，生成聚合Web源，Web页面和其他服务。

-  `**Apiary** <http://apiary.io/>`__\ **：**\ 语言和工具用于生成REST
   API文档及进行交互式督查。类似工具：\ `Swagger <http://swagger.wordnik.com/>`__\ 。

-  **`JSFiddle <http://jsfiddle.net/>`__  **\ 一个在线的代码编辑可以让你编译一些HTML,
   CSS 和
   JavaScript的东西，并演示之。相似工具: \ `JSBin <http://jsbin.com/>`__

-  `Google Feed
   API <https://developers.google.com/feed/v1/jsondevguide>`__ 你可以使用这个API来查询有RSS
   Feed的网站 (\ `example <http://ajax.googleapis.com/ajax/services/feed/lookup?v=1.0&q=http://ivanzuzak.info/>`__)，或是搜索有RSS
   Feed(\ `example <https://ajax.googleapis.com/ajax/services/feed/find?v=1.0&q=ivan%20zuzak>`__)
   ，或是把JSON变成一个JSON返回
   (`example <https://ajax.googleapis.com/ajax/services/feed/load?v=1.0&q=http://ivanzuzak.info/atom.xml>`__)

未在列表的工具
^^^^^^^^^^^^^^

-  `Fiddler <http://www.fiddler2.com/fiddler2/>`__ —
   可能是最强大最好用的Web调试工具之一，它能记录所有客户端和服务器的http和https请求，允许你监视，设置断点，甚至修改输入输出数据.
   使用Fiddler无论对开发还是测试来说，都有很大的帮助。.

-  `960 grid system generator <http://grids.heroku.com/>`__ 和 `CSS
   reset <http://meyerweb.com/eric/tools/css/reset/>`__ —
   两个关注于Web站点设计的工具。

-  `NuvolaBase <http://www.nuvolabase.com/site/index.html>`__ —
   一个可以共享个人私有数据的解决方案。正如作者所说，这不是一个开发工具。

-  `Open exchange rates <https://openexchangerates.org/>`__ —
   一个和汇率货币相关的JSON式的API。这样的API你可以到 \ `Programmable
   Web <http://www.programmableweb.com/>`__ 上查找。

-  `Browsershots <https://browsershots.org/>`__ —
   一个用来测试网页在不同平台下的工具。（参看）

-  `Scriptular <http://scriptular.com/>`__ and `Rubular <http://rubular.com/>`__
   —
   正则表达式工具，这样的工具太多了，如： \ `ReFiddle <http://refiddle.com/>`__, \ `Regex
   pal <http://regexpal.com/>`__ and `Txt2Re <http://www.txt2re.com/>`__\ 。

（全文完）

.. |image6| image:: /coolshell/static/20140921233221483000.jpg

.. note::
    原文地址: http://coolshell.cn/articles/8767.html 
    作者: 陈皓 

    编辑: 木书架 http://www.me115.com