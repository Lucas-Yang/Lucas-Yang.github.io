深度学习--windows 下安装mxnet
---------------------------------
前言：关于什么是mxnet，为什么选用mxnet框架这里就不一一介绍了，有兴趣的同学可以参考[mxnet实战心得](http://blog.csdn.net/dcxhun3/article/details/53897961) 和 [为什么强大的mxnet一直火不起来](http://www.sohu.com/a/119098283_465975)

## 安装过程
#### 1、安装cuda, cudnn
  具体的安装步骤以及方法，可以参考这篇blog[相关安装方式](http://www.cnblogs.com/hzm12/p/6422701.html), 当然网上的教程蛮多的，也可以参考

#### 2、安装anaconda
   根据自己电脑的版本 型号选择相应的下载，点击这里下载[下载](https://www.continuum.io/downloads#windows) 
   安装过程很简单， 如果事先安装有python，则注意选择相应的anaconda版本进行下载，如果没有安装python，则在安装anaconda的时候要把是否安装python那里打勾选择安装。
#### 3、安装相应的包
  既然anaconda已经安装好了 那我们就开始安装我们开发时候所需要的第三方依赖包，编辑器等等
  首先打开我们的软件，把快捷方式放在桌面上吧，在这里找到：C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Anaconda
  ![这里写图片描述](http://img.blog.csdn.net/20170703224452049?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  打开Navigator
  ![这里写图片描述](http://img.blog.csdn.net/20170703224654509?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  
  既然我们我们可能以后也会使用tensorflow caffe等等进行开发啊，所以在root目录下面直接装的话会很混乱啊，那我们就create Environments。点击左边栏目的Environments 然后点下面的create 我们就create我们的mxnet 的envs吧 就命名mxnet吧
  ![这里写图片描述](http://img.blog.csdn.net/20170703225438194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  好啦，我们就可以在mxnet下面安装各种包啦当然安装的方式我们可以直接在上面图片的左边选择这样的图形化界面安装我们所需要的包，上上一张图片里面有我们可以看到一系列的东西，那我们选择几个install吧，spyder是一个很不错的编译器，用来写python。通过这两种图形化界面安装所需包的方式好像只可以安装有conda命令的包，很多东西无法安装，比如mxnet就无法找到。所以我们用另外一种安装方式，终端命令方式，点击上一张图片我们create的envs 就是那个横着的三角形，我们就可以看到，选择打开终端，那样我们就可以用命令行方式做事情了
  
  在安装前，我们最好将安装源修改一下，改成国内的会快一些。 输入如下两条命令。

    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    conda config --set show_channel_urls yes 
我选的清华的源，当然你也可以选择交大的源啊，蛤蛤蛤
 
 好了感觉可以安装其他的东西了。
 （1）安装opencv

    conda install opencv
 （2）安装openBlas 方法相同
  （3）根据你的需要，其他包都可以采用相应的方法安装
  （4）最重要的东西来了，安装mxnet 这里直接用conda install mxnet是不可以的，所以我们选择pip方式来安装吧，根据网上网上很多的教程，都是通过下载mxnet的预编译版本，自己编译后安装，可以去看一看[mxnet预编译版本下载](https://github.com/dmlc/mxnet/releases)，感觉挺麻烦的，有没有什么办法可以直接一个命令就安装好的啊？是有的，我在网上(mxnet的whl文件)，可以下载whl文件通过pip方式安装，但是这样安装后会有一些问题 就会在import mxnet时候会报错，找不到dll文件。

找到一种方法 终端输入如下命令

    pip install mxnet-cu80
就可以安装好，我的cuda版本是这个cuda-8.0 具体的安装要看你的版本选择相应的mxnet安装。 大功告成，我们写一段py代码测试下
![这里写图片描述](http://img.blog.csdn.net/20170703235246795?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast) 
 没有报错。

如果有问题欢迎指正探讨，比丁丁

   
             
  
    
