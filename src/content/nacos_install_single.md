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

查看启动日志：
```shell
tail -f /server/nacos-server/nacos/logs/start.out
```

### 登录控制台

浏览器输入网址：`http://ip:port/nacos` 如：`http://192.168.0.106:8848/nacos`   

从版本2.2.1开始，需要自己进行开启鉴权配置，否则不需要登录。这在公共网络下会造成配置数据泄露。`nacos`自带了一个简单的鉴权插件，有更高数据安全要求的需要自己实现鉴权插件。  
[鉴权参考](https://nacos.io/zh-cn/docs/v2/guide/user/auth.html)

下面修改配置，需要登录才能进入首页。  
编辑配置文件`application.properties`，更改一下配置：  

修改之前：
```properties
### If turn on auth system:
nacos.core.auth.enabled=false
```
修改之后：
```properties
### If turn on auth system:
nacos.core.auth.system.type=nacos
nacos.core.auth.enabled=true
```

自定义密钥：  
开启鉴权之后，自定义用于生成JWT令牌的密钥，application.properties中的配置信息为：
```properties
### The default token (Base64 String):
nacos.core.auth.plugin.nacos.token.secret.key=
```
用不少于32位的Base64字符串作为key，如下：
```properties
nacos.core.auth.plugin.nacos.token.secret.key=VGhpc0lzTXlDdXN0b21TZWNyZXRLZXkwMTIzNDU2Nzg=
```

接入nacos服务账号，密码配置：
```properties
### The two properties is the white list for auth and used by identity the request from other server.
nacos.core.auth.server.identity.key=admin
nacos.core.auth.server.identity.value=admin123
```

修改配置文件立马生效的，不需要重启nacos服务。


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



