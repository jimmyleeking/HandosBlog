---
layout: post
title:  "关于Socket编程的简单研究"
date:   2015-05-11 16:50:23
categories: Java
---


套接字是一个网络非常通用的概念，java在套接字上面的开发是相对简单的，几句代码就能够实现套接字通讯。


##服务端

对于服务器来说，他只需要被动等待客户端的连接，对于服务器的通用流程如下：

1. ServerSocket用来创建服务端
2. 当有Socket连接的时候，accept就会被触发，返回一个客户端的socket。
3. 我们可以通过客户端的socket来进行输入和输出处理。

1.创建服务端

<pre>
<code>
int port=7878;//指定端口
ServerSocket server = new ServerSocket(port);
</code>
</pre>

2.获取连接客户端
<pre>
<code>
Socket socket=server.accept();
</code>
</pre>
3,获取客户端输入数据

<pre>
<code>
//客户端-》服务器
BufferedInputStream in=new BufferedInputStream(socket.getInputStream());

//获取输入字符串
String str=null;
StringBuffer sb=new StringBuffer();
while((str=sb.readLine())!=null)
{
	sb.append(str);
}

//输出
BufferedOutputStream out=new BufferedOutputStream(socket.getOutputStream());
//输出内容
String outContent="Hello,Nice!";
out.write(outContent.getBytes());
out.flush();
</code>
</pre>

##客户端

在客户端，我们只需要创建Socket，然后指定服务器的地址和端口就可以，对于局域网我们可以通过简单的IP来进行通讯。

1.创建socket
<pre>
<code>
//服务器IP
String ip="192.168.1.1";
//服务器端口
int port=8080;
Socket socketClient=new Socket();
SocketAddress addr=new InetSocketAddress(ip,port)
socketClient.connect(addr);
</code>
</pre>

2.输入和输出

同样的和服务器，只要正确建立连接之后，我们就可以用我们创建的socket来和服务器进行通讯。

<pre>
<code>
if(socketClient.isConnected())
{
	//用来接受服务器信息
	BufferedInputStream in=new BufferedInputStream(socket.getInputStream());
	//用来给服务器发送信息
	BufferedOutputStream out=new BufferedOutputStream(socket.getOutputStream());

}
</code>
</pre>

