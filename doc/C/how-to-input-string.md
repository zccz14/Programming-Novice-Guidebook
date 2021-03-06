# 如何输入字符串？

在C语言中，字符串直接被解释为"字符"——"串"

即字符数组的形式：

```C
#define STR_LENGTH 40
char Str[STR_LENGTH];

```

于是就有人以与数字数组一样的方式去输入它：
```C
for(int i = 0 ; i < STR_LENGTH; i++)
	scanf("%c",&Str[i]);

```
可以是可以的，但是一定要注意

> 
**使用%c这个占位符是相当危险的**  
因为它不会放过任何的输入，包括回车、空格、制表符这些空白字符  
如果要使用它，务必确定输入的格式是经过严格考量的。  

举个栗子(。· ·)ノ
```C
int n;
char S[100];
scanf("%d",&n);
for(int i = 0 ; i < n ;i++)
	scanf("%c",&S[i]);
```
然后我输入一个
```
5
abcde
```
这时候S字符串里面存了什么？  
存了："\nabcd"  
怎么回事？它可是把5后面的换行符也读进去了哟！  

此时正确的输入是`5abcde`  
**Σ( ° △ °|||)︴**——很奇怪吧？

***

**所以**我建议使用`%s`这个占位符来读取字符串
或者干脆使用gets函数吧

举个栗子(。O-O)/
```C
char S[1000];
scanf("%s",S);
```

```C
char S[1000];
gets(S);
```
这两种输入方式还有微妙的不同  
+ gets读取字符串直至接受到换行符或EOF时停止
+ scanf读取字符串直至接受到换行符或EOF或空格或制表符等**空白字符**时停止

所以简单地说gets用于读取一整行，scanf用于读取一个连续字符串。