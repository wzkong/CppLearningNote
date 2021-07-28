# Python

[TOC]

## Day1

注释

```python
"""
多行注释
"""

#单行注释
```

## Day2 语言元素

运算器、控制器、存储器、输入设备和输出设备

冯·诺依曼结构：存储设备与中央处理器分开；二进制方式编码

### 变量和类型

* 整型
* 浮点型：123.456和1.23456e2
* 字符串型
* 布尔型：True和False
* 复数型：1+2j

#### 变量命名：

跟cpp差不多

字母、数字和下划线，数字不能开头

大小写敏感

PEP8要求

* 小写字母拼写，多个单词用下划线
* 受保护的实例属性用单下划线开头
* 私有实例属性用两个下划线开头

```
type()

int()
float()
str()

#占位符
%d整数，%f小数，%s字符串
```

运算符

![image-20210407204312563](Python.assets/image-20210407204312563.png)

\ 可以中断某一句话

## Day3 分支结构

### if语句

```
#if elif else
#能扁平化就不要嵌套
```

## Day4 循环结构

### for-in循环

```
range(101) 0~100
range(1, 101) 1~100
range(1, 101, 2)
range(100, 0, -2) 100到1中的偶数
```

#### while循环

```
while True:

break中断循环
continue跳到最后
```

## Day5 构造程序逻辑

1.寻找水仙花数

2.正整数反转

3.百钱百鸡问题

 4.CRAPS赌博游戏

生成斐波那契数列的前20个数。

找出10000以内的完美数。

输出100以内所有的素数。

## Day6 函数和模块的使用

### 函数：

#### 定义函数：

```
def fac(num):
	return
```

#### 函数的参数

```
#可默认
#可不按照设定的顺序
#不确定参数时，多个参数。args的名字可以变的
def add(*args):
    total = 0
    for val in args:
        total += val
    return total
```

### 模块：

#### 用模块管理函数

解决重名的问题，后导入的会覆盖前面的

**如果导入的模块除了定义函数之外还有可执行的代码，导入模块时就会执行这些代码，所以我们用**`__main__`

```
def main():
	pass
	
if __name__ == '__main__':
	main()
```

### 变量的作用域

跟Cpp大致一致

```
global #就可以修改函数外的量，但是最好别用
nonlocal #来自嵌套域
```

## Day7 字符串和常用数据结构

### 字符串：

```
s1 = 'hello, world!'
s2 = "hello, world!"
# 以三个双引号或单引号开头的字符串可以折行
s3 = """
hello, 
world!
"""
print(s1, s2, s3, end='')
```

**转义序列**，如果不想转义用r

```
#运算符
#使用*运算符来重复一个字符串的内容
s1 = 'hello ' * 3
#+
s1 += s2
#可以使用in和not in来判断一个字符串是否包含另外一个字符串
print('ll' in s1) # True
print('good' in s1) # False

str2 = 'abc123456'
# 从字符串中取出指定位置的字符(下标运算)
print(str2[2]) # c
# 字符串切片(从指定的开始索引到指定的结束索引)
print(str2[2:5]) # c12
print(str2[2:]) # c123456
print(str2[2::2]) # c246
print(str2[::2]) # ac246
print(str2[::-1]) # 654321cba
print(str2[-3:-1]) # 45
```

