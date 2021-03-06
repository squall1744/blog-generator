---
title: 如何学习Linux命令行
date: 2018-03-11 13:45:45
tags: 学习
---
<br />
#### 命令行界面简介

在我们普通孩子的生活中, 一般电脑都是跟windows系统挂钩的, 所以大多数孩子们对于电脑的操作很自然的就认为是鼠标点击各种图标, 就像下面这种, 我们双击qq, qq就启动了, 这种操作系统界面呢我们叫做**图形化界面**
![Mac桌面](https://upload-images.jianshu.io/upload_images/8412690-39f55adf602cf2fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
但是呢, 在程序员的世界里, 其实有很多时间, 我们很多时间是需要跟linux系统以及命令行打交道的。

对于命令行界面, 我相信很多年龄大的孩子肯定都很熟悉, 毕竟那个年代的孩子不一定用过, 但是一定见过DOS系统, 就是一个黑黑的背景, 现实几行看不懂的英文, 然后干什么都需要输入指令, 改变目录用cd什么的, 我相信很多大龄孩子们童年都经历过对于DOS的恐惧吧.
![Mac命令行界面](https://upload-images.jianshu.io/upload_images/8412690-7ff0a1e9027404a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

由于我们日常生活中太熟悉图形化界面了, 以致于我们大多数孩子第一次见到命令行的时候完全被吓住了, 感觉又难看, 又难懂, 用起来也很不习惯, 好像还要记很多很多命令才行,  对于用惯了图形化界面的孩子们可能刚开始确实有这种感觉, 但是其实这只是因为我们用的少的原因, 毕竟我们大多数人都用了20多年图形化界面,所以对于图形化界面很熟悉, 但是随着使用的时间增多, 我相信大家一定会发现命令行其实也是很好用的, 下面我就通过几个例子来告诉大家我们应该怎么学习命令行, 希望通过我的一些小经验让大家的命令行入门之路能平缓一些

--------------------------
#### Linux命令行学习

Linux命令行的学习, 我个人认为是有些不同于我们书本知识的学习的, 不需要抱一本书从头看到尾, 把每一条命令都背下来, 而且我相信, 基本上也没人几个人能背下来那几百条命令, 我个人推荐的方法就是, 根据需求学, 用到哪条学哪条, 因为我们日常应用中, 实际上常用的命令行没有太多, 而且由于每天都在用, 所以根本就不需要专门的去记忆, 在平时使用中我们慢慢的就记住了，我总结下来学习一条指令, 一般分一下几个步骤:

1. google需要的指令

    比如说进入命令行,第一件事我们肯定是要进入我们想查看文件夹，那我们就google 'linux 查看文件夹', , 如下图
![ls](https://upload-images.jianshu.io/upload_images/8412690-e65df77f6feadf9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   这样我们就知道了linux查看文件夹命令是ls了, 然后找几个点进去看一下大概的用法, 选一个你能看懂的。。。比如下面这个链接http://www.runoob.com/linux/linux-comm-ls.html

   **这里肯定有人会问, 那我用百度行不行啊, 我只能说程序员远离百度搜索, 在延伸一下, 对于所有技术性学术性的相关搜索都远离百度, 反正你们爱听不听**
**还有人说google已经被封了上不去, 那我再说一句, 不会科学上网, 不会英语的人, 你还搞什么编程啊**

2. 跟着google出来的结果敲一遍

    这里我要强调一下啊, 动手很重要，动手很重要, 动手很重要, 这一部是非常关键的, 你不动手再好的搜索结果也救不了你

    就拿上面那个链接为例把, 我们点进去, 里面有实例, 我们跟着敲就是了, 
![ls实例](https://upload-images.jianshu.io/upload_images/8412690-bbc669e3885ddafd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    我们根据上面的实例敲一下`ls /`, 里面那个斜杠别忘了啊
![ls命令](https://upload-images.jianshu.io/upload_images/8412690-8fd2daf78e4d93ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
    我们会发现我里面列出了README.md  _config.yml db.json等文字, 这个好像和我们对应文件夹下的文件和文件夹是一样的, 只是拿文字表示出来了, 到这里我们其实差不多有点感觉了对吧.
  ls就是通过文字把我们有哪些文件和文件夹显示出来, 文件是灰色字体, 文件夹是白色

    然后我们继续跟着教程往下试`ls -ltr`
![ls -ltr](https://upload-images.jianshu.io/upload_images/8412690-5b2ca0dd1d63d455.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   我们发现后面带上-ltr这样的字符以后, 文件和文件夹会换一种方式显示出来, 前面还有好多我们看不懂的东西, 但是似乎这样排了看起来好像更清楚一些

    既然看不懂, 我们就google啊, 这次我们google “linux ls wr 意思”, 然后搜索结果里面会出现若干跟档案权限有关的答案,如下图
![搜索结果](https://upload-images.jianshu.io/upload_images/8412690-4c57acad2df40e21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   那么我们随便点一个进去, 就第一个吧, 鸟哥什么的(这里说一下啊, 如果想深入学习linux, 鸟哥的书入门的话其实还不错, 有兴趣的google鸟哥的Linux私房菜), 进去后我们往下找找, 然后我们就会发现一个似曾相识的东西, 如下图
![鸟哥](https://upload-images.jianshu.io/upload_images/8412690-2dcbcaecd1014656.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    这好像就是我们要找的东西耶, 好吧, 赶紧看看吧, 到这里我们差不多就对linux命令行显示文件及文件夹功能基本掌握了. 看不是很难吧, 做到这一步, 我们基本上就算成功了, 但是作为一个有追求的人, 我们肯定不会仅仅满足于此, 因为我们注意到`ls`这个命令后面跟不同参数好像会有不同效, 那我们就研究一下呗

3. man一下命令

    这里教大家一个有用的命令, 我们想查看某个命令的具体用法, 可以在命令行里输入man后面跟你想查的命令比如 `man ls`, 这样就可以看到这个命令的具体描述, 以及后面跟的参数的意思, 到这里基本上一个命令的学习就完成了

4. 多多使用

    学完了就要用啊, 以后我们没事就用一用学过的命令就好了, 随着我们学的命令的增多, 命令行我们就会用的越来越6啦, 看吧, 学习命令行其实很简单吧

    到这里我们这次的教程算是完成了, 下面甩一个地址你们自己进去看看, 这个学习linux命令行很好用的
[explainshell](www.explainshell.com)

    另外, 给大家留个作业啊, 用我教的方法学习cat和mv还有touch的用法, 祝大家学习愉快啊 

