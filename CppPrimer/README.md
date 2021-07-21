

# **C++_primer**

[TOC]



## 第一部分	基本语言

### 第一章 快速入门

![image-20210613160043738](C++_笔记.assets/image-20210613160043738.png)

![image-20210613160349670](C++_笔记.assets/image-20210613160349670.png)

![image-20210613160530818](C++_笔记.assets/image-20210613160530818.png)

![image-20210613160736573](C++_笔记.assets/image-20210613160736573.png)

![image-20210613161104959](C++_笔记.assets/image-20210613161104959.png)

![image-20210613161357550](C++_笔记.assets/image-20210613161357550.png)

![image-20210613161439634](C++_笔记.assets/image-20210613161439634.png)



### 第二章 变量和基本类型

#### 2.1 基本内置类型

![屏幕截图 17-03-2021 17.33.40](D:\Anzhuan\MovaviScreenRecorderPortable\Record\屏幕截图 17-03-2021 17.33.40.png)

##### 2.1.1 算数类型

**整型**

**整型**：整数、字符、布尔型

带符号和无符号类型（signed、unsigned），**默认带符号**。unsigned后不加，意味着unsigned int

```
#取值越界                                                                                                                          无符号
例如：8位的unsigned char，取值范围是0~255，则数字对2^8 = 256取模，负数也是取模，如-1取模是255
有符号由编译器决定
```

**浮点型**

float一个字，6位有效数字

double两个字，至少10位有效数字

```
#建议
unsigned比较好，避免越界出现负数
很少用short
char尽量不要用来计算
用int比较好，不管是出错或者是性能
浮点就用double
```

##### 2.1.2 类型转换

自动类型转换

有符号会转换成无符号

`sizeof`可以看有多少个字节

##### 2.1.3 字面值常量

**1.整型字面值和浮点字面值**

20：10进制	024：8进制	0x14：十六进制

后面增加l或L，强制转化为long，用L；加U则unsigned；如1024UL



3.14159E0F

E是指数，F单精度，默认double

**3.布尔字面值、字符字面值和字符串字面值**

true和false

‘a' 单引号，L’a' wchar_t

“Hello World”

![image-20210615122321950](C++_笔记.assets/image-20210615122321950.png)

**4.非打印字符的转义序列**

```
\n	换行
\t
\r	回车
后面的是当你用到这些符号的时候
\\
\'
\?
\''
```

**5.字符串字面值**

"",会在字符串字面值加个空字符’\0‘

```
#字符串字面值连接
空格、制表符或者换行符分开最后都会连接
```

![image-20210317233859395](C:\Users\m\AppData\Roaming\Typora\typora-user-images\image-20210317233859395.png)

```
#用反斜线\就可以连接任何东西，不允许有任何东西
```

![image-20210613183152126](C++_笔记.assets/image-20210613183152126.png)

#### 2.2 变量

C++是一种静态类型语言，编译时会检查类型，所以需要先定义变量的类型

##### 2.2.1 什么是变量

**左值和右值：**左值可以出现在赋值语句的左边或者右边，右值只能出现在右边

**对象：**对象是内存中具有类型的区域

##### 2.2.2 变量名

变量的标识符，**字母、数字、下划线**，变量必须以字母或者下划线开头而且区分大小写

**1.C++关键字**

![image-20210319115730975](C:\Users\m\AppData\Roaming\Typora\typora-user-images\image-20210319115730975.png)

![image-20210319115759329](C:\Users\m\AppData\Roaming\Typora\typora-user-images\image-20210319115759329.png)

**2.变量命名习惯**

* 一般用小写字母
* 提示用法
* 每个词之间添加下划线：student_loan或者内嵌的词第一个字母都大写：studentLoan

##### 2.2.3 定义对象

类型说明符 变量名；

**1.初始化**

* 复制初始化 =
* 直接初始化()
* 列表初始化={} **列表初始化没有类型转换，所以里面必须是相应类型的**

**2.使用多个初始化式**

内置类型没区别

类类型有些初始化只能用直接初始化，**构造函数**，多个初始化式时不能用复制初始化

**3.初始化多个变量**

##### 2.2.4 变量初始化规则

**1.内置类型变量的初始化**

取决于变量定义的位置，函数体外为零，体里的不进行自动初始化（包括int）

**2.类类型变量的初始化**

构造函数控制初始化

没提供就会有**默认构造函数**

##### 2.2.5 声明和定义

**定义**：分配存储空间，指定初始值

**声明**：表明变量的类型和名字，定义也是声明。可以使用extern关键字声明

![image-20210406154722560](C++_笔记.assets/image-20210406154722560.png)

![image-20210613200541074](C++_笔记.assets/image-20210613200541074.png)

![image-20210613200644939](C++_笔记.assets/image-20210613200644939.png)

这时候是一个全局变量

##### 2.2.6 名字的作用域

用花括号界定

* 全局作用域：函数外部的名字
* 局部作用域：
* 语句作用域：比如for语句中

**作用域可嵌套**

##### 2.2.7 在变量使用处定义变量

通常把一个对象定义在首次使用的地方

#### 2.3 复合类型

![image-20210615125045177](C++_笔记.assets/image-20210615125045177.png)

##### 2.3.1 引用

引用就是别名，主要用作函数的形式参数，必须初始化

![image-20210613203531327](C++_笔记.assets/image-20210613203531327.png)

**1.引用是别名**

**2.定义多个引用**

**3.const 引用**

![image-20210613203827839](C++_笔记.assets/image-20210613203827839.png)

![image-20210613203956995](C++_笔记.assets/image-20210613203956995.png)

##### 2.3.2 指针

![image-20210615130131914](C++_笔记.assets/image-20210615130131914.png)

**定义**

![image-20210615130231817](C++_笔记.assets/image-20210615130231817.png)

**获取地址**

![image-20210615130255131](C++_笔记.assets/image-20210615130255131.png)

**利用指针访问对象**

![image-20210615130405801](C++_笔记.assets/image-20210615130405801.png)

**空指针**

![image-20210615130504976](C++_笔记.assets/image-20210615130504976.png)

**初始化所有指针，实在不清楚就`nullptr`**

**`void*`指针**

![image-20210615130713276](C++_笔记.assets/image-20210615130713276.png)

##### 2.3.4 理解复合类型的声明

![image-20210615131209676](C++_笔记.assets/image-20210615131209676.png)

![image-20210615131226304](C++_笔记.assets/image-20210615131226304.png)

**指向指针的指针**

![image-20210615131324998](C++_笔记.assets/image-20210615131324998.png)

**指向指针的引用**

![image-20210615132306931](C++_笔记.assets/image-20210615132306931.png)

![image-20210615132554109](C++_笔记.assets/image-20210615132554109.png)

#### 2.4 const限定符

![image-20210613201951765](C++_笔记.assets/image-20210613201951765.png)

#### 1.定义const对象

```
const int i = 0; //必须初始化
```

#### 2.const对象默认为文件的局部变量

想要别的用，要提前加extern

##### 2.4.1 const的引用

常量的引用必须是const的引用，但是const引用的对象不一定是个常量，所以这个常量有可能通过其他途径修改

![image-20210615132918727](C++_笔记.assets/image-20210615132918727.png)

##### 2.4.2 指针和const

**指向常量的指针**

和const的引用一样，但是指针可以改变指向的对象

![image-20210615133404648](C++_笔记.assets/image-20210615133404648.png)

**const 指针**

`*const` 必须初始化，指针不可以改变指向的对象，但是可以改变指向对象的值

![image-20210615133656275](C++_笔记.assets/image-20210615133656275.png)

##### 2.4.3 顶层const

![image-20210615134351656](C++_笔记.assets/image-20210615134351656.png)

##### 2.4.4 constexpr和常量表达式

#### 2.5 处理类型

##### 2.5.1 类型别名

 **typedef名字**

类型同义词

![image-20210613231326502](C++_笔记.assets/image-20210613231326502.png)

**using**

![image-20210615141632652](C++_笔记.assets/image-20210615141632652.png)

##### 2.5.2 auto类型说明符

![image-20210615142054250](C++_笔记.assets/image-20210615142054250.png)

auto会忽略顶层const，保留底层const

![image-20210615142310013](C++_笔记.assets/image-20210615142310013.png)

##### 2.5.3 decltype类型指示符

![image-20210615142545848](C++_笔记.assets/image-20210615142545848.png)

![image-20210615142711327](C++_笔记.assets/image-20210615142711327.png)

### 2.7 enum枚举

![image-20210613232251900](C++_笔记.assets/image-20210613232251900.png)

![image-20210613232318699](C++_笔记.assets/image-20210613232318699.png)

#### 2.8 类类型

#### 1.从操作开始设计类

接口和实现

![image-20210613232853107](C++_笔记.assets/image-20210613232853107.png)

#### 2.定义类

![image-20210613233323088](C++_笔记.assets/image-20210613233323088.png)

注意最后的分号

#### 3.类的数据成员

#### 4.访问标号

public和private

public可以在程序的任何部分访问

private只能被类的组成部分访问或者是该类的友元

#### 5.使用struct关键字

成员都是默认public，class默认为private

#### 2.9 编写自己的头文件

header file

#### 2.9.1设计自己的头文件

![image-20210613234648962](C++_笔记.assets/image-20210613234648962.png)

##### 1.头文件用于声明而不是用于定义

![image-20210613234808333](C++_笔记.assets/image-20210613234808333.png)

##### 2.一些const对象定义在头文件中

常量表达式初始化的const对象

#### 2.9.2 预处理器的简单介绍

#include是预处理器的一部分

##### 1. 头文件经常需要其他头文件

文件保护符

##### 2.避免多重包含

为了避免名字冲突，所以用全大写字母

![image-20210613235432220](C++_笔记.assets/image-20210613235432220.png)

##### 3.使用自定义的头文件

![image-20210613235505867](C++_笔记.assets/image-20210613235505867.png)

“” 认为是非系统头文件，查找通常开始于源文件所在的路径

### 第三章 字符串、向量和数组

#### 3.1 命名空间的using声明

作用域操作符 `::`

`using namespace::std`

`using std::cin`

![image-20210614133837796](C++_笔记.assets/image-20210614133837796.png)

**1.每个名字都需要一个using声明**

**2.使用标准库类型的类定义**

**3.头文件不应该包含using声明**

**习题**

![image-20210614134954570](C++_笔记.assets/image-20210614134954570.png)

```c++
#include <iostream>

using std::cin;
using std::cout;
using std::endl;

int main()
{
	int base, exponent;
    int result = 1;
    
    cout << "Enter base and exponent: " << endl;
    cin >> base >> exponent;
    
    if(exponent < 0){
        cout << "Exponent must be bigger than 0" << endl;
        return -1;
    } else {
        for(int cnt = 0; cnt < exponent; ++ cnt){
			result *= base;
        }
    }
    
    cout << "Result = " << result << endl;
    return 0;
}
```

#### 3.2 标准库string类型

长度可变的字符串

`#include <iostream>`

`using std::string`

##### 3.2.1 string对象的定义和初始化

![image-20210614141924746](C++_笔记.assets/image-20210614141924746.png)

##### 3.2.2 string对象的读写

![image-20210614142128589](C++_笔记.assets/image-20210614142128589.png)

**1.读入未知数目的string对象**

`while(cin >> word){}`

**2.用getline读取整行文本**

```c++
 string line;
 while(getline(cin, line)) #getline会丢弃输入时的换行符
        cout << s4 << endl;
```

##### 3.2.3 string对象的操作

![image-20210614142634970](C++_笔记.assets/image-20210614142634970.png)

**2.string::size_type类型**

s.size()返回的类型是string::size_type类型，而不是int，所以返回值不要赋给一个int对象。**C++11**中推荐用`auto`或者`decltype`

**3.string关系操作符**

比较大小是按照字典顺序的

**6.和字符串字面值连接**

左右操作数至少有一个需要是string

![image-20210614143504245](C++_笔记.assets/image-20210614143504245.png)

**7.获取字符**

![image-20210614143603290](C++_笔记.assets/image-20210614143603290.png)

**8.下标操作可用作左值**

##### 3.2.4 string对象中字符的处理

![image-20210614144044181](C++_笔记.assets/image-20210614144044181.png)

![image-20210615144352013](C++_笔记.assets/image-20210615144352013.png)

![image-20210615144410291](C++_笔记.assets/image-20210615144410291.png)

![image-20210615144514144](C++_笔记.assets/image-20210615144514144.png)

**习题**