```
str1 = 'hello, world!'
# 通过内置函数len计算字符串的长度
print(len(str1)) # 13
# 获得字符串首字母大写的拷贝
print(str1.capitalize()) # Hello, world!
# 获得字符串每个单词首字母大写的拷贝
print(str1.title()) # Hello, World!
# 获得字符串变大写后的拷贝
print(str1.upper()) # HELLO, WORLD!
# 从字符串中查找子串所在位置
print(str1.find('or')) # 8
print(str1.find('shit')) # -1
# 与find类似但找不到子串时会引发异常
# print(str1.index('or'))
# print(str1.index('shit'))
# 检查字符串是否以指定的字符串开头
print(str1.startswith('He')) # False
print(str1.startswith('hel')) # True
# 检查字符串是否以指定的字符串结尾
print(str1.endswith('!')) # True
# 将字符串以指定的宽度居中并在两侧填充指定的字符
print(str1.center(50, '*'))
# 将字符串以指定的宽度靠右放置左侧填充指定的字符
print(str1.rjust(50, ' '))
str2 = 'abc123456'
# 检查字符串是否由数字构成
print(str2.isdigit())  # False
# 检查字符串是否以字母构成
print(str2.isalpha())  # False
# 检查字符串是否以数字和字母构成
print(str2.isalnum())  # True
str3 = '  jackfrued@126.com '
print(str3)
# 获得字符串修剪左右两侧空格之后的拷贝
print(str3.strip())
```

**格式化字符方法**

```
a, b = 5, 10
print(f'{a} * {b} = { a * b}')
```

### 使用列表

list

```
基本操作：
for index, elem in enumerate(list1):
	print(index, elem)

#插入
list.append(5)
list.insert(1, 100)

#合并
list += [100, 200]

#删除,满足条件左边的第一个
if 3 in list:
	list.remove(3)
list.pop(0)

list.clear

切片：
# 可以通过完整切片操作来复制列表
fruits3 = fruits[:]
# 可以通过反向切片操作来获得倒转后的列表的拷贝
fruits5 = fruits[::-1]

排序：
list1 = ['orange', 'apple', 'zoo', 'internationalization', 'blueberry']
list2 = sorted(list1)
# sorted函数返回列表排序后的拷贝不会修改传入的列表，list1不变，list2变
#	key=len, reverse=True
list3 = sorted(list1, reverse=True)
```

```
生成式和生成器
列表生成式语法：
f = [x + y for x in 'ABCDE' for y in '1234567']
生成器对象：不占用语法
f = (x ** 2 for x in range(1, 1000))

通过yield可以将一个普通函数改造成生成器函数
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
        yield a


def main():
    for val in fib(20):
        print(val)


if __name__ == '__main__':
    main()
```

### 使用元组()

元组就是内部元素不能修改

* 多线程环境
* 创建时间和空间都更快

```
list()、tuple()
```

### 使用集合{}

```
增减
set1.add(4)
set1.add(5)
set2.update([11, 12])
set2.discard(5)
if 4 in set2:
    set2.remove(4)
print(set1, set2)
print(set3.pop())
print(set3)

集合运算
# 集合的交集、并集、差集、对称差运算
print(set1 & set2)
# print(set1.intersection(set2))
print(set1 | set2)
# print(set1.union(set2))
print(set1 - set2)
# print(set1.difference(set2))
print(set1 ^ set2)
# print(set1.symmetric_difference(set2))
# 判断子集和超集
print(set2 <= set1)
# print(set2.issubset(set1))
print(set3 <= set1)
# print(set3.issubset(set1))
print(set1 >= set2)
# print(set1.issuperset(set2))
print(set1 >= set3)
# print(set1.issuperset(set3))
```

### 使用字典

```
# 对字典中所有键值对进行遍历
for key in scores:
    print(f'{key}: {scores[key]}')
    
scores.update(five = 5, six = 6)

#删除
scores.pop('骆昊', 100)
```

练习4：设计一个函数返回传入的列表中最大和第二大的元素的值。

练习5：计算指定的年月日是这一年的第几天。

```
#对列表进行选择，还挺好用的
days_of_month = [
        [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
        [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    ][is_leap_year(year)]
```

练习6：打印杨辉三角，首先把框架搭出来，再进行赋值

## Day8 面向对象编程基础

### 类

"把一组数据结构和处理它们的方法组成对象（object），把相同行为的对象归纳为类（class），通过类的封装（encapsulation）隐藏内部细节，通过继承（inheritance）实现类的特化（specialization）和泛化（generalization），通过多态（polymorphism）实现基于对象类型的动态分派。"

