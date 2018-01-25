make faces in videos hard to recognize with the help of tensorflow
---

# 安装opencv
参考
python3 安装 opencv3 （win10,64bit）  
<https://www.cnblogs.com/combfish/p/5639424.html>  

# pipeline
## 1 视频预处理
目前查到的需要逐帧提取出图像，图像的尺寸可能需要用插值的办法放缩一下，得到一系列图像。  
放缩的比例要记录，后面用来还原视频

## 2 人脸检测
定位所有图像中所有人脸的的位置(猫脸和汪脸也可能混进来)  
一个人可能长时间处在画面中，导致重复脸过多，下面的聚类时间可能很长。  
可能可以使用跟踪算法，只记录轨迹和和区域  
跟踪算法:  
- KCF 
- dlib的相关滤波器(dlib不能解决遮挡恢复的问题)  
太长时间没办法, 可以设定30帧以内的可以恢复，通过特征的马氏距离比对，可以恢复
- kalman滤波

## 3 归类(识别)
对人脸分类  
使用不依赖于类别数量的聚类算法，比如 chinese whispers  
参考  
<facenet chinese whispers(face cluster)>  
http://blog.csdn.net/liyuan123zhouhui/article/details/70312716  
https://github.com/zhly0/facenet-face-cluster-chinese-whispers-  

# Reference
基于mtcnn和facenet的实时人脸检测与识别系统开发  
<https://zhuanlan.zhihu.com/p/25025596>  

Tensorflow Object Detection API  
<https://github.com/tensorflow/models/tree/master/research/object_detection>  
TensorFlow-Slim image classification model library  
<https://github.com/tensorflow/models/tree/master/research/slim>  

目标检测 - Tensorflow Object Detection API  
<http://blog.csdn.net/linolzhang/article/details/73730463>  
目标干脆面君：动动手，用TensorFlow API训练出自己的目标检测模型  
<https://36kr.com/p/5096924.html>  

亲测好用！Google发布了一个新的Tensorflow物体识别API  
<https://36kr.com/p/5090812.html?from=related>  
<https://towardsdatascience.com/is-google-tensorflow-object-detection-api-the-easiest-way-to-implement-image-recognition-a8bd1f500ea0>  

<https://github.com/priya-dwivedi/Deep-Learning/blob/master/Object_Detection_Tensorflow_API.ipynb>  

如何盯住梅西：TensorFlow目标检测实战  
<https://www.jiqizhixin.com/articles/2017-10-13-2>  