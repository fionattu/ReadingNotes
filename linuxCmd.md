## 文件操作

#### wc: *用于计算文件的lines/words/characters/bytes*.
* -l：查阅文件的行数 
* -w: 查阅文件词语数量
 
```
wc file.txt #依次显示lines words characters 文件名
wc -l file1.txt file2.txt #分别显示文件行数，最后显示总行数
```
#### grep: *查找满足条件的文件*
```
grep wc file.txt #查找file.txt中不包括关键词wc的行并打印出来
grep -n wc file.txt #查找file.txt中不包括关键词wc的行并打印出行号和行内容
grep -i WC file.txt #不区分大小写
grep -v wc file.txt #查找file.txt中包括关键词wc的行并打印出来
grep -r wc dev/data #递归查找dev/data路径中包含wc的文件并打印出包括wc的行

```
#### find	
```
find . -name "*.md"  #从当前目录开始查找所有扩展名为md的文件 
```
#### source


## 内存磁盘管理

* 检查内存使用情况：free -h
* 检查磁盘使用情况：df -sh
* 检查某个目录下的磁盘使用情况： du -sh <directory>
* top/htop

## 进程管理

* ps aux | grep <name>
* kill -9 <pid>

## 权限管理

* groupadd/useradd/newgrp/chown/chmod

## 其他

* export