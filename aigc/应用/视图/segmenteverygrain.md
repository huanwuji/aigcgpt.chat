# segmenteverygrain

基于sam的颗粒图像分割实例模型.
segmenteverygrain'是一个Python包，旨在检测图像中的颗粒(或类似颗粒的对象)。
目标是开发一个ML模型，在检测照片中的比较多的颗粒做得相当好，这样它就可以用于确定颗粒大小和颗粒形状，
这是地貌学和沉积地质学中的一个常见任务。“分离颗粒”依赖于分段任何模型(SAM)。
由Meta开发，用于获得高质量的颗粒轮廓。
但是，SAM需要对检测到的每个对象进行提示，并且当在“everything”模式下使用时。
它往往是缓慢的，并导致许多重叠蒙版和非颗粒(背景)对象。
为了解决这些问题，“segmenteverygrain”依赖于Unet-style, patch-based的卷积神经网络来创建第一次分割，
然后将其用作基于sam的分割的一组提示。
这种方法会丢失一些颗粒，但创建的分割往往是高质量的。

'segmenteverygrain'还包括一组功能，使清理分割结果成为可能:删除和合并对象通过点击他们，并添加未自动分割的颗粒。
QC-d蒙版可以保存并添加到颗粒图像的数据集(参见“images”文件夹)。
这些图像可以用来改进Unet模型。数据集中使用的许多图像都来自sedinet项目。

github: [https://github.com/zsylvester/segmenteverygrain](https://github.com/zsylvester/segmenteverygrain)