#### 定义类

```
class Student(object):

    # __init__是一个特殊方法用于在创建对象时进行初始化操作
    # 通过这个方法我们可以为学生对象绑定name和age两个属性
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def study(self, course_name):
        print('%s正在学习%s.' % (self.name, course_name))

    # PEP 8要求标识符的名字用全小写多个单词用下划线连接
    # 但是部分程序员和公司更倾向于使用驼峰命名法(驼峰标识)
    def watch_movie(self):
        if self.age < 18:
            print('%s只能观看《熊出没》.' % self.name)
        else:
            print('%s正在观看岛国爱情大电影.' % self.name)
```

#### 创建和使用

```
def main():
    # 创建学生对象并指定姓名和年龄
    stu1 = Student('骆昊', 38)
    # 给对象发study消息
    stu1.study('Python程序设计')
    # 给对象发watch_av消息
    stu1.watch_movie()
    stu2 = Student('王大锤', 15)
    stu2.study('思想品德')
    stu2.watch_movie()


if __name__ == '__main__':
    main()
```

#### 访问可见性问题

在Python中，属性和方法的访问权限只有两种，也就是公开的和私有的

属性是私有的，在给属性命名时可以用两个下划线作为开头

我们并不建议将属性设置为私有的，因为这会导致子类无法访问

Python并没有从语法上严格保证私有属性或方法的私密性，可以

```python
class Test:

    def __init__(self, foo):
        self.__foo = foo

    def __bar(self):
        print(self.__foo)
        print('__bar')


def main():
    test = Test('hello')
    test._Test__bar()
    print(test._Test__foo)


if __name__ == "__main__":
    main()
```

程序员会遵循一种命名惯例就是让属性名以单下划线开头来表示属性是受保护的

## Day9 面向对象进阶

### `@property`修饰器

将属性命名以单下划线开头，通过这种方式来暗示属性是受保护的，不建议外界直接访问，那么如果想访问属性可以通过属性的getter（访问器）和setter（修改器）方法进行对应的操作。如果要做到这点，就可以考虑使用@property包装器来包装getter和setter方法，使得对属性的访问既安全又方便

```python
class Person(object):

    def __init__(self, name, age):
        self._name = name
        self._age = age

    # 访问器 - getter方法
    @property
    def name(self):
        return self._name

    # 访问器 - getter方法
    @property
    def age(self):
        return self._age

    # 修改器 - setter方法
    @age.setter
    def age(self, age):
        self._age = age

    def play(self):
        if self._age <= 16:
            print('%s正在玩飞行棋.' % self._name)
        else:
            print('%s正在玩斗地主.' % self._name)


def main():
    person = Person('王大锤', 12)
    person.play()
    person.age = 22
    person.play()
    # person.name = '白元芳'  # AttributeError: can't set attribute


if __name__ == '__main__':
    main()
```

### `__slots__`魔法

如果我们需要限定自定义类型的对象只能绑定某些属性，可以通过在类中定义`__slots__`变量来进行限定。需要注意的是`__slots__`的限定只对当前类的对象生效，对子类并不起任何作用。

```
# 限定Person对象只能绑定_name, _age和_gender属性
    __slots__ = ('_name', '_age', '_gender')
```

### 静态方法和类方法

我们在类中定义的方法都是对象方法，实际上，我们写在类中的方法并不需要都是对象方法,只是属于该类的

#### 静态方法

```python
@staticmethod
def is_valid(a, b, c):
    return a + b > c and b + c > a and a + c > b

def main():
    a, b, c = 3, 4, 5
    # 静态方法和类方法都是通过给类发消息来调用的
    if Triangle.is_valid(a, b, c):
        t = Triangle(a, b, c)
        print(t.perimeter())
        # 也可以通过给类发消息来调用对象方法但是要传入接收消息的对象作为参数
        # print(Triangle.perimeter(t))
        print(t.area())
        # print(Triangle.area(t))
    else:
        print('无法构成三角形.')
```

