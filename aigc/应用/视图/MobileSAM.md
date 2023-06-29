# MobileSAM

更快的Segment Anything (MobileSAM)项目，让SAM更快

MobileSAM的性能与原始SAM相当(至少在视觉上)，并且除了图像编码器上的变化外，与原始SAM保持完全相同的管道。
具体来说，我们用更小的Tiny-ViT (5M)取代了原来的重量级ViT-H编码器(632M)。
在单个GPU上，MobileSAM每张图像运行大约12ms:在图像编码器上运行8ms，在掩码解码器上运行4ms。

github: [https://github.com/ChaoningZhang/MobileSAM](https://github.com/ChaoningZhang/MobileSAM)