C++中几个关键字的解析
--------
### 一、const（定义不变量）
```c
class Test{
  private:
    int a;
  public:
    void testFunction(int b)const{
        a=b;     //错误，在const成员函数中，不能修改任何类成员变量
        help(b)  //报错，const成员函数不能调用非onst成员函数，因为非const成员函数可以会修改成员变量
    }
    
    void help(int b){
       a=b;
    }
};


void testConst(const int _x) {
     _x=5;　　　///编译出错
}
const int* testok(){
 return 1;
 }
 
int main(){
    int a1=3;
    const int a2=a1; //修饰成员变量，a2不可改变
    int * a3 = &a1;
    const int * a4 = &a1; 
    int * const a5 = &a1; 
    int const * const a6 = &a1;
    const int * const a7 = &a1;
    
     const int *a = testok();
     ///int *b = mallocA();  ///编译错误 返回是什么就应该用什么去接收
   
    return 1;
}
```
###### 1：修饰指针成员变量
    (1)只有一个const，如果const位于*左侧，表示指针所指数据是常量，不能通过解引用修改该数据；指针本身是变量，可以指向其他的内存单元。
    (2)只有一个const，如果const位于*右侧，表示指针本身是常量，不能指向其他内存地址；指针所指的数据可以通过解引用修改。
    (3)两个const，*左右各一个，表示指针和指针所指数据都不能修改。
    
###### 2：const修饰函数参数
    传递过来的参数在函数内不可以改变，与上面修饰变量时的性质一样。
    
###### 3：修饰成员函数
    (1)const修饰的成员函数不能修改任何的成员变量(mutable修饰的变量除外)
    (2)const成员函数不能调用非onst成员函数，因为非const成员函数可以会修改成员变
    
###### 4:修饰函数返回值
    如果返回const data,non-const pointer，返回值也必须赋给const data,non-const pointer。因为指针指向的数据是常量不能修改。

### 二、static（静态 面向对象+面向过程）
#### 1、面向过程中的static
```c
static void test();//声明静态函数
static int a; //定义静态全局变量
void main()
{
 　　a=20;
 　　cout<<a<<endl;
 　　test();
}

void test()//定义静态函数
{
 　　static int a=10; //定义静态局部变量
 　　cout<<a<<endl;
}
```
###### 1.1静态全局变量
     该变量在全局数据区分配内存；
     未经初始化的静态全局变量会被程序自动初始化为0；
     静态全局变量在声明它的整个文件都是可见的，而在文件之外是不可见的；
     静态全局变量不能被其它文件所用；
     其它文件中可以定义相同名字的变量，不会发生冲突
     
###### 1.2静态局部变量
     该变量在全局数据区分配内存；
     静态局部变量在程序执行到该对象的声明处时被首次初始化，即以后的函数调用不再进行初始化；  
     静态局部变量一般在声明处初始化，如果没有显式初始化，会被程序自动初始化为0；
     它始终驻留在全局数据区，直到程序运行结束。但其作用域为局部作用域，当定义它的函数或语句块结束时，其作用域随之结束； 
     
###### 1.3静态函数
    静态函数不能被其它文件所用；
    其它文件中可以定义相同名字的函数，不会发生冲突； 
    
#### 2、面向对象的static
```c
class Mytest
{
public:
 　　Mytest(int a,int b,int c);
 　　static void GetSum();
private:
 　　int a,b,c;
 　　static int Sum;//声明静态数据成员
};
int Mytest::Sum=0;//定义并初始化静态数据成员
void Mytest::GetSum() //静态成员函数的实现
{
　　// cout<<a<<endl; //错误代码，a是非静态数据成员
 　　cout<<"Sum="<<Sum<<endl;
}
```
###### 2.1静态数据成员
    在类内数据成员的声明前加上关键字static，该数据成员就是类内的静态数据成员
    注意：static 并不占用类的栈空间，sizeof是计算栈空间大小。
    有如下特性：
    (1)静态数据成员存储在全局数据区。静态数据成员定义时要分配空间，所以不能在类声明中定义。
    (2)对于非静态数据成员，每个类对象都有自己的拷贝。而静态数据成员被当作是类的成员。无论这个类的对象被定义了多少个，静态数据成员在程序中也只有一份拷贝，由该类型的所有对象共享访问。也就是说，静态数据成员是该类的所有对象所共有的。对该类的多个对象来说，静态数据成员只分配一次内存，供所有对象共用。所以，静态数据成员的值对每个对象都是一样的，它的值可以更新；
    (3)静态数据成员存储在全局数据区。静态数据成员定义时要分配空间，所以不能在类声明中定义。
    
###### 2.2静态成员函数
    非静态成员函数可以访问静态数据成员
    静态成员之间可以相互访问，包括静态成员函数访问静态数据成员和访问静态成员函数;
    非静态成员函数可以任意地访问静态成员函数和静态数据成员;
    静态成员函数不能访问非静态成员函数和非静态数据成员;

###### 有不正之处欢迎指正，不胜感激 比心（ylucas923@gmail.com）
    
##### [返回主页](http://Lucas-Yang.github.io)

  
