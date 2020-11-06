# Python 自学笔记

### Day 1:Python 入门与安装

#### 1.1 Python简介

* Python的发明：Guido Van Rossum于1989年圣诞节开发的一门编程语言。

* Python的优缺点：Python拥有丰富的基础代码库，在开发网络应用的时候很有优势。但是由于Python是解释型代码，因此运行起来非常的慢。同样因为这个原因，Python的程序发布的时候必须发布源代码。

  **NB:传统的语言例如C语言的源代码会经过编译器转换成为对应的机器码，因此CPU执行的时候只需要执行对应的机器码即可，而Python则是边执行变转换为机器码，耗费时间。**

#### 1.2 Python的解释器

* Python的解释器和代码文件：上一小节我们提到，Python是边执行边转换，因此Python程序的执行必须依赖于**解释器**。（这一点和C不同，C程序不见得必须有C的编译器才行）。Python的源代码文件以.py结尾。
* 不同的Python解释器：
  * CPython:因为是使用C代码写的，所以叫做CPython.它也是目前最流行的解释器
  * IPython:基于CPython的交互式解释器，新增加了交互功能。CPython使用>>>作为提示符，IPython使用In作为提示符
  * PyPy:类似于一个编译器的存在，显著提升执行效率
  * JPython和IronPython:将Python代码分别转换成JAVA的字节码和.NET字节码

#### 1.3 Hello World

* 代码：直接编辑好如下的`Hello.py`文本文件，调用`python hello.py`即可运行

  ```python
  print('Hello')
  ```

* 语法规定：
  * 文件必须使用.py结尾
  * `print`前面不能有任何的空格

* 直接运行`py`文件：在`Unix-Like`终端中，只需要在代码的第一行填写如下的文本即可直接运行`#!/bin/env python3`即可

#### 1.4 输出函数print

* 字符串输出：输出函数`print`字符串使用单引号框住表示字符串（不同于C语言的双引号）。字符串可以分别输出多个，但会以空格隔开
* 整数输出：直接加入待输出的整数，这个整数可以是一个整数表达式
* 变量：`print(variable)`来对变量进行直接打印
* 对字符串的格式化输出：`%? %? %(decimalnum1,decimalnum2)`.特别地，%s可以将任意的数据类型转化为字符串。除此以外，可以使用`f`开头的字符串，它会自动识别其中的`{}`起来的变量，并且使用对应的值进行替换。

#### 1.5 输入函数input

* 字符串：可以直接使用`variable=input()`类型的方式来对一个字符串变量进行输入。同时还可以直接输入变量的名字来检查该变量的内容。
* 输入函数的`Prompt`功能：可以在`input`函数中传入一个字符串参数来作为输入的`Prompt`功能
* input函数返回的数据类型：默认是字符串类型。如果需要进行整数的转换，可以使用int函数。

#### 1.6 Python中的数据类型

* 整数：Python可以处理**任意**大小的整数。除此以外，为了方便用户查找，Python允许用户在数字中间以下划线隔开不同数字。

* 浮点数：支持常见的浮点数。而且支持科学计数法表示（以e表示10）。

  NB：浮点数在计算机中的表示是不准确的，但是整数则是准确的

* 字符串：可以是单引号或者双引号括起来的任意文本。为了表示引号本身，可以使用转义字符`\`。如果有大量的需要转义，则可以使用`r''`把他们括起来。

  NB：可以使用`'''...'''`来表示换行

* 布尔值：可以使用`True`和`False`来表示对应的布尔值。布尔值有对应的运算符`and /or/not`运算。
* 空值：空值是一个特殊的值，而非零
* `byte`类型：可以使用带`b`前缀的单引号或者双引号表示。

#### 1.7 Python中的变量

* 变量可以是上述数据类型的任何一个值
* Python中的变量是动态的，变量有数据类型，但是它的数据类型是由上一次赋值的值决定的，变量可以被不同的数据类型赋值
* Python中的变量都是指针，因此变量之间的互相赋值实际上是地址的互相赋值

#### 1.8 Python中的除法

* Python中的除法有两种
  * `/`是浮点数的触发，结果一定是浮点数
  * `//`是整数触发，和C语言中的触发相同

#### 1.9 Python中的字符串编码

* Python的编码：最新的Python3使用的是Unicode编码。具体地，针对单个字符，`ord`函数获取字符的编码，而`chr`函数则可以让编码转化为对应的字符。

NB：常见的编码有`ASCII/Unicode/UTF-8`编码。`ASCII`编码略过不讲，主要谈一谈`Unicode`码和`UTF-8`编码。`Unicode`码也叫做万国码，是对世界上所有的语言都使用统一的编码来表示（包括英文，只是只需要在前面添加零即可）。`UTF-8`编码则是一种变长的编码，节约了内存空间。计算机系统中处理的方式是这样的，内存中统一使用`Unicode`码（因为方便），当需要写入硬盘、传输的时候就是用`UTF-8`编码。

* 字符串中的编码：在字符串中可以使用`\ucode`来表示对应的字符。不过字符默认是十六进制的。、
* 指明对应的编码：在第二行写下`#-*- coding:utf-8 -*-`.而且必须保证你的编辑器使用的是`UTF-8 without BOM`编码的

