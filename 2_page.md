char *a 与char a[]所占空间解析
-------------
###### 在分析之前，我们先熟悉下在16位、32位、64位下指针类型 与char类型所占空间
         16位        32位       64位
    char 1           1          1
    指针  2           4          8（我们在有的编译环境下面sizeof出来是4 是因为编译器为了编译32位机器代码而做的妥协，按道理上是8位）

ok,让我们开始测试并分析如下各种情况
######如下
假设我们的程序（64位机器）如下：


```c
void countsize(char a[])  
{  
  
    cout<< sizeof a ;  
  
} 
int main(){
    char a[]="hello";
    char *b = "hello";
    char c[10]="hello";
}

```
siezeof(a)==6, sizeof(b)==4, sizeof(*b)==1, sizeof(c)=10  
因为a的结尾还有一个字符串结束符'\0'所以一共有6个字节
同时 b是一个指针 无论如何都是4， 但是*可以理解为一个地址类型，b才存放着另外一个变量的地址所以输出为1
，c已经指定了大小 则输出为10.

###### 如果有错误欢迎指正 感谢 比心

特别有意思的是 countsiz(a)==4 countsize(b)==4 countsize(c)==4 其实coutsize(char a[])与coutsize(char *a)是一样的，它是不会为你记录数组的大小，而是传入了地址参数。

#### [返回主页](http://Lucas-Yang.github.io)
