# 如何将一个数字转化为字符串？

Hint : sprintf函数  
(String-Print-Function: 字符串打印函数)

普通的printf函数是对console(控制台)打印

而sprintf则是打印到字符串里呢

举个栗子o(- -)/
```C
char S[1000];
int A = 21312441;
double B = 123.45;
sprintf(S,"%d,%lf",A,B);
puts(S);
```

这样输出
```
21312441,123.450000
```

啊是不是很神奇

> 
### 函数原型
`int sprintf(char* S,const char* format, ...);`
> 
### 参数
+ char* S : 载体字符串(就相当于打印纸)
+ const char* format : 打印格式(通常带有各种占位符)
+ ... : 缺省的占位符
> 
可以看到这就是一个挖坑、填坑的过程。
### 返回值
+ int : 一共打印了多少个字符。
