#  数据托管客户端使用说明

------

## 1. 简介
### 1.1数据托管客户端简介
本文档为二级标识数据托管客户端使用帮助文档。用于二级标识数据托管。应用名称为deposit-client。
  

### 1.2 编写目的
对数据客户端运行环境、软件配置进行说明，并提供数据托管客户端的使用方法。


## 2. 环境搭建
### 2.1 运行要求  
硬件环境：  
CPU: 2*4core 2.4G  
内存 >=8GB·  
  
软件环境：  
JDK 1.8及其以上
centos服务器

### 2.2 快速上手
对客户端使用方法进行简要说明。使用手册详见[二级标识数据托管客户端使用文档](./二级标识数据托管客户端使用文档.docx)。
#### 2.2.1 生成SM2密钥对
执行以下命令之后，会在console控制台输出sm2密钥对结果文件地址。  
```Java
java -jar deposit-client-mysql.jar sm2keygenerator
```
#### 2.2.2 默认配置方式执行
默认下，应用配置文件已集成在deposit-client-mysql.jar中，即解压后目录BOOT-INF/classes/config中。默认生效的配置文件为其中的application.yaml与application-production.yaml。由于其中有数据库信息和SFTP服务器和密钥信息配置，这些配置都是需要修改的。这些需要自定义修改的配置都在application-production.yaml中。

#### 2.2.3 外部配置文件方式执行
参考配置详解中的配置内容，也可以参照jar包内BOOT-INF/classes/config目录下的application-demo.yaml。创建自己使用的配置文件applicatin-demo.yaml，修改好之后
调用指令如下：
```Java
java -jar deposit-client.jar --spring.config.location=application-demo.yaml --escrow.client=true
#指定前缀
java -jar deposit-client.jar --spring.config.location=application-demo.yaml --escrow.client=true --escrow.prefix=88.100
```
#### 2.2.4 状态维护
每一次托管执行，都会在escrow_record_log表生成一条记录。
指令执行结束后，如果escrow_record_log表中增加了一条记录并且status字段=SUCCESS，则代表托管提交成功。不过，这个状态并不代表托管平台的处理结果，最终结果应以托管平台的通知为准。如托管平台处理失败，则需要根据托管平台的提示信息针对处理后重新提交。

   

