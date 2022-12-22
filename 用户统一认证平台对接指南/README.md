#  用户统一认证平台对接使用说明

------

## 1. 简介
### 1.1统一认证平台简介
工业互联网用户统一认证平台是一款易使用、易管理、高效率的用户认证综合平台。
这个系统通过对应用信息的管理来实现不同应用之间对同一用户的鉴权及认证，达到一个用户可登陆多个系统的目的，方便了多系统之间登陆的便捷性和易用性
  

### 1.2 编写目的
提供子系统接入相关接口说明、jar包和接入流程说明，使用户更容易、更便捷使用此产品。


## 2. 环境搭建
### 2.1 运行要求  
硬件环境：  
操作系统：win7及以上  
CPU: 2*4core 2.4G  
内存 >=8GB·  
  
软件环境：  
JDK 1.8及其以上  
ssoclient-1.0.2.jar  
spring-context.jar  
slf4j-api.jar  
javax.servlet-api.jar  
gson.jar  
hutool-all.jar    

### 2.2 快速上手
对接入流程进行简要说明，以java版为例子，详细接入说明见[java版-单点登录接入说明](./java版-单点登录接入说明.docx)。
#### 2.2.1 添加jar包
将ssoclien-1.0.2.jar添加到自己的工程中，jar包详见[ssoclient-1.0.2](./ssoclient-1.0.2.jar)。
#### 2.2.2 修改application.properties配置文件
在自己的application.properties配置文件中添加sso.server.url（sso服务器地址）、sso.client.system.code（系统接入码）、local.logout.suffix（本地服务登出后跳转的地址后缀）3个字段。
#### 2.2.3 本地启动应用服务
本地启动服务，在浏览器中输入应用的访问地址，会自动跳转到SSO认证中心（如下图所示）。
在此页面输入正确的用户名和密码后，会跳转至登录成功后的应用首页（即本地启动服务后在浏览器中输入的应用访问地址）。
#### 2.2.4 自定义登录登出逻辑
登录和登出成功以后可以通过实现 LoginSuccessHandler、onAuthenticationSuccess、 LogoutSuccessHandler接口来自定义登录登出逻辑。
## 3. 使用说明
### 3.1 用户信息同步API使用说明
统一认证平台接入用户信息相关接口和子系统向统一认证平台进行用户信息同步调用接口说明详见[统一认证平台接口说明](./统一认证平台接口说明.docx)。
   

