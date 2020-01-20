# PyTorch学习笔记
##基本介绍
**开源深度学习框架，由facebook开发维护**。近年来PyTorch的arkiv论文使用量已经开始超过tensorflow，github上的fork，star等数量也与tensorflow齐平，可以说是非常强劲的后起之秀了。下载的时候可以在官方网站选择相应的操作系统，python，gpu和pytorch的相应版本，然后进行安装，此处非常推荐使用anaconda来安装和管理lib。如果有gpu，需要先下载cuda(nvidia英伟达开发的基于GPU的通用并行架构)以及cuDNN(用于深度网络的GPU加速库，插入式设计)。没有gpu就选择cpu。

## 动态图
pytorch为动态图，意思是边建立**计算图**边进行运算。Tensorflow是静态图，计算图网络搭建好了，再进行tensor传播。