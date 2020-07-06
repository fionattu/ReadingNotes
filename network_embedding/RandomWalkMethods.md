## 基于RandomWalk的网络表示学习

针对network embedding两篇经典论文DeepWalk和Node2Vec的学习笔记。Reference：https://zhuanlan.zhihu.com/p/45167021

### 知识预备

skipgram：https://zhuanlan.zhihu.com/p/27234078

公式推导

* word2vec skipgram/CBOW  model：区别https://zhuanlan.zhihu.com/p/37477611
	* skipgram: 用中心词预测周围词，训练时间长，效果好
	* CBOW:用周围词预测中心词，效果稍差但效率高
* softmax
* negative sample负采样
