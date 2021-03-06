# KafkaDemo
Apache kafka是消息中间件的一种， 用于构建实时数据管道和流应用程序，小白学习

kafka中文教程：<br/>
http://orchome.com/kafka/index<br/>
<br/>
Kafka在windows安装运行：<br/>
http://blog.csdn.net/evankaka/article/details/52421314<br/>
<br/>

Apache Kafka 分布式消息队列中间件安装与配置：<br/>
http://blog.csdn.net/wangjia184/article/details/37921183<br/>

kafka单节点启动<br/>
https://blog.csdn.net/l1028386804/article/details/78348367

# 注意：
1. kafka安装目录下config/server.properties有如下配置信息，listeners配置的是hostname：<br/>
> listeners=PLAINTEXT://node1:9092

利用kafka的producer API生产数据时，需要在程序运行的客户端的hosts文件上配置kafka集群每台机器的ip-hostname，如：<br/>
>192.168.187.201 node1<br/>
 192.168.187.202 node2<br/>
 192.168.187.203 node3
 
 否则会报错<br/>
 - 配置log4j日志，可以看到报 "java.io.IOException: Can't resolve address: node1:9092"错误
 - 不配置日志，可以看到报"Expiring 3 record(s) for zlikun_topic-1: 30043 ms has passed since batch creation plus linger time"错误
 
2. kafka安装目录下config/server.properties有如下配置信息，listeners配置的是ip地址：<br/>
 > listeners=PLAINTEXT://192.168.187.201:9092
 
 参考资料：<br/>
 配hostname的解决方法：https://segmentfault.com/q/1010000008863969<br/>
 直接配ip地址，而不是hostname: http://www.orchome.com/946
 
 kafka安装部署请参考：https://www.cnblogs.com/swordfall/p/8859053.html
 
 ### Kafka压力测试
 https://blog.csdn.net/laofashi2015/article/details/81111466
 
 ### Kafka监控
 kafka eagle:<br/>
 https://www.cnblogs.com/smartloli/p/5829395.html<br/>
 https://github.com/smartloli/kafka-eagle<br/>
 kafka-eagle报错JMX service url[192.168.187.202:9999] create has error,msg is Connection refused to host: 127.0.0.1; nested exception is: java.net.ConnectException: Connection refused (Connection refused)<br/>
 >这个是由于/etc/hosts与hostname配置不正确所导致<br/>
 /etc/hosts需配置kafka集群所有的ip和hostname对应<br/>
 hostname设置为/etc/hosts里面所对应的hostname<br/>
 
 kakfa manager:<br/>
 https://blog.csdn.net/yuan_xw/article/details/79188565<br/>
 https://github.com/yahoo/kafka-manager<br/>
 https://www.cnblogs.com/dadonggg/p/8205302.html<br/>

### kafka JMX监控
https://blog.csdn.net/u013256816/article/details/53524884<br/>
https://blog.csdn.net/feelwing1314/article/details/80808721<br/>

### 如何为Kafka集群选择合适的partitions数量：
https://www.cnblogs.com/fanguangdexiaoyuer/p/6066820.html<br/>

### kafka的topic及日志删除
https://www.cnblogs.com/moonandstar08/p/6204581.html

### kafka中partition和消费者的关系
https://www.jianshu.com/p/6233d5341dfe

### kafka配置合适的partitions数量
1. 一般建议：Partitions Num = Broker Num * Consumer Num<br/>
2. kafka权威指南所说的，分区数 = 每秒的写入量/每秒的消费量，partition最好小于kafka集群的总cores数<br/>
3. 每秒目标吞吐量t，每秒生产量p，每秒消费量c，max(t/p, t/c) 最大值<br/>

https://www.jianshu.com/p/8689901720fd<br/>
https://yezhwi.github.io/bigdata/2018/05/25/Kafka%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E6%80%BB%E7%BB%93/<br/>
http://shift-alt-ctrl.iteye.com/blog/2423162

### Kafka提供两种策略去删除旧数据。一是基于时间，二是基于partition文件大小
http://www.jasongj.com/2015/01/02/Kafka%E6%B7%B1%E5%BA%A6%E8%A7%A3%E6%9E%90/

### kafka性能测试方法及Benchmark报告
http://www.uml.org.cn/bigdata/201709252.asp<br/>
https://www.hadoop1024.com/2015/10/15/kafka%E6%80%A7%E8%83%BD%E6%B5%8B%E8%AF%95/

### kafka清空数据
https://blog.csdn.net/belalds/article/details/80575751

### kafka集群调优
https://www.iteblog.com/archives/1879.html<br/>
https://blog.csdn.net/high2011/article/details/79822730<br/>