![image-20210614144319109](C++_笔记.assets/image-20210614144319109.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

int main()
{
    string s1;
    string s2;

    cout << "Enter two string: ";
    cin >> s1 >> s2;

    if(s1 == s2)
        cout << "s1 == s2" << endl;
    else if(s1 > s2)
        cout << "s1 > s2" << endl;
    else
        cout << "s1 < s2" << endl;
    return 0;
}

int main()
{
    string s1;
    string s2;

    cout << "Enter two string: ";
    cin >> s1 >> s2;

    if(s1.size() == s2.size())
        cout << "s1 == s2" << endl;
    else if(s1.size() > s2.size())
        cout << "s1 > s2" << endl;
    else
        cout << "s1 < s2" << endl;
    return 0;
}
```

![image-20210614145844635](C++_笔记.assets/image-20210614145844635.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

int main()
{
    string s;
    string result;

    cin >> s;
    result = s;
    while(cin >> s){
        if(s != "EOF")
            result += ' ' + s;
        else
            break;
    }
    cout << result << endl;
    return 0;
}
```

![image-20210614150643753](C++_笔记.assets/image-20210614150643753.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

int main()
{
    string s;
    string result;

    cout << "Enter string with punct: ";
    cin >> s;

    for(string::size_type idx = 0; idx != s.size(); ++ idx){
        if(!ispunct(s[idx]))
            result += s[idx];
    }
    if(result.size() == s.size()){
        cout << "Enter wrong string" << endl;
        return -1;
    }
    else
        cout << result << endl;
    return 0;
}
```

#### 3.3 标准库vector类型

vector是同一种类型的对象的集合

```
#include <vector>
using std::vector;
```

![image-20210614154134184](C++_笔记.assets/image-20210614154134184.png)

##### 3.3.1 vector对象的定义和初始化

![image-20210614154215250](C++_笔记.assets/image-20210614154215250.png)

**1.创建确定个数的元素**

![image-20210614154323034](C++_笔记.assets/image-20210614154323034.png)

![image-20210614154335846](C++_笔记.assets/image-20210614154335846.png)

所以最好先创建空的，然后动态增加元素

**列表初始化**

![image-20210615145405191](C++_笔记.assets/image-20210615145405191.png)

**2.值初始化**

![image-20210614155204833](C++_笔记.assets/image-20210614155204833.png)

##### 3.3.2 vector对象的操作

![image-20210614155347109](C++_笔记.assets/image-20210614155347109.png)

**1.vector对象的size**

`vector<int>::size_type`

**2.向vector添加元素**

![image-20210614155524680](C++_笔记.assets/image-20210614155524680.png)

![image-20210614155641537](C++_笔记.assets/image-20210614155641537.png)

**下标操作不会添加元素，只能用push_back**

**习题**

![image-20210614160342298](C++_笔记.assets/image-20210614160342298.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    vector<int> ivec;
    int num;
    while(cin >> num)
        ivec.push_back(num);
    if(ivec.size() == 0){
        cout << "Error" << endl;
        return -1;
    }

    for(vector<int>::size_type idx = 0; idx < ivec.size() - 1; idx += 2)
        cout <<ivec[idx] + ivec[idx + 1] << endl;

    if(ivec.size() % 2 == 1)
        cout << ivec[ivec.size() - 1] << endl;
    return 0;
}

int main()
{
    vector<int> ivec;
    int num;
    while(cin >> num)
        ivec.push_back(num);
    if(ivec.size() == 0){
        cout << "Error" << endl;
        return -1;
    }

    for(vector<int>::size_type idx = 0; idx < ivec.size() / 2; idx += 1)
        cout <<ivec[idx] + ivec[ivec.size() - idx - 1] << endl;

    if(ivec.size() % 2 == 1)
        cout << ivec[ivec.size() / 2] << endl;
    return 0;
}
```

![image-20210614182218538](C++_笔记.assets/image-20210614182218538.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    vector<string> svec;
    string s1;

    while(cin >> s1)
        svec.push_back(s1);

    for(vector<string>::size_type idx = 0; idx != svec.size(); ++ idx){
        for(string::size_type idy = 0; idy != svec[idx].size(); ++ idy)
            svec[idx][idy] = toupper(svec[idx][idy]);
        cout << svec[idx] << '\t';
        if(idx % 8 == 7)
                cout << endl;
    }
    return 0;
}
```

#### 3.4 迭代器简介

另一种访问`vector`对象的元素的方法，`iterator`

**1.容器的iterator类型**

`vector<int>::iterator iter;`

**2.begin 和 end操作**



`vector<int>::iterator iter = ivec.begin();`

![image-20210614195259399](C++_笔记.assets/image-20210614195259399.png)

![image-20210614195309358](C++_笔记.assets/image-20210614195309358.png)

**3.vector迭代器的自增和解引用运算**

![image-20210615145645977](C++_笔记.assets/image-20210615145645977.png)

![image-20210614195408710](C++_笔记.assets/image-20210614195408710.png)

![image-20210614195429556](C++_笔记.assets/image-20210614195429556.png)

**5.程序示例**

![image-20210614195511868](C++_笔记.assets/image-20210614195511868.png)

c++11中修改为`auto`也可以，begin和end

**6.const_iterator**

只能读取，不能改变值，这个可以++iter

如果是const vector::iterator 就不可以++iter

**习题**

![image-20210614204559275](C++_笔记.assets/image-20210614204559275.png)

![image-20210614160342298](file://E:\postgraduate\work\C++\C++_%E7%AC%94%E8%AE%B0.assets\image-20210614160342298.png?lastModify=1623674758)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    vector<int> ivec;
    int n1;

    while(cin >> n1)
        ivec.push_back(n1);

    vector<int>::iterator iter;
    for(iter = ivec.begin(); iter < ivec.end() - 1; iter += 2)
        cout << *iter + *(iter + 1) << endl;

    if(ivec.size() % 2 == 1)
        cout << *iter << endl;
    return 0;
}

int main()
{
    vector<int> ivec;
    int n1;

    while(cin >> n1)
        ivec.push_back(n1);

    vector<int>::iterator first;
    vector<int>::iterator last;
    for(first = ivec.begin(), last = ivec.end() - 1; first < last; ++first, --last)
        cout << *first + *last << endl;

    if(first == last)
        cout << *first << endl;
    return 0;
}
```

![image-20210614182218538](file://E:\postgraduate\work\C++\C++_%E7%AC%94%E8%AE%B0.assets\image-20210614182218538.png?lastModify=1623675483)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    vector<string> svec;
    string s1;

    while(cin >> s1)
        svec.push_back(s1);

    int count = 0;
    for(vector<string>::iterator iter = svec.begin(); iter != svec.end(); iter ++){
        for(string::size_type idx = 0; idx != (*iter).size(); ++idx)
            (*iter)[idx] = toupper((*iter)[idx]);
        cout << *iter + ' ';
        if((count + 1) % 8 == 0)
            cout << endl;
        count ++;
    }
    return 0;
}
```

![image-20210614210749941](C++_笔记.assets/image-20210614210749941.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    vector<int> ivec(10, 10);

    for(vector<int>::iterator iter = ivec.begin(); iter != ivec.end(); ++iter){
        *iter *= 2;
        cout << *iter << endl;
    }
    return 0;
}c
```

**迭代器的算数操作**

* `iter + n`
* `iter1 - iter2`

![image-20210614211956865](C++_笔记.assets/image-20210614211956865.png)

![image-20210614212015039](C++_笔记.assets/image-20210614212015039.png)

#### 3.5 标准库bitset类型

![image-20210614212129408](C++_笔记.assets/image-20210614212129408.png)

```
#include <bitset>
using std::bitset
```

##### 3.5.1 bitset对象的定义和初始化

![image-20210614215026556](C++_笔记.assets/image-20210614215026556.png)

**1.unsigned值**

![image-20210614215204577](C++_笔记.assets/image-20210614215204577.png)

**2.string**

![image-20210614215219990](C++_笔记.assets/image-20210614215219990.png)

![image-20210614215233719](C++_笔记.assets/image-20210614215233719.png)

##### 3.5.2 bitset对象上的操作

![image-20210614215259510](C++_笔记.assets/image-20210614215259510.png)

#### 3.5 数组

如果不清楚元素的确切个数，使用vector。设计良好的程序只在强调速度时才在类实现的内部使用数组和指针。

##### 3.5.1 定义和初始化内置数组

![image-20210615150201450](C++_笔记.assets/image-20210615150201450.png)

**显式初始化数组元素**

![image-20210615150241018](C++_笔记.assets/image-20210615150241018.png)

**字符数组的特殊性**

![image-20210615150316829](C++_笔记.assets/image-20210615150316829.png)

**不允许拷贝和复制**

![image-20210615150352377](C++_笔记.assets/image-20210615150352377.png)

**理解复杂的数组声明**（由内向外，由右到左）

![image-20210615151211610](C++_笔记.assets/image-20210615151211610.png)

![image-20210615152407217](C++_笔记.assets/image-20210615152407217.png)

##### 3.5.2 访问数组元素

![image-20210615153226646](C++_笔记.assets/image-20210615153226646.png)

##### 3.5.3 指针和数组

![image-20210615153910298](C++_笔记.assets/image-20210615153910298.png)



![image-20210615154055203](C++_笔记.assets/image-20210615154055203.png)

**指针也是迭代器**

![image-20210615154250954](C++_笔记.assets/image-20210615154250954.png)

**begin和end**

![image-20210615154436661](C++_笔记.assets/image-20210615154436661.png)

![image-20210615154504418](C++_笔记.assets/image-20210615154504418.png)

**指针运算**

指向数组的指针运算和迭代器一样

pt[2]

*(pt + 2)

![image-20210615154922545](C++_笔记.assets/image-20210615154922545.png)

##### 3.5.4 C风格字符串

也就是cstring

![image-20210615155137177](C++_笔记.assets/image-20210615155137177.png)

最好不要用

##### 3.5.5 与旧代码接口

**混用string和C**

![image-20210615155308371](C++_笔记.assets/image-20210615155308371.png)

**使用数组初始化vector对象**

![image-20210615155406207](C++_笔记.assets/image-20210615155406207.png)

![image-20210615155428085](C++_笔记.assets/image-20210615155428085.png)

![image-20210615155606277](C++_笔记.assets/image-20210615155606277.png)

#### 3.6 多维数组

![image-20210615155633369](C++_笔记.assets/image-20210615155633369.png)

**初始化**

![image-20210615155736855](C++_笔记.assets/image-20210615155736855.png)

![image-20210615155753793](C++_笔记.assets/image-20210615155753793.png)

**多维数组的下标引用**

**使用for语句处理**

![image-20210615161641503](C++_笔记.assets/image-20210615161641503.png)

使用引用是为了避免数组呗自动转换成指针

![image-20210615161847529](C++_笔记.assets/image-20210615161847529.png)

**指针和多维数组**

![image-20210615162104003](C++_笔记.assets/image-20210615162104003.png)

**类型别名**

![image-20210615162247460](C++_笔记.assets/image-20210615162247460.png)

**练习**

![image-20210615162525627](C++_笔记.assets/image-20210615162525627.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    int arr[3][4] = {1, 2, 3, 4, 5};

    for(int (&row)[4] : arr){
        for(int &col : row)
            cout << col << " ";
        cout << endl;
    }
    cout << endl;

    for(size_t i = 0; i < 3; ++i){
        for(size_t j = 0; j < 4; ++j)
            cout << arr[i][j] << " ";
        cout << endl;
    }

    cout << endl;
    for(int (*p)[4] = begin(arr); p != end(arr); ++p){
        for(int *q = begin(*p); q != end(*p); ++q)
            cout << *q << " ";
        cout << endl;
    }
    return 0;
}
```

**类型别名**

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

using int_4 = int[4];
int main()
{
    int arr[3][4] = {1, 2, 3, 4, 5};

    for(int_4 &row : arr){
        for(int &col : row)
            cout << col << " ";
        cout << endl;
    }
    cout << endl;

    for(size_t i = 0; i < 3; ++i){
        for(size_t j = 0; j < 4; ++j)
            cout << arr[i][j] << " ";
        cout << endl;
    }

    cout << endl;
    for(int_4 *p = begin(arr); p != end(arr); ++p){
        for(int *q = begin(*p); q != end(*p); ++q)
            cout << *q << " ";
        cout << endl;
    }
    return 0;
}

```

### 第四章 表达式

表达式由一个或多个运算对象(operand)组成,对表达式求值将得到一个结果(result).·字面值和变量是最简单的表达式(expression),其结果就是字面值和变量的值。把一个运算符(operator)和一个或多个运算对象组合起来可以生成较复杂的表达式。

#### 4.1 基础

##### 4.1.1 基本概念

一元运算符 & *

二元运算符 + - * /

**重载运算符**

**左值和右值**

左值可以在左边，右值不可以

##### 4.1.2 优先级和结合律

page147

##### 4.1.3 求值顺序

没有规定，取决于编译器

![image-20210615165243832](C++_笔记.assets/image-20210615165243832.png)

#### 4.2 算术运算符

bool除了0都会被转化为true

余数直接丢弃，向0取整，**取余**结果可以先看除法的结果

![image-20210615165737973](C++_笔记.assets/image-20210615165737973.png)

#### 4.3 逻辑和关系运算符

&& 和 || 短路求值，算左再算右

![image-20210615170057739](C++_笔记.assets/image-20210615170057739.png)

#### 4.4 赋值运算符

可以用初始值列表赋值

满足右结合律

![image-20210615170604859](C++_笔记.assets/image-20210615170604859.png)

![image-20210615170833561](C++_笔记.assets/image-20210615170833561.png)

**复合赋值运算符**

![image-20210615170909678](C++_笔记.assets/image-20210615170909678.png)

#### 4.5 递增和递减运算符

![image-20210615174247335](C++_笔记.assets/image-20210615174247335.png)

除非必须，否则不用后置版本

![image-20210615174354632](C++_笔记.assets/image-20210615174354632.png)

#### 4.6 成员访问运算符

点运算符和箭头运算符

ptr->mem 等价于 （*ptr）.mem

![image-20210615185256373](C++_笔记.assets/image-20210615185256373.png)

合法：a d f

#### 4.7 条件运算符

?:

`cond?expr1:expr2`

![image-20210615192142222](C++_笔记.assets/image-20210615192142222.png)

**练习：**

![image-20210615192713708](C++_笔记.assets/image-20210615192713708.png)

```c++
int main()
{
    vector<int> ivec = {1, 2, 3, 4, 5};

    for(auto &val : ivec)
        val = (val % 2 == 1) ? val * 2 : val;

    for(auto val : ivec)
        cout << val << " ";

    return 0;
}
```

![image-20210615194248651](C++_笔记.assets/image-20210615194248651.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    string final_grade;
    int grade;

    while(cin >> grade && grade >= 0 && grade <= 100){
        final_grade = (grade > 90) ? "High pass"
                    : (grade > 75) ? "pass"
                    : (grade > 60) ? "Low pass" : "Fail";
        cout << final_grade << endl;
    }
    return 0;
}
```

#### 4.8 位运算符

![image-20210615194905843](C++_笔记.assets/image-20210615194905843.png)

#### 4.9 sizeof运算符

![image-20210615195149861](C++_笔记.assets/image-20210615195149861.png)

![image-20210615195337734](C++_笔记.assets/image-20210615195337734.png)

#### 4.10 逗号运算符

![image-20210615195502154](C++_笔记.assets/image-20210615195502154.png)

![image-20210615195740348](C++_笔记.assets/image-20210615195740348.png)

条件运算符优先级比逗号要高

#### 4.11 类型转换

**隐式转换**

##### 4.11.1 算术转换

转换成最宽的类型

首先会做整型提升，小整数类型转换成大整数类型，char变int

然后再做转换

![image-20210615200410924](C++_笔记.assets/image-20210615200410924.png)

##### 4.11.2 其他隐式类型转换

**数组转换成指针**

##### 4.11.3 显示转换

强制类型转换

![image-20210615200845579](C++_笔记.assets/image-20210615200845579.png)

`static_cast`

只要不包含底层const

![image-20210615201000632](C++_笔记.assets/image-20210615201000632.png)

`const_cast`

![image-20210615201050638](C++_笔记.assets/image-20210615201050638.png)

`reinterpret_cast`

![image-20210615201209596](C++_笔记.assets/image-20210615201209596.png)

**练习**

![image-20210615201328222](C++_笔记.assets/image-20210615201328222.png)

![image-20210615201336736](C++_笔记.assets/image-20210615201336736.png)

#### 4.12 运算符优先级表

### 第五章 语句

#### 5.1 简单语句

; 空语句

**复合语句**

#### 5.2 语句作用域

**练习**

![image-20210615210411718](C++_笔记.assets/image-20210615210411718.png)

#### 5.3 条件语句

`if`和`switch`

##### 5.3.1 if语句

```c++
if ()
	;
else if ()
	;
```

![image-20210615210752859](C++_笔记.assets/image-20210615210752859.png)

**练习**

![image-20210615210903364](C++_笔记.assets/image-20210615210903364.png)

```c++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main() {
    int grade;
    cout << "请输入您的成绩：" << endl;
    cin >> grade;
    if (grade < 0 || grade > 100) {
        cout << "该成绩不合法" << endl;
        return -1;
    }
    if (grade == 100) {                             // 处理满分的情况
        cout << "等级成绩是：" << "A++" << endl;
        return 0;
    }
    const vector<string> scores = {"F", "D", "C", "B", "A"};
    string lettergrade;
    // 如果成绩不合格，不需要考虑添加加号减号的问题
    if (grade < 60)
        lettergrade = scores[0];
    else {
        lettergrade = scores[(grade - 50) / 10];    // 获得字母形式的成绩
        if (grade != 100)       // 只要不是 A++，就考虑添加加号减号
            if (grade % 10 > 7)
                lettergrade += '+';     // 末尾是 8 或者 9 的成绩添加一个加号
            else if (grade % 10 < 3)
                lettergrade += '-';     // 末尾是 0、1 或者 2 的成绩添加一个减号
    }
    cout << "等级成绩是：" << lettergrade << endl;

    return 0;
}
```

##### 5.3.2 switch语句

![image-20210615212418273](C++_笔记.assets/image-20210615212418273.png)

**练习**

![image-20210615212507112](C++_笔记.assets/image-20210615212507112.png)

```c++
#include <iostream>

using namespace std;

int main() {
    unsigned int vowelCnt = 0;
    char ch;
    cout << "请输入一段文本：" << endl;
    while (cin >> ch && ch != 'Q') {
        if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')
            ++vowelCnt;
    }
    cout << "您输入的文本中共有 " << vowelCnt << " 个元音字母" << endl;

    return 0;
}
```

![image-20210615213352829](C++_笔记.assets/image-20210615213352829.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
#include <vector>
using namespace std;

int main()
{
    unsigned int ff_cnt = 0, fl_cnt = 0, fi_cnt = 0;
    char ch, prech = '\0';
    cout << "请输入一段文本：" << endl;
    while (cin >> noskipws >> ch)
    {
        switch (ch)
        {
        case 'f':
            if (prech == 'f')
                ++ ff_cnt;
            break;
        case 'l':
            if (prech == 'f')
                ++ fl_cnt;
            break;
        case 'i':
            if (prech == 'f')
                ++ fi_cnt;
            break;
        }
        prech = ch;
    }
    cout << "ff 的数量是：" << ff_cnt << endl;
    cout << "fl 的数量是：" << fl_cnt << endl;
    cout << "fi 的数量是：" << fi_cnt << endl;

    return 0;
}
```

**case 标签必须是整型常量表达式**

#### 5.4 迭代语句

循环 

循环前检查条件：`while`和`for`

先执行循环体：`do while`

##### 5.4.1 while语句

```c++
while (condition)
	statement
```

1）不清楚迭代几次的时候。2）循环结束后访问循环控制变量

![image-20210619223457513](C++_笔记.assets/image-20210619223457513.png)

**练习**

```c++
int main()
{
    string s;
    string pres = "/0";
    string max_s;
    unsigned max_cnt = 1;
    unsigned temp_cnt = 1;
    while(cin >> s)
    {
        if(s == pres)
        {
            ++ temp_cnt;
            if (temp_cnt >= max_cnt){
                max_cnt = temp_cnt;
                max_s = s;
            }

        }
        else
            temp_cnt = 1;
        pres = s;
    }

    if (max_cnt == 1)
        cout << "没有连续出现过" << endl;
    else
        cout << max_s << "出现过" << max_cnt << endl;

    return 0;
}

int main()
{
	pair<string, int> max_duplicated;
	int cnt;

	for(string str, prestr; cin >> str; prestr = str)
    {
        if (str == prestr)
            ++cnt;
        else
            cnt = 0;
        if (cnt > max_duplicated.second)
            max_duplicated = {str, cnt};
    }

    if (max_duplicated.second == 1)
        cout << "No duplication" << endl;
    else
        cout << max_duplicated.first << " occurs " << max_duplicated.second + 1 << " times " << endl;

	return 0;
}
```

##### 5.4.2 传统的for语句

```c++
for (init-statemen; condition; expression) // 先执行init-statement，判断condition
	statement
```

**for语句头中的多重定义**

`init-statement`只能有一条声明语句，因此，所有变量的基础类型必须相同

**省略for语句头的某些部分**

任何一个都可以被空语句替换

**练习**

![image-20210619230222631](C++_笔记.assets/image-20210619230222631.png)

```c++
#include <iostream>
#include <vector>

using std::cout; using std::vector;

bool is_prefix(const vector<int>& lhs, const vector<int>& rhs)
{
	if (lhs.size() > rhs.size())
		return is_prefix(rhs, lhs);
	for (unsigned i = 0; i != lhs.size(); ++i)
		if (lhs[i] != rhs[i]) 
			return false;
	return true;
}

int main()
{
	vector<int> l{ 0, 1, 1, 2 };
	vector<int> r{ 0, 1, 1, 2, 3, 5, 8 };
	cout << (is_prefix(r, l) ? "yes\n" : "no\n");

	return 0;
}
```

##### 5.4.3 范围for语句

```
for (declaration : expression)
	statement
```

##### 5.4.4 do while 语句

```
do
	statement
while (condition);
```

![image-20210621135720675](README.assets/image-20210621135720675.png)

```c++
#include <iostream>
#include <string>

using std::cout; using std::cin; using std::endl; using std::string;

int main()
{
	string rsp;
	do
	{
		cout << "Input two strings: ";
		string str1, str2;
		cin >> str1 >> str2;
		cout << (str1 <= str2 ? str1 : str2)
			<< " is less than the other. " << "\n\n"
			<< "More? Enter yes or no: ";
		cin >> rsp;
	} while (tolower(rsp[0]) == 'y');
	return 0;
```

#### 5.5 跳转语句

`break`	`continue`	`goto`	 `return`

##### 5.5.1 break语句

![image-20210621140739658](README.assets/image-20210621140739658.png)

**练习**

![image-20210621140904240](README.assets/image-20210621140904240.png)

```c++
#include <iostream>
#include <string>
using std::cout; using std::cin; using std::endl; using std::string;

int main()
{
	string read, tmp;
	while (cin >> read)
		if (read == tmp) break; else tmp = read;

	if (cin.eof())  cout << "no word was repeated." << endl;
	else            cout << read << " occurs twice in succession." << endl;

	return 0;
}
```

##### 5.5.2 continue 语句

![image-20210621142735243](README.assets/image-20210621142735243.png)

##### 5.5.3 goto语句

![image-20210621142926153](README.assets/image-20210621142926153.png)

```
goto label;
label:
后面的都是
```

#### 5.6 try语句块和异常处理

![image-20210621144908679](README.assets/image-20210621144908679.png)

##### 5.6.1 throw表达式

异常检测部分使用throw表达式引发一个异常

![image-20210621145621854](README.assets/image-20210621145621854.png)

##### 5.6.2 try语句块

```c++
try {
	program-statements
} catch (exception-declaration) {
	handler-statements
}
```

```c++
while (true)
    {
        try
        {
            throw runtime_error("Data must refer to same ISBN");
        }
        catch (runtime_error err)
        {
            cout << err.what()
                << "\nTry Again? Enter y or n" << endl;
            char c;
            cin >> c;
            if (!cin || c == 'n')
                break;
        }
    }
    return 0;
```

##### 5.6.3 标准异常

![](README.assets/image-20210621151245793.png)

![image-20210621151306024](README.assets/image-20210621151306024.png)

**练习**

![image-20210621152523187](README.assets/image-20210621152523187.png)

```c++
#include <iostream>
#include <stdexcept>
using std::cin; using std::cout; using std::endl; using std::runtime_error;

int main(void)
{
	int i, j;
	cout << "please input tow numbers: " << endl;
	while (cin >> i >> j)
	{
		try
		{
			if (j == 0)
				throw runtime_error("divisor is 0");
			cout << i / j << endl;
		}
		catch (runtime_error err)
		{
			cout << err.what() << "\nTry Again? Enter y or n" << endl;
			char c;
			cin >> c;
			if (c != 'y')
				break;
		}
		cout << "please input tow numbers: " << endl;
	}

	return 0;
}
```

### 第六章 函数

函数定义和声明，包括参数传入函数以及如何返回结果

允许重载函数，即不同函数可以使用同一个名字

函数指针

#### 6.1 函数基础

返回类型、名字、形参数列表、函数体

**编写函数**

```c++
int fact(int val)
{
	int result = 1;
	while (val > 1)
		result *= val--;
	
	return result;
}
```

**调用函数**

![image-20210621155819965](README.assets/image-20210621155819965.png)

**形参和实参**

实参的类型和数量必须与形参匹配，类型会有强制类型转换

**函数的形参列表**

空：void f1(void)

必须把每个类型都写出来

任意两个形参不能同名，且函数最外层变量也不能同名

**函数返回类型**

不返回是void

返回类型不能是数组类型或函数类型，但是可以是指向数组或函数的指针

**练习**

![image-20210621160517444](README.assets/image-20210621160517444.png)

```c++
int fact(int i)
{
	return i > 1 ? i * fact(i - 1) : 1;
}

void interactive_fact()
{
	std::string const prompt = "Enter a number within [1, 13) :\n";
	std::string const out_of_range = "Out of range, please try again.\n";
	for (int i; std::cout << prompt, std::cin >> i;)
	{
		if (i < 1 || i > 12)
		{
			std::cout << out_of_range;
			continue;
		}
		std::cout << fact(i) << std::endl;
	}
}

int main()
{
	interactive_fact();
	return 0;
}
```

![image-20210621163328146](README.assets/image-20210621163328146.png)

```c++
#include <iostream>

int abs(int i)
{
    return i > 0 ? i : -i;
}

int main()
{
    std::cout << abs(-5) << std::endl;
    return 0;
}
```

##### 6.1.1 局部对象

![image-20210621164317561](README.assets/image-20210621164317561.png)

**自动对象**

**局部静态对象**（定义的时候会被初始化，其他都不会）

![image-20210621164425135](README.assets/image-20210621164425135.png)

![image-20210621164700597](README.assets/image-20210621164700597.png)

##### 6.1.2 函数声明

只可以定义一次，声明多次。 如果一个函数永远不会被用到，可以只有声明，没有定义。

声明无需函数体，用一个分号代替

可以无需形参的名字，但是也最好写

**在头文件中进行函数声明**

##### 6.1.3 分离式编译

![image-20210621165134978](README.assets/image-20210621165134978.png)

**编译和链接多个源文件**

如果修改了一个源文件，只需要重新编译改动了的文件

![image-20210621165312876](README.assets/image-20210621165312876.png)

#### 6.2 参数传递

![image-20210621170357358](README.assets/image-20210621170357358.png)

引用的话才可以更改原来的值**引用调用**，不然的话只是拷贝**值传递**

##### 6.2.1 传值参数

形参操作不影响实参

**指针形参**

![image-20210621170715170](README.assets/image-20210621170715170.png)

![image-20210621170703165](README.assets/image-20210621170703165.png)

**练习**

![image-20210621170912639](README.assets/image-20210621170912639.png)

```c++
#include <iostream>
#include <string>

void swap(int* lhs, int* rhs)
{
	int tmp;
	tmp = *lhs;
	*lhs = *rhs;
	*rhs = tmp;
}

int main()
{
	for (int lft, rht; std::cout << "Please Enter:\n", std::cin >> lft >> rht;)
	{
		swap(&lft, &rht);
		std::cout << lft << " " << rht << std::endl;
	}

	return 0;
}
```

##### 6.2.2 传引用参数

相当于别名

**使用引用避免拷贝**

​	拷贝比较低效，且有的不支持拷贝操作

![image-20210621204027537](README.assets/image-20210621204027537.png)

**使用引用形参返回额外信息**

可以帮助返回多个值

![image-20210621204220188](README.assets/image-20210621204220188.png)

**练习**

![image-20210621210034547](README.assets/image-20210621210034547.png)

```c++
#include <iostream>
#include <string>

void swap(int &lhs, int &rhs)
{
	int tmp;
	tmp = lhs;
	lhs = rhs;
	rhs = tmp;
}

int main()
{
	for (int lft, rht; std::cout << "Please Enter:\n", std::cin >> lft >> rht;)
	{
		swap(lft, rht);
		std::cout << lft << " " << rht << std::endl;
	}

	return 0;
}
```

##### 6.2.3 const 形参和实参

![image-20210621211236860](README.assets/image-20210621211236860.png)

**指针或 引用形参与const**

**尽量使用常量引用**

**练习**

![image-20210621212701029](README.assets/image-20210621212701029.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
using namespace::std;
bool is_upper(const string &s)
{
    for (auto c : s)
        if (isupper(c))
            return false;
        else
            return true;
}

string to_lowercase(string &s)
{
    for (auto &c : s)
        if (isupper(c))
            c = tolower(c);
    return s;
}

int main()
{
	string str = "adFasdf";

	cout << is_upper(str) << endl;
    cout << to_lowercase(str) << endl;

	return 0;
}
```

##### 6.2.4 数组形参

数组不允许拷贝数组；使用数组时会将其转换成指针

所以实际上传递的是首元素的指针

![image-20210621220251521](README.assets/image-20210621220251521.png)

函数不知道数组的确切尺寸，所以

**使用标记指定数组长度**

要求数组本身包含一个结束标记，C风格字符串

![image-20210621220808170](README.assets/image-20210621220808170.png)

**使用标准库规范**

传递首元素和尾后元素

![image-20210621220910952](README.assets/image-20210621220910952.png)

**显示传递一个表示数组大小的形参**

![image-20210621220957711](README.assets/image-20210621220957711.png)

**数组形参和const**

![image-20210621221442428](README.assets/image-20210621221442428.png)

**数组引用形参**

![image-20210621221511971](README.assets/image-20210621221511971.png)

这个会有大小限制

**传递多维数组**

![image-20210621222517735](README.assets/image-20210621222517735.png)

![image-20210621222530334](README.assets/image-20210621222530334.png)

**练习**

![image-20210621223844280](README.assets/image-20210621223844280.png)

```c++
#include <iostream>
#include <string>
#include <cctype>
using namespace::std;

void swap(int *&lft, int *&rft)
{
    auto tmp = lft;
    lft =rft;
    rft = tmp;
}

int main()
{
	int i = 42, j = 99;
	auto lft = &i;
	auto rht = &j;
	swap(lft, rht);
	cout << *lft << " " << *rht << endl;
	return 0;
}
```

##### 6.2.5 main: 处理命令行选项

![image-20210621224538314](README.assets/image-20210621224538314.png)

![image-20210621224622965](README.assets/image-20210621224622965.png)

![image-20210621224632413](README.assets/image-20210621224632413.png)

![image-20210621224648571](README.assets/image-20210621224648571.png)

![image-20210621224904969](README.assets/image-20210621224904969.png)

![image-20210621225317028](README.assets/image-20210621225317028.png)

```c++
#include <iostream>
#include <string>

int main(int argc, char **argv)
{
	std::string str;
	for (int i = 1; i != argc; ++i)
		str += std::string(argv[i]) + " ";

	std::cout << str << std::endl;
	return 0;
}
```

##### 6.2.6 含有可变形参的函数

两种方法： 

* 所有实参类型相同： `initializer_list`
* 特殊函数，可变参数模板

**initializer_list**

![image-20210621232930601](README.assets/image-20210621232930601.png)

![image-20210621233033477](README.assets/image-20210621233033477.png)

**省略符形参**

![image-20210621233304168](README.assets/image-20210621233304168.png)

**练习**

![image-20210621233342615](README.assets/image-20210621233342615.png)

```c++
  
#include <iostream>
#include <initializer_list>

int sum(std::initializer_list<int> const& il)
{
	int sum = 0;
	for (auto i : il) 
		sum += i;
	return sum;
}

int main(void)
{
	auto il = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
	std::cout << sum(il) << std::endl;

	return 0;
}
```

#### 6.3 返回类型和return语句

##### 6.3.1 无返回值函数

* 无返回值
* void函数

`return;`

##### 6.3.2 有返回值函数

保证类型是正确的

![image-20210621234820995](README.assets/image-20210621234820995.png)

**值如何被返回**

![image-20210621235234202](README.assets/image-20210621235234202.png)

**不要返回局部对象的引用和指针**

![image-20210621235347804](README.assets/image-20210621235347804.png)

**返回类类型的函数和调用运算符**

类类型可以访问结果对象的成员

**引用返回左值**

引用是左值，其他返回类型是右值

所以函数引用返回可以在赋值语句的左侧

![image-20210622202736191](README.assets/image-20210622202736191.png)

**列表初始化返回值**

![image-20210630143337517](README.assets/image-20210630143337517.png)

**主函数main的返回值**

![image-20210630143732773](README.assets/image-20210630143732773.png)

**递归**

函数调用了自身

递归循环

**练习**

![image-20210705210322614](README.assets/image-20210705210322614.png)

```c++
#include <iostream>
#include <string>
#include <cstdlib>
#include <vector>
using namespace::std;

void print(vector<int> ivec, auto index)
{
    if(index != ivec.size())
    {
        cout << ivec[index] << endl;
        print(ivec, index + 1);
    }
    return;
}

int main()
{
    vector<int> ivec = {1, 2, 32, 43};
    print(ivec, 0);

    return 0;
}
```

##### 6.3.3 返回数组指针

因为数组不能被拷贝，所以不能返回数组，只能返回数组的指针或引用

使用类型别名

![image-20210705210524895](README.assets/image-20210705210524895.png)

**声明一个返回数组指针的函数**

![image-20210705210704326](README.assets/image-20210705210704326.png)

**使用尾置返回类型**

![image-20210705210811948](README.assets/image-20210705210811948.png)

**使用decltype**

![image-20210705210944964](README.assets/image-20210705210944964.png)

**练习**

![image-20210705212359518](README.assets/image-20210705212359518.png)

```c++
string (&func())[10];

typedef string arr[10];
arr &func();

auto func() -> string (&)[10];

string str[10];
decltype(str) &func();
```

#### 6.4 函数重载

同一作用域，名字相同但形参列表不同：**重载函数**

main函数不能重载

**定义重载函数**

![image-20210705212711178](README.assets/image-20210705212711178.png)

![image-20210705212744910](README.assets/image-20210705212744910.png)

**判断两个形参的类型是否相异**

省略名字和别名还是相同

**重载和const形参**

顶层const

![image-20210706142637846](README.assets/image-20210706142637846.png)

底层const

![image-20210706142652729](README.assets/image-20210706142652729.png)

优先使用非常量版本的函数

**const_cast和重载**

![image-20210706143038750](README.assets/image-20210706143038750.png)

**调用重载的函数**

* 最佳匹配
* 无匹配的错误信息
* 二义性调用：有多个函数可以匹配

##### 6.4.1 重载于作用域

![image-20210706144211630](README.assets/image-20210706144211630.png)

#### 6.5 特殊用途语言特性

* 默认实参
* 内联函数
* constexpr函数

#### 6.5.1 默认实参

一旦某个形参被赋予了默认值，后面的所有形参都必须有默认值

**使用默认实参调用函数**

直接省略就好

**默认实参声明**

只能赋予一次实参

![image-20210706144945725](README.assets/image-20210706144945725.png)

**默认实参初始化**

局部变量不能作为默认实参，其他只要可以转换的就可以

##### 6.5.2 内联函数和const而向旁人函数

**内联函数可避免函数调用的开销**

在编译时直接替换

只要在返回类型前面加上inline就好了

![image-20210706145911654](README.assets/image-20210706145911654.png)

![image-20210706145930069](README.assets/image-20210706145930069.png)

**constexpr 函数**

constexpr 函数是指能用于常量表达式的函数，constexpr 函数的返回类型和所有形参的类型都得是字面值类型，而且函数体中必须有且只有一条 return 语句。

**把内联函数和constexpr函数放在头文件内**

#### 6.5.3 调试帮助

用于调试的代码

预处理功能：assert和NDEBUG

**assert预处理宏**

类似内联函数

![image-20210706152436787](README.assets/image-20210706152436787.png)

**NDEBUG预处理变量**

![image-20210706152619502](README.assets/image-20210706152619502.png)

![image-20210706152731997](README.assets/image-20210706152731997.png)

**练习**

![image-20210706152922381](README.assets/image-20210706152922381.png)

```c++
#include <iostream>
#include <vector>

using namespace std;

// 递归函数输出 vector<int> 的内容
void print(vector<int> vInt, unsigned index) {
    unsigned sz = vInt.size();
    // 设置在此处输出调试信息
    #ifndef NDEBUG
    cout << "vector 对象的大小是：" << sz << endl;
    #endif // NDEBUG
    if (!vInt.empty() && index < sz) {
        cout << vInt[index] << endl;
        print(vInt,index + 1);
    }
}

int main() {
    vector<int> v = {1, 3, 5, 7, 9, 11, 13, 15};
    print(v, 0);
    return 0;
}
```

#### 6.6 函数匹配

形参数量相等且可以类型转换时

**确定候选函数和可行函数**

候选函数就是名字

科兴函数就是实参数量以及类型

**寻找最佳匹配**

类型越匹配

**含有多个形参的函数匹配**

![image-20210706154257629](README.assets/image-20210706154257629.png)

![image-20210706154244811](README.assets/image-20210706154244811.png)

![image-20210706154314461](README.assets/image-20210706154314461.png)

#### 6.6.1 实参类型转换

1.精确匹配

2.const

3.类型提升

4.算数类型转换

5.类类型转换

**需要类型提升和算术类型转换 的匹配**

**函数匹配和const实参**

#### 6.7 函数指针

![image-20210706160311214](README.assets/image-20210706160311214.png)

**使用函数指证**

![image-20210706160438472](README.assets/image-20210706160438472.png)

不需要取地址符，也不需要解引用

**重载函数的指针**

![image-20210706160625651](README.assets/image-20210706160625651.png)

**函数指针形参**

![image-20210706160817201](README.assets/image-20210706160817201.png)

**返回指向函数的指针**

![image-20210706160915590](README.assets/image-20210706160915590.png)

也可以尾置

**将auto和decltype用于函数指针类型**

![image-20210706161016452](README.assets/image-20210706161016452.png)

### 第七章 类

类的基本思想是**数据抽象**和**封装**。

数据抽象依赖于接口和实现，封装实现了类的接口和实现的分离

#### 7.1 定义抽象数据类型

令Sales_data变成抽象数据类型

##### 7.1.1 设计Sales_data类

![image-20210706203916608](README.assets/image-20210706203916608.png)

**练习**

![image-20210707134732752](README.assets/image-20210707134732752.png)

Sale_data.h

```c++
#ifndef TEST_SALES_DATA_H
#define TEST_SALES_DATA_H

// Definition of Sales_data class and related functions goes here
#include <iostream>
#include <string>

// 头文件不应包含 using 声明
// using namespace std;

class Sales_data {
    // 友元函数
    friend std::istream &operator>>(std::istream &, Sales_data &);

    // 友元函数
    friend std::ostream &operator<<(std::ostream &, const Sales_data &);

    // 友元函数
    friend bool operator<(const Sales_data &, const Sales_data &);

    // 友元函数
    friend bool operator==(const Sales_data &, const Sales_data &);

public:     // 构造函数的 3 种形式
    Sales_data() = default;

    Sales_data(const std::string &book) : bookNo(book) {}

    Sales_data(std::istream &is) { is >> *this; }

    Sales_data &operator+=(const Sales_data &);

    std::string isbn() const { return bookNo; }

private:
    std::string bookNo;         // 书籍编号，隐式初始化为空串
    unsigned units_sold = 0;    // 销售量，显式初始化为 0
    double sellingprice = 0.0;  // 原始价格，显式初始化为 0.0
    double saleprice = 0.0;     // 实售价格，显式初始化为 0.0
    double discount = 0.0;      // 折扣，显式初始化为 0.0
};

inline bool compareIsbn(const Sales_data &lhs, const Sales_data &rhs) {
    return lhs.isbn() == rhs.isbn();
}

Sales_data operator+(const Sales_data &, const Sales_data &);

inline bool operator==(const Sales_data &lhs, const Sales_data &rhs) {
    return lhs.units_sold == rhs.units_sold &&
           lhs.sellingprice == rhs.sellingprice &&
           lhs.saleprice == rhs.saleprice &&
           lhs.isbn() == rhs.isbn();
}

inline bool operator!=(const Sales_data &lhs, const Sales_data &rhs) {
    return !(lhs == rhs);   // 基于运算符 == 给出 != 的定义
}

Sales_data &Sales_data::operator+=(const Sales_data &rhs) {
    units_sold += rhs.units_sold;
    saleprice = (rhs.saleprice * rhs.units_sold + saleprice * units_sold)
                / (rhs.units_sold + units_sold);
    if (sellingprice != 0)
        discount = saleprice / sellingprice;
    return *this;
}

Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs) {
    Sales_data ret(lhs);    // 把 lhs 的内容拷贝到临时变量 ret 中，这种做法便于运算
    ret += rhs;             // 把 rhs 的内容加入其中
    return ret;             // 返回 ret
}

std::istream &operator>>(std::istream &in, Sales_data &s) {
    in >> s.bookNo >> s.units_sold >> s.sellingprice >> s.saleprice;
    if (in && s.sellingprice != 0)
        s.discount = s.saleprice / s.sellingprice;
    else
        s = Sales_data();   // 输入错误，重置输入的数据
    return in;
}

std::ostream &operator<<(std::ostream &out, const Sales_data &s) {
    out << s.isbn() << " " << s.units_sold << " "
        << s.sellingprice << " " << s.saleprice << " " << s.discount;
    return out;
}

#endif //TEST_SALES_DATA_H
```

main.cpp

```c++
#include <iostream>
#include "Sales_data.h"
using namespace std;

int main() {
    cout << "请输入交易记录（ISBN、销售量、原价、实际售价）：" << endl;
    Sales_data total;               // 保存当前求和结果的变量
    if (cin >> total) {             // 读入第一笔交易记录
         Sales_data trans;          // 保存下一条交易数据的变量
         while (cin >> trans) {     // 读入剩余的交易
             if (total.isbn() == trans.isbn())  // 检查 isbn
                 total += trans;    // 更新变量 total 当前的值
             else {
                 cout << total << endl;     // 输出结果
                 total = trans;             // 处理下一本
             }
         }
         cout << total << endl;     // 输出最后一条交易
    }
    else {                              // 没有输入任何信息
        cerr << "No data?!" << endl;    // 通知用户
        return -1;
    }
    return 0;
}
```



##### 7.1.2 定义改进的Sales_data类

![image-20210706232328598](README.assets/image-20210706232328598.png)

**定义成员函数** 

![image-20210706233001107](README.assets/image-20210706233001107.png)

**引入this**

![image-20210706233115263](README.assets/image-20210706233115263.png)

**引入const成员函数**

![image-20210706233328694](README.assets/image-20210706233328694.png)

![image-20210706234131838](README.assets/image-20210706234131838.png)

这里面为什么需要用到参数列表后面的const呢？因为在实际调用的时候

```c++
inline bool compare_isbn(const Sales_data &lhs, const Sales_data &rhs)
{
    return lhs.isbn() == rhs.isbn();
}
```

所以需要修改this指针的类型

**类作用域和成员函数**

![image-20210706234553664](README.assets/image-20210706234553664.png)

**在类的外部定义成员函数**

![image-20210706234641457](README.assets/image-20210706234641457.png)

**定义一个返回this对象的函数**

![image-20210706234814903](README.assets/image-20210706234814903.png)

引用对应 `*this`，就可以返回本身对象

**练习**

![image-20210707134144829](README.assets/image-20210707134144829.png)

```c++
std::string isbn() const { return bookNo;}

Sales_data & combine(const Sales_data &rhs)
{
    sale_price = (rhs.sale_price * rhs.units_sold + sale_price * units_sold) / (rhs.units_sold + units_sold);
    units_sold += rhs.units_sold;
    if (selling_price != 0)
        discount = sale_price / selling_price;
    return *this;
}
```

![image-20210707134219701](README.assets/image-20210707134219701.png)

```
total.combine(trans);
```

![image-20210707134845512](README.assets/image-20210707134845512.png)

Person.h

```c++
#ifndef PERSON_H_INCLUDED
#define PERSON_H_INCLUDED

#include <iostream>
#include <string>

class Person
{
    friend std::istream &operator>>(std::istream &, Person &);

    friend std::ostream &operator<<(std::ostream &, Person &);
public:
    std::string get_name() const { return person_name; }
    std::string get_address() const { return address; }
private:
    std::string person_name;
    std::string address;
};

std::istream &operator>>(std::istream &is, Person &pes)
{
    is >> pes.person_name >> pes.address;
    return is;
}

std::ostream &operator<<(std::ostream &os, Person &pes)
{
    os << pes.person_name << '\t' << pes.address;
    return os;
}
#endif // PERSON_H_INCLUDED
```

##### 7.1.3 定义类相关的非成员函数

跟类声明在同一个头文件内

**定义read和print函数**

![image-20210707151720866](README.assets/image-20210707151720866.png)

**定义add函数**

![image-20210707151754806](README.assets/image-20210707151754806.png)

**练习**

![image-20210707152716512](README.assets/image-20210707152716512.png)

Sale_data.h

```c++
#ifndef TEST_SALES_DATA_H
#define TEST_SALES_DATA_H

// Definition of Sales_data class and related functions goes here
#include <iostream>
#include <string>

// 头文件不应包含 using 声明
// using namespace std;

class Sales_data {
private:                            // 定义私有数据成员
    std::string bookNo;             // 书籍编号，隐士初始化为空串
    unsigned units_sold = 0;        // 销售量，显示初始化为 0
    double sellingprice = 0.0;      // 原始售价，显示初始化为 0.0
    double saleprice = 0.0;         // 实售价格，显示初始化为 0.0
    double discount = 0.0;          // 折扣，显示初始化为 0.0
public:                             // 定义公有函数成员
    // isbn 函数只有一条语句，返回 bookNo
    std::string isbn() const { return bookNo; }
    // combine 函数用于把两个 ISBN 相同的销售记录合并在一起
    Sales_data& combine(const Sales_data &rhs) {
        units_sold += rhs.units_sold;   // 把 rhs 的成员加到 this 对象的成员上
        saleprice = (rhs.saleprice * rhs.units_sold + saleprice * units_sold)
                    / (rhs.units_sold + units_sold);    // 计算平均实际售价
        if (sellingprice != 0)
            discount = saleprice / sellingprice;    // 计算 this 对象的折扣
        return *this;               // 返回调用该函数的对象
    }
    Sales_data add(const Sales_data &lhs, const Sales_data &rhs);
    std::istream &read(std::istream &is, Sales_data &item);
    std::ostream &print(std::ostream &os, const Sales_data &item);
};

Sales_data Sales_data::add(const Sales_data &lhs, const Sales_data &rhs) {
    Sales_data sum = lhs;
    sum.combine(rhs);
    return sum;
}

std::istream &Sales_data::read(std::istream &is, Sales_data &item) {
    is >> item.bookNo >> item.units_sold >> item.sellingprice >> item.saleprice;
    if (is && item.sellingprice != 0)
        item.discount = item.saleprice / item.sellingprice;
    else
        item = Sales_data();   // 输入错误，重置输入的数据
    return is;
}

std::ostream &Sales_data::print(std::ostream &os, const Sales_data &item) {
    os << item.isbn() << " " << item.units_sold << " " << item.sellingprice
       << " " << item.saleprice << " " << item.discount;
    return os;
}

#endif //TEST_SALES_DATA_H
```

main.cpp

```c++
#include "Sales_data.h"
using namespace std;

int main() {
    cout << "请输入交易记录（ISBN、销售量、原价、实际售价）：" << endl;
    Sales_data total;               // 保存当前求和结果的变量
    if (total.read(cin, total)) {             // 读入第一笔交易记录
        Sales_data trans;          // 保存下一条交易数据的变量
        while (trans.read(cin, trans)) {     // 读入剩余的交易
            if (total.isbn() == trans.isbn())  // 检查 isbn
                total = total.add(total, trans);     // 更新变量 total 当前的值
            else {
                total.print(cout, total) << endl;    // 输出结果
                total = trans;                 // 处理下一本
            }
        }
        total.print(cout, total) << endl;            // 输出最后一条交易
    }
    else {                              // 没有输入任何信息
        cerr << "No data?!" << endl;    // 通知用户
        return -1;
    }
    return 0;
}
```

![image-20210707152901476](README.assets/image-20210707152901476.png)

```c++
std::istream &Person::read(std::istream &is, Person &pes)
{
    is >> pes.person_name >> pes.address;
    return is;
}

std::ostream &Person::print(std::ostream &os, const Person &pes)
{
    os << pes.person_name << '\t' << pes.address;
    return os;
}
```

##### 7.1.4 构造函数

初始化类对象的数据成员

**合成的默认构造函数**

![image-20210707164503769](README.assets/image-20210707164503769.png)

**某些类不能依赖于合成的默认构造函数**

![image-20210707164602216](README.assets/image-20210707164602216.png)

所以需要定义默认构造函数

**定义Sales_data的构造函数**

![image-20210707164804458](README.assets/image-20210707164804458.png)

**= default的含义**

要求编译器生成构造函数

**构造函数初始值列表**

![image-20210707164930298](README.assets/image-20210707164930298.png)

**在类的外部定义构造函数**

![image-20210707165116589](README.assets/image-20210707165116589.png)

**练习**

![image-20210707172912135](README.assets/image-20210707172912135.png)

```c++
Person() = default;
Person(const std::string &nam, const std::string &add) : person_name(nam), address(add) {}
Person(std::istream &);

Person::Person(std::istream &is)
{
    read(is, *this);
}
```

##### 7.1.5 拷贝、赋值和析构

**某些类不能依赖于合成的版本**

![image-20210707175112285](README.assets/image-20210707175112285.png)

#### 7.2 访问控制与封装

访问说明符加强类的封装

![image-20210707175234364](README.assets/image-20210707175234364.png)

**使用class或struct关键字**

struct默认public，class默认private

##### 7.2.1 友元

![image-20210707180818509](README.assets/image-20210707180818509.png)

![image-20210707180906970](README.assets/image-20210707180906970.png)

![image-20210707180924292](README.assets/image-20210707180924292.png)

#### 7.3 类的其他特性

##### 7.3.1 类成员再探

Screen和Window-mgr

**定义一个类型成员**

1.自定义某种类型在类中的别名

![image-20210707184234869](README.assets/image-20210707184234869.png)

要先定义后使用

**Screen类的成员函数**

![image-20210707184434817](README.assets/image-20210707184434817.png)

**令成员作为内联函数**

最好只在类外部定义的地方说明inline

![image-20210707184633075](README.assets/image-20210707184633075.png)

**重载成员函数**

一样的

**可变数据成员**

`mutable` 即使在const成员函数中也可以被修改

**类数据成员的初始值**

![image-20210707184958769](README.assets/image-20210707184958769.png)

![image-20210707185029144](README.assets/image-20210707185029144.png)

**练习**

![image-20210707185205851](README.assets/image-20210707185205851.png)

```c++
class Screen {
private:
    unsigned height = 0, width = 0;
    unsigned cursor = 0;
    string contents;

public:
    Screen() = default;     // 默认构造函数
    Screen(unsigned ht, unsigned wd) : height(ht), width(wd),
        contents(ht * wd, ' ') { }
    Screen(unsigned ht, unsigned wd, char c)
        : height(ht), width(wd), contents(ht * wd, c) { }
};
```

![image-20210707185306635](README.assets/image-20210707185306635.png)

含有指针数据成员的类一般不宜使用默认的拷贝和赋值操作，如果类的数据成员都是内置类型的，则不受干扰。

##### 7.3.2 返回*this的成员函数

**从const成员函数返回*this**

![image-20210707185724062](README.assets/image-20210707185724062.png)

**基于const的重载**

![image-20210707191744630](README.assets/image-20210707191744630.png)

**练习**

![image-20210707192317332](README.assets/image-20210707192317332.png)

Screen.h

```c++
#ifndef SCREEN_H_INCLUDED
#define SCREEN_H_INCLUDED

#include <iostream>

class Screen {
private:
    unsigned height = 0, width = 0;
    unsigned cursor = 0;
    std::string contents;

public:
    Screen() = default;     // 默认构造函数
    Screen(unsigned ht, unsigned wd) : height(ht), width(wd),
                                       contents(ht * wd, ' ') {}

    Screen(unsigned ht, unsigned wd, char c)
            : height(ht), width(wd), contents(ht * wd, c) {}

public:
    Screen &move(unsigned r, unsigned c) {
        cursor = r * width + c;
        return *this;
    }
    Screen &set(char ch) {
        contents[cursor] = ch;
        return *this;
    }
    Screen &set(unsigned r, unsigned c, char ch) {
        contents[r * width + c] = ch;
        return *this;
    }
    Screen &display(std::ostream &os) {
        os << contents;
        return *this;
    }
};

#endif // SCREEN_H_INCLUDED

```

main.cpp

```c++
#include <iostream>
#include "Screen.h"

int main() {
    Screen myScreen(5, 5, 'X');
    myScreen.display(std::cout);
    std::cout << "\n";
    myScreen.move(4, 0).set('#').display(std::cout);
    std::cout << "\n";
    myScreen.display(std::cout);
    std::cout << "\n";

    return 0;
}
```

##### 7.3.3 类类型

![image-20210707192501478](README.assets/image-20210707192501478.png)

![image-20210707192531543](README.assets/image-20210707192531543.png)

**类的声明**

声明和定义可以分开

前向声明，不完全类型

##### 7.3.4 友元再探

![image-20210707194936468](README.assets/image-20210707194936468.png)

**类之间的友元关系**

![image-20210707195627702](README.assets/image-20210707195627702.png)

友元关系不存在传递性

![image-20210707195733436](README.assets/image-20210707195733436.png)

**令成员函数作为友元**

![image-20210707195828435](README.assets/image-20210707195828435.png)

![image-20210707195852198](README.assets/image-20210707195852198.png)

**函数重载和友元**

要对每个重载函数分别声明

**友元声明和作用域**

![image-20210707200037409](README.assets/image-20210707200037409.png)

**练习**

![image-20210707200637079](README.assets/image-20210707200637079.png)

```c++
#include <iostream>
#include <string>
using namespace std;

class Window_mgr {
public:
    void clear();
};

class Screen {
    friend void Window_mgr::clear();

private:
    unsigned height = 0, width = 0;
    unsigned cursor = 0;
    std::string contents;
public:
    Screen() = default;     // 默认构造函数
    Screen(unsigned ht, unsigned wd, char c)
            : height(ht), width(wd), contents(ht * wd, c) {}
};

void Window_mgr::clear() {
    Screen myScreen(10, 20, 'X');
    cout << "清理之前 myScreen 的内容是：" << endl;
    cout << myScreen.contents << endl;
    myScreen.contents = "";
    cout << "清理之后 myScreen 的内容是：" << endl;
    cout << myScreen.contents << endl;
}

int main() {
    Window_mgr w;
    w.clear();
    return 0;
}
```

#### 7.4 类的作用域

**作用域和定义在类外部的成员**

一个类就是一个作用域

第一种

![image-20210707200919760](README.assets/image-20210707200919760.png)

第二种

![image-20210707200932102](README.assets/image-20210707200932102.png)

##### 7.4.1 名字查找与类的作用域

![image-20210707201644055](README.assets/image-20210707201644055.png)

![image-20210707201042142](README.assets/image-20210707201042142.png)

**用于类成员声明的名字查找**

**类型名要特殊处理**

![image-20210707201305214](README.assets/image-20210707201305214.png)

**成员定义中的普通块作用域的名字查找**

![image-20210707201617965](README.assets/image-20210707201617965.png)

![image-20210707201523485](README.assets/image-20210707201523485.png)

**类作用域之后，在外围的作用域中查找**

![image-20210707201744580](README.assets/image-20210707201744580.png)

#### 7.5 构造函数再探

##### 7.5.1 构造函数初始值列表

![image-20210707202117399](README.assets/image-20210707202117399.png)

![image-20210707202141154](README.assets/image-20210707202141154.png)

![image-20210707202155713](README.assets/image-20210707202155713.png)

**成员初始化的顺序**

![image-20210707205436952](README.assets/image-20210707205436952.png)

![image-20210707205443869](README.assets/image-20210707205443869.png)

**默认实参和构造函数**

相当于在参数表里面设定一个值

![image-20210707205607366](README.assets/image-20210707205607366.png)

##### 7.5.2 委托构造函数

![image-20210707205922824](README.assets/image-20210707205922824.png)

就只写一个构造函数，别的构造函数都利用这个构造函数生成

##### 7.5.3 默认构造函数的作用

![image-20210707210223666](README.assets/image-20210707210223666.png)

**使用默认构造函数**

![image-20210707210308610](README.assets/image-20210707210308610.png)

**练习**

![image-20210707210447048](README.assets/image-20210707210447048.png)

上述语句的含义是创建一个 vector 对象 vec，该对象包含 10 个元素，每个元素的类型都是 NoDefault 且执行默认初始化。然而，因为我们在类 NoDefault 的定义中没有设计默认构造函数，所以所需的默认初始化过程无法执行。编译器会报告这一错误。

##### 7.5.4 隐式的类类型转换

转换构造函数

![image-20210707210830248](README.assets/image-20210707210830248.png)

![image-20210707210644780](README.assets/image-20210707210644780.png)

**只允许一步类类型转换**

![image-20210707210803844](README.assets/image-20210707210803844.png)

**抑制构造函数定义的隐式转换**

加`explicit`

![image-20210707211010419](README.assets/image-20210707211010419.png)

explicit只能用于直接初始化

![image-20210707211046698](README.assets/image-20210707211046698.png)

**为转换显示地使用构造函数**

![image-20210707211126469](README.assets/image-20210707211126469.png)

##### 7.5.5 聚合类

![image-20210707211603132](README.assets/image-20210707211603132.png)

![image-20210707211632741](README.assets/image-20210707211632741.png)

##### 7.5.6 字面值常量类

![image-20210707211752290](README.assets/image-20210707211752290.png)

**constexpr构造函数**

![image-20210707211833331](README.assets/image-20210707211833331.png)

#### 7.6 类的静态成员

**声明静态成员**

`static`

![image-20210707220020723](README.assets/image-20210707220020723.png)

**使用类的静态成员**

![image-20210707220127443](README.assets/image-20210707220127443.png)

![image-20210707220143160](README.assets/image-20210707220143160.png)

**定义静态成员**

![image-20210707220233991](README.assets/image-20210707220233991.png)

![image-20210707220333421](README.assets/image-20210707220333421.png)

**静态成员能用于某些场景**

![image-20210707220502726](README.assets/image-20210707220502726.png)

![image-20210707220535811](README.assets/image-20210707220535811.png)

## 第II部分 C++标准库

### 第八章 IO库

#### 8.1 IO类

![image-20210708155853065](README.assets/image-20210708155853065.png)

**IO类型间的关系**

![image-20210708160117407](README.assets/image-20210708160117407.png)

![image-20210708160126296](README.assets/image-20210708160126296.png)

##### 8.1.1 IO对象无拷贝或赋值

所以需要设置成引用

##### 8.1.2 条件状态

确定一个流对象 的状态最简单对的方法是将它当作一个条件来使用

![image-20210708161124491](README.assets/image-20210708161124491.png)

**查询流的状态**

**管理条件状态**

![image-20210708161236439](README.assets/image-20210708161236439.png)

![image-20210708161243031](README.assets/image-20210708161243031.png)

**练习**

![image-20210708161702504](README.assets/image-20210708161702504.png)

```c++
#include <iostream>
using namespace std;

istream& func(istream &is)
{
    std::string buf;
    while (is >> buf)
        std::cout << buf << std::endl;
    is.clear();
    return is;
}

int main() {
    cout << "请输入一些整数，按 Ctrl+Z 结束" << endl;
    func(cin);

    return 0;
}
```

##### 8.1.3 管理输出缓存

文本串可能立即打印出来，也可能保存在缓冲区

缓冲刷新（数据真正写到输出设备或文件）：

* endl显式刷新

**刷新输出缓冲区**

![image-20210708162145310](README.assets/image-20210708162145310.png)

**unitbuf操纵符**

![image-20210708162225458](README.assets/image-20210708162225458.png)

![image-20210708162253167](README.assets/image-20210708162253167.png)

**关联输入和输出流**

cin会导致cout的缓冲区刷新

#### 8.2 文件输入输出

头文件`fstream`

`ifstream`:读数据

`ofstream`:写数据

![image-20210708224256960](README.assets/image-20210708224256960.png)

##### 8.2.1 使用文件流对象

![image-20210708224556207](README.assets/image-20210708224556207.png)

**用fstream代替iostream&**

![image-20210708225013986](README.assets/image-20210708225013986.png)

**成员函数open和close**

![image-20210714194015596](README.assets/image-20210714194015596.png)

![image-20210714194024763](README.assets/image-20210714194024763.png)

![image-20210714194100515](README.assets/image-20210714194100515.png)

**自动构造和析构**

![image-20210714194154282](README.assets/image-20210714194154282.png)

 **练习**

![image-20210714214129765](README.assets/image-20210714214129765.png)

```c++
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

using namespace std;

int main() {
    // ../data 为文件data的文件名及其相对路径（是相对于可执行程序所在目录的相对路径）
    ifstream in("data.txt");         // 打开文件
    if (!in) {
        cerr << "无法打开输入文件" << endl;
        return -1;
    }

    string line;
    vector<string> words;
    while (getline(in, line))       // 从文件中读取一行
        words.push_back(line);      // 添加到 vector 中

    in.close();                     // 输入完毕，关闭文件

    vector<string>::const_iterator it = words.begin();  // 迭代器
    while (it != words.end()) {     // 遍历 vector
        cout << *it << endl;        // 输出 vector 中的元素
        ++it;
    }

    return 0;
}
```

![image-20210714214933405](README.assets/image-20210714214933405.png)

```c++
#include <iostream>
#include <fstream>
#include "Sales_data.h"
using namespace std;

int main(int argc, char *argv[]) {
    if (argc != 2) {
        cerr << "请给出文件名" << endl;
        return -1;
    }
    ifstream in(argv[1]);
    if (!in) {
        cerr << "无法打开输入文件" << endl;
        return -1;
    }

    Sales_data total;               // 保存当前求和结果的变量
    if (total.read(in, total)) {             // 读入第一笔交易记录
        Sales_data trans;          // 保存下一条交易数据的变量
        while (trans.read(in, trans)) {     // 读入剩余的交易
            if (total.isbn() == trans.isbn())  // 检查 isbn
                total = total.add(total, trans);     // 更新变量 total 当前的值
            else {
                total.print(cout, total) << endl;    // 输出结果
                total = trans;                 // 处理下一本
            }
        }
        total.print(cout, total) << endl;            // 输出最后一条交易
    }
    else {                              // 没有输入任何信息
        cerr << "没有数据" << endl;    // 通知用户
        return -1;
    }
    return 0;
}
```

**8.2.2 文件模式**

![image-20210714215155174](README.assets/image-20210714215155174.png)

![image-20210714215229052](README.assets/image-20210714215229052.png)

![image-20210714215250301](README.assets/image-20210714215250301.png)

**每次调用open时都会确认文件模式**

![image-20210714215343268](README.assets/image-20210714215343268.png)

**练习**

![image-20210714222719357](README.assets/image-20210714222719357.png)

```c++
#include <iostream>
#include <fstream>
#include "Sales_data.h"
using namespace std;

int main(int argc, char *argv[]) {
    if (argc != 3) {
        cerr << "请给出文件名" << endl;
        return -1;
    }
    ifstream in(argv[1]);
    if (!in) {
        cerr << "无法打开输入文件" << endl;
        return -1;
    }
    ofstream out(argv[2]);
    if (!out) {
        cerr << "无法打开输出文件" << endl;
        return -1;
    }

    Sales_data total;               // 保存当前求和结果的变量
    if (total.read(in, total)) {             // 读入第一笔交易记录
        Sales_data trans;          // 保存下一条交易数据的变量
        while (trans.read(in, trans)) {     // 读入剩余的交易
            if (total.isbn() == trans.isbn())  // 检查 isbn
                total = total.add(total, trans);     // 更新变量 total 当前的值
            else {
                total.print(out, total) << endl;    // 输出结果
                total = trans;                 // 处理下一本
            }
        }
        total.print(out, total) << endl;            // 输出最后一条交易
    }
    else {                              // 没有输入任何信息
        cerr << "没有数据" << endl;    // 通知用户
        return -1;
    }
    return 0;
}
```

#### 8.3 string流

头文件`sstream`

`istringstream`读数据

`ostringstream`写数据

##### 8.3.1 使用istringstream

![image-20210714225938156](README.assets/image-20210714225938156.png)

```c++
#include <iostream>
#include <sstream>
#include <string>
#include <stdexcept>

using namespace std;

istream &f(istream &in) {
    string v;
    while (in >> v, !in.eof()) {
        if (in.bad())
            throw runtime_error("IO 流错误");
        if (in.fail()) {
            cerr << "数据错误，请重试" << endl;
            in.clear();
            in.ignore(100, '\0');
            continue;
        }
        cout << v << endl;
    }
    in.clear();
    return in;
}

int main() {
    ostringstream msg;
    msg << "C++ Primer 第五版" << endl;
    istringstream in(msg.str());
    f(in);
    return 0;
}
Copy
// 运行结果
C++
Primer
第五版

Process finished with exit code 0
```

##### 8.3.2 使用ostringstream

![image-20210714230059593](README.assets/image-20210714230059593.png)

![image-20210714230111380](README.assets/image-20210714230111380.png)

```c++
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <vector>

using namespace std;

struct PersonInfo {
    string name;
    vector<string> phones;
};

string format(const string &s) {
    return s;
}

bool valid(const string &s) {
    // 如何验证电话号码将在第 17 章介绍
    // 现在简单返回 true
    return true;
}

int main(int argc, char *argv[]) {
    string line, word;              // 分别保存来自输入的一行和单词
    vector<PersonInfo> people;      // 保存来自输入的所有记录
    istringstream record;

    if (argc != 2) {
        cerr << "请给出文件名" << endl;
        return -1;
    }
    ifstream in(argv[1]);
    if (!in) {
        cerr << "无法打开输入文件" << endl;
        return -1;
    }

    // 逐行从输入读取数据，直至 cin 遇到文件尾（或其他错误）
    while (getline(in, line)) {
        PersonInfo info;            // 创建一个保存此记录数据的对象
        record.clear();             // 重复使用字符串流时，每次都要调用 clear
        record.str(line);           // 将记录绑定到刚读入的行（将 line 拷贝到 record 中）
        record >> info.name;        // 读取名字
        while (record >> word)      // 读取电话号码
            info.phones.push_back(word);    // 保持它们
        people.push_back(info);     // 将此记录追加到 people 末尾
    }

    ostringstream os;
    for (const auto &entry : people) {  // 对 people 中每一项
        ostringstream formatted, badNums;   // 每个循环步创建的对象
        for (const auto &nums : entry.phones) {     // 对每个数
            if (!valid(nums))
                badNums << " " << nums;     // 将数的字符串形式存入 badNums
            else
                // 将格式化的字符串"写入" formatted
                formatted << " " << format(nums);
        }
        if (badNums.str().empty())      // 没有错误的数
            // 打印名字和格式化的数
            os << entry.name << " " << formatted.str() << endl;
        else
            // 否则，打印名字和错误的数
            cerr << "input error: " << entry.name
            << " invalid numbers(s) " << badNums.str() << endl;
    }
    cout << os.str() << endl;

    return 0;
}
Copy
// 运行结果
zhangsan  23443 34432
lisi  23423434
wangwu  234324


Process finished with exit code 0
```

### 第九章 顺序容器

#### 9.1 顺序容器概述

![image-20210715143058897](README.assets/image-20210715143058897.png)

![image-20210715144648238](README.assets/image-20210715144648238.png)

#### 9.2 容器库概览

通用操作

**对容器可以保存的元素类型的限制**

![image-20210715145213459](README.assets/image-20210715145213459.png)

![image-20210715145249575](README.assets/image-20210715145249575.png)

![image-20210715145308089](README.assets/image-20210715145308089.png)

![image-20210715145320057](README.assets/image-20210715145320057.png)

##### 9.2.1 迭代器

使用解引用运算符来访问

**迭代器范围**

[begin, end)

![image-20210715151658748](README.assets/image-20210715151658748.png)

```c++
#include <iostream>
#include <vector>
using namespace std;

vector<int>::iterator search_vec(vector<int>::iterator beg,
        vector<int>::iterator end, int val) {
    for ( ; beg != end; ++beg)      // 遍历范围
        if (*beg == val)            // 检查是否与给定值相等
            return beg;             // 搜索成功，返回元素对应迭代器
    return end;                     // 搜索失败，返回尾后迭代器
}

int main() {
    vector<int> ilist = {1, 2, 3, 4, 5, 6, 7};

    cout << search_vec(ilist.begin(), ilist.end(), 3) - ilist.begin() << endl;
    cout << search_vec(ilist.begin(), ilist.end(), 8) - ilist.begin() << endl;

    return 0;
}
Copy
// 运行结果
2
7

Process finished with exit code 0
```

##### 9.2.2 容器类型成员

##### 9.2.3 begin和end成员

r版本的是反向迭代器

c版本是const迭代器

##### 9.2.4 容器定义和初始化

![image-20210715152712618](README.assets/image-20210715152712618.png)

![image-20210715153000372](README.assets/image-20210715153000372.png)

**标准库array具有固定大小**

![image-20210715153118593](README.assets/image-20210715153118593.png)

##### 9.2.5 赋值和swap

![image-20210715153405734](README.assets/image-20210715153405734.png)

![image-20210715153426278](README.assets/image-20210715153426278.png)

**使用assign**

![image-20210715153529602](README.assets/image-20210715153529602.png)

![image-20210715153553958](README.assets/image-20210715153553958.png)

**使用swap**

![image-20210715153638206](README.assets/image-20210715153638206.png)

##### 9.2.6 容器大小操作

`size`

`max_size`

`empty`

#### 9.3 顺序容器操作

##### 9.3.1 向顺序容器添加元素

![image-20210715161108728](README.assets/image-20210715161108728.png)

**在容器中的特定位置添加元素**

![image-20210715161454205](README.assets/image-20210715161454205.png)

**插入范围**

![image-20210715161559137](README.assets/image-20210715161559137.png)

**使用insert的返回值**

![image-20210715161647514](README.assets/image-20210715161647514.png)

**使用emplace操作**

emplace相当于元素类型的构造函数

![image-20210715162810651](README.assets/image-20210715162810651.png)

**练习**

![image-20210715163637177](README.assets/image-20210715163637177.png)

```c++
#include <iostream>
#include <list>
#include <deque>

using namespace std;

int main() {
    list<int> ilist = {1, 2, 3, 4, 5, 6, 7, 8};     // 初始化 int 的 list
    deque<int> odd_d, even_d;

    // 遍历整数 list
    for (auto lb = ilist.cbegin(); lb != ilist.cend(); ++lb)
        if (*lb & 1)        // 查看最低位，1：奇数；0：偶数
            odd_d.push_back(*lb);
        else
            even_d.push_back(*lb);

    cout << "奇数值有：";
    for (auto db = odd_d.cbegin(); db != odd_d.cend(); ++db)
        cout << *db << " ";
    cout << endl;

    cout << "偶数值有：";
    for (auto db = even_d.cbegin(); db != even_d.cend(); ++db)
        cout << *db << " ";
    cout << endl;

    return 0;
}
Copy
// 运行结果
奇数值有：1 3 5 7 
偶数值有：2 4 6 8 

Process finished with exit code 0
```

##### 9.3.2 访问元素

![image-20210715164003916](README.assets/image-20210715164003916.png)

**访问成员函数返回的是引用**

**下标操作和安全的随机访问**

at会抛出一个out_of_range异常

##### 9.3.3 删除元素

![image-20210715164412301](README.assets/image-20210715164412301.png)

![image-20210715164440411](README.assets/image-20210715164440411.png)

![image-20210715164456961](README.assets/image-20210715164456961.png)

![image-20210715164510797](README.assets/image-20210715164510797.png)

##### 9.3.4 特殊的forward_list操作

![image-20210715164608649](README.assets/image-20210715164608649.png)

![image-20210715164637057](README.assets/image-20210715164637057.png)

##### 9.3.5 改变容器大小

![image-20210715164710385](README.assets/image-20210715164710385.png)

![image-20210715164722683](README.assets/image-20210715164722683.png)

##### 9.3.6 容器操作可能使迭代器失效

![image-20210715164852011](README.assets/image-20210715164852011.png)

![image-20210715164912483](README.assets/image-20210715164912483.png)

**编写改变容器的循环程序**

insert和erase会返回

![image-20210715165022381](README.assets/image-20210715165022381.png)

![image-20210715165045823](README.assets/image-20210715165045823.png)

**不要保存end返回的迭代器**

![image-20210715165150322](README.assets/image-20210715165150322.png)

#### 9.4 vector对象是如何增长的

**管理容量的成员函数**

![image-20210715165339054](README.assets/image-20210715165339054.png)

**capacity和size**

![image-20210715165419658](README.assets/image-20210715165419658.png)

![image-20210715165550609](README.assets/image-20210715165550609.png)

#### 9.5 额外的string操作

##### 9.5.1 构造string的其他方法

![image-20210715201056739](README.assets/image-20210715201056739.png)

![image-20210715201152764](README.assets/image-20210715201152764.png)

**substr**

返回一个string，是原来的部分或全部

![image-20210715201609662](README.assets/image-20210715201609662.png)

**练习**

![image-20210715202656770](README.assets/image-20210715202656770.png)

```c++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main() {
    vector<char> cv = {'H', 'e', 'l', 'l', 'o'};
    string s(cv.data(), cv.size());
    cout << s << endl;

    return 0;
}
Copy
// 运行结果
Hello

Process finished with exit code 0
```

##### 9.5.2 改变string的其他方法

![image-20210715204400951](README.assets/image-20210715204400951.png)

**append和replace函数**

![image-20210715204938504](README.assets/image-20210715204938504.png)

![image-20210715204948685](README.assets/image-20210715204948685.png)

**改变string的多种重载函数**

##### 9.5.3 string搜索操作

![image-20210715205130796](README.assets/image-20210715205130796.png)

![image-20210715205150962](README.assets/image-20210715205150962.png)

![image-20210715205222106](README.assets/image-20210715205222106.png)

**指定从哪里开始搜索**

![image-20210715205321941](README.assets/image-20210715205321941.png)

**逆向搜索**

![image-20210715205420518](README.assets/image-20210715205420518.png)

##### 9.5.4 compare函数

![image-20210715205501676](README.assets/image-20210715205501676.png)

##### 9.5.5 数值转换

![image-20210715205558756](README.assets/image-20210715205558756.png)

#### 9.6 容器适配器

stack queue priority_queue

**定义一个适配器**

![image-20210715205801530](README.assets/image-20210715205801530.png)

**栈适配器**

![image-20210715205843569](README.assets/image-20210715205843569.png)

![image-20210715205856875](README.assets/image-20210715205856875.png)

**队列适配器**

![image-20210715205926136](README.assets/image-20210715205926136.png)

![image-20210715205949557](README.assets/image-20210715205949557.png)

### 第十章 泛型算法

![image-20210715213409457](README.assets/image-20210715213409457.png)

头文件algorithm

#### 10.1 概述

迭代器令算法不依赖于容器

**算法永远不会执行容器的操作**

#### 10.2初识泛型算法

![image-20210715213739662](README.assets/image-20210715213739662.png)

##### 10.2.1 只读算法

`find`

`count`

`accumulate`

**算法和元素类型**

![image-20210715213912044](README.assets/image-20210715213912044.png)

![image-20210715213925476](README.assets/image-20210715213925476.png)

**操作两个序列的算法**

`equal`

![image-20210715214008776](README.assets/image-20210715214008776.png)

##### 10.2.2 写容器元素的算法

`fill`

![image-20210715214127710](README.assets/image-20210715214127710.png)

**算法不检查写操作**

`fill_n`假定安全，所以容易在空容器上调用

`back_inserter`

![image-20210715214312085](README.assets/image-20210715214312085.png)

![image-20210715214353159](README.assets/image-20210715214353159.png)

`copy`

![image-20210715214428605](README.assets/image-20210715214428605.png)

##### 10.2.3 重拍容器元素的算法

`sort`

`unique`

![image-20210715214601948](README.assets/image-20210715214601948.png)

![image-20210715214652934](README.assets/image-20210715214652934.png)

#### 10.3定制操作

##### 10.3.1 向算法传递函数

谓词，第三个参数

**谓词**

一元谓词和二元谓词

![image-20210715220740788](README.assets/image-20210715220740788.png)

##### 10.3.2 lambda表达式

**介绍lamda**

![image-20210715220955244](README.assets/image-20210715220955244.png)

![image-20210715221043675](README.assets/image-20210715221043675.png)

![image-20210715221122633](README.assets/image-20210715221122633.png)

**向lambda传递参数**

![image-20210715221254355](README.assets/image-20210715221254355.png)

**使用捕获列表**

![image-20210715221425302](README.assets/image-20210715221425302.png)

![image-20210715221725576](README.assets/image-20210715221725576.png)

##### 10.3.3 lambda捕获和返回

**值捕获**

创建时捕获

![image-20210715222053964](README.assets/image-20210715222053964.png)

**引用捕获**

![image-20210715222121903](README.assets/image-20210715222121903.png)

![image-20210715222206203](README.assets/image-20210715222206203.png)

![image-20210715222227495](README.assets/image-20210715222227495.png)

**隐式捕获**

&或者=

![image-20210715222459525](README.assets/image-20210715222459525.png)

**可变lambda**

![image-20210715222634609](README.assets/image-20210715222634609.png)

**指定lambda返回类型**

![image-20210715222746439](README.assets/image-20210715222746439.png)

![image-20210715222809424](README.assets/image-20210715222809424.png)

##### 10.3.4 参数绑定

![image-20210715223003151](README.assets/image-20210715223003151.png)

**标准库bind函数**

头文件`functional`

![image-20210715223111709](README.assets/image-20210715223111709.png)

![image-20210715223351245](README.assets/image-20210715223351245.png)

![image-20210715223420236](README.assets/image-20210715223420236.png)

![image-20210715223430620](README.assets/image-20210715223430620.png)

**使用placeholders名字**

名字_n都在这里面

![image-20210715223504787](README.assets/image-20210715223504787.png)

![image-20210715223547029](README.assets/image-20210715223547029.png)

**bind的参数**

![image-20210715223700718](README.assets/image-20210715223700718.png)

![image-20210715223709100](README.assets/image-20210715223709100.png)

**用bind重排参数顺序**

![image-20210715223743659](README.assets/image-20210715223743659.png)

**绑定引用参数**

![image-20210715223833681](README.assets/image-20210715223833681.png)

#### 10.4 再探迭代器

* 插入迭代器
* 流迭代器
* 反向迭代器
* 移动迭代器

##### 10.4.1 插入迭代器

![image-20210715224144975](README.assets/image-20210715224144975.png)

![image-20210715224202841](README.assets/image-20210715224202841.png)

##### 10.4.2 iostream迭代器

未看

##### 10.4.3 反向迭代器

![image-20210715224418481](README.assets/image-20210715224418481.png)

![image-20210715224843529](README.assets/image-20210715224843529.png)

![image-20210715224850843](README.assets/image-20210715224850843.png)

![image-20210715224909283](README.assets/image-20210715224909283.png)

#### 10.5 泛型算法结构

![image-20210715224954462](README.assets/image-20210715224954462.png)

##### 10.5.1 5类迭代器

![image-20210715225042271](README.assets/image-20210715225042271.png)

![image-20210715225054210](README.assets/image-20210715225054210.png)

##### 10.5.2 算法形参模型

![image-20210715225135937](README.assets/image-20210715225135937.png)

**接受单个目标迭代器的算法**

![image-20210715225218339](README.assets/image-20210715225218339.png)

**接受第二个输入序列的算法**

![image-20210715225248814](README.assets/image-20210715225248814.png)

##### 10.5.3 算法命名规范

**一些算法使用重载形式传递一个谓词**

**_if版本的算法**

![image-20210715225418545](README.assets/image-20210715225418545.png)

**区分拷贝元素的版本和不拷贝的版本**

![image-20210715225459437](README.assets/image-20210715225459437.png)

#### 10.6 特定容器算法

![image-20210715225538090](README.assets/image-20210715225538090.png)

![image-20210715225548974](README.assets/image-20210715225548974.png)

![image-20210715225603778](README.assets/image-20210715225603778.png)

![image-20210715225623980](README.assets/image-20210715225623980.png)

### 第十一章 关联容器

关联容器中的元素时按**关键字**来保存和访问的，顺序容器时按它们在容器中的位置来顺序保存和访问的

两个主要类型：`map`和`set`

`map`是关键字-值

`set`每个元素只包含一个关键字

![image-20210716150201644](README.assets/image-20210716150201644.png)

##### 11.1 使用关联容器

map类似被称为关联数组

**使用map**

![image-20210716150324699](README.assets/image-20210716150324699.png)

**使用set**

![image-20210716153118553](README.assets/image-20210716153118553.png)

**练习**

![image-20210716153448861](README.assets/image-20210716153448861.png)

```c++
#include <iostream>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

string &trans(string &s) {
    for (int p = 0; p < s.size(); ++p) {
        if (s[p] >= 'A' && s[p] <= 'Z')
            s[p] += ('a' - 'A');
        else if (s[p] == ',' || s[p] == '.')
            s.erase(p, 1);
    }
    return s;
}

int main() {
    // 统计每个单词在输入中出现的次数
    map<string, size_t> word_count;     // string 到 size_t 的空 map
    string word;
    while (cin >> word)
        ++word_count[trans(word)];      // 提取 word 的计数器并将其加 1
    for (const auto &w : word_count)    // 对 map 中的每个元素
        // 打印结果
        cout << w.first << " occurs " << w.second
             << ((w.second > 1) ? " times" : " time") << endl;
    return 0;
}
Copy
// 运行结果
example. Cplusplus Primer example, Example primer
^D
cplusplus occurs 1 time
example occurs 3 times
primer occurs 2 times

Process finished with exit code 0
```

#### 11.2 关联容器概述

##### 11.2.1 定义关联容器

![image-20210716153616709](README.assets/image-20210716153616709.png)

**初始化multimap或multiset**

![image-20210716153732890](README.assets/image-20210716153732890.png)

##### 11.2.2 关键字类型的要求

**有序容器的关键字类型**

![image-20210716154036195](README.assets/image-20210716154036195.png)

**使用关键字类型的比较函数**

![image-20210716154316137](README.assets/image-20210716154316137.png)

##### 11.2.3 pair类型

头文件`utility`

![image-20210716154441685](README.assets/image-20210716154441685.png)

![image-20210716154504701](README.assets/image-20210716154504701.png)

**创建pair对象的函数**

![image-20210716154623609](README.assets/image-20210716154623609.png)

#### 11.3 关联容器操作

![image-20210716154732729](README.assets/image-20210716154732729.png)

##### 11.3.1 关联容器迭代器

解引用

![image-20210716155036480](README.assets/image-20210716155036480.png)

**set的迭代器是const的**

![image-20210716155112510](README.assets/image-20210716155112510.png)

**遍历关联容器**

![image-20210716155154721](README.assets/image-20210716155154721.png)

**关联容器和算法**

通常不使用泛型算法

![image-20210716155254065](README.assets/image-20210716155254065.png)

![image-20210716155303099](README.assets/image-20210716155303099.png)

##### 11.3.2 添加元素

![image-20210716155418473](README.assets/image-20210716155418473.png)

**向map添加元素**

![image-20210716155452976](README.assets/image-20210716155452976.png)

![image-20210716155525166](README.assets/image-20210716155525166.png)

**检测insert的返回值**

![image-20210716155656919](README.assets/image-20210716155656919.png)

![image-20210716155601229](README.assets/image-20210716155601229.png)

**向multiset或者multimap添加元素**

![image-20210716155809245](README.assets/image-20210716155809245.png)

##### 11.3.3 删除元素

![image-20210716155904529](README.assets/image-20210716155904529.png)

![image-20210716155920222](README.assets/image-20210716155920222.png)

##### 11.3.4 map的下标操作

![image-20210716160008226](README.assets/image-20210716160008226.png)

![image-20210716160057083](README.assets/image-20210716160057083.png)

##### 11.3.5 访问元素

![image-20210716160142298](README.assets/image-20210716160142298.png)

![image-20210716160152142](README.assets/image-20210716160152142.png)

**对map使用find代替下标操作**

![image-20210716160226430](README.assets/image-20210716160226430.png)

**在multimap后multiset中查找元素**

![image-20210716160328410](README.assets/image-20210716160328410.png)

**一种不同的，面向迭代器的解决方法**

![image-20210716160531022](README.assets/image-20210716160531022.png)

![image-20210716160542788](README.assets/image-20210716160542788.png)

![image-20210716160558066](README.assets/image-20210716160558066.png)

**equal_range**

![image-20210716160623512](README.assets/image-20210716160623512.png)

![image-20210716160645012](README.assets/image-20210716160645012.png)

##### 11.3.6 一个单词转换的map

![image-20210716160714398](README.assets/image-20210716160714398.png)

![image-20210716160735256](README.assets/image-20210716160735256.png)

**程序**

![image-20210716160751313](README.assets/image-20210716160751313.png)

**建立转换映射**

![image-20210716160801167](README.assets/image-20210716160801167.png)

**生成转换文本**

![image-20210716160841721](README.assets/image-20210716160841721.png)

#### 11.4 无序容器

![image-20210716160911254](README.assets/image-20210716160911254.png)

**使用无序容器**

![image-20210716160938185](README.assets/image-20210716160938185.png)

**管理桶**

![image-20210716161032971](README.assets/image-20210716161032971.png)

**无序容器对关键字类型的要求**

![image-20210716161302238](README.assets/image-20210716161302238.png)

![image-20210716161312767](README.assets/image-20210716161312767.png)

### 第12章 动态内存

自动

局部static对象在第一次使用前分配，程序结束时销毁

动态分配对象：标准库定义了两个智能指针类型来管理动态分配的对象

![image-20210716163459118](README.assets/image-20210716163459118.png)

#### 12.1 动态内存与智能指针

![image-20210716163526892](README.assets/image-20210716163526892.png)

![image-20210716163549818](README.assets/image-20210716163549818.png)

##### 12.1.1 shared_ptr类

![image-20210716163645893](README.assets/image-20210716163645893.png)

**使用**

![image-20210716163714330](README.assets/image-20210716163714330.png)

![image-20210716163731454](README.assets/image-20210716163731454.png)

**make_shared函数**

![image-20210716163834009](README.assets/image-20210716163834009.png)

![image-20210716163902055](README.assets/image-20210716163902055.png)

**shared_ptr的拷贝和赋值**

![image-20210716163941633](README.assets/image-20210716163941633.png)

![image-20210716164022574](README.assets/image-20210716164022574.png)

**shared_ptr自动销毁所管理的对象**

**析构函数**：引用技术变为0，就会销毁对象并释放内存

**还会自动释放相关联的内存**

![image-20210716164237623](README.assets/image-20210716164237623.png)

![image-20210716164251209](README.assets/image-20210716164251209.png)

![image-20210716164306205](README.assets/image-20210716164306205.png)

**定义StrBlob类**

![image-20210716164532929](README.assets/image-20210716164532929.png)

**构造函数**

![image-20210716164644218](README.assets/image-20210716164644218.png)

**元素访问成员函数**

![image-20210716164720356](README.assets/image-20210716164720356.png)

![image-20210716164733934](README.assets/image-20210716164733934.png)

##### 12.1.2 直接管理内存

**使用new动态分配和初始化对象**

![image-20210716182630871](README.assets/image-20210716182630871.png)

![image-20210716182715917](README.assets/image-20210716182715917.png)

![image-20210716182725095](README.assets/image-20210716182725095.png)

![image-20210716182802797](README.assets/image-20210716182802797.png)

**动态分配const对象**

![image-20210716182837533](README.assets/image-20210716182837533.png)

**内存耗尽**

会抛出一个类型为bad_alloc的异常

定义在头文件`new`

![image-20210716182950719](README.assets/image-20210716182950719.png)

**释放动态内存**

![image-20210716183043376](README.assets/image-20210716183043376.png)

**指针值和delete**

![image-20210716183204692](README.assets/image-20210716183204692.png)

![image-20210716183251282](README.assets/image-20210716183251282.png)

**delete之后重置指针值**

指针还存在**空悬指针**，未初始化指针。要么就在离开作用域时释放，要么就赋值nullptr

##### 12.1.3 shared_ptr和new结合使用

![image-20210716185330684](README.assets/image-20210716185330684.png)

![image-20210716185358289](README.assets/image-20210716185358289.png)

![image-20210716185430650](README.assets/image-20210716185430650.png)

**不要混合使用普通指针和智能指针**

![image-20210716185538834](README.assets/image-20210716185538834.png)

![image-20210716185621774](README.assets/image-20210716185621774.png)

![image-20210716185630481](README.assets/image-20210716185630481.png)

**也不要用get初始化另一个智能指针或赋值**

![image-20210716185828260](README.assets/image-20210716185828260.png)

![image-20210716185837373](README.assets/image-20210716185837373.png)

**其他shared_ptr操作**

![image-20210716185921629](README.assets/image-20210716185921629.png)

![image-20210716185936883](README.assets/image-20210716185936883.png)

##### 12.1.4 智能指针和异常

![image-20210716190037376](README.assets/image-20210716190037376.png)

**智能指针和哑类**

**使用我们自己的释放操作**

deleter

![image-20210716190212745](README.assets/image-20210716190212745.png)

![image-20210716190231813](README.assets/image-20210716190231813.png)

##### 12.1.5 unique_ptr

![image-20210716190433197](README.assets/image-20210716190433197.png)

![image-20210716190448908](README.assets/image-20210716190448908.png)

![image-20210716190527732](README.assets/image-20210716190527732.png)

**向unique_ptr传递删除器**

![image-20210716190651128](README.assets/image-20210716190651128.png)

##### 12.1.6 weak_ptr

![image-20210716190745953](README.assets/image-20210716190745953.png)

![image-20210716190814500](README.assets/image-20210716190814500.png)

**检查指针类**

应用，还没看

#### 12.2 动态数组

![image-20210716193834263](README.assets/image-20210716193834263.png)

![image-20210716193844623](README.assets/image-20210716193844623.png)

##### 12.2.1 new和数组

![image-20210716194000495](README.assets/image-20210716194000495.png)

**分配数组得到一个元素类型的指针**

不能用begin或者end，也不能用for

![image-20210716194314101](README.assets/image-20210716194314101.png)

**初始化动态分配对象的数组**

![image-20210717090151605](README.assets/image-20210717090151605.png)

**动态分配一个空数组是合法的**

![image-20210717090320295](README.assets/image-20210717090320295.png)

**释放动态数组**

![image-20210717090403869](README.assets/image-20210717090403869.png)

![image-20210717090428336](README.assets/image-20210717090428336.png)

**智能指针和动态数组**

![image-20210717090519434](README.assets/image-20210717090519434.png)

![image-20210717090551477](README.assets/image-20210717090551477.png)

![image-20210717090619510](README.assets/image-20210717090619510.png)

![image-20210717090652134](README.assets/image-20210717090652134.png)

##### 12.2.2  allocator类

![image-20210717093506204](README.assets/image-20210717093506204.png)

**allocator类**

头文件`memory`

![image-20210717093623483](README.assets/image-20210717093623483.png)

![image-20210717093704434](README.assets/image-20210717093704434.png)

**allocator分配未构造的内存**

![image-20210717093856921](README.assets/image-20210717093856921.png)

![image-20210717093907248](README.assets/image-20210717093907248.png)

![image-20210717093928952](README.assets/image-20210717093928952.png)

![image-20210717093956288](README.assets/image-20210717093956288.png)

**拷贝和填充为初始化内存的算法**

两个伴随算法

![image-20210717094048624](README.assets/image-20210717094048624.png)

![image-20210717094135336](README.assets/image-20210717094135336.png)

#### 12.3 使用标准库：文本查询程序

未看

## 第III部分 类设计者的工具

拷贝控制、重载运算符、继承和模板

### 第十三章 拷贝控制

拷贝构造函数、移动构造函数、拷贝赋值运算符、移动赋值运算符以及析构函数

![image-20210719103526000](README.assets/image-20210719103526000.png)

#### 13.1 拷贝、赋值与销毁

拷贝构造函数、拷贝赋值运算符、析构函数

##### 13.1.1 拷贝构造函数

![image-20210719103732991](README.assets/image-20210719103732991.png)

几乎都是const引用，不应该是explicit的

**合成拷贝构造函数**

![image-20210719104017188](README.assets/image-20210719104017188.png)

**拷贝初始化**

![image-20210719104110443](README.assets/image-20210719104110443.png)

![image-20210719104153439](README.assets/image-20210719104153439.png)

**参数和返回值**

![image-20210719104323754](README.assets/image-20210719104323754.png)

**拷贝初始化的限制**

**编译器可以绕过拷贝构造函数**

##### 13.1.2 拷贝赋值运算符

![image-20210719120445493](README.assets/image-20210719120445493.png)

**重载赋值运算符**

![image-20210719120942335](README.assets/image-20210719120942335.png)

![image-20210719121002810](README.assets/image-20210719121002810.png)

**合成拷贝赋值运算符**

![image-20210719121113302](README.assets/image-20210719121113302.png)

##### 13.1.3 析构函数

![image-20210719121226855](README.assets/image-20210719121226855.png)

**析构函数完成什么工作**

![image-20210719122750519](README.assets/image-20210719122750519.png)

![image-20210719122951761](README.assets/image-20210719122951761.png)

**合成析构函数**

![image-20210719123020349](README.assets/image-20210719123020349.png)

##### 13.1.4 三/五法则

不需要定义所有这些操作

**需要析构函数的类也需要拷贝和赋值操作**

![image-20210719123227372](README.assets/image-20210719123227372.png)

**需要拷贝操作的类也需要赋值操作**，反之亦然

##### 13.1.5 使用=default

显示地使用合成版本

![image-20210719123803314](README.assets/image-20210719123803314.png)

##### 13.1.5 阻止拷贝

![image-20210719135923391](README.assets/image-20210719135923391.png)

**定义删除地函数**

![image-20210719140030362](README.assets/image-20210719140030362.png)

**析构函数不能是删除地成员**

![image-20210719140200598](README.assets/image-20210719140200598.png)

**private拷贝控制**

![image-20210719140329519](README.assets/image-20210719140329519.png)

![image-20210719140350553](README.assets/image-20210719140350553.png)

![image-20210719161150586](README.assets/image-20210719161150586.png)

```c++
#include <iostream>
#include <string>

using namespace std;

class HasPtr {
public:
    HasPtr(const std::string &s = std::string()) :
            ps(new std::string(s)), i(0) { }
    HasPtr(const HasPtr &);                 // 拷贝构造函数
    HasPtr &operator=(const HasPtr &);      // 拷贝赋值运算符
    HasPtr &operator=(const string &);      // 赋予新 string
    string &operator*();                    // 解引用
    ~HasPtr();                              // 析构函数
private:
    std::string *ps;
    int i;
};

HasPtr::HasPtr(const HasPtr &orig) :
        ps(new std::string(*orig.ps)), i(orig.i) { }

HasPtr& HasPtr::operator=(const HasPtr &rhs) {
    std::string *newps = new std::string(*rhs.ps);  // 拷贝指针指向的对象
    delete ps;                                      // 销毁原 string
    ps = newps;                                     // 指向新 string
    i = rhs.i;                                      // 使用内置的 int 赋值
    return *this;                                   // 返回一个此对象的引用
}

HasPtr& HasPtr::operator=(const string &rhs) {
    *ps = rhs;
    return *this;
}

string& HasPtr::operator*() {
    return *ps;
}

HasPtr::~HasPtr() {
    delete ps;          // 释放 string 内存
}

int main() {
    HasPtr h("hi mom!");
    HasPtr h2(h);       // 行为类值，h2、h3 和 h 指向不同 string
    HasPtr h3 = h;
    h2 = "hi dad!";
    h3 = "hi son!";
    cout << "h: " << *h << endl;
    cout << "h2: " << *h2 << endl;
    cout << "h3: " << *h3 << endl;
    return 0;
}
Copy
// 运行结果
h: hi mom!
h2: hi dad!
h3: hi son!

Process finished with exit code 0
```



#### 13.2 拷贝控制和资源管理

##### 13.2.1 行为像值的类

#####  13.2.2定义行为向指针的类

有个记录使用次数的

![image-20210719161442072](README.assets/image-20210719161442072.png)

![image-20210719161527105](README.assets/image-20210719161527105.png)

#### 13.3 交换操作

swap

![image-20210719161706121](README.assets/image-20210719161706121.png)

![image-20210719161731046](README.assets/image-20210719161731046.png)

**在赋值运算中使用swap**

![image-20210719161835085](README.assets/image-20210719161835085.png)

![image-20210719161857596](README.assets/image-20210719161857596.png)

#### 13.4 拷贝控制示例

未看

#### 13.5 动态内存管理类

**StrVec类的设计**

**定义**

![image-20210719162209573](README.assets/image-20210719162209573.png)

**使用construct**

![image-20210719162352704](README.assets/image-20210719162352704.png)

**alloc_n_copy成员**

![image-20210719162445097](README.assets/image-20210719162445097.png)

未看完

#### 13.6 对象移动

拷贝后就销毁，移动的性能会更好

新标准的一个最主要特性

![image-20210719162628480](README.assets/image-20210719162628480.png)

##### 13.6.1 右值引用

&&

![image-20210719162823873](README.assets/image-20210719162823873.png)

![image-20210719162835820](README.assets/image-20210719162835820.png)

**左值持久，右值短暂**

![image-20210719162913484](README.assets/image-20210719162913484.png)

![image-20210719162923609](README.assets/image-20210719162923609.png)

**变量是左值**

![image-20210719163004167](README.assets/image-20210719163004167.png)

**标准库move函数**

显示转换

![image-20210719163044393](README.assets/image-20210719163044393.png)

![image-20210719163054115](README.assets/image-20210719163054115.png)

![image-20210719163134912](README.assets/image-20210719163134912.png)

##### 13.6.2 移动构造函数和移动赋值运算符

移动构造函数第一个参数是右值引用

![image-20210719163439141](README.assets/image-20210719163439141.png)

**移动操作、标准库容器和异常**

![image-20210719180335811](README.assets/image-20210719180335811.png)

**移动赋值运算符**

![image-20210719180459705](README.assets/image-20210719180459705.png)

**移后源对象必须可析构**

**合成的移动操作**

![image-20210719180719206](README.assets/image-20210719180719206.png)

后面还没看

##### 13.6.3 右值引用和成员函数

![image-20210719180856212](README.assets/image-20210719180856212.png)

![image-20210719180910904](README.assets/image-20210719180910904.png)

后面还没看

### 第14章 重载运算与类型转换

#### 14.1 基本概念

![image-20210719181108729](README.assets/image-20210719181108729.png)

![image-20210719181416007](README.assets/image-20210719181416007.png)

**直接调用一个重载的运算符函数**

![image-20210719181523495](README.assets/image-20210719181523495.png)

![image-20210719181533338](README.assets/image-20210719181533338.png)

**某些运算符不应该被重载**

![image-20210719181649523](README.assets/image-20210719181649523.png)

![image-20210719181715172](README.assets/image-20210719181715172.png)

**使用与内置类型一致的含义**

**赋值和复合赋值运算符**

**选择作为成员或者非成员**

![image-20210719182009376](README.assets/image-20210719182009376.png)

#### 14.2 输入和输出运算符

##### 14.2.1 重载输出运算符<<

![image-20210719184444900](README.assets/image-20210719184444900.png)

**输出运算符尽量减少格式化操作**

![image-20210719184534173](README.assets/image-20210719184534173.png)

**输入输出运算符必须是非成员函数**

friend

##### 14.2.2 重载输入运算符>>

![image-20210719184653895](README.assets/image-20210719184653895.png)

![image-20210719184711236](README.assets/image-20210719184711236.png)

![image-20210719184802795](README.assets/image-20210719184802795.png)

#### 14.3 算术和关系运算符

非成员函数

![image-20210719184858491](README.assets/image-20210719184858491.png)

![image-20210719184913612](README.assets/image-20210719184913612.png)

##### 14.3.1 相等运算符

![image-20210719185004544](README.assets/image-20210719185004544.png)

##### 14.3.2 关系运算符

#### 14.4 赋值运算符

除了拷贝、移动之外的第三种

![image-20210719185212702](README.assets/image-20210719185212702.png)

![image-20210719185223427](README.assets/image-20210719185223427.png)

![image-20210719185306186](README.assets/image-20210719185306186.png)

**复合赋值运算符**

![image-20210719185350757](README.assets/image-20210719185350757.png)

#### 14.5 下标运算符

必须是成员函数

![image-20210719191340750](README.assets/image-20210719191340750.png)

![image-20210719191331687](README.assets/image-20210719191331687.png)

#### 14.6 递增和递减运算符

![image-20210719191428950](README.assets/image-20210719191428950.png)

**前置**

![image-20210719191509024](README.assets/image-20210719191509024.png)

**后置**

int类型的形参

![image-20210719191554643](README.assets/image-20210719191554643.png)

**显示调用后置运算符**

![image-20210719191654703](README.assets/image-20210719191654703.png)

#### 14.7 成员访问运算符

解引用*和箭头运算符->

![image-20210719191953557](README.assets/image-20210719191953557.png)

![image-20210719192241755](README.assets/image-20210719192241755.png)

**对箭头运算符返回值的限定**

![image-20210719192439834](README.assets/image-20210719192439834.png)

#### 14.8 函数调用运算符

![image-20210719192648283](README.assets/image-20210719192648283.png)

**含有状态的函数对象类**

![image-20210719195623125](README.assets/image-20210719195623125.png)

##### 14.8.1 lambda是函数对象

##### 14.8.2 标准库定义的函数对象

![image-20210719195843886](README.assets/image-20210719195843886.png)

![image-20210719195852789](README.assets/image-20210719195852789.png)

##### 14.8.3 可调用对象与function

还没看

#### 14.9 重载、类型转换与运算符

转换构造函数和类型转换运算符

##### 14.9.1 类型转换运算符

```
operator type() const;
```

![image-20210719201247729](README.assets/image-20210719201247729.png)

**定义含有类型转换运算符的类**

![image-20210719201312961](README.assets/image-20210719201312961.png)

![image-20210719201401007](README.assets/image-20210719201401007.png)

避免过度使用

**显示的类型转换运算符**

![image-20210719201537918](README.assets/image-20210719201537918.png)

![image-20210719201613981](README.assets/image-20210719201613981.png)

##### 14.9.2 避免由二义性的类型转换

##### 14.9.3 函数匹配与重载运算符

### 第十五章 面向对象程序设计

#### 15.1 OOP:概述

数据抽象 继承和动态绑定

继承：基类和派生类

虚函数：派生类适应自身的版本

动态绑定，用的是基类还是派生类取决于运行时的绑定

![image-20210719202513532](README.assets/image-20210719202513532.png)

#### 15.2 定义基类和派生类

##### 15.2.1 定义基类

![image-20210719215619789](README.assets/image-20210719215619789.png)

**成员函数与继承**

需要覆盖的用虚函数动态绑定

**访问控制与继承**

派生类能访问共有成员和受保护的成员，不能访问私有成员

##### 15.2.2 定义派生类

**类派生列表**

![image-20210719220023692](README.assets/image-20210719220023692.png)

大多数类都只继承自一个类，**单继承**

**派生类中的虚函数**

![image-20210719220334398](README.assets/image-20210719220334398.png)

**派生类对象及派生类向基类的类型转换**

![image-20210719220647842](README.assets/image-20210719220647842.png)

**派生类构造函数**

派生类要使用基类的构造函数来初始化基类部分

![image-20210719220816951](README.assets/image-20210719220816951.png)

![image-20210719220837089](README.assets/image-20210719220837089.png)

**派生类使用基类的成员**

![image-20210719220924159](README.assets/image-20210719220924159.png)

**派生类的声明**

![image-20210719221004017](README.assets/image-20210719221004017.png)

**被用作基类的类**

![image-20210719221045810](README.assets/image-20210719221045810.png)

![image-20210719221117176](README.assets/image-20210719221117176.png)

**防止继承的发生**

final

![image-20210719221232809](README.assets/image-20210719221232809.png)

##### 15.2.3 类型转换与继承

基类和派生类的转换

![image-20210719221344746](README.assets/image-20210719221344746.png)

**静态类型与动态类型**

未看

#### 15.3 虚函数

![image-20210719221617336](README.assets/image-20210719221617336.png)

**对虚函数的调用可能在运行时才被解析**

![image-20210720100607739](README.assets/image-20210720100607739.png)

![image-20210720100641600](README.assets/image-20210720100641600.png)

**派生类中的虚函数**

![image-20210720100751117](README.assets/image-20210720100751117.png)

![image-20210720100804685](README.assets/image-20210720100804685.png)

**final和override说明符**

![image-20210720100905875](README.assets/image-20210720100905875.png)

**虚函数与默认实参**

![image-20210720104349111](README.assets/image-20210720104349111.png)

**回避虚函数的机制**

![image-20210720104449400](README.assets/image-20210720104449400.png)

#### 15.4 抽象基类

**纯虚函数**

![image-20210720104707796](README.assets/image-20210720104707796.png)

![image-20210720104728315](README.assets/image-20210720104728315.png)

**含有纯虚函数的类时抽象基类**

不能直接创建一个抽象基类对象，可以派生，但是必须覆盖这个纯虚函数

![image-20210720105131566](README.assets/image-20210720105131566.png)

#### 15.5 访问控制与继承

**受保护的成员**

![image-20210720105423995](README.assets/image-20210720105423995.png)

**公有、私有和受保护继承**

![image-20210720105556804](README.assets/image-20210720105556804.png)

![image-20210720105617739](README.assets/image-20210720105617739.png)

**派生类向基类转换的可访问性**

![image-20210720105853445](README.assets/image-20210720105853445.png)

**友元与继承**

![image-20210720105949041](README.assets/image-20210720105949041.png)

![image-20210720110022487](README.assets/image-20210720110022487.png)

**改变个别成员的可访问性**

![image-20210720110139464](README.assets/image-20210720110139464.png)

**默认的继承保护级别**

![image-20210720110221670](README.assets/image-20210720110221670.png)

#### 15.6 继承中的类作用域

![image-20210720110323465](README.assets/image-20210720110323465.png)

![image-20210720110333141](README.assets/image-20210720110333141.png)

**在编译时进行名字查找**

![image-20210720110540595](README.assets/image-20210720110540595.png)

**名字冲突与继承**

派生类的成员将隐藏同名的基类成员

**通过作用域运算符来使用被隐藏的成员**

![image-20210720110803703](README.assets/image-20210720110803703.png)

![image-20210720110816112](README.assets/image-20210720110816112.png)

后面还没看

#### 15.7 构造函数与拷贝控制

##### 15.7.1 虚析构函数

基类通常定义一个虚析构函数

![image-20210720110950377](README.assets/image-20210720110950377.png)

![image-20210720111004923](README.assets/image-20210720111004923.png)

**虚析构函数将阻止合成移动操作**

**15.7.2 合成拷贝控制与继承**

##### 15.7.3 派生类的拷贝控制成员

![image-20210720111146915](README.assets/image-20210720111146915.png)

**定义派生类的拷贝或移动构造函数**

![image-20210720111254227](README.assets/image-20210720111254227.png)

**派生类赋值运算符**

需要显式的赋值

![image-20210720111412680](README.assets/image-20210720111412680.png)

**派生类析构函数**

![image-20210720111442516](README.assets/image-20210720111442516.png)

##### 15.7.4 继承的构造函数

![image-20210720111556543](README.assets/image-20210720111556543.png)

![image-20210720111614742](README.assets/image-20210720111614742.png)

**继承的构造函数的特点**

不会改变 访问等级，不管using声明出现在哪里，基类是public就是public，private也是如此

#### 15.8 容器与继承

![image-20210720111759940](README.assets/image-20210720111759940.png)

![image-20210720111844863](README.assets/image-20210720111844863.png)

**在容器中放置(指针)而非对象**

![image-20210720111946256](README.assets/image-20210720111946256.png)

#### 15.9 文本查询程序再探

### 第十六章 模板与泛型编程

#### 16.1 定义模板

##### 16.1.1 函数模板

![image-20210721115555585](README.assets/image-20210721115555585.png)

模板参数可以逗号分隔开

**实例化函数模板**

![image-20210721120853659](README.assets/image-20210721120853659.png)

**模板类型参数**

可以用来指定返回类型或函数的参数类型，变量声明或类型转换

![image-20210721121409288](README.assets/image-20210721121409288.png)

**非类型模板参数**

表示一个值而不是类型

![image-20210721124159877](README.assets/image-20210721124159877.png)

**inline和constexpr的函数模板**

![image-20210721124312990](README.assets/image-20210721124312990.png)

##### 16.1.2 类模板

**定义类模板**

![image-20210721141959488](README.assets/image-20210721141959488.png)

**实例化类模板**

**显示模板实参**

![image-20210721142030848](README.assets/image-20210721142030848.png)

**在模板作用域中引用模板类型**

**类模板的成员函数**

![image-20210721142352764](README.assets/image-20210721142352764.png)

**check和元素访问成员**

![image-20210721142440765](README.assets/image-20210721142440765.png)

之后还没看

##### 16.1.3 模板参数

![image-20210721142544902](README.assets/image-20210721142544902.png)

**模板参数与作用域**

![image-20210721142718167](README.assets/image-20210721142718167.png)

**模板声明**

![image-20210721142809861](README.assets/image-20210721142809861.png)

##### 16.1.4 成员模板

**普通类的成员模板**

![image-20210721143907916](README.assets/image-20210721143907916.png)

**类模板的成员函数**

![image-20210721143945970](README.assets/image-20210721143945970.png)

##### 16.1.5 控制实例化

![image-20210721144112144](README.assets/image-20210721144112144.png)

![image-20210721144132477](README.assets/image-20210721144132477.png)

##### 16.1.6 效率与灵活性

#### 16.2 模板实参推断

##### 16.2.1 类型转换与模板类型参数

![image-20210721144403733](README.assets/image-20210721144403733.png)

![image-20210721144512370](README.assets/image-20210721144512370.png)

#### 16.3 重载与模板

#### 16.4 可变参数模板

#### 16.5 模板特例化

