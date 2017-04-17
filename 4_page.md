typedef与define的区别
----------
     #define是C中定义的语法，typedef是C++中定义的语法，二者在C++中可以通用，但#define成了预编译指令，typedef当成语句处理。Typedef和define都可以用来给对象取一个别名，但是两者却有着很大不同。
##### 执行时间不同
    typedef 在编译阶段有效，同时也有类型检查的功能。
    define 则是宏定义，发生在预处理阶段，相当于就是简单的字符串的替换，不进行任何检查
##### 功能不同
    Typedef 用来定义类型的别名，这些类型不只包含内部类型（int，char等），还包括自定义类型（如struct），可以起到使类型易于记忆的功能。 
    #define不只是可以为类型取别名，还可以定义常量、变量、编译开关等。
##### 作用域不同
    #define没有作用域的限制，只要是之前预定义过的宏，在以后的程序中都可以使用。而typedef有自己的作用域。
##### 对指针的操作不同
```c
Typedef int * pint；  
#define PINT int *  
Const pint p；//p不可更改，p指向的内容可以更改，相当于 int * const p;  
Const PINT p；//p可以更改，p指向的内容不能更改，相当于 const int *p；或 int const *p；  
pint s1, s2; //s1和s2都是int型指针  
PINT s3, s4; //相当于int * s3，s4；只有一个是指针。 
```
[返回主页](http://Lucas-Yang.github.io)
