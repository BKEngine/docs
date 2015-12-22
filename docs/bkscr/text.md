
[TOC]

## text
在文字框中显示文字，相当于直接在脚本中写文本。  

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	text	|	✓	|	String	|	文字内容	|

```javascript
//以下两行等同
[text text="这是一行文字"]
这是一行文字
```

---

## textwindow
设置文字框。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	file	|		|	String	|	文字框背景图片，与color不能同时指定	|
|	color	|		|	Color	|	文字框底色，与file不能同时指定	|
|	opacity	|		|	Number	|	文字框透明度	|
|	pos   	|		|	Point	|	文字框相对于游戏画面的坐标	|
|	rect	|		|	Rectangle	|	文字内容区的大小，相对于文字框	|
|	xinterval|		|	Number	|	字间距(px)	|
|	yinterval|		|	Number	|	行间距(px)	|

```javascript
[textwindow file="ui/textwindow.png" opacity=255 pos=[0,420] rect=[5,5,600,200]]
[textwindow color=0xff6600 xinterval=3 yinterval=10]
```

!!! important "说明"
    非必须的参数若不写则为保持原有设置，这点与其他指令不同。

---

## textcursor
文字光标，可使用普通精灵或动画精灵。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	光标精灵的编号	|
|	follow	|	✓	|	Boolean	|	是否跟随在文字末尾出现	|
|	pos   	|		|	Point	|	若follow为false，需指定光标的固定位置（坐标相对于文字框）	|

```javascript
[textcursor index=10 follow=true]
[textwindow index=10 follow=false pos=[5,160]]
```

---

## textoff
隐藏文字框。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	time	|		|	Number	|	淡出时间，默认为0	|

```javascript
[textoff]
[textoff time=300]
```

---

## texton
显示文字框。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	time	|		|	Number	|	淡入时间，默认为0	|

```javascript
[texton]
[texton time=300]
```

---

## textspeed
调节文字显示速度。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	interval|	✓	|	Number	|	文字显示的速度，范围0-100，100为立即显示	|

```javascript
[textspeed interval=50]
```

---

## textstyle
修改文字样式。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	name    |   	|	String	|	字体文件名	|
|	size    |   	|	Number	|	字号	|
|	color	|   	|	Color	|	颜色	|
|	bold	|   	|	Boolean	|	是否为粗体	|
|	italic	|   	|	Boolean	|	是否为斜体	|
|	strike	|   	|	Boolean	|	是否加删除线	|
|	under	|   	|	Boolean	|	是否加下划线	|
|	shadow	|   	|	Boolean	|	开启阴影	|
|	shadowcolor	|   	|	Color	|	阴影颜色	|
|	stroke	|   	|	Boolean	|	开启描边	|
|	strokecolor|   	|	Color	|	描边颜色	|


```javascript
[textstyle name="font/SourceHans.otf" size=22]
[textstyle shadow=true shadowcolor=0x333333]
```

!!! important "说明"
    非必须的参数若不写则为保持原有设置，这点与其他指令不同。
    
---

## texttag
定义文本tag处理。  
默认tag标记为`【】`，括号内的内容将作为参数传入处理标签中。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	label	|	✓	|	String	|	处理用的标签	|
|	file	|		|	String	|	标签所在文件，默认为当前文件	|

```javascript
*main
[texttag label="*tagHandler"]
【小明|xm_voice_1.ogg】我们是共产主义接班人！
...
...
*otherlabels

*texttag
##
var tags = tag.split("|",true);
var name = tags[0];	//"小明"
var voice = tags[1];	//"xm_voice_1.ogg"
##
@return

```

---

## textsprite
创建一个文字精灵，文字精灵是一种特殊的精灵。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index   |   ✓	|	Number	|	要创建的精灵编号	|
|	text    |   ✓	|	String	|	文字内容	|
|	font    |   	|	String	|	字体文件名	|
|	size    |   	|	Number	|	字号	|
|	color	|   	|	Color	|	颜色	|
|	width	|   	|	Number	|	最大宽度(px)，默认为-1（不限制）	|
|	height	|   	|	Number	|	最大高度(px)，默认为-1（不限制）	|
|	xinterval|		|	Number	|	字间距(px)	|
|	yinterval|		|	Number	|	行间距(px)	|
|	extrachar|		|	String	|	超过高宽时显示省略字符，默认为"..."	|
|	bold	|   	|	Boolean	|	是否为粗体	|
|	italic	|   	|	Boolean	|	是否为斜体	|
|	strike	|   	|	Boolean	|	是否加删除线	|
|	under	|   	|	Boolean	|	是否加下划线	|
|	shadow	|   	|	Boolean	|	开启阴影	|
|	shadowcolor	|   	|	Color	|	阴影颜色	|
|	stroke	|   	|	Boolean	|	开启描边	|
|	strokecolor|   	|	Color	|	描边颜色	|

