
// [TOC]





## 类Channel

音频通道类

**可创建实例**

使用Channel(int channelNo)或Channel("bgm"或"voice")直接创建。

### 属性

#### fileName

##### 简介

该通道播放音频的文件名

##### 返回

string 

##### 权限

只读

#### isPaused

##### 简介

是否处于暂停状态

##### 返回

bool 

##### 权限

只读

#### isPlaying

##### 简介

是否正在播放

##### 返回

bool 

##### 权限

只读

#### loopTimes

##### 简介

循环次数

##### 返回

integer 

##### 权限

只读

#### loopTo

##### 简介

歌曲循环的终点，单位为毫秒

##### 返回

number 

##### 权限

只读

#### musicVolume

##### 简介

bgm通道的总体音量，范围为0-100。

##### 说明

实际音量为bgm命令或volume属性设置的音量乘上总体音量/100。

##### 返回

number 

##### 权限

只读

#### soundVolume

##### 简介

voice通道的总体音量，范围为0-100。

##### 说明

实际音量为bgm命令或volume属性设置的音量乘上总体音量/100。

##### 返回

number 

##### 权限

只读

#### voiceVolume

##### 简介

se通道（编号>=0的通道）的总体音量，范围为0-100。

##### 说明

实际音量为bgm命令或volume属性设置的音量乘上总体音量/100。

##### 返回

number 

##### 权限

只读

#### volume

##### 简介

歌曲的音量，范围为0-1

##### 返回

number 

##### 权限

只读

### 函数

#### load

##### 简介

加载路径为file的文件

##### 原型
```cpp
void load(string file);
```

##### 参数

参数 | 解释
---- | -----
file | 文件的路径

#### pause

##### 简介

暂停播放

##### 原型
```cpp
void pause();
```

#### play

##### 简介

播放音频

##### 原型
```cpp
void play(string file, integer vol, int looptimes);
```

##### 参数

参数 | 解释
---- | -----
file | 音频文件名
vol | 0-100，音量
looptimes | 循环次数，bgm通道默认此值为-1，即无限循环。其余通道默认为0，即不循环。

#### resume

##### 简介

恢复播放

##### 原型
```cpp
void resume();
```

#### seek

##### 简介

跳转到音频第time毫秒

##### 原型
```cpp
void seek(number time);
```

##### 参数

参数 | 解释
---- | -----
time | 毫秒时间

#### stop

##### 简介

经过fadetime(毫秒)的淡出之后,停止播放

##### 原型
```cpp
void stop(integer fadetime);
```

##### 参数

参数 | 解释
---- | -----
fadetime | 毫秒时间

#### tell

##### 简介

获得当前播放的时间进度(单位毫秒)

##### 原型
```cpp
double tell();
```

##### 返回

时间位置

## 类Debug

调试类，仅开发模式可用，用于打印一些游戏当前的状态。

**不可实例化**

### 函数

#### memoryStatus

##### 简介

打印当前各部分内存使用状态。

##### 原型
```cpp
void memoryStatus();
```

#### printAliveSprites

##### 简介

打印当前正在使用的精灵

##### 原型
```cpp
void printAliveSprites();
```

#### printCallStack

##### 简介

打印当前脚本调用栈

##### 原型
```cpp
void printCallStack();
```

#### printDeadSprites

##### 简介

打印当前所有精灵中未被使用（也就是被remove但是未被删除的精灵）

##### 原型
```cpp
void printDeadSprites();
```

#### printSprites

##### 简介

打印当前所有精灵

##### 原型
```cpp
void printSprites();
```

## 类DownloadManager

DownloadManager类

**必须创建实例才能使用**

此类支持断网重连和断点续传

构造函数DownloadManager(string url, string fileName)

把url地址的文件下载到本地fileName。

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

下载成功时所调用回调函数

##### 权限

只写

#### outFileName

##### 简介

输出文件的文件名，下载过程中修改无效。

##### 返回

string 

##### 权限

只读

#### packageUrl

##### 简介

将要下载文件的URL，下载过程中修改无效。

##### 返回

string URL

##### 权限

只读

### 函数

#### begin

##### 简介

开始下载

##### 原型
```cpp
void begin();
```

#### stop

##### 简介

停止下载

##### 原型
```cpp
void stop();
```

## 类Event

事件类，代表BKEngine里一个回调事件，可由系统触发或用户手动触发。

构造函数：

### 属性

#### enable

##### 简介

事件是否启用。

##### 返回

bool 

##### 权限

只读

