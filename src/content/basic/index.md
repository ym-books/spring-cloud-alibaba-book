# 架构基础

本架构中使用的基础框架列表：

>- [Spring Boot](#spring-boot)
>- [Spring MVC](#spring-mvc)
>- [Spring Security](#spring-security)
>- [Spring JPA](#spring-jpa)
>- [Mybatis](#mybatis)
>- [j2cache](#j2cache)
>- [sharding-jdbc](#sharding-jdbc)
>- [xxl-job](#xxl-job)

<a id="spring-boot"/>

## Spring Boot

大名鼎鼎，这里不做过多介绍！

<a id="spring-mvc"/>

## Spring MVC 

Rest接口框架。名声在外，不做过多介绍。

<a id="spring-security"/>

## Spring Security

在架构中作为安全基础框架。安全登录、安全授权、跨域设置、拦截恶心请求等等……

<a id="spring-jpa"/>

## Spring JPA

`Spring`全家桶中的`ORM`框架，实现的`Java JPA`规范。   

在本架构中的作用：               
- 面向对象维护关系数据表。
- 新增、更改表操作；简单的查询操作；与`Mybatis`组合使用

<a id="mybatis"/>

## Mybatis

数据库操作框架，只能算半个`ORM`框架，由于其灵活性，所以是事实上的国内很多企业采用的`标准`模式。但是这里，它将和`Spring JPA`搭配使用。

在本架构中作用：
- 复杂的查询，特别是连表查询的场景
- 对性能要求比较高的场景。可以对`SQL`优化。如：复杂查询、大数据量插入等

**_问题:_**_`JPA`和`Mybatis`事务管理器是否都统一交给`Spring`处理了吗？实际操作中是否出现事务问题，思考！_

<a id="j2cache"/>

## j2cache

分布式二级缓存框架。集成`Spring Cache`，作为本架构的缓存管理框架。

具体使用请参考: [分布式二级缓存框架`J2Cache`](j2cache.md)

<a id="sharding-jdbc"/>

## sharding-jdbc

数据库分库分表框架。具体集成方式请查阅：[集成`sharding-jdbc`](sharding-jdbc.md)

<a id="xxl-job"/>

## xxl-job

分布式调度系统。集体集成方式请查阅：[分布式调度`xxl-job`](xxl-job.md)
