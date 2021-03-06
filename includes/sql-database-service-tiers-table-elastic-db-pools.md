
### <a name="basic-elastic-pool-limits"></a>基本弹性池限制
|  |  |
| --- |:---:|
| 每个池的最大 eDTU 数 |&nbsp;100 &nbsp;&nbsp;&nbsp; 200 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp;&nbsp;&nbsp; 1200 |
| 每个池的最大存储空间 (GB)* |&nbsp;&nbsp;&nbsp;&nbsp;10 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;20 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;39 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;73 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;117 |
| 每个池的数据库的最大数目 |&nbsp;&nbsp;&nbsp;200 &nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 |
| 每个池的最大内存中 OLTP 存储 (GB) |不适用 |
| 每个池的最大并发工作线程数 |&nbsp;&nbsp;&nbsp;200 &nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp;&nbsp;2400 |
| 每个池的最大并发登录数 |&nbsp;&nbsp;&nbsp;200 &nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp;&nbsp;2400 |
| 每个池的最大并发会话数 |4800 &nbsp;9600 &nbsp; 19200 &nbsp; 28800 &nbsp; 28800 |
| 每个数据库的最大 eDTU 数* |5 |
| 每个数据库的最小 eDTU 数* |0,5 |
| 每个数据库的最大存储空间 (GB)** |2 |
| 时间点还原 |过去 7 天的任一时间点 |
| 灾难恢复 |活动异地复制 |
|  | |

* 只要所选的池 DTU 大小与每个 DB 的最大 eDTU 数一样大，每个数据库的最大和最小 eDTU 数就可能设置为任何列出的值 

** 弹性数据库共享池存储空间，因此数据库存储空间限制为小于池的剩余存储空间或每个数据库的最大存储空间

### <a name="standard-elastic-pool-limits"></a>标准弹性池限制
|  |  |
| --- |:---:|
| 每个池的最大 eDTU 数 |&nbsp;100 &nbsp;&nbsp;&nbsp; 200 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp;&nbsp;&nbsp; 1200 |
| 每个池的最大存储空间 (GB)* |&nbsp;100 &nbsp;&nbsp;&nbsp; 200 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp;&nbsp;&nbsp; 1200 |
| 每个池的数据库的最大数目 |&nbsp;200 &nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;400 |
| 每个池的最大内存中 OLTP 存储 (GB) |不适用 |
| 每个池的最大并发工作线程数 |&nbsp;&nbsp;200 &nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp; 2400 |
| 每个池的最大并发登录数 |&nbsp;&nbsp;200 &nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp; 2400 |
| 每个池的最大并发会话数 |4800 &nbsp; 9600 &nbsp;19200 &nbsp;28800 &nbsp;&nbsp; 28800 |
| 每个数据库的最大 eDTU 数* |10, 20, 50, 100 |
| 每个数据库的最小 eDTU 数* |0, 10, 20, 50, 100 |
| 每个数据库的最大存储空间 (GB)** |250 |
| 时间点还原 |过去 35 天的任一时间点 |
| 灾难恢复 |活动异地复制 |
|  | |

* 只要所选的池 DTU 大小与每个 DB 的最大 eDTU 数一样大，每个数据库的最大和最小 eDTU 数就可能设置为任何列出的值 

** 弹性数据库共享池存储空间，因此数据库存储空间限制为小于池的剩余存储空间或每个数据库的最大存储空间

### <a name="premium-elastic-pool-limits"></a>高级弹性池限制
|  |  |
| --- |:---:|
| 每个池的最大 eDTU 数 |125 &nbsp;&nbsp;&nbsp; 250 &nbsp;&nbsp;&nbsp; 500 &nbsp;&nbsp;&nbsp; 1000 &nbsp;&nbsp;&nbsp; &nbsp;1500 |
| 每个池的最大存储空间 (GB)* |250 &nbsp;&nbsp;&nbsp; 500 &nbsp;&nbsp;&nbsp; 750 &nbsp;&nbsp;&nbsp;&nbsp; 750 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 750 |
| 每个池的数据库的最大数目 |50 |
| 每个池的最大内存中 OLTP 存储 (GB) |不适用 |
| 每个池的最大并发工作线程数 |&nbsp;&nbsp;200 &nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp; 2400 |
| 每个池的最大并发登录数 |&nbsp;&nbsp;200 &nbsp;&nbsp;&nbsp; 400 &nbsp;&nbsp;&nbsp; 800 &nbsp;&nbsp; 1600 &nbsp;&nbsp;&nbsp; 2400 |
| 每个池的最大并发会话数 |4800 &nbsp; 9600 &nbsp;19200 &nbsp;28800 &nbsp;&nbsp; 28800 |
| 每个数据库的最大 eDTU 数* |125, 250, 500, 1000 |
| 每个数据库的最小 eDTU 数* |0, 125, 250, 500, 1000 |
| 每个数据库的最大存储空间 (GB)** |500 |
| 时间点还原 |过去 35 天的任一时间点 |
| 灾难恢复 |活动异地复制 |
|  | |

* 只要所选的池 DTU 大小与每个 DB 的最大 eDTU 数一样大，每个数据库的最大和最小 eDTU 数就可能设置为任何列出的值 

** 弹性数据库共享池存储空间，因此数据库存储空间限制为小于池的剩余存储空间或每个数据库的最大存储空间



<!--HONumber=Nov16_HO2-->