#### 类方法

通过这个参数我们可以获取和类相关的信息并且可以创建出类的对象

```python
@classmethod
def now(cls):
	ctime = localtime(time())
	return cls(ctime.tm_hour, ctime.tm_min, ctime.tm_sec)

def main():
    # 通过类方法创建对象并获取系统时间
    clock = Clock.now()
    while True:
        print(clock.show())
        sleep(1)
        clock.run()
```

### 类之间的关系

类和类之间的关系有三种：is-a（继承or泛化）、has-a（关联）和use-a（依赖）关系。

可以用UML

### 继承和多态

#### 继承

```python
class Student(Person):
    """学生"""

    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self._grade = grade

    @property
    def grade(self):
        return self._grade

    @grade.setter
    def grade(self, grade):
        self._grade = grade

    def study(self, course):
        print('%s的%s正在学习%s.' % (self._grade, self._name, course))
```

**重写**

通过方法重写我们可以让父类的同一个行为在子类中拥有不同的实现版本，当我们调用这个经过子类重写的方法时，不同的子类对象会表现出不同的行为，这个就是多态（poly-morphism）。

```python
from abc import ABCMeta, abstractmethod


class Pet(object, metaclass=ABCMeta):
    """宠物"""

    def __init__(self, nickname):
        self._nickname = nickname

    @abstractmethod
    def make_voice(self):
        """发出声音"""
        pass


class Dog(Pet):
    """狗"""

    def make_voice(self):
        print('%s: 汪汪汪...' % self._nickname)


class Cat(Pet):
    """猫"""

    def make_voice(self):
        print('%s: 喵...喵...' % self._nickname)


def main():
    pets = [Dog('旺财'), Cat('凯蒂'), Dog('大黄')]
    for pet in pets:
        pet.make_voice()


if __name__ == '__main__':
    main()
```

`Pet`类处理成了一个抽象类，所谓抽象类就是不能够创建对象的类,我们可以通过`abc`模块的`ABCMeta`元类和`abstractmethod`包装器来达到抽象类的效果

## Day10 图形用户界面和游戏开发

### 基于tkinter模块的GUI

基本上使用tkinter来开发GUI应用需要以下5个步骤：

1. 导入tkinter模块中我们需要的东西。
2. 创建一个顶层窗口对象并用它来承载整个GUI应用。
3. 在顶层窗口对象上添加GUI组件。
4. 通过代码将这些GUI组件的功能组织起来。
5. 进入主事件循环(main loop)。

wxPython、PyQt、PyGTK等模块都是不错的选择

### 使用Pygame进行游戏开发

https://www.pygame.org/news

## Day11 文件和异常

### 文件

`open()`函数，操作模式: r, w, a

#### 文本文件

```
f = open('致橡树.txt', 'r', encoding='utf-8')

# 通过for-in循环逐行读取
    with open('致橡树.txt', mode='r') as f:
        for line in f:
            print(line, end='')

# 读取文件按行读取到列表中
    with open('致橡树.txt') as f:
        lines = f.readlines()
```

```
def main():
    f = None
    try:
        f = open('致橡树.txt', 'r', encoding='utf-8')
        print(f.read())
    except FileNotFoundError:
        print('无法打开指定的文件!')
    except LookupError:
        print('指定了未知的编码!')
    except UnicodeDecodeError:
        print('读取文件时解码错误!')
    finally:
        if f:
            f.close()


if __name__ == '__main__':
    main()
```



#### 二进制文件

'rb',不用encoding

```python
def main():
    try:
        with open('guido.jpg', 'rb') as fs1:
            data = fs1.read()
            print(type(data))  # <class 'bytes'>
        with open('吉多.jpg', 'wb') as fs2:
            fs2.write(data)
    except FileNotFoundError as e:
        print('指定的文件无法打开.')
    except IOError as e:
        print('读写文件时出现错误.')
    print('程序执行结束.')


if __name__ == '__main__':
    main()
```

