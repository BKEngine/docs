
[TOC]

BKEngine提供了丰富帧动画模式，同时提供简单的控制选项，他们都归属于`animate`指令。  
帧动画是一种特殊的精灵。

## horizontal
通过精灵表单(spritesheet)横向读取片段并创建帧动画精灵。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的精灵编号	|
|	file	|	✓	|	String	|	精灵表单文件名	|
|	frame	|	✓	|	Number	|	每行的帧数	|
|	row   	|		|	Number	|	行数，默认为1	|
|	interval|		|	Number	|	每帧的播放时间(ms)，默认为33	|
|	loop	|		|	String	|	动画循环模式，默认为“forward”，说明见下	|

!!! important "说明"
	循环模式可选的值有：  
    1. `none` 不循环  
    2. `forward` 单项循环（正向播放完最后一帧后跳回第一帧继续正向播放）  
    3. `bouncing` 弹性循环（正向播放完最后一帧后反向播放回第一帧）  

```javascript
[animate "horizental" index=10 file="animate/sheet.png" frame=10 row=2 loop="bouncing"]
```

---

## vertical
通过精灵表单(spritesheet)纵向读取片段并创建帧动画精灵。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的精灵编号	|
|	file	|	✓	|	String	|	精灵表单文件名	|
|	frame	|	✓	|	Number	|	每列的帧数	|
|	column	|		|	Number	|	列数，默认为1	|
|	interval|		|	Number	|	每帧的播放时间(ms)，默认为33	|
|	loop	|		|	String	|	动画循环模式，同horizental	|

```javascript
[animate "vertical" index=10 file="animate/sheet.png" frame=10 column=2 loop="bouncing"]
```

---

## multifiles
通过多个单帧文件创建帧动画精灵。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的精灵编号	|
|	file	|	✓	|	[String]|	文件名数组	|
|	interval|		|	Number	|	每帧的播放时间(ms)，默认为33	|
|	loop	|		|	Boolean	|	动画是否循环，默认为true	|
|	delay	|		|	Number	|	每次循环之间的间隔，默认为0	|

```javascript
[animate "multifiles" index=10 file=["animate/frame1.png","animate/frame2.png","animate/frame3.png"] loop=true]
```

---

## start
开始播放。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	精灵编号	|

```javascript
[animate "start" index=10]
```

---

## cell
修改动画精灵当前帧。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	精灵编号	|
|	frame	|	✓	|	Number	|	与修改到的帧号	|

```javascript
[animate "cell" index=10 frame=2]
```

---

## start
停止播放。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	精灵编号	|

```javascript
[animate "stop" index=10]
```