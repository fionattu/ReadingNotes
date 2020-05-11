## gather

经过softmax层后，所有label的分数可以看成一个分布，有时候我们需要得到真实的label所对应的分数，然后计算loss。比如在bilstm_crf的， 我们想要计算emission score。

如以下，假设一个batch只有一个seq_len=4的序列，且序列中的每个词对应的tag有3种。

```
emissions = torch.tensor([[0.1, 0.2, 0.7], 
						  [0.4, 0.5, 0.1], 
					   	  [0.3, 0.4, 0.3],
						  [0.5, 0.4, 0.1]])
								
# 四个词对应的真实tag_id分别为[0,1,2,2]	
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