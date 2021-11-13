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

### 回溯 HTTP 事务处理过程：

![](https://i.loli.net/2021/11/12/6D4NKQAWus8haqM.png)

- 当客户端访问Web站点时，首先会通过DNS服务器生成HTTP请求，并通过TCP/IP协议发送给Web服务器。Web服务器接收到请求后会根据请求生成响应内容，并通过TCP/IP协议返回给客户端。

![](https://i.loli.net/2021/11/12/iGx4uWKjDpt9YwQ.png)

#### 实验：与 HTTP 请求的第一次亲密接触：

- 下载工具：

  [wireshark]: https://www.wireshark.org/#download

### 熟悉 HTTP 协议结构和通讯原理：

##### 支持客户/服务器模式：

- 客户/服务器模式工作的方式是由客户端向服务器发出请求，服务端响应请求，并进行相应服务

![](https://i.loli.net/2021/11/12/lhzg48F9OCKq3HG.png)

##### 简单快速：

- 客户向服务器发送请求时，只需传送请求方法和路径。
- 请求方法常用的有 GET、HEAD、POST。每种方法规定了客户与服务器联系的类型不同。

##### 灵活：

- HTTP 允许传输任意类型的数据对象
- 正在传输的类型由 Content-Type （Content-Type 是 HTTP 包中用来表示内容类型的标识）加以标记

##### 无连接：

- 无连接的含义是限制每次只处理一个请求
- 服务器处理完客户的请求，并收到客户的应答后，即断开连接
- 采用这种方式可以节省传输时间

##### 无状态：

- HTTP 协议是无状态协议
- 无状态是指协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息，则它必须重传，这样可能导致每次连接传送的数据量增大
- 另一方面，在服务器不需要先前信息时它的应答就较快

### URL 和 URI：

Q：我们输入在浏览器里的Web地址应该叫 URL 还是 URI？

![](https://i.loli.net/2021/11/12/OhlIA1moaNE8fke.png)

- URI：一个紧凑的字符串用来标示抽象或物理资源

- A URI 可以进一步被分为定位符、名字或两者都是
- 术语 ”Uniform Resource Locator“ （URL）是 URI 的子集，除了确定一个资源，还提供一种定位该资源的主要访问机制（如：其网络”位置“）

维基百科的解释：

- URI 可以分为 URL，URN 或同时具备 locators 和 names 特性的一个东西
- URN 作用就好像一个人的名字，URL 就像一个人的地址
- 换句话说：URN 确定了东西的身份，URL 提供了找到它的方式

总结：

- URL 是 URI 的一种，但不是所有的 URI 都是 URL，就好比蝴蝶都会飞但会飞的不一定都是蝴蝶。
- URI 和 URL 最大的差别是 ”访问机制“
- URN 是唯一标识的一部分，是身份信息

辨别：

1. ftp://ftp.is.co.za/rfc/rfc1808.txt
2. http://www.ietf.org/rfc/rfc2396.txt
3. ldap://[2001:db8::7]/c=GB?objectClass?one'
4. mailto:John.Doe@example.com
5. news:comp.infosystems.www.servers.unix
6. tel:+1-816-555-1212
7. telnet://192.0.2.16:80/
8. urn:oasis:names:specification:docbook:dtd:xml:4.1.2

上面的都是 URI，1其中 1、2、3、4、5 、7 也是 URL，也就是提供访问机制的 URI 也可以是 URL

### HTTP 报文结构分析 - 请求报文：

![](https://i.loli.net/2021/11/12/SVfZCDzQj7kpLdO.png)

#### HTTP 报文头：

- HTTP 的报文头可以分为四类，分别是：

  通用报文头、请求报文头、响应报文头和实体报文头。

- 在 HTTP/1.1里一共规范了 47 种报文头字段

##### 通用报文头：

![](https://i.loli.net/2021/11/12/snHFq6PZor34aAu.png)

##### 请求报文头：

![](https://i.loli.net/2021/11/12/OTblyS5g64ivsop.png)

##### 响应报文头：

![](https://i.loli.net/2021/11/12/7R62jYaJMHhn8oV.png)

##### 实体报文头：

![](https://i.loli.net/2021/11/12/xZ4tYzGKeF5mybS.png)

#### 常见的：

###### ACCEPT：

- 作用：浏览器端可以接受的媒体类型。

  Accept：text/html 代表浏览器可以接受服务器回发的类型为 text/html 也就是我们常说的 html 文档，如果服务器无法返回 text/html 类型的数据，服务器应该返回一个 406 错误（Non Acceptable）；

  Accept：\*/* 代表浏览器可以处理所有类型

  如果想要给显示的媒体类型增加优先级，则使用 q = 来额外表示权重值；重值 q 的范围是 0 ~ 1（可精确到小数点后 3 位），且 1 为最大值。不指定权重 q 值时，默认权重值为 q = 1.0 。当服务器提供多种内容时，将会首先返回权重值最高的媒体类型。

###### Accept-Encoding：

- 作用：浏览器申明自己接收的编码方法，通常指定压缩方法，是否支持压缩，支持什么压缩方法（gzip，deflate）

###### Accept-Language：

- 作用：浏览器申明自己接收的语言
- 如：Accept-Language：zh-cn,zh;q=0.7,en-us,en;q=0.3
- 客户端在服务器中有中文版资源的情况下，会请求其返回中文版对应的响应，没有中文版时，则返回英文版响应

###### Connection：

- Connection：keep-alive    当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，如果客户端再次访问这个服务器上的网页，会继续使用这一条已经建立的连接
- Connection：close    代表一个 Request 完成后，客户端和服务端之间用于传输 HTTP 数据的 TCP 连接会关闭，当客户端再次发送 Request，需要重新建立 TCP 连接

###### Host：

- 作用：请求报头域主要用于指定被请求资源的 Internet 主机和端口号，它通常从 HTTP URL 中提取出来的

  我们在浏览器中输入： http://www.fljf.com:8008

  浏览器发送的请求消息中，就会包含 Host 请求报头域，如下：

  Host：www.fljf.com:8080

###### Referer:

- 当浏览器向web服务器发送请求的时候，一般会带上Referer，告诉服务器我是从哪个页面链接过来的，服务器籍此可以获得一些信息用于处理

###### User-Agent：

- 作用：告诉 HTTP 服务器，客户端使用的操作系统和浏览器的名称和版本
- 很多情况下我们会通过 User-Agent 来判断浏览器类型，从而进行不同的兼容设计

###### Content-Type:

- 作用：说明了报文体内对象的媒体类型

  text/html：HTML 格式

  text/plain：纯文本格式

  text/xml：XML格式

  image/gif：gif图片格式

  image/jpeg：jpg图片格式

  image/png：png图片格式

  application/xhtml + xml：XHTML格式

  application/xml：XML数据格式

  application/atom + xml：Atom XML 聚合格式

  applicaton/json：JSON 数据格式

  application/pdf：pdf格式

  application/msword：Word文档格式

  application/octet-stream：二进制流数据（如常见的文件下载）

  application/x-www-form-urlencoded：表单提交

### HTTP 报文结构分析 - 响应报文：

![](https://i.loli.net/2021/11/12/YKdzRpNPmf65jyW.png)

可以把上面响应头中的第一行单独划出来划为响应行

### HTTP 请求方法剖析：

- HTTP/1.1 常用方法：

  GET、POST、PUT、HEAD、DELETE、OPTIONS、TRACE、CONNECT

##### GET 获取资源：

- GET 方法用来请求访问已被 URL 识别的资源

- 指定的资源经服务器端解析后返回响应内容

- 浏览器对长度有要求 --- IE：2803    firefox：655536    chrome：8186    sfafie：80000

- GET 方法也可以用来提交表单和其他数据

  http://localhost/login.php?username=xx&password=1234

  从上面的URL请求中，很容易就可以辨认出表单提交的内容

##### POST：

- POST 方法与GET功能类似，一般用来传输实体的主体
- POST 方法的主要目的不是获取响应主体的内容

##### PUT：

- 从客户端向服务器传送的数据取代指定的文档内容
- PUT 方法与 POST 方法最大的不同是：PUT 是幂等，而 POST 是不幂等的
- 因此，我们更多时候将 PUT 方法用作传输资源

##### HEAD：

- 类似于 GET 请求，只不过返回的响应中没有具体的内容，用于获取报头、
- 用来测试超链接的可行性，有没有更新啥子的

##### DELETE：

- 请求服务器删除指定的资源

##### OPTIONS：

- 用来查询针对请求 URL 指定的资源支持的方法

##### TRACE：

- 回显服务器收到的请求，主要用于测试或诊断
- 容易引发 XST（跨站跟踪） 攻击方式

##### CONNECT：

- 开启一个客户端与所请求资源之间的双向沟通的通道，它可以用来创建隧道

### 状态码：

- 是用来表示服务器超文本传输协议响应状态的三位数字代码。

![](https://i.loli.net/2021/11/13/BCiqHcS62ENmM7g.png)

![](https://i.loli.net/2021/11/13/vGUouZEdxBfN91n.png)

![](https://i.loli.net/2021/11/13/EO5RN6D7dC9wLeM.png)

![](https://i.loli.net/2021/11/13/D9ypYIuP1dmL8fk.png)

![](https://i.loli.net/2021/11/13/yMKJvd7rtsZGqC1.png)

### HTTP 状态管理：Cookie 和 Session

##### Cookie：

- 实际上是一小段的文本信息。客户端请求服务器，如果服务器需要记录该用户状态，就向客户端浏览器颁发一个
- 客户端浏览器会把Cookie保存起来。当浏览器再次请求该网站时，浏览器把请求的网址连同该Cookie一同提交给服务器。服务器检查该Cookie，以此来辨别用户状态

![](https://i.loli.net/2021/11/13/FYwmLcde8sk7gVz.png)

首次见面相认不相识，再次见面相认又相识

![](https://i.loli.net/2021/11/13/SYdxRW16KH5e3ZU.png)

##### Session：

- Session 是另一种记录客户状态的机制，保存在服务器上。客户端浏览器访问服务器的时候，服务器把客户端信息以某种形式记录在服务器上

![](https://i.loli.net/2021/11/13/PRVXG6o5IMKs834.png)

##### 保存 Session ID 的方式：

- Cookie
- URL 重写 
  - 作为一个参数写在 URL 后面
  - 写在 URL 路径后面，作为 URL 的附加信息
- 隐藏表单    服务器会自动添加一个字段以便服务器提交时把Session ID传递到服务端

##### Session 的有效期：

- Session 超时失效（自动失效）
- 程序调用 HttpSession.invalidate() （主动失效---关闭等）
- 服务器进程被停止（如：断电导致的服务器异常终止）

##### Cookie 与 Session：

- 存放位置不同:
  - Cookie 存储在客户端，Session 存储在服务端
- 安全性（隐私策略）的不同:
  - Session不存在敏感信息泄露问题，而Cookie存储在客户端可能会存在信息泄露问题，解决方法是不在Cookie中存储敏感信息，或者像百度、谷歌那样对Cookie进行加密存储，再进行服务端的解密，保证信息只能服务端能读得懂
- 有效期上的不同:
  - Cookie可以在客户端存储很长时间，但是Session不行，服务器端会定期的对过期的Session进行清理，避免出现过大的压力
- 对服务器压力的不同：
  - Session 如果服务端用户量非常大那么Session就会很大对服务端的压力也会很大
  - Cookie存储在客户端，对服务端压力不会很大

### HTTP协议中的编码和解码：

#### 字符集和编码：

编码规范：通过不同的二进制数表示不同的字符

##### 什么是编码：

##### 为什么需要编码：

##### 什么时候出现乱码：

### 网友博客：

https://blog.csdn.net/weixin_42100064/article/details/102739531