# 全局函数

## appendFile

### 简介

将一个字符串添加到文件末尾。等同于[saveFile](#saveFile "saveFile")(filename, str, -1);

### 原型
```c++
bool appendFile(string filename, string str);
```

### 参数

参数 | 解释
---- | -----
filename | 文件名
str | 将要保存的字符串

### 返回

是否成功

## char

### 简介

返回str[0]对应的unicode编码。没有则返回0。

### 原型
```c++
integer char(string str);
```

## clock

### 简介

返回当前的时间戳（单位ms）。

### 原型
```c++
number clock();
```

## eval

### 简介

返回str的执行结果。

### 原型
```c++
anytype eval(string str);
```

## evalFile

### 简介

对文件读取并且解析（反序列化），将结果返回。

### 原型
```c++
var evalFile(string filename, bool krmode = false, bool rawstr = false);
```

### 参数

参数 | 解释
---- | -----
filename | 文件名
krmode | 若为真，表示双引号字符串可以像单引号字符串一样使用转义（此时不使用原有的""表示"的功能）
rawstr | 若为真，表示字符串可以跨行

### 返回

反序列化的结果

### 说明

等同于[eval](#eval "eval")([loadFile](#loadFile "loadFile")(filename, krmode, rawstr));

## hash

### 简介

返回value对应的32位hash值。

### 原型
```c++
integer hash(anytype value);
```

## hash16

### 简介

返回value对应的hash值（short版本）。

### 原型
```c++
integer hash16(anytype value);
```

## itoa

### 简介

相当于(string)(int)num，先对数字取整，然后生成相应的字符串。

### 原型
```c++
string itoa(number num);
```

## itoa2

### 简介

同itoa，只是生成的字符串是全角的'０', '１'等字符。

### 原型
```c++
string itoa2(number num);
```

## loadClass

### 简介

内部用，用于从保存的类对象中还原。

### 原型
```c++
class loadClass(string classname, sictionary dic[, anytype nativedata)
```

### 返回

instance

## loadFile

### 简介

读取一个文件，返回里面的原始内容（字符串）

### 原型
```c++
string loadFile(string filename);
```

### 参数

参数 | 解释
---- | -----
filename | 文件名

### 示例

以下将演示一个从内容为
    abc
的1.txt文件载入为数组的示例：

#### 示例代码

```c++
[].loadFile("1.txt")
```

#### 运行结果

```c++
"abc"
```

## log

### 简介

逐个打印参数，逗号分隔。

### 原型
```c++
void log([anytype value1, anytype value2, ...)
```

## print

### 简介

逐个打印字符串内容（没有双引号），逗号分隔。

### 原型
```c++
void print([string str1, string str2, ...)
```

## random

### 简介

生成一个随机整数。

### 原型
```c++
void random(number num1
number num1, number num2
```

### 说明

如果是第一种形式，那么相当于random(0, num1)。
如果是第二种形式，那么：
  如果num2>num1，那么生成的是num1到num2-1之间的一个整数
  如果num2<num1，那么生成的是num2到num1-1之间的一个整数
  如果num2=num1，那么返回num1

## range

### 简介

生成一个数组。

### 原型
```c++
void range(number num1
number num1, number num2
```

### 说明

如果是第一种形式，那么生成的是[0, 1, ..., num1-1]
如果是第二种形式，那么：
  如果num2>num1，那么生成的是[num1, num1+1, ..., num2-1]
  如果num2<num1，那么生成的是[num1, num1-1, ..., num2+1]
  如果num2=num1，那么生成的是空数组

## saveFile

### 简介

将一个字符串写入文件。

### 原型
```c++
bool saveFile(string filename, string str, bool append = false);
```

### 参数

参数 | 解释
---- | -----
filename | 文件名
str | 将要保存的字符串
append | 是否追加在文件末尾。若为否，则覆盖整个文件。

### 返回

是否成功

## time

### 简介

执行str，然后返回执行用的时间（单位ms）。

### 原型
```c++
number time(string str);
```

## toString

### 简介

将value转变成字符串，format表示是否加上缩进格式。

### 原型
```c++
string toString(anytype value, bool format);
```

### 示例

以下将演示一个数组[1,2,3]的toString结果

#### 示例代码

```c++
toString([1,2,3])
```

#### 运行结果

```c++
[1,2,3]
```

#### 示例代码

```c++
toString([1,2,3], true)
```

#### 运行结果

```c++
[
{@t}1,
{@t}2,
{@t}3
]
```

# 全局类

## 类Date

时间类。
**可实例化。**
使用Date()直接创建，时间为当前时间。

### 函数

#### format

##### 简介

根据提供的格式化字串返回格式化后的字符串。

##### 原型
```c++
格式化后的字符串 format(string formatString);
```

##### 参数

参数 | 解释
---- | -----
formatString | 格式字符串

##### 说明

格式化字串里：%Y，%M，%D，%h，%m，%s分别表示全宽度的年份（四位）、月份（两位）、日期（两位）、24小时制的小时（两位）、分钟（两位）、秒（两位）
%#Y，%#M，%#D，%#h，%#m，%#s分别表示压缩宽度，其中年份固定为两位，其余的在前面有无效0的时候会省略0
%%代表一个%

#### getDay

##### 简介

返回当前的日期(1-31)。

##### 原型
```c++
number getDay();
```

##### 返回

日期

#### getHour

##### 简介

返回现在的小时(0-23)。

##### 原型
```c++
number getHour();
```

##### 返回

小时

#### getMinute

##### 简介

返回现在的分钟(0-59)。

##### 原型
```c++
number getMinute();
```

##### 返回

分钟

#### getMonth

##### 简介

返回当前的月份(1-12)。

##### 原型
```c++
number getMonth();
```

##### 返回

月份

#### getSecond

##### 简介

返回现在的秒数(0-59)。

##### 原型
```c++
number getSecond();
```

##### 返回

秒数

#### getYear

##### 简介

返回当前的年份。

##### 原型
```c++
number getYear();
```

##### 返回

年份

#### setDay

##### 简介

设置当前的日期(1-31)。

##### 原型
```c++
void setDay(value );
```

#### setHour

##### 简介

设置当前的小时(0-23)。

##### 原型
```c++
void setHour(value );
```

#### setMinute

##### 简介

设置当前的分钟(0-59)。

##### 原型
```c++
void setMinute(value );
```

#### setMonth

##### 简介

设置当前的月份(1-12)。

##### 原型
```c++
void setMonth(value );
```

#### setSecond

##### 简介

设置当前的秒数(0-59)。

##### 原型
```c++
void setSecond(value );
```

#### setYear

##### 简介

设置当前的年份。

##### 原型
```c++
void setYear(number year);
```

## 类Flags

用于处理按位设置标记的情况，最多0-31位共32个标记。

### 函数

#### contains

##### 简介

判断num里有没有flags里的所有标记

##### 原型
```c++
bool contains(number num, number flags);
```

##### 示例

以下将演示一个从内容为
0xF0 的标记中判断是否存在 0xC1 中的所有标记

###### 示例代码

```c++
Flags.contains(0xF0, 0xC1)
```

###### 运行结果

```c++
false
```

#### mask

##### 简介

返回num是否包含flags的某一标记。

##### 原型
```c++
bool mask(number num, number flags);
```

##### 示例

以下将演示一个从内容为
0xF0 的标记中判断是否存在 0xC1 中的某一标记

###### 示例代码

```c++
Flags.mask(0xF0, 0xC1)
```

###### 运行结果

```c++
true
```

#### merge

##### 简介

将num设置完所有参数中的标记后返回。

##### 原型
```c++
number merge(number num[, number flag1, number flag2, ...)
```

##### 示例

以下将演示一个从内容为
0x02 的标记中合并上 0x01, 0x10

###### 示例代码

```c++
Flags.merge(0x02, 0x01, 0x10)
```

###### 运行结果

```c++
0x13
```

#### split

##### 简介

返回一个数组，包含num里所有存在的标记。

##### 原型
```c++
array split(number num);
```

## 类Math



### 属性

#### E

##### 简介

只读属性。

##### 权限

只读

#### PI

##### 简介

只读属性。

##### 权限

只读

### 函数

#### acos

##### 简介

返回反余弦值,参数单位为弧度。

##### 原型
```c++
number acos(number x);
```

#### asin

##### 简介

返回反正弦值,参数单位为弧度。

##### 原型
```c++
number asin(number x);
```

#### atan

##### 简介

返回反正切值,参数单位为弧度。

##### 原型
```c++
number atan(number x);
```

#### ceil

##### 简介

返回大于或等于x的最小整数。

##### 原型
```c++
integer ceil(number x);
```

#### cos

##### 简介

返回余弦值,参数单位为弧度。

##### 原型
```c++
number cos(number x);
```

#### floor

##### 简介

返回小于或等于x的最大整数。

##### 原型
```c++
integer floor(number x);
```

#### lg

##### 简介

返回以10为底的对数。

##### 原型
```c++
number lg(number x);
```

#### ln

##### 简介

返回自然对数。

##### 原型
```c++
number ln(number x);
```

#### log

##### 简介

返回以base为底的x的对数值。

##### 原型
```c++
number log(number base, number x);
```

#### pow

##### 简介

指数函数，返回x^y

##### 原型
```c++
number pow(number x, number y);
```

#### random

##### 简介

返回0-1的浮点数。和全局的random相比，这里采用的是随机数性能更好速度更慢些的mt19937算法。

##### 原型
```c++
number random();
```

##### 返回

0-1的浮点数

#### round

##### 简介

返回返回四舍五入后的整数。

##### 原型
```c++
integer round(number x);
```

#### sgn

##### 简介

符号函数,大于0返回1,等于0(误差10^-8)返回0,小于0返回-1。

##### 原型
```c++
integer sgn(number x);
```

#### sin

##### 简介

返回返回正弦值,参数单位为弧度。

##### 原型
```c++
number sin(number x);
```

#### sqrt

##### 简介

返回平方根。

##### 原型
```c++
number sqrt(number x);
```

#### tan

##### 简介

返回正切值,参数单位为弧度。

##### 原型
```c++
number tan(number x);
```

## 类Regex

使用Regex(regstr[,ignorecase=false])创建。

### 函数

#### getSubMatch

##### 简介

返回子匹配(即正则表达式里用()括住的字符串的匹配)数组，没有子匹配将返回空数组。

##### 原型
```c++
array getSubMatch(string str);
```

##### 示例

以下将演示一个从内容为
"abcd"
的字符串中匹配到的数组

###### 示例代码

```c++
Regex("(.)bc(.)").getSubMatch("abcd")
```

###### 运行结果

```c++
["abcd","a","d"]
```

#### matchAll

##### 简介

判断这个正则表达式是否可以全部匹配这个字符串,可以返回true,否则返回false。

##### 原型
```c++
bool matchAll(string str);
```

#### replaceAll

##### 简介

同[replaceFirst](#replaceFirst "replaceFirst"),只是对所有匹配串都进行替换

##### 原型
```c++
string replaceAll(string src, string dst);
```

##### 参数

参数 | 解释
---- | -----
src | 源字符串
dst | 目标字符串

#### replaceFirst

##### 简介

将src里第一个匹配替换成dst，dst里可以使用\1,\2等表示子匹配，\0表示整个的匹配串。

##### 原型
```c++
string replaceFirst(string src, string dst);
```

##### 参数

参数 | 解释
---- | -----
src | 源字符串
dst | 目标字符串

##### 示例

以下将演示一个从内容为
"abcd"
的字符串中匹配到的字符串

###### 示例代码

```c++
Regex("(.)bc(.)").replaceFirst("abcd","\0\1\2")
```

###### 运行结果

```c++
“abcdad”
```

#### search

##### 简介

返回所有匹配到的数组，匹配失败将返回空数组。

##### 原型
```c++
array search(string str);
```

##### 示例

以下将演示一个从内容为
"a1b2c3"
的字符串中匹配数组的示例

###### 示例代码

```c++
Regex("\d").search("a1b2c3")
```

###### 运行结果

```c++
[1,2,3]
```

## 类array

系统内置类，提供了对应类型的属性和方法。

### 属性

#### length

##### 简介

返回数组的长度。

##### 返回

integer 

##### 权限

只读

#### size

##### 简介

同length，返回数组的长度。

##### 返回

integer 

##### 权限

只读

### 函数

#### add

##### 简介

向数组尾部添加参数。

##### 原型
```c++
void add([anytype arg1, anytype arg2, ...)
```

#### clear

##### 简介

清空本字典。

##### 原型
```c++
void clear();
```

#### clone

##### 简介

复制出一份一样的新数组，更改新数组不会影响原数组。

##### 原型
```c++
array clone();
```

#### concat

##### 简介

会将此数组与参数中所有数组的元素连接起来形成的大数组，原数组不受影响。

##### 原型
```c++
string concat([array arr1, array arr2, ...)
```

##### 示例

以下将演示[1,2,3]和[3,2,1]连接的结果

###### 示例代码

```c++
[1,2,3].concat([3,2,1])
```

###### 运行结果

```c++
[1,2,3,3,2,1]
```

#### equals

##### 简介

比较本对象与value值是否相等。如果value是数组，会比较每个元素是否相等，长度较短的数组会补上void去做比较

##### 原型
```c++
bool equals(anytype value);
```

##### 示例

以下将演示[1,2,3]和[1,2,3,0]的比较

###### 示例代码

```c++
[1,2,3].equals([1,2,3,0])
```

###### 运行结果

```c++
true
```

#### erase

##### 简介

从数组中删除参数对应下标的元素，负数表示从后往前数，注意是从前往后逐个删除的，所以erase(1,1)会删除原数组下标为1,2位置的元素。越界会抛出异常。

##### 原型
```c++
void erase([integer index1, integer index2, ...)
```

#### find

##### 简介

返回数组中第一个等于value的元素的位置，使用==比较，找不到返回-1。

##### 原型
```c++
integer find(anytype value);
```

#### insert

##### 简介

在数组index位置插入一个新的value。

##### 原型
```c++
void insert(integer index, anytype value
```

##### 示例

以下将演示在[1,2,3]的2位置插入4的结果

###### 示例代码

```c++
var a=[1,2,3];
a.insert(2,4);
log(a);
```

###### 运行结果

```c++
[1,2,4,3]
```

#### join

##### 简介

将数组中所有元素转成字符串，然后用str连接。

##### 原型
```c++
string join(string str);
```

##### 参数

参数 | 解释
---- | -----
str | 分隔符

##### 示例

以下将演示用"-"连接[1,2,3]的结果

###### 示例代码

```c++
[1,2,3].join("-")
```

###### 运行结果

```c++
"1-2-3"
```

#### load

##### 简介

读取文件并按照换行切分为数组。

##### 原型
```c++
array load(string filename);
```

##### 参数

参数 | 解释
---- | -----
filename | 文件名

##### 示例

以下将演示一个从内容为
box}a
box}b
box}c
的1.txt文件载入为数组的示例：

