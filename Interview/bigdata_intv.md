面试官您好，我叫雷洪亮，本科毕业于武汉工程大学，现在是杭州电子科技大学人工智能学院电子信息专业的一名硕士研究生，现在发表了一篇软著，一项专利以及一篇论文再投。本科期间学校就开展了大数据的相关选修课程，进入硕士研究期间后也是深入研究深度学习领域。

同时在校期间学习了Java基础，常用数据结构与算法、并发、
数据采集方向学习了Flume,DataX和Maxwell的使用。
数据存储熟悉了Hadoop，Hive，HBase，ElasticSearch以及ClickHouse的存储。
数据计算方面熟悉了Flink，HiveSQL以及Spark体系。

并自己动手做了两个项目去巩固学习到的知识，最开始做的是一个电商的离线数据仓库系统，通过这个项目我学习到了 1、源数据传输过程中的解耦与流量削峰；2、数仓的搭建流程以及kimiball维度建模方法；3、熟练的使用SQL进行指标分析；4、以及元数据管理管理。

第二个项目是基于flink实现的实时电商业务分析系统，通过这个项目学习到了flink CDC监控和捕捉数据的原理；维表与流表的动态分流；查询维表时的旁路缓存优化和异步I/O优化；在指标分析过程中熟练使用flink丰富的窗口机制与状态编程并防止了数据倾斜的发生；
 

# 数仓建模

### 介绍下数据仓库

1. 数据库
	1. 是按照一定格式和数据结构在计算机保存数据的软件，属于物理层。关系数据库是指采用了关系模型来组织数据的数据库
	2. 以行和列的形式存储数据，具有结构化程度高，独立性强，冗余度低等优点。
2. 数据仓库
	1. 数据仓库存在的意义在于对企业的所有数据进行汇总，为企业各个部门提供统一的， 规范的数据出口。
	2. 数据仓库是面向主题集成的
	3. 数据仓库是集成的 对企业内不同业务部门数据完整集合，而且还是处理过的数据。
	4. 数据仓库的数据是稳定的 数仓里不存在数据的更新和删除（不是指数据到期的删除）操作。
	5. 数据仓库中的数据是随时间变化而变化的 数仓里会完整的记录某个对象在一段时期内的变化情况。
3. 数据湖
	1. 是一个集中存储各类结构化和非结构化数据的大型数据仓库，它可以存储来自多个数据源、多种 数据类型的原始数据，数据无需经过结构化处理，就可以进行存取、处理、分析和传输。数据湖能帮助 企业快速完成异构数据源的联邦分析、挖掘和探索数据价值。
	2. 与数据仓库相比，数据湖缺乏结构性，而且更灵活，并且提供了更高的敏捷性。数据仓库具有高性能、可 重复性的特点 

---

### 分层的目的

如果不分层的话：有什么数据就去原始数据查，这样比较麻烦、而且效率低、逻辑多、SQL语句长 、定位改动麻烦。

1. 复杂问题简单化： 将复杂的任务分解成多层来完成，每一层只处理简单的任务。
2. 清晰的数据结构：每层都有它的作用域和职责，在使用表的时候能更方便地定位和理解；
3. 减少重复开发： 通过主题层数据，提升计算结果的复用性。
4. 隔离原始数据：真实数据与统计数据解耦开。

---

### -3-数仓分层

1.  ODS ==原始==数据层
	1. 存放未经过处理的原始数据（实时数仓中保存在kafka，离线数仓中保存在hive），结构上与源系统保持一致，不做任何转换，与业务侧的数据保持同构
2.  DIM层 公共==维度==层 Dimension 
	1. 基于维度建模理论进行构建，存放维度模型中的维度表， 保存一致性维度信息。例如（商品维度表、地区维度表、用户维度表）
3.  DWD ==明细==数据层 Data Warehouse Detail (事实表)
	1. 基于维度建模理论进行构建，主要职责是：数据清洗，业务主题的划分（交易域、用户域）。将维度退化至事实表中，减少事实表和维表的关联，这一层主要起到缓冲的作用，屏蔽底层影响，尽量还原业务，统一标准存放维度模型中的事实表（具体的业务事件，流量域独立访客事务事实表，交易域下单事务事实），保存各业务过程最小粒度的操作记录。
4.  DWS ==汇总==数据层 Data Warehouse Summary 
	1. 主要职责是划分分析主题、建设各个主题公共统计粒度的汇总表，例如（交易域省份粒度下单各窗口汇总表）
5.  ADS 数据==应用==层 Application Data Service
	1. 为了具体需求而构建的应用层

---

### 维度退化
维度属性也可以存储到事实表中，这种存储到事实表中的维度列被称为“退化维度”。将维度退化到事实表中，减少事实表和维度表的关联。
1. 例如：用户id，这种量级很大的维度，没必要用一张维度表来进行存储，而我们一般在进行数据分析时用户id又非常重要，所以我们将订单id冗余在事实表中，这种维度就是退化维度
2. 数据明细层：DWD  该层一般保持和ODS层一样的数据粒度，并且提供一定的数据质量保证。同时，为了提高数据明细层的 易用性，该层会采用一些维度退化手法，将维度退化至事实表中，减少事实表和维表的关联。 另外，在该层也会做一部分的数据聚合，将相同主题的数据汇集到一张表中，提高数据的可用性
---

### [0] 数仓建模关系建模/维度建模

数据处理大致可以分为两大类：

1. 操作型处理，叫联机事务处理 OLTP（On-Line Transaction Processing），
   1. 针对具体业务在数据库联机的日常操作，通常对少数记录进行查询、修改。用户较为关心操作 的响应时间、数据的安全性、完整性和并发支持的用户数等问题。传统的数据库系统作为数据管理的主 要手段，主要用于操作型处理。
2. 分析型处理，叫联机分析处理 OLAP（On-Line Analytical Processing）
   1. 一般针对某些主题的历史数据 进行分析，支持管理决策。
---
### 维度建模
1. 关系（ER实体）建模
	1. 主要应用于OLTP系统中，为了保证数据的一致性以及避免冗余，所以大部分业务系统的表都是 遵循第三范式的。
	2. 缺点：范式的缺点是获取数据时，需要通过Join拼接出最后的数据。这种模型并不适合直接用于分析统计。
2. 维度模型
	1. 主要应用于OLAP系统中，通常以某一个事实表为中心进行表的组织，主要面向业务
	2. 可能存在数据冗余，但是能方便的得到数据。
3. 维度建模
	1. 维度建模是一种以业务为驱动的数仓建模方法，比较贴近人的思维 容易理解 表的关系简单 查询的时候不会join太多层 所以效率较高。维度模型更适合做数据的分析--比如聚合分析等等。
	2.  维度表：一般是对事实的描述信息。每一张维表对应现实世界中的一个对象或者概念。 例如：用户、商品、日期、地区等。
	3. 事实表：每行数据代表一个业务事件（下单、支付、退款、评价等）。“事实”这个术语表示的是业务事件的度量值（可统计次数、个数、金额等）
		1. 事务型事实表
			1. 一行数据就是一个具体的业务事件。例如一笔支付记录。对应于增量同步策略
		2. 周期型快照事实表
			1. 周期型快照事实表中不会保留所有数据，只保留固定时间间隔的数据，例如每天或者每月的销售额。对应于全量同步策略。
		3. 累计快照事实表
			1. 用于跟踪业务事实的变化。比如跟踪订单的生命周期(打包、运输和签收)，对应于新增及变化同步策略。
			2. 累积型快照事实表通常具有多个日期字段，每个日期对应业务流程中的一个关键业务过程（里程碑）。
---

### Kimball维度建模
	  1. 选择业务过程比如下单业务，一条业务线对应一张事实表。
  1. 声明粒度：声明粒度意味着精确定义事实表中的一行数据表示什么，应该尽可能选择最小粒度，以此来应对各种各样的需求。
  2. 确认维度：维度的主要作用是描述事实表，比如时间维度、地区维度、用户维度。
  3. 确认事实: 此处的“**事实**”一词，指的是**业务中的度量值**（次数、个数、件数、金额，可以进行累加），例如订单金额、下单次数等



---



### 1 关系建模
1. ER模型常用于OLTP数据库建模
	1. 减少数据冗余，尽量让每个数据只出现一次，获取数据时通过 join 拼接出最后 的数据。
2. 属性不可切割
	1. 数据库表的每一列都是不可分割的原子数据项
3. 不能存在“部分函数依赖”
	1. 每一列都和所有主键相关，而不能只与主键的某一部分相关（主要针对联合主键而言）
	2. 数据冗余 \ 删除异常 \ 插入异常  \ 更新异常
4. 不能存在传递函数依赖
	1. 要求任何字段不能由其他字段派生出来，它要求字段没有冗余，即不存在传递依赖；
	2. 大数据表拆分成两个或者更多个更小的数据表。

---

### 1 维度建模的三种模型

1. 星型模型
	1. 当所有维表都直接连接到事实表上时，整个图解就像星星一样，故将该模型称为星型模型。
	2. 不存在渐变维度， 所以==数据冗余==，但因此==效率高==。
2. 雪花模型
	1. 当有一个或多个维表没有直接连接到事实表上，而是通过其他维表连接到事实表上时，其图解就像多个 雪花连接在一起，故称雪花模型。
	2. 通过最大限度地减少数据存储量以及联合较小的维表来改善查询性能，==较少数据冗余==，但 是在分析数据的时候，操作比较复杂，需要join的表比较多所以其性能并不一定比星型模型高，因此==查询性能低==（jion太多shuffle流程也太多）
	3. 地域维，国家维，省份维
3. 星座模型
	1. 星座模式也是星型模式的扩展。包含多个事实表，而维表是公共的，可以共享，这种模式可以看做星型模式的汇集

---

### 1 数仓建模的流程

1. 业务建模
	1. 和业务人员梳理业务的过程，帮助技术人员更好的理解业务，深入了解各个业务部门的内具体业务流程并将其程序化。
2. 概念建模
	1. 画关系图。抽取关键业务概念，并将之抽象化。理清分组概念之间的关联
3. 逻辑建模
	1. 表设计。业务概念实体化，并考虑其具体的属性。 
	2. 事件实体化，也就是所谓的事实，并考虑其属性内容。 
	3. 说明实体化，也就是所谓的维度，并考虑其属性内容。
4. 物理建模
	1. 综合现实的大数据平台、采集工具、etl工具、数仓组件、性能要求、管理要求等多方面因素，设计出具 体的项目代码，完成数仓的搭建。
---

###   压缩方法

1. ODS 层要保存全部历史数据，故其压缩格式应选择压缩比较高的，此处选择 gzip。
2. DIM，DWS，DWD层的数据存储格式为 orc 列式存储+snappy 压缩。

压缩方法
1. Gzip
	1. 压缩比高，解压慢，冷数据
2. Snappy 
	1. 快速，压缩比适中，ORC + Snappy
3. Lzo
	1. 压缩率比gzip要低一些，Parquet+ Lzo
4. Bzip2压缩 
	1. 压缩/解压速度慢
---



###   列式存储
1. 数据库
	1. OLTP（联机事务处理）是传统关系型数据库的主要应用，用来执行一些基本的、日常的事务处理，比如数据库记录的增、删、改、查等等。
	2. OLAP（联机分析处理）则是分布式数据库的主要应用，它对实时性要求不高，但处理的数据量大，通常应用于复杂的动态报表系统上
2. 传统的数据编码方式是以行为单位进行，列式存储则是将==数据划分成数据块==，每个数据块内部按列的方式进行编码存储，通过使用列式存储会有以下好处：

- ==存储效率更高==，因为同一列的数据类型一致，编码效率也会更高
- ==查询效率更高==，利用列式存储的统计信息，可以跳过大量的数据，减少IO压力

ORC和Parquet都是列式存储格式，用于高效地存储和查询大规模数据。

 Parquet + Lzo / ORC + snappy 

- ORC在写入和读取方面更加高效，支持动态结构和嵌套数据类型，适用于存储非常规数据和半结构化数据。
  - 不支持lzo
- Parquet在支持跨平台查询和集成方面表现更好，被广泛应用于多种开源和商业分布式计算和分析系统中。

snappy本身不可切分。但orc和parquet两种存储文件格式因为其结构中都有索引指引，支持随机读取行的功能，因此orc＋snappy和parquet＋snappy都可以进行数据切分。

---

# 离线数仓
## 介绍
集群规模：一台4核6GB，两台2核4GB阿里云服务器(学生机)
数据规模：一天大概1.5~2GB , 用到了两天的数据；（最多2x2x3副本=12G）
ETL流程
1. 抽取主要包含两方面的数据==用户行为日志数据==和==业务数据==
	1. 对于用户行为日志数据（页面数据，动作数据），通过网页埋点得到，，为了避免单层flume采集数据在高峰期阶段容易出现数据积压导致宕机的情况，所以使用双层的flume结构进行数据采集
		1. 第一层：flume采集log文件发送到kafka消息队列（并对其中错误格式的json数据进行一个清洗)
		2. 第二层：使用flume将Kafka消息队列的 用户行为日志数据 存入到HDFS
			1. 写到hdfs 配置roll.size等参数  从源头预防大量小文件的产生
	2. 对于MySQL数据库中的业务数据，我们使用DataX进行全量同步直接到HDFS，Maxwell增量同步到Kafka再用flume采集
 
数仓建模
1.  ODS ==原始==数据层
	1. 存放未经过处理的原始数据（实时数仓中保存在kafka，离线数仓中保存在hive），结构上与源系统保持一致，不做任何转换，与业务侧的数据保持同构
2.  DIM层 公共==维度==层 Dimension 
	1. 基于维度建模理论进行**构建**，存放维度模型中的维度表， 保存一致性维度信息。例如（商品维度表、地区维度表、用户维度表）
3.  DWD ==明细==数据层 Data Warehouse Detail 
	1. 基于维度建模理论进行构建，主要职责是：业务主题的划分、数据规范化，例（交易域、用户域等多个主题）。这一层主要起到缓冲的作用，屏蔽底层影响，尽量还原业务，统一标准存放维度模型中的事实表（具体的业务事件，流量域独立访客事务事实表，交易域下单事务事实），保存各业务过程最小粒度的操作记录。
4.  DWS ==汇总==数据层 Data Warehouse Summary 
	1. 主要职责是划分分析主题、建设各个主题公共统计粒度的汇总表，例如（交易域省份粒度下单各窗口汇总表）
5.  ADS 数据==应用==层 Application Data Service
	1. 为了具体需求而构建的应用层

 

##   Flume

Flume是一个高可靠的，分布式的海量日志采集、聚合和传输的系统；

1. 需求：log日志到Kafka，Kafka到HDFS
2. Flume可以采集文件、kafka、mysql数据库等各种形式源数据，又可以将采集到的数据输出到HDFS、hbase、hive、kafka等众多外部存储系统中。[基于Flume的美团日志收集系统(一)架构和设计](https://tech.meituan.com/2013/12/09/meituan-flume-log-system-architecture-and-design.html)
3. Flume当初的设计初衷就是将数据传送到HDFS中，它更加地注重数据的传输，此外他具有高可靠特性，在Flume中传输的数据会持久化在channel中，除非已确认数据被传输到了下一位置，即sink端，否则不会删除，这个过程是通过事务来控制的，这样的设计使得可靠性非常好。
4. 缺点：就是==没有采集记忆==，当flume在运行时，出现错误，必须终止flume才能解决时，在再次启动flume时，他会重新采集数据，会造成数据的重复。

flume采集系统就是由一个个agent连接起来所形成的一个或简单或复杂的数据传输通道。
Agent 主要有 3 个部分组成，Source、Channel、Sink。 
1. Source 采集组件，用于跟数据源对接，以获取数据；它有各种各样的内置实现；
	1. Taildir Source：断点续传、多目录
	2. kafka source 对接kafka数据源
2. Channel 传输通道组件，用于从source将数据传递到sink
	1. File Channel：将所有事件写到磁盘，数据存储在磁盘中，宕机数据可以保存
	2. Memory Channel:事件数据写到内存中
	3. Kafka Channel：减少Flume的Sink阶段，提高了传输效率 
	4. . Event 。是数据在channel中的封装形式，由Header和 Body两部分组成，Header用来存放属性，为K-V结构，Body用来存放该条数据，为字节数组
3. Sink 下沉组件，用于往下一级agent传递数据或者向最终存储系统传递数据
	1.  HDFS Sink：推送数据到HDFS，可能产生大量小文件问题
---

##  Taildir Source / Kafka Source

Flume中有三种可监控文件或目录的source
1. Exec Source
   1. 通过tail -f命令去tail==一个文件==，然后实时同步日志到sink。但是在 Flume 不运行或者 Shell 命令出错的情况下，数据将会丢失。
2. Spooling Directory Source
   1. 监听一个目录，同步目录中的新文件到sink，被同步完的文件可被立即删除或被打上标记。适合用于==同步新文件==，但不适合对实时追加日志的文件进行监听并同步。
3. Taildir Source
   1. Taildir Source可实时==监控一批文件==，并记录每个文件最新消费位置，agent进程重启后不会有重复消费的问题。支持断点续传。
4. Kafka Source

**为什么选择Kafka Channel**
1. Memory Channel有很大的丢数据风险，而且容量一般。File Channel虽然能缓存更多的消息，但如果缓存下来的消息还没写入Sink，此时Agent出现故障则File Channel中的消息一样不能被继续使用，直到该Agent恢复。
2. 而Kafka Channel容量大，容错能力强。不用配置Sink组件，减少了日志收集层启动的进程数，有效降低服务器内存、磁盘等资源的使用率。

---

## DataX全量同步
1. 为每张全量表编写一个DataX 的 json 配置文件
	1. DataX 的使用十分简单，用户只需根据自己同步数据的数据源和目的地选择相应的 Reader 和Writer，并将 Reader 和Writer 的信息配置在一个 json 文件中，然后执行如下命令 提交数据同步任务即可。
	2. 为每张全量表编写一个 DataX 的 json 配置文件，根据自己同步数据的数据源和目的地选择相应的 Reader 和Writer，并将 Reader 和Writer 的信息配置在json 文件中`gen_import_config.py`
	3. 批量生成json配置文件`gen_import_config.sh`
2. 全量表数据同步脚本`mysql_to_hdfs_full.sh`
3. hdfs创建目标路径 origin_data/gmall/db/2020-06-14
4. 全量表同步 `mysql_to_hdfs_full.sh`之后hdfs会出现15张全量表
---

## 自定义flume拦截器

自定义拦截器的步骤
三步走：
① 实现Interceptor拦截器的接口
② 重写四个方法：
1. initialize 初始化
2. public Event intercept(Event event) 处理单个Event
3. `public List<Event>  intercept(Listevents)` 处理多个event方法，在这个方法中调用Event intercept(Event event)
4. close 方法
	静态内部类，实现interceptor.Builder；返回一个拦截器

**TimeStamp时间戳拦截器**：把事件时间加入到header中，**以事件时间而不是系统处理时间分区，解决日志数据的时间跨天的问题。**

**将获取的ts时间写入拦截器header头，header的key必须是timestamp，因为Flume框架会根据这个key的值识别为时间，写入到HDFS**

① 获取数据，数据都存在body中：使用event.getBody()
② 解析Json：JSON.parseObject(json)
获取时间戳：Long ts = obj.getLong(“ts”);
③将时间戳写入header
Map<String, String> headers = event.getHeaders();
// 要求传入字符串，但解析得到的ts为Long类型，故使用+""，即用字符串拼接方法转换成字符串
headers.put(“timestamp”,ts+"");
④ 数据返回
return event;


## 介绍一下Maxwell

1. Maxwell是一个抓取MySQL变更数据的软件。它会实时监控Mysql数据库的数据变更操作（包括insert、update、delete），并将变更数据以 JSON 格式发送给 Kafka等流数据处理平台。
2. Maxwell的工作原理是实时读取MySQL数据库的二进制日志（Binlog），从中获取变更数据，再将变更数据以JSON格式发送至Kafka等流处理平台
3. 很简单，就是将自己伪装成slave，并遵循MySQL主从复制的协议，从master同步数据。
	1. 启用MySQL Binlog
	2. 创建Maxwell所需数据库和用户

---

## 2 Maxwell如何区分新增数据
1. json有一个字段`type`
2. 新增数据 insert / delete / update
3. 历史数据 bootstrap-insert
4. 第一条type为bootstrap-start和最后一条type为bootstrap-complete的数据，是bootstrap开始和结束的标志，不包含数据，中间的type为bootstrap-insert的数据才包含数据

---

## 2 数据同步工具

1. 基于Select查询的离线、批量同步工具
   1. DataX
   2. Sqoop

2. 基于数据库数据变更日志
   1. Canal / Maxwell
      1. canal 每一条 SQL 只会产生一条日志，如果该条 Sql 影响了多行数据，则已经会通过集合的方式归集在这条日志中。（即使是一条数据也会是数组结构） 需要遍历数组才能拿到数据，maxwell一个json就是一个查询对象
         maxwell 以影响的数据为单位产生日志，即==每影响一条数据就会产生一条日志==。如果想知道这些日志是否是通过某一条 sql 产生的可以通过 xid 进行判断，相同的 xid 的日志来 自同一 sql。
      2. Maxwell 有一个亮点功能，就是 canal 只能抓取最新数据，对已存在的历史数据没有办 法处理。而 Maxwell 有一个 ==bootstrap== 功能，可以直接引导出完整的历史数据用于初 始化，非常好用。
      3. Maxwell 比 Canal 更加轻量级
   2. Flink CDC

---

## [0] 为什么使用Flume+Kafka

**flume 多数据源 + kafka  缓冲 与 解耦合**

- 生产环境中，往往是读取日志进行分析，而这往往是多数据源的，如果Kafka构建多个生产者使用文件流的方式向主题写入数据再供消费者消费的话，无疑非常的不方便。
- 如果Flume直接对接实时计算框架，当数据采集速度大于数据处理速度，很容易发生数据堆积或者数据丢失，而kafka可以当做一个消息缓存队列；
- Kafka属于中间件，一个明显的优势就是使各层解耦。因此数据从数据源到Flume再到Kafka时，数据一方面可以同步到HDFS做离线计算，另一方面可以做实时计算，可实现数据多分发。
---

## 2 Spark和Hive对比

- Hive是基于Hadoop的一个==数据仓库工具==，可以将结构化的数据文件映射为一张表，并提供类SQL查询功能。
- Spark 是一种基于内存的快速、通用、可扩展的大数据分析==计算引擎==
要看实际使用场景。
1. Hive：
   1. 大数据存储
   2. 通过sql方式进行MapReduce操作，降低大数据使用门槛，成本低
   3. 用途：==数据存储和清洗==，处理==海量数据==，比如一个月、一个季度、一年的数据量，依然可以处理，虽然很慢。
2. Spark SQL：
   1. 基于内存操作，速度快
   2. 流式计算。
   3. 用途：数据清洗和流式计算，上述情况下Spark SQL不支持，无法处理，因为其基于内存，量级过大承受不住，并且性价比不如Hive高。

---

## 2 Hive on Spark / Spark on Hive 

实际应用中，经常把二者 结合起来使用。Spark和Hive结合和使用的方式

* Hive on Spark（离线数仓使用）
  * 如果用Hive on Mapreduce太慢了（十倍）
  * Hive 既作为存储元数据又负责 SQL 的解析优化，语法是 ==HQL 语法==，执行引擎变成了 Spark，Spark 负责采用 RDD 执行。

* Spark on Hive :
  * Spark本身只负责数据计算处理，并不负责数据存储。Hive 只存储数据，==Spark 负责 SQL 解析优化==，语法是 Spark SQL语法，Spark 负责采用 RDD 执行。


---


## kafka 分区数怎么计算确定

1. 创建一个只有1个分区的topic
2. 测试这个topic的producer吞吐量和consumer吞吐量。
3. 假设他们的值分别是Tp和Tc，单位可以是MB/s。
4. 然后假设总的目标吞吐量是Tt，那么分区数 = Tt / min（Tp，Tc）
 

---
## atlas元数据管理

- 元数据：数据结构信息，在数据仓库中指的是库、表、字段等；
- 元数据管理的意义：让开发人员和业务人员快速的了解数据的关系以及数据本身的含义；精准的定位需要查找的数据，从而减少数据的研究成本，提高效率，减少熟悉业务的时间减少

| 元数据分类 | 支持对元数据进行分类管理，例如个人信息，敏感信息等           |
| :--------- | :----------------------------------------------------------- |
| 元数据检索 | 可按照元数据类型、元数据分类进行检索，支持全文检索           |
| 血缘依赖   | 支持表到表和字段到字段之间的血缘依赖，便于进行问题回溯和影响分析等 |

Atlas安装需要集成 Kafka和HBase和 Solr，

1. Kafka用于将元数据导入Atlas；
2. Atlas采用HBase存储元数据；
3. 采用Solr来建立索引 方便的访问元数据；
   1. Solr是一个开源的搜索平台。Solr的主要功能是提供强大而高效的全文搜索和实时分析，它可以轻松地将数据索引和搜索功能添加到应用程序中。

现在可以启动Atlas了，需要将

1. 自带脚本`import-hive.sh`可完成 Hive 元数据的 初次全量导入
2. 执行SQL 语句之后，登录Atlas WEB21000页面就可以看到相关，就能看到血缘关系了

---
## 5、数据管理模块
**Atlas元数据管理**

元数据的管理的意义：让开发人员和业务人员快速的了解数据的关系以及数据本省的含义；精准的定位需要查找的数据，从而减少数据的研究成本，提高效率，减少熟悉业务的时间。

Atlas提供 **元数据分类、元数据检索、构建血缘**关系的功能。

**数据质量管理**

数据质量管理（Data Quality Management），是指对数据生命周期的每个阶段里可能引发的各类**数据质量问题，进行识别、度量、 监控、预警等一系列管理活动，并通过改善和提高组织的管理水平使得数据质量获得进一步提高**。

数据质量的评价标准包括：唯一性；完整性；准确性；合法性；时效性；

在本数仓中进行了

- ODS 层数据量，每日环比和每周同比变化不能超过一定范围    （准确性）
- DIM 层id 不能有空值，重复值；  （完整性、唯一性）
- DWD 层id 不能有空值，重复值 ；（完整性、唯一性）
  的指标监控
---


##  订单业务数仓工作流程

以订单业务为例：

1. 从ODS层开始，是最接近数据源中数据的一层，为了考虑后续可能需要追溯数据问题，因此对于这一层就不建议做过多的数据清洗工作，原封不动地接入原始数据即可，至于数据的去噪、去重、异常值处理等过程可以放在后面的DWD层来做。

   1. 订单明细表 / 订单明细活动关联表 / 订单表 / 

2. 到DWD层首先对订单信息进行清洗和脱敏；得到订单事实表

   1. 订单明细表 
      1. left join  订单表(省份id)  
      2. left join 订单明细活动关联表（活动id，活动规则id）
      3. left join 订单明细优惠券关联表（优惠券id）
      4. left join 编码字典表（全量表）（编号，编码名称）

3. 到达DWS宽表层：与DWD层的其他事实表（如评论事实表）一同构建为用户行为宽表；进行数据汇总

   1. 交易域省份粒度订单最近 1 日汇总表

      ```sql
      select
          province_id,
          count(distinct(order_id)) order_count_1d,
          sum(split_original_amount) order_original_amount_1d,
          sum(nvl(split_activity_amount,0)) activity_reduce_amount_1d,
          sum(nvl(split_coupon_amount,0)) coupon_reduce_amount_1d,
          sum(split_total_amount) order_total_amount_1d,
          dt
      from ${APP}.dwd_trade_order_detail_inc
      group by province_id,dt
      ```

   2. 与维度表关联进行维度建模

      ```sql
      select
          id,
          province_name,
          area_code,
          iso_code,
          iso_3166_2
      from ${APP}.dim_province_full
      where dt='$do_date'
      ```


4、最后到达ADS层；进行指标分析；可进行用户行为漏斗分析；

> 漏斗分析:浏览首页->浏览商品详情页->加入购物车->下单->支付

---


## 为什么要设计DWS宽表

DWS层成为宽表层，这两层的设计思想大致相同，通过以下案例进行阐述。

1）问题引出：两个需求，统计每个省份订单的个数、统计每个省份订单的总金额

2）处理办法：都是将省份表和订单表进行join，group by省份，然后计算。同样数据被计算了两次，实际上类似的场景还会更多。

那怎么设计能避免重复计算呢？

针对上述场景，可以设计一张地区宽表，其主键为地区ID，字段包含为：下单次数、下单金额、支付次数、支付金额等。上述所有指标都统一进行计算，并将结果保存在该宽表中，这样就能有效避免数据的重复计算。

3）总结：

（１）需要建哪些宽表：**基本上以维度为基准**。

（２）宽表里面的字段：是站在不同维度的角度去看事实表，重点关注事实表聚合后的度量值。

 


## 分析过最难的指标

**最近** **7** **天连续** **3** **天活跃用户数**

1）查询出最近7天的活跃用户，并对用户活跃日期进行排名

2）计算用户活跃日期及排名之间的差值

3）对同用户及差值分组，统计差值个数

4）将差值相同个数大于等于3的数据取出，然后去重(group by用户；一个用户可能多个三天活跃)，即为连续3天及以上活跃的用户

![image-20220426090015241](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171529990.png)

 

# Flink项目面试题

## 介绍

ETL流程
1. 抽取主要包含两方面的数据==用户行为日志数据==和==业务数据==
2. 对于用户行为日志数据（页面数据，动作数据），通过网页埋点得到
	1. flume采集log文件发送到kafka消息队列（并对其中错误格式的json数据进行一个清洗)
3. 对于MySQL数据库中的业务数据，我们使用Maxwell增量同步到Kafka
 
1. ODS 层：flume采集到的用户行为日志，和Maxwell从mysql采集到的业务日志
2. DIM维表：
	1. 使用FlinkCDC读取mysql的配置表信息，作为广播流再将主流字段过滤得到维表写入Hbase
3. DWD数据明细层：
	1. 对日志数据的处理，主要使用状态编程，UV
	2. 对业务数据的处理。 FlinkSQL ，交易域加购事务事实表
4. DWS
	1. 关联维表。主要职责是划分分析主题、建设各个主题公共统计粒度的汇总表，例如（交易域省份粒度下单各窗口汇总表），将结果写入ClickHouse
5. 不落盘,实质上是接口模块中查询ClickHouse的SQL语句
---

## DIM
 **思考**
如果增加维表，需要修改代码、重新编译、打包、上传、重启任务  
改进：
1. 不修改代码、只重启任务
    1. 配置信息中保存需要的维表信息,配置信息只在程序启动的时候加载一次
2. 不修改代码、不重启任务
    1. 监控配置信息:一旦配置信息增加了数据,可以立马获取到 MySQLBinlog:FlinkCDC监控直接创建流
        1. 将配置信息处理成广播流：缺点 如果配置信息过大,冗余太多
        2. 按照表名进行KeyBy处理：缺点 -> 有可能产生数据倾斜
根据MySQL table_process的数据建表，将主流数据写入表
1. 过滤数据:过滤出所需要的维表数据
2. 过滤条件:在代码中给定十几张维表的表名

==为什么要用广播流？==因为有多个并行度，每个并行度可能只会包含配置表的一部分信息，导致比配失败！！！

1. 环境准备
    
    ```java
       StreamExecutionEnvironment env = StreamExecutionEnvironment.getExecutionEnvironment();
       // 设置作业的并行度 = Kafka主题的分区数 
       env.setParallelism(1); 
    ```
    
2. 开启CheckPoint
    
    ```java
    // 检查点间隔时间，5 分钟，单位为毫秒。
    env.enableCheckpointing(5 * 60000L, CheckpointingMode.EXACTLY_ONCE);
    // 检查点超时时间，10 分钟，单位为毫秒。
    env.getCheckpointConfig().setCheckpointTimeout(10 * 60000L);
    // 同时进行最大检查点数量，2
    env.getCheckpointConfig().setMaxConcurrentCheckpoints(2);
    // 重启策略， 最多重启3次。固定延迟5秒
    env.setRestartStrategy(RestartStrategies.fixedDelayRestart(3, 5000L));
    ```
    
3. 设置状态后端
    
    ```java
    env.setStateBackend(new HashMapStateBackend());
    env.getCheckpointConfig().setCheckpointStorage("hdfs://hadoop102:8020/211126/ck");
    System.setProperty("HADOOP_USER_NAME", "atguigu");
    ```
    
4. 提取kafka业务 主流 DataStreamSource< String >
    
    1. 引入Flink和Kafka依赖库，`flink-connector-kafka`
        
    2. 创建 `FlinkKafkaConsumer` 实例。指定读取的topic，kafka的地址，groupId
        
    3. 自定义序列化的方式`KafkaDeserializationSchema`来实现自定义返回数据的结构
        
        1. `SimpleStringSchema())`会报空指针异常，重写一个`KafkaDeserializationSchema`处理空值，重写`deserialize`
        2. 重写`deserialize`方法，将字节数据转换为字符串。
5. 主流数据结构转换 SingleOutputStreamOperator< JSONObject >
    
    1. `flatMap`。filter用来过滤，map用来转换，==flatMap==直接完成两项。输出是一个Collector
        
    2. 将数据转换为JSONObject格式(fatjson，parseObject)。fastjson的parseObject()，JSON是一个抽象类，JSON中有一个静态方法parseObject（String text），将text解析为一个JSONObject对象并返回
        
    3. 保留新增、变化以及初始化数据
        
    4. 过滤掉非JSON数据。
        
        ```java
        SingleOutputStreamOperator<JSONObject> filterJsonObjDS = kafkaDS.flatMap(new FlatMapFunction<String, JSONObject>() {
            @Override
            public void flatMap(String value, Collector<JSONObject> out) throws Exception {
                try {
                    JSONObject jsonObject = JSON.parseObject(value);
                    String type = jsonObject.getString("type");
                    if ("insert".equals(type) || "update".equals(type) || "bootstrap-insert".equals(type)) {
                        out.collect(jsonObject);
                    }
                } catch (Exception e) {
                    System.out.println("发现脏数据：" + value);
                }
            }
        });
        ```
        
6. 使用FlinkCDC读取MySQL配置信息表创建==配置流==
    
    1. 导入依赖。flink-connector-jdbc flink-connector-mysql-cdc flink-table-api-java-bridge
        
    2. 构造一个MySqlSource类，写入mysql配置信息
        
        1. `MySqlSource.<String>builder()`，库名，表名
            
        2. 配置表
            
            1. 总共46张表，包含五个字段。一行表示，mysql原始数据哪张表，执行什么类型的操作，需要输出到DIM哪里，以及要输出哪些字段；**
                
                1. sourceTable:主流中的数据表名
                    
                2. sinkTable:Phoenix中的维表表名
                    
                3. columns:建表使用的字段名、过滤主流数据字段
                    
                4. sinkPk:建表使用的主键
                    
                5. sinkExtend:建表使用的扩展字段

            2. 配置表里面只会有维度表信息，**手动维护**，在配置表中创建一个表，然后在Hbase中创建这张表
                
            3. 方法
                
                1. Mysql 中创建数据库gmall_config ，然后建表gmall_config.table_process，**并开启Binlog**
                    
                2. 在MySQL配置文件中增加 gmall_config 开启Binlog（FlinkCDC监控）
                    
    3. CDC读到的 string：
        
        ```json
        {"before":null,"after":{"source_table":"base_trademark","sink_table":"dim_base_trademark","sink_columns":"id,tm_name","sink_pk":"id","sink_extend":""},"source":{"version":"1.5.4.Final","connector":"mysql","name":"mysql_binlog_source","ts_ms":1652513039549,"snapshot":"false","db":"gmall-211126-config","sequence":null,"table":"table_process","server_id":0,"gtid":null,"file":"","pos":0,"row":0,"thread":null,"query":null},"op":"r","ts_ms":1652513039551,"transaction":null}
        ```
        
    4. 将自定义源（MySqlSource）转化为数据流（mysqlSourceDS）
        
        ```java
        DataStreamSource<String> mysqlSourceDS = env.fromSource(mySqlSource,
        		WatermarkStrategy.noWatermarks(),
        		"MysqlSource");
        ```
        
7. 配置流处理为广播流
    
    1. 设置一个map状态描述器`mapStateDescriptor`，key为主键String，value为`TableProcess`类（上面配置表的五个列名）
    2. 调用broadcast方法，转换为广播流 `mysqlSourceDS.broadcast(mapStateDescriptor)`
    3. 连接主流`JSONObject`与广播流`String`
        
        ```java
        BroadcastConnectedStream<JSONObject, String> connectedStream = filterJsonObjDS.connect(broadcastStream);
        ```
        
8. 处理连接流，根据配置信息处理主流数据BroadcastProcessFunction
    
    1. **广播流处理方法 processBroadcastElement**
        
        1. 转为jsonObject，提出==after字段==，创建TableProcess类
            
            ```json
            {"source_table":"base_trademark","sink_table":"dim_base_trademark","sink_columns":"id,tm_name","sink_pk":"id","sink_extend":""}
            ```
            
        2. 处理特殊字段，sinkPk为主键，没有主键的就叫id
            
        3. 拼接SQL
            
        4. 编译SQL `connection.prepareStatement(createTableSql.toString())`
            
        5. 执行SQL,建表 `preparedStatement.execute();`
            
        6. 写入状态，广播出去（**==k是来源表的表名，V是TableProcess类==**）主流数据处理方法 processElement
            
            ```java
            broadcastState.put(tableProcess.getSourceTable(), tableProcess)；
            ```
            
    2. **主流的处理方法 processElement**
        
        1. 主流本身就是JSONObject，maxwell格式的
            
            ```json
            {"database":"gmall-flink","table":"base_trademark","type":"update","ts":1652499176,"xid":188,"commit":true,"data":{"id":13,"tm_name":"atguigu","logo_url":"/bbb/bbb"},"old":{"logo_url":"/aaa/aaa"}}
            ```
            
        2. 获取广播流的配置数据 `ctx.getBroadcastState(mapStateDescriptor)`
            
        3. 获取主流table名字，去==**广播变量**==找TableProcess这个类
            
            1. `value.getString("table")` 提出table字段的名字
        4. 过滤==data==字段，只保留维表需要的==输出字段==（id，tm_name）。将主流data字段和广播流的tableProcess类的SinkColumns字段做对比，删除主流多余的字段
            
        5. 补充一个主流的字段==sinkTable==
            
            ```json
            {"database":"gmall_flink","table":"base_trademark","type":"update","ts":1652499176,"xid":188,"commit":true,"data":{"id":13,"tm_name":"atguigu"},"old":{"logo_url":"/aaa/aaa"},"sinkTable":"dim_base_trademark"}
            ```
            
9. 将数据写出到HBase
    
    1. 不确定字段的个数；需要自定义DimSinkFunction继承RichSinkFunction
    2. open
        1. 任务启动时执行一次。连接池创建工具类DruidDSUtil，创建连接池，设置驱动全类名
    3. invoke
        1. 获取到表名sinkTable，data字段
        2. 获取数据类型，如果是updata，删除Redis中的数据
        3. 拼接SQL语句:upsert into db.tn(id,name,sex) values('1001','zhangsan','male')
        4. 预编译，执行SQL
    4. 输出结果
        
        ```json
        	最后的输出：{"sinkTable":"dim_base_trademark","database":"gmal1_flink","xid":1358,"data":{"tm_name":"atguigu","id":12},"commit":true,"type":"insert","table":"base_trademark","ts":1652518734} 
        ```


## flinkCDC

CDC是Change Data Capture(变更数据获取)的简称。核心思想是，监测并捕获数据库的变动（包括数据或数据表的插入、更新以及删除等），将这些变更按发生的顺序完整记录下来，写入到消息中间件中以供其他服务进行订阅及消费。

**CDC种类**

1.基于查询的CDC

例如：Sqoop、Kafka 、JDBC source等产品。
特点：基于批处理，不能捕获到所有数据的变化、高延迟、需要查询数据库，会增加数据库压力

2.基于**binlog** 的CDC

例如：Maxwell、Canal、**Debezium**
特点：基于streaming模式、能捕捉所有数据的变化、低延迟、不会增加数据库压力。

1. 节省消息中间件
2. 不能开窗？

因为 Flink 相对 Kafka Streams 而言，有如下优势：

- Flink 的算子和 SQL 模块更为成熟和易用
- Flink 作业可以通过调整算子并行度的方式，轻松扩展处理能力
- Flink 支持高级的状态后端（State Backends），允许存取海量的状态数据
- Flink 提供更多的 Source 和 Sink 等生态支持
- Flink 有更大的用户基数和活跃的支持社群，问题更容易解决
- Flink 的开源协议允许云厂商进行全托管的深度定制，而 Kafka Streams 只能自行部署和运



## UV指标

1. 过滤 last_page_id 不为 null 的数据 
	1. 独立访客数据对应的页面必然是会话起始页面，last_page_id 必为 null。过滤last_page_id != null 的数据，减小数据量，提升计算效率。 
2. 筛选独立访客记录 
	1. 运用 Flink 状态编程，为每个 mid 维护一个键控状态 `ValueState`，记录末次登录日期 `lastVisitState`。 如果末次登录日期为 null 或者不是今日，则本次访问是该 mid 当日首次访问，保留数据，将末次登录日期更新为当日。否则不是当日首次访问，丢弃数据。 
3. 状态存活时间设置 
	1. 如果保留状态，第二日同一 mid 再次访问时会被判定为新访客，如果清空状态，判定结果相同，所以只要时钟进入第二日状态就可以清空。 设置状态的 TTL 为 1 天，更新模式为 OnCreateAndWrite，表示在创建和更新状态时重置状态存活时间。如：2022-02-21 08:00:00 首次访问，若 2022-02-22 没有访问记录，则 2022-02-22 08:00:00 之后状态清空。

## DWS优化 -旁路缓存

我们在DWS（数仓明细层）会进行关联维表操作，实际上就是在流中的dwd中的id（例如省份id，用户id，活动id），查询存储在HBase中的维度表（地区维度表，用户维度表，商品维度表）。尽管HBase客户端会有缓存，查询时间还是不理想，hbase的查询速度也是不及流之间的join。外部数据源的查询常常是流式计算的性能瓶颈，以决定进行一个维度查询的优化。

**1 旁路缓存**

旁路缓存模式是一种非常常见的按需分配缓存模式。所有请求优先访问缓存，若缓存命中，直接获得数据返回给请求者。如果未命中则查询数据库，获取结果后，将其返回并写入 缓存以备后续请求使用。

我们的优化方向主要针对两点

1. 缓存要设过期时间，不然冷数据会常驻缓存，浪费资源。 

2. 要考虑维度数据是否会发生变化，如果发生变化要主动清除缓存


**2 缓存选择**

一般两种：堆缓存或者独立缓存服

1. 堆缓存，从性能角度看更好，毕竟访问数据路径更短，减少过程消耗。但是管理性差，其他进程无法维护缓存中的数据（我们要==更新维表的数据==），如Flink的状态。

2. 独立缓存服务：读立缓存服务便于维护和扩展，对于数据会发生变化且数据量很大的场景更加适 用，此处选择独立缓存服务，将 redis 作为缓存介质。


**3 RedisKey的设计**

关键是考虑到过期时间，所以为什么选string不选hash

1. Hash: TableName id
	1. Hash 先是 tablename 为外层 key， 里面还是单条数据的k-v 类型，要给==每条==数据设置过期时间，但redis中针对Hash表的过期时间是针对外层key，也就是==Tablename==整张表，这样表中只要有一条热数据，其他的冷数据就都会被保留
3. String: TableName+id
	1. 根据当前==每一条独立数据设置过期时间==，表名+id `DIM:DIM_BASE_TRADEMARK:18`


**4 具体实现**

[DimUtil.java](E:\HDU\Java\Project\DW_Flink\Code\gmall-flink-211126\gmall-realtime\src\main\java\com\atguigu\utils\DimUtil.java)

1. 因为存在多表，不能写死； 所以封装了一个函数：`getDimInfo`，用来获取`JSONObject`
2. 查询结果JSONObject获取jedis连接
3. 用redisKey查询 
   ```java
   Jedis jedis = JedisUtil.getJedis();
   String redisKey = "DIM:" + tableName + ":" + key;
   String dimJsonStr = jedis.get(redisKey);
   ```
4. 如果查询查到
	1. 重置过期时间，归还连接，返回维度数据（==String类型的json转化为JSONObject==）
		`{"ID": "13", "TM_NAME":"SHANGHAI"}` 
5. 如果没查到，将从Phoenix查询到的数据写入Redis
	1. 拼接查询语句，查询数据，将从Phoenix查询到的数据（` List<JSONObject>`）`get(0)`写入Redis，设置过期时间，归还连接
	   ```java
	   //拼接Phoenix的查询SQL语句
	   String querySql = "select * from " + GmallConfig.HBASE_SCHEMA + "." + tableName + " where id='" + key + "'";
	   //查询数据
	   List<JSONObject> queryList = JdbcUtil.queryList(connection, querySql, JSONObject.class, false);
	   //将从Phoenix查询到的数据写入Redis
	   JSONObject dimInfo = queryList.get(0);
	   jedis.set(redisKey, dimInfo.toJSONString());
	   //设置过期时间
	   jedis.expire(redisKey, 24 * 60 * 60);
	   //归还连接
	   jedis.close();
	   
	   ```

6. 写入HBase
	1. 就是往HBase 写入数据，如果是更新，先删除 redis中的缓存，再往hbase中写入数据；

**5 缓存一致性**
1. maxwell读取为updata信息，则先删除redis里面的数据，再写入Hbase
2. 先更新数据库 + 再删除缓存
	1. 因为缓存的写入通常要远远快于数据库的写入，所以在实际中很难出现请求 B 已经更新了数据库并且删除了缓存，请求 A 才更新完缓存的情况

---

## 异步I/O优化

flink在做实时处理时，有时候需要和外部数据交互，但是通常情况下这个交互过程是同步的，这样就会产生大量的等待时间；而异步操作可以在单个函数实例中同时处理多个请求，并且同时接收相应。这样等待时间就平均分摊到了多个请求上，大大减少了请求的等待时长，可以提高实时处理的吞吐量。

在异步模式下，将IO操作异步化，单个并行可以连续发送多个请求，哪个请求先返回就先处理，从而在连续的请求间不需要阻塞式等待，大大提高了流处理效率

**1 实现**
异步方法核心的类是 AsyncDataStream，这个类有两个方法一个是有序等待（orderedWait），一个是无序等待（unorderedWait）。
1. **无序等待**（unorderedWait）
   1. 后来的数据，如果异步查询速度快，可以超过先来的数据，这样性能会更好一些，但是会有乱序出现。
   2. 数据流（来自kafka的事实表数据流）、**一个继承异步方法类 RichAsyncFunction的实例**、超时时间（100s）和超时时间单位 4个参数。
   3. **继承异步方法类 RichAsyncFunction**，封装了一个**带泛型**的维度异步查询的函数类DimAsyncFunction（因为还是有**多个维表**的存在）
   4. 主要实现两个方法:
      1. `open`用于初始化异步连接池。
      2. `asyncInvoke`方法是核心方法，**里面的操作必须是异步的**，如果你查询的数据库有异步api也可以用线程的异步方法。如果没有异步方法，就要自己利用线程池等方式实现异步查询。方法**内部开启线程提交任务**（异步）：1、根据 表名+id  查询维度数据（先从redis中查，查不到再从habse中查，因为配置了旁路缓存优化）2、补充维度信息（将维度字段加入到输入数据中）  3、将数据输出

2. 有序等待（orderedWait）
   1. 严格保留先来后到的顺序，所以后来的数据即使先完成也要等前面的数据。所以性能会差一些。
3. 自定义一个线程池`ThreadPoolUtil`，用于异步查询
   1. （增大吞吐量最有效的是 增大并行度 但是会带来非常大的资源消耗）
      实现异步I/O有客户端（查询的库可提供异步请求的客户端） 和 线程池两种方式进行异步I/O；
      我们要查两个：hbase和redis，用客户端不方便，所以采用线程池的方式
   2. 采用**双重校验的方式初始化一个线程池**，把**维表的查询操作托管给单独的线程池完成**，这样不会因为某一个查询造成阻塞，单个并行可以连续发送多个请求，提高并发效率。
---

## DIM 主流广播流

**1️ 介绍**
3. 公共维度层，依据是维度建模理论，该层存储维度模型的维度表
4. DIM层的数据存储在 HBase 表中

**2️ 思考**

如果增加维表，需要修改代码、重新编译、打包、上传、重启任务
改进：

1. 不修改代码、只重启任务
	   1. 配置信息中保存需要的维表信息,配置信息只在程序启动的时候加载一次
2. 不修改代码、不重启任务
   1. 监控配置信息:一旦配置信息增加了数据,可以立马获取到 MySQLBinlog:FlinkCDC监控直接创建流
	      1. 将配置信息处理成广播流：缺点 如果配置信息过大,冗余太多
	      2. 按照表名进行KeyBy处理：缺点 -> 有可能产生数据倾斜

根据MySQL table_process的数据建表，将主流数据写入表 

1. 过滤数据:过滤出所需要的维表数据
2. 过滤条件:在代码中给定十几张维表的表名

==为什么要用广播流？==因为有多个并行度，每个并行度可能只会包含配置表的一部分信息，导致比配失败！！！

1. 环境准备
   ```java
      StreamExecutionEnvironment env = StreamExecutionEnvironment.getExecutionEnvironment();
      // 设置作业的并行度 = Kafka主题的分区数 
      env.setParallelism(1); 
   ```

2. 开启CheckPoint
   ```java
   // 检查点间隔时间，5 分钟，单位为毫秒。
   env.enableCheckpointing(5 * 60000L, CheckpointingMode.EXACTLY_ONCE);
   // 检查点超时时间，10 分钟，单位为毫秒。
   env.getCheckpointConfig().setCheckpointTimeout(10 * 60000L);
   // 同时进行最大检查点数量，2
   env.getCheckpointConfig().setMaxConcurrentCheckpoints(2);
   // 重启策略， 最多重启3次。固定延迟5秒
   env.setRestartStrategy(RestartStrategies.fixedDelayRestart(3, 5000L));
   ```

3. 设置状态后端

   ```java
   env.setStateBackend(new HashMapStateBackend());
   env.getCheckpointConfig().setCheckpointStorage("hdfs://hadoop102:8020/211126/ck");
   System.setProperty("HADOOP_USER_NAME", "atguigu");
   ```

4. 提取kafka业务 主流 DataStreamSource< String >
	 1. 引入Flink和Kafka依赖库，`flink-connector-kafka`
	 2. 创建 `FlinkKafkaConsumer` 实例。指定读取的topic，kafka的地址，groupId
	 3. 自定义序列化的方式`KafkaDeserializationSchema`来实现自定义返回数据的结构
		 1. `SimpleStringSchema())`会报空指针异常，重写一个`KafkaDeserializationSchema`处理空值，重写`deserialize`
		 2. 重写`deserialize`方法，将字节数据转换为字符串。
5. 主流数据结构转换 SingleOutputStreamOperator< JSONObject >
	1. `flatMap`。filter用来过滤，map用来转换，==flatMap==直接完成两项。输出是一个Collector
	2. 将数据转换为JSONObject格式(fatjson，parseObject)。fastjson的parseObject()，JSON是一个抽象类，JSON中有一个静态方法parseObject（String text），将text解析为一个JSONObject对象并返回 
	3. 保留新增、变化以及初始化数据
	4. 过滤掉非JSON数据。

      ```java
      SingleOutputStreamOperator<JSONObject> filterJsonObjDS = kafkaDS.flatMap(new FlatMapFunction<String, JSONObject>() {
          @Override
          public void flatMap(String value, Collector<JSONObject> out) throws Exception {
              try {
                  JSONObject jsonObject = JSON.parseObject(value);
                  String type = jsonObject.getString("type");
                  if ("insert".equals(type) || "update".equals(type) || "bootstrap-insert".equals(type)) {
                      out.collect(jsonObject);
                  }
              } catch (Exception e) {
                  System.out.println("发现脏数据：" + value);
              }
          }
      });
      ```

6. 使用FlinkCDC读取MySQL配置信息表创建==配置流==
	1. 导入依赖。flink-connector-jdbc flink-connector-mysql-cdc flink-table-api-java-bridge
	2. 构造一个MySqlSource类，写入mysql配置信息
		1. `MySqlSource.<String>builder()`，库名，表名
		2. 配置表
			1. 总共46张表，包含五个字段。一行表示，mysql原始数据哪张表，执行什么类型的操作，需要输出到DIM哪里，以及要输出哪些字段；
				1. sourceTable:主流中的数据表名
				2. sinkTable:Phoenix中的维表表名
				3. columns:建表使用的字段名、过滤主流数据字段
				4. sinkPk:建表使用的主键
				5. sinkExtend:建表使用的扩展字段

                      | source_table  | sink_table        | sink_columns                                    | sink_pk | sink_extend |
                      | ------------- | ----------------- | ----------------------------------------------- | ------- | ----------- |
                      | base_province | dim_base_province | id,name,region_id,area_code,iso_code,iso_3166_2 |         |             |
                      | base_region   | dim_base_region   | id,region_name                                  | id      |             |
		3. 配置表里面只会有维度表信息，**手动维护**，在配置表中创建一个表，然后在Hbase中创建这张表
			1. 方法
				1. Mysql 中创建数据库gmall_config ，然后建表gmall_config.table_process，**并开启Binlog**
				2. 在MySQL配置文件中增加 gmall_config 开启Binlog（FlinkCDC监控）

     3. CDC读到的 string：	

           ```json
           {"before":null,"after":{"source_table":"base_trademark","sink_table":"dim_base_trademark","sink_columns":"id,tm_name","sink_pk":"id","sink_extend":""},"source":{"version":"1.5.4.Final","connector":"mysql","name":"mysql_binlog_source","ts_ms":1652513039549,"snapshot":"false","db":"gmall-211126-config","sequence":null,"table":"table_process","server_id":0,"gtid":null,"file":"","pos":0,"row":0,"thread":null,"query":null},"op":"r","ts_ms":1652513039551,"transaction":null}
           ```

     4. 将自定义源（MySqlSource）转化为数据流（mysqlSourceDS）	

         ```java
         DataStreamSource<String> mysqlSourceDS = env.fromSource(mySqlSource,
         		WatermarkStrategy.noWatermarks(),
         		"MysqlSource");
         ```

7. 配置流处理为广播流

   1. 设置一个map状态描述器`mapStateDescriptor`，key为主键String，value为`TableProcess`类（上面配置表的五个列名）
   2. 调用broadcast方法，转换为广播流 `mysqlSourceDS.broadcast(mapStateDescriptor)`
   3. 连接主流`JSONObject`与广播流`String`
	    ``` java
	    BroadcastConnectedStream<JSONObject, String> connectedStream = filterJsonObjDS.connect(broadcastStream);
	    ```
8. 处理连接流，根据配置信息处理主流数据BroadcastProcessFunction
	1. **广播流处理方法 processBroadcastElement**
        1. 转为jsonObject，提出==after字段==，创建TableProcess类
            ``` json
            {"source_table":"base_trademark","sink_table":"dim_base_trademark","sink_columns":"id,tm_name","sink_pk":"id","sink_extend":""}
            ```

        3. 处理特殊字段，sinkPk为主键，没有主键的就叫id

        4. 拼接SQL

        5. 编译SQL `connection.prepareStatement(createTableSql.toString())`

        6. 执行SQL,建表 `preparedStatement.execute();`

        7. 写入状态，广播出去（**==k是来源表的表名，V是TableProcess类==**）主流数据处理方法 processElement

	        ```java
	        broadcastState.put(tableProcess.getSourceTable(), tableProcess)；
	        ```

   2. **主流的处理方法 processElement**

        1. 主流本身就是JSONObject，maxwell格式的

           ```json
           {"database":"gmall-flink","table":"base_trademark","type":"update","ts":1652499176,"xid":188,"commit":true,"data":{"id":13,"tm_name":"atguigu","logo_url":"/bbb/bbb"},"old":{"logo_url":"/aaa/aaa"}}
           ```

        2. 获取广播流的配置数据 `ctx.getBroadcastState(mapStateDescriptor)`

        3. 获取主流table名字，去==**广播变量**==找TableProcess这个类
	        1.  `value.getString("table")` 提出table字段的名字

        5. 过滤==data==字段，只保留维表需要的==输出字段==（id，tm_name）。将主流data字段和广播流的tableProcess类的SinkColumns字段做对比，删除主流多余的字段

        6. 补充一个主流的字段==sinkTable==

           ```json
           {"database":"gmall_flink","table":"base_trademark","type":"update","ts":1652499176,"xid":188,"commit":true,"data":{"id":13,"tm_name":"atguigu"},"old":{"logo_url":"/aaa/aaa"},"sinkTable":"dim_base_trademark"}
           ```
           
           <img src="https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202305252158960.png" alt="image-20230523150916393" style="zoom:50%;" />
           

9. 将数据写出到HBase
	1. 不确定字段的个数；需要自定义DimSinkFunction继承RichSinkFunction
	2. open
		1. 任务启动时执行一次。连接池创建工具类DruidDSUtil，创建连接池，设置驱动全类名
	3. invoke
		1. 获取到表名sinkTable，data字段
		2. 获取数据类型，如果是updata，删除Redis中的数据
		3. 拼接SQL语句:upsert into db.tn(id,name,sex) values('1001','zhangsan','male')
		4. 预编译，执行SQL
	4.  输出结果
	    ``` json
			最后的输出：{"sinkTable":"dim_base_trademark","database":"gmal1_flink","xid":1358,"data":{"tm_name":"atguigu","id":12},"commit":true,"type":"insert","table":"base_trademark","ts":1652518734} 
		```
		
---

## [0] 存储方案

实时数仓在设计中不同于离线数仓在各层级使用同种储存方案，比如都存储在 Hive中的策略。

首先对中间过程的表，采用将结构化的数据通过消息队列存储和高速 KV 存储混合的方案。

实时计算引擎可以通过监听消息消费消息队列内的数据，进行实时计算。而在高速 KV 存储上的数据则可以用于快速关联计算，比如维度数据。 

其次在应用层上，针对数据使用特点配置存储方案直接写入。避免了离线数仓应用层同步数据流程带来的处理延迟。 为了解决不同类型的实时数据需求，合理的设计各层级存储方案，我们调研了美团内部使用比较广泛的几种存储方案。


##  如果主流先来 而配置表还没来，那么就会造成丢数据的情况

两个流连接之后，调用process()方法 传入一个BroadcastProcessFunction进行处理，

processBroadcastElement()方法 处理广播流的数据

processElement() 处理主流数据 处理主流的数据

在这两个方法**之前**一定会先执行的一个方法：open()方法，在这个方法里面先jdbc查询一次MySQL ，并保存到一个map中，之后处理主流数据**先查看map中是否存在相应的数据**；即可解决这个问题

**完全不能接受丢数据：接着查mysql，有对应数据再进行处理**

> 等待一点时间，继续处理；可能会丢

## inteval join
批处理有两种方式处理两个表的Join，一种是基于排序的Sort-Merge Join，另一种是转化为Hash Table 加载到内存里做Hash Join。
在双流Join的场景中，Join的对象是两个流，数据是不断进入的，所以我们Join的结果也是需要持续更 新的。基本思路是将一个无线的数据流，尽可能拆分成有限数据集去做Join。 
1. Regular Join 
	1. 这种 Join 方式需要去保留两个流的状态，持续性地保留并且不会去做清除。两边的数据对于对方的流 都是所有可见的，所以数据就需要持续性的存在 State 里面，那么 State 又不能存的过大，因此这个场景 的只适合有界数据流。 
2. Interval Join
	1. 原理：两条流数据缓存在内部 State 中，任意一数据到达，获取对面流相应时间范围数据，执行 joinFunction 进行 Join。随着时间的推进，State 中两条流相应时间范围的数据会被清理。
	2. 加入了一个时间窗口的限定，要求在两个流做 Join 的时候，其中一个流必须落在另一个流的时间戳的 一定时间范围内，并且它们的 Join key 相同才能够完成 Join。加入了时间窗口的限定，就使得我们可以 对超出时间范围的数据做一个清理，这样的话就不需要去保留全量的 State。 
	3. Interval Join 是同时支持 processing time 和 even time去定义时间的。如果使用的是 processing time， Flink 内部会使用系统时间去划分窗口，并且去做相关的 state 清理。
	4. 如果使用 even time 就会利用 Watermark 的机制去划分窗口，并且做 State 清理。 
		``` java
		SingleOutputStreamOperator<Tuple2<WaterSensor, WaterSensor2>> result = waterSensorDS1.keyBy(WaterSensor::getId)  
		        .intervalJoin(waterSensorDS2.keyBy(WaterSensor2::getId))  
		        .between(Time.seconds(-5), Time.seconds(5))  
		        .process(new ProcessJoinFunction<WaterSensor, WaterSensor2, Tuple2<WaterSensor, WaterSensor2>>() {  
		            @Override  
		            public void processElement(WaterSensor left, WaterSensor2 right, Context ctx, Collector<Tuple2<WaterSensor, WaterSensor2>> out) throws Exception {  
		                out.collect(new Tuple2<>(left, right));  
		            }  
		        });
		```
3. Window join 
	1. 将两个流中有相同 key 和处在相同 window 里的元素去做 Join。它的执行的逻辑比较像 Inner Join，必 须同时满足 Join key 相同，而且在同一个 Window 里元素才能够在最终结果中输出。

---

## DWS 每小时各省份累积下单金额 和 TOP3累积下单金额的省份

1. 环境准备
	1. flink-table-planner
2. 开启CheckPoint，设置状态后端
3. 设置状态的TTL  生产环境设置为最大乱序程度
	```java
	tableEnv.getConfig().setIdleStateRetention(Duration.ofSeconds(5));
	```
4. 读取 Kafka DWD中 订单明细表 的数据
	1. 用flatmap算子将kafka读到的每行`String`类型的数据转换为`JSONObject`
	2. filter用来过滤，map用来转换，`flatMap`直接完成两项
5. 按照 下单事务事实表的 id分组 ==一个订单中的一个商品项==
6. 去重（取最后一条数据）
	1. 可能会有重复，因为一个订单中可能同一商品购买了多次，每条都是该订单的最终金额，所以之后要做一个去重，只保留一条，方便之后算总金额
	2. 去重的方法是状态编程＋定时器 `process`richfilter也可以
		1. 在`open`中初始化，状态就是数据本身
			 ```java
			 public void open(Configuration parameters) throws Exception {
				 valueState = getRuntimeContext().getState(new ValueStateDescriptor<JSONObject>("value-state", JSONObject.class));
			 }
			 ```
	  1. 在`processElement`中去重。
		 1. 如果状态为null，保存状态，并注册定时器5s。提取处理时间，5s内没有新的数据来就输出。
				```JAVA
				long processingTime = ctx.timerService().currentProcessingTime();
				ctx.timerService().registerProcessingTimeTimer(processingTime + 5000L);
				```
		 1. 如果不为null比较当前数据和状态中的数据比较，保存后一条。
	  3. `onTimer`定时器，5s后，先输出数据后清空状态
		 ```java
		 @Override
		 public void onTimer(long timestamp, OnTimerContext ctx, Collector<JSONObject> out) throws Exception {
			 //输出数据并清空状态
			 out.collect(valueState.value());
			 valueState.clear();
		 }
         ```

7. 将每行`josnobject`数据转换为JavaBean`map`

   1. 窗口起始时间/窗口结束时间/省份 ID/省份名称/累计下单次数/订单 ID/ 集合累计下单金额/时间戳

	   ```java
	   SingleOutputStreamOperator<TradeProvinceOrderWindow> provinceOrderDS = filterDS.map(line -> {
	   
	       HashSet<String> orderIdSet = new HashSet<>();
	       orderIdSet.add(line.getString("order_id"));
	   
	       return new TradeProvinceOrderWindow("", "",
	               line.getString("province_id"),
	               "",
	               0L,
	               orderIdSet,
	               line.getDouble("split_total_amount"),
	               DateFormatUtil.toTs(line.getString("create_time"), true));
	   });
	   ```

8. 提取时间戳生成Watermark 
	```java
   SingleOutputStreamOperator<TradeProvinceOrderWindow> tradeProvinceWithWmDS = provinceOrderDS.assignTimestampsAndWatermarks(WatermarkStrategy.<TradeProvinceOrderWindow>forBoundedOutOfOrderness(Duration.ofSeconds(2)).withTimestampAssigner(new SerializableTimestampAssigner<TradeProvinceOrderWindow>() {
	   @Override
	   public long extractTimestamp(TradeProvinceOrderWindow element, long recordTimestamp) {
		   return element.getTs();
	   }
   }));
	```

9. 分组，开窗，聚合

   1. 按照省份id分组
      1. `tradeProvinceWithWmDS.keyBy(TradeProvinceOrderWindow::getProvinceId)`
   2. 开一个10s的窗
      1. `.window(TumblingEventTimeWindows.of(Time.seconds(10)))`
   3. 聚合
      1. `.reduce(new ReduceFunction<TradeProvinceOrderWindow>()` 
		``` java
	   SingleOutputStreamOperator<TradeProvinceOrderWindow> reduceDS =
		   tradeProvinceWithWmDS.keyBy(TradeProvinceOrderWindow::getProvinceId)
			   .window(TumblingEventTimeWindows.of(Time.seconds(10)))
			   .reduce(new ReduceFunction<TradeProvinceOrderWindow>() {
				   @Override
				   public TradeProvinceOrderWindow reduce
					   (TradeProvinceOrderWindow value1, TradeProvinceOrderWindow value2) throws Exception {
					   value1.getOrderIdSet().addAll(value2.getOrderIdSet());
					   value1.setOrderAmount(value1.getOrderAmount() + value2.getOrderAmount());
					   return value1;
				   }
			   }, new WindowFunction<TradeProvinceOrderWindow, TradeProvinceOrderWindow, String, TimeWindow>() {
				   @Override
				   public void apply(String s, TimeWindow window, Iterable<TradeProvinceOrderWindow> 
									 input, Collector<TradeProvinceOrderWindow> out) throws Exception {
	   
					   TradeProvinceOrderWindow provinceOrderWindow = input.iterator().next();
	   
					   provinceOrderWindow.setTs(System.currentTimeMillis());
					   provinceOrderWindow.setOrderCount((long) provinceOrderWindow.getOrderIdSet().size());
					   provinceOrderWindow.setStt(DateFormatUtil.toYmdHms(window.getStart()));
					   provinceOrderWindow.setEdt(DateFormatUtil.toYmdHms(window.getEnd()));
	   
					   out.collect(provinceOrderWindow);
				   }
			   });
		// reduceDS>>>>>>>>>>>>> TradeProvinceOrderWindow(stt=2022-05-26 16:55:20,edt=2022-05-26 16:55:30,provinceId=2, provinceName=, orderCount=1, orderIdSet=[10081],orderAmount=258.0,ts=1653900969395)
		```

10. 关联省份维表补充省份名称字段
	   ```java
	SingleOutputStreamOperator<TradeProvinceOrderWindow> reduceWithProvinceDS = AsyncDataStream.unorderedWait(reduceDS,  
	        new DimAsyncFunction<TradeProvinceOrderWindow>("DIM_BASE_PROVINCE") {  
	            @Override  
	            public String getKey(TradeProvinceOrderWindow input) {  
	                return input.getProvinceId();  
	            }  
	  
	            @Override  
	            public void join(TradeProvinceOrderWindow input, JSONObject dimInfo) {  
	                input.setProvinceName(dimInfo.getString("NAME"));  
	            }  
	        }, 100, TimeUnit.SECONDS);
	```
11. 将数据写出到ClickHouse
	```sql
	select province_name,
	       sum(order_amount) order_amount
	from dws_trade_province_order_window
	where toYYYYMMDD(stt) = #{date}
	and province_name is not null 
	and province_name !='' 
	group by province_id, province_name;")
	```

```shell
TradeProvinceOrderWindow(stt=2022-05-26 16:55:20,edt=2022-05-26 16:55:30,provinceId=2, provinceName=, orderCount=1, orderIdSet=[10081],orderAmount=258.0,ts=1653900969395)
```



---

# Hadoop

## 3 Hadoop

Hadoop是一==个分布式系统基础架构==，主要是为了解决==海量数据的存储==和==分析计算==问题。

hadoop的核心组件包括：HDFS（高可靠、高吞吐的分布式文件系统，用于数据存储），MapReduce（处理业务逻辑运算），YARN（负责作业调度与集群资源管理）

**1 部分**

1. HDFS
	1. 高可靠性、高吞吐的分布式文件系统，用于数据存储
	2. 通过==目录树==来定位文件。
	3. ==分布式==。由多服务器联合起来实现功能，集群中的服务器有各自的角色。
	4. 使用场景：适合==一次写入，多次读出==的场景。一个文件经过创建、写入和关闭之后就不需要改变。
2. MapReduce
	1. 是分布式运算程序的编程框架，用于处理业务逻辑运算
	2. MapReduce核心功能是将用户编写的业务逻辑代码和自带默认组件整合成一个完整的分布式运算程序，并发运行在一个Hadoop集群上。
	3. MapReduce将计算过程分为两个阶段：Map和Reduce  Map阶段并行处理输入数据，Reduce阶段对Map结果进行汇总
3. YARN
	1. 是一个资源调度平台，负责作业调度与集群资源管理
	2. 为运算程序提供服务器运算资源，相当于一个分布式的操作系统平台，而MapReduce等运算程序则相当于运行于操作系统之上的应用程序。
4. Common
	1. Hadoop体系最底层的一个模块，为Hadoop各子项目提供各种工具，如：配置文件和日志操作等。


**2 特点**
1. 高可靠性
	1. Hadoop底层维护多个数据副本，即使Hadoop某个计算元素或存储出现故障时，也不会导致数据的丢失
2. 高效性
	1. 在MapReduce的思想下，Hadoop是并行工作，加快任务处理速度
3. 高扩展性
	1. 在集群间分配任务数据，可方便的扩展数以千计的节点
4. 高容错性
	1. 能够自动将失败的任务重新分配

---

## ⭐ 介绍HDFS


**==高可靠性、高吞吐量的分布式文件系统，用于数据存储==**

- 通过目录树来定位文件。
- 分布式。由多服务器联合起来实现功能，集群中的服务器有各自的角色。
- 使用场景：适合**一次写入，多次读出**的场景。一个文件经过创建、写入和关闭之后就不需要改变。

1 优点
1. ==高容错==
	1. 数据自动保存多个副本。某一个副本丢失以后，它可以自动恢复。
2. ==高吞吐==
	1. 数据规模：能够处理数据规模达到GB、TB、甚至PB级别的数据；
	2. 文件规模：能够处理百万规模以上的文件数量，数量相当之大。
3. ==低成本==
	1. 可构建在廉价机器上，降低硬件成本。

2 缺点
1. 不适合==低延时数据==访问
2. 无法高效的对大量==小文件==进行存储
	1. 存储大量小文件的话，它会占用NameNode大量的内存来存储 文件目录和 块信息。这样是不可取的，因为NameNode的内存总是有限的；
	2. 小文件存储的寻址时间会超过读取时间，它违反了HDFS的设计目标
3. 不支持==并发写入==、文件随机修改
	1. 一个文件只能有一个写，不允许多个线程同时写；
	2. 仅支持数据append（追加），不支持文件的随机修改


---



## 2 HDFS组成架构


HDFS采用主从架构

1. Client 客户端
	1. 文件切分。
	2. 与NN交互，获取文件的位置信息；
	3. 与DN交互，读取或者写入数据；
	4. Client提供一些命令来管理HDFS，比如启动或者关闭HDFS；
	5. Client可以通过一些命令来访问HDFS；
2. NameNode
	1. 就是Master，它是一个主管、管理者。是用来管理HDFS的命名空间，其将所有的文件和文件目录的元数据保存在一个文件系统树中。
	2. 管理HDFS的命名空间；
	3. 管理数据块（Block）映射信息；
		1. 块ID，所在的DN列表，存储位置和状态
	4. 配置副本策略
	5. 处理客户端读写请求
3. DataNode
	1. 就是Slave。NameNode下达命令，DataNode执行实际的操作
	2. 存储实际的数据块；
	3. 执行数据块的读/写操作。
4. Secondary NameNode
	1. 并非NameNode的热备。辅助NN
	2. 周期合并Fsimage和Edits，并推送给NameNode；
	3. 在紧急情况下，可辅助恢复NameNode。

---

## -3- NN 和 2NN 

1. NN和 2NN工作机制
	1. 备份元数据，以及更新备份信息
	2. 元数据存储内存edits文件中，并持久化到fsimage文件 + edits
		1. **edits**：保存NN启动后，HDFS执行所有的写操作。
		2. **fsimage**：是HDFS文件系统元数据的**一个永久性检查点**，其中包含HDFS文件系统的所有目录和文件inode的序列化信息
2. NameNode
	1. 是用来管理HDFS的命名空间，保存元数据，相应客户端读写请求
	2. 第一次启动 NN 格式化后，创建 Fsimage 和 Edits 文件。如果不是第一次启动，直接加载到内存
	3. 接受客户端对元数据进行增删改的请求
	4. NN 记录操作日志，更新滚动日志
3. Secondary NameNode
	1. 周期性到NN去获取edits，fsimage，并合并更新到自己的fsimage上。有新的fsimage文件，它将其拷贝回NN中
	2. 2NN 询问 NN 是否需要 checkpoint， 直接带回 NameNode 是否检查结果；
		1. 定时时间1h到或者Edits中数据满了（100万条） 会直接触发
	3. 2NN 请求执行 checkpoint；
	4. NN 滚动正在写的 edits 日志
		1. 将滚动前的 edits 和 fsimage 拷贝到 2NN内存，进行合并；
	5. 生成新的镜像文件 fsimage.chkpoint；
	6. 拷贝 fsimage.chkpoint 到 NameNode；
	7. NN 将 fsimage.chkpoint 重新命名成 fsimage；

---

## 3 HDFS 读 / 写 流程

**HDFS写流程**
1. 客户端会先对==文件分块==，然后通过Distributed FileSystem模块向NameNode请求上传文件，==NameNode==检查目标文件是否已存在，父目录是否存在。
2. NameNode返回是否可以上传。
3. 如果可以上传，客户端请求第一个 block，以及上传到哪几个DN服务器上。
4. NameNode返回3个datanode节点，分别为dn1、dn2、dn3。
5. 客户端通过FSDataOutputStream模块向dn1请求上传数据，dn1收到请求会继续调用dn2，然后dn2调用dn3，将这个通信管道建立完成。
6. dn1、dn2、dn3==逐级应答==客户端。
7. 客户端开始往dn1上传第一个block，FSDataOutputStream会将文件分割成==packets==数据包，然后将这些packets写到其内部的一个叫做data queue(数据队列)中，然后以packet为单位发送数据，dn1收到一个packet就会传给dn2，dn2传给dn3；**dn1每传一个packet会放入一个应答队列等待应答**。
8. 当一个block传输完成之后，客户端再次请求NameNode上传第二个block的服务器

**HDFS读流程**
1. 客户端通过 DistributedFileSystem 向 NameNode 请求下载文件，NameNode 通过查 询元数据，找到文件块在哪些DataNode。
2. 客户端挑选一台 DataNode（就近原则，然后随机）服务器，请求读取数据。
3. DataNode 开始传输数据给客户端（从磁盘里面读取数据输入流，以 Packet 为单位来做发送校验，校验不通过会从别的datanode读取）。
4. 客户端以 Packet 为单位接收，先在本地缓存，然后写入目标文件。

---
 
## 2 HDFS的容错机制

1. **针对 DataNode失效 问题**
	1. 每个DataNode以固定的周期向NameNode 发送==心跳==信号，通过这种方法告诉 NameNode 它们在正常工作。如果在一定的时间内 NameNode 没有收到 DataNode 心跳，就认为该 DataNode 宕机了。
2. **针对 网络故障 而导致无法收发数据的问题**
	1. HDFS提供了==ACK机制==，在发送端发送数据后，如果没有收到ACK并且经过多次重试后仍然如此，则认为网络故障；
3. **针对 数据损坏(脏数据) 问题**
	1. 在传输数据的时候，同时会发送==校验和==，当数据存储到硬盘时，校验和也会被存储。（Flume）
	2. 所有的 DataNode 都会定期向 NameNode 发送数据块的存储状况。在发送数据块报告前，会先检查总和校验码是否正确，如果数据存在错误就不发送该数据块的信息。


---



## 2 HDFS数据不丢失

- **先答心跳机制，保证datanode 节点可用；**
- **其次传输过程中有ACK应答机制**
- **然后再说校验**

**数据的读取和写入都要进行校验**

1. 数据在==写入之后==会进行校验和CheckSum的计算，之后DataNode周期性的进行校验和计算，将计算结果与第一次进行对比，若相同表示无数据丢失，若不相同表示有数据丢失，丢失后将进行数据修复；

2. 数据==读取之前==对数据进行校验，与第一次的结果进行对比，若相同表示数据没有丢失，可以读取，若不相同表示数据有所丢失，到其他副本读取数据。
3. 默认校验算法：循环冗余校验 CRC32算法的原理是将待校验的数据看作一个二进制数，并通过除法运算生成一个固定长度（32位）的校验值

**DataNode 节点保证数据完整性的方法：**

1. 当 从DataNode ==读取== Block 的时候，它会计算 CheckSum。
2. 如果计算后的 CheckSum，与 Block 创建时值不一样，说明 Block 已经损坏。
3. Client 读取其他 DataNode 上的 Block。
4. DataNode 在其文件创建后==周期验证== CheckSum。


---

## 3 DN的工作机制 

1. DN作用
	1. 存储 数据块和元数据
	2. 执行客户端发送的读写操作
	3. 通过心跳机制定期（默认 3 秒）向 NameNode 汇报运行状态和 Block 列表信息
	4. 集群启动时，DataNode 向 NameNode 提供 Block 列表信息
2. DataNode的工作机制
	1. DataNode是HDFS的组件之一，其主要工作是==存储和管理数据块==。
	2. 一个数据块在 DataNode 上以文件形式存储在磁盘上，包括两个文件，一个是数据本身，一个是元数据（包括数据块的长度，块数据的校验和，以及时间戳）。
	3. DataNode 启动后向 NameNode 注册，通过后，周期性（6 小时）的向 NameNode 上报所有的块信息。
	4. DataNode在周期性（3s）向NameNode发送心跳，同时DataNode也会收到来自NameNode的响应，响应内部包含了NameNode下发给DataNode的一些指令。如果超过10 分钟没有收到某个 DataNode 的心跳， 则认为该节点不可用。
	5. 集群运行中可以安全加入和退出一些机器。
3. DataNode 节点保证数据完整性的方法（数据损坏）
	1. 当 从DataNode 读取 Block 的时候，它会计算 ==CheckSum==。如果计算后的 CheckSum，与 Block 创建时值不一样，说明 Block 已经损坏。
	2. Client 读取其他 DataNode 上的 Block。
	3. DataNode 在其文件创建后周期验证 CheckSum。

---

## 3 HDFS高可用

HDFS的高可用指的是指系统能够在出现故障或中断的情况下保持可用性和继续正常工作的能力

因为客户端对HDFS的读、写操作 之前都要访问NameNode服务器，客户端只有从NameNode获取元数据之后才能继续进行读、写。所以 HDFS的高可用的关键在于NameNode上的元数据持续可用。

1. 双 NameNode 消除单点故障
	1. 两台 NameNode 形成互备，一台处于 Active 状态，为主 NameNode，另外一台处于 Standby 状态，为备 NameNode，只有主 NameNode 才能对外提供读写服务。
2. 主备切换控制器 ZKFailoverController
	1. ZKFC 作为独立的进程运行，对 NameNode 的主备切换进行总体控制。ZKFailoverController 能及时检测到 NameNode 的健康状况，在主 NameNode 故障时借助 Zookeeper 实现自动的主备选举和切换，当然 NameNode 目前也支持不依赖于 Zookeeper 的手动主备切换
3. Zookeeper 集群
	1. 分布式协调器，NameNode选主用的。选择一个节点 为 active 状态， 排外锁
4. 健康监测
	1. 监控NameNode状态。ZKFC 使用一个健康检查命令定期地 ping 与之在相同主机的 NameNode， 只要该 NameNode 及时地回复健康状态，ZKFC 认为该节点是健康的。如果该节点崩溃，冻 结或进入不健康状态，健康监测器标识该节点为非健康的。
5. 共享存储系统
	1. Active NameNode 和 Standby NameNode 通过共享存储系统实现元数据同步。JournalNode主要用于记录和维护HDFS的Edits（命名空间日志），这些日志用于跟踪文件系统的元数据更改。


---
## Hadoop 小文件
对于小文件问题，Hadoop本身也提供了几个解决方案，分别为： Hadoop Archive ， Sequence
file 和 CombineFileInputFormat 。

1. Hadoop Archive
	1. 将多个小文件打包成一个HAR文件，这样在减少namenode内存使用的同时，仍然允许对文件进行透明的访问。
2. Sequence file
	1. sequence file由一系列的二进制key/value组成，如果为key小文件名，value为文件内容，则可以将大批小文件合并成一个大文件。
3. CombineFileInputFormat
	1. 它是一种新的inputformat，用于将多个文件合并成一个单独的split，另外，它会考虑数据的存储位置。


## ⭐ MapReduce

MapReduce 是一个==分布式运算程序==的编程框架，它的核心功能是将用户编写的业务逻辑代码和自带默认组件整合成一个完整的分布式运算程序，并发运行在一个 Hadoop 集群上。

- 实现 一定程序的并行处理海量数据，提高效率。
- 海量数据难以在单机上处理，而一旦将单机版程序扩展到集群上进行分布式运行势必将大大增加程序的 复杂程度。引入MapReduce架构，开发人员可以将精力集中于数据处理的核心业务逻辑上，而将分布式 程序中的公共功能封装成框架,以降低开发的难度。
- 一个完整的mapreduce程序有三类实例进程
  1. MRAppMaster：负责整个程序的协调过程 
  2. MapTask：负责map阶段的数据处理
  3. ReduceTask：负责reduce阶段的数据处理

**优点**

扩大易容 

1.   **高容错**
     1. MapReduce 设计的初衷就是使程序能够部署在廉价的 PC 机器上，这就要求它具有很高的容错性。比如其中一台机器挂了，它可以把上面的==计算任务转移到另外一个节点==上运行， 不至于这个任务运行失败，而且这个过程不需要人工参与，而完全是由 Hadoop 内部完成的。
2.   **大数据**
     1. 适合 PB 级以上海量数据的离线处理，可以实现上千台服务器集群并发工作，提供数据处理能力。
3.   **扩展**
     1. 当你的计算资源不能得到满足的时候，你可以通过==简单的增加机器==来扩展它的计算能力。
4.   **易于编程**
     1. ==它简单的实现一些接口，就可以完成一个分布式程序==，这个分布式程序可以分布到大量廉价的 PC 机器上运行。也就是说你写一个分布式程序，跟写一个简单的串行程序是一模一样的。就是因为这个特点使得 MapReduce 编程变得非常流行。

 **:two:缺点**

实流图

1.   **不擅长实时计算**

     1.   MapReduce无法毫秒或者秒级内返回结果。

2.   **不擅长流式计算**

     1.   流式计算的输入数据是动态的，而MapReduce的==输入数据集是静态的==，不能动态变化。这是因为MapReduce 自身的设计特点决定了数据源必须是静态的。

3.   **不擅长 DAG（有向无环图）计算**
     1. 多个应用程序存在依赖关系，后一个应用程序的输入为前一个的输出。在这种情况下，MapReduce并不是不能做，而是使用后，==每个MapReduce作业的输出结果都会写入到磁盘， 会造成大量的磁盘 IO，导致性能非常的低下。==


---

## 3 MapReduce流程

1. ==切片 split==
   - 在`FileInputFormat` 类中，首先会校验文件是否支持切片
   - 然后将文件分片（默认分片大小就是blockSize128M，但是源码中还有一个 SPLIT_SLOP = 1.1），
   - 最后将切片信息放入ArrayList数组
2. 执行MapTask
	1. ==Map阶段==。`LineRecorderReader`读取切片数据 ，转化为<k,v>键值对形式，k是偏移量， v是每一行内容
3. Shuffle
	1. ==Collect==
		1. 每个 Map 任务都有一个环形缓冲区在`MapOutputBuffer`定义，本质是一个byte数组( 100MB )，源码定义了一个`equator`
		2. key/value按照索引递增的方向存储，元数据则按照索引递减的方向存储
	2. ==Spill溢写==
		1. 当环形缓冲区满80%`spill.percent`后，MapReduce会将数据写到本地磁盘上，生成一个临时文件。这个溢写是由单独线程来完成，不影响往缓冲区继续写数据。
	3. ==Sort==
		1. QuickSort==快速排序==。先对==分区==进行排序其次对==key值==排序。这样，数据按分区排序（同一partition的放在一起），并且在每个分区内按键对元数据`kvmeta`排序。
	4. ==Combiner== 阶段
		1. 如果用户设置了 Combiner，则写入文件之 前，对每个分区中的数据进行一次聚集操作。
	5. ==Merge==
		1. 每次spill都会在磁盘上生成一个临时文件，MapTask 会对所有临时文件使用==归并排序==合并，应将所有溢出文件合并在一起以形成一个map输出文件。
	6. ==Copy（ReduceTask）== 
		1. Reduce进程启动Fetcher线程，通过HTTP方式请求获取上一阶段的输出文件。并针对某一片数据，如果其大小超过一定國值，则写到磁盘上，否则直接放到内存中
	7. ==Merge==
		1. Copy过来的数据会先放入内存缓冲区中。同时启动两个后台线程`inMemoryMerger`，`onDiskMerger`，开启内存到磁盘的和磁盘到磁盘的me1rge。
		2. merge合并分为3种：内存到内存合并（默认不开启）、内存到磁盘合并、磁盘到磁盘合并。
	8. ==Sort== 
		1. 在合并过程中，会对数据进行Sort排序，默认情况下是key的字典序，Task 已经实现对自己的处理结果进行了局部排序，因此， ReduceTask 只需对所有数据进行一次==归并排序==即可。如果用户设置比较器，则以用户设置的为准。
4. ==Reduce== 
   1. 调用用户定义的 reduce 函数进行处理，调用`TextOutPutFormat`并将计算结果写到HDFS上

---

##   Shuffle / 优化

Map 方法之后，Reduce 方法之前的数据处理过程称之为 Shuffle。

1. Collect 阶段：将 MapTask 的结果输出到默认大小为 100M 的环形缓冲区， 保存的是 key/value等。
2. **Spill 阶段**：当内存中的数据量达到一定的阀值的时候，就会将数据写入本地磁盘，在将数据写入磁盘之前，线程首先根据reduce任务的数目将数据划分为相同数目的分区，然后对区内数据进行一次快排，如果 配置了 combiner，还会将有相同分区号和 key 的数据进行聚合。
3. **MapTask 阶段的 Merge**：把所有溢出的临时文件进行一次合并然后做一个归并排序，以确保**一个** MapTask 最终只产生一个中间数据文件。
4. **Copy 阶段**：ReduceTask 启动 Fetcher 线程到已经完成 MapTask 的节点上复制一份属于自己的数据，这些数据默认会保存在内存的缓冲区中，当内存的缓冲区达到一定的阀值的时候，就会将数据写到磁盘之上。
5. **ReduceTask 阶段的 Merge**：在 ReduceTask 远程复制数据的同时，会在后台开启两个线程对内存到本地的数据文件进行合并操作；
6. **sort** ：对数据进行一个最终的归并排序；由于各个MapTask已经实现对自己的处理结果进行了局部排序，因此，ReduceTask只需对所有数据进行一次归并排序即可。

  **MapReduce Shuffle后续优化方向**

1. 压缩：对==数据压缩==，减少写读数据量；
2. 减少不必要的排序：并不是所有类型的Reduce需要的数据都是需要排序的，排序这个过程如果不需要最好还是不要的好；
3. ==内存化==：Shuffle的数据不放在磁盘而是尽量放在内存中，除非逼不得已往磁盘上放、
4. 网络框架：放弃RPC，==netty网络通信==的性能据说要占优了；
5. 本节点上的数据不走网络框架：对于本节点上的Map输出，Reduce直接去读吧，不需要绕道网络框架。


---

  ## ⭐ 介绍YARN

 YARN是一个资源管理、任务调度的框架，负责为运算程序提供服务器运算资源，相当于一个**分布式的操作系统平台**， 而**MapReduce等运算程序则相当于运行于操作系统之上的应用程序**。主要包含ResourceManager、NodeManager、 ApplicationMaster和Container模块。

1. ResourceManager（RM）主要作用如下：

   - 与客户端交互，处理来自客户端的请求。

   - 启动和管理ApplicatinMaster，并在它运行失败时重新启动它。

   - 管理NodeManager，接受来自NodeManager的资源管理汇报信息，并向NodeManager下达管理命令（比如杀死Contanier）等。

   - 资源管理与调度，接收来自ApplicationMaster的资源申请请求，并为之分配资源（核心）。

2. NodeManager（NM）主要作用如下：

   - 管理单个节点上的资源
   - 处理来自ResourceManager的命令
   - 处理来自ApplicationMaster的命令

3. ApplicationMaster（AM）作用如下：

   - 为应用程序申请资源并分配给内部的任务

   - 任务的监督与容错

4. Container

   - Container是YARN中的资源抽象，它封装了某个节点上的多维度资源，如内存、CPU、磁盘、网络等。



  ## 3 YARN提交流程

1. **提交**
	1. 用户提交应用程序：用户通过YARN客户端工具提交应用程序。
	2. 应用程序向RM请求资源：应用程序在提交时指定了所需的资源以及其他配置参数。这些资源请求和参数将被发送到YARN资源管理器（ResourceManager）
2. **分配**
	1. RM分配AM：RM接收到应用程序的资源请求后，会为应用程序分配一个应用程序主节点（ApplicationMaster）。
	2. AM启动：AM启动，并在一个Container中运行。
	3. AM请求资源：AM与RM通信，向其请求MapTask资源。
	4. 任务调度：AM收到资源后，将任务分配给NodeManager，NM分别领取任务并创建Container
3. **运行**
	1. 任务执行：Container中的任务启动并在相应的节点上执行。任务可以是MapReduce作业、Spark应用程序、Hive查询等。
	2. 进度更新和状态报告：AM会定期向RM发送进度更新和状态报告，以便RM了解应用程序的执行情况。
4. **完成**
	1. 完成和资源释放：一旦应用程序的所有任务完成，AM会通知RM，释放应用程序占用的资源。
	2. 结果返回：应用程序可以将结果写入适当的存储位置，以便用户检索和处理。

---

  ## YARN容错机制

1. 任务失败
	1. 重新调度该任务，一个任务失败的次数超过4次，将不会再重新调度。
2.   ApplicationMaster运行失败
		1. ApplicationMaster有几次尝试次数，默认为2。
3.   **NodeManager运行失败**
	   1.   向ResourceManager发送心跳信息。则如果10分钟
4.   **ResourceManager运行失败**
	   1.   在YARN中，ResourceManager失败是个致命的问题，如果失败，任何任务和作业都无法启动。所以我们需要配置高可用；我们需要配置一对ResourceManager，在主ResourceManager失败后，备份ResourceManager可以继续运行。
	   2.   将所有的ApplicationMaster的运行信息保存到一个高可用的状态存储中（由ZooKeeper或者HDFS备份），这样备份ResourceManager就可以恢复出失败的ResourceManager状态
	   3.   ResourceManager在主备切换由故障转移器（failover controller）处理。默认情况，failover controller自动工作，由ZooKeeper的Leader选举，保证同一时刻只有一个主ResourceManager。


---

## YARN HA

  YARN ResourceManager 的高可用与 HDFS NameNode 的高可用类似但是 ResourceManager 不像 NameNode ，没有那么多的元数据信息需要维护，所以它的状态信息可以直接写到Zookeeper 上，并依赖 Zookeeper 来进行主备选举。

  - 同样是基于zookeeper的ZKFC实现监控RM的健康状态，并执行选举作用；在zookeeper指定目录下创建一个临时节点，创建成功则认为获取了锁，成为Active的RM；没获取成功的成为stand by。。

  - RM会把job的信息存放在zookeeper的/rmstore目录下，active RM会向这个目录写app的信息。当active RM挂掉之后，standby RM会通过zkfc切换为active状态，然后从zookeeper的/rmstore目录下读取相应的作业信息，恢复集群的工作；

# Hive

1 介绍Hive

**:one:介绍**

Hive是基于Hadoop的一个数据仓库工具，可以将==结构化的数据文件映射为一张表==，并==提供类SQL查询功能==

Hive的本质是将HQL转化成MapReduce程序

1. Hive处理的数据存储在HDFS

2. Hive分析数据底层的实现是MapReduce

3. 执行程序运行在Yarn上


**:two:作用**

提供了一种==SQL方言，查询HDFS中的数据==或其他和Hadoop集成的文件系统，如HBase这样的数据库中的数据。

大多数数据仓库应用程序都是使用关系数据库进行实现的，并使用SQL作为查询语言。Hive降低了将这些应用程序转移到Hadoop系统上的难度。凡是会使用SQL语言的开发人员都可以很轻松的学习并使用Hive。如果没有Hive，那么这些用户就必须学习新的语言和工具，然后才能应用到生产环境中。

**:three:优点**

1. 操作接口采用类SQL语法，提供快速开发的能力（简单、==易上手==）。

2. 避免了去写MapReduce，减少开发人员的学习成本。

3. Hive的执行延迟比较高，因此Hive常用于数据分析，对实时性要求不高的场合。

4. Hive优势在于处理大数据，对于处理小数据没有优势，因为Hive的执行延迟比较高。

5. Hive支持用户自定义函数，用户可以根据自己的需求来实现自己的函数。


**:four:缺点**

1. Hive的HQL==表达能力有限== 
   1. 迭代式算法无法表达 
   2. 数据挖掘方面不擅长，由于MapReduce数据处理流程的限制，效率更高的算法却无法实现。
2. ==效率低==
   1. Hive自动生成的MapReduce作业，通常情况下不够智能化 
   2. Hive调优比较困难，粒度较粗

**:five:架构**

1. ==用户接口：Client==
   1. CLI（command-line interface）、JDBC/ODBC(jdbc 访问 hive)、WEBUI（浏览器访问 hive）

2. ==元数据：Metastore==
   1. 元数据包括：表名、表所属的数据库（默认是 default）、表的拥有者、列/分区字段、表的类型（是否是外部表）、表的数据所在目录等；

   2. 默认存储在自带的 derby 数据库中，推荐使用 MySQL 存储 Metastore
3. HDFS

   1. ==使用 HDFS 进行存储==，使用 MapReduce 进行计算，程序运行在yarn上

4. 驱动器：Driver

   1. 解析器（SQL Parser）：将 SQL 字符串转换成抽象语法树 AST（abstract syntax tree）（这一步一般都用第三方工具库完成，比如 antlr；）对 AST 进行语法分析，比如表是否存在、字段是否存在、SQL语义是否有误。

   2. 编译器（Physical Plan）：将 AST 编译生成逻辑执行计划。

   3. 优化器（Query Optimizer）：对逻辑执行计划进行优化。

   4. 执行器（Execution）：把逻辑执行计划转换成可以运行的物理计划，提交执行。对于 Hive 来说，就是 MR/Spark。

---



## -1- Hive / 传统数据库

Hive 本质：将 HQL 转化成 MapReduce 程序。

传统数据库：基本就是数据得存储与查找。

1. 数据==存储==位置。
	1. Hive HDFS / 数据库  块设备或本地文件系统
2. 数据格式。
	1. Hive中没有定义专门的数据格式，由用户指定，需要指定三个属性：列分隔符，行分隔符，以及读取文件数据的方法。
	2. 数据库中，存储引擎定义了自己的数据格式。所有数据都会按照一定的组织存储。
3. 数据==更新==。
	1. Hive==不支持行级别==的更新、插入或者删除操作。
	2. 而数据库中的数据通常是需要经常进行修改。
4. 执行==延迟==。
	1. Hive在查询数据的时候，需要==扫描整个表(或分区)==，因此延迟较高，只有在处理大数据是才有优势。
	2. 数据库在处理小数据是执行延迟较低。
5. ==索引==。
	1. Hive==没有== / 数据库有
6. 可扩展性。
	1. Hive==高== / 数据库低
7. 数据规模。
	1. Hive==大== / 数据库

---



## -2- 内部表和外部表

1. 建表
	1. 内部表
	2. 外部表 被external修饰 `create external table if not exists table_name`
2. 数据管理
	1. 内部表 ==自身管理==
	2. 外部表 HDFS管理
3. 数据存储
	1. 内部表，一般在默认位置存储数据  /user/hive/warehouse
	2. 外部表，一般会搭配 location 来指定数据的存放目录（项目中我是按表名将表存放在不同的文件夹）
	3. 不论是外部表还是内部表，都能使用 location 指定数据的存放路径的。
4. 删除
	1. 内部表 ==删除元数据（metadata）及 存储数据==
	2. 外部表==仅删除元数据==，HDFS上的文件并不会被删除；
5. 修改
	1.  内部表 ==自动同步==给元数据
	2.  外部表 ==需要修复表==（`MSCK REPAIR TABLE table_name`;）就是相当于手动更新元数据，不然修改后可能访问不到数据。

**外部表的优点**

1. 外部表不会加载数据到Hive的默认仓库（挂载数据），==减少数据传输==。
2. 使用外部表，Hive不会修改元数据，==不用担心数据损坏或丢失==。
3. Hive在删除外部表时，删除的只是表结构，而不会删除数据，能和其他外部表共享数据

---

## 3 Map join

1. Map join
   通过==两个只有 map 阶段的 Job== 完成一个 join 操作。适用于小表 join 大表，主要是用来解决数据倾斜的问题，因为需要将小表加载进内存；分两步：
   小于25M就会被加载进内存，

   ```
   hive.auto.convert.join=false(关闭自动MAPJOIN转换操作)
   hive.ignore.mapjoin.hint=false(不忽略MAPJOIN标记)
   ```

   整个JOIN过程包含Map、Shuffle和Reduce三个阶段。通常情况下，join操作在Reduce阶段执行表连接。==mapjoin在Map阶段执行表连接==，而非等到Reduce阶段才执行表连接，可以缩短大量数据传输时间，提升系统资源利用率，从而起到优化作业的作用。

   1. 则第一个 Job 会读取小表数据，转化为为 hash table，并上传至 Hadoop 分布式缓存。
   2. 第二个Job 会先从 分布式缓存中读取小表数据，并缓存在 Map Task 的内存中，然后扫描大表数据，这样在 map 端即可完成关联操作。


---


## -3-Hive数据倾斜
**倾斜问题排查**
访问MR执行任务情况端口：8088
1. 通过时间判断
   1. 如果某个 reduce的时间比其他 reduce 时间长的多，reduce卡在99%
2. 通过任务Counter判断
   1. Counter 会记录整个 job 以及每个 task 的统计信息；通过输入记录数，普通的 task counter 如下，输入的记录数是 13 亿多；而 task=000000 的 counter，其输入记录数是 230 多亿。是其他任务的 100 多倍

**定位 SQL 代码**
1. 确定任务卡住的 stage
   1. 通过 jobname ，括号里面会有一个 stage：
   2. 如果 jobname 是自定义的，那可能没法通过 jobname 判断 stage。需要借助于任务日志并参考执行计划确定；
      1.  Ctrl+F 搜索 “CommonJoinOperator: JOIN struct” ，比如Hive 在 join 的时候，会把 join 的 key 打印到日志中。如下
      2.  上图中的关键信息是：**struct<_col0:string, _col1:string, _col3:string>**
      3.  这时候，需要参考该 SQL 的执行计划。通过参考执行计划，可以断定该阶段为 Stage-4 阶段
2. 确定 SQL 执行代码
   1. 确定了 stage。通过SQL执行计划，则可以判断出是执行哪段代码时出现了倾斜；（比如这个 stage 中进行连接操作的表别名是 d）

数据倾斜主要表现在，mapreduce程序执行时，reduce节点大部分执行完毕，但是有一个或者几个reduce节点运行很慢，导致整个程序的处理时间很长，这是因为某一个key的条数比其他key多很多(有时是百倍或者千倍之多)，这条Key所在的reduce节点所处理的数据量比其他节点就大很多，从而导致某几个节点迟迟运行不完甚至执行失败。

**Join**
1. 大表join小表，
	1. 小表放在 join 的左边，可以使用 map join 让小表先进内存。在 map 端完成 join。 
		1. 实际测试发现：新版的 hive 已经对小表 JOIN 大表和大表 JOIN 小表进行了优化。
2. 大表join大表，空值过多，导致对应的数据都发送到相同的 reducer 上
	1. 空 KEY 过滤
		1. 如日志中，常会有信息丢失的问题，比如日志中的 user_id，如果取其中的 user_id 和 用户表中的 user_id 关联，会碰到数据倾斜的问题。==SQL 语句==中进行过滤
	2. 空 KEY 转换
		  1. 有时虽然某个 key 为空对应的数据很多，但是相应的数据不是异常数据，必须要包含在join 的结果中，此时我们可以表 a 中 key 为空的字段==赋一个随机值==，使得数据随机均匀地 分不到不同的 reducer 上。

**Group by**
1. group by 维度过小，某值的数量过多
	1. Map-Side 聚合。`set hive.map.aggr = true`。生成的查询计划会有两个 MR Job。
		1. 数据会现在 Map 端完成部分聚合工作。这样一来即便原始数据是倾斜的，经过 Map 端的初步聚合后，发往 Reduce 的数据也就不再倾斜。
		2. 就是在 map 端维护一个 hash table，利用其完成部分的聚合，然 后将部分聚合的结果，按照分组字段分区，发送至 reduce 端，完成最终的聚合。map-side 聚合能有效减少 shuffle 的数据量，提高分组聚合运算的效率。

**Count Distinct**
1. 某特殊值过多，处理此特殊值的reduce耗时
	1. COUNT DISTINCT 使用先 GROUP BY 再 COUNT 的方式替换

      ```sql
      select count(id) from (select id from bigtable group by id) a;
      select count(distinct id) from bigtable;
      ```

      

**参数调节**

1、不影响最终业务逻辑的情况下，开启map端预聚合

```
hive.map.aggr = true // Map 端部分聚合，相当于Combiner
```

2、**有数据倾斜的时候进行负载均衡**，当选项设定为true，生成的查询计划会有两个MR Job。第一个MR Job中，Map 的输出结果集合会随机分布到Reduce中，每个Reduce做部分聚合操作，并输出结果，这样处理的结果是相同的Group By Key有可能被分发到不同的Reduce中，从而达到负载均衡的目的；第二个MR Job再根据预处理的数据结果按照Group By Key分布到Reduce中（这个过程可以保证相同的Group By Key被分布到同一个Reduce中），最后完成最终的聚合操作。

```
hive.groupby.skewindata=true
```

3、调整reduce的内存大小，使用`mapreduce.reduce.memory.mb`这个配置

4、合理调整reduce个数

6、最后不可拆分大文件引发的数据倾斜

**当对文件使用GZIP压缩等不支持文件分割操作的压缩方式，在日后有作业涉及读取压缩后的文件时，该压缩文件只会被一个任务所读取**。如果该压缩文件很大，则处理该文件的Map需要花费的时间会远多于读取普通文件的Map时间，该Map任务会成为作业运行的瓶颈。这种情况也就是Map读取文件的数据倾斜

这种数据倾斜问题没有什么好的解决方案，只能将使用GZIP压缩等不支持文件分割的文件转为bzip和zip等支持文件分割的压缩方式

---

## 3 Hive 优化

优化的根本思想

- 尽早尽量过滤数据，减少每个阶段的数据量
- 减少job数
- 解决数据倾斜问题

1. ==分组聚合优化==`set hive.map.aggr=true;`
	1. Hive 中未经优化的分组聚合，是通过一个 MapReduce Job 实现的。Map 端负责读取数据，并按照分组字段分区，通过 Shuffle，将数据发往 Reduce 端，各组数据在 Reduce 端完成最终的聚合运算。Hive 对分组聚合的优化主要围绕着==减少 Shuffle 数据量==进行，具体做法是 ==map-side 聚合==。所谓 map-side 聚合，就是在 map 端维护一个 ==hash table==，利用其完成==部分的聚合==，然 后将部分聚合的结果，按照分组字段分区，发送至 reduce 端，完成最终的聚合。map-side 聚合能有效减少 shuffle 的数据量，提高分组聚合运算的效率。
2. 任务并行度
	1. 一般更关注reduce的并行度。默认以整个 MR Job 输入的文件大小估算并行度。开启map-side 聚合后可以==适当调小==。
3. 小文件合并
	1. ==Map端输入文件合并==
		1. `CombineHiveInputFormat`。防止为单个小文件启动一个 Map Task，浪费计算资源。
	2. ==Reduce输出文件合并==
		1. 开启合并`map only` 和`map reduce`任务输出的小文件。目的是减少 HDFS 小文件数量。
---

## 小文件
1. 通过调整参数进行合并
	1. Map输入的时候, 把小文件合并 `CombineHiveInputFormat`
	2. 在Reduce输出的时候, 把小文件合并 `map only` 和`map reduce`
2. 对按分区插入数据的时候产生大量的小文件的问题，可以使用DISTRIBUTE BY rand() 将数据随机分配给Reduce，这样可以使得每个Reduce处理的数据大体一致。
3. 使用Sequencefile作为表存储格式，不要用textfile，在一定程度上可以减少小文件
4. 使用hadoop的archive归档

---

## 3 Hive自定义函数

**数仓项目中使用了自定义的UDTF**；为了获取动作日志表：action字段中包括多个字段，需要将他解析出来

作用：当Hive提供的内置函数无法满足你的业务处理需要时，此时就可以考虑使用用户自定义函数，来进行方便的扩展（UDF： user-defined function）。

根据用户自定义函数类别分为以下三种：

1. UDF（User-Defined-Function）：==一进一出==
2. UDAF（User-Defined Aggregation Function）：聚集函数，==多进一出==
	1. 类似于：count/max/min
3. UDTF（User-Defined Table-Generating Functions）：==一进多出==
	1. 如lateral view  explode()

**实现步骤与流程**
1. 导入依赖`hive-exec`
2. 创建类继承 `GenericUDTF`
3. 重写三个方法
	1. `initialize`
		  1. 输入参数合法性检查。确保只有一个输入参数。
		  2. 校验输入参数的类型。确保第一个输入参数是 string 类型。
		  3. 定义返回值名称和类型。这里定义了一个名为 "items" 的字段，并且其类型为 string。
	2. `process`
		  1.  获取传入的数据。该参数是一个 JSON 数组的字符串表示。
		  2.  将String转换为`JSONArray`对象，便于后续处理。
		  3.  循环遍历 JSONArray，每次取出其中一个 JSON 字符串，并将其写出（通过 `forward` 方法）。

5. 打成 jar 包上传到服务器/opt/module/hive/datas/myudf.jar
6. 创建临时函数，将 jar 包添加到 hive 的 classpath，临时生效
	1. 临时函数只跟会话有关系，跟库没有关系。只要创建临时函数的会话不断，在当前会话下，任意一个库都可以使用，其他会话全都不能使用。
	   ```sql
	   add jar /opt/module/hive/datas/myudf.jar;
	   create temporary function my_len 
	   	as "com.atguigu.hive.udf.MyUDF";
	   ```

6. 创建永久函数
	1. 永久函数跟会话没有关系，创建函数的会话断了以后，其他会话也可以使用。
	   ```sql
	   create function my_len2 
	   	as "com.atguigu.hive.udf.MyUDF" 
	   	using jar "hdfs://hadoop102:8020/udf/myudf.jar";
	   ```

```java
public class ExplodeJSONArray extends GenericUDTF {
 
    @Override
    public StructObjectInspector initialize(StructObjectInspector argOIs) throws UDFArgumentException {
        // 1 输入参数合法性检查
        if (argOIs.getAllStructFieldRefs().size() != 1){
            throw new UDFArgumentException("ExplodeJSONArray 只需要一个参数");
        }
        // 2 第一个参数必须为string  校验输入参数个数
        if(!"string".equals(argOIs.getAllStructFieldRefs().get(0).getFieldObjectInspector().getTypeName())){
            throw new UDFArgumentException("json_array_to_struct_array的第1个参数应为string类型");
        }
        // 3 定义返回值名称和类型
        List<String> fieldNames = new ArrayList<String>();
        List<ObjectInspector> fieldOIs = new ArrayList<ObjectInspector>();
        fieldNames.add("items");
        fieldOIs.add(PrimitiveObjectInspectorFactory.javaStringObjectInspector);
        return ObjectInspectorFactory.getStandardStructObjectInspector(fieldNames, fieldOIs);
    }
 
    public void process(Object  objects) throws HiveException {
 
        // 1 获取传入的数据
        String jsonArray = objects[0].toString();
        // 2 将string转换为json数组
        JSONArray actions = new JSONArray(jsonArray);
        // 3 循环一次，取出数组中的一个json，并写出
        for (int i = 0; i < actions.length(); i++) {
            String  result = new String1;
            result[0] = actions.getString(i);
            forward(result);
        }
    }
 
    public void close() throws HiveException {
    }
}
 
```

----

 

## 1 HSQL排序关键字

1. order by 
   1. ==全局排序==，一个Reduce
2. distribute by 
   1. ==分区==，按照指定的字段对数据进行划分输出到不同的reduce中。
   2. 结合 sort by 使用。
3. sort by 
   1. ==每个Reduce内部排序==，
4. cluster by ：
   1. ==分区排序==。当 distribute by 和 sort by 字段相同时，可以使用 cluster by 方式。

---



## 2 分区表和分桶表

**分区表**

例如我们会使用数据的加载时间分区`partitioned by (dt string)`

1. 分区表针对的是数据的==存储路径==。实际上就是对应一个 HDFS 文件系统上的独立的文件夹
2. 一个分区名对应一个目录名，子分区名就是子目录名，==不是一个实际字段==
3. 插入数据的时候指定分区，其实就是新建一个目录或者子目录，或者 在原有的目录上添加数据文件

**分桶表**

1. 分桶表针对的是数据==文件==。在分区表的基础上，进一步对表进行组织`clustered by(id)  into 4 buckets` 
2. Hive 的分桶采用对==**分桶字段**的值进行哈希==，然后除以桶的个数取模的方式决定该条记录存放在哪个桶当中

**区别**

- 目的：分区==缩小范围==，==加快速度==。分桶==取样更高效==
- 随机：分桶==随机==分割数据库，分区是==非随机==
- 粒度：分区对应HDF上的==目录粗粒度==，分桶是对应==目录里的文件细粒度==
- 注意：普通表（外部表、内部表）、分区表这三个都是对应HDFS上的目录，桶表对应是目录里的文件。

---



## 2 执行流程

> Hive元数据存放在MySQL里。
> Hive的表数据存在HDFS上的。

主要过程:

1. 客户端发送一条==HQL语句==给Hive的==驱动器driver==。
2. Hive的驱动器driver里面有==:解析器、编译器、优化器、执行器==等。这些主要完成HQL查询语句从词法分析、语法分析、编译、优化以及查询计划的生成。这一步完成了HSQL翻译成MR。
   1. 语法解析：将 SQL 转化为抽象 ==语法树== AST Tree；
   2. 语义解析：遍历 AST Tree，抽象出==查询块== QueryBlock；
   3. 生成逻辑执行计划：遍历 QueryBlock，翻译为执行==操作==树 OperatorTree；
   4. 优化逻辑执行计划：==优化操作树==，合并不必要的 ReduceSinkOperator，减少 shuffle 数据量；
   5. 生成物理执行计划：遍历操作树，翻译为 M==apReduce任务==；
   6. 优化物理执行计划：物理层==优化MapReduce== 任务的变换，生成最终的执行计划。
3. driver生成相应的==MapReduce jar包==，结合元数据里提供的对应的文件路径，把jar包提交到Hadoop的Yarn上面执行(提交给ResourceManager执行task) 。



---

## [0] 窗口函数(分析)

分析函数用于计算基于组的某种聚合值，它和聚合函数的不同之处是：**对于每个组返回多行，而聚合函数对于每个组只返回一行**。

1. 计算
   1. sum/ avg/ max/ min/ count
2. 取值
   1. first_value/ last_value 取排名最前／最后记录的字段的值取值
   2. lag/ lead 往前/后第 n 行数据
3. 排序
   1. rank/ dense_rank
   2. row_number 行号，不重复的连续行号
   3. ntitle 按顺序切片后，返回当前记录的切片值
4. 序列
   1. cume_dist 小于等于当前值的行数／分组内总行数序列
   2. percent_rank 分组内当前行的RANK值 -1／分组内总行数-1

---



## [0] Hive服务部署

1. HiveServer2
   1. 作用是提供 ==jdbc/odbc 接口==，为用户提供远程访问 Hive 数据的功能
2. Metastore
   1. 为 Hiveserver2 提供元数据访问接口。客户端连接metastore服务，metastore再去连接MySQL数据库来存取元数据。有了metastore服务，就可以有多个客户端同时连接，而且这些客户端不需要知道MySQL数据库的用户名和密码，只需要连接metastore 服务即可
   2. 内嵌模式（Embedded） 
   3. 本地模式（Local）
   4. 远程模式（Remote）
3. beeline
   1. hive客户端链接到hive的一个工具。可以理解成mysql的客户端。如：navite cat 等这样的工具。Hive客户端工具后续将使用Beeline 替代HiveCLI ，并且后续版本也会废弃掉HiveCLI 客户端工具。Beeline是Hive新的命令行客户端工具。

---



# Spark

### [0]介绍下spark

Spark 是一种基于内存的快速、通用、可扩展的大数据==分析计算引擎==

**核心模块**

1. Spark Core
	1. 实现spark的基本功能，任务调度，内存管理，错误恢复
2. Spark SQL 
	1. Spark SQL 是 Spark 用来操作结构化数据的组件。==数据处理和分析==，住哪换和和清洗
3. Spark Streaming 
	1. 实时流处理
4. Spark MLlib 
	1. 机器学习算法库。==机器学习和数据挖掘==
5. Spark GraphX 
	1. 面向图计算提供的框架与算法库。

---

### -3- Spark和MR对比 

1. 计算速度
	1. 磁盘I/O：Spark处理数据==基于内存==的，而MapReduce是基于磁盘处理数据的。
	2. 并行度：Spark会增加任务的==并行度==从而提高速度：由于将中间结果写到磁盘与从磁盘读取中间结果属于不同的环节，MR只是将它们简单的通过串行执行衔接起来。而Spark把不同的环节抽象为Stage，允许多个Stage既可以串行执行，又可以并行执行。
	3. DAG：Spark 拥有高效的调度算法，是基于 ==DAG有向无环图==的, 多个任务之间的通信基于内存，且在计算过程中减少了shuffle以及落地磁盘（Action）的次数，
2. 资源
	1. MR是基于==进程==，Spark是基于==线程==。MR是多进程单线程模型，而Spark是多进程多线程模型
	2. Spark是粗粒度资源申请模式，而MR是细粒度资源申请模式
3. 容错
	1. Spark 引进了弹性分布式数据集 RDD (Resilient DistributedDataset) 的抽象，它是分布在一组节点中的只读对象集合，这些集合是弹性的，如果数据集一部分丢失，则可以根据“==血统==”（即允许基于数据衍生过程）对它们进行重建。另外在RDD 计算时可以通过 CheckPoint 来实现容错。而MapReduce的容错可能只能重新计算，成本较高。
4. 功能通用
	1. mapreduce 只提供了Map和Reduce两种操作，Spark提供的数据集操作类型有很多，大致分为：==Transformations和Actions==两大类。Transformations包括Map、Filter、FlatMap、GroupByKey、 ReduceByKey等多种操作类型，Actions包括reduce、collect、count、save、aggregate等操作。此外spark支持SQL、图论、机器学习;
5. 生态
	1. Spark框架和生态更为复杂，首先由RDD、血缘lineage、执行时的有向无环图DAG、stage划分等等。Spark作业都需要根据不同的业务场景的需要进行调优，以达到性能要求，MR框架及其生态相对较为简单，对性能的要求也相对较弱。
6. 运行环境
	1. MR运行在YARN上。Spark支持Local，YARN，Standalone Deploy Mode，Amazon EC2

---

###  2 Spark 和Hadoop的区别 

1. 应用场景不同
	1. Hadoop是一个在分布式服务器集群上存储海量数据并运行分布式 分析应用的==开源框架==
	2. Spark只是快速、通用、可扩展的==大数据分析引擎==
2. 处理速度不同
	1. Spark多个作业之间数据 通信是基于内存，而Hadoop 是基于磁盘。
3. 容错性不同
	1. Hadoop将每次处理后的数据都写入到磁盘上
	2. Spark的数据对象存储在弹性分布式数据集 RDD，RDD是分布在一组节点中的只读对象集合，如果数据集一部分丢失，则可以根据于数据衍生过程对它们进行重建。而且RDD 计算时可以通过 CheckPoint 来实现容错。
4. 联系
	1. 两者完全可以结合在一起，hadoop提供分布式==集群==和分布式==文件系统==，spark可以依附在hadoop的HDFS==代替MapReduce==弥补MapReduce计算能力不足的问题。

---

### 2 Spark和Hive对比

- Hive是基于Hadoop的一个==数据仓库工具==，可以将结构化的数据文件映射为一张表，并提供类SQL查询功能。
- Spark 是一种基于内存的快速、通用、可扩展的大数据分析==计算引擎==

要看实际使用场景。

1. Hive：
	1. 大数据存储
	2. 通过sql方式进行MapReduce操作，降低大数据使用门槛，成本低
	3. 用途：==数据存储和清洗==，处理==海量数据==，比如一个月、一个季度、一年的数据量，依然可以处理，虽然很慢。
2. Spark SQL：
	1. 基于内存操作，速度快
	2. 流式计算。
	3. 用途：数据清洗和流式计算，上述情况下Spark SQL不支持，无法处理，因为其基于内存，量级过大承受不住，并且性价比不如Hive高。

---

### 2 Hive on Spark / Spark on Hive 

实际应用中，经常把二者 结合起来使用。Spark和Hive结合和使用的方式

1. Hive on Spark（离线数仓使用）
	1. 如果用Hive on Mapreduce太慢了（十倍）
	2. Hive 作为==存储数据==和 ==SQL 解析优化==，语法是 ==HQL 语法==，执行引擎变成了 Spark，Spark 负责采用 RDD 执行。
2. Spark on Hive :
	1. Hive ==存储数据==，==Spark 负责 SQL 解析优化==，数据计算处理，语法是 Spark SQL语法，Spark 负责采用 RDD 执行。


---

### 1 Spark的架构

Spark 框架的核心是一个计算引擎，整体来说，它采用了标准 ==master-slave== 的结构。Driver 表示master， 负责管理整个集群中的作业任务调度。Executor 则是 slave，负责实际执行任务

1. **Driver**驱动器：用于执行 Spark 任务中的 main 方法，负责实际代码的执行工作
   1. 将用户程序转化为作业（job）
   2. 在 Executor 之间调度任务(task) 
   3. 跟踪 Executor 的执行情况 
   4. 通过 UI 展示查询运行情况
2. **Executor**：执行器，是集群中工作节点（Worker）中的一个 JVM进程，负责在 Spark 作业中运行具体任务（Task），任务彼此之间相互独立。
   1. 负责运行组成 Spark 应用的任务，并将结果返回给驱动器进程 ➢
   2. 它们通过自身的块管理器（Block Manager）为用户程序中要求缓存的 RDD 提供内存 式存储。RDD 是直接缓存在 Executor 进程内的，因此任务可以在运行时充分利用缓存 数据加速运算。
3. **Cluster Manager**：
   1. 主要负责资源的调度和分配，并进行集群的监控等职责，类似于Yarn 环境中的 RM
4. **Worker节点**：
   1. 对数据进行并行的处理和计算，类似于Yarn 环境中NM。

---

### 3Spark运行流程

1. 构建Application的运行环境，Driver创建一个==SparkContext==
2. SparkContext向资源管理器申请==Executor==资源，资源管理器启动
3. Executor向SparkContext==申请Task==
4. SparkContext将==应用程序==分发给Executor
5. SparkContext构建DAG图，DAGScheduler将DAG图解析成Stage，每个Stage有多个task，形成taskset 发送给task Scheduler，由task Scheduler将Task发送给Executor运行
6. Task在Executor上运行，运行完释放所有资源

---

### [0] Spark运行环境

1. Local 本地模式(单机)。分为 Local 单线程和 Local-Cluster 多线程。

2. Standalone 独立集群模式。 包含 Standalone 模式和 Standalone-HA 高可用模式。Standalone-HA 使用 Zookeeper 搭建高可用，避免单点故障问题。

3. Spark On Yarn 集群模式。运行在 Yarn 集群之上，由 Yarn 负责资源管理，Spark 负责任务调度和计算。Spark on YARN 模式根据 Driver 在集群中的位置分为两种模式：一种是 YARN Client 模式，另一种是 YARN-Cluster (或称为 YARN-Standalone 模式)。
   1. Yarn-Client模式中，Driver在==客户端本地==运行，这种模式可以使得Spark Application和客户端进行交互，适用于交互、调试，希望立即看到app的输出

   2. Yarn-Cluster模式中，Driver运行在==ApplicationMaster==中；适用于生产环境

4. K8S & Mesos 模式

---

### [0] YARN Cluster 模式下的执行流程

1. 任务提交后会和 ResourceManager 通讯申请启动ApplicationMaster，
2. RM在合适的 NM上启动Container，并分配 AM，
3. NM接到RM的分配，启动AM并初始化作业，此时 NM就称为Driver
4. AM向RM申请资源，RM分配资源的同时通知其他NM启动相应的Executor。
5. Executor向NM上的AM注册汇报并完成相应的任务

---

### Spark提交job的流程

1. Stage==划分与提交==
   1. Job按照RDD之间的依赖关系是否为宽依赖，由DAGScheduler划分为一个个Stage，并将每个Stage提 交给TaskScheduler
   2. Stage随后被提交，并由TaskScheduler将每个stage转化为一个TaskSet
2. Task==调度与执行==
   1. 由TaskScheduler负责将TaskSet中的Task调度到Worker节点的Executor上执行

---

### ⭐ RDD 属性 / 缺点

RDD（Resilient Distributed Dataset）叫做弹性分布式数据集，RDD 为一个分布式对象集合，本质上是一个只读的分区记录集合。每个 RDD 可以分成多个分区，每个分区就是一个数据集片段。一个 RDD 的不同分区可以保存到集群中的不同结点上，从而可以在集群中的不同结点上进行并行计算
1. 特点
	1. 弹性
		1. 存储的弹性：内存与磁盘的自动切换；
		2. 容错的弹性：数据丢失可以自动恢复；
		3. 计算的弹性：计算出错重试机制；
		4. 分片的弹性：可根据需要重新分片。
	2. 分布式：数据自动分布在大数据集群不同节点上
	3. 数据集：RDD 封装了计算逻辑，并==不保存数据==
	4. 数据抽象：RDD 是一个抽象类，需要子类具体实现
	5. 只读：不能修改，只能通过转换操作生成新的 RDD。
2. RDD的属性
	1. 分区列表 
	2. 分区器
	3. 分区计算函数
	4. 依赖关系
	5. 首选位置
3. 缺点
	1. 不支持细粒度的写和更新操作
		1. （如网络爬虫）， spark 写数据是粗粒度的所谓粗粒度，就是批量写入数据，为了提高效率。但是读数据是细粒度的也就是说可以一条条的读。
	2. 不支持增量迭代计算
		1.  Flink 支持

---

### 1 RDD / DataFrame / DataSet

1. RDD
	1. RDD弹性分布式数据集，是Spark中最基本的数据抽象。代码中是一个抽象类，它代表一个不可变、可分区、里面的元素可并行计算的集合。
	2. RDD==不支持 SparkSQL==  操作，一般和 ==spark mllib== 同时使用
2. DataFrame
	1. 是以RDD为基础的分布式数据集，类似于传统数据库中的二维表格。前者带有schema元信息，即DataFrame所表示的二维表数据集的每一列都带有名称和类型。
	2. 每一行的类型固定为Row, 但是每一列的值没法直接访问，只有通过解析才能获取各个字段的值。
	3. 性能上比 RDD 要高，主要原因是会对执行计划进行优化
	4. ==均支持 SparkSQL== 的操作，一般不与 spark mllib 同时使用
3. DataSet
	1.  Dataset 和DataFrame 拥有完全相同的成员函数，区别只是每一行的数据类型不同。Dataset 中，每一行是什么类型是不一定的，
	2.  Dataset支持编解码器，当需要访问非堆上的数据时可以避免反序列化整个对象，提高了效率

---

### 2 转换算子和行动算子

Spark算子主要划分为两类：transformation和action，并且只有action算子触发的时候才会真正执行任务，触发job执行形成DAG；这样有利于减少内存消耗，提高了执行效率。

1. Transformation是==得到一个新的RDD==
	1. ==map==：将处理的数据逐条进行映射转换
	2. ==filter==：将数据根据指定的规则进行筛选过滤，符合规则的数据保留，不符合规则的数据丢弃。
	3. flatMap：将处理的数据进行扁平化后再进行映射处理，所以算子也称之为扁平映射
	4. ==union==：返回一个新的数据集，由原数据集和参数联合而成。
	5. groupByKey：将数据源的数据根据 key 对 value 进行分组
	6. reduceByKey：可以将数据按照相同的Key 对Value 进行聚合
	7. join：在类型为（K,V)和（K,W)类型的数据集上调用，返回一个（K,(V,W))对， 每个key中的所有元素都在一起的数据集。
2. Action是==得到一个值==，或者一个结果
	1. reduce：通过函数func聚集数据集中的所有元素。Func函数接受2个参数，返回一个值。这个函数 必须是关联性的，确保可以被正确的并发执行。 
	2. collect()：在Driver的程序中，以数组的形式，返回数据集的所有元素。这通常会在使用filter或者其它操 作后，返回一个足够小的数据子集再使用，直接将整个RDD集Collect返回，很可能会让Driver程序OOM。 
	3. count()：返回数据集的元素个数。 
	4. foreach(func): 在数据集的每一个元素上，运行函数func。这通常用于更新一个累加器变量，或者和外部 存储系统做交互。
---

###  2 RDD的持久化

1. ==Cache== 缓存 将结果存入内存
	1. cache只有一个默认的缓存级别MEMORY_ONLY，血缘关系保留，宕机后可以通过依赖链重放计算出来
2. ==Persist==机制 将结果存入磁盘
	1. persist可以根据情况设置其它的缓存级别
3. ==checkpoint== 将结果存入HDFS
	1. checkpoint 检查点==切断血缘依赖==
	2. job 结束后另外启动专门的 job 去完成 checkpoint 。RDD 会被计算两次。因此，在使用 rdd.checkpoint() 的时候，建议加上 rdd.cache()
	3. Checkpoint的RDD，先执行cache/persist，直接从内存/磁盘上读取rdd的数据，更高效
4. Lineage机制
	1. 将粗颗粒度相同的操作（map flatmap filter之类的）记录下来，万一RDD信息丢失 可通过Lineage获取信息从新获得原来丢失的RDD


---

### Checkpoint
1. 哪些rdd需要
	1. -计算需要很长时间的
	2. 计算链太长的
	3. 依赖于太多的父RDD
2. Checkpointing可以将RDD从其依赖关系中抽出来，保存到可靠的存储系， 即它可以将数据和元数据保存到检查指向目录中。 因此，在程序发生崩溃的时候，Spark可以恢复此数据，并从停止的任何地方开始

**步骤**

1.  rdd.checkpoint() 设定哪些 rdd 需要 checkpoint，设定存储路径
2. RDDCheckpointData 会将 rdd 标记为 MarkedForCheckpoint。
3. 每个 job 运行结束后 回溯扫描，碰到要 checkpoint 的 RDD 就将其标记为 CheckpointingInProgress，然后将写如hdfs需要的配置文件广播到其他节点。完成以后，启动一个 job 来完成 checkpoint
4. job 完成 checkpoint 后，将该 rdd 的依赖全部清掉，并设定该 rdd 状态为 checkpointed。

---

### 0 RDD血缘关系 Lineage 
1. RDD 通过操作算子进行转换，转换得到的新 RDD 包含了从其他 RDD 衍生所必需的信息，RDDs 之间维护着这种依赖关系，也称之为依赖。
2. RDD的血缘机制将创建 RDD 的一系列==粒度相同的操作==记录下来，以便之后恢复丢失的分区

---

###  3 RDD的宽窄依赖

1. 窄依赖表示每一个上游RDD的分区最多被下游RDD的==一个分区==使用，（不会产生shuffle）
	  1. map，filter，union
2. 宽依赖表示同一个上游RDD的分区被下游RDD的==多个分区==依赖，（==产生shuffle==）
	  1. sort，reduceByKey，groupByKey，join
---

### 2 reduceByKey / groupByKey

1. shuffle
	1. reduceByKey 和 groupByKey 都存在 ==shuffle== 的操作
	2. reduceByKey 可以在 shuffle ==前对分区内相同 key 的数据进行预聚合==（combine）功能，这样会减少落盘的数据量
	3. groupByKey 只是进行分组，不存在数据量减少的问题，reduceByKey 性能比较 高。
2. 功能
	1. reduceByKey 包含分组和聚合的功能。
	2. GroupByKey 只能分组，不能聚合，

   所以在分组聚合的场合下，推荐使用 reduceByKey，仅分组，使用 groupByKey

---

### 1 reduceByKey、foldByKey、aggregateByKey、combineByKey

1. reduceByKey  
	1. 可以将数据按照相同的Key 对Value 进行聚合
	2. 没有初始值  分区内和分区间逻辑相同
2. foldByKey  
	1. 当分区内计算规则和分区间计算规则相同时，aggregateByKey 就可以简化为 foldByKey
	2. 有初始值  分区内和分区间逻辑相同
3. aggregateByKey 
	1. 将数据根据不同的规则进行分区内计算和分区间计算
	2. 有初始值  分区内和分区间逻辑可以不同
4. combineByKey  
	1. 初始值可以变化结构（发现数据结构不满足要求时，可以让第一个数据转换结构）  分区内和分区间逻辑不同

---

### -3- RDD 任务划分/调度

RDD 任务切分中间分为：Application、Job、Stage 和 Task
1. ==Application==
	1. 初始化一个 ==SparkContext== 即生成一个 Application；
	2. Application是spark的一个应用程序，它包含了客户端写好的代码以及任务运行的时候需要的资源信息。
2. ==Job==：
	1. Driver解析代码，一个Action 算子就会生成一个 Job（DAG）；
3. ==Stage==：
	1. DAGScheduler负责Stage级的调度。
	2. DAGScheduler根据RDD的血缘关系构成的DAG进行切分
	3. 最终的RDD不断通过血缘依赖回溯判断父依赖是宽依赖，就创建一个stage；即以Shuffle为界，划分Stage，窄依赖的RDD都被划分到同一个Stage中（宽依赖+1）
	4. Stage提交时会将Task信息（主要是**分区信息**）序列化并被打包成TaskSet交给TaskScheduler，一个Partition对应一个Task。
4. ==Task==
	1. TaskScheduler负责Task级的调度。
	2. 将DAGScheduler给过来的TaskSet，封装为 TaskSetManager 加入到调度队列中。
	3. 一个stage有若干个task，一个 Stage 阶段中，==最后一个 RDD 的分区个数==就是 Task 的个数。


---

### 2 DAG

Directed Acyclic Graph，有向无环图。
顶点代表RDD，边代表对RDD的一系列操作。
原始的RDD通过一系列的转换就形成了DAG，根据RDD之间的依赖关系的不同将DAG划分成不同的Stage， 对于窄依赖，partition的转换处理在Stage中完成计算。对于宽依赖，由于有Shuffle的存在，只能在 parent RDD处理完成后，才能开始接下来的计算，宽依赖是划分Stage的依据

MapReduce的局限性主要有两个：

1. 每个MapReduce==操作都是相互独立==的，Hadoop不知道接下来会有哪些Map Reduce。 
2. 每一步的输出结果，都会==持久化==到硬盘或者HDFS上。

Spark 中引入了 DAG，它可以优化计算计划，比如减少 shuffle 数据。

---

### ⭐Spark Shuffle

Spark遇到宽依赖时，会划分 stage，从而需要 shuffle。根据Record的key对parent RDD进行重新分区。 将数据根据指定的规则进行==分组==, 分区默认不变，但是数据会被打乱重新组合，我们将这样 的操作称之为 shuffle。

1. Spark 0.8 以前 hash-based shuffle V1 
	1. Shuffle Write过程会按照hash的方式重组partition的数据，不排序。
2. Spark 2.0 sort-based shuffle
	1. 每个 Task 不会为后续的每个 Task 创建单独的文件，而是将所有对结果写入同一个文件。根据 key 进行排序。
	2. 在Reduce阶段，Reduce Task拉取数据做Combine时不再是采用HashMap，而是采用ExternalAppendOnlyMap，该数据结构在做Combine时，如果内存不足，会刷写磁盘，很大程度上保证了系统的鲁棒性，避免了大数据情况下的OOM。
3. ==shuffle write== 对数据按照指定规则进行分区排序预聚合
	1. 每个map端的任务为每个下游的ReduceTask生成一个文件，按照 Partition Id 排序，每个 Partition 内部再按照 Key 进行排序
4. ==shuffle read== 对上游 map task 生成的数据进行拉取处理
	1. Reduce端任务将Shuffle write生成的文件fetch到本地节点，如果Shuffle Read阶段有combiner操作，则它会把拉到的数据保存在一个SparkExternalAppendOnlyMap中进行合并。

---

### 2 Shuffle过程的算子(宽依赖)

1. 重分区
	1. repartition、repartitionAndSortWithinPartitions、coalesce(shuffle=true)
	2. 重分区一般会shuffle，因为需要在整个集群中，对之前所有的分区的数据进行随机，均匀的打乱，然后把数据放入下游新的指定数量的分区内。
2. bykey
	1. reduceByKey、groupByKey、sortByKey等。
	2. 聚合操作，那么肯定要保证集群中，所有节点上的相同的key，移动到同一个节点上进行处理。
3. join
	1. join、cogroup等。
	2. 两个rdd进行join，就必须将相同join key的数据，shuffle到同一个节点上，然后进行相同key的两个rdd数据的笛卡尔乘积。
4. 去重
	1. distinct

无shuffle操作的一些算子
如map，filter，union等。

---

### [0] MR和spark shuffle的区别

1. 本质上相同，都是把Map端数据分类处理后交由Reduce的过程。
2. 数据流有所区别，
	1. MR有明确阶段，按map, spill, merge, shuffle, sort, reduce等各阶段逐一实现。
	2. Spark基于DAG数据流，只有不同的 stage 和一系列的 转换算子，可实现更复杂数据流操作（根据宽/窄依赖实现）
3. 实现功能上有所区别，
	1. MR在map中做了排序操作，
	2. Spark假定大多数应用场景Shuffle数据的排序操作不是必须的，而是采用Aggregator机制（Hashmap每个元素<K,V>形式）实现。

---

###  [0] Spark广播变量和累加器

在默认情况下，当 Spark 在集群的多个不同节点的多个任务上并行运行一个函数时，它会把函数中涉及到的每个变量，在每个任务上都生成一个副本。但是，**有时候需要在多个任务之间共享变量，或者在任务(Task)和任务控制节点(Driver Program)之间共享变量**。

为了满足这种需求，Spark 提供了两种类型的变量：

1. 累加器 accumulators==只写变量==

   1. 支持在所有不同节点之间进行==累加计算==(比如计数或者求和)。在driver端定义，在Excutor端更新，更新后传回driver端进行合并。
2. 广播变量 broadcast variables ==只读变量==；

   1. 变量在所有节点的内存之间进行共享，在每个机器上缓存一个只读的变量，而不是每个任务都生成一个副本。
   2. 适用于高效分发较大的对象。

---

### 3 Spark的容错机制

分布式数据集的容错性有两种方式：数据检查点（会发生拷贝，浪费资源）和记录数据的更新。

1. Lineage机制

   RDD的血缘机制将创建 RDD 的一系列==粒度相同的操作==记录下来，本质上类似于重做日志（Redo Log），只不过这个重做日志粒度很大，是对全局数据做同样的重做进而恢复数据。

   1. 当这个RDD的部分分区数据丢失时，它可以通过Lineage获取足够的信息来重新运算和恢复丢失的数据分区
   2. ==窄依赖==只需要重新计算丢失的那一块数据来恢复
   3. ==宽依赖==则要将祖先RDD 中的所有数据块全部重新计算来恢复。

2. Checkpoint机制

   将RDD写入hdfs做检查点（类似于edits -> fsimage）

---

### ⭐ Spark数据倾斜问题

Spark中的数据倾斜问题主要指shuffle过程中出现的数据倾斜问题，是由于==不同的key==对应的数据量不同导致的==不同task==所处理的数据量不同的问题

导致：1.Out Of Memory 2.运行速度慢
表现：1）Spark作业只有几个task执行的非常慢 / 反复执行几次都在某一个task报出OOM错误
**定位**
1. 查阅代码中的shuffle算子，例如reduceByKey、sortbykey、groupByKey、join等算子，根据代码逻辑判断此处是否会出现数据倾斜
2. 查看Spark作业的log文件，log文件对于错误的记录会精确到代码的某一行，可以根据异常定位到的代码位置来明确错误发生在第几个stage，对应的shuffle算子是哪一个；

**处理**
1. 聚合源数据
	1. 避免shuffle过程
		  1. 通过Hive来进行数据预处理，让Spark直接使用预处理的Hive中间表
	2. 增大key粒度（减小数据倾斜可能性，增大每个task的数据量）
2. ==过滤==导致倾斜的key
	1. 如果在Spark作业中允许丢弃某些数据，那么可以考虑将可能导致数据倾斜的key进行过滤，滤除可能导致数据倾斜的key对应的数据
3. 提高shuffle操作的==并行度==
	1. 增加shuffle read task的数量，可以让原本分配给一个task的多个key分配给多个task，从而让每个task处理比原来更少的数据。
4. ==两阶段聚合==
	1. 第一次是局部聚合，先给每个key都打上一个随机数。
	2. 第二次然后将各个key的前缀给去掉，再次进行全局聚合操作。
5. 将reduce join转换为map join
	1. join操作都会执行shuffle 过程，并且执行的是reduce join。在小表join大表的情况，==广播小表+map算子==，实现和join一样的操作
6. ==Sample采样==对倾斜key单独进行join
	1. 少量key。通过采样获得数据量大的key，将少数几个key分拆成独立RDD，加随机前缀打散成n份去进行join，此时这几个key对应的数据就不会集中在少数几个task上，而是分散到多个task进行join了
7. 使用随机数以及扩容进行join
	1. 大量key。通过附加随机前缀变成不一样的key，对正常RDD扩容，数据分散到多个task中去处理。对内存占用大

---

### -3- Spark 小文件  
1. 通过Spark的coalesce()方法和repartition()方法
	1. 最后的DataSet的分区数,
2. 降低spark并行度
	1. 调节spark.sql.shuffle.partitions
3. 新增一个并行度=1任务，专门合并小文件

### JOIN  
[[bigdata_intv#Hive#3 Map join]]
1.  Broadcast Hash Join（小表10M JOIN 大表）
	2. broadcast ：小表广播到大表的各个分区上（内存中）
	3. hash join：小表映射成hashtable，根据大表中记录的join key的hash值拿来进行匹配
2. shuffle hash join（小表 JOIN 大表）
	1. shuffle：将两个表按照join key进行分区，
	2. hash join：小表映射成hashtable，根据大表中记录的join key的hash值拿来进行匹配 
3.  sort-merge join （大表 JOIN 大表） 
	1. shuffle：将两个表按照join key进行分区，
	2. sort：对单个分区节点的两表数据，分别进行排序
	3. merge：对排好序的两张分区表数据执行join操作。分别遍历两个有序序列，碰到相同join key就merge输出，否则继续取更小一边的key
---

### ⭐ Spark 性能调优

1. 常规性能调优
	1. 最优资源配置
		1. 根据资源队列的实际情况（内存，CPU核数），配置Executor的数量，内存，CPU核数（8核2G）
	2. RDD优化
		  1. RDD复用
			  1. 要避免==相同==的算子和计算逻辑之下对RDD进行重复的计算
		  2. RDD持久化
			 1. 在Spark中，多次对同个RDD执行算子操作时，每一次都会对这个RDD以之前的父RDD重新计算一次，这种情况是必须要避免的，对同一个RDD的重复计算是对资源的极大浪费。==对多次使用的RDD进行持久化==，之后对于公共RDD的计算都会从内存/磁盘中直接获取RDD数据。
		  3. RDD尽可能早的filter操作
			 1. 获取到初始RDD后，尽早地过滤掉不需要的数据，进而减少对内存的占用，从而提升Spark作业的运行效率。
	2. 并行度调节	
		1. 并行度指各个stage的task的数量。如果并行度设置不合理而导致并行度过低，会导致资源的极大浪费
		2. task数量（也就是并行度）应该设置为Spark作业总CPU core数量的2~3倍
	3. 广播大变量
		  1. 默认情况下，task中的算子中如果使用了外部的变量，每个task都会获取一份变量的==复本==，这就造成了内存的极大消耗；
		  2. 广播变量在每个==Executor==保存一个副本，此Executor的所有task共用此广播变量，这让变量产生的副本数量大大减少。
	4. Kryo序列化
	5. 调节本地化等待时长
2. 算子调优
	1. mapPartitions代替map
		  1. map算子对RDD中的每一个元素进行操作，而mapPartitions算子对RDD中每一个分区进行操作。
		  2. 数据量不是特别大时，用mapPartitions算子代替map
	2. foreachPartition代替foreach
		  1. foreach算子完成数据库的操作，遍历RDD的每条数据，并建立数据库连接。
		  2. foreachPartition是将RDD的每个分区作为遍历对象，
	3. filter + coalesce
	4. repartition解决SparkSQL低并行度问题
	5. reduceByKey代替groupByKey
		  1. 由于reduceByKey有map端聚合的特性，使得网络传输的数据量减小， 因此效率要明显高于groupByKey。
3. **shuffle调优**
	1. 调大map端==缓冲区大小==
		1. 如果shuffle的map端处理的数据量比较大。可以增大map端缓冲的大小，减少溢写次数
	2. 调大reduce端拉取数据缓冲区大小
		1. 增加拉取数据缓冲区的大小，减少拉取数据的次数，
	3. 增大reduce端拉取数据==重试次数== / ==等待间隔==
		1. 增加shuffle操作的稳定性。
	4. 调节Sort-Shuffle排序操作阈值
4. jvm调优
	1. 降低cache操作的内存占比
	2. 调大Executor堆外内存
	3. 调大连接等待时长

---



### **Spark Streaming是什么？**

Spark Streaming 用于流式数据的处理；Spark Streaming 支持的数据输入源很多，例如：Kafka、Flume等等。数据输入后可以用 Spark 的高度抽象原语如：map、reduce、join、window 等进行运算。而结果也能保存在很多地方，如 HDFS，数据库等。

Spark Streaming 使用离散化流(discretized stream)作为抽象表示，叫作 DStream。DStream 是随时间推移而收到的数据的序列。在内部，每个时间区间收到的数据都作为 RDD 存在，而 DStream 是由这些 RDD 所组成的序列(因此得名“离散化”)。所以简单来将，DStream 就是对 RDD 在实时数据处理场景的一种封装。

**所以：**

Spark Streaming 中的流式计算其实并不是真正的流计算，而是微批计算。Spark Streaming 把流式计算当做一系列连续的小规模批处理(batch)来对待（RDD）。Spark Streaming 接收输入数据流，并在内部将数据流按均匀的时间间隔分为多个较小的batch。然后再将这部分数据交由Spark引擎进行处理，处理完成后将结果输出到外部文件。------**Spark Streaming** **如何执行流式计算的?**

---

### 2 Spark Streaming从Kafka中读取数据

1. ReceiverAPI
   1. 需要一个专门的 Executor 去接收数据，然后发送给其他的 Executor 做计算。接收数据的 Executor 和计算的 Executor 速度会有所不同，特别在接收数据的 Executor 速度大于计算的 Executor 速度，会导致计算数据的节点内存溢出。
1. DirectAPI
   1. 不使用Receiver来接收数据，而是向Kafka==定期查询==每个主题的每个分区中的==最新offset==，并==定义==要在每个批次中处理的==偏移量范围==。当Spark Streaming启动处理数据的作业时，利用Kafka的低阶API读取Kafka定义的偏移范围的数据。
   2. 把`"auto.commit"`设置为 false，实现手动提交和获取偏移量，用redis作为偏移量的存储。key是topic+groupid，值是hash字段，field 为分区 ，value为offset



# Mysql

### 非关系 / 关系 型数据库

1. 关系型数据库
	1. 由==二维表==及其之间的关系组成的一个数据组织。存储的是结构化的数据；MySQL、Oracle
	2. 易于维护。使用方便。
	3. 读写性能较差。高并发表现较差
2. 非关系型数据库
	1. 严格上不是一种数据库，而是一种数据结构化存储方法的集合，可以是文档或者键值对等。 Hbase，Elasticsearch ，Redis，ClickHouse 
	2. 格式灵活。速度快。高拓展。成本低

---

###  MySQL架构

1. 网络连接层：提供与Mysql服务器建立连接的支持
2. 核心服务层：主要包含 系统管理控制工具、连接池、SQL接口、解析器、查询优化器和缓存六个部分
3. 存储引擎：负责Mysql中数据的存储与提取，与底层系统文件进行交互
4. 文件系统：负责将数据库的数据和日志存储在文件系统之上，并完成与存储引擎的交互，是文件的物理存储层

---

### SQL执行流程

1. 连接器
2. 查询缓存
3. 解析 SQL
	1. 词法分析。识别出关键字出来，构建出 SQL 语法树。
	2. 语法分析。判断是否满足 MySQL 语法。
4. 执行 SQL
	1. 预处理阶段
		1. 检查 SQL 查询语句中的表或者字段是否存在；
		2. 将 select * ，扩展为表上的所有列；
	2. 优化阶段
		1. 基于查询成本的考虑， 选择查询成本最小的执行计划；
	3. 执行阶段
		1. 根据执行计划执行 SQL 查询语句，从存储引擎读取记录，返回给客户端；

---

### 2 MyISAM / InnoDB 

MyISAM ：做很多count 的计算。查询非常频繁。没有事务。

1. 事务：
	1. MyISAM不支持事务。InnoDB支持事务；
2. ==不支持全文索引==
	1. MyISAM 支持全文索引。InnoDB 5.6 之前不支持全文索引；
3. count()
	1. MyISAM会直接存储总行数。InnoDB 则不会，需要按行扫描。
4. 外键约束
	1. MyISAM 不支持外键。InnoDB 支持外键；
5. 行级锁
	1. MyISAM 只支持表锁，InnoDB 可以支持行锁。
6. MVCC
	1. MyISAM 不支持，而 InnoDB 支持。


---

### -2- MySQL锁机制

1. 全局锁
	1. 整个数据库就处于只读状态
2. 表级锁
	1. 表锁；
	2. 元数据锁（MDL）
	3. 意向锁；
	4. AUTO-INC 锁
1. 行级锁
	1. Record Lock
		1. 记录锁，仅仅把一条记录锁上；
	2. Gap Lock
		1. 间隙锁，锁定一个范围，但是不包含记录本身；
	3. Next-Key Lock
		1. Record Lock + Gap Lock 的组合，锁定一个范围，并且锁定记录本身。左开右闭


---

### 1 死锁
1. 分析
	1. 报Deadlock异常
	2. 查询事务隔离级别 查询事务隔离级别select @@tx_isolation
	3. 查询数据库死锁日志 show engine innodb status
2. 原因：
	1. 由于间隙锁是共享的，当两个事务获取到了相同范围的间隙锁，并且两个事务往范围内插入记录，那么两个事务会等待间隙锁释放而全部阻塞，形成死锁
	2. 互斥、占有且等待、不可强占用、循环等待
3. 避免
	1. 设置事务等待锁的超时时间，超时就回滚事务；开启主动检测死锁，检测到了就回滚

---

### ⭐事务四个特性

事务是应用程序中一系列严密的操作，所有操作必须成功完成，否则在每个操作中所作的所有更改都会被撤消。也就是事务具有原子性，一个事务中的一系列的操作要么全部成功，要么一个都不做。

ACID
1. ==原子性== Atomicity
	1. 事务是最小的执行单位，不允许分割。事务的原子性确保动作要么全部完成，要么完全不起作用；
	2. ==undo log==（回滚日志） 来保证的；
		1. 每条数据变更操作都伴随一条undo log的生成，优先据持久化到磁盘上。中途崩溃，可以通过这个日志回滚到事务之前的数据
2. ==一致性== Consistency
	1. ==执行事务前后==，数据库保持一致性状态；
	2. 持久性 + 原子性 + 隔离性来保证；
3. ==隔离性== Isolation
	1. 并发访问数据库时，一个用户的事务不被其他事务所干扰，==各并发事务之间数据库是独立的==；
	2. ==MVCC==（多版本并发控制） 或锁机制来保证的；
4. ==持久性== Durability
	1. 一个事务被提交之后。它==对数据库中数据的改变是持久的==，即使数据库发生故障也不应该对其有任何影响。
	2. ==redo log== （重做日志）来保证的
	3. redo log 是物理日志，记录了某个数据页做了什么修改。记录的是事务完成后，更新后的数据。

---

### 3 并发事务带来哪些问题

1. 脏读
	1. 读到其他事务未提交的数据
2. 不可重复读
	1. 前后读取的数据不一致
	2. 例子：a事务读取两次读取数据间隔中，被b事务update，delete并提交
3. 幻读
	1. 前后读取的记录数量不一致
	2. 例子：a事务查询两次读取数据间隔中，被b事务insert并提交

---

### [0] 开启事务

- 第一种：begin/start transaction 命令；
  - 只有在执行这个命令后，执行了增删查改操作的 SQL 语句，才是事务真正启动的时机；
- 第二种：start transaction with consistent snapshot 命令；
  - 马上启动事务。

---

### 3 事务的隔离级别

读读可串

1. 读未提交
	1. 直接读取最新的数据
	2. 一个事务还没提交时，它做的变更就能被其他事务看到
2. 读提交
	1. 语句执行前都会生成一个 Read View
	2. 一个事务提交之后，它做的变更才能被其他事务看到
	3. 允许读取并发事务已经提交的数据，只值==阻止脏读==
3. 可重复读
	1. 启动事务时生成一个 Read View
	2. 一个事务执行过程中看到的数据，一直跟这个事务启动时看到的数据是一致的，MySQL InnoDB 引擎的==默认隔离级别==
	3. 只阻止==脏读和不可重复读==
4. 串行化
	1. 对记录加读写锁，避免串行
	2. 在多个事务对这条记录进行读写操作时，如果发生了读写冲突的时候，后访问的事务必须等前一个事务执行完成，才能继续执行

---

### [0] ReadView
1. Read View 相当于数据快照。读提交在 每个语句执行前 都会重新生成ReadView，可重复读 是 启动事务时。
	1. m_ids ：「启动但还没提交的事务」的事务 id 列表
	2. min_trx_id ：「启动但还没提交的事务」中事务 **id 最小的事务**。
	3. max_trx_id ：全局事务最大的事务 id 值 + 1；
	4. creator_trx_id ：创建该 Read View 的事务的事务 id。
---

### 3 MVCC
MVCC是多版本并发控制协议，避免频繁加锁，它实现==读不加锁，读写不冲突==。
1. 通过read view + undo log
2.  Read View是一个快照，保存了当前事务id，未提交最小事务，未提交最大事务，事务列表
	1. 「读提交」在「每个语句执行前」生成一个 Read View，「可重复读」在「启动事务时」生成一个 Read View
3. 事务对某条记录进行改动时，就会分配一个单向增长的隐藏事务 id，指向上一个版本记录的指针roll_pointer
4. 在某个事务对一条记录进行操作的时候，需要查看这一条记录的隐藏列中的事务 id，根据事物隔离级别去判断读取哪个版本的数据。

read view+ undo log
1. Read View是一个快照，其中主要保存了当前事务id，活跃（启动未提交）事务id列表，最小活跃事务id和最大活跃事务序号+1。
2. 回滚日志。每行记录中有两个隐藏字段，最近修改该记录的事务id trx_id，指向上一个版本记录的指针（形成历史版本链）roll_pointer
4. 对于读提交隔离级别：语句执行前生成 read view，并且事务在每次读取数据时都会重新创建Read View
5. 对于可重复读隔离级别：事务开始时生成 read view，直到事务结束都使用这个版本
6. 当读取数据时，数据中有隐藏信息包括：最近修改该记录的事务id，指向上一个版本记录的指针（形成历史版本链），事务会判断该记录的版本是否符合要求，如果不符合就追溯历史版本链找到合适的记录进行读取

**Misc**
1. 回滚日志
	1. 用于记录数据被修改前的信息。在表记录修改之前，会先把数据拷贝到undo log里，如果事务回滚，即可以通过undo log来还原数据。
	2. 可以这样认为，当delete一条记录时，undo log 中会记录一条对应的insert记录，当update一条记录时，它记录一条对应相反的update记录。
	3. 事务回滚时，保证原子性和一致性。用于MVCC快照读。
2. 隐式字段
	1. 对于使用 InnoDB 存储引擎的数据库表，它的聚簇索引记录中都包含下面两个隐藏列：
		1. trx_id  记录操作该数据事务的事务ID。事务每次开启前，都会从数据库获得一个单向增长的事务ID，可以从事务ID判断事务的执行先后顺序。
		2. roll_pointer 相当于一个指针，指向回滚段的undo日志。多个事务并行操作某一行数据时，不同事务对该行数据的修改会产生多个版本，通过回滚指针，连成一个版本链
3. 快照读和当前读
	1. 快照读： 读取的是记录数据的可见版本（有旧的版本）。不加锁,普通的select语句都是快照读,如：
		1. select * from core_user where id > 2;
	2. 当前读：读取的是已经完成提交的最新的版本数据，update类型、显式加锁的都是当前读
		1. select * from core_user where id > 2 for update;
		2. select * from account where id>2 lock in share mode;
4. 1. Read View    
	1. `trx_id < min_trx_id` ，表明生成该版本的事务在生成Read View前已提交，所以该版本的记录对当前事务可见。
	2. `trx_id>= max_trx_id` ，表明生成该版本的事务在生成ReadView后才生成，所以该版本的记录对当前事务不可见。
	3. `min_trx_id =<trx_id< max_trx_id`,需要分2种情况讨论：在数组内（只有自己可读）
		1. 不在`m_ids`，则代表生成Read View生成时已提交，因此是可见的。
		2. 在`m_ids`，则代表生成Read View生成时未提交，因此是不可见的。
5. 流程
	1. 获取事务自己的事务ID
	2. 获取Read View
	3. 查询目标数据，然后与Read View中的字段进行比较。
	4. 如果不符合Read View的可见性规则， 即就需要Undo log中历史数据 ;
	5. 最后返回符合规则的数据

---


### 2 可重复读不能完美解决幻读

1. 针对**快照读**（普通 select 语句），是**通过 MVCC 方式解决了幻读**，因为可重复读隔离级别下，事务执行过程中看到的数据，一直跟这个事务启动时看到的数据是一致的，即使中途有其他事务插入了一条数据，是查询不出来这条数据的，所以就很好了避免幻读问题。
   1. 可重复读隔离级是由 MVCC（多版本并发控制）实现的，实现的方式是开始事务后（执行 begin 语句后），在执行第一个查询语句后，会创建一个 Read View，**后续的查询语句利用这个 Read View，通过这个 Read View 就可以在 undo log 版本链找到事务开始时的数据，所以事务过程中每次查询的数据都是一样的**，即使中途有其他事务插入了新纪录，是查询不出来这条数据的，所以就很好了避免幻读问题。
2. 针对**当前读**（select ... for update 等语句），是**通过 next-key lock（记录锁+间隙锁）方式解决了幻读**，因为当执行 select ... for update 语句的时候，会加上 next-key lock，如果有其他事务在 next-key lock 锁范围内插入了一条记录，那么这个插入语句就会被阻塞，无法成功插入，所以就很好了避免幻读问题
   1. Aselect不存在（ReadView），Binsert，Aupdata，Aselect存在
   2. Aselect n条记录（ReadView），Binsert，Aselect n+1条记录
   3. **是尽量在开启事务之后，马上执行 select ... for update 这类当前读的语句**

---

###⭐谈谈你对索引的理解 ？ 

1. 目的
	1. 索引的出现是为了提高数据的查询效率，就如同书的目录一样。
2. 优点
	1. ==提高查询性能==：使用索引可以大大加快数据的检索速度（大大减少检索的数据量）。
	2. ==实现唯一性约束==：通过创建唯一性索引，可以保证数据库表中每一行数据的唯一性。
	3. ==加速排序和连接操作==：索引对于排序和连接操作也非常有用。例如，当执行`ORDER BY`语句时，MySQL可以利用索引的排序顺序，直接按照索引进行排序，而不需要对整个表进行排序。对于连接操作，如果涉及到连接的列上有索引，MySQL可以利用索引快速定位和匹配连接的数据行。
3. 索引缺点
	1. ==占空间==：占用物理文件存储空间
	2. ==耗时间==：创建索引和维护索引要耗费时间
	3. ==降效率==：会降低表的增删改的效率，因为每次增删改索引，B+ 树都需要进行动态维护。
4. 适合建立索引的字段
	1. ==唯一性==。字段有唯一性限制的，比如商品编码；
	2. ==查询频繁==。经常用于 `WHERE` 查询条件的字段，这样能够提高整个表的查询速度，如果查询条件不是一个字段，可以建立联合索引。
	3. ==需要排序==。经常用于 `GROUP BY` 和 `ORDER BY` 的字段，这样在查询的时候就不需要再去做一次排序了，因为我们都已经知道了建立索引之后在 B+Tree 中的记录都是排序好的。
5. 不适合建立索引的字段
	1. ==少==。`WHERE` 条件，`GROUP BY`，`ORDER BY` 里用不到的字段，索引的价值是快速定位，如果起不到定位的字段通常是不需要创建索引的，因为索引是会占用物理空间的。
	2. ==重复==。字段中存在大量重复数据，不需要创建索引，比如性别字段
	3. ==表数据==。太少的时候，不需要创建索引；
	4. ==常更新==。经常更新的字段不用创建索引，比如不要对电商项目的用户余额建立索引，因为索引字段频繁修改，由于要维护 B+Tree的有序性，那么就需要频繁的重建索引，这个过程是会影响数据库性能的。

---

### [0] 索引为什么能加快查询速度

1. 默认的方式是根据搜索条件进行全表扫描，遇到匹配条件的就加入搜索结果集合。O(n)
2. 如果对某一字段增加索引， 查询时就会先去索引列表中查询，索引列表是B+树的数据结构。**现在O(logn)**

使用

1. 主键索引，用户ID id INT PRIMARY KEY
2. 唯一索引，银行卡号 email VARCHAR(255) UNIQUE
3. 普通索引，姓名 INDEX name_index(email)

---

### 3 B+ 树 / B 树 / Hash
**1B+ 树 / B 树** 
1. B树，是一种多路搜索树，每个节点存储多个关键字和多个指针。
2. B+树是B树的变体，==叶子节点==才存放数据，非叶子节点只存放==索引==，而且每个节点里的数据是按主键顺序存放的。因此查询数据时，时间复杂度固定为O(log n)。
	1. B+树能显著==减少IO次数==，提高效率
	2. B+树的查询==效率更加稳定==
	3. B+树更加适合在==区间查询==的情况
	4. B+ 树所有数据均存储在叶子节点，数据按主键顺序排列

**2 Hash**
1. 不适合做范围查询，只支持等值查找
2. 无法用于排序
3. 存在Hash冲突

---

### ⭐  索引分类
1. 按「数据结构」分类：B+tree索引、Hash索引、Full-text索引。
2. 按「物理存储」分类：聚簇索引、二级索引。
3. 按「字段特性」分类：主键索引、唯一索引、普通索引、前缀索引。
4. 按「字段个数」分类：单列索引、联合索引。

---

### 1 聚簇索引 / 二级索引
1. 聚簇索引的叶子节点存放的是==实际数据==，数据都存放在聚簇索引的叶子节点；
2. 二级索引的叶子节点存放的是==主键值==，而不是实际数据。
3. 回表：某个查询语句使用了二级索引，但是查询的数据不是主键值（覆盖索引），在二级索引找到主键值后，需要去聚簇索引中获得数据行（查两个B+树）

---

### [0] 最左匹配原则

通过将多个字段组合成一个索引，该索引就被称为联合索引。
匹配的时候严格从左到右匹配。
1. 最左前缀匹配原则会一直向右匹配直到遇到范围查询（>、<、between、like）就停止匹配

---

### -3- 索引失效

 Explain 命令来查看语句的执行计划。key： 实际使用的索引。如果为NULL，则没有使用索引。

1. 字段开头模糊查询。like关联字（%在前）
2. 查询条件中对索引列==使用函数==（IN (2,3)），==表达式计算==，==类型转换==，就会导致索引失效。
	1. IN (2,3) 换 BETWEEN 2 AND 3
3. 在 ==WHERE== 子句中，OR左边是索引列，右边不是
	1. OR 换 UNION
4. 联合索引遵循==最左匹配原则==
5. 索引列要设置为 NOT NULL 约束

---

### 2 索引优化

1. 前缀索引优化
	1. 使用某个字段中字符串的前几个字符建立索引，减小索引字段大
2. 覆盖索引优化
	1. 多个条件经常同时出现，可以考虑多个字段建立联合索引
3. 主键索引最好是自增的；
4. 索引最好设置为 NOT NULL
5. 防止索引失效

 

###   -3- SQL语句查询太慢
1. 定位慢查询
	1. 开启慢查询日志，SET GLOBAL slow_query_log = 1;
	2. 设置longquerytime 查询超过多少秒才记录
	3. 查看mysql-slow.log 或者 日志分析工具mysqldumpslow
2. 使用 ==Explain 命令==查询 SQL 语句执行计划； （看走没走索引）
	1. `id` sql语句执行的顺序
	2. `key` 实际使用的索引
	3. `rows` 显示MYSQL执行查询的行数
	4. `filtered` 百分比值，表示存储引擎返回的数据经过滤后，剩下多少满足查询条件记录数量的比例
	5. `type` 数据扫描类型
		1. ALL 就是没走索引
3. 查询性能的优化方法？
	1. 避免索引失效的情况[[#-3- 索引失效]]
	2. 索引优化
	3. 优化查询语句，避免笛卡尔积
	4. 缓存重复查询的数据：使用缓存可以避免在数据库中进行查询，特别在要查询的数据经常被重复查询时，缓存带来的查询性能提升将会是非常明显的。
	5. 建立合适的索引，快得多的速度检索特定的行，尤其是在查询语句当中包含有MAX(),MIN()和ORDERBY这些命令的时候，性能提高更为明显
4. 分库分表
	1. 垂直切分：将表结构进行细分，形成多个不同结构的表。例如电商数据库中将用户信息和商品信息切分
	2. 水平切分：将表数据分表存储，例如订单信息表按时间划分，每三个月形成一张表，或者按主键id通过hash映射到索引位置来进行表的划分
		1. 分表后就无法使用自增主键id，考虑使用分布式算法：例如雪花算法生成全局唯一id
5. 读写分离
	1. 采用代理服务器，根据请求类型、数据库负载情况进行转发
	2. 方案主库用来读，从库用来写，从而提高性能
		1. 读和写操作在各自的数据库中进行，避免了锁资源争抢
		2. 数据库冗余，增加可用性
		3. 从数据库可以使用MyISAM，节省开销提升查询性能





### 主从复制

MySQL使用binlog日志实现主从复制，一般采用异步模型：
1. 写入binlog：主库提交事务前保存binlog日志，提交事务后，更新主库数据（涉及binlog线程）
2. 复制binlog：调线程把binlog日志复制到从库，从库进行保存（涉及IO线程）
3. 回放binlog：从库通过回放binlog将数据进行更新（涉及SQL线程）
一般主库用于写，从库用于读，从而读写不会互相堵塞

 

**为什么要主从复制/优点**

- 随着系统中业务访问量的增大，如果是单机部署数据库，就会导致I/O访问频率过高。有了主从复制，增加多个数据存储节点，将负载分布在多个从节点上，降低单机磁盘I/O访问的频率，提高单个机器的I/O性能；
- 一般会让主库负责写，从库负责读，这样**读写分离**，即使主库出现了锁表的情景，通过读从库也可以保证业务的正常运作；
- 从库可以实时从主库进行复制，这样就可以做数据的热备；

 


### 32.主从复制涉及到哪三个线程？★★★★★

主要涉及三个线程：binlog 线程、I/O 线程和 SQL 线程。

1. binlog 线程（log dump线程） ：负责将主服务器上的数据更改写入二进制日志（Bin log）中。
2. I/O 线程 ：负责从主服务器上读取二进制日志，并写入从服务器的重放日志（Relay log）中。
3. SQL 线程 ：负责读取relay log中的内容，解析成具体的操作并执行，最终保证主从数据的一致性。



### 33.主从同步的延迟原因及解决办法？

**主从同步的延迟的原因：**

假如一个服务器开放 Ｎ 个连接给客户端，这样有会有大并发的更新操作, 但是从服务器的里面读取 binlog 的线程仅有一个， 当某个 SQL 在从服务器上执行的时间稍长或者由于某个 SQL 要进行锁表就会导致主服务器的 SQL 大量积压，未被同步到从服务器里。这就导致了主从不一致， 也就是主从延迟。

解决办法：

1. 采用更好的硬件设备
2. 增加从服务器，降低读的压力

3. 同步参数调整：主库是写，对数据安全性较高，比如sync_binlog=1，innodb_flush_log_at_trx_commit = 1 之类的设置是需要的。而slave则不需要这么高的数据安全，完全可以讲sync_binlog设置为0或者关闭binlog，innodb_flush_log_at_trx_commit 也可以设置为0来提高 SQL 的执行效率。

（sync_binlog=1，表示每次事务提交，MySQL都会把binlog刷写到磁盘，性能消耗大）；

（innodb_flush_log_at_trx_commit 默认值1的意思是每一次事务提交或事务外的指令都需要把日志写入（flush）硬盘，这是很费时的）





# Kafka

### 3 Kafka

Kafka 是一个分布式、高吞吐量的发布订阅消息系统，它可以处理消费者规模的网站中的所有动作流数据，主要应用于大数据实时处理领域。

1. **作用**
	1. 发布和订阅消息流 
	2. 以容错的方式记录消息流，kafka以文件的方式来存储消息流 
	3. 在消息发布的时候进行处理
2. **消息队列的功能**
	1. 解耦
		1. 通过消息队列，可独立的扩展或修改消息队列两边的处理过程，只要确保它们遵守同样的接口约束，实现了解耦。
	2. 缓冲/流量削峰
		1. 可以使用消息队列进行缓冲，能够使关键组件顶住突发访问造成流量高峰压力，而不会因为突发的超负荷的请求而完全崩溃。
	3. 异步通信
		1. 允许用户把一个消息放入队列，但并不立即处理它。想向队列中放入多少消息就放多少，然后在需要的时候再去处理它们。
3. **优势**
	1. 高吞吐、低延迟：kafka每秒可以处理几十万条消息，它的延迟最低只有几毫秒；
	2. 持久性、可靠性：消息被持久化到本地磁盘，并且支持数据备份防止数据丢失；
	3. 高并发：支持数千个客户端同时读写。
	4. 兼容性：Kafka 与周边生态系统的兼容性是最好的没有之一，尤其在大数据和流计算领域。
	5. 可扩展性：Kafka集群可以透明的扩展，增加新的服务器进集群。
	6. 容错性：允许集群中节点故障（若副本数量为n,则允许n-1个节点故障）；
	7. 多个生产者
	8. 多个消费者
4. **缺点**
	1. 非实时：Kafka采用异步批量发送的方式，所以数据达不到真正的实时
	2. 丢失数据或重复消费：如果kafka消费者消费完数据，来不及提交 offset，会造成数据重复消费；如果数据没有消费完成就提交了offset , 会出现丢数据的问题。
	3. 乱序：Kafka单个partition内部的消息是有序的，但是一个topic有多个partition的话，就不能保证有序了；topic一般需要人工创建，部署和维护成本高
   

### [ ] kafka的架构 

1. Producer
   1. 生产者负责创建消息。一般情况下，生产者在把消息均衡地分布到在主题的所有分区上，而并不关心消息会被写到哪个分区。如果我们想要把消息写到指定的分区，可以通过自定义分区器来实现。
2. Consumer：
   1. 消费者是消费者群组的一部分，消费者负责消费消息。消费者可以订阅一个或者多个主题，并按照消息生成的顺序来读取它们。消费者通过检查消息的偏移量 (offset) 来区分读取过的消息。偏移量是一个不断递增的数值，在创建消息时，Kafka 会把它添加到其中，在给定的分区里，每个消息的偏移量都是唯一的。消费者把每个分区最后读取的偏移量保存在 Zookeeper 或 Kafka 上，如果消费者关闭或者重启，它还可以重新获取该偏移量，以保证读取状态不会丢失。
3. Consumer Group（CG）：
   1. 消费者组，由多个consumer组成。消费者组内每个消费者负责消费不同分区的数据，==一个分区只能由一个消费者组的一个消费者消费==；消费者组之间互不影响。所有的消费者都属于某个消费者组，即消费者组是逻辑上的一个订阅者。

4. Broker 
   1. 一个独立的 Kafka 服务器被称为 Broker。Broker 接收来自生产者的消息，为消息设置偏移量，并提交消息到磁盘保存。Broker 为消费者提供服务，对读取分区的请求做出响应，返回已经提交到磁盘的消息。
5. Topic / Partition
   1. Kafka 的消息通过 Topics(主题) 进行分类，一个主题可以被分为若干个 Partitions(分区)，一个分区就是一个提交日志 (commit log)。消息以追加的方式写入分区，然后以先入先出的顺序读取。Kafka 通过分区来实现数据的冗余和伸缩性，分区可以分布在不同的服务器上，这意味着一个 Topic 可以横跨多个服务器，以提供比单个服务器更强大的性能。
6. Replica：副本，为保证集群中的某个节点发生故障时，该节点上的partition数据不丢失，且kafka仍然能够继续工作，kafka提供了副本机制，一个topic的每个分区都有若干个副本，其中包括一个leader和若干个follower。

7. leader：每个分区多个副本的“主”，生产者发送数据的对象，以及消费者消费数据的对象都是leader。

8. follower：每个分区多个副本中的“从”，实时从leader中同步数据，保持和leader数据的同步。leader发生故障时，某个follower会成为新的leader。



---



### 2 Kafka工作原理

**:one:发送数据**

**:two:保存数据**

Producer 将数据写入Kafka 后，Kafka单独开辟一块磁盘空间，将数据顺序写入磁盘。

**Partition结构**

- 在Kafka中，消息被组织成一个个topic（主题）。每个topic被划分为一个或多个partition（分区），每个partition是一系列有序、不可变的消息序列。每个消息都有一个唯一的offset（偏移量），用于标识消息在分区中的位置。
- ==Kafka使用日志（log）的方式来存储消息==。每个partition都有一个对应的log文件，称为日志段（log segment）。日志段以追加（append）的方式写入新的消息，并在达到一定大小或时间限制时进行切换。
- log文件中存储的就是Producer生产的数据。Producer生产的数据会被不断追加到该log文件末端，为防止log文件过大导致数据定位效率低下，Kafka采取了分片和索引机制， 将每个partition的log文件分为多个segment文件。每个segment主要包括：`.index`、`.log`和`.timeindex`。这些文件位于一个文件夹下，该文件夹的命名规则为：topic名称+分区序号，例如：first-0。

**Message结构**

 Log 文件就实际是存储 Message 的地方，往 Kafka 写入的也是一条一条的 Message

- Offset：Offset 是一个占 8byte 的有序 id 号，它可以唯一确定每条消息在 Parition 内的位置！ 
- 消息大小：消息大小占用 4byte，用于描述消息的大小。
- 消息体：消息体存放的是实际的消息数据（被压缩过），占用的空间根据具体的消息而不一样

**存储策略** ：旧数据存七天

**:three:消费数据**

Kafka 采用的是点对点的模式，消费者主动的去Kafka 集群拉取消息，与 Producer 相同的是，消费者在拉取消息的时候也是找 Leader 去拉取。多个消费者可以组成一个消费者组（Consumer Group），同一个消费组者的消费者可以消费同一 Topic 下不同分区的数据，但是不会组内多个消费者消费同一分区的数据！



[深入理解kafka——RecordAccumulator 和 InFlightRequests - 码出地球 - 博客园 (cnblogs.com)](https://www.cnblogs.com/leonandyou/p/15563776.html#:~:text=RecordAc,erBatch。)

[kafka3.x原理详解看这篇就够了 - rainple - 博客园 (cnblogs.com)](https://www.cnblogs.com/rainple/p/15914065.html#:~:text=2)

---



### [ ] 生产者发消息的流程

1. 生产者要往 Kafka 发送消息时，需要先创建 ProducerRecoder对象。ProducerRecoder 对象包含目标 topic，分区内容，以及指定的 key 和value,  在发送 ProducerRecoder 时，生产者会先把键和值对象序列化成字节数组，然后在网络上传输。
2. 接下来，数据被传给分区器。如果之前已经在 ProducerRecord 对象里指定了分区，那么分区器就不会再做任何事情。如果没有指定分区 ，那么分区器会根据 ProducerRecord 对象的key 来选择（murmur 的 Hash 算）一个分区，紧接着，这条记录被添加到一个记录批次里，这个批次里的所有消息会被发送到相同的主题和分区上。有一个独立的线程负责把这些记录批次发送到相应的 broker 上。若没有指定分区，且消息的 key 也是空，则用**轮询**的方式选择一个分区。
3. broker在收到Msg 时会返回一个响应。如果消息成功写入 Kafka，就返回一个 RecordMetaData 对象，它包含 Topic 和 Partition 信息，以及记录在分区里offset。如果写入失败，则会返回一个错误异常。生产者在收到错误之后会尝试重新发送消息，如果达到指定的重试次数后还没有成功，则直接抛出异常，不再重试。

---



###  3 Kafka分区策略


[(166条消息) Kafka 核心技术与实战学习笔记（九）生产者消息分区_kafka生产者分区策略_孔汤姆的博客-CSDN博客](https://blog.csdn.net/weixin_42369687/article/details/123881859)

**分区好处**

1. ==便于合理使用存储资源==，每个Partition在一个Broker上存储，可以把海量的数据按照分区切割成一块一块数据存储在多台Broker上。合理控制分区的任务，可以实现负载均衡的效果。
2. ==提高并行度==，生产者可以以分区为单位发送数据；消费者可以以分区为单位进行消费数据

 **1 生产者分区**

根据源码来说

通过 **消息键** 和 **分区器** 来实现，分区器为键生成一个 offset，然后使用 offset 对主题分区进行取模，为消息选取分区，这样就可以保证包含同一个键的消息会被写到同一个分区上。

1. **有 Partition**：，则消息投递到指定的partition。
2. **没有 Partition 有 Key**，则将key的hash值与topic的partition数取余得到partition值
3. **没有 Partition 没有 Key**，则用 **轮询** 的方式选择一个分区
   1. Sticky Partition（黏性分区器），会随机选择一个分区，并尽可能一直 使用该分区，待该分区的batch已满或者已完成，Kafka再随机一个分区进行使用（和上一次的分区不同）。


**2 消费者分区**

- Consumer 须自己从Topic 的 Partition 依次拉取消息。

- 同一个分区内的消息只能被一个 **group 里**的一个消费者消费。

Kafka有四种主流的分区分配策略： Range、RoundRobin、Sticky、CooperativeSticky。 可以通过配置参数partition.assignment.strategy，修改分区的分配策略。默认策略是Range + CooperativeSticky。Kafka可以同时使用 多个分区分配策略

1. **range分区策略**

   1. Range分配策略==面向每个主题（小排序）==，首先对同个 ==topic 的分区按照序号==排序，并对==消费者按照字母==顺序排序。
   2. 然后用 partitions数/consumer数 来判断每个消费者线程消费几个分区。如果除不尽，那么前面几个消费者线程将会多消费一个分区。
   3. 如果有N 多个 topic，那么针对每 个 topic，消费者C0都将多消费 1 个分区，容易产生数据倾斜！
   4. 45s内：整体被分配到C1或者 C2

2. **RoundRobin分配策略**

   1. ==把所有的 partition 和所有的 consumer 都列出来==，然后按照 hashcode 进行排序，最后 通过==轮询算法==来分配 partition 给到各个消费者。

3. **Sticky分配策略**

   1. 之前的分配原则，当前的分区分配算法都没有考虑上一次的分配结果。这种分配策略是在kafka的0.11.X版本才开始引入的，是目前最复杂也是最优秀的分配策略。

   2. Sticky是“粘性的”，可以理解为分配结果是带“粘性的”——每一次分配变更相对上一次分配做最少的变动（上一次的结果是有粘性的），其目标有两点：

   3. Sticky分配策略的原理比较复杂，它的设计主要实现了两个目的：

      1. 分区的分配要尽可能的均匀；
      2. 分区的分配尽可能的与上次分配的保持相同。
      3. 如果这两个目的发生了冲突，优先实现第一个目的。

      [StickyAssignor](https://blog.csdn.net/u4110122855/article/details/103616791)

4. **CooperativeSticky策略** 

   1. ==Kafka2.4.0==开始引入CooperativeStickyAssignor策略。

   2. StickyAssignor仍然是基于eager协议，分区重分配时候，都需要consumer==s先放弃当前持有的分区==，重新加入consumer group；

   3. 而CooperativeStickyAssignor基于cooperative协议，该协议将原来的一次全局分区重平衡，==改成多次小规模分区重平衡==。渐进式的重平衡。

---



### 3 数据可靠性

> 金山

数据完全可靠条件 = 分区副本大于等于2 + ISR里应答的最小副本数量大于等于2 +  ACK级别设置为-1 

**1 分区副本**
1. 一个topic会被分成多个partition，为每个Partition 生成多个副本（默认为3），并且把它们分散在不同的 Broker。
2. 分区副本里只有一个是 Leader，其余的副本是 follower，Kafka 生产者只会把数据发往 Leader，然后 Follower找 Leader进行同步数据。
3. Kafka分区中的所有副本统称为AR（Assigned Repllicas） AR = ISR + OSR（延迟过多的副本）
4. 当 Leader 挂了的时候，其中一个 follower 会重新成为新的 Leader。
5. Kafka 的分区多副本架构是 Kafka 可靠性保证的核心，把消息写入多个副本可以使Kafka 在发生崩溃时仍能保证消息的持久性

**2 ISR机制**
每个分区的Leader 维护了一个动态的 **ISR** 列表（in-sync replica，同步副本）, 是指==与 leader副本保持同步状态的Follower+Leader集合==（leader：0，isr:0,1,2）。 当 ISR 中的 全部follower 完成数据同步之后， leader 就会给 follower 发送 ack，如果其中一个 follower 长时间未向 leader 同步数据，该 follower 将会被踢出 ISR 集合（该时间阈值由 replica.log.time.max.ms 参数设定，默认30s）。当 leader 发生故障后，就会从ISR 集合中重新选举出新的 leader。

**3 ACK应答机制**
为保证producer发送的数据，能可靠的发送到指定的topic，topic的每个partition收到producer发送的数据后，都需要向producer发送ack（acknowledgement确认收到），如果producer收到ack，就会进行下一轮的发送，否则重新发送数据。

Kafka为用户提供了三种可靠性级别`request.required.acks`（acks参数）：

1. **0**：生产者发送过来的数据，==不需要等数据落盘应答==。这意味着producer无需等待来自broker的确认而继续发送下一批消息。数据传输效率最高，可靠性最低。
2. **1（默认**）：生产者发送过来的数据，==Leader 收到数据后应答==。这意味着producer在ISR中的leader已成功收到的数据并得到确认后发送下一条message。但如果leader接收完消息宕机了，则会丢失数据。
3. **-1**：生产者发送过来的数据，==Leader 和 ISR 队列 里面的所有节点收齐数据后应答==。producer需要等待ISR中的所有follower都确认接收到数据后才算一次发送完成，可靠性最高。
	1. 但是这样也不能保证数据不丢失，比如当ISR中只有leader时（前面ISR那一节讲到，ISR中的成员由于某些情况会增加也会减少，最少就只剩一个leader），这样就变成了acks=1的情况.
	2. 如果在follower同步完成后，broker发送ack之前leader发生故障，此时kafka从ISR中重新选举一个leader，生产者没有收到ack重新发送一份到新leader上，则造成数据重复。
	3. 如果ISR中只剩一个leader时，此时leader发生故障，可能会造成数据丢失。
      如果一个follower故障，该节点被踢出ISR，只要ISR中所有节点都同步即可返回ack，不影响。

---

### 3 数据一致性
这里介绍的数据一致性主要是说不论是老的Leader还是新选举的Leader，Consumer都能读到一样的数 据。通过LEO和HW保证各副本数据之间的一致性
1. ==LEO==（Log End Offset）：日志末端位移。每个副本的最后一个offset，LEO其实就是==最新的offset + 1==。（每个副本有一个自己的LEO，follwer的LEO不能大于leader）
2. ==HW==（High Watermark）：所有副本中==最小的LEO== （只有一个）
   1. 小于等于HW值的所有消息都被认为是“已备份”的

**HW 和 LEO 的更新机制**
1. **follower故障**
	1. follower发生故障后会被临时踢出ISR，待该follower恢复后，follower会读取本地磁盘记录的上次的HW， 并将log文件==高于HW的部分截取掉==，从HW开始向leader进行同步。等该follower的==LEO大于等于HW==，即follower追上leader之后，就可以重新加入ISR了。
2. **leader故障**
	1. leader发生故障之后，会从ISR中选出一个新的leader，之后，为保证多个副本之间的数据一致性，其余的follower会先将各自的log文件==高于HW的部分截掉==，然后从新的leader同步数据。
	2. 注意：这只能保证副本之间的数据一致性，并不能保证数据不丢失或者不重复。（是否丢数据是acks保证）
unclean.leader.election.enable 设为false(0.11版本之后已经默认为false)；表示非ISR中的副本不能够参与选举；因为非ISR列表中的follwer数据落后leader很多，如果将其选举为leader，会极大可能出现副本之间的数据不一致。

---

### [0] Kafka的offset管理

消费者在消费的过程中需要记录自己消费了多少数据，即消费 Offset。
2. HBASE、Redis 等外部 NOSQL 数据库：这一方式可以支持大吞吐量的 Offset 更新，但它最大的问题在于：用户需要自行编写 HBASE 或 Redis 的读写程序，并且需要维护一个额外的组件。
3. ZOOKEEPER：老版本的位移offset是提交到zookeeper中的，目录结构是：` /consumers/<group.id>/offsets/ <topic>/<partitionId> `，但是由于 ZOOKEEPER 的写入能力并不会随着 ZOOKEEPER 节点数量的增加而扩大，因而，当存在频繁的 Offset 更新时，ZOOKEEPER 集群本身可能成为瓶颈。因而，不推荐采用这种方式。
4. Kafka自身的一个特殊Topic（__consumer_offsets）中：这种方式支持大吞吐量的Offset更新，又不需要手动编写 Offset 管理程序或者维护一套额外的集群，因而是迄今为止最为理想的一种实现方式


---



###   offset更新/提交方式

1. 自动提交offset
	1. 设置enable.auto.commit=true，更新的频率根据参数【auto.commit.interval.ms】来定。
2. 手动提交offset
	1. commitSync（同步提交）：必须等待offset提交完毕（失败重试），再去消费下一批数据。
	2. commitAsync（异步提交） ：发送完提交offset请求后，就开始消费下一批数据了（不失败重试，有可能会提交失败）。

---

# zookeeper

### 3 介绍下Zookeeper

Zookeeper是一个为分布式应用提供协调服务，用于协调和管理分布式系统中各种任务的项目。
是一个由一个领导者（Leader），多个跟随者（Follower）组成的集群。
Zookeeper从设计模式角度来理解，是一个基于观察者模式设计的分布式服务管理框架，它负责存储和管理大家都关心的数据，然后接受观察者的注册，一旦这些数据的状态发生了变化，Zookeeper就负责通知已经在Zookeeper上注册的那些观察者做出相应的反应。

1. 作用
	1. 存储数据（文件系统）和监听（监听通知机制）

**应用场景**

Zookeeper提供的服务包括：分布式数据发布/订阅功能、统一命名服务、统一配置管理、统一集群管理、服务器节点动态上下线、软负载均衡等。它致力于为那些高吞吐的大型分布式系统提供一个高性能、高可用、且具有严格顺序访问控制能力的分布式协调服务。

1. **分布式数据发布/订阅功能**
	1. 一个典型的发布/订阅模型系统定义了一种一对多的订阅关系，能让多个订阅者同时监听某一个主题对象，当这个主题对象自身状态变化时，会通知所有订阅者，使他们能够做出相应的处理。
2. **命名服务**
	1. 在分布式系统中，通常需要一个全局唯一的名字，如生成全局唯一的网站名称等，Zookeeper可以通过顺序节点的特性来生成全局唯一ID，从而可以对分布式系统提供命名服务。
3. **Master选举**
   1. 分布式系统一个重要的模式就是主从模式(Master/Salves)，Zookeeper可以用于该模式下的Matser选举。 可以让所有服务节点去竞争性地创建同一个ZNode，由于Zookeeper不能有路径相同的ZNode，必然只有 一个服务节点能够创建成功，这样该服务节点就可以成为Master节点。
4. 分布式锁
   可以通过Zookeeper的临时节点和Watcher机制来实现分布式锁，这里以排它锁为例进行说明：分布式系 统的所有服务节点可以竞争性地去创建同一个临时ZNode，由于Zookeeper不能有路径相同的ZNode，必 然只有一个服务节点能够创建成功，此时可以认为该节点获得了锁。其他没有获得锁的服务节点通过在 该ZNode上注册监听，从而当锁释放时再去竞争获得锁。锁的释放情况有以下两种： 当正常执行完业务 逻辑后，客户端主动将临时ZNode删除，此时锁被释放； 当获得锁的客户端发生宕机时，临时ZNode会 被自动删除，此时认为锁已经释放。 当锁被释放后，其他服务节点则再次去竞争性地进行创建，但每次 都只有一个服务节点能够获取到锁，这就是排他锁。





1. **统一配置管理**

   1. 分布式环境下，配置文件同步非常常见。 一般要求一个集群中，所有节点的配置信息是一致的，比如 Kafka 集群。对配置文件修改后快速同步到各个节点上；

2. 配置管理可由zookeeper实现；可将配置信息写入zookeeper的一个znode  ，各个客户端服务器监听这个Znode。 一旦Znode中的数据被修改，ZooKeeper将通知各个客户端服务器。

3. **统一集群管理**

4. 分布式环境中，实时掌握每个节点的状态是必要的。 可根据节点实时状态做出一些调整。

5. ZooKeeper可以实现实时监控节点状态变化；可将节点信息写入ZooKeeper上的一个ZNode。 监听这个ZNode可获取它的实时状态变化

6. **服务器节点动态上下线**

7. 服务器启动时在zookeeper的节点注册信息；客户端监听这个节点就可以知道服务器的工作情况。

8. **软负载均衡**

9. 在Zookeeper中记录每台服务器的访问数，让访问数最少的服务器去处理最新的客户端请求。

10. **master选举**

11. **分布式锁**

 

 优点

- 集群中只要有**半数以上**节点存活，Zookeeper集群就能正常服务。所以Zookeeper适合安装奇数台服务器。

- 更新请求顺序执行，来自同一个Client的更新请求按其发送顺序依次执行。

- 数据更新原子性，一次数据更新要么成功，要么失败。

- 可扩展性：可以通过部署更多机器来加强zk的性能

  > 实时性，一旦一个事务被成功应用后，Zookeeper可以保证客户端立即可以读取到这个事务变更后的最新状态的数据。？？

 缺点

- zookeeper的选举过程缓慢，而zookeeper对网络隔离非常敏感。一旦出现网络隔离，zookeeper就要发起选举流程

  > 网络隔离：两个或两个以上的计算机或网络，不相连、不相通、相互断开

- zookeeper的性能是有限的

  > 本身不是为高可用性设计，master撑不住高流量容易导致系统宕机

- 不支持机架感知

 

  **Zookeeper的选举策略？ **★ ☆★☆★

> 半数机制：集群中半数以上机器存活，集群可用。所以Zookeeper适合安装奇数台服务器。
>
> Zookeeper虽然在配置文件中并没有指定Master和Slave。但是，Zookeeper工作时，是有一个节点为Leader，其他则为Follower，Leader是通过内部的选举机制临时产生的。

 **都是初次启动时的选举策略**

假设有五台服务器组成的Zookeeper集群，它们的**id从1-5**，**同时它们都是最新启动的**，也就是没有历史数据，假设这些服务器依序启动：

1）服务器1启动，发起一次选举。服务器1投自己一票。此时服务器1票数一票，不够半数以上（3票），选举无法完成，服务器1状态保持为LOOKING；

2）服务器2启动，再发起一次选举。服务器1和2分别投自己一票并交换选票信息：此时服务器1发现服务器2的ID比自己目前投票推举的（服务器1）大，更改选票为推举服务器2。此时服务器1票数0票，服务器2票数2票，没有半数以上结果，选举无法完成，服务器1，2状态保持LOOKING

3）服务器3启动，发起一次选举。此时服务器1和2都会更改选票为服务器3。此次投票结果：服务器1为0票，服务器2为0票，服务器3为3票。此时服务器3的票数已经超过半数，服务器3当选Leader。服务器1， 2更改状态为FOLLOWING，服务器3更改状态为LEADING；

4）服务器4启动，发起一次选举。此时服务器1，2，3已经不是LOOKING状态，不会更改选票信息。此时服务器3为3票，服务器4为1票。此时服务器4服从多数，更改选票信息为服务器3，并更改状态为FOLLOWING；

5）服务器5启动，同4一样为FOLLOWING状态。

 **leader故障下线时重新选举**

**SID**：服务器ID。用来唯一标识一台ZooKeeper集群中的机器，每台机器不能重复，和myid一致。

**ZXID**：事务ID。ZXID是一个事务ID，用来标识一次服务器状态的变更。在某一时刻，集群中的每台机器的ZXID值不一定完全一致，这和ZooKeeper服务器对于客户端“更新请求”的处理逻辑有关。

**Epoch**：每个Leader任期的代号。每完成一次选举这个数据就会增加

**选举Leader规则： ①EPOCH大的直接胜出 ②EPOCH相同，事务id大的胜出 ③事务id相同，服务器id大的胜出**

---

### leader和follower的区别

**领导者Leader**

Leader在集群中只有一个节点，可以说是老大，是zookeeper集群的中心，负责协调集群中的其他节点。从性能的角度考虑，leader可以选择不接受客户端的连接。

**主要作用**

1）发起与提交写请求。

所有的跟随者Follower与观察者Observer节点的写请求都会转交给领导者Leader执行（读不会，就是事务请求会）。Leader接受到一个写请求后，首先会发送给所有的Follower，统计Follower写入成功的数量。当有超过半数的Follower写入成功后，Leader就会认为这个写请求提交成功，通知所有的Follower commit这个写操作，保证事后哪怕是集群崩溃恢复或者重启，这个写操作也不会丢失。

2）与**Learner（Follower与Observer）**保持心跳

3）崩溃恢复时负责恢复数据以及同步数据到Learner

 

**跟随者Follower**

Follow在集群中有多个

**主要作用**

1）与老大Leader保持心跳连接

2）当Leader挂了的时候，经过投票后成为新的leader。leader的重新选举是由Follower们内部投票决定的。

3）向leader发送消息与请求

4）处理leader发来的消息与请求

 

### 3 Zookeeper的数据结构

**数据结构**

Zookeeper数据模型的结构与Unix文件系统很类似，整体上可以看作一棵树，每个节点称作一个ZNode。每一个ZNode默认能够存储1MB的数据，每个ZNode都可以通过其路径唯一标识。

1. 节点（Node）：
   1. 节点是 ZooKeeper 数据模型的基本单元。每个节点都有一个唯一的路径名，形式类似于文件系统中的路径。例如，`/myapp/node1` 是一个节点路径。
   2. 节点可以是持久的（persistent）或临时的（ephemeral）。持久节点在创建后会一直存在，直到被显式删除。临时节点在创建它们的客户端会话结束后自动删除。
   3. 节点可以有子节点，形成一个层次化的树状结构。每个节点路径都可以包含多个子节点，类似于文件系统中的目录结构。
2. 节点数据（Node Data）：
   1. 每个节点都可以关联一个数据值，称为节点数据。
   2. 节点数据是一个字节数组，可以存储任意类型的数据。
   3. 客户端可以读取和更新节点的数据。

![image-20220323101404892](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527327.png)



**Znode有四种形式的目录节点（默认是persistent ）**

1）持久化目录节点（PERSISTENT）

客户端与zookeeper断开连接后，该节点依旧存在

2）持久化顺序编号目录节点（PERSISTENT_SEQUENTIAL）

客户端与zookeeper断开连接后，该节点依旧存在，只是Zookeeper给该节点名称进行顺序编号

3）临时目录节点（EPHEMERAL）

客户端与zookeeper断开连接后，该节点被删除

4）临时顺序编号目录节点（EPHEMERAL_SEQUENTIAL）

客户端与zookeeper断开连接后，该节点被删除，只是Zookeeper给该节点名称进行顺序编号

**创建znode时设置顺序标识，znode名称后会附加一个值就是顺序号，顺序号是一个单调递增的计数器，由父节点维护**

**在分布式系统中，顺序号可以被用于为所有的事件进行全局排序，这样客户端可以通过顺序号推断事件的顺序**

 

**都有监听功能；持久化节点更多用于数据存储，持久化顺序节点可对多个事件进行排序；临时节点主要功能是分布式锁；**

 

### **Zookeeper架构**

**Zookeeper集群角色**

**Leader（领导者）**

负责处理事务请求，投票的发起和决议，即时更新状态和数据。

**Follower（跟随者）**

Follower角色接受客户端请求并返回结果，参与Leader发起的投票和选举，但不具有写操作的权限。

**Observer（观察者）**

Observer角色接受客户端连接，将写操作转给Leader，但Observer不参与投票（即不参加一致性协议的达成），只同步Leader节点的状态，Observer角色是为集群系统扩展而生的。

![image-20220322211315143](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527294.png)

**Clinet（客户端）**

连接Zookeeper集群的使用者，请求的发起者，独立于Zookeeper集群的角色。

 

### 既然有了Follower，为什么还要有Observer呢？

虽然通过Client直接连接到ZooKeeper集群的性能已经很好了，但该架构在面对超大规模的Client时，需添加ZooKeeper集群的Server数量。

随着Server的添加，ZooKeeper集群的写性能必定下降（ZooKeeper的ZNode变更是要过半数投票通过，随着机器的添加，因为网络消耗等原因必定导致投票成本添加，从而导致写性能的下降。）

Observer是一种新型的ZooKeeper节点，提供ZooKeeper的可扩展性，同时Observer不參与投票，仅仅是简单的接收投票结果，并向leader 同步消息。因此我们添加再多的Observer也不会影响集群的写性能；另一方面，Observer不參与投票，所以他们不属于ZooKeeper集群的关键部位，即使他们Failed，或者从集群中断开，也不会影响集群的可用性。

---

### -3- ZooKeeper来实现高可用
1. 多节点部署：
	1. 奇数节点，以确保在发生故障时能够维护多数投票
2. 选举机制：
	1. Zab协议来确保数据的一致性和可用性。
		1. 第一次启动选举规则： 投票过半数时，服务器 id 大的胜出
		2. 第二次启动选举规则： 
			1. EPOCH 大的直接胜出 
			2. EPOCH 相同，事务 id 大的胜出 
			3. 事务 id 相同，服务器 id 大的胜出
3. 数据复制：
	1. 数据首先被写入Leader节点，然后Leader节点将数据同步到Follower节点
4. 客户端负载均衡
	1. 在客户端使用ZooKeeper时，通常会使用负载均衡机制来分散请求到多个ZooKeeper节点，从而分散负载和提高可用性。
5. 快速故障检测和恢复
	1. ZooKeeper集群会定期进行心跳检测来检测节点的健康状态。
6. 数据持久性
	1. 数据持久化到磁盘
---


### 2 Zookeeper的zab协议
Zookeeper原子广播），来保证分布式事务的==最终一致性==。支持崩溃恢复的原子广播协议，基于该协议，Zookeeper 实现了一种主备模型（Leader 与 Follower）的系统架构保证集群中各个副本之间的数据一致性。
1. 消息广播
	1. 客户端发起一个写操作请求
	2. Leader 服务器处理客户端请求后将请求转换为 Proposal，同时为每个 Proposal 分配一个全局唯一 ID，即  ZXID
	3. Leader 服务器与每个 Follower 之间都有一个队列，Leader 将消息发送到该队列，并且根据FIFO策略发送消息
	4. Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。
	5. Leader 服务器收到半数以上的 Follower 的 ACK 后，即认为消息发送成功，可以发送commit消息。
	6. Leader向所有Follower广播commit消息，同时自身也会完成事务提交。Follower 接收到commit消息后，会将上一条事务提交。
2. 崩溃恢复模式
	1. 一旦 Leader 服务器出现崩溃或者由于网络原因导致 Leader 服务器失去了与过半 Follower 的联系，那么就会进入崩溃恢复模式。
	2. 崩溃恢复主要包括两部分：Leader选举 和 数据恢复

ZAB协议为了保证数据一致性，规定了 如果⼀个事务Proposal在⼀台机器上被提交处理成功，那么应该在所有的机器上都被提交处理成功

所以Zab 协议崩溃恢复需满足以下2个要求
1. 已经被处理的消息不能丢失
2. 被丢弃的消息不能再次出现

1）Zab 协议需要确保那些 已经在 Leader 服务器上提交（Commit）的事务最终被所有的服务器提交。
2）Zab 协议需要确保 丢弃那些只在 Leader 上被提出而没有被提交的事务。

**Leader选举**：

根据上述要求，Zab协议需要保证选举出来的Leader需要满足以下条件：

（1）**新选举出来的Leader不能包含未提交的Proposal**。**即新Leader必须都是已经提交了Proposal的Follower服务器节点**。

（2）**新选举的Leader节点中含有最大的zxid**。这样做的好处是可以避免Leader服务器检查Proposal的提交和丢弃工作。

**数据恢复：**

1）完成 Leader 选举后（新的 Leader 具有最高的zxid），在正式开始工作之前（接收事务请求，然后提出新的 Proposal），Leader 服务器会首先确认事务日志中的所有的 Proposal 是否已经被集群中过半的服务器 Commit，即 **是否完成数据同步**。

> 2）Leader 服务器需要确保所有的 Follower 服务器能够接收到每一条事务的 Proposal ，并且能将所有已经提交的事务 Proposal 应用到内存数据中。等到 Follower 将所有尚未同步的事务 Proposal 都从 Leader 服务器上同步并且应用到内存数据中以后，Leader 才会把该 Follower 加入到真正可用的 Follower 列表中。

 

### **ZAB是以什么算法为基础的？ZAB流程/原理？**★ ☆★☆★

ZAB是在Paxos算法基础上进行了扩展改造而来的。

zookeeper在实现ZAB流程的时候分为三个步骤：

1、选举阶段

选举阶段使用的是 Fast Leader Election（FLE）；在选举的过程中会对每个Follower节点的ZXID进行对比只有**highestZXID的Follower才可能当选Leader；**   **并且ledaer 没有未提交的Proposal**；

> **ZAB协议中使用ZXID作为事务编号，ZXID为64位数字**，低32位为一个递增的计数器，每一个客户端的一个事务请求使Leader产生新的事务后该计数器都会加1，高32位为Leader周期epoch编号，当新选举出一个Leader节点时Leader会取出本地日志中最大事务Proposal的ZXID解析出对应的epoch把该值加1作为新的epoch，将低32位从0开始生成新的ZXID；ZAB使用epoch来区分不同的Leader周期；

2、恢复阶段

在election阶段选举出来的Leader已经具有最新的ZXID，所有本阶段的主要工作是根据Leader的事务日志对Follower节点数据进行更新；这一阶段 Follower 发送他们的 lastZxid 给 Leader，Leader 根据 lastZxid 决定如何同步数据。Follower 收到 TRUNC 指令会终止 `Leader.lastCommitedZxid` 之后的 Proposal ，收到 DIFF 指令会从leader同步接收新的 Proposal，SNAP：Follower数据太老，Leader将发送快照SNAP指令给Follower同步数据。

半数以上的Follower完成数据同步之后，即进入广播阶段

3、广播阶段

- 客户端发起一个写操作请求
- Leader 服务器处理客户端请求后将请求转换为 Proposal，同时为每个 Proposal 分配一个全局唯一 ID，即  ZXID
- Leader 服务器与每个 Follower 之间都有一个队列，Leader 将消息发送到该队列，并且根据FIFO策略发送消息
- Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。
- Leader 服务器收到半数以上的 Follower 的 ACK 后，即认为消息发送成功，可以发送commit消息。
- Leader向所有Follower广播commit消息，同时自身也会完成事务提交。Follower 接收到commit消息后，会将上一条事务提交。

[Zookeeper一致性协议——ZAB - Jacian - 博客园 (cnblogs.com)](https://www.cnblogs.com/Jacian/p/14212401.html#选举阶段leader-election)

[zab协议流程图总结_luonanqin的博客-CSDN博客_zab协议流程](https://blog.csdn.net/luonanqin/article/details/78314096)

 

### zookeeper脑裂问题

脑裂就是一个集群中同时出现了两个master的场景；

1. **半数机制：**这样的方式可以确保Leader的唯一性,要么选出唯一的一个Leader，要么选举失败，**不会选出两个master**。

2. **假设某个Leader假死**，其余的followers选举出了一个新的Leader。这时，旧的Leader复活并且仍然认为自己是Leader，这个时候它向其他followers发出写请求也是会被拒绝的。

   因为每当新Leader产生时，会生成一个epoch标号(标识当前属于那个Leader的统治时期)，这个epoch是递增的，followers如果确认了新的Leader存在，知道其epoch，就会拒绝epoch小于现任Leader epoch的所有请求。

 

### **Zookeeper从三台扩容到七台怎么做？**

1）先检查三台设备的状态，两台为follower，一台为leader；

2）修改节点数量，由三台增加到七台，修改相应的zoo.cfg文件；

3）完成相关配置后，启动对应zk实例，确认启动ok，节点四到七依次验证实例状态；

4）在leader节点上查看目前状态同步的follower数，确认新增节点已经成功加入集群；

5）确认新增节点加入集群后，滚动更新原有集群的配置，并重启，这个时候会触发一次新的leader选举，epoch标号最大的默认优先当选新的leader，当epoch标号相同，zxid最新的默认优先当选新的leader，当zxid相同，myid最大的优先当选新的leader。

 

### 基于zookeeper的分布式锁？ ★ ☆★☆★

> 锁是多线程代码中的概念，只有当**多任务**访问同一个**互斥**的**共享资源**时才需要
>
> 在我们进行单机应用开发，涉及并发同步的时候，我们往往采用synchronized或者Lock的方式来解决多线程间的代码同步问题，这时多线程的运行都是在同一个JVM之下。但当我们的应用是分布式集群工作的情况下，属于**多JVM下的工作环境**，JVM之间已经无法通过多线程的锁解决同步问题。那么就需要一种更加高级的锁机制，**来处理种跨机器的进程之间的数据同步问题**——这就是分布式锁

**如何使用Zookeeper实现分布式锁**

大致思想为：每个客户端对某个方法加锁时，在 Zookeeper 上与该方法对应的**指定节点的目录下（如：/locks节点下）**，生成一个唯一的**临时有序节点**（就是以loks节点为父节点）。 判断是否 获取锁的方式很简单，只需要判断是否为有序节点中序号最小的一个，是，则获取到锁，不是则对前一个节点进行监听。 当释放锁的时候，只需将这个临时节点删除即可。同时，其可以避免服务宕机导致的锁无法释放，而产生的死锁问题（服务器宕机会将这个节点删除）。

基于zookeeper的分布式锁又分为**排他锁和共享锁**

**排他锁**，又称写锁或独占锁。如果事务T1对数据对象O1加上了排他锁，那么在整个加锁期间，只允许事务T1对O1进行读取或更新操作，其他任务事务都不能对这个数据对象进行任何操作，直到T1释放了排他锁。

定义锁：通过Zookeeper上的数据节点来表示一个锁

2）获取锁：客户端通过调用 create 方法创建表示锁的临时节点，可以认为创建成功的客户端获得了锁，同时可以让没有获得锁的节点在该节点上注册Watcher监听，以便实时监听到lock节点的变更情况

3）释放锁：以下两种情况都可以让锁释放

- 当前获得锁的客户端发生宕机或异常，那么Zookeeper上这个临时节点就会被删除
- 正常执行完业务逻辑，客户端主动删除自己创建的临时节点

![image-20220323143956152](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527312.png)

**共享锁**，又称读锁。如果事务T1对数据对象O1加上了共享锁，那么当前事务只能对O1进行读取操作，其他事务也只能对这个数据对象加共享锁，直到该数据对象上的所有共享锁都被释放。

共享锁与排他锁的区别在于，加了排他锁之后，数据对象只对当前事务可见，而加了共享锁之后，数据对象对所有事务都可见。

1）定义锁：通过Zookeeper上的数据节点来表示一个锁，是一个类似于/lockpath/[hostname]-请求类型-序号的**临时顺序节点**

2）获取锁：客户端通过调用 create 方法创建表示锁的临时顺序节点，如果是读请求，则创建/lockpath/[hostname]-R-序号节点，如果是写请求则创建 /lockpath/[hostname]-W-序号节点

3）判断读写顺序：大概分为4个步骤

① 创建完节点后，获取 /lockpath 节点下的所有子节点，并对该节点注册子节点变更的Watcher监听

② 确定自己的节点序号在所有子节点中的顺序

③

对于读请求：

- 如果没有比自己序号更小的子节点，或者比自己序号小的子节点都是读请求，那么表明自己已经成功获取到了共享锁，同时开始执行读取逻辑
- 如果有比自己序号小的子节点有写请求，那么等待

对于写请求，**如果自己不是序号最小的节点**，那么等待

④ 接收到Watcher通知后，重复步骤①

4）释放锁：与排他锁逻辑一致

 

**（羊群效应）改进**：[基于Zookeeper实现分布式锁 - kosamino - 博客园 (cnblogs.com)](https://www.cnblogs.com/jing99/p/11607094.html)

![image-20220726163514589](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527317.png)

### **master选举使用场景及结构**

选主原理介绍：Zookeeper的节点有两种类型，持久节点跟临时节点。临时节点有个特性，就是如果注册这个节点的机器失去连接（通常是宕机），那么这个节点会被zookeeper删除。选主过程就是利用这个特性，在服务器启动的时候，去zookeeper特定的一个目录下注册一个临时节点（这个节点作为master，谁注册了这个节点谁就是master），注册的时候，如果发现该节点已经存在，则说明已经有别的服务器注册了（也就是有别的服务器已经抢主成功），那么当前服务器只能放弃抢主，作为从机存在。同时，抢主失败的当前服务器需要订阅该临时节点的删除事件，以便该节点删除时（也就是注册该节点的服务器宕机了或者网络断了之类的）进行再次抢主操作。（从机具体需要去哪里注册服务器列表的临时节点，节点保存什么信息，根据具体的业务不同自行约定。）选主的过程，其实就是简单的争抢在zookeeper注册临时节点的操作，谁注册了约定的临时节点，谁就是master。

 

### zookeeper的watch机制？★ ☆★☆★

> 在 ZooKeeper 中，引入了 Watch 机制来实现了分布式的通知功能。ZooKeeper 允许客户端向服务端注册一个 Watch 监听，当服务端的一些事件触发了这个 Watch ，那么就会向指定客户端发送一个事件通知，来实现分布式的通知功能。

**ZooKeeper的Watch架构**

客户端先向ZooKeeper服务端成功注册想要监听的节点状态，就是注册一个watcher（其中客户端注册 watcher 有三种方式，调用客户端 API 可以分别通过 getData、exists、getChildren 实现），同时客户端本地会存储该监听器相关的信息（watcher对象）在WatchManager中，当ZooKeeper服务端监听的数据状态发生变化时，ZooKeeper就会主动通知发送相应事件信息给相关会话客户端，客户端线程从watchManager中回调watcher对象执行相应的功能。

![image-20220324092135223](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527281.png)

 

> ***ZooKeeper的Watch特性***
>
> 1. Watch是一次性的，每次都需要重新注册，并且客户端在会话异常结束时不会收到任何通知，而快速重连接时仍不影响接收通知。
>
> 2. Watch的回调执行都是顺序执行的，并且客户端在没有收到关注数据的变化事件通知之前是不会看到最新的数据，另外需要注意不要在Watch回调逻辑中阻塞整个客户端的Watch回调
>
> 3. Watch是轻量级的，**WatchEvent**是最小的通信单元，结构上只包含通知**状态、事件类型**和节点路径。ZooKeeper服务端只会通知客户端发生了什么，并不会告诉具体内容。

 

   下表列举了常见的连接状态和事件类型

![image-20220323153012451](https://hl-lei.oss-cn-hangzhou.aliyuncs.com/typoraimg/202308171527278.png)

 

### zookeeper的发布订阅功能

**发布订阅基本概念**

**发布订阅模式可以看成一对多的关系**：多个订阅者对象同时监听一个主题对象，这个主题对象在自身状态发生变化时，会通知所有的订阅者对象，使他们能够自动的更新自己的状态。

发布订阅模式在分布式系统的典型应用有：**配置管理和服务发现**。

**配置管理：**是指如果集群中机器拥有某些相同的配置，并且这些配置信息需要动态的改变，我们可以使用发布订阅模式，对配置文件做统一的管理，让这些机器各自订阅配置文件的改变，当配置文件发生改变的时候这些机器就会得到通知，把自己的配置文件更新为最新的配置

**服务发现：**是指对集群中的服务上下线做统一的管理，每个工作服务器都可以作为数据的发布方，向集群注册自己的基本信息，而让模型机器作为订阅方，订阅工 作服务器的基本信息，当工作服务器的基本信息发生改变时如上下线，服务器的角色和服务范围变更，监控服务器就会得到通知，并响应这些变化。

 

### Zookeeper 读写数据流程 ★ ☆★☆★

读流程

当Client向zookeeper发出读请求时，无论是Leader还是Follower，都直接返回查询结果。

**Zookeeper并不保证读取的是最新数据**

如果是对zk进行读取操作，在follower上读取到的数据可能是过期的旧数据，不是最新的数据。

想要数据强一致 客户端应该调用zk api的sync方法 强制从leader节点读取

 写流程

zookeeper写入操作分为两种情况，① 写入请求直接发送到leader节点，② 写入请求发送到Follower节点，这两种情况有略微的区别。

**写入请求直接发送到Leader节点时的操作步骤如下：**

- 1.Client向Leader发出写请求。
- 2.Leader将数据写入到本节点，并将数据发送到所有的Follower节点；
- 3.等待Follower节点返回ACK；
- 4.当Leader接收到一半以上节点(包含自己)返回写成功的信息之后，返回写入成功消息给client;

**写入请求发送到Follower节点的操作步骤如下：**

- 1.Client向Follower发出写请求
- 2.Follower节点将请求转发给Leader
- 3.Leader将数据写入到本节点，并将数据发送到所有的Follower节点
- 4.等待Follower节点返回ACK
- 5.当Leader接收到一半以上节点(包含自己)返回写成功的信息之后，返回写入成功消息给原来的Follower
- 6.原来的Follower返回写入成功消息给Client

 

### Paxos算法及其与ZAB的联系和区别？

Paxos算法是分布式技术大师Lamport提出的，主要目的是通过这个算法，让参与分布式处理的每个参与者逐步达成一致意见。用好理解的方式来说，就是在一个选举过程中，让不同的选民最终做出一致的决定。

在Paxos算法中，有三种角色：

Proposer
Acceptor
Learners
在具体的实现中，一个进程可能 同时充当多种角色 。比如一个进程可能 既是Proposer又是Acceptor又是Learner 。Proposer负责提出提案，Acceptor负责对提案作出裁决（accept与否），learner负责学习提案结果。

**为了避免单点故障，会有一个Acceptor集合，Proposer向Acceptor集合发送提案，Acceptor集合中的每个成员都有可能同意该提案且每个Acceptor只能批准一个提案，只有当一半以上的成员同意了一个提案，就认为该提案被选定了。**

Paxos的目标：保证最终有一个value会被选定，当value被选定后，进程最终也能获取到被选定的value。

 提议过程

**Prepare阶段：**

**Proposer**会选择一个提案，并且编号为**M0**,然后向**Acceptor**集合中发送**M0**编号的**Prepare**请求，如果这个时候**Acceptor**集合中的某个**Acceptor**收到了这个请求，并且编号**M0**比当前已经相应的所有的提案的最大编号还要大，那么**Acceptor**就需要反馈自己处理的最大编号，并且不会再去响应低于**M0**编号的任何请求。如果没有响应过请求，则会直接响应当前的**M0**编号的请求。

**Accept阶段:**

同样的，当**Proposer**发出的提案请求收到了来自整个**Acceptor**集合中的过半**Acceptor**的响应，那么就代表该提案可以生成，这个时候如果响应中过半是无任何提案信息的，则代表当前的提案的取值可以是任意值，如果响应中过半是其他的提案信息，那么则从中找到最大编号的提案的值，这里称为**V0**，组成**[M0,V0]**的**Acceptor**请求，再次发送给整个**Acceptor**集合。这个时候**Acceptor**如果没有通过大于**[M0,V0]**编号的提案，那么则会视为自动同意该提案，同样如果得到了过半数的同意，则当前提案视为通过。

当然在整个过程中，每个**Proposer**都有自己的周期定时生成不同的提案，并且严格按照上述过程运行，最终一定能保证算法的正确性，同样的，如果**Proposer**已经要生成更大编号的提案，**Accept**将收到的最大的编号信息通知给上一个同意的最大提案的**Proposer**，让其放弃自己的提案，选择最新的最大编号的提案即可。

  联系

1. **过半原则**

 区别

> 1. Paxos算法中，新选举产生的主进程会进行两个阶段的工作；第一阶段称为读阶段：新的主进程和其他进程通信来收集主进程提出的提议，并将它们提交。第二阶段称为写阶段：当前主进程开始提出自己的提议。
> 2. ZAB协议在Paxos基础上添加了同步阶段，此时，新的Leader会确保存在过半的Follower已经提交了之前Leader周期中的所有事物Proposal。这一同步阶段的引入，能够有效保证，Leader在新的周期中提出事务Proposal之前，所有的进程都已经完成了对之前所有事务Proposal的提交。

总的来说，ZAB协议和Paxos算法的本质区别在于两者的设计目的不一样：ZAB协议主要用于构建一个高可用的**分布式数据主备系统**，而Paxos算法则用于构建一个**分布式的一致性状态机系统**。

---


# Flink

### 3 Flink简介 

Flink是一个以==流==为核心的高可用、高性能的==分布式计算引擎==。具备 流批一体，高吞吐、低延迟，高容错，大规模复杂计算等特点，在数据流上提供 ==数据分发、通信==等功能。

1. 流批一体：

   1. Flink 的设计思想是以 **流** 为核心，批是流的特例， Flink 提供 精确的时间控制能力 和 有状态 计算机制，可以轻松应对无界数据流，同时 提供 **窗口** 处理有界数据流，处理无界的数据可以理解为流处理，处理有界的数据可以理解为批处理；所以被成为流批一体。
2. **集群级容错：** 
   1. Flink 与 集群管理器紧密连接，如 YARN、Kubernetes（集群管理工具），当进程挂掉后，自动重启新进程接管之前的工作。同时具备 **高可用性 ，**可消除所有单点故障
3. **应用级容错：**
   1. Flink 使用 轻量级分布式快照，设计检查点（**checkpoint**）实现可靠容错。Flink 利用检查点特性，在框架层面 提供 **Exactly-once** 语义，即端到端的一致性，确保数据仅处理一次，不会重复也不会丢失，即使出现故障，也能保证数据只写一次。

-----

### 流批一体
在大数据处理计算领域，有离线计算和实时计算两种模式。一般都是用mapreduce / hive / sparkSQL来处 理离线场景，用 sparkStreaming / flink处理实时场景，但是这种lambda架构会导致一个问题：进行更改 时要同时更改两套代码，进行同步
Flink 的开发者认为批处理是流处理的一种特殊情况。批处理是有限的流处理。Flink 使用一个引擎支持了 DataSet API 和DataStream API。
1. 流处理
	1. 检查点机制和状态机制：用于实现容错、有状态的处理； 
	2. 水印机制：用于实现事件时钟；
	3. 窗口和触发器：用于限制计算范围，并定义呈现结果的时间。
2. 批处理
	1. 用于调度和恢复的回溯法：由 MicrosoDryad 引入，现在几乎用于所有批处理器； 
	2. 用于散列和排序的特殊内存数据结构：可以在需要时，将一部分数据从内存溢出到硬盘上； 优化器：尽可能地缩短生成结果的时间。
3. 流计算：无限数据之上的计算
4. 批计算：有限数据之上的计算

5. 考虑到这些优点，社区已朝着流批统一的 DataStream API 迈出了第一步：支持高效的批处理（FLIP-134）。从长远来看，这意味着 DataSet API 将被弃用（FLIP-131），其功能将被包含在 DataStream API 和 Table API / SQL 中。
6. 数仓架构的流批一体 DWD的数据流失入仓




### 2 Flink 架构

**运行时架构**

Flink运行时架构主要包括四个不同的组件，它们会在运行流处理应用程序时协同工作
1. **分发器（Dispatcher）**
	1. 接收用户提交作业，为每个作业启动一个新的==JobMaster组件==，
	2. 以及维护==已完成作业==的归档信息。
2. **作业管理器（JobManager）**
	1. 根据并行度将 Flink 客户端提交的 Flink 应用的==作业图（JobGraph）生成 执行图（ExecutionGraph）==，分解为子任务，从资源管理器 ResourceManager ==申请资源==，
	2. 资源具备之后，开始分发任务到TaskManager 执行 Task，
	3. 并负责应用容错，跟踪作业的执行状态，发现异常则恢复作业等。
3. **资源管理器（ResourceManager）**
	1. 负责管理和分配TaskManager的插槽（slot），即Flink的处理资源单元。Flink为不同的环境和资源管理工具提供了不同的ResourceManager，比如YARN，Mesos，K8s等。
4. **任务管理器（TaskManager）**
	1. 是Flink的工作进程，通常多个，负责==执行具体的任务==（task），以及数据交换和缓存。
	2. 每一个TaskManager都包含了一定数量的 插槽（slots），并向ResourceManager汇报slot状态。

组成架构（任务调度原理）

1. **Client**：
	1. Flink 客户端是 Flink 提供的 CLI 命令行工具，用来提交 Flink 作业到 Flink 集群，在客户端中负责 StreamGraph (流图)和 JobGraph (作业图)的构建。
3. **JobManager**：
	1. JobManager 是一个 Flink 集群中任务管理和调度的核心，是控制应用执行的主进程。
	2. JobManager 根据并行度将 Flink 客户端提交的 Flink 应用生成“执行图” （ExecutionGraph），分解为子任务，从资源管理器 ResourceManager 申请所需的计算资源，资源具备之后，开始分发任务到TaskManager 执行 Task，并负责应用容错，跟踪作业的执行状态，发现异常则恢复作业等。
4. **TaskManager**：
	1. TaskManager 接收 JobManage 分发的子任务，根据自身的资源情况管理子任务的启动、 停止、销毁、异常恢复等生命周期阶段。Flink 程序中必须有一个TaskManager。在 TaskManager 中资源调度的最小单位是 task slot。TaskManager 中 task slot 的数量表示并发处理 task 的数量。一个 task slot 中可以执行多个算子。


-----



### 3 Flink 相比 Spark Streaming 有什么区别

==最重要的区别==：**Flink 是标准的==实时处理引擎==，基于事件驱动。而 Spark Streaming 是微批（Micro-Batch）的模型。**

1.  架构模型
	1. SparkStreaming 在运行时的主要角色包括：Master、Worker、Driver（调度器）、Executor（执行器），
	2. Flink 在运行时主要包含：Jobmanager、Taskmanager 、ResourceManager和Dispatcher。
2. 任务调度
	1. Spark 采用RDD 模型，Spark Streaming 的DStream 实际上也就是一组组小批数据 RDD 的集合。Spark 是批计算，将DAG 划分为不同的 stage，一个完成后才可以计算下一个
	2. Flink 基本数据模型是数据流，以及事件（Event）序列。Flink 是标准的流执行模式，一个事件在一个节点处理完后可以直接发往下一个节点进行处理
3. 时间机制
	1. Spark Streaming 支持的时间机制有限，只支持 处理时间。
	2. Flink 支持了流处理程序在时间上的三个定义：事件时间、注入时间、处理时间。同时也支持 watermark 机制来处理滞后数据。
4. 容错机制
	1. 对于 Spark Streaming 任务，我们可以设置 checkpoint，然后假如发生故障并重启，我们可以从上次 checkpoint 之处恢复，但是这个行为只能使得数据不丢失，可能会重复处理，不能做到恰一次处理语义。 
	2. Flink 则使用了两阶段提交协议来解决这个问题。

---

### -2- Flink State? 
什么是状态？一般来说，状态是由一个task维护，并用于计算某个结果的所有数据，都属于这个任务的状态。也可以理解为一个本地变量，可以被task的业务逻辑访问。task在处理数据时，会先访问state，并根据输入信息和state信息更新state。

1. 有状态计算是Flink非常重要的特性之一。==中间的计算结果==，并提供给后续的计算使用：
3. 由一个task维护，并用于计算某个结果的所有数据，都属于这个任务的状态。也可以理解为一个本地变量，可以被task的业务逻辑访问。下图展示了一个task与它的state的常规交互过程：task在处理数据时，会先访问state，并根据输入信息和state信息更新state。
4. 根据状态是否需要保存中间结果，分为 
	1. 无状态计算 map、filter、flatMap
	2. 有状态计算 sum
（需要保存之前所有数据的和，例如：计算过去一小时的平均水位/一分钟内收到两个相差 20cm 以上的水位差读数，则发出警告）

**状态的分类**

Flink有两种基本类型的状态

1. 托管状态（ManagedState）
	1. 由 Flink 自行进行管理的 State。
2. 原始状态（Raw State）
	1. 由用户自行进行管理，需要自己序列化

1. 从状态管理方式的方式来说
	1. Managed State 由 Flink Runtime 管理，自动存储，自动恢复，在==内存管理上有优化==
	2. Raw State 需要用户==自己管理==，需要==自己序列化==，Flink 不知道 State 中存入的数据是什么结构，只有用户自己知道，需要最终序列化为可存储的数据结构
2. 从状态数据结构来说
	1. Managed State ==支持已知的数据结构==，如Value、List、Map 等。
	2. Raw State ==只支持int数组==，所有状态都要转换为二进制字节数组才可以。
3. 从推荐使用场景来说
	1. Managed State 大多数情况下均可使用，实际生产推荐使用
	2. Raw State 是当 Managed State 不够用时，比如==需要自定义 Operator== 时，才会使用 Raw State

**托管状态分为两类**
1. 算子状态（Operator State）
	1. 状态是和算子进行绑定的，一个算子的状态不能被其他算子所访问到
	2. ListState：存储列表类型的状态。
	3. UnionListState：存储列表类型的状态，与 ListState 的区别在于：如果并行度发生变化，ListState 会将该算子的所有并发的状态实例进行汇总，然后均分给新的 Task；而 UnionListState 只是将所有并发的状态实例汇总起来，具体的划分行为则由用户进行定义。
	4. BroadcastState：用于广播的算子状态。
2. 键控状态（Keyed State）
	1. 状态是根据 key 值进行区分的，Flink 会为每类键值维护一个状态实例。
	2. ValueState：存储单值类型的状态。可以使用 `update(T)` 进行更新，并通过 `T value()` 进行检索。
	3. ListState：存储列表类型的状态。可以使用 `add(T)` 或 `addAll(List)` 添加元素；并通过 `get()` 获得整个列表。
	4. ReducingState：用于存储经过 ReduceFunction 计算后的结果，使用 `add(T)` 增加元素。
	5. AggregatingState：用于存储经过 AggregatingState 计算后的结果，使用 `add(IN)` 添加元素。
	6. FoldingState：已被标识为废弃，会在未来版本中移除，官方推荐使用 `AggregatingState` 代替。
	7. MapState：维护 Map 类型的状态。
---
 

### 3 Flink 广播状态？

**背景：**

1. 状态只限定在同一任务的算子中，**状态不能由相同或不同算子的另一个任务访问**。如何其它的任务数据流需要使用另一任务数据流中的状态，则需要将数据流中的状态广播出去，其它任务数据流才能访问

**定义：**

1. 所谓广播状态模式， 就是**来自一个流的数据需要被广播到下游算子的所有子任务**，在下游算子本地存储，在处理另一个流的时候依赖于广播的数据。**所以广播状态可以用于通过一个特定的方式来组合并共同处理两个事件流**

**应用**

1. **动态配置**：动态规则是一条事件流，要求吞吐量不能太高。
   **关键字、敏感信息过滤 /** 当一个报警规则时触发报警信息等。
2. **数据分流**：设置不同数据的分流条件和相应的配置信息，对主数据流进行自动分流存储。

 [(145条消息) 《Flink应用实战》(一)--广播状态-CSDN博客](https://blog.csdn.net/lwqhp/article/details/124804037)

-----

### 3 Flink 状态 如何存储 / 状态后端

**1 状态后端**
1.  ==本地的状态管理==，以及将checkpoint写入远程的==持久化==存储
Flip142
有种状态后端
1. MemoryStateBackend
	1. 内存存储。在java堆空间中存储
	2. HashMapStateBackend() + JobManagerCheckpointStorage()
2. FsStateBackend
	1. 文件存储。在本地文件系统，或HDFS
4. RocksDBStateBackend。
	1. 运行时状态（序列化后）存储在 TaskManager 的 RocksDB 数据库（key-value 型）中
	2. 进行快照时，RocksDB 中的所有数据会被传输到配置的文件目录，少量元数据信息保存在 Jobmanager 内存中
	3. 特点：大状态、长窗口，或大键值；唯一支持增量检查点的后端
	4. 缺点：访问成本高，可能导致数据流的吞吐量剧烈下降
更新后
1. HashMapStateBackend
2. EmbeddedRocksDBStateBackend

---

### 3 状态 如何持久化

1. 定义
	1. 状态后端是 Flink 用于管理和存储应用程序状态的组件。它负责将应用程序的键控状态（Keyed State）和操作符状态（Operator State）持久化到后端存储系统中，以便在故障恢复时恢复状态
2. RocksDBStateBackend 持久化策略
	1. ==全量持久化策略== RocksFullSnapshotStrategy（内存型，文件型）
		1. 每次将全量的 State 写入到状态存储中（如HDFS）
		2. 在执行持久化策略的时候，使用异步机制，每个算子启动 1 个独立的线程，将自身的状态写入分布式可靠存储中。在做持久化的过程中，状态可能会被持续修改，**基于内存的状态后端**使用 CopyOnWriteStateTable 来保证线程安全
	2. ==增量持久化策略== RocksIncementalSnapshotStrategy  （RocksDB）
		1. 增量持久化就是每次持久化增量的 State，只有RocksDBStateBackend支持增量持久化
3. Misc
	1. Flink使用检查点机制来实现状态持久化，即在输入的数据集上间隔性地生成Checkpoint Barrier，通过Barrier将间隔时间段内的数据划分到相应的Checkpoint中。Flink提供不同的状态后端来区分状态的存储方式和存储位置，例如Heap State Backends和RocksDB State Backends。Flink状态持久化可以保证应用的容错性和一致性。
	2. Flink 增量式的检查点以 RocksDB 为基础， RocksDB 是一个基于 LSM-Tree 的 KV 存储。新的数据保存在内存中， 称为 memtable。如果 Key 相同，后到的数据将覆盖之前的数据，一旦 memtable 写满了，RocksDB 就会将数据压缩并写入 磁盘。memtable 的数据持久化到磁盘后，就变成了不可变的 sstable。RocksDB 会将多个sstable 合并成新的sstable，然后删除旧的sstable；
	3. 在 Flink 执行检查点时，会将新的 sstable 持久化到HDFS 中，同时保留引用。
	4. 因为 sstable 是不可变的，Flink 对比前一个检查点创建和删除的 RocksDB sstable 文件就可以计算出状态有哪些发生改变。RocksDB 会在后台合并 sstable 并删除其中重复的数据。然后在 RocksDB 删除 原来的 sstable，替换成新合成的 sstable。新的 sstable 包含了被删除的 sstable 中的信息，这样可以减少检查点的历史文件，避免大量小文件的产生  

-----

### 大状态调优
**排查**
1. 算子收到第一个 checkpoint barrier 的时间。
2. Alignment Duration
	1. 为处理第一个和最后一个 checkpoint barrier 之间的时间。在 unaligned checkpoints 下，`exactly-once` 和 `at-least-once` checkpoints 的 subtasks 处理来自上游 subtasks 的所有数据，且没有任何中断。 然而，对于 aligned `exactly-once` checkpoints，已经收到 checkpoint barrier 的通道被阻止继续发送数据，直到所有剩余的通道都赶上并接收它们的 checkpoint barrier（对齐时间）。

1. RocksDB调优
	1. 增量Checkpoint
	2. RocksDB 内存调优
		1. block_cache_size 的配置
			1. 整个 RocksDB 共享一个 block cache，读数据时内存的 cache 大小，该参数越大读数据时缓存命中率越高，默认大小为 8 MB，建议设置到 64 ~ 256 MB。
		2. write_buffer_size 的配置
			1. 控制着 RocksDB 中 MemTable 的最大值。
		3. max_write_buffer_number 的配置
			1. 控制着内存中保留的 MemTables 的最大数量，即内存中“只读内存表“的最大数量。
2. 容量规划
3. 压缩状态数据
	1. Flink 为所有 checkpoints 和 savepoints 提供可选的压缩（默认：关闭）。 目前，压缩总是使用 snappy 压缩算法
4. 作业恢复状态
	1. Task 本地恢复


### 2 Savepoints 保存点

是基于 Flink 检查点机制的==应用完整快照备份机制==，原则上，算法与检查点完全相同，因此保存点可以认为就是具有一些==额外元数据==的检查点。

1. ==目的==
	1. checkpoint的是 恢复机制，以确保能从潜在的故障中恢复
	2. savepoint的是 手动备份之后重启、恢复暂停作业的方法。
2. ==实现==
	1. Checkpoint 的设计轻量并快速。
	2. Savepoints数据的可移植性
3. ==生命周期==
	1. Checkpoint 是自动和定期的。
	2. Savepoint 是由用户手动创建和管理的（即，调度、创建、删除）。


---


## ⭐Checkpiont 检查点算法/保存

**==1 Checkpiont 检查点==**
1. 为了使 Flink 的状态具有良好的容错性，Flink 提供了检查点机制 (CheckPoints) 。某一时刻，Flink中所有状态的全局快照，一般存在磁盘上。

**==2 算法流程==**
1. JobManager的 检查点协调器 发送指令，触发检查点的保存
2. Source 任务保存快照，并barrier插入到当前的数据流中，同时向所有下游并行算子广播该 barrier
3. 算子接受到上游所有分区barrier时，触发快照操作，报告自身快照情况，并向下游广播barrier
4. 最后 barrier 传递 到 Sink 算子， 当 Sink 算子已经收到了所有上游的barrier 时， Sink 算子进行快照，然后通知==检查点协调器==端到端精确一次。
5. 当所有算子都向检查点协调器汇报成功之后，检查点协调器向所有的算子确认本次Checkpoint完成

-----

## -2- Checkpoint AtleastOnce / EXACTLY-ONCE
1. flink是多并行度的，一个算子会受到不同source的barrier
2. barrier对齐
	1. 精准一次。先到的barrier，进入缓冲区阻塞，当都到齐时，才进行备份，所以数据不会重复。会造成数据积压，OOM。
	2. 至少一次。先到的barrier不会缓存，而会继续处理。重复计算
4. 非Barrier对齐
	1.   精准一次。先到的barrier不会等待对齐，将所有缓冲区的数据和状态进行备份，kafka提交。磁盘IO

---

##  -3-Checkpoint失败
1. 状态数据过大
	1. 作业存在反压或者数据倾斜
	2. [FLIP-158](https://cwiki.apache.org/confluence/display/FLINK/FLIP-158%3A+Generalized+incremental+checkpoints) (Flink Improvement Proposals)提出广义增量检查点（Generalized Incremental Checkpoints），其核心思想是基于 state changelog, changelog 能够细粒度地记录状态数据的变化 则只备份上一 次 Checkpoint 中 不 存 在 的 state，。具体描述如下
		1. 有状态算子除了将状态变化写入状态后端外，再写一份到预写日志中。
		2. 预写日志上传到持久化存储后，operator 确认 checkpoint 完成。
		3. 独立于 checkpoint 之外，state table 周期性上传，这些上传到持久存储中的数据被成为物化状态。
		4. state stable 上传后，之前部分预写日志就没用了，可以被裁剪。
2. 数据流动缓慢
	1. **动态调整buffer大小**
		1.  FLIP-183 Dynamic buffer size adjustment。只缓存配置时间内可以处理的数据量，这可以很好的控制 checkpoint。
	2. **取消barrier对齐**
		1. FLIP-76 Unaligned Checkpoint，对于实时性要求很好，但数据重复性要求低。 
---

## Flink 压测
## 2 Kafka压测
kafka压测
采用官方的脚本进行测试；
1. prducer端
	1. kafka-producer-perf-test.sh
	2. 创建一个test topic，设置为3个分区2个副本；我此时三台服务器的总带宽在30m/s左右，两个副本 ；所以Kafka的吞吐量预期为 15m/s；
	3. 如果压测结果显示没达到预期那么就要Kafka调整参数，Kafka默认异步批量发送，所以可调以下两个参数
		1. 调整batch.size
			1. batch.size默认值是16k。batch.size较小，会降低吞吐量，测试吞吐量如果小于期望吞吐量比较多，可以调大这个值；但也不能调太大。batch.size过大，会增加消息发送延迟；
		2. linger.ms
			1. linger.ms为消息发送的时间间隔，可设置为你能接受的延迟时间
			2. 同时设置batch.size和 linger.ms，就是哪个条件先满足就都会将消息发送出去
			3. Kafka需要考虑高吞吐量与延时的平衡
2. comsumer端
	1. kafka-consumer-perf-test.sh
	2. 测试的吞吐量小于预期：

1. 调整fetch-size
2. 增加fetch-size值，增大每次拉取的数据量
3. 如果这四个指标（IO，CPU，内存，网络）都不能改变，考虑增加分区数来提升性能

## -2- Flink的反压
1.  反压
	1. 流系统中数据的处理速度跟不上数据的发送速度，导致数据的堆积，这造成了反压。
	2. checkpoint超时。
		1. 因为barrier 是不会越过普通数据的，数据堆积导致 barrier 流经整个数据管道的时长变长，因而checkpoint 总体时间（End to End Duration）变长。
		2. checkpoint 超时失败
	3. state过大。
		1. 为保证Exactly-Once语义，对于有两个以上输入管道的 Operator，checkpoint barrier 需要对齐，接受到较快的输入管道的 barrier 后，它后面数据会被缓存起来但不处理，直到较慢的输入管道的 barrier 也到达，这些==被缓存的数据会被放到 state 里面==，反压的话缓存的数据变多，导致state 变大。
		3. OOM（使用 Heap-based StateBackend）或者物理内存使用超出容器资源（使用 RocksDBStateBackend）的稳定性问题
2. 排查
	1. 要解决反压首先要做的是定位到造成反压的节点
	2. 通过 Flink Web UI 发现反压问题。
	3. Task Metrics / 普罗米修斯监
		1. Flink 提供的 Task Metrics 是更好的反压监控手段
		2. output buffer usage 高，当前Subtask下游背压。
		3. input buffer usage 高，它有可能是背压的根源。
3. 解决
	1. 假设下游处理不过来，压力会一直传导到Source，Source就不会拉数据。这种固定大小缓冲池就像阻塞队列一样，保证了 Flink 有一套健壮的反压机制，使得 Task 生产数据的速度不会快于消费的速度。
	2. 数据倾斜：可以在 Flink 的后台管理页面看到每个 Task 处理数据的大小。当数据倾斜出现时，通常是简单地使用类似 KeyBy 等分组聚合函数导致的，需要 用户将热点 Key 进行预处理，降低或者消除热点 Key 的影响。
---

## 数据倾斜
1. 数据源 source 消费不均匀
	1. 通过调整并发度，解决数据源消费不均匀或者数据源反压的情况
2. key 分布不均匀的无统计场景
	1. 通过添加随机前缀，打散 key 的分布，使得数据不会集中在几个 Subtask
3. key 分布不均匀的统计场景
	1. 聚合统计前，先进行预聚合，例如两阶段聚合
		1. 预聚合：加盐局部聚合，在原来的 key 上加随机的前缀或者后缀
		2. 聚合：去盐全局聚合，删除预聚合添加的前缀或者后缀，然后进行聚合统计。


## ⭐ 端到端 状态一致性

**1 背景**
1. 状态一致性有三种级别
   1. 最多一次（AT-MOST-ONCE）
   2. 至少一次（AT-LEAST-ONCE）
   3. 精确一次（EXACTLY-ONCE）

**2 状态一致性**
最核心的是**两阶段提交协议（和状态保存）**，但流系统要实现 Exactly-Once，需要保证上游 Source 层、中间计算层和下游 Sink 层三部分同时满足Exactly-Once

1. Source端
	1. ==数据可重放==。Flink 将 Kafka Consumer 作为 Source，将偏移量保存下来，如可重置读取数据偏移量
2. Flink计算层
	1. ==Checkpoint 机制==。把状态数据定期持久化存储下来，Flink程序一旦发生故障的时候，可以选择检查点恢复，避免数据的丢失、重复。
3. Sink 端
	1. 幂等写入 
		1. 一个操作可以重复执行很多次，但只导致一次结果更改（Redis KV）
	2. 事务写入
		1. 预写日志
		2. ==两阶段提交2PC==

---

## -3- 两阶段提交
1. 当第一条数据来时，或者收到barrier时，开启一个 kafka 的事务
2. 接下来的所有数据，写入 kafka 分区日志但不可用，是==预提交==状态
3. 当Sink任务收到JobManager发来检查点完成的通知时
4. ==正式提交==事务，交的数据可以正常消费了

---



## Flink常用的算子有哪些

分两部分：

1. **数据读取的算子**，这是 Flink 流计算应用的起点，常用算子有：

- 从内存读：fromElements
- 从文件读：readTextFile
- Socket 接入 ：socketTextStream
- 自定义读取：createInput

2. **处理数据的算子**，常用的算子包括：Map（单输入单输出）、FlatMap（单 输入、多输出）、Filter（过滤）、KeyBy（分组）、Reduce（聚合）、 Window（窗口）、Connect（连接）、Split（分割）等。

 

## Flink中的数据传输形式（算子之间的数据传输形式）？

一个程序中，不同的算子可能具有不同的并行度

算子之间传输数据的形式可以是 one-to-one (forwarding) 的模式也可以是redistributing 的模式，具体是哪一种形式，取决于算子的种类

➢ One-to-one：stream维护着分区以及元素的顺序（比如source和map之间）。 这意味着map 算子的子任务看到的元素的个数以及顺序跟 source 算子的子任务生产的元素的个数、顺序相同。map、fliter、flatMap等算子都是one-to-one的对应关系。

➢ Redistributing：stream的分区会发生改变。每一个算子的子任务依据所选择的transformation发送数据到不同的目标任务。例如，keyBy 基于 hashCode 重分区、而 broadcast 和 rebalance 会随机重新分区，这些算子都会引起redistribute过程，而 redistribute 过程就类似于 Spark 中的 shuffle 过程。

 

## 2 Flink SQL

Flink SQL 是 Flink 实时计算为简化计算模型，降低用户使用实时计算门槛而设计的一套符合标准 SQL 语义的开发语言。

1. Catalog 提供了元数据信息，例如数据库、表、分区、视图以及数据库或其他外部系统中存储的函数和信息。
2. Catalog 允许用户引用其数据存储系统中现有的元数据，并自动将其映射到 Flink 的相应元数据

3. 提取事件时间
4. 自定义函数
5. 开窗

**创建表环境**

对于Flink这样的流处理框架来说，数据流和表在结构上还是有所区别的。所以使用Table API和SQL需要一个特别的运行时环境，这就是所谓的表环境(TableEnvironment)。主要负责：

1. 注册Catalog和表
2. 执行SQL查询
3. 注册用户自定义函数(UDF)
4. DataStream和表之间的转换

**创建连接器表(Connector Tables)**

- 通过连接器(connector)连接到一个外部系统（Kafka），然后定义表结构。例如我们可以连接到Kafka或者文件系统，将存储在这些外部系统的数据以表的形式定义出来，这样对表的读写就可以通过连接器转换成对外部系统的读写了。当我们在表环境中读取这张表，连接器就会从外部系统读取数据并进行转换。而当我们向这张表写入数据，连接器就会将数据输出(Sink)到外部系统中。

```java
  tableEnv.executeSql("" +
                "create table page_log( " +
                "    `page` map<string,string>, " +
                "    `ts` bigint, " +
                "    `rt` as TO_TIMESTAMP(FROM_UNIXTIME(ts/1000)), " +
                "    WATERMARK FOR rt AS rt - INTERVAL '2' SECOND " +
                " ) " + MyKafkaUtil.getKafkaDDL(topic, groupId));
```

**虚拟表(Virtual Tables)**

在环境中注册之后，我可以在SQL中直接使用这张表进行查询转换了。

- 调用表环境的sqlQuery()方法，直接传入一条SQL语句作为参数执行查询，得到的结果是一个Table对象。Table是Table API中提供的核心接口类，就代表了一个Java中定义的表实例。
- 得到的filterTable是一个中间转换结果，如果之后又希望直接使用这个表执行SQL，又该怎么做呢？由于newTable是一个Table对象，并没有在表环境中注册。所以我们还需要将这个中间结果表注册到环境中`createTemporaryView`，才能在SQL中使用：

```java
Table filterTable = tableEnv.sqlQuery("" +
                " select " +
                "    page['item'] item, " +
                "    rt " +
                " from page_log " +
                    " where page['last_page_id'] = 'search' " +
                    " and page['item_type'] = 'keyword' " +
                    " and page['item'] is not null");
tableEnv.createTemporaryView("filter_table", filterTable);
```



---



## 2 Flink的窗口？

窗口（window）就是将无限流切割为有限流的一种方式，flink的window可分为时间窗口和计数窗口。

1. ==时间窗口==（Time Window） ：根据时间对数据流进行分组的。
	1. 滚动时间窗口 Tumbling Time Window!
		  1. 将数据流切分成不重叠的窗口，每一个事件只能属于一个窗口。
		  2. 每一分钟中用户购买的商品的总数
	2. 滑动时间窗口 Sliding Time Window
		  1. 对于某些应用，它们需要的窗口是不间断的，需要平滑地进行窗口聚合
		1. 近一分钟用户购买的商品总数
	3. 会话窗口
2. ==计数窗口==（Count Window）： 是根据元素个数对数据流进行分组的。
   1. 滚动计数窗口 Tumbling Count Window
      1. 每100个用户购买行为事件统计购买总数
   2. 滑动计数窗口 Sliding Count Window
      1. 每10个元素计算一次最近100个元素的总和
3. ==会话窗口== （Session Window）： 通过 session 活动来对元素进行分组，
   1. 每个用户在活跃期间总共购买的商品数量
   2. session 窗口分配器通过 session 活动来对元素进行分组，一个 session 窗口通过一个 session 间隔来配置，这个 session 间隔定义了非活跃周期的长度，在这个间隔内没有数据到来，就会关闭这个窗口。后续数据进入新的窗口。session 窗口跟滚动窗口和滑动窗口相比，不会有重叠和固定的开始时间

## 3 Watermark

Watermark在Google的[The Dataflow Model](https://link.zhihu.com/?target=https%3A//research.google.com/pubs/archive/43864.pdf)论文中被首次提出。理想状态下数据一旦产生立即被处理, 即Event Time和Processing Time之间不存在偏差, 也就是图中斜率为1虚线展示的情况, 它表示Event Time总是等于Processing Time。真实状态下由于处理管道引入的随机延时, Processing Time总是滞后于Event Time, 也就是图中红色曲线展示的情况, 它表示Processing Time总是大于Event Time。[Flink最佳实践 - Watermark原理及实践问题解析 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/507776567)

Watermark是Flink中一种衡量Event Time进展的机制，应对乱序和延迟数据的机制。流处理从事件产生，到流经source，再到operator，中间是有一个过程和时间的，大部分情况下，流到operator的数据都是按照事件产生的时间顺序来的，但是也不排除由于网络、分布式等 原因，导致乱序的产生，Flink接收到的事件的先后顺序不是严格按照事件的Event Time顺序排列的。如果只根据eventTime决定window的运行，我们不能明确数据是否全部到位，但又不能无限期的等下去，需要Watermark来保证一个特定的时间后，必须触发window去进行计算了。

Watermark水印就是一个时间戳（timestamp），可以理解成一个延迟触发机制，假设允许的延迟时间为t； 那么表示Event Time小于或等于 t的事件都已经到达。



- **Watermark = 进入Flink的最大时间时间 - 指定的延迟时间**

- 水印并不会影响原有 Eventtime 事件时间
- 当数据流添加水印后，会按照水印时间来触发窗口计算,也就是说**watermark 水印是用来触发窗口计算的**

例如一个5秒时刻结束的时间窗口，可允许的延迟时间为2秒；那么此时以Watermark=5触发窗口计算（即Eventtime =7时）；也就是说等待了2秒让窗口内的数到齐。**综上Watermark用于处理乱序和延迟数据。**

  

Watermark的使用

- Flink 1.11中对Watermark相关的API进行了重构。DataStream API指定，常用的是调用assignTimestampsAndWatermarks方法（dataStram.assignTimestampsAndWatermarks）传入一个

BoundedOutOfOrdernessTimestampExtractor为乱序的数据设置时间戳和Watermark，传入一个AscendingTimestampExtractor为升序数据定义时间戳；

 项目中 flink 1.12 是  assignTimestampsAndWatermarks、watermakerstratergy() ...传入需要的watermaker

 **==1. Source Function==**

Source Function生成， 将Timestamp的分配(也就是上文提到的离散化)和watermark的生成放在上 游

通过collectwithTimestamp方法发送数据，和调用emitWatermark产生watermark,我们可以看到，调用 collectwithTimestamp需要传入两个参数，第一个参数就是数据，第二次参数就是数据对应的时间戳，这 样就完成了timestamp的分配，调用emitWatermark生成watermark。

```java
override def run(ctx: SourceContext[MyType]): Unit = { 
	while (/* condition */) { 
		val next: MyType = getNext() 
		ctx.collectWithTimestamp(next, next.eventTimestamp)
		if (next.hasWatermarkTime) { 
			ctx.emitWatermark(new Watermark(next.getWatermarkTime))
		} 
	} 
}
```

> 需要注意的是:如果一个timestamp分配器被使用的话，由源提供的任何Timestamp和Watermark都会被重写。



 **==2. DataStream API==**

==看源码==

在 Flink 1.11 版本之前，Flink 提供了两种生成 Watermark 的策略

1. **定期生成：AssignerWithPeriodicWatermarks**
   1. 周期性的生成 watermark：系统会周期性的将 watermark 插入到流中.默认周期是200毫秒
1. **标记生成：AssignerWithPunctuatedWatermarks**
   1. 对每一个事件都会尝试进行Watermark的生成，但是如果生成的Watermark是null或者Watermark小于之前的Watermark，则该Watermark不会发往下游，因为发往下游 也不会有任何效果，不会触发任何窗口的执行。

新API提供了WatermarkStrategy接口, 用于组装WaterMarkGenerator(用于实现Watermark生成算法)和TimestampAssigner(用于指示如何从事件中提取事件时间). 在DataStream API中有两种使WatermarkStrategy的方法: 1) 直接在Source中给出; 2) 调用DataStream的assignTimestampsAndWatermarks方法. 具体使用方式如下.



WatermarkStrategy中的TimestampAssigner一般根据数据格式传入相应的Lambda函数提取时间戳即可。WaterMarkGenerator, 它是Watermark生成算法的实现, 实现类都是BoundedOutOfOrdernessWatermarks，Flink内置了两种实现

1. **以当前最大时间戳**： WatermarkStrategy.forMonotonousTimestamps
2. **以当前最大时间戳减去固定值**：WatermarkStrategy.forBoundedOutOfOrderness
   1. `Duration.ofSeconds(2)`
---


## 3 迟到数据的处理

1. 推迟水印推进 
2. 在水印产生时，设置一个乱序容忍度，推迟系统时间的推进，保证窗口计算被延迟执行，
	1. 为乱序的数据争取更多的时间进入窗口
3. 设置窗口延迟关闭
	1. Flink的窗口，也允许迟到数据。当触发了窗口计算后，会先计算当前的结果，但是此时并不会关闭窗口。 以后每来一条迟到数据，就触发一次这条数据所在窗口计算(增量计算)。直到wartermark 超过了窗口结束时间+推迟时间，此时窗口会真正关闭。
4. 使用侧流接收迟到的数据使用侧流接收迟到的数据



在某些情况下，数据延迟会非常严重，即使通过 Watermark + EventTimeWindow 也无法等到数据全部进入窗口再进行处理，因为窗口触发计算后，**对于延迟到达的本属于该窗口的数据，Flink默认会将这些延迟严重的数据进行丢弃**

此时使用 **WaterMark + EventTimeWindow + AllowedLateness** **方案**（将严重迟到的数据通过侧输出流输出），可以做到数据不丢失。

 

**侧输出流这种方法只针对于基于 event-time 的窗口**

```java
allowedLateness(lateness:Time)---设置允许延迟的时间
 
sideOutputLateData(outputTag:OutputTag[T])--保存延迟数据
 
DataStream.getSideOutput(tag:OutputTag[X])--获取延迟数据
```


## Flink 相比 Spark Streaming 
==最重要的区别==：**Flink 是标准的==实时处理引擎==，基于事件驱动。而 Spark Streaming 是微批（Micro-Batch）的模型。**
1. ** 架构模型**
	1. SparkStreaming 在运行时的主要角色包括：Master、Worker、Driver（调度器）、Executor（执行器），
	2. Flink 在运行时主要包含：Jobmanager、Taskmanager 、ResourceManager和Dispatcher。
2. **任务调度**
	1. Spark 采用RDD 模型，Spark Streaming 的DStream 实际上也就是一组组小批数据 RDD 的集合。Spark 是批计算，将DAG 划分为不同的 stage，一个完成后才可以计算下一个
	2. Flink 基本数据模型是数据流，以及事件（Event）序列。Flink 是标准的流执行模式，一个事件在一个节点处理完后可以直接发往下一个节点进行处理
3. **时间机制**
	1. Spark Streaming 支持的时间机制有限，只支持 处理时间。
	2. Flink 支持了流处理程序在时间上的三个定义：事件时间、注入时间、处理时间。同时也支持 watermark 机制来处理滞后数据。
4. ** 容错机制**
	1. 对于 Spark Streaming 任务，我们可以设置 checkpoint，然后假如发生故障并重启，我们可以从上次 checkpoint 之处恢复，但是这个行为只能使得数据不丢失，可能会重复处理，不能做到恰一次处理语义。 
	2. Flink 则使用了两阶段提交协议来解决这个问题。
   
- Spark中分布式RDD缓存是一个非常强大的功能，在这一点上比Flink好用很多。比如在实时计算过程中需要一些离线大数据与之关联，Spark相比占有比较大的优势。
- Saprk比Flink还有占优的地方就是Spark的executor死了之后不会导致整个job挂掉，而是会创建新的executor再重新执行失败的任务。而Flink的某个task manager死了会导致整个job就失败了，必须设置checkpoint来进行容错。
- Spark 在进行图计算、机器学习等方面也会有优势；
- spark做 批处理 比 fink 强

---


# HBase / CK / ES

## 2 介绍下HBase 

1. HBase 是以 hdfs 为数据存储的，一种分布式、可扩展的支持海量数据存储的==非关系型数据库==
2. HBase的目标是存储和处理非常庞大的表，可以通过水平扩展的方式，利用廉价计算机集群处理极大的（超过10亿行数据和数百万列元素组成的）数据表。
3. 广泛应用于：交通、金融、电商、电信等场景；


1. 优点
	1. 海量存储 / 列式存储 / 极易扩展 / 稀疏 / 高并发
2. 缺点
	1. 原生不支持SQL
	2. 原生不支持二级索引
	3. 数据分析能力弱
		1. 比如聚合运算、多维度复杂查询、多表关联查询等。一般架设Phoenix或Spark等组件


---

##  2 Hbase架构

1. HMaster
	1. Master 是所有 ==RegionServer 的管理者==
	2. 为HRegionServer==分配HRegion==，监控状态，负载均衡和故障转移
2. HRegionServer
	1. ==维护HRegion==，处理对这些HRegion的==IO请求==，并负责切分与合并Region
3. Zookeeper
	1. ==Master 的高可用==、RegionServer 的监控、元数据的入口以及 集群配置的维护等工作。
4. HDFS
	1. 提供最终的底层==数据存储==服务，同时为 HBase 提供高可用的支持。

---

##  2 Hbase的数据模型

1. Name Space
	1. 命名空间，类似于关系型数据库的 DatabBase 概念，
2. Region
	1. 类似于关系型数据库的表概念。不同的是，HBase 定义表时==只需声明列族==即可，不需要声明具体的列
3. Row
	1. HBase 表中的每行数据都由一个 RowKey 和多个 Column（列）组成，数据是按照 RowKey的字典顺序存储的，并且查询数据时需要根据 RowKey 进行检索，所以 RowKey 的设计十分重要。
4. Column
	1. 每个列都由 Column Family(列族)和 Column Qualifier（列限定符）进行限定，例如 info:name，info:age
5. Time Stamp
	1. 用于标识数据的不同版本（version）
6. Cell
	1. 一个列中可以存储多个版本的数据。而每个版本就称为一个单元格（Cell）。cell 中的数据是没有类型的，全部是字节码形式存贮 由{rowkey, column Family：column Qualifier, time Stamp} 唯一确定的单元。
```sql
// 写入数据
put 'bigdata:student','1001','info:name','zhangsan'
// 读取数据
get 'bigdata:student','1001'
get 'bigdata:student','1001' , {COLUMN => 'info:name'}
// 删除数据
delete 'bigdata:student','1001','info:name'
```

---

##  3 Hbase的读写流程

1. 写流程(两段式写入)
	1. Client 先==访问 zookeeper==创建连接，获取 meta 表位于哪个 ==RegionServer==
	2. 访问对应的 RegionServer，==获取meta 表==，根据读请求的 namespace:table/rowkey，查询出目标数据位于哪个 RegionServer中的哪个==Region==中。并将该 table 的 region 信息以及 meta 表的位置信息缓存在客户端的 ==MetaCache==，方便下次访问。
	3. 将数据==顺序写入到 HLog==（预写日志，Write-Ahead Logging），直接落盘
		1. 为了数据的持久化和故障恢复
		2. Master首先处理遗留的HLog文件，将不同region的log数据拆分，分别放在相应region目录下，然后再将失效的region（带有刚刚拆分的log）重新分配，领取到这些region的HRegionServer在Load Region的过程中，会发现有历史HLog需要处理，因此会Replay HLog中的数据到Memstore中，然后flush到StoreFile，完成数据恢复。
	4. 根据写入命令的 RowKey 和ColumnFamily ==写入MemStore==，并且在MemStore中排序
		1. 为了维持数据按照RowKey的字典序排列（hdfs不支持数据修改）
	5. 向客户端发送写入成功 ACK
		1. 挂了就再读一遍region 
	6. 等达到 MemStore 的刷写时机后，将数据刷写到 HFile
		1. 默认128M
2. 读流程(读三次)
	1. Client 先==访问 zookeeper==创建连接，获取 meta 表位于哪个 ==Region Server==
	2. 访问对应的 RegionServer，==获取meta 表==，根据读请求的 namespace:table/rowkey，查询出目标数据位于哪个 RegionServer中的哪个Region中。并将该 table 的 region 信息以及 meta 表的位置信息缓存在客户端的 ==MetaCache==，方便下次访问
	3. 从==BlockCache（读缓存）==中读取到数据（原数据）
		1. 上次读过，有索引，数据变了也知道
	4. 从==MemStore（写缓存）==中读取数据（刚写进来）
	5. 从==StoreFile==（HFile 数据存储单元）中读取数据
		1. 慢，读磁盘
	6. 将从文件中查询到的数据块（BlockCache，StoreFile，默认大小为 64KB）缓存到Block Cache。
		1. 方便下次直接拿来用
	7. 合并所有读取数据返回
		1. 高版本覆盖低版本
---

## HBase的RowKey设计原则

HBase 表中的每行数据都由一个 RowKey 和多个 Column（列）组成，数据是按照 RowKey 的字典顺序存储的，并且查询数据时只能根据 RowKey 进行检索，所以 RowKey 的设计十分重 要。

1. 长度
	1. Rowkey是一个二进制码流，==不要超过16个字节==
	2. 数据的持久化文件HFile中是按照Key Value 存储的，Rowkey过长对于多列数据会消耗大量存储空间，极大影响 HFile的==存储效率==
	3. MemStore将缓存部分数据到内存，如果 Rowkey字段过长内存的有效利用率会降低，系统将无法缓存更多的数据，这会降低检索效率，增大==读取时间==
2. 散列
	1. 建议将Rowkey的==高位作为散列==字段，由程序循环生成，低位放时间字段，这样将提高数据均衡分布在每个Regionserver实现负载均衡的几率。
	2. 如果没有散列字段，首字段直接是时间信息将产生所有新数据都在一个 Region Server上==堆积==的热点现象，这样在做数据检索的时候负载将会集中在个别Region Server，降低查询效率。
		 1. 预分区，预先设计10个region;
		 2. Salt加盐，随机前缀，
		 3. Hash，hash前缀
		 4. Reverse反转，经常改变的部分放在最前面
3. 唯一
	1. 必须保证RowKey的唯一性，由于在HBase中数据存储是Key-Value形式，**若向HBase中同一张表插入相同RowKey的数据，则原先存在的数据==会被新的数据覆盖==**

---

## ⭐ 为什么用Clickhouse？

用于OLAP的列式存储数据库
1. 优点
	1. 速度快。一亿级数据，ClickHouse，比Hive快279倍，比MySQL快801倍。
	2. 列式存储与数据编码压缩
	3. 索引和分区
2. 缺点
	1. 不支持高并发，官方建议qps为100，可以通过修改配置文件增加连接数，但是在服务器足够好的情况下；

---
## Clickhouse为什么快
1. 
---


## Elasticsearch
Elasticsearch 让你可以快速、实时地存储、搜索和分析大量数据
使用IK分词器替换默认的分词插件
1. 基础
	1. ElasticsearchES中的index相当于mysql的db，一个mysql可以有多个db，类似的，
	2. 一个ES集群可以有多个index。
	3. ES中的type相当于mysql中的某个表，mysql中的某个db可以有多个表，在某个表中存储我们的某一类数据。
	4. ES中的type对应的mapping，相当于mysql中的表结构，定义了不同字段的数据类型。
2. 倒排索引
	1. 倒排索引是一种==数据结构==，用于优化文本搜索。传统的我们的检索是通过文章，逐个遍历找到对应关键词的位置。而倒排索引，是通过分词策略，形成了词和文章的映射关系表，这种词典+映射表即为倒排索引。有了倒排索引，就能实现O（1）时间复杂度的效率检索文章了，极大的提高了检索效率。

**Elasticsearch写入数据**
1. 索引准备：在将数据写入ES之前，首先需要确定要写入的索引（Index）、类型（Type）和文档ID（Document ID）。索引是具有相似特征的文档集合的逻辑容器，类型已在较新的版本中逐渐被弃用，而文档ID是每个文档在索引中的唯一标识符。
2. 创建文档：在确定了索引、类型和文档ID后，将要写入的数据组织成一个文档（Document）。文档是一条JSON格式的数据，它可以是结构化的数据或者半结构化的文本。文档中可以包含字段（Fields）和对应的值。
3. 发送写入请求：使用HTTP协议的PUT、POST或者DELETE请求，将准备好的文档发送到Elasticsearch的指定索引、类型和文档ID位置。通常，使用PUT请求来创建新文档或者更新已存在的文档，使用POST请求来创建新文档，而使用DELETE请求来删除文档。
4. 数据处理和写入：当Elasticsearch接收到写入请求时，它会对数据进行处理并将其写入合适的分片（Shard）。分片是索引在集群中的分布式存储单元，它允许数据在多个节点上进行水平分布，从而实现数据的高可用性和性能扩展。

**将DWD层的订单明细数据存入Elasticsearch**
1. 添加pom依赖，`flink-connector-elasticsearch`
2. 使用Flink的`ElasticsearchSink`类创建一个Elasticsearch Sink，用于将数据`json`写入Elasticsearch。
3. 数据以`Map<String, String>`的形式存储，将需要写入ES的字段依次添加到Map当中，key是mid，value是完整的json（途径，时间，设备名称）。这个方法返回一个`IndexRequest`对象，用于表示要写入Elasticsearch的文档。

---

#  计算机网络

### 3 TCP/IP 五层模型

ATNDP

1. **应⽤层**（应用层，表示层，会话层）
	1. 为操作系统或网络应用程序提供访问==网络服务接口==。
2. **传输层**
	1. 负责向两台主机进程之间的通信提供通⽤的==数据传输服务==。
3. **网络层** 
	1. 负责对子网间的==数据包==进行==路由选择==
4. **数据链路层**（网络结构层）
	1. 是各种控制协议，将有差错的物理信道==变为无差错的、能可靠传输数据帧的数据链路==
5. **物理层**（网络结构层）
	1. 利用传输介质为数据链路层提供物理连接，==实现比特流的透明传输==
---

### 3 TCP三次握手
三次握手保证双方具有接收和发送的能力

**三次握手**

1. 客户端和服务端都处于 `CLOSE` 状态。先是服务端主动监听某个端口，处于 `LISTEN` 状态
2. 客户端发送一个`SYN`报文段，首部标志位`SYN`置为1，另外还会指明自己的==初始化序号==`seq=x`，此时客户端处于`SYN_SENT`状态。
3. 服务器收到`SYN`的报文段后，会以自己的报文`SYN-ACK`进行应答。该应答报文的首部有三个重要信息：`SYN`被置为1；服务器选择自己的==初始序列号==`seq=y`；==确认号字段==`ack=x+1`。此时服务器处于`SYN_RCVD`状态。
4. 客户端收到`SYN-ACK`报文后，会发送一个`ACK`报文段，该报文段中==序列号==`seq=x+1`，==确认号==`ack=y+1`。此时客户端处于`ESTABLISHED`状态。
5. 服务端收到客户端的`ACK`报文后，也进入 `ESTABLISHED` 状态。 



- 第一次握手和第二次握手都只是消耗掉一个序号，但不能携带数据；第三次握手可以携带数据。
- SYN：同步SYN(SYNchronization),在连接建⽴时⽤来同步序号。SYN置1表示这是⼀个连接请求或连接接受请求。
- ACK：确认ACK(ACKnowledgment),仅当ACK=1时确认号字段才有效。TCP规定，在连接建⽴后所有的报⽂段都必须把 ACK置1。

1. 第一次握手
	1. 客户端发送报文，“客户端想和服务器建立连接”。
	2. 服务器收到报文后得出结论：客户端==发送==正常，服务器==接收==正常。
	3. 当客户端超时重传 3 次 FIN 报文后，由于 tcp_orphan_retries 为 3，已达到最大重传次数，于是再等待一段时间（时间为上一次超时时间的 2 倍），如果还是没能收到服务端的第二次挥手（ACK报文），那么客户端就会断开连接。
2. 第二次握手
	1. 服务器收到后回复，“服务器收到了你的请求，同意和客户端建立连接”。
	2. 客户端收到报文得出结论：客户端==发送接收==都正常，服务器的==发送接收==正常。
	3. 服务器收到报文得出结论：客户端==发送==正常，服务器==接收==正常。
3. 第三次握手
	1. 客户端收到回复，“客户端收到回复，知道服务器同意连接，开始连接吧”
	2. 客户端收到报文得出结论：客户端==发送接收==都正常，服务器的==发送接收==正常。
	3. 服务器收到报文得出结论：客户端==发送接收==都正常，服务器的==发送接收==正常。

### **为什么要三次握⼿**
确认双方的接受能力、发送能力是否正常。指定自己的初始化序列号，为后面的可靠传送做准备。

1. **「两次握手」：无法防止历史连接的建立，会造成双方资源的浪费，也无法可靠的同步双方序列号；**
	1. 一个「旧 SYN 报文」比「最新的 SYN 」 报文早到达了服务端；
	2. 那么此时服务端就会回一个 `SYN + ACK` 报文给客户端；
	3. ==客户端==收到后可以根据自身的上下文，判断这是一个历史连接（序列号过期或超时），那么客户端就会发送 `RST` 报文给服务端，表示中止这一次连接
	4. 两次握手的情况下，服务器在收到 SYN 报文后，就进入 ESTABLISHED 状态，意味着这时可以给对方发送数据；服务端 在向客户端 发送数据前，并没有阻止掉历史连接，导致 服务端 建立了一个历史连接，又白白发送了数据， 浪费了服务端 的资源
3. **「四次握手」：三次握手就已经理论上最少可靠连接建立，所以不需要使用更多的通信次数。**

---


### 四次挥手

1. 客户端 发送⼀个 FIN，并初始序号seq=u，⽤来关闭客户端到服务器的数据传送，客户端进入FIN_WAIT1 状态；
2. 服务器 收到这个 FIN，返回⼀ 个 ACK，==确认号== ack = u+1，返回 ⼀个==初始序列号== seq=v 。此时服务器进入CLOSE_WAIT 状态，客户端收到ACK消息，进入FIN_WAIT2状态；
3. 服务器 发送⼀个FIN，==确认号==ack = u+1,，重新选择 ⼀个初始的序号 seq=w，此时服务器进入LAST_WAIT 状态
4. 客户端 发送 ACK ，并将确认序号设置为收到序号w加1，序列号为u+1，进入TIME_WAIT状态；服务端收到ACK后连接正式关闭。

---

### HTTP / HTTPS的区别

1. 端⼝
	1. HTTP的默认使⽤==端⼝80==，HTTPS默认使⽤==端⼝443==
2. 安全性
	1. HTTP 是明文传输协议
	2. HTTPS 协议是由 SSL+HTTP 协议构建的可进行加密传输，身份认证的网络协议
		1. 所有传输的内容都经过对称加密。

---
### Https的连接过程


2.  客户端向服务器发送请求，并传送客户端 SSL 协议的版本号，加密算法的种类，产生的随机数以及其他相关信息
3.  服务器向客户端传送 SSL 协议的版本号，加密算法的种类，随机数以及其他相关信息，同时服务器还将向客户端传送自己的证书（地址信息，加密公钥，证书颁发机构信息）    
3. 客户端利用服务器传过来的信息验证服务器的合法性 ，无误后会生成一个对称加密钥匙，然后用服务器的公钥加密后发送给服务端
4. 服务端收到后用自己的私钥去解密并验证；然后同样计算握手信息的摘要，使用对称加密来加密一段握手信息，发送给客户端，客户端检查无误后建立连接，后续都使用对称加密来进行通信。

---

### 输入url到页面显示
1. 域名解析（通过DNS映射, 将域名变为 ip 地址）。
2. 发起网络请求
	1. tcp 的三次握手，建立 tcp 连接。浏览器会以一个随机端口（1024-65535）向服务端的 web 程序 80 端口发起 tcp 的连接。
	2. 建立 tcp 连接后发起 http 请求。
3. 接收HTML文件
	1. 服务器接收到浏览器的请求后，将网页的HTML文件作为响应发送给浏览器。
4. 构建DOM树
	1. 它从HTML的根元素开始，逐步解析和构建所有HTML元素及其嵌套关系。
5. 构建CSSOM树
	1. CSSOM树表示CSS样式规则的层次结构，包括选择器、样式属性等。
6. 构建渲染树
7. 浏览器对页面进行渲染，并呈现给用户。

---

### 网页加载缓慢
1. 网络连接问题
2. 服务器响应时间慢
	1. 服务器负载过重、服务器配置不佳等
	2. 联系网站管理员或服务提供商，了解服务器状态，升级服务器配置，或者考虑使用内容分发网络（CDN）来提高网页加载速度。
3. 大量的HTTP请求
	1. 网页中包含大量的图片、脚本和其他外部资源，每个资源都需要单独的HTTP请求。
	2. 解决方法：优化网页，减少资源的数量和大小，合并文件、压缩文件，使用CSS精灵图或图标字体等技术来减少HTTP请求次数
4. 图片过大或未经优化
5. 脚本加载和执行时间过长
	1. 网页中的JavaScript代码过多或复杂，导致脚本加载和执行时间过长
	2. 解决方法：优化和压缩JavaScript代码，将脚本放置在页面底部，使用异步加载脚本的方式，以便在页面加载完成后再加载脚本。
6. 缓存设置不当
	1. 在服务器端设置适当的缓存策略，利用浏览器缓存来存储静态资源，减少重复的网络请求。
---

### 网络排查
[排错五大步骤](https://zhuanlan.zhihu.com/p/607083215?utm_id=0)
1. 检查物理链路是否有问题；
2. 查看本机IP地址、路由、DNS的设置是否有问题；
3. 测试网关或路由器的通畅情况。先测网关然后再测路由器，一级一级地测试；
4. 测试ping公网ip的通畅情况（平时要记几个外部IP）；
5. 测试DNS的通畅情况，可以直接ping网站地址；

---

# Java

## List, Set, Queue, Map

1. List(对付顺序的好帮手): 
	1. 存储的元素是==有序==的、可==重复==的。
2. Set(注重独一无二的性质): 
	1. 存储的元素是==无序==的、==不可重复==的。
3. Queue(实现排队功能的叫号机): 
	1. 按特定的排队规则来确定先后顺序，存储的元素是==有序==的、可==重复==的。
4. Map(用 key 来搜索的专家): 使
	1. 用键值对（key-value）存储，Map 中的每一个元素包含一个键和一个值，成对出现，==键不可重复，值可重复==；

 但Tree Set 类，可以默认顺序，也可以通过实现 Java.util.Comparator< Type >接口来自定义排序方式。
---
## ArrayList / LinkedList

1. ArrayList
	1. 数据结构实现：数组队列，相当于==动态数组==
	2. ==查改== 性能好
		1. 通过索引直接访问元素
	3. 内存空间占⽤：
		1. 需要连续的内存空间存储元素，因此在存储大量元素时可能会浪费一部分内存。
	5. 非线程安全
	6. 应用场景：
		1. 数据库查询结果的存储
		2. 缓存数据的存储
		3. 处理大量数据的存储，数据量大时可能复制比遍历快
		4. 实现动态数组
2. LinkedList
	1. 数据结构实现：==双向链表==
	2. 增删 性能好（实际情况想反）
		1. 任意位置都高效，因为只需要调整节点的引用
		2. 头插 链表＞数组
		4. 尾插 链表＜数组
	3. 内存空间占⽤：
		1. 需要额外的空间来存储节点之间的引用，因此在存储大量元素时可能会占用更多的内存。
	4. 非线程安全
	5. 应用场景：
		1. 大数据集合操作（频繁读写）
		2. 队列和栈，循环列表，模拟链表结构
		3. 双向迭代器：文本编辑器中的撤销/重做操作


**Vector**

- 数据结构实现：矢量队列，相当于动态数组
- 随机访问效率：
- 增加和删除效率：
- 内存空间占⽤：
- 线程安全：

**Stack**

- 栈，继承于Vector。特性是后进先出。

[(2条消息) 数组和链表的区别_博可睿的博客-CSDN博客_数组和链表的区别](https://blog.csdn.net/weixin_42438797/article/details/115339605)

---

## ⭐HashMap

**底层实现**

JDK1.8 之前 `HashMap` 底层是 ==数组和链表== 结合在一起使用也就是 ==链表散列==。HashMap 通过 key 的 hash值 经过扰动函数处理过后得到 位值，然后判断当前元素存放的位置，如果当前位置存在元素的话，就判断该元素与要存入的元素的 hash 值以及 key 是否相同，如果相同的话，直接覆盖，不相同就通过拉链法解决冲突。

JDK1.8 之后在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）时，将链表转化为红黑树，以减少搜索时间。

[hashmap中为何链表长度大于8才转换成红黑树 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/348756860)  

**put原理**

1. HashMap map = new HashMap():
	1. 在实例化以后，底层创建了长度是16的一维数组Entry  table
2. map.put(key,value1):
	1. 调用hashCode()得到hash码计算key1哈希值，此哈希值经过扰动函数计算以后，得到在数组中的存放位置。
	2. 如果此位置上的数据为空，则添加
	3. 否则迭代该处元素链表并依次比较其 key 的 hash 值
		1.  hash 值相等但 key 值不等 ,那么这个新节点将会被添加到链表的尾部。
		2.  如果两个 hash 值相等且 key 值相等，那么这个节点上的value将会被新节点的value覆盖。

**底层实现**

1. JDK1.8 之前 
	1.  ==Entry数组 + 链表== 结合在一起使用（ ==链表散列==）。
	2. 解决Hash冲突：将冲突的值加到链表中即可。
	3. HashMap 通过 key 的`hashcode`经过扰动函数处理过后得到hash值，然后数组的长度取模运算 `(n - 1) & hash`得到存放的位置，如果当前位置存在元素的话，就判断该元素与要存入的元素的 hash 值以及 key 是否相同，如果相同的话，直接覆盖，不相同就通过拉链法解决冲突。
	4. ==扰动函数==指（`hash`方法） 。防止一些实现比较差的 `hashCode()` 方法 换句话说使用扰动函数之后可以减少碰撞。h右移16位，将hashcode和右移16位的hashcode做异或运算，来加大低位的随机性。
	5. 右移16位正好为32bit的一半，自己的高半区和低半区做异或，是为了混合原始哈希吗的高位和低位，来加大低位的随机性。而且混合后的低位掺杂了高位的部分特征，使高位的信息也被保留下来
		```java
		static final int hash(Object key) {  
		    int h;  
		    return (key == null) ? 0 : (h = key.hashCode()) ^ (h %3E>> 16);  
		}
		```
1. JDK1.8 之后
	1. ==Node 数组 + 链表/红黑树==
	2.  解决Hash冲突：当链表长度大于阈值（默认为 8）
		1. 如果当前数组的长度小于 64，那么会选择先进行数组扩容
		2. else将链表转化为红黑树，以减少搜索时间 O(logN)）

**put原理**
1. HashMap map = new HashMap():
	1. 在实例化以后，底层创建了长度是16的一维数组`Entry[] table`
2. map.put(key,value1):
	1. 调用`hashCode()`得到hash码，再经过扰动函数，得到在数组中的存放位置。
   1. 如果此位置上的数据为空，则添加
   2. 否则迭代该处元素链表并依次比较其 key 的 hash 值
      1.  hash 值相等但 key 值不等 ，那么这个新节点将会被添加到链表的尾部（尾插法）
      2.  如果两个 hash 值相等且 key 值相等，那么这个节点上的value将会被新节点的value覆盖。
---

## hash冲突
1. 开放定址法。从冲突位置，就往后找没有元素的位置
2. 拉链法。Hash冲突的key，以单向链表来进行存储
3. 再哈希。两次哈希
4. 建立公共溢出区。存在冲突的元素，一律放到溢出表中
5. 扰动函数
6. 负载因子0.75 就是说当阀值容量占了 3/4s 时赶紧扩容，减少 Hash 碰撞。
---

## 红黑树
红黑树是一种自平衡的二叉搜索树
1. 3. 二叉搜索树性质
	1. 右节点＞父点＞左节点
2. 节点颜色
	1. 任何一个节点都有颜色，黑色或者红色。
	2. 根节点是黑色的。
	3. 空节点被认为是黑色的。
	4. 如果一个节点是红色的，则它的子节点必须是黑色的
	5. 任何一个节点向下遍历到其子孙节点的所有路径，所经过的黑节点个数必须相等
3. 自平衡性
	1. 红黑树通过在插入和删除操作时进行必要的旋转和颜色调整，

---

## -1- HashMap / HashTable

底层数据结构两者基本相似。JDK1.8 以后的 HashMap 在解决哈希冲突时有了较⼤的变化，当链表⻓度⼤于阈值（默认为8）并且数组长度大于64时，将链表转化为红⿊树，以减少搜索时间。Hashtable 没有这样的机制。

1. ==线程安全==
	1. HashMap 是⾮线程安全的
	2. HashTable 是线程安全的
		1. HashTable 内部的⽅法基本都经过 synchronized 修饰
2. ==效率==
	1. HashMap 要⽐ HashTable 效率⾼⼀点
3. ==Null key==
	1. HashMap 中，一个键可以为null
	2.  HashTable 的键值不能是 null
4. ==容量==
	  1. Hashtable 默认的初始⼤⼩为11（n），每次扩充为2n+1
	  2. HashMap 默认的初始化⼤⼩为16（$2^n$）。之后每次扩充为2n。
---


## -1- HashMap /  HashSet
HashSet 底层就是基于 HashMap 实现的。
1. ==实现==
	1. HashMap实现Map接口。HashSet实现实现 Set 接口
2. ==存储==
	1. HashMap存储键值对。HashSet仅存储对象
3. ==添加==
	1. HashMap调用 put()。HashSet调用 add()
4. ==hashcode==
	1. HashMap 使用Key计算 hashcode。HashSet 使用成员对象来计算 hashcode值。

---

## -1- HashMap /  TreeMap
1. TreeMap 和 HashMap 都继承自 `AbstractMap` ，但是需要注意的是 TreeMap还实现了`NavigableMap`接口和`SortedMap` 接口。
2. 实现 `NavigableMap` 接口，有了对集合内元素的搜索的能力。
3. 实现`SortedMap`接口，有了对集合中的元素根据键排序的能力（默认按 key 的升序排序，或者重写`compare`方法）
---

##  -1- HashSet 如何检查重复
1. 计算`hashcode`来判断加入位置
2. 与其他加入的对象的 `hashcode` 值作比较。有相同 `hashcode` 值的对象，会调用`equals()`方法
	1. 如果相同，`HashSet` 就不会让加入操作成功。

---

##  ConcurrentHashMap

1. 数据结构：
	1. ConcurrentHashMap  JDK1.7   ==Segment数组 + Entry 数组 + 链表== 。JDK1.8 ，==Node数组+链表/红黑二叉树==。
	2. Hashtable   ==数组+链表==  的形式
2. 线程安全
	1. JDK1.7 ，segment分段锁 + 读不加锁
	2. JDK1.8 ，Node数组 + CAS + synchronized
3. Hashtable(同一把锁) 
	1. 使用 `synchronized` 来保证线程安全，效率非常低下。当一个线程访问同步方法时，其他线程也访问同步方法，可能会进入阻塞或轮询状态，如使用 put 添加元素，另一个线程不能使用 put 添加元素，也不能使用 get，竞争会越来越激烈效率越低。
4. SynchronizedMap 
	1. 一次锁住整张表来保证线程安全，所以每次只能有一个线程来访问Map（效率极低）

---

##   == 和 equals() 的区别(1)

  1. \==：如果比较的对象是基本数据类型，则比较的是数值是否相等；如果比较的是引用数据类型，则比较的是对象的地址值是否相等。
  2. equals 方法：用来比较两个对象的内容是否相等。注意：equals 方法不能用于比较基本数据类型的变量。如果没有对 equals 方法进行重写，则比较的是引用类型的变量所指向的对象的地址（此时等价于用== )


## ⭐Java 基本数据类型

Java 中有 8 种基本数据类型，分别为：

1. 4整数类型 ：`byte`、`short`、`int`、`long`
2. 2浮点类型：`float`、`double`
3. 1 字符类型：`char`
4. 1 布尔型：`boolean`。

   1字节 = 8比特

   | 基本类型 | 占用内存（字节Bytes） | 位数 | 默认值  | 范围                                       |
   | -------- | :-------------------- | :--- | :------ | ------------------------------------------ |
   | byte     | 1                     | 8    | 0       | - 2^7 ~ 2^7 - 1  (128~127)                 |
   | short    | 2                     | 16   | 0       | - 2^15 ~ 2^15 - 1 (-32768~32767)           |
   | int      | 4                     | 32   | 0       | - 2^31 ~ 2^31 - 1 (-2147483648~2147483647) |
   | long     | 8                     | 64   | 0L      | - 2^63 ~ 2^63 - 1                          |
   | float    | 4                     | 32   | 0f      | - 2^31 ~ 2^31 - 1 (2147483648~2147483647)  |
   | double   | 8                     | 64   | 0d      | - 2^63 ~ 2^63 - 1                          |
   | char     | 2                     | 16   | 'u0000' | 0 ~ 2^16 - 1                               |
   | boolean  | 1                     | 1    | false   |                                            |

   基本数据类型直接存放在 Java 虚拟机栈中的局部变量表中，而包装类型属于对象类型，我们知道对象实例都存在于堆中。相比于对象类型， 基本数据类型占用的空间非常小。

---

## 字节码

被JVM理解的代码就是字节码（.class文件，十六进制组成）。它不面向任何特定的处理器，只面向虚拟机，因此java编译成字节码文件后，在任何操作系统上都可以运行。因此java具有跨平台移植性以及不错的执行效率。

---

## ⭐ 面向对象
1. 封装：只对象可以隐藏自己的属性和方法不被外界访问
2. 继承：可以基于现有类的基础上定义新的子类
3. 多态：指一个对象可以拥有多种形态，具体的表现为父类的引用指向子类的实例

---
## 抽象类 / 接口 

抽象类是对事物的抽象，而接口是对行为的抽象
1. 子类扩展
	1. 抽象类是单继承，而接口是多继承
2. 属性修饰符
	1. 抽象类不限制
	2. 接口中的属性默认是 public static final 修饰的
4. 方法修饰符
	1. 抽象类中的方法控制符无限制，其中抽象方法不能使用 private 修饰
	2. 接口中方法的默认控制符是 public
6. 方法实现
	1. 抽象类中的普通方法必须有实现，抽象方法必须没有实现
	2. 接口中普通方法不能有具体的方法实现，在 JDK 8 之后 static 和 default 方法必须有方法实现，
7. 静态代码块
	1. 抽象类可以有静态代码块，而接口不能有。
---

## 引用拷贝、浅拷贝和深拷贝

1. 引用拷贝：直接复制对象的==引用地址==
2. 浅拷贝：在堆上创建一个新的对象，内部==引用类型==的属性采用引用拷贝
3. 深拷贝：开辟一个新的对象，复制整个对象，引用类型的属性也会开辟新地址进行值复制

---
## this() / super()

是两个在Java中用于调用构造函数的关键字
1. this() 表示调用同类中的另一个构造器；super() 表示调用父类的一个构造器
2. this() 和 super() 都需要在构造器的第一行调用，且只能调用一个

---

## ⭐final 关键字 
1. final、finally、finalize的区别
	1. final 是==关键字==，表示修饰的对象引用不可变用。可修饰变量、方法和类。
	2. finally 是java中==异常处理==结构的一部分，表示这段代码总会被执行
	3. finalize 是==方法==，在对象被回收的时候被调用。
---

## static 关键字 

一个变量或是方法可以在在没有创建对象的情况下进行调用
1. 静态变量
	1. 这个变量属于类的，类所有的实例都==共享静态变量==，可以直接通过类名来访问它。静态变量在内存中只存在一份
2. 静态方法
	1. 静态方法在==类加载==的时候就存在了，它不依赖于任何实例

---

## ⭐ String / StringBuffer / StringBuilder 

1. String：不可变对象，线程安全，适用于不常修改的场景
	1. String内部维护一个char[]数组，其被private和final修饰
	2. private：将内部数据私有化，同步不提供更改的操作
	3. final：使内部数据无法继承从而避免子类继承来修改
2. StringBuffer：可变对象，线程安全，适用于多线程大量修改的场景
3. StringBuilder：可变对象，线程不安全，适用于单线程大量修改的场景

---

## 反射

反射就是把java类中的各种成分映射成一个个的Java对象，反射使得我们能够在程序运行过程分析类并执行类的方法，通过反射，可以获取到任意类的所有属性和方法并且可以修改属性或执行方法

优缺点
1. 反射使代码更加灵活，许多框架的实现都大量使用了反射
2. 反射会增加安全性问题，并且反射的性能不高
[Java反射](https://www.cnblogs.com/chanshuyi/p/head_first_of_reflection.html)

应用场景
1. 动态代理（Spring）
2. 注解

---


## ⭐ 单例模式 - 创建型 
1. 单例模式是一种创建型设计模式，它确保一个类只有一个实例，并提供了一个全局访问点来访问该实例。
2. 数据库连接池，网站计数器，日志记录器，缓存管理器
3. ==饿汉式==。其在类加载的时候，静态实例`instance` 就已创建并初始化好了
	1. 优点：没有加锁，执行效率会提高，线程安全
	2. 缺点：类加载时就初始化，浪费内存，

		``` java
		public class Singleton {
			private static Singleton instance = new Singleton();
			private Singleton() {}
			public static Singleton getInstance() {
				return instance;
			}
		}
		```

3. ==懒汉式==。为了支持延时加载，将对象的创建延迟到了获取对象的时候
	1. 这种方式采用双锁机制，安全且在多线程情况下能保持高性能。

		``` java
		public class Singleton {  
			private static class SingletonHolder {  
				private static final Singleton INSTANCE = new Singleton();  
			}  
			private Singleton (){}  
			public static final Singleton getInstance() { 
				return SingletonHolder.INSTANCE;  
			}  
		}
		public class Singleton {
			private volatile static Singleton instance = null;
			private Singleton() {}
			public static Singleton getInstance() {
				if (instance == null) {
					synchronized (Singleton.class) {
						if (instance == null) {
							instance = new Singleton();
						}
					}
				}
				return instance;
			}
		}
		```
   4. ==静态内部类==
	   1. 使用静态内部类来实现懒汉式单例模式，保证线程安全和性能。这种方式能达到双检锁方式一样的功效，但实现更简单。
			``` java
			public class Singleton {
			    private Singleton() {}
			    private static class SingletonHolder {
			        private static final Singleton INSTANCE = new Singleton();
			    }
			    public static Singleton getInstance() {
			        return SingletonHolder.INSTANCE;
			    }
			}
			```
	5. ==枚举类==
		 ```java
		public enum Singleton { 
			INSTANCE; 
		}
		```

---

## 简单工厂- 创建型 
1. 面向产品。解耦对象的创建和使用。通过一个工厂类来实现对象的创建，而无需直接暴露对象的创建逻辑给客户端。
2. 使用场景
	1. 对象的创建逻辑比较复杂，不只是简单的 new 一下，而是要组合其他类对象，做各种初始化操作的时候，将复杂的创建逻辑拆分到多个工厂类中，让每个工厂类都不至于过于复杂。
	2. 如果需要创建的产品类数量较多，则工厂类的代码会变得很臃肿，不便于维护。
3. 步骤
	1. 定义一个抽象类
	2. 不同的子类继承这个抽象类
	3. 定义一个简单工厂类实现不同子类的创建
 ```java
abstract class Animal {  public abstract void sound();} 
class Dog extends Animal {  
	@Override  
	public void sound() {...}
}

class AnimalFactory {  
	public static Animal createAnimal(String type) {  
		if (type.equalsIgnoreCase("dog")) {  
			return new Dog();  
		}
	}  
}  
public class simpleFactory {  
	public static void main(String[] args) {  
		Animal dog = AnimalFactory.createAnimal("dog"); 
	}  
}

```
---

## 抽象工厂- 创建型 
1. 面相产品族。通过定义一个创建对象的接口来创建对象，但将具体实现的决定留给子类来决定。  这样就可以有效地减少工厂类的个数。
2. 在抽象工厂中增加创建产品的接口，并在具体子工厂中实现新加产品的创建。
3. 步骤
	1. 定义一个抽象类
	2. 不用的子类继承这个抽象类
	3. 定义一个抽象工厂，创建对象的方法也是抽象的
	4. 不同的子类我们通过不同的工厂去继承抽象工厂中的方法
``` java 
abstract class AnimalFactory {   
	public abstract Animal createAnimal();  
}  
class DogFactory extends AnimalFactory02 {  
	@Override  
	public Animal createAnimal() {  
		return new Dog();  
	}  
}  
public class simpleFactory {  
	public static void main(String[] args) {  
		AnimalFactory dogFactory = new DogFactory();  
		Animal dog = dogFactory.createAnimal();
		dog.sound();  
	}  
}
```

---

 ## 策略模式-行为型
 1. 定义一族算法类，将每个算法分别封装起来，让它们可以互相替换。类的行为或其算法可以在运行时更改。
 2. 应用场景
	 1. 促销策略 / 满减 / 不同等级返现
	 2. 去除复杂的if-else或switch-case
 3. 实现
	1. 创建策略接口
	2. 创建实现接口的不同实现类
	3. 创建 Context 类，随着策略对象改变而改变
	 ```java
	interface Strategy { void sort(int[] arr);}  
	class BubbleSort implements Strategy {  
		@Override  
		public void sort(int[] arr) {...}  
	}  
	class QuickSort implements Strategy {  
		@Override  
		public void sort(int[] arr) {...}   
	}  
	  
	class Context {  
		private Strategy strategy;  
		public void setStrategy(Strategy strategy) {  
			this.strategy = strategy;  
		}  
		public void executeStrategy(int[] arr) {  
			strategy.sort(arr);  
		}  
	}  
	  
	public class StrategyPattern {  
		public static void main(String[] args) {  
			Context context = new Context();  
			
			Strategy bubbleSortStrategy = new BubbleSort(); 
			context.setStrategy(bubbleSortStrategy);  
			context.executeStrategy(arr);
			  
			Strategy quickSortStrategy = new QuickSort();  
			context.setStrategy(quickSortStrategy);  
			context.executeStrategy(arr);  
	  
		}  
	}
	```

## 装饰器模式 - 结构型

1. 装饰器模式主要解决继承关系过于复杂的问题，通过组合来替代继承。
2. 应用场景
	1.  扩展一个类的功能。 
	2. 动态增加功能，动态撤销。
3. 实现
	1. 创建一个 原始类接口，以及其实现类（原始类）
	2. 创建扩展了 原始类接口 的 实体装饰类。
	3. 使用  实体装饰类 来装饰 原始对象。

## 观察者模式- 行为型
1. 行为型设计模式，它定义了一种一对多的依赖关系，当一个对象的状态发生改变时，其所有依赖者都会收到通知并自动更新
2. 应用场景
	1. 消息通知系统
3. 实现
	1. 创建 主题 / 观察者 接口
	2. 创建 主题 / 观察者 实现类
	3. 在客户端代码中创建主题对象和观察者对象，并将观察者注册到主题上。然后，当主题的状态发生改变时，观察者会自动收到通知并执行相应的操作。

---
# Linux
## 服务器
1. 磁盘
	1. `df -h` 看磁盘
	2. `du -sh ` 看文件夹
	3. `ls -lh` 看文件大小
2. CPU
	1. `top -n` 看进程cpu使用率
3. 内存
	1. `free -h` 看物理内存mem和交换内存swap
4. 进程
	1. `ps aux`
	2. `ps -ef | grep 进程名`
## tail
1. 查看最后100行 `tail -n 100 filename
2. 从第 20 行至文件末尾:`tail -n +20 notes.log`
3. 实时显示末尾 `tail -f 100 filename`

## grep
全局正则表达式及打印
1. options
	1. -i：忽略大小写进行匹配。
	2. -v：反向查找，只打印不匹配的行。
	3. -n：匹配行的行号。
	4. -r：递归查找子目录中的文件。
	5. -l：只带有匹配行的文件名
	6. -c：匹配的总行数。
2. 基本搜索 `grep "pattern" filename`
3. 正则表达式搜索 `grep -E "^a" example.txt` 以字母"a"开头的单词

## sed
sed是一种流编辑器，流编辑器会在编辑器处理数据之前基于预先提供一组规则来编辑数据流。sed编辑器可以根据命令来处理数据流中的数据，这些命令要么从命令行中输入，要么存储在一个命令文本中。
`sed [option] command input_file`
1. option
	1. -e \<script>
		1. 将script中指定的命令添加到已有的命令中
	2. -f<script文件 
		1. 将file中指定的命令添加到已有的命令中
	3. -h或--help 显示帮助。
	4. -n
		1. 不产生命令输出，使用print命令来完成输出
	5. -V
		1. 显示版本信息。
2. command
	1. a：追加行，appand。
	2. c\：替换行，c\后面跟上字符串s(多行字符串可以用\n分隔)，则会将当前选中的行替换成字符串s
	3. i\：插入行，i\后面跟上字符串s(多行字符串可以用\n分隔)，则会在当前选中的行的前面都插入字符串s
	4. d：删除行，delete。该命令会将当前选中的行删除
	5. p：打印，print。该命令会打印当前选择的行到屏幕上
	6. y：替换字符，通常y命令的用法是这样的：y/Source-chars/Dest-chars/，分割字符/可以用任意单字符代替，用Dest-chars中对应位置的字符替换掉Soutce-chars中对应位置的字符
	7. s：替换字符串，通常s命令的用法是这样的：1,$s/Regexp/Replacement/Flags，分隔字符/可以用其他任意单字符代替，用Replacement替换掉匹配字符串
3. example
	1. testfile文件的第四行后添加一行
		1. `sed -e 4a\newLine testfile`
	2. 将第 2-5 行的内容取代成为 EXAMPLE 
		1.   `nl testfile | sed '2,5c EXAMPLE'
	3. 数据的搜寻并显示
		1.  `nl testfile | sed -n '/oo/p`

---

## awk
处理文本文件的语言，是一个强大的文本分析工具。
`awk 'pattern { action }' input_file`
1. example
	1. 上述命令将打印 input_file 文件的所有行。
		1. `awk '{ print }' input_file`
	2. 此命令将打印 input_file 文件的第n列
		1. `awk '{ print $n }' input_file`
	3. 打印 input_file 文件中包含 "pattern" 的所有行
		1. `awk '/pattern/ { print }' input_file`
	4. 使用字段分隔符，并打印 input_file 文件的第一个字段。
		1. `awk -F',' '{ print $1 }' input_file`

---
##  CPU 100%

1. 定位高负载进程 pid：
	1. 登录进服务器使用top或top -c命令 p
2. 根据进程pid查出消耗cpu最高的线程号：
	1. top -Hp 18571，按下P，进程按照Cpu使用率排序
3. 根据线程号查出对应的java线程：
	1. 将 十进制线程id 转化为十六进制 
	2. jstack 18571 | vim +/0x4898 -查看线程的堆栈信息。
	3. 区分导致CPU过高的原因具体是Full GC次数过多还是代码中有比较耗时的计算了。如果是Full GC次数过多，那么通过jstack得到的线程信息会是类似于VM Thread之类的线程，而如果是代码中有比较耗时的计算，那么我们得到的就是一个线程的具体堆栈信息如下:



---
# 测试

## 软件测试是什么

在规定的条件下对一个产品或者程序进行操作，以
1. 发现软件错误
2. 衡量软件质量
3. 评估能否能满足设计要求

## 测试开发和测试的区别

1. 测试的任务：检查软件**是否有bug**、是否具**有稳定性**，写出相应的**测试计划、测试规范、测试用例、测试数据、测试报告**。总的来说，就是**确保产品的正常运转**。
1. 测开的任务：在具备测试经验、熟练使用测试工具并有一定开发能力的前提下，可以**自主开发平台，**或对现有的开源工具进行二次开发。最**终目的是提升产品的测试效率**。
1. 两者的关联：测试开发是测试岗位衍生的一个分支，利用开发能力解决测试工作中的问题，小到生成数据、并发模拟等工具的开发，大到整个自动化测试平台的设计与实现，旨在提高效率，降低成本。
    

## 为什么选择测试开发

首先，我也是在学习开发技术的时候接触到测试相关的技术，尤其在在做项目的时候经常需要去做测试，测试的过程我觉得还是挺有意思并且具有技术含量的。后面自己就看了一些测试相关的东西，了解到测试也是产品研发中重要的一环，是产品质量与效率的重要保证，并且测试涉及的技术广度也很深，所以我认为测开岗位也是值得深入的领域。最后，我在浏览贵公司发布的岗位要求的时候，觉得自己的技术栈跟测开岗位也是比较匹配的，所以就投递了测开岗位做一个尝试。

## 一个完整的测试流程

测试工作需要贯穿整个软件的生命周期，可以分为以下几个阶段：
1. 需求评审
2. 测试计划
3. 需求分析：了解和把握功能需求
4. 制定测试计划：根据开发计划确定各个测试时间点
5. 设计测试用例：根据需求写用例
6. 用例评审：与开发人员、项目经理共同商讨，对用例进行评审
7. 执行测试用例：进行测试，做好记录，发现问题要保留现场
8. 缺陷报告编写及提交：写成正式的缺陷报告，提交给开发人员进行确认和修复
9. 跟踪修改情况
    

## 什么是黑盒测试

主要是检查软件的每一个功能是否能够正常使用，检查程序功能是否按照设计需求以及说明书的规定能够正常使用。在测试过程中，不考虑程序内部结构和特性的基础上通过程序接口进行测试

## 黑盒测试常用方法

- 等价类划分：将系统输入划分为若干区域，那么可以认为每类中的一个典型值在测试中的作用与这一类中其他值的作用相同。因此可以从每个部分选取少量代表性数据进行测试
    
- 边界值分析法：边界值分析法是通过优先选择不同等价类间的边界值覆盖有效等价类和无效等价类来更有效的进行测试，因此该方法要和等价类划分法结合使用。选取的测试数据应该刚好等于、刚刚小于和刚刚大于边界值
    
- **判定表法**：判定表驱动法是分析和表达多逻辑条件下执行不同操作的情况的工具。（看不懂）
    
- 错误分析法：错误推测法是基于以往的经验和直觉，参照以往的软件系统出现的错误，推测当前被测程序中可能存在的缺陷和错误，有针对性地设计测试用例。
    

## 什么是白盒测试

它根据程序的控制结构设计测试用例，白盒测试法检查程序内部逻辑结构，对所有的逻辑路径进行测试，是一种穷举路径的测试方法

## 白盒测试常用方法

- 语句覆盖：设计若干个测试用例，使每个执行语句至少被执行一次
    
- 判定覆盖：包含语句覆盖，每个判断的取值分支都至少执行一次
    
- 条件覆盖：包含语句覆盖，判定中每个条件的所有可能结果至少出现一次
    
- 判定条件覆盖：包含判定覆盖、条件覆盖。说白了就是我们设计的测试用例可以使得判断中每个条件所有的可能取值至少执行一次（条件覆盖），同时每个判断本身所有的结果，也要至少执行一次（判定覆盖）
    
- 条件组合覆盖：每个条件的每种组合。在白盒测试法中，选择足够的测试用例，使所有判定中各条件判断结果的所有组合至少出现一次，满足这种覆盖标准成为条件组合覆盖
    
- 路径覆盖：所有路径至少执行一次
---

## 测试用例步骤
1. 详细了解并梳理系统功能需求，必要时找产品进行需求澄清；
2. 如果是比较复杂，或者对原有功能改动较多，在梳理需求的过程最好能画出业务流程图；
3. 根据需求/流程图列出所有功能测试点；
4. 根据测试点编写详细的功能测试用例。

---
## 数据质量
1. 数据完整性测试
	1. 数据不多
		1. 数据是否重复
		2. 数据是否主键唯一
	2. 数据不少
		1. 数据规模决定
			1. 总条数据是否缺失
			2. 日期是否缺失，存在空值
			3. 业务关键字字段是否缺失
		2. 数据规模不确定
			1. 通过历史数据条数的波动性进行对比结果
2. 数据一致性测试
	1. 数据记录规范一致
	2. 数据逻辑一致
	3. 多节点数据一致
3. 数据准确性测试
	1. 数据检查
		1. 数据值是否存在常规范围
		2. 数据值是否在业务范围
		3. 数据值的分布是否异常
	2. 时间维度对比
	3. 数据值的分布是否异常
		1. 上下游数据对比
		2. 与系统内的数据对比
		3. 与系统外的数据对比
4. 数据及时性测试

---

## 微信红包测试

1. 功能测试
	1. 红包填写（边界值分析）
		1. 非特殊日期正确金额
		2. 非特殊日期超出金额
		3. 特殊金额 金额范围
		4. 错误金额
		5. 祝福语 / emoji
	2. 红包发送
		1. 支付金额一致性 / 余额 / 密码验证 / 支付方式
	3. 红包发送成功
		1. 扣款正确 / 消息正确 / 发红包记录
	4. 拆红包
		1. 红包消息显示 / 领取金额 /  退款
	5. 其他功能
2. 性能测试
	1. 多人收发红包
3. 异常测试
	1. 前后台切换，网络异常，低电量，断电，来电，短信等
4. 安全性测试
	1. 敏感隐私内容禁止搜索
5. 兼容性测试
	1. 安卓/iOS，不同分辨率，微信版本
6. 界面测试
	1. 界面颜色/ 无错别字
7. 网络测试
	1. 络兼容性，弱网，无网

---

## 百度搜索测试
1. 功能测试
	1. 输入内容填写（边界值分析）
		1. 内容数据类型
		2. 输入内容长度
		3. 特殊金额 金额范围
		4. 错误金额
		5. 祝福语 / emoji
	2. 红包发送
		1. 支付金额一致性 / 余额 / 密码验证 / 支付方式
	3. 红包发送成功
		1. 扣款正确 / 消息正确 / 发红包记录
	4. 拆红包
		1. 红包消息显示 / 领取金额 /  退款
	5. 其他功能
---
## 共享单车
对于小黄车（或类似的共享单车）的二维码扫描功能，需要进行多方面的测试，以确保用户体验和系统的可靠性。以下是一些测试点：

1. **二维码扫描**：
    - 测试扫描二维码的稳定性和速度。
    - 确保二维码扫描在不同光照条件下都能正常工作。
    - 测试不同类型的二维码，如动态生成的、静态的、不同尺寸的二维码。
    - 验证扫描后是否正确地解析车辆的信息。
2. **用户身份确认**：
    - 测试用户身份验证，确保只有合法用户可以扫描并解锁车辆。
    - 模拟多个用户尝试同时扫描一个码，以确保系统可以正确识别和处理这种情况。
3. **车辆状态**：
    - 确保用户能够获取有关车辆状态的准确信息，如电池电量、车辆位置和可用性。
    - 验证系统是否能够正确显示车辆占用状态和可用状态。
4. **用户行为和事务**：
    - 模拟用户行为，包括扫描、解锁、骑行和锁定车辆，以确保整个流程的可靠性。
    - 测试用户取消或中途中断骑行的情况，以确保系统可以正确处理。
5. **巡视和报告问题**：
    - 测试用户能否报告车辆的问题，如损坏或需要维护。
    - 验证系统是否能够及时更新车辆的状态，以反映问题和解决情况。

对于小程序的测试，可以包括以下内容：

- 测试小程序内嵌的二维码扫描功能，确保其与原生App的性能和可靠性相当。
- 确保小程序能够准确地获取位置信息，以便用户能够找到附近的车辆。
- 测试小程序与后端服务器之间的通信，以确保数据的同步和更新正常进行。

在高峰期，可能会出现多人同时扫描一个码的情况。系统可以采用排队机制或其他方法来管理这种情况。测试需要验证系统是否能够正确识别和分配车辆，避免冲突和混淆。

总之，对于共享单车的二维码扫描功能，测试需要覆盖扫描、用户身份验证、车辆状态、用户行为和各种特定情况的处理。这有助于确保系统的可用性、稳定性和用户友好性。

## 卡牌

1. **卡牌效果测试**:
    
    - 测试某个卡牌的效果是否按照描述的方式生效。例如，使用一张卡牌，然后验证其效果是否正确。
    - 测试不同类型的卡牌（法术、随从、武器）的效果是否在游戏中适用。
2. **回合机制测试**:
    
    - 测试回合结束后，玩家是否获得适当的法力水晶。
    - 测试连续回合的情况，例如回合内的效果是否正常结算。
3. **英雄技能测试**:
    
    - 测试不同英雄的特殊能力是否按规则生效。
    - 测试英雄技能的冷却时间是否正确。
4. **卡牌交互测试**:
    
    - 测试不同卡牌之间的互动，例如随从的战吼效果、亡语效果等。
5. **胜利条件测试**:
    
    - 测试游戏是否在满足胜利条件时结束。例如，验证英雄生命值归零时游戏是否结束。
6. **随机效果测试**:
    
    - 测试涉及随机因素的卡牌效果，例如抽卡、伤害随机目标等。
7. **状态效果测试**:
    
    - 测试状态效果如冻结、沉默、中毒等是否在游戏中正常工作。
8. **牌库与抽牌测试**:
    
    - 测试牌库中的卡牌是否正常抽取，并验证牌库抽光时游戏结束。
9. **武器和攻击测试**:
    
    - 测试武器的攻击力和耐久度是否在战斗中按照规则工作。
10. **场地效果测试**:
    
    - 测试场地上的效果，例如法术石等，是否在游戏中正常应用。
11. **计算与统计测试**:
    
    - 验证游戏中各种数值、统计数据、计分板等是否正确显示。
12. **多人游戏测试**:
    
    - 测试多人对战情况，包括回合同步、网络延迟等方面。
---

#  操作系统
## ⭐  进程间通信方式
每个进程的用户地址空间都是独立的，一般而言是不能互相访问的，但内核空间是每个进程都共享的，所以进程之间要通信必须通过内核。
1. 管道
	1. 匿名管道：用于父子进程间的通信
	2. 命名管道：FIFO，用于没有血缘关系的进程也可以进程间通信
3. 消息队列
	1. 消息队列是保存在内核中的消息链表
4. 共享内存
	1. 拿出虚拟地址空间，映射到相同的物理内存中
5. 信号量
	1. 整型的计数器
6. 信号
	1. 针对异常情况下的工作模式
7. socket
	1. 用于不同主机的进程互相通信

---

##⭐ 虚拟内存
1. 将不同进程的虚拟地址和不同内存的物理地址映射起来。
2. 避免程序直接引用绝对物理地址，让操作系统为每个进程分配独立的一套虚拟地址
---

## 内存分段
1. 分段机制下的虚拟地址由两部分组成，==段选择因子==和==段内偏移量==
2. 段选择因子：保存在段寄存器里面。
	1. 段号，用作段表的索引。
	2. 段表，段的基地址、段的界限和特权等级等。
3. 段内偏移量：应该位于 0 和段界限之间，
	1. 物理内存地址 = 段基地址 + 段内偏移量
4. 不足之处
	1. 内存碎片
	2. 内存交换的效率低
---
## 内存分页
1. 分页是把整个虚拟和物理内存空间切成一段段固定尺寸的大小
2. 步骤
	1. 把虚拟内存地址，切分成页号和偏移量；
	2. 根据页号，从页表里面，查询对应的物理页号；
	3. 直接拿物理页号，加上前面的偏移量，就得到了物理内存地址。
3. 优点：页与页之间是紧密排列的，所以不会有外部碎片。
4. 缺点：
	1. 最小储存一页，会有内部内存碎片；
	2. 有空间上的缺陷，进程太多页表太大（多级页表）
---
## ⭐ 调度算法
1. 进程调度算法
	1. 先来先服务
	2. 最短作业优先。时间最短的进程
	3. 高响应比优先。先计算 响应比优先级
2. 页面置换算法
	1. 最佳页面。优先置换 未来最长时间不访问的页面
	2. 先进先出。内存驻留时间很长的页面
	3. 最近最久未使用。最长时间没有被访问的页面进行置换
3. 磁盘调度算法
	1. 先来先服务。
	2. 最短寻道时间优先。
	3. 扫描算法
---

# JVM
## -3-垃圾回收机制
1. Java的垃圾回收机制是一种自动管理内存的机制，它可以回收不再被使用的对象所占用的内存空间，从而避免内存泄露和内存溢出。
---

## -3- 垃圾处理器
1. Serial
	1. 串行，新生代，复制算法，相应速度优先
	2. 它使用单线程来进行垃圾回收，在进行垃圾回收时会暂停应用程序的所有线程。
2. Parallel
	1.  并行，新生代，复制算法，相应速度优先
	2. 使用多个线程来进行垃圾回收，但在进行垃圾回收时也会暂停应用程序的所有线程。
3. CMS
	1. 并发，老生代，标记清除算法，相应速度优先
	2. 以获取最短回收停顿时间为目标的收集器。，可以在不暂停应用程序的情况下进行垃圾回收。CMS垃圾回收器主要针对的是响应时间敏感的应用程序。
4. G1
	1. 面向服务器的垃圾收集器，主要针对配备多颗处理器及大容量内存的机器.，以极高概率满足 GC 停顿时间要求的同时，还具备高吞吐量性能特征。
5. ZGC
	1. 是一种可扩展的低延迟垃圾回收器，可以在几毫秒内处理数百兆或数千兆堆大小的垃圾回收。ZGC垃圾回收器采用了柔性实时策略，可以有效避免长时间的停顿。它是Java 11中新增的一种垃圾回收器。
---

##  -3- 垃圾回收算法 

1. 标记-清除算法：
	1. 首先标记出所有不需要回收的对象，在标记完成后统一回收掉所有没有被标记的对象
	2. 从根集合（GC Roots）进行扫描，对存活的对象进行标记，标记完毕后，再扫描整个空间中未被标记的对象，进行回收。
	3. 效率不⾼，会造成内存碎⽚。
2. 复制算法：
	1. 将内存分为大小相同的两块，每次使用其中的一块。当这一块的内存使用完后，就将还存活的对象复制到另一块去，然后再把使用的空间一次清理掉。
	2. 内存使⽤率不⾼，只有原来的⼀半。不会造成内存碎片
3. 标记-整理算法：
	1. 标记⽆⽤对象，让所有存活的对象都向⼀端移动，然后直接清除掉未存活的对象。
	2. 不会造成内存碎片
4. 分代算法：
	1. 根据对象存活周期的不同将内存划分为⼏块（新⽣代和⽼年代），根据年代的特点选择合适的垃圾收集算法。
	2. 在新生代中，每次收集都会有大量对象死去而少量存活，所以可以选择”标记-复制“算法，只需要付出少量对象的复制成本就可以完成每次垃圾收集。而老年代的对象存活几率是比较高的，而且没有额外的空间对它进行分配担保，所以我们可以采用标记整理算法或标记复制算法。
---

# Redis
## Redis
1. Redis 是一种基于内存的非关系型数据库，对数据的读写操作都是在内存中完成的，因此读写速度非常快，常用于缓存，消息队列，分布式锁等场景。
2. 高性能：MySQL需要从硬盘读取数据，速度较慢。而Redis可以将数据缓存到内存，从内存中读取，性能会高许多
3. 高并发：Redis(10w QPS) 相比于MySQL(1wQPS以下) 同时可以处理的请求要大得多
---
## 问题
1. 内存不足
	1. 设置合理的内存大小 物理内存的3/4
	2. 大key  debug object key
2. 连接数过多
	1. 调整最大连接数 config set maxclients xxx
3. 慢命令
	1. slowlog get
4. 查询网络延迟
	1. 查询延迟信息 redis-cli-latency 

---
## 数据结构
1. String （key-value结构）：
	1. 缓存、计数、分布式锁、共享 session 信息等。
2. List（LinkedList）：
	1. 消息队列（但是有两个问题：1. 生产者需要自行实现全局唯一 ID；2. 不能以消费组形式消费数据）等。
3. Set（key-set结构，无序唯一）：
	1. 聚合计算（并集、交集、差集）场景，比如点赞、共同关注、抽奖活动等。
4. Hash（ String 类型的 field-value结构）
	1. 缓存对象、购物车等。
5. Zset（有序set，带sorce值）
	1. 排序场景，比如排行榜、电话和姓名排序等。

3 种特殊数据结构
7. BitMap（2.2 版新增）
	1. 二值状态统计的场景，比如签到、判断用户登陆状态、连续签到用户总数等；
8. HyperLogLog（2.8 版新增）
	1. 海量数据基数统计的场景，比如百万级网页 UV 计数等；
9. GEO（3.2 版新增）
	1. 存储地理位置信息的场景，比如滴滴叫车；
10. Stream（5.0 版新增）
	1. 消息队列，相比于基于 List 类型实现的消息队列。

---
## 主从复制
1. 为什么做成主从集群，而不是传统的负载均衡集群。因为redis大多数是读多写少，更多的是读的压力
2. 全量同步
	1. 建立连接，协商同步：从库向主库请求同步，主库收到请求后返回相应给从库，同时开始准备数据同步
	2. 主库将数据同步给从库：主库执行bgsave命令开启子进程生成RDB快照，在生成RDB快照期间，发送RDB以及从库复制RDB的期间，主库的写操作命令会记录到缓冲区（replication buffer）
	3. 主库将增量操作发送给从库：从库完成同步后发送信息给主库，主库收到后，将缓冲区中的写操作命令发送给从库，从库接受后执行，完成同步
3. 增量同步
	1. 主从第一次同步是全量同步，但如果从库重启后同步，就是增量同步
	2. 缓冲区是环形队列，在每次命令传输时，主服务器会把命令记录到这个缓冲区，并使用一个偏移量记录写入的位置，从服务器同步命令时也会用偏移量记下读的位置。当网络中断恢复后，从服务会向主服务发送请求，同时携带偏移量，主服务器收到请求后，会拿着偏移量在环形缓冲区比对：
		1. 如果存在：则返回读写偏移量之间的增量命令给从服务进行同步
		2. 如果不存在：那么说明缺少的数据已经不在环形缓冲区，进行全量复制
---

## 哨兵机制
哨兵机制的作用是实现故障时主从切换，它会对主节点进行监测，如果发现主节点不可用，则选举出新的主节点，并通知从节点和客户端。哨兵的工作有三个：监控、选举、通知。

## 缓存
1. 缓存穿透
	1. 原因：查询的key不存在，请求直接到数据库上
	2. 非法请求的限制
		1.  API 入口处判断求请求参数是否合理
	3. 缓存空对象
		1. 从缓存中读取到空值或者，而不会继续查询数据库。
	4. 布隆过滤器
		1. 快速判断数据是否存在，避免通过查询数据库来判断数据是否存在
		2. 布隆过滤器由「初始值都为 0 的位图数组」和「 N 个哈希函数」两部分组成。
2. 缓存击穿
	1. 原因：某个缓存热点key失效，导致大量请求访问数据库
	2. 热点数据永不过期或者过期时间比较长
	3. 热点数据提前预热
	4. 互斥锁
		1. 保证同一时间只有一个业务线程更新缓存，未能获取互斥锁的请求，要么等待锁释放后重新读取缓存，要么就返回空值或者默认值
3.  缓存雪崩
	1. 原因：某一时间大量的key同时过期，导致大量请求访问到数据库；或者Redis宕机
	2. 设置过期时间的时候加一些随机值
	3.  互斥锁
	4.  后台更新缓存
	5. 设置二级缓存
	6. 设置高可用Redis集群

---
# JUC
## ⭐进程和线程

1. 进程是程序的一次==执行过程==，是系统运行程序的基本单位，因此进程是动态的。系统运行一个程序即是一个进程从创建，运行到消亡的过程
2. 线程是==进程的一个实体==，是程序执行的最小单位 ,，是比进程更小的执行单位。同一进程中的多个线程之间可以==并发执行==并==共享内存资源==。

**为什么使用**
1.  线程可以比作是轻量级的进程，是程序执行的最小单位 , 线程间的切换和调度的成本远远小于进程。这==减少线程上下文切换开销==
	1. ==上下文==：线程在执行过程中自己的运行条件和状态
	2. ==切换==：==保存==线程的上下文信息，留待线程下次占用 CPU 的时候**恢复**现场
		1. 主动让出 CPU，比如调用了 sleep(), wait() 等
		2. 调用了阻塞类型的系统中断，比如线程被阻塞。
2.  在并发量背景下，多线程并发编程正是开发高并发系统的基础，多线程机制可以提高系统并发能力以及性能。

**问题**
1. 内存泄漏、死锁、线程不安全
2. ==线程安全==指：多线程环境下，对于同一份数据，多个线程同时访问，都能保证数据的正确性和一致性。
3. 线程不安全会导致数据混乱、错误或者丢失。

---

##  -0- 线程共享与私有

1. 共享
	1. ==堆==
	2. 方法区 (JDK1.8 之后的==元空间==)资源，
2. 私有
	1. ==程序计数器==
		1. 字节码解释器通过改变程序计数器来依次读取指令，从而实现代码的==流程控制==
		2. 线程切换后能恢复到正确的执行位置
	2. ==虚拟机栈== 
		1. 为虚拟机执行 Java 方法 （也就是字节码）服务
		2. 存储局部变量表、操作数栈、常量池引用等信息
	3. ==本地方法栈==
		1. 为虚拟机执行 Native 方法服务
		2. 保证线程中的==局部变量==不被别的线程访问到

---

##  -0- 并行/并发 同步/异步

1. 并发：两个及两个以上的作业在同一 ==时间段== 内执行。
2. 并行：两个及两个以上的作业在同一 ==时刻== 执行。（同时，多CPU）
2. 同步：调用在发出之后，在没有得到结果之前， 该调用就不可以返回，==一直等待==。
3. 异步：调用在发出之后，==不用等待返回结果==，该调用直接返回。

---

##  -0- 线程的生命周期和状态

1. NEW: ==初始==状态，线程被创建出来但没有被调用 `start()` 。
2. RUNNABLE: ==运行==状态，线程被调用了 `start()`等待运行的状态。
3. BLOCKED：==阻塞==状态，需要等待锁释放。
4. WAITING：==等待==状态，表示该线程需要等待其他线程做出一些特定动作（通知或中断）。
5. TIME_WAITING：==超时等待==状态，可以在指定的时间后自行返回而不是像 WAITING 那样一直等待。
6. TERMINATED：==终止==状态，表示该线程已经运行完毕。

---

## -1- 创建线程五种方式

1. 继承 Thread 类创建线程；
2. 实现 Runnable 接口创建线程；没有返回值，不能抛出异常
3. 通过 Callable 和 Future 创建线程；有返回值，可以抛出异常
4. 使用Lambda表达式
5. 通过线程池创建线程。
---


##  ⭐ 避免死锁 

死锁：多线程同时被阻塞，它们中的一个或者全部都在==等待某个资源被释放==（交叉持有，交叉申请）。线程被无限期阻塞，程序不可能正常终止。

1. ==互斥==条件：该资源任意一个时刻只由一个线程占用。
2. 请求与==保持==条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放。
3. ==不剥夺==条件：线程已获得的资源在未使用完之前不能被其他线程强行剥夺，只有自己使用完毕后才释放资源。
4. ==循环等待==条件：若干进程之间形成一种头尾相接的循环等待资源关系。

**预防死锁** 

1. 破坏持有并等待条件：一次申请所有资源    
2. 破坏不可剥夺条件：当无法声情到自己，将自己占有的资源释放
3. 破坏环路等待条件：按序申请资源，反序释放资源

##  sleep() / wait()

两者都可以暂停线程执行。`wait()` 通常被用于线程间==交互/通信==，`sleep()`通常被用于==暂停==执行。

**区别**
1. 锁
	1. sleep() 方法没有释放锁（只是让出了时间片）
	2. wait() 方法释放了锁
2. 苏醒
	1. sleep()执行完成后，线程会自动苏醒，也可以定时
	2. wait() 被调用后，线程不会自动苏醒，需要别的线程调用 `notify()`或者 `notifyAll()` 方法
3. 所属类
	1. sleep()是 ==Thread 类==的静态本地方法
		1. sleep() 是让当前线程暂停执行，不涉及到对象类，也不需要获得对象锁。
	2. wait() 则是 ==Object 类==的本地方法。
		1. 让获得对象锁的线程实现等待，会自动释放当前线程占有的==对象锁==。
---

## -2- 乐观锁/悲观锁

1. 悲观锁
	1. 写加锁。认为每次访问时都会有人修改数据，适用于写操作多
	2. `synchronized` 和` ReentrantLock` 等独占锁就是悲观锁思想的实现。
2. 乐观锁
	1. 写不加锁。认为每次访问数据时都不会有人来修改数据。
	2. 可以使用版本号机制和 CAS实现。
		1. 操作数据后会检查版本号是否与之前一致，如果不一致，则证明在操作数据期间有另一个人也修改了数据，所以会重新读取，修改，更新数据。
		2. 用一个预期值和要更新的变量值进行比较，两值相等才会进行更新。在 Java 中` java.util.concurrent.atomic `包下面的原子变量类就是使用了乐观锁的一种实现方式 CAS 实现的。
4. 共享锁
	1. 允许多个线程并发访问共享资源。读写锁就是共享锁。
5. 独占锁
	1. 一次只允许一个线程访问一个资源，也叫互斥锁。
6. 公平锁 
	1. 在分配锁的候考虑等待获取锁的队列优先级。先排的先分配，后来的往后稍稍。
7. 非公平锁
	1. 分配时不考虑队列，直接获取锁。
8. 可重入锁
	1. 也叫递归锁，指的是线程可以再次获取自己的内部锁。比如一个线程获得了某个对象的锁，此时这个对象锁还没有释放，当其再次想要获取这个对象的锁的时候还是可以获取的，如果是不可重入锁的话，就会造成死锁

---

## -1- 乐观锁的两种实现方式

1. 版本号机制MVCC
	1. 在修改时会比对版本号是否一致，不一致则失败
		1. 在数据表中加上一个数据版本号 version 字段，表示数据被修改的次数，当数据被修改时，version 值会加 1。
		2. 当线程 A 要更新数据是，会读取 version 值，在提交更新时也会读取version 值==，两次version值相等才更新==，否则重试更新操作，直到更新成功。
2. CAS算法
	1. 比较与交换，在修改值判断要更新的值是否等于预期值
		1. Compare And Swap（比较与交换）。用一个==预期值和要更新的变量值进行比较==，两值相等才会进行更新。
		2. V：要更新的变量值 / E：预期值 / N：拟写入的新值
		3. 当且仅当 V 等于 E 时，CAS 通过原子方式用新值 N 来更新 V 的值。如果不等，说明已经有其它线程更新了 V，则当前线程放弃更新。


---

##  -0- 乐观锁（CAS）的缺点？

1. ==ABA==问题
	1. 读取到的CAS 值，可能经过一次更改但是又被改回
	2. 追加版本号或者时间戳。JDK 1.5 以后的AtomicStampedReference类增加了` compareAndSet `方法，增加并且当前标志是否等于预期标志。
2. ==循环==时间长，开销大
	1. 更新不成功会自旋，循环执行消耗CPU
3. 只能保证==一个共享变量==的原子操作
	1. CAS 只对单个共享变量有效，
	2. JDK 1.5 开始，提供了 `AtomicReference `类来保证引用对象之间的原子性，你可以把多个变量放在一个对象

---

##  可以直接调用 Thread 类的 run 方法吗
no
1. new 一个 Thread，线程进入了==初始==状态。
2. 调用 start()方法，会启动一个线程并使线程进入了==运行==状态
3. 当分配到时间片后就可以开始运行了。 start() 会执行线程的相应准备工作，
4. ==自动执行 run()== 方法的内容，这是真正的多线程工作。

 直接执行 run() 方法，会把 run() 方法当成一个 main 线程下的==普通方法==去执行，并不会在==某个线程中==执行它，所以这并不是多线程工作。

---

##  ⭐volatile

volatile 关键字可以保证==变量的可见性和有序性==，
1. 有序性：
	1. 对变量进行读写操作的时，通过插入特定的==内存屏障==的方式来禁止指令重排序。
		1. 写屏障，写入缓存的数据写回到主内存，所有线程更新
		2. 读屏障，让缓存中的数据失效，重新从主内存加载最新的数据
		3. JVM 会在不影响正确性的前提下，可以调整语句的执行顺序，这被称为指令重排；指令重排在单线程环境下不会出现问题，但在多线程模式下，可能会出现一个线程获得还没有初始化的实例
2. 可见性：
	1. 将变量声明为 volatile ，会指示 JVM，这个变量是==共享==且==不稳定==的，禁止从本地内存读取数据，每次加载数据都要经过==主存==。避免不同线程读取内容不一致的情况
3. 不能保证原子性
	1. 多个线程对于一个int的自增操作，inc 可能只增加了 1
	2. 利用 `synchronized`、`Lock`或者`AtomicInteger`都可以。

---

## -3- synchronized 

同步锁，被它修饰的方法和代码块在同一时刻只能有一个线程执行，  synchronized 关键字解决的是多个线程之间访问资源的同步性。

1. 修饰实例方法：锁资源为当前对象
2. 修饰静态方法：锁对象为当前类对象
3. 修饰代码块：括号内指定
1. 不能修饰构造方法。构造方法本身就属于线程安全的，不存在同步的构造方法一说。

底层
1. 每个对象都会关联一个monitor监视器对象，monitor监视器对象在同一时间只能被一个线程所获取，内部有一个计数器，当计数器为0时表示锁可以被获取；线程获取锁或者重入锁时都会使计数器+1，释放锁时就减1，当减到0就表示这个锁被释放了可以被其他线程获取

---

## -2- synchronized / volatile 

1. volatile 关键字是线程同步的==轻量==级实现，所以 volatile性能肯定比synchronized关键字要好 。
2. 对象
	1. volatile 关键字==只能用于变量== 
	2. synchronized 关键字可以修饰变量，方法以及代码块 。
4. volatile 保证可见性，不保证原子性。synchronized 关键字保证可见性和原子性。
5. volatile关键字主要用于解决==变量==在多个线程之间的==可见性==
   synchronized 关键字解决的是多个线程之间==访问资源的同步性==。

---

## -1-  ReenTrantLock  / synchronized
1. synchronized  是和 for、while 一样的关键字，ReentrantLock 是类实现了Lock接口，是==可重入且独占且非公平==式==的锁。既然 ReentrantLock 是类，那么它更灵活，增加了轮询、超时、中断、公平锁（先申请先获取锁）和非公平锁等高级功能。
2. 两者都是==可重入锁==
	1. 同一个线程可以再次获取自己的内部锁。避免死锁。
3. synchronized依赖于 ==JVM== ， ReenTrantLock依赖于 ==API==。
	1. synchronized 是依赖于 JVM 实现的，优化都是在虚拟机层面实现的
	2. ReenTrantLock 是 API 层面，需要 lock() 和 unlock 方法配合 try/finally 语句块来完成锁的释放;
4. ReentrantLock 有高级功能
	1. 等待==可中断== 
		1. 正在等待的线程可以选择放弃等待，改为处理其他事情。（ synchronized 属于不可中断锁）
	2. 可实现==公平锁== 
		1. 锁被释放之后，先申请的线程先得到锁。
	3. 可实现选择性通知（锁可以==绑定多个条件==）
		1. Condition接口与newCondition()方法。实现等待/通知机制。

---

## -1- Atomic
1. Atomic 是指一个操作是不可中断的。即使是在多个线程一起执行的时候，一个操作一旦开始，就不会被其他线程干扰。所以，所谓原子类说简单点就是具有原子操作特征的类。volatile不保证原子性，volatile+CAS
2. volatile+CAS
3. 基本类型原子类：AtomicInteger
4. 数组类型原子类：AtomicIntegerArray
5. 引用类型原子类：AtomicReference
6. 对象的属性修改类型：AtomicIntegerFieldUpdater


## ⭐ ThreadLocal 原理

1. ThreadLocal 类让每个线程绑定自己的==专属本地变量==。
2. 如果创建了一个ThreadLocal变量，那么访问这个变量的每个线程都会有这个变量的==本地副本==，他们可以使用 `get（）` 和 `set（）` 方法来获取默认值或将其值更改为当前线程所存的副本的值，从而避免了线程安全问题。

**原理**

1. 每个线程都有自己的ThreadLocalMap，当使用ThreadLocal时，会先获取到当前线程，再获取当前线程的ThreadLocalMap，其中键就是ThreadLocal，值就是数据，从而获取到每个线程独有的数据

**使用场景**
1. 使用ThreadLocal为每个线程分配一个 ==JDBC 连接== 。这样就可以保证每个线程的都在各自的 连接 上进行数据库的操作，不会出现 A 线程关了 B线程正在使用的 连接 ；
2. 在调用 API 接口的时候传递了一些==公共参数==，可以用ThreadLocal代替，避免参数的显式层层传递。

 **内存泄露问题**
 1. 在ThreadLocalMap中，键是弱引用，而值是强引用，因此当键被内存清理时会变成null导致值无法清除，value 永远无法被 GC 回收，

这样一来，ThreadLocalMap 中就会出现 key 为 null 的 Entry。假如我们不做任何措施的话，value 永远无法被 GC 回收，这个时候就可能会产生内存泄露。ThreadLocalMap 实现中已经考虑了这种情况，在调用 set()、get()、remove() 方法的时候，会清理掉 key 为 null 的记录；使用完 ThreadLocal方法后 最好手动调用`remove()`方法.



---

## ⭐ 线程池

线程池是管理一系列线程的资源池。当有任务要处理时，直接从线程池中获取线程来处理，处理完之后线程并不会立即被销毁，而是等待下一个任务。
1. 降低==资源消耗==。通过重复利用已创建的线程降低线程==创建和销毁==造成的消耗。
2. 提高==响应速度==。当任务到达时，任务可以不需要等到线程==创建==就能立即执行。
3. 提高线程的==可管理性==。线程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以进行==统一分配==，调优和监控。

---

## 线程池参数
ThreadPoolExecutor 3 个最重要的参数
1. corePoolSize 核心线程大小
	1. 最少线程数
2. maximumPoolSize 最大线程数量
	1. 任务队列中存放的任务达到队列容量的时候，当前可以同时运行的线程数量变为最大线程数。
3. workQueue 工作队列 
	1. 新任务来的时候会先判断当前运行的线程数量是否达到核心线程数，如果达到的话，新任务就会被存放在队列中。
1. keepAliveTime 
	1. 一个线程如果处于空闲状态，并且当前的线程数量大于corePoolSize，那么在指定的时间后，这个空闲的线程将被销毁
2. unit :
3. threadFactory :executor
	1. 创建新线程的时候会用到。
4. handler 
	1. 拒绝策略 


---

## -3- 线程池的四种创建类型

1. 通过ThreadPoolExecutor构造函数来创建（推荐）
2. 通过Executor 框架的工具类 Executors 来实现

多种类型的 `ThreadPoolExecutor`：
1. FixedThreadPool： 
	1. 该方法返回一个==固定线程数量==的线程池
	2. 使用的是无界的任务队列，可能堆积大量的请求，容易导致 OOM
3. ScheduledThreadPool：
	1. 可以设置定期的执行任务的线程池
4. SingleThreadExecutor： 
	1. 方法返回一个只有==一个线程==的线程池
	2. 使用的是无界的任务队列，可能堆积大量的请求，容易导致 OOM
6. CachedThreadPool：
	1. 可缓存线程池。该方法返回一个可根据实际情况==调整线程数量==的线程池
	2. 使用的是同步队列，如果任务数量过多且执行速度较慢，可能会创建大量的线程，从而导致 OOM

---

## -0- 线程池的三种阻塞队列
新任务来的时候会先判断当前运行的线程数量是否达到==核心线程==数，如果达到的话，新任务就会被存放在队列中。
1.  ArrayBlockingQueue ==有界队列==
	1. 基于数组的先进先出队列，有界
2.  LinkedBlockingQueue ==无界队列==
	1. 基于链表的先进先出队列，无界
3.  SynchronousQueue ==同步队列==
	1. 无缓冲的等待队列，无界。有空闲则处理，无空闲新开线程。容易OOM

---

##  -0- 线程池四种拒绝策略 / 饱和策略
如果当前同时运行的线程数量达到最大线程数量并且队列也已经被放满了任务时，ThreadPoolTaskExecutor 定义一些策略:
1. AbortPolicy： 丢任务抛出异常（默认）
2. DiscardPolicy：丢任务不抛异常
3. DiscardOldestPolicy： 将最早进入队列的任务删除，之后再尝试加入队列
4. CallerRunsPolicy：回退给调用者来执行

---

##  -0- 线程池提交流程
1. 在使用execute方法提交一个Runnable对象时
2. 如果当前运行的线程数小于==核心线程数==，那么就会新建一个线程来执行任务。
3. 如果当前运行的线程数大于等于核心线程数，但是小于==最大线程数==，那么就把该任务放入到任务队列里等待执行。
4. 如果向任务队列投放任务失败（任务队列已经满了），但是当前运行的线程数是小于最大线程数的，就新建一个线程来执行任务。
5. 如果当前运行的线程数已经等同于最大线程数了，新建线程将会使当前运行的线程超出最大线程数，那么当前任务会被拒绝，饱和策略

在使用execute方法提交一个Runnable对象时
2.会先判断当前线程池中的线程数是否小于corePoolSize
3.如果小于则创建新线程并执行runnable.
4.如果大于或者等于，则尝试将Runnable加入到workQueue中
5.如果workQueue没满，则将Runnable正常入队，等待执行
6.如果workQueue满了，则会入队失败，那么会尝试继续增加线程
7.判断当前线程池中的线程数是否小于maximumpoolSize
8.如果小于，则创建新线程并执行任务899·
9.如果大于等于，则执行拒绝策略，拒绝此Runnable

---
# Spring
## ⭐Spring
Spring 是一款开源的轻量级 Java 开发框架，旨在提高开发人员的开发效率以及系统的可维护性。提供了一种更加轻量级和可扩展的方式来处理应用程序的各种方面，包括依赖注入、事务管理、AOP（面向切面编程）、数据访问、消息传递等
1. Spring IoC
	1. IoC意思为控制反转，是一种设计思想：
		1. 控制：对于对象的控制权（实例化、管理）
		1. 反转：将控制权交给外部进行管理（框架、IoC容器）
	2. 作用：可以将复杂的对象依赖关系将给IoC容器进行统一的管理，并由 IoC 容器完成对象的注入，从而简化应用的开发
	3. 实现原理：其实现方法是依赖注入，工厂模式+反射
2. Spring AOP
	1. 意思为面向切面编程，将与业务无关的通用代码（例如事务管理、日志管理、权限控制等等）进行封装，从而降低耦合性，使代码易于拓展和维护
	2. Spring AOP是基于动态代理来实现AOP的，当目标对象实现了某个接口时，那么Spring AOP会通过JDK Proxy来创建代理对象；当目标对象没有实现接口时，会通过Cglib生成一个目标对象的子类来作为代理对象。
		1. 动态代理是一种在运行时动态生成代理对象的技术
---
## 注释
1. 声明bean的注解
	1. @Component 组件，没有明确的角色
	2. @Service 在业务逻辑层使用（service层）
	3. @Repository 在数据访问层使用（dao层）
	4. @Controller 在展现层使用，控制器的声明（C）
2. 注入bean的注解
	1. @Autowired：由Spring提供
	2. @Resource：由JSR-250提供
3. java配置类相关注解
	1. @Configuration 声明当前类为配置类，相当于xml形式的Spring配置
	2. @Bean 注解在方法上，声明当前方法的返回值为一个bean，替代xml中的方式
4. 切面（AOP）相关注解
	1. @Aspect 作用是把当前类标识为一个切面供容器读取
		1. @After 在方法执行之后执行
		2. @Before 在方法执行之前执行
		3. @Around 在方法执行之前与之后执行

---

##  @Component  /  @Bean
1. @Component作用于==类==，而@Bean作用于==方法==
2. @Component通过==类路径搜索==自动加载到容器中，而@Bean一般在==方法中自定义产生==bean然后提交给容器
3. 一些场景，例如第三方的库，只能通过@Bean注册bean
    

## @Autowired和@Resource的区别
1. @Aurowired是==Spring==提供的注解，@Resource是==JDK==提供的注解    
2. @Autowired默认匹配==类型==，@Resource默认匹配==名字==
3. 当一个接口有多个实现类时，两者都无法匹配，@Autowired通过@Qualifier指定名字，@Resource通过name指定名字
---

## Bean的作用域有哪些
1. singleton：单例模式，在容器中唯一
2. prototype：每次获取Bean都会创建新对象

针对Web环境：
1. request：每次请求都会创建新的Bean
2. session：每次新的会话都会创建新的Bean
3. application：每次启动新的Web应用时创建新的Bean    
4. websocket：每次开启一个websocket创建新的Bean 
---

## 单例Bean的线程安全问题

单例Bean是线程不安全的，一般有两种解决方案：
1. 尽量避免在Bean中定义可变的变量
2. 在Bean中使用ThreadLocal来保存变量
Bean一般都是无状态的（没有成员变量），这种情况下可以不考虑线程安全问题
---

## Bean的生命周期

1. 根据Bean定义利用反射创建实例
2. 设置Bean的属性值
3. 检查Bean是否实现了`Aware`相关接口并执行
4. 调用容器的`BeanPostProcessor`的前置处理方法
5. 检查Bean是否实现了`InitializingBean`接口并执行`afterPropertiesSet`方法
6. 检查是否配置了Bean的inti-method方法并执行
7. 调用容器的`BeanPostProcessor`的后置处理方法
8. 使用中
9. 销毁Bean时，检查是否实现了`DisposableBean`接口并执行`destoty`方法
10. 销毁Bean时，检查是否配置了destory-method并执行

---

## ⭐SpringBoot 启动流程

1. 构造SpringApplication的实例：
	1. 将启动类添加到SpringApplication的属性当中
	2. 获取应用类型并判断是否是web工程，设置到属性中
	3. 创建并初始化所有的初始化器，添加到initializers属性中    
	4. 创建并初始化所有的监听器，添加到listeners属性中
	5. 初始化主类mainApplicationClass
2. 调用run方法：    
	1. 获取监听器及参数配置，并启动
	2. 打印banner信息
	3. 创建并初始化容器
	4. 监听器发送通知告知启动完成
   
---

## SpringBoot 优点

1. 可以快速构建项目
2. 提供默认配置，减少重复开发
3. 内嵌Http服务器，可以方便的测试和开发web应用
4. 极大提高项目开发和部署效率
5. 提供多种插件
6. 提供运行时程序监测

---

## SpringBoot 自动装配
在主程序中添加@SpringBootApplication或者@EnableAutoConfiguration注解，就会自动去读取starter中的spring.factories文件，其中就配置了所需要的bean（约定）

---

## ⭐AspectJ 定义的通知类型有哪些？

1. Before：方法调用前执行
2. After：方法调用后执行
3. AferReturning：方法返回后执行
4. AfterThrowing：抛出异常后执行
5. Around：可以拿到目标对象和调用方法，从而在调用方法前后随意操作
---

## Spring AOP / AspectJ AOP

1. AOP是运行时增强，而Aspect是编译时增强
2.  Spring AOP 基于代理(Proxying)，AspectJ 基于字节码操作(Bytecode Manipulation)。
3. 在切面较少时，两者性能差不多；在切面很多时，AspectJ性能更好
4. 多个切面的执行顺序，通常使用@order决定，值越小优先级越高

##  SpringMVC

一种设计思想。模型、视图、控制器的缩写。其核心思想是将业务逻辑、数据、显示进行分离

---


# 算法
## 十大排序
[十大排序算法)](https://zhuanlan.zhihu.com/p/57088609/)
1. 归并排序 $O(N^2)$ $O(1)$
	1. 归并排序是建立在归并操作上的一种有效的排序算法。该算法是分治法的典型应用。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为二路归并。   
	2. 分解：将当前区间一分为二，即求分裂点 mid = (low + high) / 2；
	3. 求解：递归地对两个子区间 low…mid和 mid+1…high 进行归并排序。递归的终结条件是子区间长度为1；
	4. 合并：将已排序的两个子区间 low…mid 和 mid+1…high 归并为一个有序的区间 low…high
		``` java
		public static void mergeSort(int[] arr, int l, int r) {  
		    if (l >= r) return;  
		    int m = l + (r - l)/2;  
		    mergeSort(arr, l, m);  
		    mergeSort(arr, m + 1, r);  
		    merge(arr, l, r, m);  
		}  
		public static void merge(int[] arr, int l, int r, int m) {  
		    int[] tmp = new int[r - l + 1];  
		    int i = l;  
		    int j = m + 1;  
		    int k = 0;  
		    while (i <= m && j <= r) {  
		        if (arr[i] < arr[j]) {  
		            tmp[k++] = arr[i++];  
		        } else {  
		            tmp[k++] = arr[j++];  
		        }  
		    }  
		    while(i <= m) tmp[k++] = arr[i++];  
		    while(j <= r) tmp[k++] = arr[j++];  
		    for (i = 0; i < k; i++) {  
		        arr[l++] = tmp[i];  
		    }  
		}
		```
2. 快速排序  $O(NlogN)$ $O(NlogN)$ [[quickSort]]
	1.  从要排序的数据中取一个数为“基准数”。 
	2. 通过一趟排序将要排序的数据分割成独立的两部分，其中左边的数据都比“基准数”小，右边的数据都比“基准数”大。
	3. 然后再按步骤2对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列。
		``` java
		    private static void quickSort(int[] arr, int l, int r) {
				if(l >= r) return;  
				int i = l;  
				int j = r;  
				int index = arr[i];  
				while (i < j) {  
				    while(i < j && arr[j] >= index) j--;  
				    if (i < j) arr[i++] = arr[j];  
				    while(i < j && arr[i] < index) i++;  
				    if (i < j) arr[j--] = arr[i];  
				}  
				arr[i] = index;  
				quickSort(arr, l, i-1);  
				quickSort(arr, i+1, r);
		    }
		```
1.  选择排序 $O(N^2)$ $O(1)$
	1. 首先，找到数组中最小的那个元素，其次，将它和数组的第一个元素交换位置(如果第一个元素就是最小元素那么它就和自己交换)。其次，在剩下的元素中找到最小的元素，将它与数组的第二个元素交换位置。如此往复，直到将整个数组排序。这种方法我们称之为**选择排序**
		```java
		    public static int[] selectSort(int[] a) {
		        int n = a.length;
		        for (int i = 0; i < n - 1; i++) {
		            int min = i;
		            for (int j = i + 1; j < n; j++) {
		                if(a[min] > a[j]) min = j;
		            }
		            //交换
		            int temp = a[i];
		            a[i] = a[j];
		            a[j] = temp;
		        }
		        return a;
		    }
		```
		  

## 连续登录7天用户数
1. 只保留当天的一次登录
2. 根据登录日期分配行号
3. 计算登录的第一天

```sql
# 找出连续登录7天的用户数  
select count(distinct name) num  
from (select name, base_dt, count(1)  
         from (select *, DATE_SUB(dt,INTERVAL rn DAY) as base_dt  
                 from ( select *, row_number() over(partition by a.name order by a.dt) as rn  
                         from( select name, date(dt) as dt from login_log 
	                         # where dt >= CURDATE() - INTERVAL 7 DAY
	                         group by name, date(dt)) a  
                         ) b  
                 ) c  
group by name,base_dt HAVING COUNT(1)>=7 ) d;  
  
# 找出连续登录7天的用户  
select name,  
       count(1)  
from ( select *, DATE_SUB(dt,INTERVAL rn DAY) as base_dt  
        from ( select *, row_number() over(partition by a.name order by a.dt) as rn  
                from ( select name, date(dt) as dt from login_log group by name, date(dt)) a  
                ) b  
        ) c  
group by name, base_dt HAVING COUNT(1)>=7;
```

## 7天内登录三天的用户
```sql
SELECT name  
FROM login_log  
where dt >= CURDATE() - INTERVAL 7 DAY  
# where dt >= date('2021-03-05 09:58:29.438123') - INTERVAL 7 DAY  
GROUP BY name  
HAVING COUNT(DISTINCT DATE(dt)) >= 3;
```


## 笔试
1. 丢失报文的位置
	1. 初始化两个整数变量 `min` 和 `max`，分别用于记录数组中最小元素的索引和值。
	2. 遍历数组，从最小元素的位置开始搜索特定值的起始和结束索引。
	3. 计算当前搜索的数组索引，通过取余确保在数组范围内循环。
	4. 输出查找到的特定值的起始和结束索引。
2. 快速传球
	1. 创建一个队列用于广度优先搜索，创建一个map用于记录每个位置的最短距离
		1. key是坐标 row * 100 + col value是次数
	2. 进入广度优先搜索循环，直到队列为空 上右下左
	3. 判断是否越界，以及是否来过  row2 * 100 + col2
3. 模拟
	1. 处理一行输入
		1. 按等号分割输入 
			1. 有等号。
				1. 是let复制。
					1. 获取左边的变量名，左边的计算用空格分割，按不同的运算符计算
			2. 无等号。
				1. 判断是否是out函数。是则直接输出
	2. 判断是否是合法整数
		1. try...catch Integer.parseInt(s);
	3. 判断是否是合法变量
		1. `first != '_' && !Character.isLetter(first)`
 