#### 读写json文件

- `dump` - 将Python对象按照JSON格式序列化到文件中
- `dumps` - 将Python对象处理成JSON格式的字符串
- `load` - 将文件中的JSON数据反序列化成对象
- `loads` - 将字符串的内容反序列化成Python对象

```
with open('test.json', 'w', encoding = 'utf-8') as fs:
	json.dump(mydict, fs)
```

## Day12 正则表达式

在编写处理字符串的程序或网页时，经常会有查找符合某些复杂规则的字符串的需要，正则表达式就是用于描述这些规则的工具，换句话说正则表达式是一种工具，它定义了字符串的匹配模式（如何检查一个字符串是否有跟某种模式匹配的部分或者从一个字符串中将与模式匹配的部分提取出来或者替换掉）。

* 元字符

  ![image-20210410220658209](Python.assets/image-20210410220658209.png)

* 字符转义 `\.`例如：deerchao\.cn匹配deerchao.cn

* 重复： * + ? {n} {n,} {n,m}

![image-20210410220908066](Python.assets/image-20210410220908066.png)

* 字符类：[a-z0-9A-Z_]

* 分枝条件|：\(0\d{2}\)[- ]?\d{8}|0\d{2}[- ]?\d{8}

* 分组：(\d{1,3}\.)**{3}**\d{1,3}

* 反义

  ![image-20210410221501163](Python.assets/image-20210410221501163.png)