```javascript
[textsprite index=10 text="示例文字" size=20 color=0xff6600]
[textsprite index=20 text='第一行\n第二行' width=100 extrachar="……"]
```

!!! important "说明"
    非必须的参数若不写则为保持原有设置，这点与其他指令不同。  
    若需要创建多行文本的文字精灵，请使用`\n`换行，并使用单引号表示字符串（如上例二）。双引号中的`\n`不会被识别为换行符。  

---

## locate
改变下一次文字绘制位置。

|	参数名	|	必须	|	类型	|	说明 |
|	:---:	| :-: 	| :--:	|	:--	|
|	x	|		|	Number	|	x坐标，默认为当前坐标	|
|	y	|		|	Number	|	y坐标，默认为当前坐标	|

```javascript
[locate x=100 y=50]
```

---

## 文字风格快捷开关
一共有4种开关，分别为：  

- 开关斜体	`[i]`
- 开关粗体	  `[b]`
- 开关删除线	`[s]`
- 开关下划线	`[u]`

示例：

```javascript
这是一行普通的文本，可以同时混合[i]斜体[i]、[b]粗体[b]、[s]删除线[s]、[u]下划线[u]使用；
也可以多个同时使用，如加了[b][u]下划线的粗体[b][u]等。
```

实际效果：
> 这是一行普通的文本，可以同时混合<i>斜体</i>、<b>粗体</b>、<s>删除线</s>、<u>下划线</u>使用；  
> 也可以多个同时使用，如加了<b><u>下划线的粗体</b></u>等。

---

## 换行、清屏、等待点击、等待换页

- 换行	`[r]`
- 清屏	`[er]`
- 等待点击	`[l]`
- 等待换页	  `[p]`

这4个指令是游戏中最常用的指令。

示例：

```javascript
这是一行文本[r]这是第二行[l]点击后才能看到这些文字[p]
前面的文字都没有了，再点击这一行也会消失。[l][er]
```

---

## ruby
显示小字注释（常用于日文中汉字上标记假名等）。

|	参数名	|	必须	|	类型	|	说明 |
|	:---:	| :-: 	| :--:	|	:--	|
|	text	|	✓	|	String	|	注释内容	|
|	size	|		|	Number	|	注释字号，默认为6	|
|	char	|		|	Number	|	被注释的字符数，默认为1	|

```javascript
日语中，汉字写作和读作[ruby text="かん"]漢[ruby text="じ"]字
```

效果：  
> 日语中，汉字写作和读作<ruby>漢<rt>かん</rt>字<rt>じ</rt></ruby>

---

## storefont
暂存当前字体信息。

## restorefont
恢复先前存储的字体信息。

```javascript
...
[storefont]
...(修改字体信息)
[restorefont]
...
```

---

#messagelayer
额外初始化一个消息层或切换到某个已经存在的消息层，不同的消息层之前文字风格（textstyle）和绘制位置不同。  
适合以下场景：  

- 同时在两个不同的地方输出文字
- 交替进行的对话等文字风格或位置相差较大，频繁使用`textstyle``locate`等命令不利于后续修改

|	参数名	|	必须	|	类型	|	说明 |
|	:---:	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的消息层编号	|
|	active	|		|	Boolean	|	是否激活，默认为false	|
|	char	|		|	Number	|	被注释的字符数，默认为1	|

```javascript
//若编号对应的消息层不存在
[messagelayer index=1 active=true]  //创建消息层，编号为1，并切换到此层。
[messagelayer index=1 active=false]  //创建消息层，编号为1，但不切换到此层。

//若编号对应的消息层已存在
[messagelayer index=1]  //切换到此层
[messagelayer index=message_layer]  //切换到默认消息层
[messagelayer index=1 active=false]  //没有任何效果
```

!!! important "说明"
    消息层与精灵共用一套编号系统，注意冲突问题。  
    默认的消息层编号为-2，对应的内置变量为`message_layer`。
