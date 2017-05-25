tcp udp https的认识
-------
##### blog上面看到这样一句话， ip相当于一条高速公路， tcp 与 udp相当于高速路上面的卡车，而http相当于卡车上面装的货物
#### 认识tcp/ip协议族
    虽然名字叫做tcp/ip但是千万不要误解，tcp/ip协议族包含计算机osi结构上面所有层的协议 只不过经常用到
    tcp与ip所以名字叫做tcp/ip 
    当然一般的tcp/ip模型主要分成了四个层次对应于常用的osi五个层次
    osi模型：                                     tcp/ip协议族层次：
    应用层                                        应用层  http ftp       tftp ntp
    传输层                                        传输层  tcp             udp
    网络层                                        网络层          ip
    数据链路层                                    主机到网络层     以太网 ppp
    物理层                                        主机到网络层

则：http等就是协议族中的一个协议  是从Web服务器传输超文本到本地浏览器的传送协议
#### 认识http协议
    建立过程
    1 客户机通过TCP/IP协议建立到服务器的TCP连接
    2 客户端向服务器发送HTTP协议请求包，请求服务器里的资源文档
    3 服务器向客户机发送HTTP协议应答包，如果请求的资源包含有动态语言的内容，那么服务器会调用动态语言的解释引擎负责处理“动态内容”，并将处理得到的数据返回给客户端
    4 客户机与服务器断开。由客户端解释HTML文档，在客户端屏幕上渲染图形结果
    
具体内容理解 参考 [HTTP协议 处理流程](http://www.cnblogs.com/zharma/p/4596102.html)

#### 一些小的总结
    TCP和UDP：传输层协议； 
参考 [tcp与udp的区别](http://blog.csdn.net/dr_neo/article/details/52400544) 感谢博主 比心

    HTTP：应用层协议；

    SOCKET：TCP/IP网络的API。
    ###### 欢迎指正 ylucas923@gamil.com
