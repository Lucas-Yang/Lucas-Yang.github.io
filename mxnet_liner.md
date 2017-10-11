深度学习-使用mxnet做线性回归问题
------------
既然已经把mxnet装好了， 那我们就可以开始机器学习之旅，至于mxnet的API和相关函数请参考官方文档[mxnet文档](http://mxnet.io/api/python/module.html#the-basemodule-class)。Andrew Ng在他的machine learning课堂上提出的一个问题就是：我们有某个地区住房面积和相应房价的数据集合，对于这样的给定的数据， 我们的目的是要利用已有的信息，来对房价建立预测模型。即对于给定的房屋信息(房屋面积)预测其房价。我们在这里就模拟做这样一个事情。
#### 1、数据准备
X_data当作横坐标，y_data 纵坐标。那我们就假装我们有100组数据。
```c
# 定义输入数据
X_data = np.linspace(-1, 1, 100)
noise = np.random.normal(0, 0.5, 100)
y_data = 5 * X_data + noise
 
# Plot 显示
fig = plt.figure()
ax = fig.add_subplot(1, 1, 1)
ax.scatter(X_data, y_data)
```
我们会看到数据的分布图如下：

![这里写图片描述](http://img.blog.csdn.net/20170718114749931?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
#### 2、定义网络与模型
```c
# 定义mxnet变量
X = mx.symbol.Variable('data')
Y = mx.symbol.Variable('softmax_label')
 
# 定义网络
Y_ = mx.symbol.FullyConnected(data=X, num_hidden=1, name='pre')
loss = mx.symbol.LinearRegressionOutput(data=Y_, label=Y, name='loss')
 
# 定义模型
model = mx.model.FeedForward(
            ctx=mx.cpu(),
            symbol=loss,
            num_epoch=100,
            learning_rate=0.001,
            numpy_batch_size=1
        )
 
```
#### 3、训练模型
```c
# 训练模型
model.fit(X=X_data, y=y_data)
 
```
#### 4、用训练好的模型进行预测
  我们选用我们训练时候的横坐标数据
```c
# 预测
prediction = model.predict(X_data)
print(prediction)
lines = ax.plot(X_data, prediction, 'r-', lw=5)
plt.show()
```
可以得到如下的结果图：
![这里写图片描述](http://img.blog.csdn.net/20170718115503355?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTHVjYXM2NjY2Ng==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

完成！