#### 1.10 有序集合 List

* `List`的定义：`Variable_name = [ele1,ele2,ele3...]`

* `List`的长度：可以使用`len`函数来检测对应的`List`的长度

* `List`的元素访问：和C相同，下标从零开始。特别地，我们可以直接使用`-1`来访问最后一个元素。以此类推，我们可以使用`-2`表示倒数第二个元素。

* `List`的末尾元素的添加：使用`append`函数来对元素进行追加。

* `List`的元素插入：可以使用`insert`函数来对元素进行插入，`test_list.insert(n,ele)`.直接将元素`ele`插入到索引号为1的位置（原来索引号为1的元素自动变成索引号为2的元素，以此类推）。

* `List`的元素弹出：删除最后一个元素，使用`List`的`pop`函数。

* `List`的指定位置的元素的删除：使用`pop(i)`函数来删除索引位置为`i`的元素，原来索引位置为`i+1`的元素自动成为索引为`i`的元素。

* `List`的元素的替换：可以直接赋值给对应的元素即可

  NB：List元素的值的类型可以不同，List元素可以是另外一个List.

#### 1.11 固定数组Tuple

* Tuple简介：Tuple和List非常类似，都是一种线性表。但是不同的地方在于，Tuple一旦被定义出来之后就不能被再次的赋值和修改（这也意味着Tuple必须在定义的时候就必须定义完整）。

* Tuple的定义：使用`()`来对Tuple进行定义。如果定义一个空的Tuple可以使用如下的操作

  ```python
  test_tuple=('a',1,'abc')
  ```

  NB:特别地，在定义一个元素的Tuple的时候，必须在元素末尾加上一个,以免误解。

#### 1.12 条件判断

* 条件判断的基本格式

  ```python
  if expression :
      something1
      something2
  elif:
      something3
      something4
  else:
      something5
  ```

* 条件判断的几个要点：
  * 冒号：在`if/elif/else`后面都必须跟上一个猫好
  * 缩进：Python根据缩进来进行判断和执行，例如somthing1和somthing2实际上实在一个block中的。
  * 短路：在一个大的if语句中，一旦满足条件，后面的都不再执行。

#### 1.13 循环

* 循环的`for in `结构：取出每一个List或者Tuple中的元素执行下面的语句。除此以外，为了方便程序的书写，Python提供了一个range(n)来生成一个序列。这个序列可以通过list函数来进行转化。

  NB：range(100)会生成0-99的序列，而非是1-100哦

* 循环的`while`结构：不断地进行判断，直到不满足条件

#### 1.14 Dict

* Dict简介：Dict就是C++中的Map.

* Dict的定义：同样使用{}来进行定义，Key和Map使用:来进行分割。

* Dict的取值：Dict_Name[Key_Value]来进行取用

* Dict的判断：Key in Dict_Name.返回一个布尔值或者也可以使用get方法，这个方法可以自定义报错返回值。

  NB：Dict中的Key值必须是一个不可变对象

#### 1.15 Set

* Set:同C++中的Set.不能有重复的元素
* Set的定义：使用set([])来进行定义
* Set的元素添加和删除：使用add函数来进行添加，使用remove函数来进行元素的删除
* Set的元素运算：
  * 交集：&
  * 并集：|

#### 1.16 函数初步

* 查看函数的详细信息：类似于Linux中的man.Python可以调用help(function_name)来实现对函数的信息的查找。
* 函数的引用：完全可以使用`variable_name=function_name`来实现函数别名的效果。

#### 1.17 自定义函数

* 自定义函数的基本语法格式：

  ```python
  def function_name(argumentlist)
  	(tab)
      function body
  ```

* 自定义函数的调用

  ```python
  from file_name import function name
  ```

  NB:`pass`关键字表示什么也不做。如果没有pass,有的地方就会报错

  NB:参s数检查，Python不会检查数据类型对不对，指挥检查参数的个数。但可以使用函数`isinstance(variable,(typelist))`来进行检查

  NB：`Python`可以返回多个函数值（实际上是一个tuple)

#### 1.18 函数进阶：函数的参数

* 默认参数：同C++。需要注意以下几点：必选参数在前，默认参数在后；当有多个默认参数的时候，可以按顺序提供，也可以使用=连接，就不必按顺序提供参数；默认参数本身是一个变量，在定义的时候就被定义出来了。
* 可变参数：定义的时候前面加上*即可。这样函数就不会检查参数的个数问题。可以使用\*加上Tuple或者List来把一个Tuple变成可变参数。
* 关键字参数：定义的时候使用**即可。使用的时候，必须使用Key=value的样式。在函数内部自动组装成一个Map.

### Day 2 Python高级特性

#### 2.1 切片

* 切片：Python中方便地取出List或者Tuple中的索引范围内的N个元素

* 使用：

  ```python
  #index denote the index of the first element
  #number denote the number of elements you want
  list_name[index_left,index_right]
  
  #Specially,you can use the negative index.
  #It looks like this.
  #0   1  2  3  4 
  #-5 -4 -3 -2 -1
  ```

  