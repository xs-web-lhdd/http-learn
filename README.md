# HTTP:

![](https://i.loli.net/2021/11/11/CEusrM9ZkzUXK7I.png)

- 超文本传输协议（HTTP）是一种**通信协议**，它允许将超文本标记语言（HTML）文档从Web服务器传送到客户端的浏览器

- HTTP 是一个属于<span style="color: red;">应用层的面向对象的协议</span>，由于其简捷、快速的方式，适用于分布式超媒体信息系统。它于1990年提出，听过几年的使用和发展，得到不断的完善和扩展

### Web 和 HTTP

- web 是一种基于超文本和HTTP的、全球性的、动态交互的、跨平台的<span style="color: red;">分布式图形信息系统</span>
- 建立在Internet上的一种<span style="color: red;">网络服务</span>，为浏览器在Internet上查找和浏览信息提供了图形化的、易于访问的直观界面，其中的文档及超级链接将Internet上的信息节点组织成一个互为关联的网状结构

### HTTP协议的前世今生：

### 透过TCP/IP看HTTP：

- HTTP 协议是构建在 TCP/IP 协议之上的，是 TCP/IP 协议的一个子集
- 为了更好的理解 HTTP 协议，我们先了解一下 TCP/IP 的相关知识

#### TCP/IP协议族：

- TCP/IP协议其实是一系列与互联网相关联的协议集合起来的总称
- 分层管理是TCP/IP协议的重要特征

##### TCP/IP协议分分层：

- TCP/IP协议族是由一个四层协议组成的系统，这四层分别是：<span style="color: red;">应用层、传输层、网络层和数据链路层</span>

![](https://i.loli.net/2021/11/11/hPOorWkRuaH5tYb.png)

###### 应用层：

- 应用层一般是我们编写的应用程序，决定了向用户提供的应用服务。应用层可以通过系统调用与传输层进行通信。如：FTP、DNS、HTTP等。

###### 传输层：

- 传输层通过系统调用向应用层提供处于网络连接中的两台计算机之间的数据传输功能。

- 在传输层有两个性质不同的协议：<span style="color: red">TCP</span>和<span style="color: red">UDP</span>
  - TCP 面向连接的而 UDP 是无连接的，这就决定了 TCP 虽然比较可靠但是需要建立连接所以效率比较低，UDP 没有连接效率比较高，但是不太安全

###### 网络层（网络互连层）：

- 网络层用来处理在网络上流动的数据包，数据包是网络传输的最小数据单位。该层规定了通过怎样的路径（传输路线）到达对方计算机并把数据包传输给对方。

###### 链路层：

- 链路层用来处理连接网络的硬件部分，包括控制操作系统、硬件设备驱动、NIC（Network Interface Card，网络适配器）以及光纤等物理可见部分。硬件上的范畴均在链路层的作用范围之内。

![](https://i.loli.net/2021/11/11/HBrRcmpO2ANuMgw.png)

#### HTTP数据传输过程：

- 发送端发送数据时，数据会从上层传输到下层，且每经过一层都会被打上该层的头部信息。而接收端接收数据时，数据会从下层传输到上层，传输前会把下层的头部信息删除

![](https://i.loli.net/2021/11/11/vY18QonpG2JHByZ.png)

#### 传输层---TCP三次握手：

- 使用TCP协议进行通信的双方必须先建立连接，然后才能开始传输数据。为了确保连接双方可靠性，在双方建立连接时，TCP协议采用了三次握手策略。

![](https://i.loli.net/2021/11/11/Js9XQLad42fPiMk.png)

##### 第一次握手：

​	客户端发送带有SYN标志的连接请求报文段，然后进入SYN_SEND状态，等待服务端的确认。

##### 第二次握手：

​	服务端接收到客户端的SYN报文段后，需要发送ACK信息对这个SYN报文段进行确认。同时，还要发送自己的SYN请求信息。服务端会将上述的信息放到一个报文段（SYN+ACK报文段）中，一并发送给客户端，此时服务端将会进入SYN_RECV状态。

##### 第三次握手：

​	客户端接收到服务端的SYN+ACK报文段后，会想服务端发送ACK确认报文段，这个报文段发送完毕后，客户端和服务端都进入 ESTABLISHED 状态，完成 TCP 三次握手。

### ”如何访问某东某宝的“ ---DNS域名解析：

- 已经介绍了与HTTP协议有着密切关系的TCP/IP协议，接下来介绍的DNS服务也是与HTTP协议有着密不可分的关系
- 通常我们访问一个网站，使用的是主机名或者域名来进行访问的。因为相对于IP地址（一组纯数字），域名更容易让人记住。但TCP/IP协议使用的是IP地址进行访问的，所以必须有个机制或服务把域名转化为IP服务。DNS服务就是用来解决这个问题的，他提供了域名到IP地址之间的解析服务。