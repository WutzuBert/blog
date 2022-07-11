---
title: Python升级之路( Lv1 ) Python 入门
tags: 时间静止不是简史
excerpt: Python介绍, 环境搭建, 基本格式, 异常处理, 注释格式, 绘图等
---

#  Python系列文章目录
第一章 Python 入门

---


@[TOC](Python 入门)

---

# 前言


最近打算新开一个坑, 但一直不知道做什么合适, 直到最近在看 **《UNIX/Linux系统管理技术手册》** 这一书的  **脚本编程与shell** 这一章节中得到启发, 书中说到

- **关于Python**

>Python 和 Ruby 都是面向对象的解释型语言, 两者被广泛用于通用脚本编程语言, 拥有数量众多的库和第三方模块. Python的语法直观, 非常容易理解, 哪怕你阅读的是别人写的代码


并且作者建议: 所有的**系统管理员都应该掌握 Python** , 因为它是 **现代系统管理和通用脚本编程的首选语言**. 并且Python 还作为胶水语言大量用于其他系统(例如Postgre SQL 数据库以及Apple Xcode 开发环境 ), 它还与REST API 之间有着清晰的接口, 在**机器学习, 数据分析和数值计算**方面也有不少优秀的库

- **关于Ruby**

Ruby 是由日本开发人员 YukiHiro Matsumotu 设计并维护, 拥有很多与 Python相同的特性, 其中就包括"万物皆对象"的做法. 书中直言
>尽管在很多方面, Ruby粗略的等同 Python, 但前者的设计理念要更为宽松. 例如: 其他软件可以随意修改Ruby的类, 一些修改了标准库的扩展也基本上不会在 Ruby 社区引发什么不满
>Ruby 对于喜欢尝试语法糖的用户很有吸引力, 语法糖是一种特性, 他并不会改变基本的语言, 但允许以更为精确, 清晰的形式编写代码.

>例如在Rails环境中 `due_date=7.days.from_now`  , 该代码不引用任何与时间相关的类, 也不需要进行任何显式的日期与时间计算, 就可以创建一个TIme 对象. 将days定义为 Fixnum(描述整数的Ruby类)的拓展, 该方法会返回一个用起来想数字一样的 Duration 对象, 作为使用值的话它等于604800, 这是7天的总秒数. 如果在调试器中查看, 它会将自身描述为 "7days"

>开发人员可以使用Ruby轻松创建特定领域的语言(domain specific language,DSL). 这种迷你语言实际上还是Ruby, 到那时可以读取特定的配置系统. 例如 Chef 和 Puppet 就可以用 Ruby DSL 来配置.

**选择学习 Python的原因**

-  同样作为面向对象的解释语言,  Python 的流行度更高, 社区更活跃
- 相比来说 Ruby 更适合科研领域学习, 而 Python 更适合企业应用
- 学习 Python 并不是为了成为 Linux/Unix 系统管理员, 而是为了今后能够能加得心应手的编写shell 脚本.
并且利用其拓展自己的技术栈
- Python 相较其他语言, 更适合用作脚本语言

**所以,   话不多说, 我们就来逐渐揭开Python的真正面纱吧**

---



# 一、Python是什么

