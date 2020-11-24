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
* Set的定义：使用一个list来进行定义，形如set([])来进行定义.（需要注意一点，之前的定义我们都是使用符号就可以完成定义，但是这里我们使用了一个函数`set`来进行定义，他的参数是一个`list`才行。）
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

  NB:参数检查，Python不会检查数据类型对不对，指挥检查参数的个数。但可以使用函数`isinstance(variable,(typelist))`来进行检查

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

#you can choose every two 
  tuple_name[index1:index2:from_every_count]
  ```
  

#### 2.2 迭代

* `Python`和其他语言的迭代：`Python`中的迭代不仅可以用于`List`或者`Tuple`中，可以用于一些其他的可迭代的对象上。

* `Python`中的迭代

  ```python
  #1.iteration in dic
  #it will get the key automatically
  score_table={'renyanjie':100,'hanrongze':99,'cuihaida':97,'zhaozehua':90}
  for key in score_table:
      print(key)
  #2. iteration in set
  #it will get every single value in the set
  score_table=set(['renyanjie','hanrongze','cuihaida','zhaozehua'])
  for key in score_table:
      print(key)
  
  ```

#### 2.3 列表生成

* ```python
  #Use for structure to generate a special list
  result_list = [x*x  for x in range(1,11)]
  for j in result_list:
      print(j)
  #use two iteration
  [m + n for m in 'ABC' for n in 'XYZ']
  #use if to select the elements
  #!/bin/python3.7
  result_list = [ x for x in range(1,11) if x%2==0 ]
  for j in result_list:
      print(j)
  ```

#### 2.4 生成器

* 生成器和列表生成：列表生成的方法会生成我们需要的列表，但是在一些场合里这样非常浪费空间。生成器只保存元素生成的逻辑而不实在地生成元素。

* 生成器的语法：

  ```python
  #use () instead of []
  result_generator=(x for x in range(10))
  
  #get the element of generator
  #warning:every generator has a static pointer which
  #indicates the element of the list
  next(generator_name)
  
  #use for structure to get element
  for x in generator_name:
      print x
   
  #Error log:if generator can not get next element
  #it will throw a stopiteration error.
  ```

* 用函数定义一个生成器：

  ```python
  #if a function defination contains the keyword yield,then this function is generator function
  #Specially,every time you call the next function
  #the function will be executed.it returns when it meets the yield keyword.And next time it will continue from the yield keyword.
  #Once a function is defined as generator.you almost never will get the return value of it.If you really need it.You can use StopIteration.value
  ```

  

#### 2.5 迭代器

* Iterable和Iterator:可以被for循环直接迭代使用的是Iterable的，可以使用next调用返回元素的是Iterator.

#### 2.6 高阶函数

* 高阶函数：将指向函数的变量作为参数出入另外一个函数，这个就叫高阶函数

  ```python
  def add(x, y, f):
      return f(x) + f(y)
  
  print(add(-5, 6, abs))
  ```

#### 2.7 map/reduce/filter/sorted

* map:有点类似于C++中的for_each的函数使用。它的第一个参数是一个函数，第二个参数是一个list.返回的是一个generator.可以使用list函数得到对应的list.

  ```python
  >>> def f(x):
  ...     return x * x
  ...
  >>> r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
  >>> list(r)
  [1, 4, 9, 16, 25, 36, 49, 64, 81]
  ```

* reduce:有点类似于C++中的accumulate函数，可以用来实现对元素的累计操作，第一个参数是一个函数，第二个参数同样是一个list.其中第一个函数必须能够接受两个参数。
* filter:类似c++中的一个函数，具体是什么我忘记了。接受两个参数，第一个参数是一个判断函数，第二个参数是一个list.
* sorted：函数可以对list进行排序，同时它可以指定key参数，则list会先被key所指定的函数作用，然后再进行排序。如果需要反向输出，可以指明Reverse=True.

#### 2.8 匿名函数

* 匿名函数：也就是lambda函数直接使用。

  ```python
  map(lambda x:x*x,[1,2,3,4])
  ```

#### 2.9 Decorator

* Decorator的作用：不改变原来的函数的功能基础上，新增一些功能。利用函数参数，可以很容易实现这个功能，新定义一个函数，这个函数执行原来的函数而且新增一些功能。

* @语法：在函数上面增加一行注释，即表示使用某一个装饰者来处理它。例如如下的语法

  ```python
  @log
  def now x
  	print x
  #======等价于=======#
  now=log(now)
  ```

  

#### 2.10 偏函数

* 偏函数：偏函数的存在是为了解决需要大量调用一些固定参数的函数调用的问题。例如一个函数有两个参数，其中一个参数是可变的，另外一个是不变的。如果不使用偏函数，就需要大量地写如下的程序。使用偏函数就可以把第二个参数给固定住。

  ```python
  fun(ar1,ar2=const)
  fun(ar1,ar2=const)
  fun(ar1,ar2=const)
  fun(ar1,ar2=const)
  ```

* 偏函数的使用方法：

  ```python
  import functools
  new_func=functools.partial(init_func,arguname=const_val)
  #If you do not want to use the set-value.you can also call the function while specifying the argument value.
  ```

### Day 3 面对对象编程

#### 3.1 Python的文件目录

* 模块：一个py文件就是一个模块。
* 包：包中有不同的模块。但是需要注意的是，一个包（文件夹）中必须有一个__init__.py文件；包本身也是一个模块，但是它实际对应的是底下的`__init_`文件
* 

#### 3.2 Python安装第三方模块

* pip:安装Python第三方模块的工具,一般来说第三方库都会在Python的官方网站www.pypi.python.org注册。

  ```shell
  pip3 install package_name
  ```

* Anaconda:基于Python的数据处理和科学计算平台，而且它内置了很多常用的第三方库。该软件会将第三方模块安装在自己的目录下，不影响Python

#### 3.3 Python类

* 类的定义：

  ```python
  class class_name(baseclass_name)
  #if no base class needs to be specified.use object which is the base class of all the classes.
  ```

* 类的使用：

  ```python
  instance_name=class_name()
  ```

* 类的构造函数

  ```python
  #the first argument of __init__ method must be self like all the functions in classes.
  def __init__(self,arg1,arg2...)
  	...
      ...
  #Once we define the init function.