#### exp

##### 简介

脚本型事件执行的表达式。

##### 返回

string 

##### 权限

只读

#### file

##### 简介

事件跳转到的脚本名称。

##### 返回

string 

##### 权限

只读

#### func

##### 简介

纯函数事件触发时执行的函数。

##### 返回

function 

##### 权限

只读

#### ignore

##### 简介

事件是否忽略重复。

##### 返回

bool 

##### 权限

只读

#### label

##### 简介

事件跳转到脚本的标签。

##### 返回

string 

##### 权限

只读

#### name

##### 简介

事件的名称。

##### 返回

string 

##### 权限

只读

#### param

##### 简介

事件触发时传递的默认参数。

##### 返回

dictionary 

##### 权限

只读

#### type

##### 简介

事件的类型，为"jump", "callback"或"call"。

##### 返回

string 

##### 权限

只读

### 函数

#### call

##### 简介

主动调用这个事件。

##### 原型
```cpp
void call(Sprite sprite, dictionary param = NULL

integer spriteIndex, dictionary param = NULL
```

##### 参数

参数 | 解释
---- | -----
sprite | 发出事件的精灵，void表示无。
spriteIndex | 发出事件的精灵编号。
param | 参数字典。

#### toVar

##### 简介

将事件转化为原本的变量形式，即Event构造函数的参数。

##### 原型
```cpp
anytype toVar();
```

##### 返回

原本的事件表达形式。

##### 说明

如果事件是个名称引用事件，则返回name的字符串。

如果事件是个纯函数事件，则返回func。

如果事件是个匿名脚本事件，则返回相应的数组。

## 类EventCenter

事件系统类，管理BKEngine里注册过的所有事件。

**不可实例化**

### 函数

#### delete

##### 简介

删除事件。

##### 原型
```cpp
void delete(string name);
```

##### 参数

参数 | 解释
---- | -----
name | 事件名称

##### 说明

删除一个给定名称的事件。

#### get

##### 简介

获得一个已被注册的事件。

##### 原型
```cpp
void get(string name);
```

##### 参数

参数 | 解释
---- | -----
name | 事件名称

##### 说明

可以用这个函数来获取事件系统中对应名字的事件。

#### register

##### 简介

注册事件。

##### 原型
```cpp
void register(string name, Event event);
```

##### 参数

参数 | 解释
---- | -----
name | 事件名称
event | 事件

##### 说明

注册一个给定名称的事件，如果event=void则删除这个名称对应的事件。

#### send

##### 简介

主动触发一个事件。

##### 原型
```cpp
void send(string name, dictionary param);
```

##### 参数

参数 | 解释
---- | -----
name | 事件名称
param | 参数字典。

##### 说明

如果用户注册过同名事件，将触发该事件，否则触发系统默认的处理方式。

如click的默认响应是对话框翻页，当脚本里改写了click事件后，该函数会触发改写过的事件

该函数可以用来触发用户自己注册的事件。

#### sendSystem

##### 简介

主动触发一个系统事件。

##### 原型
```cpp
void sendSystem(string name, dictionary param);
```

##### 参数

参数 | 解释
---- | -----
name | 事件名称
param | 参数字典。

##### 说明

该函数将触发系统默认的处理方式。

如click的默认响应是对话框翻页，即使脚本里改写了click事件，该函数依旧会使用系统默认的处理方式（即对话框翻页）

## 类History

历史记录类

**不能创建实例**

历史记录有三种模式"pageMode", "lineMode", "pageTagMode"。意义分别如下：

pageMode：

  按页记录，每经过一次p命令记录一个新的历史记录项（即data数组增加一位成员）。

  每一项是一个字典，参数有：

    tag：该页的tag（文本最开始【】括住的字串），如有多个记录最后一个。

    text：该页的文本，包括页内的回车\n。

    voice：该页的声音，以p命令之前最后一个出现的voice命令为准。

    ruby：记录ruby。类型为数组，成员是%[pos:起始的位置, char:占的主文本的字符数, size:ruby大小, text:ruby文本]。每有一个ruby该数组增加一个成员。

lineMode：

  按行记录，每经过一次r命令记录一个新的历史记录项（即data数组增加一位成员），当History.maxChars不为0时，一行文本超过maxChars长度也会产生一个新的历史记录项。

  每一项是一个字典，参数有：

    newline：布尔，是否是r命令导致的换行，为否表示是由于History.maxChars导致的强制换行。

    tag：该行的tag（文本最开始【】括住的字串）。

    text：该行的文本。

    voice：该行的声音，以r命令之前最后一个出现的voice命令为准。

    ruby：记录ruby。类型为数组，成员是%[pos:起始的位置, char:占的主文本的字符数, size:ruby大小, text:ruby文本]。每有一个ruby该数组增加一个成员。

