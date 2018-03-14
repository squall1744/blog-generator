---
title: HTTP入门
date: 2018-03-14 21:29:35
tags: 学习笔记
---
<br>
上次介绍[如何学习Linux命令行](https://www.jianshu.com/p/f326f905e365), 这次我们就来介绍介绍HTTP的入门知识吧, 这次大概会简单的介绍一下HTTP请求和响应里面包含哪些内容, 然后怎么用chrome查看请求头, 响应头, 算是HTTP最最最简单的入门知识吧

---------------------------------------------------
#### 什么是HTTP
[超文本传输协议](https://baike.baidu.com/item/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)（HTTP，HyperText Transfer Protocol)是[互联网](https://baike.baidu.com/item/%E4%BA%92%E8%81%94%E7%BD%91)上应用最为广泛的一种[网络协议](https://baike.baidu.com/item/%E7%BD%91%E7%BB%9C%E5%8D%8F%E8%AE%AE), 所有的www文件都必须遵守这个标准, HTTP是[全球网络资讯](https://zh.wikipedia.org/wiki/%E5%85%A8%E7%90%83%E8%B3%87%E8%A8%8A%E7%B6%B2 "全球資訊網")的數據通信的基礎

简单来说, 当我们访问互联网时候, 就是通过http协议来让我们电脑和你访问的网站进行通讯的

通常情况下, 我们访问一个网站的步骤大体上是这样的
![HTTP传输](https://upload-images.jianshu.io/upload_images/8412690-42d1b6c7acf59a7b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1. 我们在浏览器输入网址后, 浏览器会出现一个地址, 通常是`http://`或者`https://`开头的, 我们把这个叫做**URL**
2. 通过URL地址,就可以确定我们是向哪个服务器发送**HTTP请求**, 之后HTTP请求就会发送到那个服务器了
3. 网站的服务器接收到HTTP请求后,根据HTTP请求内容返回对应的**HTTP响应**给我们的浏览器
4. 浏览器根据**HTTP响应**的内容生成对应网页

那么到底URL是什么, HTTP请求有是什么, HTTP响应又是什么, 当我们搞懂这些东西后, HTTP就算是基本入门啦

___________________________________
#### URI和URL
通过上面的访问一个网站的步骤我们知道, 我们是通过URL来告诉浏览器应该发送HTTP请求给哪台服务器,(不然他怎么知道我们是想访问baidu还是google又或者是tencent呢), 那么URL到底是个什么东西呢？
##### URI
URI：(Uniform Resource Identifier 的缩写，统一资源标识符),一种字符串文本标准, 这种文本主要是用来确定一个唯一资源的, URL是URI的一种, 就是说，URI 属于父类，而 URL 属于 URI 的子类

##### URL
URL：(Uniform/Universal Resource Locator 的缩写，统一资源定位符)
上面我们说了URI是用来确定一个唯一资源的字符串文本标准,他能用来确定一个资源, 具有唯一性,那么在互联网领域, 我们就规定用URI的一个子集URL来表示我们要访问的资源具体放在哪里,。

打个比方吧, 当我们访问百度这个网站, 请求就是通过百度的URL地址来定位百度的服务器在哪儿的, 这样就不会因为不知道百度服务器在哪儿,把请求发送到谷歌的服务器去

##### URL组成
我们借用一下**饥人谷方方老师**的图来说明一下域名的组成

![域名组成](https://upload-images.jianshu.io/upload_images/8412690-01ad6869027696c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 协议：
这个就是告诉浏览器, 我们通过什么协议来发送请求, 一般访问网站我们就是http或者https, 当然还有ftp之类的很多协议, 有兴趣的同学请自行google

+ 域名
是由一串用点分隔的名字组成的[Internet](https://baike.baidu.com/item/Internet)上某一台[计算机](https://baike.baidu.com/item/%E8%AE%A1%E7%AE%97%E6%9C%BA)或[计算机组](https://baike.baidu.com/item/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BB%84)的名称，用于在数据传输时标识计算机的电子方位

   有一定计算机知识的同学肯定知道我们一般是通过IP地址定位网络上一台主机位置的, 但是由于IP地址不便于记忆等原因. 就产生了用域名这种具有文字意义的标示方法来标识网络上某台计算机的方法,通过**DNS**将域名与具体的IP地址进行关联, 就可以实现用域名来标示网络上某台计算机位置的功能了

   至于IP相关的知识在这里就不讲了, 毕竟这是一个HTTP的入门教程, IP的话有兴趣的同学可以自行百度**TCP/IP协议**相关知识, 或者买一本**《图解HTTP》**自行研究

+ DNS
DNS 全名叫 Domain Name Server，中文俗称“域名服务器”，正如上面所讲，在网上辨别一台电脑的方法是利用 IP地址，但是 IP用数字表示，没有特殊的意义，很不好记，因此，我们一般会为网上的电脑取一个有某种含义又容易记忆域名, 比如baidu, 我们一般都直接输入www.baidu.com就好了, 根本不会去记百度的IP地址。但是由于在 Internet 上真实辨认机器的还是IP，所以当使用者在浏览器中输入域名后，浏览器必须先到一台有域名和 IP 对应信息的主机去查询这台电脑的 IP，而这台被查询的主机，我们称它为 Domain Name Server，简称 DNS

+ 路径
`/`之后(包括'/')到`?`之前的内容, 不同的路径表示不同的位置, 服务器会根据不同的路径返回不同的内容, 这里我要强调一下, 这个路径虽然看起来很像windows电脑的路径, 但是实际上这两个没有什么关系, 最好别按windows文件路径来理解, 这里的路径就是表示不同的位置而已, 即使用`/hello.txt`这种路径也不代表返回的是txt文件, 返回什么完全是由后台程序员写的程序决定

+ 查询参数
`?`之后(包括`?`)到`#`之前的内容, 用于查询通常包含若干由等号连接的键值对组成, 每个之间由&隔开例如`?a=1&b=2&c=3`

+ 锚点
`#`及之后的内容, 锚点的作用就跟名字一样, 我们都知道锚是用来固定位置的, 那么锚点主要作用也是用来指定位置的, 通常我们用锚点来跳转到页面中的指定位置

---------------------------------

#### HTTP请求
当我们在浏览器中输入URL地址后, 浏览器就会发送一条HTTP请求, 那么HTTP请求包含哪些内容呢, 下面我们先说一下怎么通过chrome浏览器查看HTTP请求和响应

##### 如何通过chrome浏览器查看http请求和响应

1.在chrome浏览器中按键盘上的`F12`键, 就会出现下面截图右边的这个功能区, 然后点`Network`
![开发者工具](https://upload-images.jianshu.io/upload_images/8412690-859c5cadcda245f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 在浏览器的地址栏输入`www.baidu.com`, 然后我们会发现我们的`Network`功能区出现了好多的文件一样的东西, 我们网上翻, 找到带有index字样的文件, 这个就是百度首页的请求响应文件
![Network](https://upload-images.jianshu.io/upload_images/8412690-d119ed9b32a892af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.然后点击一下这个文件, 就会看到跟我下面的图一样的界面, Response Headers就是响应头, Request Headers就是请求头, Response就是响应内容, **记得一定要点view source!!!!, 记得一定要点view source!!!!, 记得一定要点view source!!!!**
![请求文件](https://upload-images.jianshu.io/upload_images/8412690-10b422b6de07393a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### HTTP请求内容
HTTP请求一般分为四部分, 我们拿图来说明, 我从网上找了个图啊
第一部分: 请求行, 图上的1, 2, 3
第二部分: 请求头, 图上的4
第三部分: 一个回车
第四部分: 请求体, 图上的5
![HTTP请求](https://upload-images.jianshu.io/upload_images/8412690-504cb7494c12995b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 请求行
这里面包含三个内容, 请求方法, 请求路径, HTTP协议及版本, 这里面特别说明一下, 请求路径是包含查询参数的, 但是不包含锚点
请求有哪些方法及这些方法的作用作用请自行百度, 这里就不展开了

+ 请求头
请求头是由若干个键值对组成的, 描述了请求的要求参数, 如

    内容|含义
    -|-
    Accept: image/jpeg, application/x-ms-application|接收的数据类型
    Content-Length: 112|请求体内容长度112字节
   User-Agent: MOzilla/4.0| 用户代理类型

  具体内容可以参考下面这个文章[HTTP请求头分类](http://blog.csdn.net/wkl305268748/article/details/78577785)

+ 请求体
请求具体内容, 在chrome浏览器里查看请求的时候, 一般看不到请求体

----------

#### HTTP响应

##### HTTP响应内容
当服务器接收到HTTP请求后, 会根据请求的具体内容返回响应, 我又从网上找了个图。。。

HTTP响应跟请求一样, 也是分为四部分
第一部分: 响应行
第二部分: 响应头
第三部分: 回车
第四部分: 响应体

![HTTP响应](https://upload-images.jianshu.io/upload_images/8412690-8f1955ad1ae3129d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 响应行
响应行包括HTTP版本协议, 状态码, 状态码描述

+ 状态码
状态码简单来说就是响应对于请求做出何种反馈的代码, 通常我们分为以下几大类型

状态码|类别|原因短语
-|-|-
1XX|Informational 信息性状态码|接收请求正在处理
2XX|Success 成功状态状态码|请求正常处理完毕
3XX|Redirection 重定向状态码|需要进行附加操作以完成请求, 意思就是要浏览器换个地方请求
4XX|Client Error 客户端错误状态码|服务器无法处理请求, 意思就是说浏览器的请求错啦
5XX|Server Error 服务器错误状态码|服务器处理请求出错, 意思是说服务器自己出问题啦
具体HTTP包含哪些, 请看下面这个链接[HTTP状态吗](https://zh.wikipedia.org/wiki/HTTP状态码)

+ 响应头
这个部分跟请求头一样, 也是一堆键值对, 包含了响应的参数, 比如Content-Length表示响应内容长度
Content-Type表示响应内容类型等, 具体的也请大家自己研究吧

+ 响应体
响应的具体内容, 比如返回一个html网页什么的

---------------
到这里HTTP入门部分算是讲完了, 其实也就是大概说了一下, 主要目的就是希望大家能对HTTP协议有个基本的认识, 更深层的内容请大家自己下来好好研究吧。
