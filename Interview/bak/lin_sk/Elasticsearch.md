# Elasticsearch

### ElasticSearch是什么？基于Lucene的，那么为什么不是直接使用Lucene呢？

Elasticsearch封装了Lucene的复杂性，提供Restful风格的接口，使用更加方便简单

### 什么是倒排索引

词到文档的映射

### ES中索引模板是什么

是一种告诉ES创建索引时如何进行配置的方法，在创建索引时作为基础从而重用其中的设置和映射

### ES中索引的生命周期管理

需求：随着索引不断增加，会导致空间不足，性能降低。只有最近的数据会经常被访问（热点数据），而有些数据几乎不再访问（历史数据），因此可以对不常访问的数据进行管理或清除

生命周期阶段：

- hot：存在写操作和读操作
- warm：不存在写操作，有读操作
- cold：不存在写操作，很少有读操作
- delete：没有读写操作，可以安全删除

### ES查询和聚合有哪些语法

查询：

- 基于文本：match
- 基于词项：term
- 复合查询

聚合：

- bucket
- metric
- pipline

### query和filter有什么区别

- query会进行匹配查询，同时会计算分数（匹配度）
- filter也是匹配查询，但不计算分数，仅仅过滤

### match和term有什么区别

- match模糊查询，对关键词分词后匹配
- term完全匹配

### should和must有什么区别

- should任意匹配，类似or
- must全部匹配，类似and

### match，match_phrase和match_phrase_prefix有什么区别

- math：普通的匹配查询，分词后匹配
- match_phrase：分词后匹配，但是分词需要全部匹配到并且按顺序匹配
- match_phrase_prefix：在match_phrase的基础上，提供一种可以让最后一个词项作为前缀匹配的方法

### 什么是复合查询，有哪些复合查询

- bool query（布尔查询）：用于将多个子查询进行组合
- boosting query（提高查询）：可以降低一些查询的显示的权重（降低分数）
- constant_sorce（固定分数查询）：查询时固定的返回指定的分数
- dis_max（最佳匹配查询）：取分数最高的查询分数最为最终的分数（一般的查询会将分数相加，这里取max）
- function_sorce（函数分数查询）：用自定义的函数计算分数

### 聚合查询有哪些

- bucket：桶聚合，根据标签分类，统计各个类中的数量
- metric：指标聚合，常用的有求最值，求均值
- pipline：管道聚合，对聚合后的桶再聚合操作，不如按类别分分组后再求各个组的平均值

### 聚合查询的基本语法

往往在query语法后使用，仅对查询结果进行聚合

三要素：

- 聚合名称：用户自定义
- 聚合类型：选择用哪个聚合函数
- 聚合字段：哪个字段上聚合

可配置属性：

- size：限定返回的数量
- order：排序

### ES的整体结构

- 一个ES下包含多个节点
- 节点中包含一些分片
- 分片本质就是Lucene index，内部有许多的段文件
- 段文件包含底层数据结构，包括：倒排索引、Doc Values、文档

### ES读写单个文档的流程

写：

1. 请求发送到任意节点，此时该节点成为协调节点
2. 协调节点确定文档id属于哪个分片，根据路由表找到对应主分片的节点，发送请求
3. 主分片节点收到请求后进行写操作，然后将请求转发到所有副分片节点，等待全部写入成功，主分片节点就像协调节点报告完成写入，协调节点返回客户端结果

读：

1. 请求发送到任意节点，此时该节点成为协调节点
2. 协调节点确定文档id属于哪个分片，根据路由表找到任意一个副分片节点（轮询），发送请求
3. 副分片节点收到请求后，读操作并将结果返回给协调节点，协调节点收到后返回给客户端

### ES Search流程

当发情query等查询操作时，会分两阶段执行：

- 查询阶段：
  1. 请求发送到任意节点，此时该节点成为协调节点
  2. 协调节点会将查询请求发送到所有的分片上
  3. 各个分片收到请求后进行查询操作，将查询结果添加到自己的本地优先有序队列当中
  4. 所有分片将结果返回给协调节点，协调节点将所有队列进行合并，得到结果的有序集合（仅包含文档id和sorce值）
- 拉取阶段：
  1. 协调节点需要根据队列中文档id去获得具体的文档，向相对应的节点发送读请求
  2. 对应节点收到读操作后，返回结果给协调节点
  3. 协调节点收集到所有文档后，返回给客户端

### ES底层数据持久化的过程

1. write：当新文档写入时，保存到内存缓冲区，顺便记录到事务日志（translog）
2. refresh：默认间隔1秒，会将内存缓冲区的文档写入文件系统缓存中，写完后情况内存缓冲区，此时文档可以被查询，但未持久化
3. flush：每隔一段时间，将文件系统缓存中的数据刷入磁盘，同时清空日志
4. merge：每次刷新都会尝产生新的段文件，随着段文件越来越多，后台会对段文件进行合并

### ES遇到什么性能问题，如何优化的

- 禁止swap
- 增大刷寻时间间隔
- 合理的映射配置：有些字段可以不设置分词器