>Python is a programming language that lets you work quickly and integrate systems more effectively
>即: Python 是一个让你工作更快速并且更高效集成系统的编程语言. 官网 [传送门](https://www.python.org/)


**特点:**
- 可读性强
- 语法简洁
- 开源易移植
- 标准脚本语言

**应用场景:**
- 人工智能AI
- web应用开发
- 操作系统管理、**服务器运维的自动化脚本**
大多数Linux发行版以及NetBSD、OpenBSD和MacOSX都集成了Python，可以在终端下直接运行Python。
**Python编写的系统管理脚本在可读性、性能、代码重用度、扩展性几方面都优于普通的shell脚本**。
- 科学计算和数据分析
- 桌面软件
- 服务器软件, **网络爬虫**
- 游戏开发

**Python版本和兼容问题解决方案**
-  Python有两大版本，分别是Python2.x和Python3.x
- Python2.x版本在2020年已经停止支持，因此Python3.x是目前主流
- Python3的很多新特性也被移植到了Python2.7，作为过渡。
如果程序可以在2.7运行，可以通过一个名为2to3（Python自带的一个脚本）的转换工具无缝迁移到Python3。

---
# 二、运行环境搭建
## 1. Python 语言环境
> 相关软件已在底部通过百度云的形式分享

![在这里插入图片描述](https://img-blog.csdnimg.cn/db0bf68d7576428db0a089187be36359.png)



1. 以管理员身份运行
将其添加到 Windows的环境变量中, 以便我们可以通过 shell 窗口直接执行 python 相关命令
![在这里插入图片描述](https://img-blog.csdnimg.cn/9843f8a860a344f598dfbb2b17cf6d80.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_15,color_FFFFFF,t_70,g_se,x_16)

2. 直接点击Next

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2d42377a8361452d966419637ec0aad0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_15,color_FFFFFF,t_70,g_se,x_16)

3. 一定要注意这里是否被勾选, 这里用于自动将python 语言环境的安装地址放入到环境变量中.
安装完毕后点击 close
![在这里插入图片描述](https://img-blog.csdnimg.cn/744402fe906b495e8185c1d72b43aea2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_15,color_FFFFFF,t_70,g_se,x_16)

4. 唤出shell 界面, 测试是否安装成功
Win+R , 然后输入 cmd, 然后在shell 中输入 `python`
![在这里插入图片描述](https://img-blog.csdnimg.cn/2f7cdfe2ddd84926b29a0a4befc597f2.png)

5. hello world

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/fca3eadd65d84f6890e0698a8df32a45.png)
6. 退出当前 Python shell

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/12c8f0c8d77346f1a21b726b64ddb5d8.png)


## 2. Python 开发环境
> 开发环境，英文是IDE（Integrated Development Environment 集成开发环境）.
这里将介绍最常用的三种开发环境, 大家可以根据自己的喜好来选择( **合适自己才是最重要的~** ).








**Python 常用开发环境**

1.  IDLE
2.  Pycharm （推荐）
3.  vscode （推荐）
4.  jupyter



### IDLE
**什么是 IDLE(What)**

-  IDLE是Python的官方标准开发环境，Python安装完后同时就安装了IDLE。

- IDLE已经具备了Python开发几乎所有功能（语法智能提示、不同颜色显示不同类型等等），也不需要其他配置，非常适合初学者使用。

- IDLE是Python标准发行版内置的一个简单小巧的IDE，包括了交互式命令行、编辑器、调试器等基本组件，足以应付大多数简单应用。

-  IDLE是用纯Python基于Tkinter编写，最初作者正是Python之父

**IDLE 如何使用(How)**

1. 点击开始

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/69ce1ed3862b4b21ab18c77f30dbbc60.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_14,color_FFFFFF,t_70,g_se,x_16)

2. 新建文件
FIle-> new FIle, 然后空白处输入 `print("hellow world") `  再保存为 `mypy01.py` ,

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/30d64db46294471787f6030d681d7eff.png)
3. 运行 hello world
最后点击 `Run-> Run Module` 或者 F5 即可运行
![在这里插入图片描述](https://img-blog.csdnimg.cn/f20901726fbf4b1baa5baf9ee3c7e416.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_13,color_FFFFFF,t_70,g_se,x_16)

**注意:**
- **不要使用中文输入**
引入使用中文拼音输入之后, 点击回车会自动弹出Python的使用文档和一个用于搜索当前 IDLE 的 Search Dialog
![在这里插入图片描述](https://img-blog.csdnimg.cn/2fa3f49e7c6b46978c19d6ba493dea22.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_20,color_FFFFFF,t_70,g_se,x_16)
 Search Dialog的作用相当于 IDEA 的 Ctrl + F, 当前页面的搜索
![在这里插入图片描述](https://img-blog.csdnimg.cn/1212d00b6aae49d58b4a1245705f5d7d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_13,color_FFFFFF,t_70,g_se,x_16)


### PyCharm
>**PyCharm出自JetBrains之手. 是一种Python IDE，带有一整套可以帮助用户在使用Python语言开发时提高其效率的工具.**
>类似IDEA, 作为 企业级软件, 用于快速开发 Python 程序, 之前使用过IDEA的非常推荐使用.
>下载地址：[传送门](https://www.jetbrains.com/pycharm/download) , 也可以使用博客底部百度云分享的 .exe 程序直接安装
>**因为个人习惯原因, 后续使用 PyCharm 来演示相关Python代码操作.**



**Pycharm的优点**

- 方便的环境管理
- 自动导入包
- 方便的代码调试
- Git管理

**Pycharm的缺点**

- 刚开始打开，索引包较慢
- 内存占用太高(3G左右)

**安装使用步骤**
1. 安装
直接运行 PyCharm.exe, 然后一直 next , 然后点击 install , 最后点击 Finish


2. 新建项目

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/c80331f10a5c49bba14a864d6ff4bbe0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_17,color_FFFFFF,t_70,g_se,x_16)

    新建项目配置

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2f15323847d341df91bca5659bc4ecf4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_17,color_FFFFFF,t_70,g_se,x_16)

3. 开发和运行项目
打开项目后，右键单击项目，new -> FIle , 创建Python文件 mypy01
![在这里插入图片描述](https://img-blog.csdnimg.cn/fdb3c8221522421d9257a53e84b7f6ed.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_16,color_FFFFFF,t_70,g_se,x_16)

    点击 Run-> Run xxx 或者直接 Shift+ F10 运行即可

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/f5dff3b3a65b49acacb7dd315c7e7651.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_17,color_FFFFFF,t_70,g_se,x_16)

4. 交互模式和控制台

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/0a45888c86134d4c9bba36a5d13ea104.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_16,color_FFFFFF,t_70,g_se,x_16)

    控制台(Terminal )相当于直接进入了 Windows的shell 界面

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/e2f409e8623f410c91c55a2d98bd7081.png)

    交互模式相当于进入类似IDLE的交互模式：

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/45e55c063f914725b8c8a531ee3ee46f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_18,color_FFFFFF,t_70,g_se,x_16)

