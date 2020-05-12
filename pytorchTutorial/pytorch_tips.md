## unsqeeze / squeeze

unsqueeze在指定的维度添加维度1， 并且返回一个新的tensor。具体使用是在进行tensor之间的操作时保持维度一致。

例如，我们首先新建一个只有4个元素的**一维tensor**：

```
x = torch.tensor([1, 2, 3, 4])
print(x.shape)

结果: 
torch.Size([4])
tensor([[1, 2, 3, 4]])
```

在dim=0对x进行unsqueeze:

```
y = x.unsqueeze(0)
print(y)
print(y.shape)

结果:
tensor([[1, 2, 3, 4]]) # 类比于list of list， 纵向扩展了一个维度
torch.Size([1, 4])
```
在dim=1对x进行unsqueeze:

```
z = x.unsqueeze(1)
print(z)
print(z.shape)

结果：
tensor([[1],
        [2],
        [3],
        [4]])
torch.Size([4, 1]) 
```

而squeeze则把所有1的维度去掉。y.squeeze()和z.squeeze()会和x相同。

以上的运用可以参考gather。


## gather

经过softmax层后，所有label的分数可以看成一个分布，有时候我们需要得到真实的label所对应的分数，然后计算loss。比如在bilstm_crf的， 我们想要计算emission score。

如以下，假设一个batch只有一个seq_len=4的序列，且序列中的每个词对应的tag有3种。

```
emissions = torch.tensor([[0.1, 0.2, 0.7], 
		  [0.4, 0.5, 0.1], 
	   	  [0.3, 0.4, 0.3],
		  [0.5, 0.4, 0.1]])
								
# 四个词对应的真实tag_id分别为[0, 1, 2, 2]	
tags = torch.tensor([0, 1, 2, 2]).unsqueeze(1)

# 在dim=1进行gather，意思是tags中的数字作为dim=1, 
# dim=0处遵守tags数字本来所在的维度
e_scores = emissions.gather(1, tags).squeeze()
```
也就是说, tags被我们扩展为：

```
[[0, 0],  # 0.1
 [1, 1],  # 0.5
 [2, 2],  # 0.3
 [3, 2]]  # 0.1
```
然后当做mask在每一行选择元素。

同理，可以从dim=0选择元素：

```
emissions = torch.tensor([[0.1, 0.2, 0.7],
			  [0.4, 0.5, 0.1],
		   	  [0.3, 0.4, 0.3],
			  [0.5, 0.4, 0.1]])

tags = torch.tensor([3, 2, 0]).view(1, 3)
e_scores = emissions.gather(0, tags)
```
输入为：

```
[0.5, ]
```