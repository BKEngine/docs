
[TOC]

##sprite
从指定的文件创建一个精灵。   

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的精灵编号	|
|	file	|	✓	|	String	|	图片文件名	|
|	rect	|		|	Rectangle	|	截取的图片范围，默认为整个图片	|

```javascript
[sprite index=10 file="image/girl.png"]
[sprite index=20 file="image/bg.png" rect=[0,0,800,600]]
```

---

##addto
将精灵添加到屏幕或其他精灵之上

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要添加的精灵编号	|
|	target	|	✓	|	Number	|	目标精灵编号	|
|	zorder	|		|	Number	|	精灵的叠加次序，默认为0，数字高的在上面	|
|	pos		|		|	Point	|	添加到的坐标（与目标精灵的相对坐标），默认为[0,0]	|
|	opacity	|		|	Number	|	精灵的透明度，取值范围为0-255，默认为255（不透明）	|
|	modal	|		|	Boolean	|	是否为模态，默认为false，具体说明见下	|

!!! important "说明"
	modal为true时，当前精灵将以模态层的形式显示。即该精灵将接管事件处理（包括键盘、鼠标悬浮、鼠标点击、tab选中等）。  
	当模态层被移除（remove），事件处理权将归还至上一个模态层。basic_layer为最低优先级的模态层。  
	`basic_layer`是内置变量，值为-1，代表最顶级的精灵层（即屏幕本身），将精灵添加到其上后，该精灵及其子精灵才会绘制在游戏画面上。  
	同一个精灵无法被同时添加到多个地方。
	
```javascript
//将编号为20的精灵添加到编号为10的精灵上，叠加次序为0
[addto index=20 target=10 zorder=0]	
//将编号为20的精灵添加到编号为10的精灵的[100,50]位置上，叠加次序为1（可能会遮挡20号精灵）
[addto index=21 target=10 pos=[100,50] zorder=1] 
//将编号为10的精灵添加到屏幕，该精灵将显示在游戏画面上，其子精灵20 21也一同显示
[addto index=10 target=basic_layer]	
```

---

##layer
创建一个层。层是一种特殊的精灵，可作为精灵的容器使用（想象一下白板与贴在上面的海报的关系）。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要创建的精灵编号	|
|	width	|	✓	|	Number	|	层的宽度	|
|	height	|	✓	|	Number	|	层的高度	|
|	color	|		|	Color	|	层的背景颜色，默认为白色（0xffffff）	|
|	opacity	|		|	Number	|	层的透明度，取值范围为0-255，默认为0（完全透明）	|

```javascript
//创建一个宽400，高300的层，编号为10
[layer index=10 width=400 height=300]
//将编号为20的精灵添加到编号为10的层上，叠加次序为0
[addto index=20 target=10 zorder=0]	
//将编号为10的层添加到屏幕，层与其上的精灵将显示在游戏画面上
[addto index=10 target=basic_layer]
```

!!! important "说明"
	虽然此处对层指定了宽度和高度，但其只对背景颜色的范围有约束作用，即在指定宽高范围内显示背景颜色，超出部分为透明；  
	**层上的子精灵即使超出了层的宽高也不会被剪裁。**若需要剪裁，请使用效果类中的剪裁指令。

---

##remove
从游戏画面移除一个精灵。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要移除的精灵编号	|
|	delete	|		|	Boolean	|	是否销毁精灵，默认为false	|

```javascript
//从屏幕或父精灵上取下编号为10的精灵，但并未销毁，编号为10的精灵可以再次使用。
[remove index=10] 
//从屏幕或父精灵上取下编号为20的精灵并销毁，若再次使用必须重新用sprite指令创建该精灵。
[remove index=20 delete=true] 
```

---

##removeall
从游戏画面移除某个精灵的全部子精灵，但该精灵不会被移除。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number	|	要移除的精灵编号	|
|	delete	|		|	Boolean	|	是否销毁精灵，默认为false	|
|	recursive	|		|	Boolean	|	是否递归销毁，默认为false	|

```javascript
[removeall index=10] 
[removeall index=20 delete=true recursive=true] 
```

---

##info
获取一个图片文件的信息，并将其保存在指定的变量中。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	file	|	✓	|	String	|	要获取信息的图片文件名	|
|	get		|	✓	|	Variable	|	信息保存到的变量	|

```javascript
[info file="image/bg.png" get=imgInfo]
```

!!! important "说明"
	信息数据为字典格式，有`filename` `width` `height`等成员。  
	例如获取一个宽高为`[800，600]`的`"image/bg.png"`文件信息，保存至`imgInfo`变量，那么imgInfo.filename值为`"image/bg.png"`，imgInfo.width值为`800`。

---

##infoex
获取一个精灵的信息，并将其保存在指定的变量中。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number		|	要获取信息的精灵编号	|
|	get		|	✓	|	Variable	|	信息保存到的变量	|

```javascript
[infoex index=10 get=imgInfo]
```

!!! important "说明"
	信息数据为字典格式，有`filename` `width` `height` `type` `pos`等成员。  
	
---

##anchor
获取一个精灵的信息，并将其保存在指定的变量中。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number		|	要获取信息的精灵编号	|
|	get		|	○	|	Variable	|	信息保存到的变量	|
|	set		|	○	|	String/Point	|	锚点位置描述或详细坐标	|
|	keep	|		|	Boolean	|	是否根据锚点变化改变坐标，默认为false	|

```javascript
[anchor index=10 get=imgAnchor]
[anchor index=10 set="center"]
[anchor index=10 set=[10,50]]
```

!!! important "说明"
	get与set参数不可同时使用。  
	set参数可用字符串表示，可选位置有：center、topleft、topright、topcenter、leftcenter、rightcenter、bottomleft、bottomcenter、bottomright
	
---

##zorder
调整/获取一个精灵的叠加次序。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number		|	要获取信息的精灵编号	|
|	get		|	○	|	Variable	|	信息保存到的变量	|
|	set		|	○	|	String/Point	|	锚点位置描述或详细坐标	|

```javascript
[zorder index=10 get=imgZorder]
[zorder index=10 set=1]
```

!!! important "说明"
	get与set参数不可同时使用。  
	
---

##spriteopt
设置一个精灵的某些属性。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	index	|	✓	|	Number		|	要获取信息的精灵编号	|
|	disable	|		|	Boolean	|	是否禁用（禁用后将不会触发任何事件），默认不改变当前值	|
|	recursive	|		|	Boolean	|	是否递归设置属性，默认为true	|

```javascript
[spriteopt index=10 disable=true recursive=true]
``` 
	
---
