# Pyhton 入门

## python介绍
python的创始人为吉多·范罗苏姆（Guido van Rossum）。1989年的圣诞节期间，Guido开始写能够解释Python语言语法的解释器。Python这个名字，来自Guido所挚爱的电视剧Monty Python’s Flying Circus。他希望这个新的叫做Python的语言，能符合他的理想：创造一种C和shell之间，功能全面，易学易用，可拓展的语言。

最新的TIOBE排行榜，Python赶超PHP占据第4， Python崇尚优美、清晰、简单，是一个优秀并广泛使用的语言。

Python可以应用于众多领域，如：数据分析、组件集成、网络服务、图像处理、数值计算和科学计算等众多领域。目前业内几乎所有大中型互联网企业都在使用Python，如：Youtube、Dropbox、BT、Quora（中国知乎）、豆瓣、知乎、Google、Yahoo!、Facebook、NASA、百度、腾讯、汽车之家、美团等。

#### 目前Python主要应用领域
```Python
#1. WEB开发——最火的Python web框架Django, 支持异步高并发的Tornado框架，短小精悍的flask,bottle, Django官方的标语把Django定义为the framework for perfectionist with deadlines(大意是一个为完全主义者开发的高效率web框架)
#2. 网络编程——支持高并发的Twisted网络框架， py3引入的asyncio使异步编程变的非常简单
#3. 爬虫——爬虫领域，Python几乎是霸主地位，Scrapy\Request\BeautifuSoap\urllib等，想爬啥就爬啥
#4. 云计算——目前最火最知名的云计算框架就是OpenStack,Python现在的火，很大一部分就是因为云计算
#5. 人工智能——谁会成为AI 和大数据时代的第一开发语言？这本已是一个不需要争论的问题。如果说三年前，Matlab、Scala、R、Java 和 Python还各有机会，局面尚且不清楚，那么三年之后，趋势已经非常明确了，特别是前两天 Facebook 开源了 PyTorch 之后，Python 作为 AI 时代头牌语言的位置基本确立，未来的悬念仅仅是谁能坐稳第二把交椅。
#6. 自动化运维——问问中国的每个运维人员，运维人员必须会的语言是什么？10个人相信会给你一个相同的答案，它的名字叫Python
#7. 金融分析——我个人之前在金融行业，10年的时候，我们公司写的好多分析程序、高频交易软件就是用的Python,到目前,Python是金融分析、量化交易领域里用的最多的语言
#8. 科学运算—— 你知道么,97年开始，NASA就在大量使用Python在进行各种复杂的科学运算，随着NumPy, SciPy, Matplotlib, Enthought librarys等众多程序库的开发，使的Python越来越适合于做科学计算、绘制高质量的2D和3D图像。和科学计算领域最流行的商业软件Matlab相比，Python是一门通用的程序设计语言，比Matlab所采用的脚本语言的应用范围更广泛
#9. 游戏开发——在网络游戏开发中Python也有很多应用。相比Lua or C++,Python 比 Lua 有更高阶的抽象能力，可以用更少的代码描述游戏业务逻辑，与 Lua 相比，Python 更适合作为一种 Host 语言，即程序的入口点是在 Python 那一端会比较好，然后用 C/C++ 在非常必要的时候写一些扩展。Python 非常适合编写 1 万行以上的项目，而且能够很好地把网游项目的规模控制在 10 万行代码以内。另外据我所知，知名的游戏<文明> 就是用Python写的
```

#### Python在一些公司的应用

```Python
# 谷歌：Google App Engine 、code.google.com 、Google earth 、谷歌爬虫、Google广告等项目都在大量使用Python开发
# CIA: 美国中情局网站就是用Python开发的
# NASA: 美国航天局(NASA)大量使用Python进行数据分析和运算
# YouTube:世界上最大的视频网站YouTube就是用Python开发的
# Dropbox:美国最大的在线云存储网站，全部用Python实现，每天网站处理10亿个文件的上传和下载
# Instagram:美国最大的图片分享社交网站，每天超过3千万张照片被分享，全部用python开发
# Facebook:大量的基础库均通过Python实现的
# Redhat: 世界上最流行的Linux发行版本中的yum包管理工具就是用python开发的
# 豆瓣: 公司几乎所有的业务均是通过Python开发的
# 知乎: 国内最大的问答社区，通过Python开发(国外Quora)
# 春雨医生：国内知名的在线医疗网站是用Python开发的
# 除上面之外，还有搜狐、金山、腾讯、盛大、网易、百度、阿里、淘宝 、土豆、新浪、果壳等公司都在使用Python完成各种各样的任务。
```

#### Python(解释器)的发展史

```Python
# 1989年，Guido开始写Python语言的编译器。
# 1991年，第一个Python编译器诞生。它是用C语言实现的，并能够调用C语言的库文件。从一出生，Python已经具有了：类，函数，异常处理，包含表和词典在内的核心数据类型，以及模块为基础的拓展系统。
# Granddaddy of Python web frameworks, Zope 1 was released in 1999
# Python 1.0 - January 1994 增加了 lambda, map, filter and reduce.
# Python 2.0 - October 16, 2000，加入了内存回收机制，构成了现在Python语言框架的基础
# Python 2.4 - November 30, 2004, 同年目前最流行的WEB框架Django 诞生
# Python 2.5 - September 19, 2006
# Python 2.6 - October 1, 2008
# Python 2.7 - July 3, 2010
# In November 2014, it was announced that Python 2.7 would be supported until 2020, and reaffirmed that there would be no 2.8 release as users were expected to move to Python 3.4+ as soon as possible
# Python 3.0 - December 3, 2008 (这里要解释清楚 为什么08年就出3.0，2010年反而又推出了2.7？是因为3.0不向下兼容2.0，导致大家都拒绝升级3.0，无奈官方只能推出2.7过渡版本)
# Python 3.1 - June 27, 2009
# Python 3.2 - February 20, 2011
# Python 3.3 - September 29, 2012
# Python 3.4 - March 16, 2014
# Python 3.5 - September 13, 2015
# Python 3.6 - 2016-12-23 发布python3.6.0版
```

#### Python 有哪些种类?

```python
我们现在知道了Python是一门解释型语言，代码想运行，必须通过解释器执行，Python的解释器本身也可以看作是个程序（翻译官司是哪国人不重要），这个程序是什么语言开发的呢？ 答案是好几种语言？ what? 因为Python有好几种解释器，分别基于不同语言开发，每个解释器特点不同，但都能正常运行我们的Python代码，下面分别来看下：

#CPython：CPython是使用最广且被的Python解释器。本教程以CPython为准。
当我们从Python官方网站下载并安装好Python 2.7后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。

#IPython
IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了IE。
CPython用>>>作为提示符，而IPython用In [序号]:作为提示符。

#PyPy
PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用JIT技术，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。
绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解PyPy和CPython的不同点。

#Jython
Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

#IronPython
IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。
```