* 后向引用
* 零宽断言
* 负向零宽断言
* 注释(?#comment)
* 贪婪与懒惰：
  * a.*b，它将会匹配最长的以a开始，以b结束的字符串。如果用它来搜索*aabab*的话，它会匹配整个字符串aabab。这被称为**贪婪**匹配。
  * a.*?b匹配最短的，以a开始，以b结束的字符串。如果把它应用于*aabab*的话，它会匹配aab（第一到第三个字符）和ab（第四到第五个字符）。**懒惰**匹配

![image-20210410224658032](Python.assets/image-20210410224658032.png)

* 处理选项
* 平衡组/递归匹配

### Python对正则表达式的支持

re模块

![image-20210410225323612](Python.assets/image-20210410225323612.png)

```python
"""
验证输入用户名和QQ号是否有效并给出对应的提示信息

要求：用户名必须由字母、数字或下划线构成且长度在6~20个字符之间，QQ号是5~12的数字且首位不能为0
"""
import re


def main():
    username = input('请输入用户名: ')
    qq = input('请输入QQ号: ')
    # match函数的第一个参数是正则表达式字符串或正则表达式对象
    # 第二个参数是要跟正则表达式做匹配的字符串对象
    m1 = re.match(r'^[0-9a-zA-Z_]{6,20}$', username)
    if not m1:
        print('请输入有效的用户名.')
    m2 = re.match(r'^[1-9]\d{4,11}$', qq)
    if not m2:
        print('请输入有效的QQ号.')
    if m1 and m2:
        print('你输入的信息是有效的!')


if __name__ == '__main__':
    main()
```

## Day13 多进程和多线程

### 多进程

进程：资源分配的基本单位

使用multiprocessing模块的`Process`类来创建子进程，而且该模块还提供了更高级的封装，例如批量启动进程的进程池（`Pool`）、用于进程间通信的队列（`Queue`）和管道（`Pipe`）等。

```python
from multiprocessing import Process
from os import getpid
from random import randint
from time import time, sleep


def download_task(filename):
    print('启动下载进程，进程号[%d].' % getpid())
    print('开始下载%s...' % filename)
    time_to_download = randint(5, 10)
    sleep(time_to_download)
    print('%s下载完成! 耗费了%d秒' % (filename, time_to_download))


def main():
    start = time()
    p1 = Process(target=download_task, args=('Python从入门到住院.pdf', ))
    p1.start()
    p2 = Process(target=download_task, args=('Peking Hot.avi', ))
    p2.start()
    p1.join()
    p2.join()
    end = time()
    print('总共耗费了%.2f秒.' % (end - start))


if __name__ == '__main__':
    main()
```

通过`Process`类创建了进程对象，通过`target`参数我们传入一个函数来表示进程启动后要执行的代码，后面的`args`是一个元组，它代表了传递给函数的参数。`Process`对象的`start`方法用来启动进程，而`join`方法表示等待进程执行结束。

### 多线程

因此目前的多线程开发我们推荐使用threading模块

```
from random import randint
from threading import Thread
from time import time, sleep


class DownloadTask(Thread):

    def __init__(self, filename):
        super().__init__()
        self._filename = filename

    def run(self):
        print('开始下载%s...' % self._filename)
        time_to_download = randint(5, 10)
        sleep(time_to_download)
        print('%s下载完成! 耗费了%d秒' % (self._filename, time_to_download))


def main():
    start = time()
    t1 = DownloadTask('Python从入门到住院.pdf')
    t1.start()
    t2 = DownloadTask('Peking Hot.avi')
    t2.start()
    t1.join()
    t2.join()
    end = time()
    print('总共耗费了%.2f秒.' % (end - start))


if __name__ == '__main__':
    main()
```

#### 通过锁保护临界资源

```
from time import sleep
from threading import Thread, Lock


class Account(object):

    def __init__(self):
        self._balance = 0
        self._lock = Lock()

    def deposit(self, money):
        # 先获取锁才能执行后续的代码
        self._lock.acquire()
        try:
            new_balance = self._balance + money
            sleep(0.01)
            self._balance = new_balance
        finally:
            # 在finally中执行释放锁的操作保证正常异常锁都能释放
            self._lock.release()

    @property
    def balance(self):
        return self._balance


class AddMoneyThread(Thread):

    def __init__(self, account, money):
        super().__init__()
        self._account = account
        self._money = money

    def run(self):
        self._account.deposit(self._money)


def main():
    account = Account()
    threads = []
    for _ in range(100):
        t = AddMoneyThread(account, 1)
        threads.append(t)
        t.start()
    for t in threads:
        t.join()
    print('账户余额为: ￥%d元' % account.balance)


if __name__ == '__main__':
    main()
```

#### Python的多线程并不能发挥cpu的多核特性

全局解释器锁（GIL）

Python代码的执行由Python虚拟机（解释器）来控制，对Python虚拟机的访问由全局解释器锁（GIL）来控制，正是这个锁能保证同时只有一个线程在运行。在多线程环境中，Python虚拟机按照以下方式执行。

### 是否采用多任务

任务分为计算密集型和I/O密集型，计算密集型没区别。

I/O密集型：Cpu消耗少，大部分在等待I/O操作完成，可以启动多任务

最简单的方法是：多进程+协程

### 单线程+异步I/O（协程）

* 程序自身控制子程序切换，没有切换开销
* 不用加锁控制共享资源

## Day14网络编程入门和网络应用开发

### 计算机网络基础

#### TCP/IP模型

#### 网络应用模式

### 基于HTTP协议的网络资源访问

#### HTTP

#### JSON

request库

### 基于传输层协议的套接字编程

实际开发中使用的套接字可以分为三类：流套接字（TCP套接字）、数据报套接字和原始套接字。

#### Tcp套接字

TCP套接字就是使用TCP协议提供的传输服务来实现网络通信的编程接口

端口的取值范围是0~65535，而1024以下的端口我们通常称之为“著名端口”（留给像FTP、HTTP、SMTP等“著名服务”使用的端口，有的地方也称之为“周知端口”

#### UDP套接字（强调性能）

### 网络应用开发

#### 发送电子邮件

#### 发送短信

## Day15 图像和办公文档处理

### 操作图像

#### 计算机图像知识：

1.颜色

2.像素

#### 用pillow操作图像

```
from PIL import Image

image = Image.open('./res/guido.jpg')
image.format, image.size, image.mode
#('JPEG', (500, 750), 'RGB')
image.show()
```

### 办公文档

#### 处理excel

```
import datetime

from openpyxl import Workbook

wb = Workbook()
ws = wb.active

ws['A1'] = 42
ws.append([1, 2, 3])
ws['A2'] = datetime.datetime.now()

wb.save("sample.xlsx")
```

#### 处理Word文档

```
from docx import Document
from docx.shared import Inches

document = Document()

document.add_heading('Document Title', 0)

p = document.add_paragraph('A plain paragraph having some ')
p.add_run('bold').bold = True
p.add_run(' and some ')
p.add_run('italic.').italic = True

document.add_heading('Heading, level 1', level=1)
document.add_paragraph('Intense quote', style='Intense Quote')

document.add_paragraph(
    'first item in unordered list', style='List Bullet'
)
document.add_paragraph(
    'first item in ordered list', style='List Number'
)

document.add_picture('monty-truth.png', width=Inches(1.25))

records = (
    (3, '101', 'Spam'),
    (7, '422', 'Eggs'),
    (4, '631', 'Spam, spam, eggs, and spam')
)

table = document.add_table(rows=1, cols=3)
hdr_cells = table.rows[0].cells
hdr_cells[0].text = 'Qty'
hdr_cells[1].text = 'Id'
hdr_cells[2].text = 'Desc'
for qty, id, desc in records:
    row_cells = table.add_row().cells
    row_cells[0].text = str(qty)
    row_cells[1].text = id
    row_cells[2].text = desc

document.add_page_break()

document.save('demo.docx')
```

# 数据结构与算法（Python）

## 算法分析

### 大O表示法

赋值语句包含了计算和存储

问题规模如何影响一个算法的执行时间

O(f(n)):f(n)主导部分

![image-20210412133829620](Python.assets/image-20210412133829620.png)

### Python数据类型的性能

**列表list**

赋值列表推导式是最快的

pop():O(1) pop(i):O(n)

sort:O(nlogn)

**字典dict**

## 数据结构

## 线性结构

唯一前驱和唯一后继，区别是数据项增减的方式

* 栈stack
* 队列queue
* 双端队列deque
* 列表list

### 栈stack

数据的加入和移除都仅发生在一端（顶top,底base）

后进先出LIFO，反转次序（后退按钮，undo按钮）

```
Stack()
is_empty()
push()
pop()
peek()
size()
```



**应用：**

简单括号匹配

十进制转化为二进制

**表达式转换**

​	正常是中缀表达式在前缀和后缀表达式，**操作符的次序**决定了运算的次序

​	首先转化为有括号，然后将操作符移动到括号前面或者右边

​	**常用算法：**

​		已经考虑了符号优先级

​		有括号

后缀表达式求值

### 队列queue

新数据项的添加发生在一端（尾rear），移除发生在另一端（首front）

先进先出FIFO

例子：排队、打印机、进程调度、键盘缓冲区

```
Queue()
enqueue(item)
dequeue()
is_empty()
size()
```

**应用：**

约瑟夫问题（热土豆）

打印

### 双端队列deque

首端和尾端都可以加入和移除，可以用来模拟栈和队列

```
Deque()
add_front(item)
add_rear(item)
remove_front(item)
remove_rear()
is_empty()
size()
```

**例子：**

回文词判定

### 列表list

按照**相对位置**存放

```
List()
add(item)
remove(item)
search(item)
is_empty()
size()

append(item)
index(item)
insert(pos, item)
pop()
pop(pos)
```

采用**链接表**的方案，要求数据项的前后位置，但不要求数据项依次存放在连续空间，所以只要有链接指向就好，第一个和 最后一个数据项需要显示标记

链表实现的基本元素节点Node

