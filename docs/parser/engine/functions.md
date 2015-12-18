[TOC]

## fileExist
判断文件是否存在且可以被读取（即文件是否存在于文件系统或者封包中）

```cpp
bool fileExist(string filename);
```

参数 | 说明
---- | -----
filename | 文件名

**示例**
```cpp
fileExist("thanks.txt") //return false
```

---