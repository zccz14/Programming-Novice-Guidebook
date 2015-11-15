# 扫描字符串的方法
当我们得到一个字符串之后，通常要对它进行一系列的操作，如读、写等。  
那么势必要对字符串进行**遍历**操作。

```C
//假设已经存在一个已被赋值的字符串S
int len = 0;
for(len = 0; S[len]; len++);  
//当这个循环结束的时候变量len的值就是字符串S的长度。
```

这就是一个典型的字符串遍历。

```C
//假设已有字符串S
for(int i = 0; S[i]; i++){
    //Todo something here
}
```
这里的i就代表了当前遍历到的字符串位置(索引)

> 
将循环变量写在for的内部是C99或者是C11的标准所支持的。  
如果你的编译器提示for(int i = 0; S[i]; i++)有错误  
`error: 'for' loop initial declarations are only allowed in C99 or C11 mode`  


请使用`std=c99`的[编译参数](what-is-compile-arguments.md) || 使用C++编译器进行编译 || 将代码改写为


```C
int i;
for(i = 0; S[i]; i++){
    //Todo something here
}
```

> 
使用C++编译器编译C语言的代码是毫无压力的。

字符串的结尾是'\\0'，其AscII码为0，在C语言中非零为真，零为假，
于是S[i]的真假性直接等同于**是否达到字符串的末尾**  
就是说，上面的代码直接等同于  

```C
for(int i = 0; S[i] != '\0'; i++){
    //Todo
}
```

> 
除此朴素的方法以外，还有一个使用[sscanf](what-is-sscanf.md)函数的方法

## 经典应用
+ [如何将字符串反转？](how-to-inverse-string.md)
+ [如何将字符串转化为数字？](how-to-get-number-from-string.md)