pageTagMode：

  按页和tag记录，每经过一次p命令记录一个新的历史记录项（即data数组增加一位成员），这个成员是个数组，每出现一个tag增加一个成员，数组的0位置保留给记录该页最开始到出现第一个tag之间的文本用，第一个tag会被记录到1位置。

  data[curline][curtagindex]为一个字典，结构同pageMode的字典。

### 属性

#### count

##### 简介

当前已有的历史记录的数目。

##### 返回

integer 

##### 权限

只读

#### curIndex

##### 简介

最近记录的历史记录在data数组中的位置。

##### 返回

integer 

##### 权限

只读

#### data

##### 简介

历史记录的总数据。

##### 说明

不要直接访问就该这个变量除非你知道你在做什么……

##### 返回

array 

##### 权限

只读

#### enabled

##### 简介

是否开启历史记录。关闭时，显示的文本不会被记录进去。

##### 返回

bool 

##### 权限

只读

#### maxChars

##### 简介

行模式下强制换行的文字数。记录文本超过这个文字数时历史记录会强制换行，为0表示禁用这个功能。

##### 返回

integer 

##### 权限

只读

#### maxPage

##### 简介

历史记录的最大行数/页数。

##### 返回

integer 

##### 权限

只读

#### nextIndex

##### 简介

当前显示文本要被记录在历史记录的data数组中的位置。

##### 返回

integer 

##### 权限

只读

#### recordMode

##### 简介

当前历史记录的模式。有"pageMode", "lineMode", "pageTagMode"三种，详情见History类的说明。

##### 返回

string 

##### 权限

只读

#### startIndex

##### 简介

最早一条历史记录在data数组中的位置。

##### 返回

integer 

##### 权限

只读

### 函数

#### add

##### 简介

往历史记录里添加字符串text，reline决定之后是否要换行。

##### 原型
```cpp
void add(string text, bool reline);
```

##### 参数

参数 | 解释
---- | -----
text | 文本
reline | 是否换行

#### clear

##### 简介

清空历史记录。

##### 原型
```cpp
void clear();
```

#### getDataAtLine

##### 简介

返回往前数第line条历史记录，0为当前这条。

##### 原型
```cpp
dictionary getDataAtLine(int line);
```

##### 参数

参数 | 解释
---- | -----
line | 行数

##### 返回

历史记录

#### reline

##### 简介

换行

##### 原型
```cpp
void reline();
```

#### repage

##### 简介

换页

##### 原型
```cpp
void repage();
```

## 类Json

json类

**不可实例化**

### 函数

#### fromJson

##### 简介

将一个Json格式化字符串转换成parser变量，返回变量

##### 原型
```cpp
anytype fromJson(string Json格式化字符串);
```

##### 返回

返回的变量

#### toJson

##### 简介

将一个parser变量转换成Json格式化字符串，返回字符串

##### 原型
```cpp
string toJson(anytype var);
```

##### 参数

参数 | 解释
---- | -----
var | 要转换的变量

##### 返回

Json格式化字符串

## 类Live2DSprite

Live2D精灵类，是Sprite类的子类。可以使用Sprite类的所有属性和方法。

通过Live2DSprite(int index = -1)来创建一个精灵。（实质上是对该编号精灵的一个引用）

### 属性

#### onFlick

##### 简介

鼠标划过时的事件。

##### 返回

Event 

##### 权限

只读

#### onTap

##### 简介

鼠标点击时的事件。

##### 返回

Event 

##### 权限

只写

### 函数

#### getMotionNum

##### 简介

获得动作组里的动作数目。

##### 原型
```cpp
integer getMotionNum(string name);
```

##### 参数

参数 | 解释
---- | -----
name | 动作组名称

#### setExpression

##### 简介

设置表情。

##### 原型
```cpp
integer setExpression(string name);
```

##### 参数

参数 | 解释
---- | -----
name | 表情动作的名称

##### 返回

返回0表示成功，-1表示名称未找到

#### setExpressionFile

##### 简介

设置表情。

##### 原型
```cpp
integer setExpressionFile(string file, bool relative);
```

##### 参数

参数 | 解释
---- | -----
file | 表情文件的名称
relative | 是否为相对主模型的路径。

