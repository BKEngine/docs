# 全局函数

## fileExist

### 简介

判断文件是否存在且可以被读取（即文件是否存在于文件系统或者封包中）

### 原型
```c++
bool fileExist(string filename);
```

### 参数

参数 | 解释
---- | -----
filename | 文件名

### 示例

以下代码判断"thanks.txt"是否存在

#### 示例代码

```c++
fileExist("thanks.txt")
```

#### 运行结果

```c++
false
```

# 全局类

## 类Channel

Channel类

### 函数

#### load

##### 简介

加载路径为file的文件

##### 原型
```c++
void load(string 文件的路径);
```

#### pause

##### 简介

暂停播放

##### 原型
```c++
void pause();
```

#### play

##### 简介

播放

##### 原型
```c++
void play(file );
```

##### 参数

参数 | 解释
---- | -----
 | ，vol，looptimes

#### resume

##### 简介

恢复播放

##### 原型
```c++
void resume();
```

#### seek

##### 简介

跳转到音频第time毫秒

##### 原型
```c++
void seek(time 毫秒时间);
```

#### stop

##### 简介

经过fadetime(毫秒)的淡出之后,停止播放

##### 原型
```c++
void stop(fadetime 毫秒时间);
```

#### tell

##### 简介

获得当前播放的时间进度(单位毫秒)

##### 原型
```c++
void tell();
```

## 类DownloadManager

DownloadManager类

### 属性

#### onError

##### 简介

下载出错时所调用的回调函数

##### 权限

只写

#### onProgress

##### 简介

下载正在进行时所调用的回调函数

##### 权限

只写

#### onSuccess

##### 简介

下载成功时所调用毁掉函数

##### 权限

只写

#### outFileName

##### 简介

设置输出文件的文件名

##### 权限

只写

#### packageUrl

##### 简介

设置要下载文件的URL

##### 权限

只写

### 函数

#### begin

##### 简介

开始下载

##### 原型
```c++
void begin();
```

#### stop

##### 简介

停止下载

##### 原型
```c++
void stop();
```

## 类History

History类

### 函数

#### add

##### 简介

往历史记录里添加字符串text,reline决定之后是否要换行，默认为false

##### 原型
```c++
void add(string );
```

##### 参数

参数 | 解释
---- | -----
 | ,bool

#### getDataAtLine

##### 简介

返回第line行的历史记录

##### 原型
```c++
string getDataAtLine(int );
```

##### 返回

历史记录

#### getParent

##### 简介

返回该精灵的父精灵

##### 原型
```c++
父精灵 getParent();
```

#### reline

##### 简介

换行

##### 原型
```c++
void reline();
```

#### repage

##### 简介

换页

##### 原型
```c++
void repage();
```

## 类Json

json类

### 函数

#### fromJson

##### 简介

讲一个Json格式化字符串转换成parser变量，返回变量

##### 原型
```c++
var fromJson(string Json格式化字符串);
```

#### toJson

##### 简介

讲一个parser变量转换成Json格式化字符串，返回字符串

##### 原型
```c++
string toJson(var );
```

##### 返回

Json格式化字符串

## 类Network

Network类

### 函数

#### download

##### 简介

创建并返回一个packageUEL=URL,outFileName-outFileName的DownloadManger实例

##### 原型
```c++
DownloadManger download(packageURL );
```

##### 参数

参数 | 解释
---- | -----
 | ,outFileName

#### getString

##### 简介

从URL处获取该文件的字符串,如果网络连接失败则会返回空字符.在返回字符串之前该线程的脚本会阻塞在此命令

##### 原型
```c++
string getString(URL );
```

##### 返回

网络连接失败会返回字符串

#### memoryStatus

##### 简介

打印当前内存使用状态

##### 原型
```c++
void memoryStatus();
```

#### printCallStack

##### 简介

打印当前脚本调用栈

##### 原型
```c++
void printCallStack();
```

#### request

##### 原型
```c++
void request(dic );
```

## 类SaveData

存储数据类

### 函数

#### exist

##### 简介

编号为n的存档是否存在

##### 原型
```c++
bool exist(int 存档编号);
```

##### 返回

是否存在

#### getText

##### 简介

获取存档时存入的额外字符串，若未保存额外字符串或存档不存在则返回空

##### 原型
```c++
string getText(string 存档的额外字符串);
```

##### 返回

& void

#### getTime

##### 简介

获取编号为n的存档时间，是一个Date类，存档不存在则返回void

##### 原型
```c++
Date getTime(int 存档编号);
```

##### 返回

& void

## 类System

系统类。

### 属性

#### FPSEnabled

##### 简介

是否开启FPS显示

##### 返回

bool 

##### 权限

只读

#### actionCount

##### 简介

当前正在执行action的层的数量

##### 返回

int 

##### 权限

只读

#### appFullName

##### 简介

主程序的全路径（包含文件名）

##### 返回

string 

##### 权限

只读

#### appName

##### 简介

主程序的文件名（不含路径）

##### 返回

string 

##### 权限

只读

#### appPath

##### 简介

主程序的路径

##### 返回

string 

##### 权限

只读

#### autoMode

##### 简介

是否开启自动模式

##### 返回

bool 

##### 权限

只读

#### autoModeTime

##### 简介

自动模式时间，单位ms

##### 返回

int 

##### 权限

只读

#### fontColor

##### 简介

**当前消息层**的文字颜色

##### 返回

int 

##### 权限

只写

#### fontSize

##### 简介

**当前消息层**的文字大小

##### 返回

int 

##### 权限

只写

#### fontSizeFactor

##### 简介

文字全局缩放比例

##### 说明

用于外部调整文字大小。默认1.0

##### 返回

number 

##### 权限

只读

