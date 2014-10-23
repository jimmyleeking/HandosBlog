---
layout: post
title:  "Microsoft BI 笔记"
date:   2014-10-23 18:22:23
categories: Learning
---


>参考书籍<br>
SQL Server 2008 商业智能完美解决方案
<br>


##因何而起

目前商业智能的书籍和相关资料还是太少，国内的BI还不是很成熟，可以给新手的公开资料有限。在网络上转了一圈，一些高品质的资料还是很或缺的。因此简单写一个Microsoft BI入门教程，希望让后来人不要再淌着浑水过河，一旦过了入门槛，会发现前途一片光明。

##学习架构

第一部分 "商业智能基本概念"

第二部分 "准备BI开发环境"


##第一部分 商业智能基本概念

商业智能解决方案包含对企业级关键数据的有效存储和表示，使得授权用户能够迅速，快捷地访问并解决相关数据。

![商业智能解决方案整合视图](/res/images/bi-concept.png)

###OLTP 联机事务处理(OnLine Transaction Processing)

用来描述为了处理事务性活动而设计，优化的关系数据存储。事务性活动指的是在表中插入、更新和删除行。
其基本特征是顾客的原始数据可以立即传送到计算中心进行处理，并在很短的时间内给出处理结果

###OLAP 联机分析处理(OnLine Analytical Processing)

用来描述为了分析活动而设计、优化的数据结构。分析活动指的是侧重于数据读取应用方面的活动，而不是为了更有效地修改数据二队数据进行的优化活动。

###OLTP和OLAP的区别

||OLTP|OLAP|
|--|--|--|
|用户|操作人员,低层管理人员|决策人员,高级管理人员|
|功能|日常操作处理|分析决策|
|DB设计|面向应用|面向主题|
|数据|当前的, 最新的细节的, 二维的分立的|历史的, 聚集的, 多维的集成的, 统一的|
|存取|读/写数十条记录|读上百万条记录|
|工作单位|简单的事务|复杂的查询|
|用户数|上千个|上百万个|
|DB大小|100MB-GB|100GB-TB|
|时间要求|具有实时性|对时间的要求不严格|
|主要应用|数据库|数据仓库，决策支持系统，保镖数据库，数据仓库，多维数据集 |

###数据仓库

数据仓库是一个单一结构，通常由一个或多个朵唯数据集构成。数据仓库用于保存聚合起来的或者滚动积累起来的主要组织数据的只读视图。

###多维数据集

多维数据集是经典数据库产品在包含许多关系表时使用的一种数据结构。多维数据集中包含的是纬度和量度（而不是数据表的行和列）。多维数据集可以包含生产数据的完整副本，通常情况下一般为源数据的子集。

###数据挖掘

用在对数据没有确定假设的情况下。一个有效场景：业务需求要对数据集中的一个或多个目标值的未来情况作出预测。

###ETL 提取、转换、加载系统。(Extrac,Transform,Load)

指的是一整套协助将各类源数据提取、转换并加载到OLAP多维数据集或者数据挖掘结构中的服务。

##Microsoft BI解决方案的核心组件

![BI核心组件](/res/images/micBIInfractruct.png)

####SSAS (SQL Server Analysis Services)

为数据仓库提供了存储和查询OLAP多维数据集数据的机制，并提供精密的OLAP多维数据集开发人员和管理人员界面。

####SSRS (SQL Server Reporting Services)

SQL Server 2005 Reporting Services 是基于服务器的报表平台，可以用来创建和管理包含关系数据源和多维数据源中的数据的表格、矩阵、图形和自由格式的报表。可以通过基于万维网的连接来查看和管理所创建的报表。Reporting Services 包括下列核心组件：

* 一整套工具，可以用来创建、管理和查看报表。
* 一个报表服务器组件，用于承载和处理各种格式的报表。输出格式包括 HTML、PDF、TIFF、Excel、CSV 等。
* 一个 API，使开发人员可以在自定义应用程序中集成或扩展数据和报表处理，或者创建自定义工具来生成和管理报表。

####SBIS (Business Integration Services)

用于对数据进行导入、清理以及验证。


##BI查询语言

###MDX(multidimensional expressions)

用来查询OLAP多维数据集的语言

查询示例
<pre>
<code>
SELECT [Customer].[Customer Geography] ON COLUMNS,[Date].[Fiscal] ON ROWS
FROM [Adventure Works]
</code>
</pre>
查询结果

||All Customers|
|--|--|
|All Periods|$80,450,596,98|

### DMX (Data Mining Extesions)

用于查询Analysis Service的数据挖掘结构。

### XMLA (XML for Analysis)

用来在Anaysis Service中执行管理员任务。

### RDL (report definition language)

报表定义语言，是另一种XML格式的语言，用于创建Reporting Service报表。






































