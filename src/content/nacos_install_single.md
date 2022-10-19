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

下载后解压：
```shell
unzip nacos-server-$version.zip 或者 tar -xvf nacos-server-$version.tar.gz
cd nacos/bin
```

### 启动服务

*<font size=2 color=#FF000>注：Nacos的运行需要以至少2C 4g 60g的机器配置下运行。</font>*

在`bin`目录中，找到对应系统平台的脚本，启动。下面在`Centos`平台启动：
```shell
sh startup.sh -m standalone
```
`standalone`代表单机模式启动，非集群模式启动。

启动结果如下：
```shell
[root@server-dev-01 bin]# sh startup.sh -m standalone
/server/java/jdk8/bin/java -Djava.ext.dirs=/server/java/jdk8/jre/lib/ext:/server/java/jdk8/lib/ext  -Xms512m -Xmx512m -Xmn256m -Dnacos.standalone=true -Dnacos.member.list= -Xloggc:/server/nacos-server/nacos/logs/nacos_gc.log -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=10 -XX:GCLogFileSize=100M -Dloader.path=/server/nacos-server/nacos/plugins/health,/server/nacos-server/nacos/plugins/cmdb,/server/nacos-server/nacos/plugins/selector -Dnacos.home=/server/nacos-server/nacos -jar /server/nacos-server/nacos/target/nacos-server.jar  --spring.config.additional-location=file:/server/nacos-server/nacos/conf/ --logging.config=/server/nacos-server/nacos/conf/nacos-logback.xml --server.max-http-header-size=524288
nacos is starting with standalone
nacos is starting, you can check the /server/nacos-server/nacos/logs/start.out
```

### 登录控制台

浏览器输入网址：`http://ip:port/nacos` 如：`http://192.168.0.106:8848/nacos`    

默认登录账号密码：`nacos    nacos`

### 停止服务

在`bin`目录中运行相关系统平台脚本即可。如下：
```shell
sh shutdown.sh
```

### 设置开机自启动

把启动`nacos`命令设成`linux`自启服务即可。

## Docker运行Nacos服务

参考：https://github.com/nacos-group/nacos-docker