#### fontStyle

##### 简介

**当前消息层**的文字样式

##### 返回

int 

##### 权限

只写

#### fullScreen

##### 简介

是否全屏显示

##### 说明

**在移动端此参数无效。**

##### 返回

bool 

##### 权限

只读

#### gameName

##### 简介

游戏名称

##### 返回

string 

##### 权限

只读

#### gameTitle

##### 简介

游戏标题

##### 返回

string 

##### 权限

只读

#### maxFrameSpeed

##### 简介

最高帧速

##### 说明

**除非你知道你在做什么，否则请不要动这个变量。**

##### 返回

int 

##### 权限

只读

#### mouseCursorAutoHideTime

##### 简介

鼠标自动消失的时间

##### 说明

**仅启用自定义鼠标指针时有效。**
单位为ms，默认为2000

##### 返回

int 

##### 权限

只读

#### mouseStatus

##### 简介

鼠标的状态

##### 说明

类型为数组，长度固定为5。5个数组成员分别为鼠标的X坐标，Y坐标（整数），左、中、右三个键的按下状态（bool）

##### 返回

array 

##### 权限

只读

#### mouseWheel

##### 简介

鼠标滚轮的旋转量

##### 说明

正数是向上。

##### 返回

int 

##### 权限

只读

#### platform

##### 简介

当前运行的平台

##### 说明

值为"windows","macos","linux","ios","android","winphone"其中之一

##### 返回

string 

##### 权限

只读

#### resolutionSize

##### 简介

游戏分辨率

##### 说明

可以用于UI相关的计算，长度固定为2，2个数组成员分别为宽和高。

##### 返回

array 

##### 权限

只读

#### saveHistory

##### 简介

是否将历史记录保存进存档

##### 返回

bool 

##### 权限

只读

#### showingText

##### 简介

当前是否正在显示文字

##### 返回

bool 

##### 权限

只读

#### skipAll

##### 简介

是否允许跳过未读文本

##### 返回

bool 

##### 权限

只读

#### skipMode

##### 简介

是否开启跳过模式

##### 返回

bool 

##### 权限

只读

#### stable

##### 简介

脚本静止状态

##### 说明

当脚本中遇到l, p, click, waitbutton并等待的时候被标记为true。

##### 返回

bool 

##### 权限

只读

#### textSpeed

##### 简介

文字速度

##### 说明

值从0到100，代表每显示一个文字耗时100ms到0ms（瞬间显示）。

##### 返回

int 

##### 权限

只读

#### touchPointEnabled

##### 简介

是否显示触摸点

##### 返回

bool 

##### 权限

只读

#### transCount

##### 简介

当前正在执行trans的层的数量

##### 返回

int 

##### 权限

只读

#### transitionEnabled

##### 简介

是否允许渐变特效

##### 说明

若为否，则所有trans特效皆适用trans的normal模式。

##### 返回

bool 

##### 权限

只写

#### version

##### 简介

已读文本信息
BKEngine版本号

##### 说明

readinfo[脚本名][标签名]=该标签已读过的偏移量
可以用来检测标签是否被经过

##### 返回

int 

##### 权限

只读

#### windowSize

##### 简介

窗口大小

##### 说明

**注意，窗口大小并不等于游戏分辨率大小。你不应该将此变量用于游戏界面相关的计算中。**

##### 返回

vec2 

##### 权限

只读

### 函数

#### call

##### 简介

访问某个标签，等同于bkscr中call指令

##### 原型
```c++
void call(string label, string file, function callback);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件
callback | 从标签return时触发的回调

#### exit

##### 简介

退出程序

##### 原型
```c++
void exit();
```

#### go

##### 简介

让脚本从等待状态（等待按钮、等待点击等等）恢复，继续执行

##### 原型
```c++
void go();
```

#### goto

##### 简介

跳转到某个脚本，等同于bkscr中jump指令

##### 原型
```c++
void goto(string label, string file);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件

##### 说明

和[jump](#jump "jump")指令等同

#### jump

##### 简介

跳转到某个脚本，等同于bkscr中jump指令

##### 原型
```c++
void jump(string label, string file);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件

##### 说明

和[goto](#goto "goto")指令等同

#### openUrl

##### 简介

打开一个网页

##### 原型
```c++
void openUrl();
```

#### runCmd

##### 简介

调用一个bkscr指令。

##### 原型
```c++
void runCmd(string name, dictionary param, function callback);
```

##### 参数

参数 | 解释
---- | -----
name | 调用的bks指令名
param | 调用的参数列表
callback | 函数真正执行完毕时触发的回调

##### 说明

如调用wait*系列函数，则在wait的条件被触发、等待结束时callback回调才被触发。正常指令则立刻触发回调。
text指令则等待文字打印完成才触发回调。

#### showText

##### 简介

脚本类
在文本框打印一段文字。等同于bkscr中text命令。

##### 原型
```c++
void showText(string text, function callback);
```

##### 说明

**不可实例化。**

## 类Timer

时间类

### 属性

#### enable

##### 简介

设置enable的状态

##### 权限

只写

#### interval

##### 简介

设置timer计数的间隔

##### 权限

只写

### 函数

#### clearTimeout

##### 简介

删除用setTimeout注册的函数。

##### 原型
```c++
void clearTimeout(func );
```

#### forceTrigger

##### 简介

强制触发一次，并更新下次触发的时间。

##### 原型
```c++
void forceTrigger(func );
```

#### setTimeout

##### 简介

延迟delay毫秒后执行func，传入的第一个参数是实际的延迟时间，之后将args依次传入。执行一次后自动删除.

##### 原型
```c++
void setTimeout(func );
```

##### 参数

参数 | 解释
---- | -----
 | ,delay,*args

