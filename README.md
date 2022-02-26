# Paddle飞桨领航团创造营第二期成果展示!

## 一、项目背景介绍

随着AI领域的发展，各种深度学习算法被应用到人们日常生活中。其中，无人驾驶领域受到人们诸多关注，百度AI在此方向也有研究。


<img style="display: block; margin: 0 auto;" src="https://ai-studio-static-online.cdn.bcebos.com/426b928b2a1444f6b17590b8534e6791f17403dc7f0f444ebc247c4c747fd655" width = "50%" height = "50%" />

本项目研究了交通标志的检测识别，获得道路标志的具体含义，控制汽车遵守交通规则。通过视觉任务的实现帮助智能算法更好地应用于交通驾驶领域。





## 二、数据介绍
[链接](https://aistudio.baidu.com/aistudio/datasetdetail/107275)

### 1. 数据集来源
中国交通标志识别数据库。里加数据科学俱乐部成员已经探索了它，以便对卷积神经网络进行一些培训。
### 2. 数据集介绍
数据集由 58 个类别的 5998 张交通标志图像组成。每个图像都是单个交通标志的放大视图。注释提供图像属性（文件名、宽度、高度）以及图像和类别中的交通标志坐标（例如，限速 5 公里/小时）
### 3. 标签注释
annotations.csv
- file_name：包含交通标志的图像的文件名
- width：图片宽度
- height：图片高度
- x1：边界矩形左上角X坐标
- y1：边界矩形左上角Y坐标
- x2：边界矩形右下角X坐标
- y2：边界矩形右下角Y坐标
- category：交通标志类别

## 三、模型介绍
VGG是由Simonyan 和Zisserman在文献[《Very Deep Convolutional Networks for Large Scale Image Recognition》](https://arxiv.org/abs/1409.1556)中提出卷积神经网络模型，其名称来源于作者所在的牛津大学视觉几何组(Visual Geometry Group)的缩写。

该模型参加2014年的 ImageNet图像分类与定位挑战赛，取得了优异成绩：在分类任务上排名第二，在定位任务上排名第一。

### 1. VGG网络结构
VGG中根据卷积核大小和卷积层数目的不同，可分为A，A-LRN,B,C,D,E共6个配置(ConvNet Configuration)，其中以D,E两种配置较为常用，分别称为VGG16和VGG19，本项目采用的是VGG16。
![](https://ai-studio-static-online.cdn.bcebos.com/5d7e1d409d3d4cfba2216b1ecc81835a7d32851c05064f22951ba78db6ed7625)




### 2. VGG16详解
VGG16共包含：

13个卷积层（Convolutional Layer），分别用conv3-XXX表示3个全连接层（Fully connected Layer）,分别用FC-XXXX表示5个池化层（Pool layer）,分别用maxpool表示。其中，卷积层和全连接层具有权重系数，因此也被称为权重层，总数目为13+3=16，这即是VGG16中16的来源。(池化层不涉及权重，因此不属于权重层，不被计数)。

![](https://ai-studio-static-online.cdn.bcebos.com/dba19c20c276453abbadb096c97f3434530e00caf321490bae009065b6bd339b)


**Stage 1**
* 卷积层Conv_1_1
* 卷积层Conv_1_2
* 池化层 max_pool_1

**Stage 2**
* 卷积层Conv_2_1
* 卷积层Conv_2_2
* 池化层 max_pool_2

**Stage 3**
* 卷积层Conv_3_1
* 卷积层Conv_3_2
* 卷积层Conv_3_3
* 池化层 max_pool_3

**Stage 4**
* 卷积层Conv_4_1
* 卷积层Conv_4_2
* 卷积层Conv_4_3
* 池化层 max_pool_4

**Stage 5**
* 卷积层Conv_5_1
* 卷积层Conv_5_2
* 卷积层Conv_5_3
* 池化层 max_pool_5

**FC Layers**
* 3 层全连接，最后接 softmax 分类



## 四、模型训练
### 1. 参数设置


| name      | value       |
| ----------- | -----------   |
| lr_schedule   | 0.001     |
| optimize     | Adam、SGD   |
| epoch       | 10       |
| batch_size   | 100       |
| Loss function | CrossEntropy |

### 2. 训练结果




## 五、模型评估
该部分主要是对训练好的模型进行评估，可以是用验证集进行评估，或者是直接预测结果。评估结果和预测结果尽量展示出来，增加吸引力。

## 六、总结与升华
本来是计划使用YOLO模型完成目标检测任务，由于是初次接触，在几天时间内学习并搭建YOLO模型有些困难。但是还是积极做了一些尝试，在接下来的时间里会继续改进，感兴趣的话请[**点此**](https://aistudio.baidu.com/aistudio/projectdetail/3511327)查看并关注，后续还会更新。

在本项目中利用了卷积神经网络VGG16模型完成了训练、测试，效果尚可。不足之处是数据集的数量有些少，应当做一些数据增强的操作，扩大数据集，提升训练效果，防止对小数据集过拟合。

## 七、个人总结
通过参加本次训练营，学习并上手paddle框架，第一次在AI studio完成了数据集处理、模型搭建、模型训练及测试完整的过程，同时也是第一次使用云端服务器及算力资源。十分感谢百度AI studio提供的平台，今后还将继续学习paddle框架，并尝试部署在嵌入式算力卡上，还会向身边同学推荐paddle框架，一起学习。

### 个人主页


| site     | url |
| ---------- | -------- |
| AI Studio  | [传送](https://aistudio.baidu.com/aistudio/usercenter)|
| Github    | [传送](https://github.com/nanamma/first-try-of-paddlepaddle)|
| Gitee     | [传送](https://gitee.com/nanamma/first-try-of-paddlepaddle/settings#index)|



## 提交链接
| sourse     | url |
| --------    | -------- | 
| aistudio | [传送](https://aistudio.baidu.com/aistudio/projectdetail/3520067) | 
| github   | [传送](https://github.com/nanamma/first-try-of-paddlepaddle) |
| gitee    | [传送](https://gitee.com/nanamma/first-try-of-paddlepaddle/settings#index)|

