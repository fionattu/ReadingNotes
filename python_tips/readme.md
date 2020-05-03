介绍python各种高级用法

## print格式限制

### 用花括号来代表变量：

```
a = 'a'
b = 'b'
print("print {} after {}".format(a, b))
```

### 数字格式约束：

[参考链接](https://pyformat.info)。

表示a需要至少4个字符，如果不够用0在前面填充：

```
a = 14
print("print {:04d}".format(a)) # 0014
```

浮点数也可以做限制，下面表示只保留2个浮点数：

```
a = 3.141592653589793
print("print {:.2f}".format(a)) # 3.14
```

结合两者，下面表示a至少需要6个字符(包含小数点)，只保留2个浮点数：

```
a = 3.141592653589793
print("print {:06.2f}".format(a)) # 003.14
```


## list + 负号

**在list索引中看到负数-a，自动变成len(x)-a来解读。**

### list + 负index

表示从list从右往左数，list[-1]表示倒数第一个元素，list[-2]表示倒数第二个，以此类推。可以把list想象成一个双向链表，负index代表从右往左， 正index代表从左往右。


```
x = [1, 2, 3, 4, 5, 6]
print(x[-1]) # 6
```

**所以我们可以用x[-1]来代替x[len(x)-1]，访问最后一个元素**。


### list + 负范围

以下，-1作为end index被解读成len(x)-1，而list的范围用法是前开后闭：

```
x = [1, 2, 3, 4, 5, 6]
print(x[:-1]) # [1, 2, 3, 4, 5]
```
以此类推：

```
x = [1, 2, 3, 4, 5, 6]
print(x[:-2]) # [1, 2, 3, 4]
```


### list + 负slice
第三个元素表示slice(切片)，会有以下效果：

```
x = [1, 2, 3, 4, 5, 6]
print(x[::2]) # [1, 3, 5]
```

如果slice为负数，代表倒序输出：

```
x = [1, 2, 3, 4, 5, 6]
print(x[::-1]) # [6, 5, 4, 3, 2, 1]
```

下面看一种用法的结合，输出为空：

```
x = [1, 2, 3, 4, 5, 6]
print(x[:-1:-1]) # []
```

**注意当slice为负数时，x[:-1:-1]会把start index变成len(x)-1**。所以x[:-1:-1]实质为x[(len(x)-1):(len(x)-1):-1], 结果为空。

## yield生成器

[参考链接](https://www.ibm.com/developerworks/cn/opensource/os-cn-python-yield/index.html)。

相当于return，但不立刻执行，返回迭代器f。减少内存占用。可以用for循环或者f.next()来执行。每次执行完一个yield即返回，需要等到下个next()调用才能继续执行。


## 下划线‘_’表示不需要调用的参数

在数据处理中，我们读完csv等文件后，通常只需要取其中的几列，这时候不需要对所有的列都做赋值，可以用下划线来表示我们不需要调用的变量。例如：

```
with open('data.txt', 'r') as f:
	for line in f: 
		input, _, _, label = line.split(',') # 只需要第1,4列
```


## 下划线在python中的含义


## list

https://coderwall.com/p/rcmaea/flatten-a-list-of-lists-in-one-line-in-python







