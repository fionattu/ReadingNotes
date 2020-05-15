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
grep wc file.txt #查找file.txt中包括关键词wc的行并打印出来
grep -n wc file.txt #查找file.txt中包括关键词wc的行并打印出行号和行
grep -i WC file.txt #不区分大小写
grep -v wc file.txt #查找file.txt中不包括关键词wc的行并打印出来
grep -r wc dev/data #递归查找dev/data路径中包含wc的文件并打印出包括wc的行

```
#### find	
```
find . -name "*.md"  #从当前目录开始查找所有扩展名为md的文件 
```
#### 解压压缩

## 磁盘管理
#### cd: *切换工作目录*
```
cd /  #进入根目录，所有跟在/后面的为绝对路径
cd或cd~或cd $HOME  #进入当前用户主目录
cd -  #切换到上一个工作目录
cd .. #切换到上一层工作目录
cd ../../ #切换到上上层工作目录，等同于cd ../.., 主要看有多少个..
```
#### df: *检查文件系统的磁盘空间占用情况*
```
df -h # 所有被挂载的文件系统(指的磁盘分区)的磁盘总量和使用量,以及其对应的挂载目录。
一般分区的磁盘使用量即使达到100%，也会留给管理员使用空间。
df -h /etc # 将/etc底下的磁盘使用情况以易读的容量格式显示
```
#### du: *检查某个目录下的磁盘空间使用情况*
```
du  # 当前目录以及其子目录的所占空间
du file.txt # 显示文件的所占空间
du -c file1.txt file2.txt # 显示多个文件空间并统计总和
du <directory> # 显示指定目录的所占空间
du -s # 只显示空间的总和大小
du -h # 方便可读格式
du -sh <directory/file> # 方便可读格式显示总和
```

## 网络通讯
#### ping: *测试本机/主机的网络功能*
```
ping localhost/127.0.0.1/本机ip地址 # 测试本机的tcp/ip协议是否正常工作
ping baidu.com # 测试域名主机是否正常工作
```
本机发送包和主机返回包的大小一样(默认64bytes)，发包一般间隔一秒(可以设置)。time是包发送+接受的时间，ttl是所能经过的路由器最大值，防止路由表错误造成无限循环。

## 系统管理
* 检查内存使用情况：free -h
* top/htop

## 进程管理

* ps aux | grep <name>
* kill -9 <pid>

## 权限管理

* groupadd/useradd/newgrp/chown/chmod

## 其他设置

* export
* source
* service
* nohup
* 操作符&&
* cp -r a1 a2  vs. cp -r a1/ a2