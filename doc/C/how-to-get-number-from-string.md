# 如何将一个字符串转化为数字？

以转化为int为例
```C
int parseInt(char* Str){
	int res = 0; //初始化返回值
	int cur = 0; //初始化数组扫描光标
	/*
		当Str[cur](即当前扫描的字符)在合法范围时('0'~'9'之间)
		Str[cur]-'0'这样一个运算将'0'~'9'这样的字符转化为int类型的0~9
		注意在运算完了再将光标向后移一位
		10 * res 这样是因为十进制进位问题
	*/
	while(Str[cur]>='0' && Str[cur]<='9')
		res = 10 * res + Str[cur++] - '0';
	/*
		在循环结束以后一定有 Str[cur] 不在'0'~'9'这个范围里(非法)
		显然这个时候跳出循环并返回res就可以了
	*/
	return res;
}
```
使用样例
`printf("%d",parseInt("123"));` => `123`

`printf("%d",parseInt("123.45"));` => `123`



无注释版
```C
int parseInt(char* Str){
	int res = 0, cur = 0;
	while(Str[cur] >= '0' && Str[cur] <= '9')
		res = 10 * res + Str[cur++] - '0';
	return res;
}
```

如果要变成浮点数版本的，就要考虑各种各样的问题了
比如小数点，又或者是科学计数法(如1.1e2)
整个处理的逻辑都会变得复杂
```C
//require : double pow(double, double) in <math.h>
//require : int parseInt(char*)
double parseDouble(char* Str){
	int curOfPoint = -1, curOfExp = -1, cur =0;
	int Int = parseInt(Str), Exp =0;
	double Dec = 0;
	while(Str[cur]){
		if(Str[cur] >= '0' && Str[cur] <='9')
			cur++;
		else if(Str[cur] == '.' && curOfPoint == -1)
			curOfPoint = cur++;
		else if(Str[cur] == 'e' && curOfExp == -1)
			curOfExp = cur++;
		else break;
	}
	if(curOfPoint != -1){
		Dec = parseInt(Str + curOfPoint + 1);
		while(Dec > 1) Dec /= 10;
	}
	if(curOfExp != -1)
		Exp = parseInt(Str + curOfExp + 1);
	return (Int + Dec) * pow(10, Exp);
}
```
> 
字符串切割算法(split)  
基本思路就是查找并记录Double字符串的分割点  
即"."(小数) 与 "e"(指数)   
然后调用之前写过的parseInt  
在三个位置扫描字符串的整数，得到X,Y,Z  
即`X.YeZ`  
>> 其中 X 为 整数部分; Y 为 小数部分; Z 为指数部分
> 
将Y处理成0.Y即可(如Y == 123 则处理成 Y == 0.123)
然后最后的结果显然应该是
>> ans = (X+Y)×10^Z (**in math**)

这个代码的细节部分还可以再感受一下，如它对**异常输入**的处理
