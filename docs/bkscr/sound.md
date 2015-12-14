
[TOC]

##se
播放音效。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	file	|	✓	|	String	|	音频文件名	|
|	channel	|		|	Number	|	通道号，默认为0	|
|	loop	|		|	Boolean	|	是否循环，默认为true	|
|	vol		|		|	Number	|	音量，取值范围0-100，默认为100（最大）	|
|	fadein	|		|	Number	|	淡入时间(ms)，默认为0	|

```javascript
[se file="se/hit.wav"]
[se file="se/run.wav" fadein=300 loop=true]
```

!!! important "说明"
	bgm命令使用通道号-1，voice命令使用通道号-2，这两个命令的详细用法见下。

---

##bgm
播放背景音乐。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	file	|	✓	|	String	|	音频文件名	|
|	loop	|		|	Boolean	|	是否循环，默认为true	|
|	vol		|		|	Number	|	音量，取值范围0-100，默认为100（最大）	|
|	fadein	|		|	Number	|	淡入时间(ms)，默认为0	|
|	loopto	|		|	Number	|	循环起始位置(ms)	|

```javascript
[bgm file="bgm/001.ogg"]
[bgm file="bgm/002.ogg" fadein=1000 loopto=60000]
```

---

##voice
播放语音。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	file	|	✓	|	String	|	音频文件名	|
|	vol		|		|	Number	|	音量，取值范围0-100，默认为100（最大）	|


```javascript
[voice file="voice/A_00001.ogg"]
[voice file="voice/B_00001.ogg" vol=80]
```

---

##stop
停止特定通道的播放。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	channel	|		|	Number	|	通道号，默认为全部通道	|
|	fadeout	|		|	Number	|	淡入时间(ms)，默认为0	|


```javascript
[stop]
[stop channel=bgm]	//停止背景音乐播放
[stop channel=voice]	//停止语音播放
```

---

##volume
读取或改变某个通道的音量。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	channel	|	✓	|	Number	|	要读取或改变音量的通道号	|
|	get		|	○	|	Variable	|	信息保存到的变量，不能与set同时存在	|
|	set		|	○	|	Number	|	新的音量值，不能与get同时存在	|

```javascript
[volume channel=bgm set=80]	//修改背景音乐音量为80
[volume channel=0 get=ch0Vol]
```

---

##pause
暂停某个通道的播放。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	channel	|	✓	|	Number	|	通道号	|

```javascript
[pause channel=bgm]
[pause channel=0]
```

---

##resume
恢复某个通道的播放。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	channel	|	✓	|	Number	|	通道号	|

```javascript
[resume channel=bgm]
[resume channel=0]
```

---

##fade
将某个通道的音量渐变至另一个值。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	channel	|	✓	|	Number	|	通道号	|
|	time	|	✓	|	Number	|	渐变时间(ms)	|
|	to		|	✓	|	Number	|	将要变化到的音量	|
|	stop	|		|	Boolean	|	渐变完成后是否停止播放，默认为false	|

```javascript
[fade channel=bgm time=1000 to=80]
[fade channel=0 time=500 to=0 stop=true]
```




