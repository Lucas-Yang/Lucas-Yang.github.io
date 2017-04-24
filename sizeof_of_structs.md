C++中结构体占字节数（sizeof）
-----------
首先看一段代码
```c
  struct X{
    char a;
    int b;
    double c;
    }SRT;


int main()
{
    cout << sizeof(SRT) << endl;
    cout << sizeof(SRT.a) << endl;
    cout << sizeof(SRT.b) << endl;
    cout << sizeof(SRT.c) << endl;
    return 1;
  }

```
输出为 sizeof(SRT)=16 sizeof(SRT.a)=1 sizeof(SRT.b)=4 sizeof(SRT.c)=8 
出现这种情况的原因是内存字节对齐导致

当然 这里记住两个原则就可以将这个问题搞清楚
#### 第一 结构体中的元素是按照顺序一个个放入内存，而且每个元素放入的首地址（相对地址）一定是自己本身长度的整数倍 如上代码中a占了0～3 b占4～7 c占8～15 0 4 8 分别是 char int double 的整数倍位置

我们再看一段代码
```c
 struct X{
    char a;
    double b;
    int c;
    }SRT;


int main()
{
    cout << sizeof(SRT) << endl;
    cout << sizeof(SRT.a) << endl;
    cout << sizeof(SRT.b) << endl;
    cout << sizeof(SRT.c) << endl;
    return 1;
  }


```
将第一处的代码的double 与int 换了一个位置后 得到sizeof(SRT)=24 char 放在了0～7 double在8～15
int在16～19 所以这里涉及到第二个原则
####  第二 占空间为最大数据占空间的整数倍 所以在内存20～23为对齐补全的。
如果有错误 欢迎指正 比心 （ylucas923@gmail.com）
###### [返回主页](https://github.com/Lucas-Yang/Lucas-Yang.github.io/blob/master/README.md)








