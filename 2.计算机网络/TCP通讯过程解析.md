# TCP通讯过程解析

## 1.Tcp数据包

​	要了解Tcp协议，先要知道TCP/IP各层协议类型，如下图所示：

![网络各层协议](/Users/liukun/Workspace/GitHub/CPP-Learning/2.计算机网络/网络各层协议.png)

​	TCP协议在传输层上。

​	Tcp数据包在IP数据包的数据部分，格式如下：

![](/Users/liukun/Workspace/GitHub/CPP-Learning/2.计算机网络/Tcp数据包.png)

​	Tcp数据包最小是20个字节。一个Tcp数据包常用的有6个部分：Flags消息标志、Seq包序、Len消息长度(len是计算出来的，或者在可选项中，不清楚)、Ack请求包序、Win窗口大小、MSS最大数据分段（只在SYN包中发）。

​	Flags有6种，常用5种：

- SYN：请求连接
- ACK：确认包序
- FIN：断开连接
- PSH：发送数据时提示接收端立即从缓冲区中将数据读取；
- RST：重置连接
- URG：紧急指针有效（不常用）

![Tcp包内容](/Users/liukun/Workspace/GitHub/CPP-Learning/2.计算机网络/Tcp包内容.png)

​	Tcp通讯过程流程图如下所示，后续章节将对其进行详细解释。

![Tcp通讯过程](/Users/liukun/Workspace/GitHub/CPP-Learning/2.计算机网络/Tcp通讯过程.png)



## 2.Tcp建立连接（三次握手）



## 3.Tcp通讯过程

### 3.1 keep alive

参考：https://blog.csdn.net/lanyang123456/article/details/90578453

### 3.2 流量控制

参考：https://blog.csdn.net/weixin_41969690/article/details/107895605

### 3.3 用塞控制

参考：https://blog.csdn.net/weixin_41969690/article/details/107895605

### 3.4 重发机制

参考：https://blog.csdn.net/whgtheone/article/details/80970292

参考：https://blog.csdn.net/weixin_41969690/article/details/107895605

### 3.5 提示

ACK生成规则

1. 当一端向另一端发送一个数据段时，它必须包含一个ACK。这就给出了它期望接收的下一个序列号。(书包)
2. 如果只有一个未完成的有序段，则接收端需要延迟发送ACK段(直到另一个段到达或500ms)。它防止ACK段产生额外的流量。
   3.任何时候不应该有超过2个顺序的未确认段。防止不必要的重传
3. 当一个段的序列号超出预期时，接收端立即发送一个ACK段，宣布下一个预期段的序列号。(快速重传)
4. 当一个缺失的段到达时，接收端发送一个ACK段来宣布预期的下一个序列号。
5. 如果一个重复的段到达，接收方立即发送一个ACK。

## 4.Tcp断开连接（四次挥手）