#The concerning arguments are forced to give
  ```
  
* Python类新绑定变量

  ```python
  #!/bin/python3.7
  class student(object):
      def print_info(self):
          print('This\'s a test infomation')
  renyanjie=student()
  renyanjie.print_info()
  student.name='xiaohong'
  print(renyanjie.name)
  
  #Class variable and instance variable
  #!/bin/python3.7
  class student(object):
      name='xiaoming'
      def __init__(self,name):
          self.name=name
  
  #The access to variable __name is prohibited.The following example shows the use of class variable and instance variable.
  s=student('xiaohong')
  print(s.name)
  s.name='xiaogang'
  print(s.name)
  print(student.name)
  #you can use del keyword to delete the variable of instance
  del s.name
  print(s.name)
  #But you can use function to get access to the variable beginning with __
  #Cause in this case,we are not trying to get access to the variable directly.
  #On the  other hand,we use the function of instance which does not violate the rule.
  ```

* Python类的访问限制

  ```python
  #By default,we have access to the all the variables of class.But in some other cases,we do not want the capsulation erupted.That's how the access limit is introduced.
  #The rule of access limit is simple.
  #Name a variable beginning with __.
  
  #!/bin/python3.7
  class student(object):
      def __init__(self,name):
          self.__name=name
          print('This\'s a test infomation')
      def get_name(self):
          return self.__name
  
  #The access to variable __name is prohibited:error:do not have the attribute __name.
  renyanjie=student('xiaohong')
  print(renyanjie.__name)
  
  #But you can use function to get access to the variable beginning with __
  #Cause in this case,we are not trying to get access to the variable directly.
  #On the  other hand,we use the function of instance which does not violate the rule.
  
  print(renyanjie.get_name())
  
  #Actually,the python intepreter will transfer this kindof variable to _classname__vaialename.But please do not use variable this way.The example is as follow.
  renyanjie=student('xiaohong')
  print(renyanjie._student__name)
  
  #Finally let's see another mistake use of private variable.Since the __name variable has been change into _student__name,what you have done is just to add a new variable for the instance which's name is '__name'
  renyanjie=student('xiaohong')
  renyanjie.__name='xiaohonghong'
  renyanjie.__name
  
  #Addtion:
  #As usual,we assume the variable beginning with only one '_' is pricate.
  #Although you can indeed get access to them.But that's a bad access.
  #Besides,variable like __variale__ is special which can be accessed direcly.
  
  ```

* 多态：

  ```python
  #Generally speaking,the child class will be regarded as the father class.(But it is not permitted inreturn).And in this case,we can use the function direcly,and do not need to care what function will be executed.like this:
  class Animal(object):
      def run(self):
          print('animal is running')
  class Dog(Animal):
      def run(self):
          print('Dog is running')
  def print_run(animal):
      animal.run()
  
  little_dog=Dog()
  print_run(little_dog)
  
  #The descriptions above are polymorphism for the static language.Since python is a dynamic language,it is more free:python even do not check if the argument type is the class type.it only care if the argument has a memeber function called run.
  
  #Althoug python is so free,sometimes we still need to figure out a datatype of a variable.we use instance function.
  
  little_dog=Dog()
  print(isinstance(little_dog,Dog))
  print(isinstance(little_dog,list))
  
  #For the unknown type.we use type function.Especially,sometimes we need to judge the type of variable dynamically,the following constants may be useful.str,int
  type(123)
  ```

* 获取一个类的详细信息：

  ```python
  #Get all the variables and functions of a class.
  #Particularly,the variables and functions like __name__ have special application.
  #For the function:__function_name__
  #the python will transfer function_name(obj) to obj.__function_name__.That means if we want rewrite len function logic,we just need to write function called __len__ in our class which is very convenicent and elegant.
  print(dir(little_dog))
  '''['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'run']
  '''
  #Atrribution
  #hasattr():to juedge
  #getattr():to get the value of attr
  #setattr():to set the value of attr
  ```

#### 3.4 Python类高级特性

* slot:

  ```python
  #we can use a __slot__ variable of a class to restrict  all the variables the class could use.
  #PS:__slot__ variable is only effective for the current class,not for the sub class.But Specially,if sub class also defined the __slot__,then the base __slot__ will be effective.
  class student(object):
      __slots__=('age','name')
      def __init__(self,name,age):
          self.name=name
          self.age=age
  s=student('xiaoming',13)
  #since gender is not defined in the slots,the following action is prohibited
  s.gender='male'
  
  ```

* Useful Decorator:

  ```python
  #Fisrly,we will show the use of property and setter.
  #First all all,the @propery and @variable_name.setter are used together.Only When you use @property decorator,another corresponding decorator will be established.That means you can use the @property decorator single.but you can not use  variable.setter decorator single.(And in that case,it will be a readonly attribute)
  #Here are some points you have to obey
  #1.The getter and setter function got the same name.
  #2.One is @property.Another is @variable.setter
  #3.As usual,the function name is the same with the variable.
  #!/bin/python3.7
  class student(object):
      __slots__=('_age','_name')
      def __init__(self,name,age):
          self._name=name
          self._age=age
      @property
      def age(self):
          return self._age
      @age.setter
      def age(self,new_age):
          self._age=new_age
  s=student('xiaoming',13)
  print(s.age)
  s.age=14
  print(s.age)
  ```

#### 3.5 多继承

* 多继承：多继承是指一个类继承自多个父类。

  ```python
  #runable and flyable class are both father class of dog.
  #Traditionaly,we call this kind of inherition mixln
  class dog(runable,flyable):
      pass
  ```

#### 3.6 定制类

* \_\_str\_\_:为一个类实现一个\_\_str\_\_函数，即可在使用print函数的时候自动调用该函数，返回我们所需要的字符串即可。非常方便。

  ```python
      def __str__(self):
          return 'student:%s,age:%d' %(self._name,self._age)
  s=student('xiaoming',13)
  #print(s.age)
  #s.age=14
  #print(s.age)
  print(s)
  ```

* \_\_repr\_\_:该函数会在interactive mode中输入对应的对象的时候被调用，输出到控制台中，也即可以认为该方法是专门给调试人员使用的，而不会输出到标准输出。

  ```python
  >>> import advanced_feature
  student:xiaoming,age:13
  ```

* \_\_iter\_\_:该函数会在next该实例的时候返回对应的结果值

* \_\_getitem\_\_:该函数会在使用`[]`的时候自动调用，该方法和上面的方法搭配使用
* \_\_getattr\_\_:一般来说，如果一个对象不存在某个方法，那么会报错，但是在一些特殊的情况下，我们希望即使不存在这个也要返回一个值。在这种情况下，可以重写\_\_getattr\_\_方法，这样在找不到对应的属性的时候，就会调用这个方法。除此以外，拓展地说，我们可以使用该方法来处理一些复杂的请求，进行请求的转发。
* \_\_call\_\_:重写该方法可以使得调用实例本身。

#### 3.7 枚举类型

* 枚举类：枚举类是库函数中的一个类，我们可以直接传入参数，这样它就拥有一些标签，返回一个拥有对应标签的实例。每一个标签其实还有一个整数值对应，从1开始计数。

* 自定义枚举类：自定义枚举类其实是完全OK的，（无非打印的时候不太舒服而已），但自定义的时候一定要注意不同的标签值不同。

* 使用unique装饰器：unique是一个装饰器，可以保证成员的值互不相同。该装饰器必须和`enum`类搭配使用

  NB：其实使用默认的类就可以了，标签也不会重值,下面给出用法

  ```
  #!/bin/python3.7
  from enum import Enum,unique
  
  Workday=Enum('day',('Mon','Tue','Wed','Thur','Fri'))
  print(Workday.Mon)
  ```

#### 3.8 动态类

* type:type不仅可以对变量类型的识别，还可以动态地创建类。它接受三个参数，分别是类名、父类、函数绑定

* metaclass:类是实例的模板，metaclass是类的模板。它的使用如下：

  ```python
  # metaclass是类的模板，所以必须从`type`类型派生：
  class ListMetaclass(type):
      def __new__(cls, name, bases, attrs):
          attrs['add'] = lambda self, value: self.append(value)
          return type.__new__(cls, name, bases, attrs)
  ```

  https://stackoverflow.com/questions/100003/what-are-metaclasses-in-python

#### 3.9 错误处理

* 错误捕捉：先执行try中的代码，如果出现预期之中的错误，那么就执行expect后的代码，最后执行finally后面的代码。finally是可选的.

  ```python
  try:
      ...
      ...
  expect error_type as var_name:
      ...
      ...
  expect error_type as var_name:
      ...
      ...
  expect error_type as var_name:
      ...
      ...
  else:
      ...
  finally:
      ...
      ...
  ```

* 错误捕捉的trick:所有的错误都继承自BaseException.但是不同的Exception之间也是有继承关系的，这就容易造成捕捉的短路。常见的错误类型和继承关系见：

  https://docs.python.org/3/library/exceptions.html#exception-hierarchy

* 错误捕捉的层次：错误会不断地循着函数的调用栈往上抛，直到到Python的解释器为止，打印出来一个错误信息。
* logging:logging是Python内置的一个函数，可以帮我们记录错误，让程序继续执行下去。
* 抛出错误：我们可以使用raise关键字抛出一个错误的实例即可，如果raise后面不加参数，就会把当前的错误原样抛出。

#### 3.10 调试

* 断言：

  ```python
  assert a!=0,'n is zero'
  #we can turn off the assert by using the option -O
  ```

* logging:使用logging可以控制输出信息的级别,只需要通过配置即可

  ```python
  logging.basicConfig(level=logging.INFO)
  '''
  level=logging.INFO
  level=logging.DEBUG
  level=logging.WARNING
  level=logging.ERROR
  '''
  ```

* 使用pdb:引入pdb.直接pdb对应的Python文件

  ```shell
  pdb test.py
  b line
  b function_name
  r #run till the next breakpoint
  c #continue till the next breakpoint
  n #next step
  
  ```


<<<<<<< HEAD
#### 3.11 测试

* 单元测试：继承自unittest.TestCase类，定义好test函数（务必以test开始），最后调用unittest.main()函数即可对所有的函数自动执行

  ```python
  #!/bin/python
  import unittest
  from algo import *
  #The functions starting with test will be regarded as test functions
  class test_algo(unittest.TestCase):
      def test_sum(self):
          self.assertEqual(local_sum(1,2),3)
      def test_mus(self):
          self.assertEqual(local_minus(2,1),0)
  ```

* setUp和tearDown方法:这两个方法会在每一个test方法之前和之后被调用

  ```python
  def setUp(self):
          print('setUp...')
  
  def tearDown(self):
          print('tearDown...')
  ```

* 文档测试：调用doctest.main方法就可以直接提取注释中的示例进行运行

#### Day 4: IO 

#### 4.1 IO基础概念

* 输入输出流：输入和输出流可以看作是两个单向的水管。数据就是流在其中的水。
* 同步IO和异步IO：IO中的速度不匹配，水管两端的水管粗细不同（这样即使水流的速度相同，流量也是不同的）。由于传完数据之后两者还需要有一些其他的操作，这个时候就存在两种方法：一种是快的一直等着，效率低下。另外一种方法是快的先做另外一些事情，等到收完了之后通知快的继续干活，或者轮询的方法。

#### 4.2 文件读写

* 文件读写的代码模板：

  ```python
  with open('/path/to/file','r') as f:
      print(f.read())
  #the code above is equal to the code following
  #in sum,it will close file automatically and handle the exceptions、
  #you can use the rb option to open a binary file
  #you can use the encoding option to open a file with specified encoding format
  #you can use the w option to write to files
  #you can use a option to append file
  try:
      f = open('/path/to/file', 'r')
      print(f.read())
  finally:
      if f:
          f.close()
  ```

* 文件读写的不同方法：

  ```python
  #without argu it will read all the bytes and return a str
  f.read()
  #argu will specify the bytes it reads
  f.read(byte_size)
  #this function will read a single line
  f.readline()
  #this function will read all the lines and return a list
  #file-like object:拥有read方法的对象都叫做file-like object.
  ```

#### 4.3 StringIO

* StringIO：StringIO可以认为是存放在内存中的文件。使用之前需要从io模块中引入StringIO。

  ```python
  
  ```

  
=======
#### Day 4 IO和进程

#### 4.1 StringIO

* StringIO:StringIO允许我们在内存中新建一个StringIO对象并且对这个String进行读写.和自定义的String进行读写不同，StringIO是一个活动的对象，我们可以向该对象输出，也可以进行输入（但是需要注意输入不等于直接读自己写的内容），这就像水流，流过去就是流过去了，只有接收方才能收到。

  ```python
  from io import StringIO
  f=StringIO()
  #IO Write
  f.write('test')
  print(f.getvalue())
  
  #you can also read from stringIO like this
  while true:
      s=f.readline()
      if s=='':
          break
      print(s.strip())
      
  ```

#### 4.2 ByteIO

* ByteIO:和StringIO类似，ByteIO是按照对应的是将二进制数字直接写入的。

  ```python
  from io import ByteIO
  f1=BytesIO()
  f1.write('Test'.encode('utf-8'))
  print(f1.getvalue())
  f1.read()
  ```

#### 4.3 os类

* name变量：识别出操作系统的信息

  ```python
  import os
  print(os.name)
  ```

* uname函数:识别出操作系统的详细信息

  ```python
  os.uname()
  ```

* getpid函数：获取当前进程的pid

  ```
  os.getpid()
  ```

  

* env变量：操作系统的所有的环境变量,使用该变量你可以获取到很多有用的信息.而通过指定get方法我们还可以获得对应的具体的变量的信息。

  ```python
  #get all of the environment variables
  os.environ
  #get a specified environment variable value
  os.environ.get('PWD')
  os.environ.get('PATH')
  os.environ.get('LOGNAME')
  os.environ.get('SHELL')
  ```

* 目录操作:

  ```python
  #print the abs path of a relative path
  os.path.abspath('.')
  os.mkdir('./testdir')
  os.rmdir('./testdir')
  #handle the different os issue:the seporators are different in different os.join and split will handle this issue well.
  os.path.join('.','test')
  #this function will split according to path
  os.path.split('/home/use/michale.txt')
  #this function will split according to text(by punc)
  ```

* 文件操作

  ```python
  #rename
  os.rename('src.txt','des.txt')
  #remove
  os.remove('test.txt')
  #The following functions will be found in module 	shutil
  ```

#### 4.4 序列化

* 序列化：所谓序列化就是将内存中的数据变为可存储、传输的数据。反序列化就是将这些数据恢复到内存中。在Python中分别叫做`pickling`和`unpickling`.

  NB:对于对象这些数据是不能直接进行存储和传输的（因为是一个指针），所以需要序列化。序列化是一个很常见的概念，在不同的语言中都有所实现例如Java中的serialization，marshalling,flattening.

* pickle模块：Python中用来实现序列化的模块的名字叫做pickle.下面是pickle模块的一些方法的使用

  ```python
  import pickle
  d=dic(name='Bob',age=20,socre=80)
  #dumps function:will transfer an object to bytes array.
  pickle.dumps(d)
  #dump function:will transfer transfer an object to bytes array and then stream out to a file-like object.
  
  #Reversly,we can use loads and load function to read from bytes or file-like object
  pickle.loads(bytes_array)
  pickle.load(file_like_object)
  ```

* 序列化的不足：序列化只能用于Python，兼容性不够（甚至不同版本的Python也不能很好地兼容）。因此考虑兼容性，可以将数据存放在xml或者json文件中。

#### 4.5 JSON

* JSON:Json是一种语言格式，目的是用于存储数据（或者叫做信息）。json不属于任何一种语言，有自己独立的标准，因此可以在不同的编程语言之间传递数据。

* Json的对象：json所表示的对象就是标准的javascript的对象。他们之间的对应关系如下图所示

  | JavaScript |    Python    |
  | :--------: | :----------: |
  |     {}     |     dict     |
  |     []     |     list     |
  |  “string”  |     str      |
  |  1234.56   | int or float |
  | true/false |  True/False  |
  |    null    |     None     |

  

* json模块：

  ```python
  #use json module
  import json
  #@argu:a python object
  #@return:standard json string
  json.dumps(dict_object)
  #@argu:a python object
  #@return:standard json string
  json.dump(dict_object,file_like_object)
  #@argu:a python object,a file_like object
  #@return:standard json string
  json.dump(dict_object,file_like_object)
  #@argu:json str
  #@return:python object
  json.loads(json_str)
  #@argu:file_like object
  #@return:python object
  json.load(file_like_object)
  
  #To transfer any kind of python object to json
  #we need to tell the json module how to transfer a python object to json.(the rules)
  ```

  [the json module:how to transfer between json file and python object]: https://www.liaoxuefeng.com/wiki/1016959663602400/1017624706151424

  

>>>>>>> fe6fc2aa2dd1346290f93da7336c778cebb8dc86
