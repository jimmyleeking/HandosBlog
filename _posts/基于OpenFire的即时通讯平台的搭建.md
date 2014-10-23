#基于OpenFire的即时通讯平台的搭建

###OpenFire介绍
Openfire是一款采用java语言开发，基于开源的实时协作（RTC）服务器基于XMPP（Jabber）协议的即时通讯平台软件，他采用Web进行管理，使得安装和使用都非常简单，易于管理，在性能上但台服务器可以支持上万并发用户。

###XMPP协议简介
XMPP（可扩展消息处理现场协议）是基于可扩展标记语言（XML）的协议，它用于即时消息（IM）以及在线现场探测。 
XMPP的前身是Jabber，一个开源形式组织产生的网络即时通信协议。 
XMPP的基本网络结构 ,xmpp定义了3个角色
Client
Server
Gateway
通信能够在这三者的任意两个之间双向发生。服务器同时承担了客户端信息记录，连接管理和信息的路由功能。网关承担着与异构即时通信系统的互联互通，异构系统可以包括SMS（短信），MSN，ICQ等。基本的网络形式是单客户端通过TCP/IP连接到单服务器，然后在之上传输XML。 
客户端利用xmpp（基于TCP/IP）访问server，传输的是XML 
Client--------Server----Client
    TCP            TCP	     TCP
 相关XMPP协议图
 
###为什么有人说Socket也可以实现即使聊天，还要用XMPP这种复杂协议来编程呢？XMPP协议和HTTP协议，SOCKET有什么关系吗？

###Openfire安装，搭建，运行
1，下载对应平台的安装包。
2，

###实现一对一的聊天



###客户端开发采用SMACK组件，IOS客户端开发采用

###

参考文档：
揭开Socket编程的面纱
http://goodcandle.cnblogs.com/archive/2005/12/10/294652.aspx
