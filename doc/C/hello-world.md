# Hello World, Hello C


``` C 
#include <stdio.h>
int main(){
  //Todo something here, just like this:
  printf("Hello World!\n");
  return 0;
}
```

这是一个基本的框架

## 头文件
`#include <stdio.h>` 这是引用头文件 `stdio.h`(Standard I/O,标准输入输出) ，里面包含了很多常用的输入输出相关的函数，
比如上面用到的printf函数(print function, 打印函数)就是在这个头文件中实现的。
在C语言中，涉及输入输出的**大多数**时候都是要使用这个头文件的。
另一方面，程序是一定有输出的(这里的输出是指广义的输出，内涵是"改变环境")。
通常输出为打印到屏幕或者输出到文件，都要用到这个 stdio.h 的头文件，因此我将其归入基本框架。

> 
`#include` 是一个预编译指令：**文本包含**，更多的解释去看[预编译指令](what-is-precompilation.md)

## int main() 与 return 0
关于main函数的声明方式另外还有:
+ void main()
+ main()
至少两种
(让我们先忽略[带参的main函数调用](how-to-use-arguments-in-main.md))

有什么区别呢？
int 是 main函数的返回值类型。

> 
函数的返回值由其调用者接收


main函数也是一个函数，那么谁去调用这个main函数呢？
简单地说就是系统，比如windows，在程序执行完毕以后，main函数返回windows一个返回值。
windows系统根据这个返回值来确定程序的运行情况。
return 0被默认地认为是表示**程序正常退出**

> 
main的返回值通常称为[错误代码 Error Code](what-is-error-code.md)


尽管 `return 0;` 有时候不写程序也会默认返回0，但是还是养成良好的习惯比较好。
因为这里所谓的默认是取决于编译器的。

>
`void main()` 这种写法是非标准的！
其出现属于历史遗留问题。
在新的标准中已经被废除。
因此强烈推荐不要使用。


> 
`main()`这种写法等同于`int main()`。 
这是因为编译器默认全局定义的变量(函数)默认为int类型。
