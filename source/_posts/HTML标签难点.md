---
title: HTML标签难点
date: 2018-03-14 21:31:40
tags: 学习笔记
---
<br>
这里我假设大家已经对html标签有了基本了, 所以一些基本标签如div, p， h1等简单的标签我就不做介绍了, 我下面只介绍常用标签中的几个需要注意的点

-----------------------------------

#### iframe标签
一个网页中嵌套页面, 现在用的不多了, 但是维护老项目可能会用到, 使用iframe后, 页面会变卡

iframe标签写法没有太大难度, 基本上就是下面这样
```html
<iframe src="http://www.qq.com" frameborder="0"></iframe>
```
+ `src` 嵌套页面的路径, 可以是相对路径
+ `frameborder=0`  嵌套页面的边框, 为0时不现实边框, 一般我们也不写

实现效果如下
![iframe](https://upload-images.jianshu.io/upload_images/8412690-26334166c33d2f79.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其实ifame我们一般可以配合a便签使用的
我们给iframe一个`name`属性`xxx`, 然后在a标签中给一个`target`属性`xxx`, 当我们点击a链接的时候, a链接的内容就会现实在iframe中, 如下代码

```html
  <iframe name ="xxx" src="" frameborder="0"></iframe>
  <a target="xxx" href="http://qq.com">qq</a>
  <a target="xxx" href="http://baidu.com">百度</a>
```

当我们点击qq链接时, iframe就会出现qq主页
![qq](https://upload-images.jianshu.io/upload_images/8412690-8c4c65321fd494ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当我们点击百度时, 就会出现百度主页
![百度](https://upload-images.jianshu.io/upload_images/8412690-c2b42e2fbaed06e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-----------

#### a标签

a标签中我们需要注意的一个是target属性, 还有一个就是download属性, 最后就是href支持的类型

```html
  <a href="" target="_blank">新页面打开链接</a>
  <a href="" target="_self">当前页面打开链接</a>
  <a href="" target="_parent">父元素打来链接</a>
  <a href="" target="_top">顶层元素打开链接</a>
  <a href="http://qq.com" download>下载链接内容</a>
```

href可用的路径类型
+ 绝对路径
`href="/src/css/style.css"`

+ 相对路径
`href="src/css/style.css"`
`href="qq.com"`

+ 锚点
`href="#5"`

+ 查询参数
`href="?name=Adam"`

+ 无协议绝对路径
`href="//qq.com"` 当前文件用什么协议就是什么协议

+ url地址
`href="http://www.qq.com"` 直接打开网址

+ javascript伪协议
`href="javascript: alert(1)"` 执行alert代码, 
这种情况一般用于防止a标签跳转, 设置`href="javascript:;"`后, 点击a标签, 将不会进行任何跳转

-----------
#### form标签
对于form标签, 我们首先要记住下面几句话
1. form标签主要是为了发送post请求
2. form表单内使用submit提交表单, 所以请不要忘记添加submit按钮
3. input中的name对应HTTP请求第四部分请求中的key, 输入的值对应第四部分的value
4. form标签是有target属性的, 什么是target属性??? 往上翻a标签章节啊! 
5. form标签其实是可以发送get请求的, 但是如果我们只是为了拿数据的话, 那为什么不用a标签呢?


下面我们看一段代码

  ```html
<form action="user" method="post">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit">
  </form>
```

我们输入账号密码, 点提交后
![输入账号密码](https://upload-images.jianshu.io/upload_images/8412690-6d0c2247046691d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

我们会看到在HTTP请求中会有一个请求,
+ 我们会发现这个请求的路径是`/user`,对应我们的form的`action="user"`
+ 请求方法是`POST`, 对应form的`method="post"`
+ form data里面的请求体是`username=adam&password=123456789`
细心的同学一定发现了这两组数据刚好对应了我们上面两个input, 等号前面的key对应我们input的name属性, 等号后面的value对应我们输入的内容
+ 从上面的分析我们就可以看出, form表单实际上就是用来发送HTTP请求的

![image.png](https://upload-images.jianshu.io/upload_images/8412690-0b631ef32ece240b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### input标签
1. `button`标签和`type="submit"`区别
   + 如果一个form里只有一个button标签, `<button></button>`会自动转变为 `<input type="submit">`
   + input中的type=button不能自动转变为submit

2. `label`
 + `label`标签的for和input的id是一对

  ```html
   <form action="user" method="post">
     <label for="a">用户名</label>
     <input type="text" name="username" id="a">
     <button>aa</button>
  </form>
   ```
   通常情况下, 我们只有点击`input输入框`才能输入内容的, 当把`label`的`for`和`input`的`id`设为一样时候, 点击`labe`l, 相应的`input输入框`也可以输入内容了,如下面的图, 当设置`label`后, 我们点击用户名三个字, 输入框也是可以输入的, label适用于很多`type`, 如`text`, `checkbox`的等

![image.png](https://upload-images.jianshu.io/upload_images/8412690-65ae03ba0b738283.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  + 不过老司机们都比较懒, 觉得每次输入`fo`r和`id`很麻烦, 那么其实我们用`label`把`input`包裹起来也能达到这个效果

   ```html
   <form action="user" method="post">
     <label>用户名
       <input type="text" name="username">
     </label>
     <button>aa</button>
   </form>
   ```

3. `checkbox`
记得给`name`和`value`啊, 不然服务器不好拿到数据啊

   ```html
   <form action="user" method="post">
       <input type="checkbox" name="fruit" value="orange">橘子
       <input type="checkbox" name="fruit" value="apple">苹果
       <input type="checkbox" name="fruit" value="banana">香蕉
     <input type="submit">
   ```

   我们点苹果和香蕉啊
![水果](https://upload-images.jianshu.io/upload_images/8412690-f912356c4ee4afad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   请求体里面有了吧？

![请求体](https://upload-images.jianshu.io/upload_images/8412690-aba930284ddad6e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. `radio`
radio我们只记住一句话就好, 只要给若干个radio同一个name属性, 就能实现单选功能

5. `select`
关于select主要强调以下几点
   + `select`标签跟input标签一样, `name`对应请求头第四部分的key, `value`对应第四部分的value
   + `select`一定是和`option`成对出现的

   + `select`设置`multiple`后, 按住键盘`ctrl`可以多选
   + 设置`disabled`的`option`不能选择
   + 设置`selected`的`option`是默认选项 

     下面是典型的`select`代码
  ```html
  <form action="user" method="post">
    <select name="fruit" multiple>
      <option value="apple">苹果</option>
      <option value="orange">橘子</option>
      <option value="banana" disabled>香蕉</option>
      <option value="peach" selected>桃子</option>
      <input type="submit">
    </select>
  </form>
   ```

6. `textarea`
   + `textarea`的特殊点在于可以通过拖动鼠标改变输入框大小, 这样很容易由于用户随意拖动输入框破坏我们页面的布局, 因此一般情况下我们都会固定宽高, 禁止拖动, 我们可以通过设置`style="resize: none"`来禁止拖动输入框

   + 虽然可以通过`col`和`rows`来设置行数和列数, 但是依然建议通过css来控制输入框大小而不是痛殴过行列来设置
   典型的textarea代码
```html
  <form action="user" method="post">
    <textarea style="resize: none" name="爱好" cols="30" rows="10"></textarea>
    <input type="submit">
  </form>
```
-------------------

#### table
table主要就是写起来复杂, 其他倒没什么

```html
  <table border=1>
    <colgroup>
      <col width=100px>
      <col width=200px>
      <col width=50px>
      <col width=150px>
    </colgroup>
    <thead>
      <tr>
        <th>项目</th><th>姓名</th><th>班级</th><th>分数</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th></th><td>小明</td><td>1</td><td>95</td>
      </tr>
      <tr>
        <th></th><td>小红</td><td>1</td><td>96</td>
      </tr>
    </tbody>
          <tr>
        <th>平均分</th><td></td><td></td><td>95.5</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <th>总分</th><td></td><td></td><td>191</td>
      </tr>
    </tfoot>
  </table>
````
具体的每个标签代表啥, 看下面的

![81D42F18-649D-4D3F-9AAA-480A08C0F7E2.png](https://upload-images.jianshu.io/upload_images/8412690-0598f8852bbd8634.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

--------------

到这里HTML标签的难点我们差不多就学完了， 这些学好后, 我相信大家其他的一定都没问题啦