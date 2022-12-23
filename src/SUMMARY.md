# Summary

[架构介绍](content/main.md)

-------------------------------------------------

- [架构基础组件](content/basic/index.md)
  - [分布式二级缓存框架`J2Cache`](content/basic/j2cache.md)
  - [集成`sharding-jdbc`](content/basic/sharding-jdbc.md)
  - [分布式调度`xxl-job`](content/basic/xxl-job.md)
  - [数据库增量数据同步`canal`](content/basic/canal.md)
- [使用中间件](content/mid/index.md)

--------------------------------------------------------------------

- [Nacos注册与配置管理中心](content/nacos.md)
  - [Nacos的安装部署](content/nacos_install.md)
    - [单机模式部署](content/nacos_install_single.md)
    - [集群模式部署](content/nacos_install_multi.md)
    - [定制配置文件](content/nacos_yaml.md)
  - [Nacos在Spring Cloud中使用](content/nacos_spring_cloud.md)
    - [作为服务治理](content/nacos_spring_cloud_register.md)
    - [作为配置管理中心](content/nacos_spring_cloud_config.md)
  - [使用问题及面试](content/nacos_issue.md)
- [网关设计](content/gateway.md)
  - [流量治理-Sentinel](content/sentinel.md)
- [负载均衡](content/load_balancing.md)
- [服务容错](content/service_fault.md)
  - [熔断降级](content/fuse.md)
- [链路追踪](content/sleuth.md)
- [服务监控](content/monitor.md)
- [日志收集可视化EKL](content/ekl.md)
- [消息驱动](content/stream.md)
- [Seata分布式事务](content/seata.md)

--------------------------------------------------------------

- [统一认证中心](content/auth.md)
  - [身份认证](content/auth_1.md)
  - [权限设计](content/auth_2.md)
- [单点登录SSO](content/sso.md)
- [分布式锁设计](content/dlock.md)
- [Mysql读写分离策略](content/mysql_master_slave.md)
- [Mysql分库分表策略](content/mysql_sub.md)
- [sass实现](content/sass.md)
- [API文档管理](content/api_manage.md)
- [API版本迭代](content/api_version.md)

---------------------------------------------

- [应用系统安全](content/system_security.md)
  - [预防XSS攻击](content/security_xss.md)
  - [预防SQL注入](content/security_sql.md)
  - [接口数据加密传输](content/security_api.md)
  - [htpps](content/security_https.md)
- [代码质量管理](content/code_good.md)
  - [代码规范-CheckStyle](content/code_checkstyle.md)
  - [代码质量检测工具-Sonar](content/code_sonar.md)
  - [代码审查`eng-practices`](content/code_review.md)
- [性能测试](content/test_pfr.md)
  - [基准测试-JMH](content/jmh.md)
  - [性能监控调试-Arthas](content/arthas.md)
  - [压力测试-jmeter](content/jmeter.md)
  - [单链路压测](content/test_pfr_single.md)
  - [全链路压测](content/test_pfr_full.md)
- [部署运维](content/dev_ops.md)
  - [开发环境搭建](content/dev_ops_dev.md)
  - [构建运行-Docker](content/dev_ops_docker.md)
  - [持续交付-Jenkins](content/dev_ops_jenkins.md)
  - [全链路灰度发布](content/dev_ops_hd.md)
  - [金丝雀发布](content/dev_ops_jsq.md)
