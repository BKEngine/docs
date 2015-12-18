# CSV文档类(CSVParser)
构造函数CSVParser()  
可以通过继承此类，重载doLine函数，然后调用doFile或doDocument来解析csv文件  
也可以使用静态方法fromFile和fromDocument来直接解析完一个csv文件。

---

## doDocument
解析一个csv内容的字符串，会触发doLine回调。

```cpp
void doDocument(string csvString);
```

参数 | 解释
---- | -----
csvString | 字符串

---

## doFile
解析一个csv文件
相当于将文件内容读成字符串再调用[doDocument](#dodocument)，会触发doLine回调。

```cpp
void doFile(string fileName);
```

参数 | 解释
---- | -----
fileName | 文件名

---

## doLine
解析每行的回调函数  
默认无行为，用于子类重载用。  
当每解析到一个新行时，此函数被调用。  
回调格式：doLine(array arr, integer lineNo)  
参数解释：  
  arr是该行解析之后生成的数组  
  lineNo是该行的行号（从0开始）  

```cpp
void doLine();
```

---

## fromDocument
解析一个csv文件

```cpp
array fromDocument(string fileName);
```

参数 | 解释
---- | -----
fileName | 文件名

### 返回
解析的结果

---

## fromFile
解析一个csv内容的字符串

```cpp
array fromFile(string csvString);
```

参数 | 解释
---- | -----
csvString | 字符串

### 返回
解析的结果