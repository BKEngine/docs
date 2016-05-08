
[TOC]

”动作“是指精灵的移动、缩放、晃动等补间动作，他们都归属于`action`指令。

通过`action`系列指令可以创建复杂的精灵补间动画效果，补间动画分为串行和并行两种执行方式：

- 并行：多个动画（移动、旋转、缩放等）同时进行，可通过[`parallel`](#parallel)方法指定。
- 串行：多个动画（移动、旋转、缩放等）按顺序逐个进行，可通过[`queue`](#queue)方法指定。
- 若不指定执行方法，默认为并行方式。
- 动作集：由[`parallel`](#parallel)或[`queue`](#queue)包裹的一系列动作，可嵌套。


## queue
创建一个串行动作集合（串行动作集），由此行指令开始到[`end`](#end)方法内的动作或动作集之间按指令顺序逐个执行。

```javascript
[action "queue"]
...
[action "end"]
```

---

## parallel
创建一个并行动作集合（并行动作集），由此行指令开始到[`end`](#end)方法内的动作或动作集同时执行。

```javascript
[action "parallel"]
...
[action "end"]
```

---

## end
结束一段动作集的声明。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	target	|		|	Number	|	动作集的默认作用对象（精灵编号）	|
|	times	|		|	Number	|	反复执行的次数，负数表示无限循环，默认为1	|

!!! important "说明"
    若单个动作指令中设置了`target`，则此处的`target`对其无效。  
    此处的`target`仅对动作集中未指定`target`的动作有效。


```javascript
[action "parallel"]
...
[action "end" target=10]
```

---

## start
结束所有动作集的声明，并开始动画过程。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	target	|		|	Number	|	动作集的默认作用对象（精灵编号）	|
|	times	|		|	Number	|	反复执行的次数，负数表示无限循环，默认为1	|

!!! important "说明"
    若单个动作指令中设置了`target`，则此处的`target`对其无效。  
    此处的`target`仅对动作集中未指定`target`的动作有效。


```javascript
[action "parallel"]
...
[action "start" target=10] 

//相当于
[action "parallel"]
...
[action "end" target=10] 
[action "start"] 
```

---

## moveby
相对移动。

|	参数名	|	必须	|	类型	|	说明 |
|	:---: 	| :-: 	| :--:	|	:--	|
|	target	|		|	Number	|	动作集的默认作用对象（精灵编号）	|
|	time	|		|	Number	|	动作时长	|
|	pos   	|		|	Point	|	偏移量	|
|	ease   	|		|	String/Number	|	反复执行的次数，负数表示无限循环，默认为1	|

```javascript



```

!!! important "说明"
    若单个动作指令中设置了`target`，则此处的`target`对其无效。  
    此处的`target`仅对动作集中未指定`target`的动作有效。
