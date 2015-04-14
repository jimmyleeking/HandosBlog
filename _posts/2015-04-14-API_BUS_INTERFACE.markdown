---
layout: post
title:  "拥抱变化的API：总线设计思想以及通过接口来暴露实现类"
date:   2015-04-14 23:07:00
categories: API
---




日常的开发工作中，我们通常需要使用很多工具类，或者将某一些常见工具类集合起来，做成一个管理器来使用。随着项目的增多和项目人员的增多，各种工具类就会越来越多，出现工具类功能重复的情况也在所难免。

我通常，非常讨厌代码重复，我的理想编程环境是，有且只有唯一的某一个特定功能通用工具类或者工具管理器。我认为工具类应该是统一管理的。首先我们要有一个类似工具类获取的核心，然后根据工具类的不同再进行不同工具类的划分，比如与网络有关的，我们就有一个获取网络工具类的方法，就像如下定义一样：

<pre>
<code>
//工具系统核心
Kernel kernel=Kernel.getInstance();
//获取网络有关的工具类
kernel.getNetworkManager();
FtpNetworkManager ftpNetworkManager=(FtpNetworkManager)kernel.getNetworkManager(Network.Ftp);
//获取与UI有关的工具类
kernel.getUIManager();
</code>
</pre>

编码首先应该有一个核心的系统总线，然后再进行功能的散发，这样才能让你的代码层级更易于理解，易于维护。其次是，暴露接口比暴露类要更具好一些，因为暴露接口我们可以让用户学习成本更低，让用户更容易获取自己所需的东西。

就比如我们设计一个Ftp连接管理器，一般我们的需要的最核心的功能是：建立连接->上传下载文件->关闭连接。如果我们有且只需要这三个功能，那么我们的接口只需要实现这个三个方法:
<pre>
<code>
public interface IFtpNetworkManager{
	public void connect();
	
	public void uploadFile(File file);
	
	public void downloadFile(String srcFilePath,String targetFilePath);
}
</code>
</pre>

但实际上一个ftp实现类需要具备的可能不单单只有三个方法，就单纯连接的话，我们需要四个信息主机地址，端口，用户名，密码（当然如果涉及到安全方面，还需要一些安全方面的参数）。因此，实际上我们的connect需要有四个变量。当然，你可能还需要一些连接的状态信息，一起其他相关必要的方法，这个时候，我们的类，还会写成这样子:

<pre>
<code>
public class SimpleFtpNetworkManager implements IFtpNetworkManager{
	public void connect(){
		...
	}
	public void connect(String host,int port,String username,String password)
	{
		....
	}
	public boolean isConnected()
	{
		...
	}
	public String getCurrentDir()
	{
		...
	}
	
	public void uploadFile(File file){
		...
	}
	
	public void downloadFile(String srcFilePath,String targetFilePath){
	...
	}
	
	// other method
	....
}
</code>
</pre>

如果作为一个新手用户，如果一开始就见到一个超级强大的实现类，可能一开始在用户的时候就会稍加困惑，但是如果这个新手恰好只是想匿名连接一个FTP服务器，并且上传和下载文件，我认为如果单纯从接口上我认为就能够满足他的需求，我相信他也无需成本来学习一些有关ftp的一些高级知识，而他仅仅需要的是:

<pre>
<code>
//遵循总线设计，提取工具类
//实际上返回的实体对象是一个非常完善的ftp实现类。
IFtpNetworkManager manager=(IFtpNetworkManager)kernel.getNetworkManager(Network.Ftp);
//但用户只需要关心接口的方法
manager.connect();

manager.downloadFile("ok.txt","/tmp/temp.txt");

</code>
</pre>

尽管在现实生活中，一个ftp连接接口当然也不会这么简单，但是我们从这个例子来拓展一下，设计一个能够符合大部分需求的接口定义方法来暴露实现类，且尽可能少暴露一些非必要的方法，对于一般用户来说，会更易于接受和学习使用，而且也更有益于一些内部字段的隐藏，我们甚至可以直接隐藏掉实现类，让用户只能感知到接口的存在，却不必清楚内部的实现机制。




