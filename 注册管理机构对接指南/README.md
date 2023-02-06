#  BMS-EPP-CLIENT使用说明书

------

## 1. 简介
### 1.1BMS-EPP-CLIENT简介
BMS-EPP是中国信通院研发的基于EPP协议的服务系统,为方便用户使用，提供了BMS-EPP-CLIENT（BMS-EPP客户端），以方便EPP客户端用户的接入BMS系统。
  

### 1.2 编写目的
文档主要bms-epp-api接口进行详细说明，并提供相应的响应示例。便于其他系统的快速接入。

### 1.3 名词说明
<table>
        <tr>
            <th width="200">术语</th>
            <th width="500">解释</th>
        </tr>
        <tr>
            <td>EPP系统</td>
            <td>遵循EPP协议的国家顶级节点服务系统</td>
        </tr>
        <tr>
            <td>BMS系统</td>
            <td>标识业务管理系统</td>
        </tr>
</table>

## 2. 环境搭建
### 2.1 运行要求  
硬件环境：  
操作系统：win7及以上  
CPU: 2*4core 2.4G  
内存 >=8GB·  
  
软件环境：  
JDK 1.8及其以上
bms-epp-client-2.1.1.jar  
commons-io-1.3.2.jar  
commons-lang3-3.5.jar  
commons-logging-1.2.jar  
commons-pool2-2.4.3.jar  
dom4j-2.1.1.jar  
jcl-over-slf4j-1.7.25.jar  
jul-to-slf4j-1.7.25.jar  
log4j-over-slf4j-1.7.25.jar  
logback-classic-1.1.11.jar  
logback-core-1.1.11.jar  
okhttp-3.6.0.jar  
okio-1.11.0.jar  
slf4j-api-1.7.25.jar  
spring-aop-4.3.18.RELEASE.jar  
spring-beans-4.3.18.RELEASE.jar  
spring-context-4.3.18.RELEASE.jar  
spring-context-support-4.3.18.RELEASE.jar  
spring-core-4.3.18.RELEASE.jar  
spring-expression-4.3.18.RELEASE.jar  
spring-test-4.3.18.RELEASE.jar  
spring-web-4.3.18.RELEASE.jar  

### 2.2 快速上手
#### 2.2.1 前置条件
（1）用户需要在BMS系统注册一个账号。  
（2）等待管理员审核通过之后，会分配给对应的二级节点一个或者多个二级前缀。  
（3）审核通过后,用户登录国家顶级节点管理系统,通过点击“标识管理”-> “节点标识”->“节点信息”，
  找到安全信息之后在弹出的更新密钥对话框中生成私钥，用户保存自己的私钥，后面会用到，并点击保存按钮。  
（4）保存私钥和appId以及前缀信息（重要）  
（5）在前缀配置详情中用户需要配置idis的注册和解析端口。(重要) 
#### 2.2.2 系统配置
（1）在项目的application.properties文件中配置，其中:appUrl对应的是国家顶级节点epp服务的地址和端口号，shrPrefix对应的是国家顶级节点分配的二级前缀，appId 是用户保存的appId    
```Java
teleinfo.eppClient.appUrl=http://172.xx.x.xx:xxxx/
teleinfo.eppClient.shrPrefix=88.104
teleinfo.eppClient.appId = 5K4gCPDxRoWqJX3vtfdXDZh4WTgNnQjHsH5oj5KZYiAf
```
（2）使用密钥为参数，在容器内注册Bean(cn.teleinfo.bms.epp.client.EppHttpClient)  
```Java
@Bean
public EppHttpClient eppClient() throws EppClientException {
    return new EppClient(appPrivKey);
}
```
## 3. 使用说明
### 3.1 EPP-API
EPP接口的常用方法和使用示例详见[BMS-EPP-CLIENT使用说明书](./BMS-EPP-CLIENT使用说明书.doc)

### 3.2 客户端测试工程
客户端测试工程源码详见[epp-client-test](./epp-client-test.rar)
   

