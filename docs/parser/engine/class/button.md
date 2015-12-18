## 按钮类(Button)
按钮类是Sprite类的子类。可以使用Sprite类的所有属性和方法。  
通过`Button(int index = -1)`来创建一个精灵。（实质上是对该编号精灵的一个引用）


| 属性 | 说明 | 返回 | 权限 |
| :---: | :---: | :---: | :---: |
| click | 左键按下状态时的精灵，不存在则返回void | Sprite | 只读 |
| hover | 悬浮态时的精灵，不存在则返回void | Sprite | 只读 |
| idle | 常态时的精灵 | Sprite | 只读 |

---