##### 返回

返回0表示成功，-1表示文件未找到

#### setRandomExpression

##### 简介

设置一个随机的表情。

##### 原型
```cpp
void setRandomExpression();
```

#### startMotion

##### 简介

通过指定动作的组名与编号来开始一个动作。

##### 原型
```cpp
integer startMotion(string name, integer no, string priority);
```

##### 参数

参数 | 解释
---- | -----
name | 动作的组名称
no | 动作在该组中的编号，可以取以下值："none"，"idle"，"normal"，"force"
priority | 优先级

##### 返回

返回0表示成功，-1表示priority被占用

#### startMotionFile

##### 简介

通过指定动作的文件名来开始一个动作。

##### 原型
```cpp
integer startMotionFile(string name, string sound, bool relative, string priority, bool lipsync, integer fadein, integer fadeout);
```

##### 参数

参数 | 解释
---- | -----
name | 动作的文件名称
sound | 声音文件
relative | 指name参数是否为相对主模型文件的相对路径。
priority | 优先级
lipsync | 有声音时，是否嘴唇同步。
fadein | 淡入时间
fadeout | 淡出时间

##### 返回

返回0表示成功，-1表示priority被占用，-2表示文件未找到

#### startRandomMotion

##### 简介

随机开始指定组名里的一个动作。

##### 原型
```cpp
integer startRandomMotion(string name, string priority);
```

##### 参数

参数 | 解释
---- | -----
name | 动作的组名称
priority | 优先级

##### 返回

返回0表示成功，-1表示priority被占用，-2表示motion组为空

#### stopMotion

##### 简介

停止动作。

##### 原型
```cpp
void stopMotion();
```

## 类MessageLayer

消息层精灵类，是Sprite类的子类。可以使用Sprite类的所有属性和方法。

通过MessageLayer(int index = -1)来创建一个精灵。（实质上是对该编号精灵的一个引用）

### 属性

#### curposX

##### 简介

当前光标的y位置。

##### 返回

integer 

##### 权限

只写

## 类Network

Network类

**不可创建实例**

### 函数

#### download

##### 简介

创建并返回一个packageUEL=URL,outFileName-outFileName的DownloadManger实例

##### 原型
```cpp
DownloadManger download(string packageURL, string outFileName
```

#### getString

##### 简介

从URL处获取该文件的字符串,如果网络连接失败则会返回空字符.在返回字符串之前该函数会处于等待状态。

##### 原型
```cpp
string getString(string URL);
```

##### 参数

参数 | 解释
---- | -----
URL | 访问的网址

##### 返回

返回字符串

#### request

##### 简介

发出网络请求

##### 原型
```cpp
void request(dictionary option);
```

##### 参数

参数 | 解释
---- | -----
option | 参数字典

##### 说明

根据给出的option发出网络请求。

option需要的成员如下：

  [async]：是否异步（非阻塞）。可缺省，默认是true。

  url：访问的网址，字符串。

  type：访问类型，字符串，可取的值有"put", "get", "post", "delete"。

  [cookies]：cookies，字符串，可缺省。

  [success]：成功时的回调函数，可缺省。回调格式为success(data, cookies)，data是request的结果，为字符串或字典（当返回的是个Json时将自动转化为字典）

  [error]：失败时的回调函数，可缺省。回调格式为error(errCode, errMsg)，errCode是错误码，errMsg是错误信息。

  [datatype]：post和put模式下有效，为字符串，可取的值有"text", "json", "urlencoded"。默认是"urlencoded"。

  [data]：get模式时，传过去的参数。datatype有效且为"urlencoded"时，data需要为一个字典，其余情况下data需要为一个字符串。无论何时该成员都可以缺省，缺省值为void。

## 类SaveData

存档数据类

**不能创建实例**

### 函数

#### exist

##### 简介

编号为n的存档是否存在

##### 原型
```cpp
bool exist(int SaveNo);
```

##### 参数

参数 | 解释
---- | -----
SaveNo | 存档编号

##### 返回

是否存在

#### getText

##### 简介

获取存档时存入的额外字符串，若未保存额外字符串或存档不存在则返回空(void)

##### 原型
```cpp
string getText();
```

##### 返回

存档时写入的额外字符串

#### getTime

##### 简介

获取编号为n的存档时间，是一个Date类，存档不存在则返回void

##### 原型
```cpp
Date getTime(int SaveNo);
```

##### 参数

参数 | 解释
---- | -----
SaveNo | 存档编号

