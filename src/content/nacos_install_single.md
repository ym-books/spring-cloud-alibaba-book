## 单机部署Nacos

这里介绍两种安装方式，一种是直接下载安装包执行，另外一种是docker方式。

## 本机安装

本机部署你要首先要获取安装包，Nacos是java开发的，你可以下载源码编译获取，另外一种直接下载已经编译好的安装包。

### 从github上下载源码方式

这首先要求你已经安装好java编译环境。这里不做介绍。

```shell
git clone https://github.com/alibaba/nacos.git
cd nacos/
mvn -Prelease-nacos -Dmaven.test.skip=true clean install -U  
ls -al distribution/target/

// change the $version to your actual path
cd distribution/target/nacos-server-$version/nacos/bin
```

### 下载编译好安装包方式

您可以从 [最新稳定版本](https://github.com/alibaba/nacos/releases) 下载 nacos-server-$version.zip 包。