###### 示例代码

```c++
[].load("1.txt")
```

###### 运行结果

```c++
["a","b","c"]
```

#### random

##### 简介

随机返回数组中一个元素。

##### 原型
```c++
anytype random();
```

#### remove

##### 简介

从数组中删除与参数相同的元素，使用==比较。

##### 原型
```c++
void remove([anytype arg1, anytype arg2, ...)
```

#### save

##### 简介

将字符串数组按照换行合并，并保存到文件

##### 原型
```c++
void save(string filename, bool append);
```

##### 参数

参数 | 解释
---- | -----
filename | 文件名
append | 是否追加在文件末尾。若为否，则覆盖整个文件。

##### 示例

以下将演示一个从内容为["a","b","c"]的数组写入文件的示例：

###### 示例代码

```c++
[].save("1.txt")
```

#### saveStruct

##### 简介

将数组进行序列化，并保存到文件。

##### 原型
```c++
void saveStruct(string filename, string mode);
```

##### 参数

参数 | 解释
---- | -----
filename | 文件名
mode | 模式。若首字母为'o'则字符串的其余部分代表一个偏移，文件将从该偏移处进行覆盖保存，负值将从文件末尾进行计算。若首字母为'z'则与'o'类似，只不过将启用压缩。

##### 说明

文件的内容可以直接使用[evalFile](#evalFile "evalFile")进行反序列化，读取至变量。

##### 示例

以下将演示一个从内容为[1,2,3]的数组写入文件的示例：

###### 示例代码

```c++
[1,2,3].saveStruct("1.txt")
```

#### sort

##### 简介

根据指定的函数或模式排序。会改动原字符串，没有返回值。

##### 原型
```c++
void sort(function func
string modestr="+"
```

##### 参数

参数 | 解释
---- | -----
func | 排序函数
modestr | 排序模式字符串

##### 说明

如果指定的是函数，将把此函数（func(a,b)）当做<的比较函数，从小到大排序。
如果指定的是模式字符串，则：
  "+"：以默认的比较运算符从小到大排序
  "-"：以默认的比较运算符从大到小排序
  "0"：按数值从小到大排序
  "9"：按数值从大到小排序
  "a"：按字符串从小到大排序
  "z"：按字符串从大到小排序

##### 示例

以下将演示[1,2,3]按"-"排序的结果

###### 示例代码

```c++
var a=[1,2,3];
a.sort("9");
log(a);
```

###### 运行结果

```c++
[3,2,1]
```

## 类dictionary

系统内置类，提供了对应类型的属性和方法。

### 函数

#### clone

##### 简介

复制出一份一样的新字典，更改新字典不会影响原字典。

##### 原型
```c++
dictionary clone();
```

#### equals

##### 简介

比较本对象与value值是否相等。如果value是字典，会比较每对键-值是否相等，不存在的键会认为值是void去做比较。

##### 原型
```c++
bool equals(anytype value);
```

##### 示例

以下将演示%[key1:1,key2:2]和%[key1:1,key2:2,key3:3]的比较

###### 示例代码

```c++
%[key1:1,key2:2].equals(%[key1:1,key2:2,key3:3])
```

###### 运行结果

```c++
false
```

#### erase

##### 简介

从字典中删除键与参数相同的元素，使用==比较。

##### 原型
```c++
void erase([anytype arg1, anytype arg2, ...)
```

#### except

##### 简介

从本字典中去除参数字典中包含的有效键（即值不为void）。

##### 原型
```c++
void except(dictionary dic);
```

#### find

##### 简介

返回字典中是否存在键名为key的键，值为空（void）的键将被视为无效键。

##### 原型
```c++
bool find(string key);
```

#### getKeyArray

##### 简介

返回所有有效键组成的数组。

##### 原型
```c++
array getKeyArray();
```

#### getValueArray

##### 简介

返回所有有效键的值组成的数组。

##### 原型
```c++
array getValueArray();
```

#### remove

##### 简介

从字典中删除值与参数相同的元素，使用==比较。

##### 原型
```c++
void remove([anytype arg1, anytype arg2, ...)
```

#### saveStruct

##### 简介

将数组进行序列化，并保存到文件。

##### 原型
```c++
void saveStruct(string filename, string mode);
```

##### 参数

参数 | 解释
---- | -----
filename | 文件名
mode | 模式。若首字母为'o'则字符串的其余部分代表一个偏移，文件将从该偏移处进行覆盖保存，负值将从文件末尾进行计算。若首字母为'z'则与'o'类似，只不过将启用压缩。

##### 说明

文件的内容可以直接使用[evalFile](#evalFile "evalFile")进行反序列化，读取至变量。

##### 示例

以下将演示一个从内容为%[key:1]的字典写入文件的示例：

###### 示例代码

```c++
%[key:1].saveStruct("1.txt")
```

#### sortKeyByValue

##### 简介

按值排序所有的有效键，比较的方式根据指定的函数或模式决定。

##### 原型
```c++
array sortKeyByValue(function func
string modestr="+"
```

##### 参数

参数 | 解释
---- | -----
func | 排序函数
modestr | 排序模式字符串

##### 说明

如果指定的是函数，将把此函数（func(a,b)）当做<的比较函数，从小到大排序。
如果指定的是模式字符串，则：
  "+"：以默认的比较运算符从小到大排序
  "-"：以默认的比较运算符从大到小排序
  "0"：按数值从小到大排序
  "9"：按数值从大到小排序
  "a"：按字符串从小到大排序
  "z"：按字符串从大到小排序

##### 示例

以下将演示%[key1:1,key2:2,key3:3]按"-"排序的结果

###### 示例代码

```c++
%[key1:1,key2:2,key3:3].sort("9");
```

###### 运行结果

```c++
["key3", "key2", "key1"]
```

#### toArray

##### 简介

返回[键1, 值1, 键2, 值2, ...]的数组，值为void的键将被无视。

##### 原型
```c++
array toArray();
```

#### update

##### 简介

与新字典合并，重复的键将被覆盖。

##### 原型
```c++
void update(dictionary dic);
```

## 类string

系统内置类，提供了对应类型的属性和方法。

### 属性

#### length

##### 简介

返回字符串的长度。

##### 返回

integer 

##### 权限

只读

#### size

##### 简介

同[length](#length "length")，返回字符串的长度。

##### 返回

integer 

##### 权限

只读

### 函数

#### beginWith

##### 简介

参数为字符串或正则表达式类。返回原字符串是否已参数给定的字符串开头。

##### 原型
```c++
bool beginWith(string str
Regex regexp
```

#### endWith

##### 简介

参数为字符串或正则表达式类。返回原字符串是否已参数给定的字符串结尾。

##### 原型
```c++
bool endWith(string str
Regex regexp
```

#### equals

##### 简介

比较本对象与value值是否相等。

##### 原型
```c++
bool equals(anytype value);
```

#### indexOf

##### 简介

第一个参数为字符串或正则表达式类。从startpos位置开始，寻找第一次出现参数1的位置。

##### 原型
```c++
integer indexOf(string str[, startpos = 0)
Regex regexp[, startpos = 0)
```

##### 示例

以下将演示在"1,2,,3"的查找","的结果

###### 示例代码

```c++
"1,2,,3".indexOf(",")
```

###### 运行结果

```c++
1
```

###### 示例代码

```c++
"1,2,,3".indexOf(",", 2)
```

###### 运行结果

```c++
3
```

#### lastIndexOf

##### 简介

第一个参数为字符串或正则表达式类。从endpos位置开始，向前寻找第一次出现参数1的位置。

##### 原型
```c++
integer lastIndexOf(string str[, endpos = 0)
Regex regexp[, endpos = 0)
```

##### 示例

以下将演示在"1,2,,3"的查找","的结果

###### 示例代码

```c++
"1,2,,3".lastIndexOf(",")
```

###### 运行结果

```c++
4
```

###### 示例代码

```c++
"1,2,,3".lastIndexOf(",", 2)
```

###### 运行结果

```c++
1
```

#### replace

##### 简介

参数为字符串或正则表达式类。将原字符串中str1全部替换为str2。

##### 原型
```c++
string replace(string str, string str2
Regex regexp, string str2
```

##### 示例

以下将演示将"aaa"中"a"替换为"ab"的结果

###### 示例代码

```c++
"aaa".replace("a", "ab")
```

###### 运行结果

```c++
"ababab"
```

#### split

##### 简介

第一个参数为字符串或正则表达式类。用第一个参数分割原字符串得到一串数组，ignorenull表示是否忽略结果数组中的空串，如果为真，结果数组中的空串将被抹去

##### 原型
```c++
array split(string str[, ignorenull = false)
Regex regexp[, ignorenull = false)
```

##### 示例

以下将演示用","来分割"1,2,,3"的结果

###### 示例代码

```c++
"1,2,,3".split(",")
```

###### 运行结果

```c++
["1", "2", "", "3"]
```

###### 示例代码

```c++
"1,2,,3".split(",", true)
```

###### 运行结果

```c++
["1", "2", "3"]
```

#### sprintf

##### 简介

格式化字符串，以本字符串为格式，根据传入的参数生成一个新的字符串。

##### 原型
```c++
string sprintf([anytype arg1, anytype arg2, ...)
```

##### 示例

以下将演示用"%04d"来格式化233的结果

###### 示例代码

```c++
"%04d".sprintf(233)
```

###### 运行结果

```c++
"0233"
```

#### substr

##### 简介

同[substring](#substring "substring")，取从start开始长度为len的子串，如果省略len，则取到原字符串末尾。如果start位置不合法，则返回空串。

##### 原型
```c++
string substr(integer start
integer start, integer len
```

#### substring

##### 简介

取子串

##### 原型
```c++
string substring(integer start
integer start, integer len
```

##### 说明

取从start开始长度为len的子串，如果省略len，则取到原字符串末尾。如果start位置不合法，则返回空串。

#### toLowerCase

##### 简介

返回新字符串，原字符串中所有大写字母被转化为小写。

##### 原型
```c++
string toLowerCase();
```

#### toUpperCase

##### 简介

返回新字符串，原字符串中所有小写字母被转化为大写。

##### 原型
```c++
string toUpperCase();
```

## 类undefined

系统内置类，提供了对应类型的属性和方法。

### 函数

#### equals

##### 简介

比较本对象与value值是否相等。

##### 原型
```c++
bool equals(anytype value);
```