5. 项目创建后引用的包版本配置
![在这里插入图片描述](https://img-blog.csdnimg.cn/0eadbeb41f374838ad9e966a638ac8d3.png)





### VSCode
> **vscode（Visual Studio Code）出自微软之手，以界面简洁，轻量著称**
> 下载地址: [传送门](https://code.visualstudio.com/)


**VSCode的优点**
- 启动超快，相比于Pycharm
- **内存占用小**（没有漫长等待索引过程）
- 界面好看，有着丰富的主题配色

**VSCode的缺点**
- 插件需要安装太多
- 默认不支持python的自动导包功能


**VSCode环境配置**
虽然VSCode支持开发多种语言，但默认并没有配置开发Python插件，因此需要安装Python插件

**具体环境配置步骤**

1. 安装 Python 插件
如图所示安装即可, 安装之后需要重启软件
![在这里插入图片描述](https://img-blog.csdnimg.cn/39e538fc6c924e468e813ea5ccf43c18.png)

2. 选择Python 解释器

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/2c4a47a001d0498c81e82495dc2431f5.png)

3. 点击运行->启动调试. 或者直接输入F5运行程序

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/0eef2fba2d71488ea62b44f1d3e5d5e8.png)







## 3. 虚拟环境
>鉴于virtualenv不便于对虚拟环境集中管理，所以推荐直接使用virtualenvwrapper
> virtualenvwrapper提供了一系列命令使得和虚拟环境工作变得便利
> 它把你所有的虚拟环境都放在一个地方


### 虚拟环境管理工具
#### 安装

**Linux、Unix、MacOS：**
```shell
sudo apt install python-pip
pip install virtualenvwrapper
```
**Windows：**

```shell
pip install virtualenvwrapper-win
```
**注意:**
Windows下, 想要在命令行运行pip 命令需要配置环境变量. 只需在 path 下添加安装后的 python\Scripts 目录即可, 例如 `C:\Program Files\python\Scripts`

![在这里插入图片描述](https://img-blog.csdnimg.cn/d210a3ea99754ed5b0f539cf2d956c8a.png)

#### 相关操作指令
1. 创建虚拟环境

	```shell
	mkvirtualenv env_name
	```
2. 激活虚拟环境

	```shell
	workon env_name
	```
3. 退出虚拟环境

	```shell
	deactivate
	```

4. 删除虚拟环境

	```shell
	rmvirtualenv env_name
	```
5. 操作演示
![在这里插入图片描述](https://img-blog.csdnimg.cn/8cb611c22e064951aed3d121e8fc7b51.png)


### 配置虚拟环境
#### PyCharm 配置虚拟环境
**使用已经存在的虚拟环境**
![在这里插入图片描述](https://img-blog.csdnimg.cn/444bfa19fcf64158bffec1121f8a02f2.png)

**创建新的虚拟环境**

![在这里插入图片描述](https://img-blog.csdnimg.cn/7197074df8144b3e883cc3d0d1093c3f.png)

#### VSCode 配置虚拟环境
**配置方式如下**

1. 打开VSCode设置

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/5ca2f3f43d65439aa9f79d4861eb31bc.png)

2. 筛选 `python venv path`, 输入虚拟环境的地址

    ![在这里插入图片描述](https://img-blog.csdnimg.cn/e55fa71f2bd24ca1a100d45872269127.png)
3. 重启 VSCode


---

# 三. Python 初识
## 1. Python基本格式
 **缩进风格**
 1. 恰当的空格，缩进问题
逻辑行首的空白（空格和制表符）用来决定逻辑行的缩进层次，从而用来决定语句的分组。
 语句从新行的第一列开始。
 2. 缩进风格统一：
 每个缩进层次使用 单个制表符 或四个空格（IDE会自动将制表符设置成4个空格）
    Python用缩进而不是{}表示程序块的层次关系
 3. **Python区分大小写**


## 2. 注释格式

```py
# 测试单行注释
print("这里是单行注释 ")

'''
我是多行注释
三个单引号实现多行注释
作者:
时间：
'''
print('三个单行引号实现多行注释')

"""
三个双引号实现多行注释
作者:
时间:
"""
print('三个双引号实现多行注释')```
```

## 3. 异常处理

```py
# 错误1, 首行是空格
 print("首行不能有空格")

# 错误2, 使用了中文引号
print(“不能使用中文引号”)
```

## 4. Python图形化程序-海龟绘图
> 这里接触到一个好玩的库, 海龟绘图
> 只需导入海龟绘图的库, 即可画图.
> 并且比 java 导入更加简单, 因为Python导入只需要声明库名. 而不需要声明库的具体路径. 奈斯~


**下面首先看一个使用demo**


```py
import turtle

turtle.showturtle()  # 显示箭头
turtle.write("时间静止不是简史")  # 写字符串
turtle.forward(300)  # 前进300像素
turtle.color("red")  # 画笔颜色改为red
turtle.left(90)  # 箭头左转90度
turtle.forward(300)
turtle.goto(0, 50)  # 去坐标（0,50）
turtle.goto(0, 0)
turtle.penup()  # 抬笔。这样，路径就不会
turtle.goto(0, 300)
turtle.pendown()  # 下笔。这样，路径就不会会画出来
turtle.circle(100)  # 画圆
turtle.done()  # 程序结束，保持窗口存在
```
**运行后, 结果如下**
![在这里插入图片描述](https://img-blog.csdnimg.cn/f1e8341e85504e5b9b7be6c508651706.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_20,color_FFFFFF,t_70,g_se,x_16)

---

<font color=red>实操: 照猫画虎, 根据上面库的调用方式, 绘制一个奥运五环图</font>

![img](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fpic.soutu123.cn%2Felement_origin_min_pic%2F16%2F09%2F15%2F2357dabd482fc64.jpg%21%2Ffw%2F700%2Fquality%2F90%2Funsharp%2Ftrue%2Fcompress%2Ftrue&refer=http%3A%2F%2Fpic.soutu123.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1659840874&t=90c0b64fafa7a483550ac4f29bb4b03e)



**思路:**

- 注意画笔大小尺寸以及每个环的颜色设置
- 因为海龟绘图是从圆的最底部开始绘制, 因此要根据这个确定每个圆绘制的起始坐标和圆的半径
- 上三圆绘制大体上是类似的, 下两圆绘制方式也是类似的

**代码**
```py
import turtle

turtle.showturtle()
turtle.pensize(5)          # 定义字体大小
turtle.color("blue")       # 定义画笔颜色
turtle.circle(50)           # 画圆, 半径为50px

turtle.penup()             # 抬笔
turtle.forward(120)        # 前进100px
turtle.pendown()           # 下笔
turtle.color("black")
turtle.circle(50)          # 画第二圆

turtle.penup()
turtle.forward(120)
turtle.pendown()
turtle.color("red")
turtle.circle(50)            # 画第三圆

turtle.color("yellow")
turtle.penup()
turtle.goto(60, -50)              # 第四圆圆心位置
turtle.pendown()
turtle.circle(50)                 # 画第四圆

turtle.penup()
turtle.goto(180, -50)             # 第五圆圆心位置
turtle.pendown()
turtle.color("green")
turtle.circle(50)                 # 画第五圆
turtle.done()                      # 窗口挂起

```

**绘制结果** :
![](https://img-blog.csdnimg.cn/04fbc6feaedc4e92b0b296b4dbb24627.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5pe26Ze06Z2Z5q2i5LiN5piv566A5Y-y,size_20,color_FFFFFF,t_70,g_se,x_16)



# 结语

> 在原有博文基础上, 为了增添趣味性, 打算在结尾书写一点点小故事.  让学技术也有种玩游戏升级打怪的感觉. 以此来为学习技术增加动力和积极性
> 因有感而发, 之前未有相关经历, 文笔拙略请大家包涵 ~~~ 如不感兴趣, 请跳过此部分内容即可.



> 这是一个叫阿拉德大陆的地方, 这里拥有魔兽遍地的密林, 也有直插入天空的城堡; 有万年不化的雪山, 也有科技发达的"天界"...
>
> 一天, 一个名叫tp冒险家想要赶往下一个城市的时候. 不幸勿入一个叫格兰之森的森林. 随着不断的深入, 开始出现一种名为哥布林的魔兽.
> 想到这, 选择踏上 Python 这个职业的tp, 念动了咒语: **Python 是一个让你工作更快速并且更高效集成系统的编程语言**, 法杖击中怪物, 怪物应声而倒.
> 继续往前走, 又遇到了一种叫猫妖的魔兽, tp一看不妙, 把**Python运行环境搭建**读了一遍. 只看到法杖散发金光, 向上一挑, 怪物便被击飞十几米后倒地不起.
>
> 在快走到森林深处的时候, 突然一阵巨响, 一只巨大的牛头怪(牛头巨兽)冲进来. 然后tp冲去. tp来不及躲闪, 转眼间便挂彩.
> 看着牛头巨兽攻势越发凶猛, tp不紧不忙, 举起手中法杖念动咒语: 将Python 基本格式, 注释方式, 以及简单异常处理大声朗诵.
> 只见, 法杖前面汇集点点星光聚成一团, 纷纷向牛头巨兽飞去(这一招名为魔法星弹), 牛头巨兽一时间血量大减. 但是在濒死之际的时候, 突然狂化了起来.
> tp见状, 回想起之前**学习海龟绘图使用方法, 在脑海里利用其api默默实现一个奥运五环图**, 只见空气中凭空汇集出一个万圣节的南瓜头(哇, 无吟唱魔法!)向牛头巨兽冲去, 瞬间牛头巨兽暴毙而亡. 而 tp 四周一片金光环绕,  头顶上显示: lv0 -> lv1 , 0的突破!!!



---
Python 开发环境相关软件
链接：https://pan.baidu.com/s/1U-5n3vrf4M3D8NTaTlTpmQ?pwd=w6bo
提取码：w6bo
