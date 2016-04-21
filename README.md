## 一个简单的分布式排序模型

整个模型借鉴hadoop的管理模型，由一个master节点来管理任务调度，slave节点完成给定的任务。

![model](https://github.com/WnFg/Distribute_sort/blob/master/image/model.png)


###主要文件说明

command.h：定义了master可以发出的3种命令的数据格式，以及表示文件状态的数据结构。
3种命令分别是传送数据，接收数据，排序。其中，在接到排序命令后，slave节点会根据当前文件状态选择不同的排序方案。

IO.h： 定义了一些可以将字符串格式化的函数，以及将read系统调用封装为一个稳定的文件读取函数。

rio_file.h： 定义了通过网络传输文件的函数，以及能生成一个随机文件名的函数等。

server.h： 封装了一些常用的套接字功能。 

master.cc: master节点的程序代码。

slave.cc： slave节点的程序代码。

sort.cc：  排序算法。数据量较小时使用快速排序，数据量大时，使用外部的两路归并排序。


