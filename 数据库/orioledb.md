# orioledb

云原生存储引擎，并解决PostgreSQL的一些问题。
OrioleDB是一个新的PostgreSQL存储引擎，为数据库容量、功能和性能带来现代化的方法。

OrioleDB包含一个扩展，创新的表访问方法框架和其他标准Postgres扩展接口。
通过扩展和增强当前的表访问方法，OrioleDB为未来更强大的存储模型打开了大门，这些模型针对云和现代硬件架构进行了优化。

OrioleDB目前在标准PostgreSQL许可下发布。

1. 现代化硬件设计，OrioleDB设计避免了包含数十个和数百个CPU内核的现代服务器上遗留的CPU瓶颈，提供了对现代存储技术(
   如SSD和NVRAM)的优化使用
2. 减少维护需求，OrioleDB实现了撤销日志和页面合并的概念，从而消除了对专用垃圾收集进程的需求。此外，OrioleDB实现了默认的64位事务标识符，从而消除了众所周知的令人痛苦的封装问题。
3. 分布式设计，OrioleDB实现了支持并行的行级预写日志。该日志架构针对基于raft共识的复制进行了优化，允许实现双活multimaster。

github: [https://github.com/orioledb/orioledb](https://github.com/orioledb/orioledb)