#### remove

##### 简介

删除存档文件，并在存档信息里清除这个存档。

##### 原型
```cpp
void remove(int SaveNo);
```

##### 参数

参数 | 解释
---- | -----
SaveNo | 存档编号

#### stashApply

##### 简介

应用该临时存档。

##### 原型
```cpp
void stashApply(StashSaveItem saveitem);
```

##### 参数

参数 | 解释
---- | -----
saveitem | 临时存档类（内部类）

#### stashSave

##### 简介

返回当前实时存档的一个副本。

##### 原型
```cpp
StashSaveItem stashSave();
```

##### 返回

saveitem 临时存档类（内部类）

##### 说明

返回值是一个内部类StashSaveItem，没有属性和方法，仅可以被传入[stashApply](#stashApply "stashApply")函数用。

## 类Spine

Spine动画精灵类，是Sprite类的子类。可以使用Sprite类的所有属性和方法。

通过Spine(int index = -1)来创建一个精灵。（实质上是对该编号精灵的一个引用）

### 属性

#### boundingBox

##### 简介

该精灵该状态下的显示范围。

##### 返回

vector4 

##### 权限

只读

#### timeScale

##### 简介

动画的时间缩放倍数。

##### 返回

number 

##### 权限

只读

### 函数

#### addAnimation

##### 简介

添加一个动画。

##### 原型
```cpp
void addAnimation(integer trackIndex, string name, bool loop, number delay);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号，从0开始
name | 动画名称
loop | 是否循环播放。
delay | 如果指定动画和当前动画相同，是否强制从头播放。

#### clearAllTrack

##### 简介

清除所有动画。

##### 原型
```cpp
void clearAllTrack();
```

#### clearTrack

##### 简介

清除动画。

##### 原型
```cpp
void clearTrack(integer trackIndex);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号。

#### mixAnimation

##### 简介

动画渐变。

##### 原型
```cpp
void mixAnimation(string fromAnimation, string toAnimation, float duration);
```

##### 参数

参数 | 解释
---- | -----
fromAnimation | 起始动画名称
toAnimation | 目标动画名称
duration | 切换时间。

#### setAnimation

##### 简介

设置动画。

##### 原型
```cpp
void setAnimation(integer trackIndex, string name, bool loop, bool forcereset);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号，从0开始
name | 动画名称
loop | 是否循环播放。
forcereset | 如果指定动画和当前动画相同，是否强制从头播放。

#### setCompleteListener

##### 简介

给一个动画轨设置动画自然结束的回调事件。

##### 原型
```cpp
void setCompleteListener(integer trackIndex, function callback);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号
callback | 回调函数

##### 说明

当回调函数为空时，表示取消这个回调事件。

当给一个动画轨中的动画被自然结束时，触发此事件。

回调函数的参数格式为：callback(int trackIndex, int loopCount)

  trackIndex为发出这个事件的动画轨的编号。

  loopCount为这个动画循环了的的次数。

#### setEndListener

##### 简介

给一个动画轨设置动画被结束的回调事件。

##### 原型
```cpp
void setEndListener(integer trackIndex, function callback);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号
callback | 回调函数

##### 说明

当回调函数为空时，表示取消这个回调事件。

当给一个动画轨中的动画被非自然结束时（比如该动画轨被clear或该动画被新动画取代），触发此事件。

回调函数的参数格式为：callback(int trackIndex)

  trackIndex为发出这个事件的动画轨的编号。

#### setEventListener

##### 简介

给一个动画轨设置播放时的回调事件。

##### 原型
```cpp
void setEventListener(integer trackIndex, function callback);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号
callback | 回调函数

##### 说明

当回调函数为空时，表示取消这个回调事件。

在spine工具中，可以设置一个动画在何时触发事件，及其参数。

当动画播放到定义了事件的位置时，即触发此回调。

回调函数的参数格式为：callback(int trackIndex, string eventName, int eventIntValue, float eventFloatValue, string eventStringValue)

  trackIndex为发出这个事件的动画轨的编号。

  eventName为这个事件的名称。

  eventIntValue为这个事件的整型参数。

  eventFloatValue为这个事件的浮点参数。

  eventStringValue为这个事件的字符串参数。

  以上三个参数的具体含义由事件定义的时候决定。

#### setStartListener

##### 简介

给一个动画轨设置动画开始的回调事件。

##### 原型
```cpp
void setStartListener(integer trackIndex, function callback);
```

##### 参数

参数 | 解释
---- | -----
trackIndex | 动画轨的编号
callback | 回调函数

##### 说明

当回调函数为空时，表示取消这个回调事件。

回调函数的参数格式为：callback(int trackIndex)

  trackIndex为发出这个事件的动画轨的编号。

## 类Sprite

精灵类

通过Sprite(int index = -1)来创建一个精灵。（实质上是对该编号精灵的一个引用）

### 属性

#### angle

##### 简介

精灵的逆时针旋转角度，单位为度。

##### 返回

number 

##### 权限

只读

#### disabled

##### 简介

是否禁用事件。禁用后，该精灵将不响应鼠标等事件。

##### 返回

bool 

##### 权限

只写

#### disabledRecursive

##### 简介

是否递归禁用事件。所有子精灵也会被递归设置。

##### 返回

bool 

##### 权限

只写

#### filename

##### 简介

精灵图像的文件名。有些精灵（如screenshot得到的）这个值为空。

##### 返回

string 

##### 权限

只读

#### focusable

##### 简介

是否可以被聚焦。为真时，可以通过上下左右和tab键选中此精灵。

##### 返回

bool 

##### 权限

只写

#### height

##### 简介

精灵显示的高度。

##### 说明

会随scale的改变而改变。

##### 返回

number 

##### 权限

只读

#### imageHeight

##### 简介

精灵图像文件的高度。

##### 返回

integer 

##### 权限

只读

#### imageWidth

##### 简介

精灵图像文件的宽度。

##### 返回

integer 

##### 权限

只读

#### index

##### 简介

该精灵的编号。

##### 返回

integer 

##### 权限

只读

#### onClick

##### 简介

鼠标在精灵上完成一次左键单击时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onEnter

##### 简介

鼠标移入精灵时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onHover

##### 简介

鼠标在精灵上移动时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onKeyDown

##### 简介

焦点在精灵上时，按下按键触发的事件。

##### 返回

Event 

##### 权限

只写

#### onKeyUp

##### 简介

焦点在精灵上时，松开按键触发的事件。

##### 返回

Event 

##### 权限

只写

#### onLeave

##### 简介

鼠标离开精灵时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onMouseWheel

##### 简介

焦点在精灵上时，滚动滚轮触发的事件。

##### 返回

Event 

##### 权限

只写

#### onRClick

##### 简介

鼠标在精灵上完成一次右键单击时触发的事件。

##### 返回

Event 

##### 权限

只写

#### onTouchBegan

##### 简介

鼠标左键在精灵上按下时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onTouchEnded

##### 简介

鼠标在精灵上左键松开时触发的事件。

##### 返回

Event 

##### 权限

只读

#### onTouchMoved

##### 简介

鼠标在精灵上左键按下后移动时触发的事件。

##### 返回

Event 

##### 权限

只读

#### opacity

##### 简介

精灵的透明度（0-255）。

##### 返回

integer 

##### 权限

只读

#### rect

##### 简介

精灵图像的显示范围。

##### 返回

vector4 

##### 权限

只读

#### type

##### 简介

该精灵的类型。

##### 返回

string 

##### 权限

只读

#### value

##### 简介

该精灵的值。

##### 说明

不同的精灵对该属性有不同的定义，比如：

  inputbox：输入框的值

  slider：滑条的值

  checkbox：复选框是否被选中

##### 返回

anytype 

##### 权限

只读

#### visible

##### 简介

精灵是否可见。

##### 说明

该值表示该精灵自身可不可见。当一个精灵被从父精灵卸下，或其不处于basic_layer的子精灵中时，即使本身可见也不会显示出来。

##### 返回

bool 

##### 权限

只读

#### width

##### 简介

精灵显示的宽度。

##### 说明

会随scale的改变而改变。

##### 返回

number 

##### 权限

只读

#### x

##### 简介

相对父精灵的左边位置。父精灵左上角为x=0，y=0处。

##### 返回

number 

##### 权限

只读

#### y

##### 简介

相对父精灵的上边位置。父精灵左上角为x=0，y=0处。

##### 返回

number 

##### 权限

只读

#### zorder

##### 简介

精灵的层级，在同一父层的所有子精灵里zorder越大越往上。

##### 返回

integer 

##### 权限

只读

### 函数

#### create

##### 简介

从图片文件创建一个精灵，相当于sprite脚本命令。

##### 原型
```cpp
Sprite create(integer index, string file, vector4 rect);
```

##### 参数

参数 | 解释
---- | -----
index | 要创建的精灵编号
file | 图片文件
rect | 裁剪范围，默认为不裁剪

##### 返回

一个精灵类或void（创建失败时）

#### getChildren

##### 简介

获得所有子精灵

##### 原型
```cpp
array getChildren();
```

##### 返回

(Sprite) 包含所有子精灵类的数组。

#### getParent

##### 简介

返回该精灵的父精灵

##### 原型
```cpp
Sprite getParent();
```

#### hasChild

##### 简介

是否存在子精灵

##### 原型
```cpp
bool hasChild();
```

#### idlesp

##### 简介

获得一个空闲的精灵编号，相当于idlesp脚本命令。

##### 原型
```cpp
integer idlesp();
```

##### 返回

一个空闲的精灵编号

#### removeAllChildren

##### 简介

移除所有子精灵

##### 原型
```cpp
void removeAllChildren();
```

#### removeFromParent

##### 简介

从父精灵上移除

##### 原型
```cpp
void removeFromParent();
```

#### saveImage

##### 简介

保存图片

##### 原型
```cpp
void saveImage(string filename, bool hasChildren);
```

##### 参数

参数 | 解释
---- | -----
filename | 图片的文件名
hasChildren | 是否包括子精灵

## 类System

系统类。

记录着一些系统相关的属性和类，用以获取预先定义的设定和控制引擎底层一些实现。

**不可实例化。**

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

integer 

##### 权限

只读

#### actualCurLabel

##### 简介

当前实际的标签

##### 返回

string 

##### 权限

只读

#### actualCurScript

##### 简介

当前实际的脚本

##### 返回

string 

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

#### autoModeDisabled

##### 简介

是否禁止自动阅读模式

##### 返回

bool 

##### 权限

只写

#### autoModeTime

##### 简介

自动模式等待时间，单位ms

##### 返回

integer 

##### 权限

只读

#### curLabel

##### 简介

当前的标签

##### 说明

该属性忽略宏调用产生的标签。

##### 返回

string 

##### 权限

只读

#### curScript

##### 简介

当前的脚本名

##### 说明

该属性忽略宏调用产生的脚本。

##### 返回

string 

##### 权限

只读

#### debugSkipMode

##### 简介

调试版本使用，是否开启强制跳过模式，所有延时等待都将被取消

##### 返回

bool 

##### 权限

只读

#### displayedResolutionSize

##### 简介

游戏显示分辨率

##### 说明

**仅启用高分辨率素材时设置**。

注意：windowSize设置游戏窗口的大小，默认情况下，分辨率仍为原分辨率，图片将自动缩放匹配窗口大小。

若要启动不同分辨率的素材，设置此值，游戏内所有图片素材将在相应的子文件夹下寻找。

如设置displayedResolutionSize为[1024, 768]，则图片优先从1024x768文件夹下寻找，如找到则启用对应的素材代替原素材。

同windowSize，该值不应参与坐标的计算。

设置此值后，还应同时修改windowSize才能看出效果，否则将出现高分辨率素材对应低分辨率窗口的情况。（某些时候还会出现锯齿）

##### 返回

vector2 

##### 权限

只写

#### fontColor

##### 简介

**当前消息层**的文字颜色

##### 返回

integer 

##### 权限

只写

#### fontSize

##### 简介

**当前消息层**的文字大小

##### 返回

integer 

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

integer 

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

integer 

##### 权限

只读

#### mouseCursorAutoHideTime

##### 简介

鼠标自动消失的时间

##### 说明

**仅启用自定义鼠标指针时有效。**

单位为ms，默认为2000

##### 返回

integer 

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

integer 

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

vector2 

##### 权限

只读

#### saveHistory

##### 简介

是否将历史记录保存进存档

##### 返回

bool 

##### 权限

只读

#### screenSize

##### 简介

已读文本信息

当前屏幕的分辨率大小

##### 说明

readinfo[脚本名][标签名]=该标签已读过的偏移量

可以用来检测标签是否被经过

##### 返回

vector2 

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

#### skipModeDisabled

##### 简介

是否禁止快进模式

##### 返回

bool 

##### 权限

只写

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

值从0到100，代表每显示一个文字耗时100ms到0ms（瞬间显示），非线性的插值。

##### 返回

integer 

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

integer 

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

BKEngine版本号

##### 返回

integer 

##### 权限

只读

#### windowSize

##### 简介

窗口大小

##### 说明

**注意，窗口大小并不等于游戏分辨率大小。你不应该将此变量用于游戏界面相关的计算中。**

##### 返回

vector2 

##### 权限

只读

### 函数

#### call

##### 简介

访问某个标签，等同于bkscr中call指令。

##### 原型
```cpp
void call(string label, string file, function callback);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件
callback | 从标签return时触发的回调

#### callback

##### 简介

触发一个callback回调。

##### 原型
```cpp
void callback(string label, string file, bool blocked, string exp, dictionary param, bool ignored);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件
blocked | 是否阻塞
exp | 执行的表达式
param | 传递的参数
ignored | 如果存在相同的callback，是否忽略本callback

#### exit

##### 简介

退出程序

##### 原型
```cpp
void exit();
```

#### getCurrentRead

##### 简介

查看现在的剧本有没有读过。

##### 原型
```cpp
bool getCurrentRead();
```

##### 返回

是否已读

#### go

##### 简介

让脚本从等待状态（等待按钮、等待点击等等）恢复，继续执行

##### 原型
```cpp
void go();
```

#### goto

##### 简介

跳转到某个脚本，等同于bkscr中jump指令

##### 原型
```cpp
void goto(string label, string file);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件

##### 说明

和[jump](#jump "jump")指令等同

#### isLabelReaded

##### 简介

查看指定标签有没有读过。

##### 原型
```cpp
bool isLabelReaded(string label, string file);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件

##### 返回

是否已读过

#### jump

##### 简介

跳转到某个脚本，等同于bkscr中jump指令

##### 原型
```cpp
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
```cpp
void openUrl(string url);
```

##### 参数

参数 | 解释
---- | -----
url | 网址

#### return

##### 简介

等同于bkscr中return指令。

##### 原型
```cpp
void return();
```

#### returnTo

##### 简介

等同于bkscr中returnto指令。

##### 原型
```cpp
void returnTo(string label, string file);
```

##### 参数

参数 | 解释
---- | -----
label | 标签
file | 文件

#### run

##### 简介

运行系统命令，或执行其他程序。（WP8和IOS无效果）

##### 原型
```cpp
void run(string file, string param);
```

##### 参数

参数 | 解释
---- | -----
file | 要执行的文件名
param | 执行时带的参数

#### runCmd

##### 简介

调用一个bkscr指令。

##### 原型
```cpp
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
```cpp
void showText(string text, function callback);
```

##### 说明

**不可实例化。**

## 类TextSprite

文字精灵类，是Sprite类的子类。可以使用Sprite类的所有属性和方法。

通过TextSprite(int index = -1)来创建一个精灵。（实质上是对该编号精灵的一个引用）

### 属性

#### color

##### 简介

文字颜色。为0xAARRGGBB格式的数字或#AARRGGBB格式的颜色，或两个颜色组成的数组。

##### 返回

color 

##### 权限

只读

#### fontName

##### 简介

字体名称。

##### 返回

string 

##### 权限

只写

#### fontSize

##### 简介

字体大小。

##### 返回

integer 

##### 权限

只写

#### fontStyle

##### 简介

字体样式。

##### 说明

字体样式为一个整数，由以下的值组合而成：

无样式：0

加粗：1

斜体：2

下划线：4

删除线：8

##### 返回

integer 

##### 权限

只写

#### text

##### 简介

文本。

##### 返回

string 

##### 权限

只写

## 类Timer

定时器类，用于隔一段时间执行一个函数或单次延迟执行一个函数。

**可创建实例**

构造函数：Timer(function func, number interval, ... args)

func表示定时执行的函数。

interval表示每次执行的时间间隔，单位毫秒。

args是传递给函数的参数。

函数回调的格式如下func(dt, args)

dt是这次调用和上次调用之间的实际时间差，单位毫秒。

args是构造时传入的参数。

### 属性

#### enable

##### 简介

设置定时器是否处于工作状态。

##### 返回

bool 

##### 权限

只读

#### interval

##### 简介

定时器的触发的间隔，设为0同样会使定时器被禁用

##### 返回

number 

##### 权限

只读

### 函数

#### clearTimeout

##### 简介

删除用setTimeout注册的函数。

##### 原型
```cpp
void clearTimeout(func );
```

#### forceTrigger

##### 简介

强制触发一次，并更新下次触发的时间。

##### 原型
```cpp
void forceTrigger();
```

#### setTimeout

##### 简介

延迟delay毫秒后执行func(dt, args)，dt是实际的延迟时间，单位毫秒，之后将args依次传入。执行一次后自动删除.

##### 原型
```cpp
void setTimeout(function func, number delay, ... args
```

