### 1、开发环境
* 1 android studio 
* 2一部真机
### 2、问题描述
 在开发时候，需要选一张好看的背景图片，但是放在drawable文件夹下面 在layout里面设置background时候，下载到真机上面背景图片无法显示，有的手机又可以显示。
### 3、问题原因
  没有将图片放在相应的分辨率background文件夹下。不同分辨率的图片放在不同的文件下 。比如drawable-hdpi drawable-xhdpi等文件夹对应放不同的分辨率的图片文件。
### 4、注意事项
   一般打开android studio我们进入的模式是android 
   如下 左上角
   ![这里写图片描述](http://img.blog.csdn.net/20170723122018883?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
这时候我们是看不到所谓的drawable下面的子文件夹的，所以我们需要自己去创建文件夹。具体方法可以参见这篇blog[连接](http://blog.csdn.net/gulingfengze/article/details/53437139)

欢迎指正
  
