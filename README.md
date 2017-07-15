# Spring Cloud Ribbon 笔记

## 简介
> Spring Cloud Ribbon 是一个基于 HTTP 和 TCP 的客户端负载均衡工具，基于 NetFlix Ribbon 实现。可以轻松实现将面向服务的 REST 模版请求
自动转换为客户端负载均衡的服务调用。

## 负载均衡
> 负载均衡分服务端负载均衡和客户端负载均衡。服务端负载均衡又分硬件负载均衡（如F5）和软件负载均衡（如nginx）；在客户端负载均衡中，所有客户端
节点都维护着自己要访问的服务端清单，而这些清单来自服务注册中心。

## 使用 Spring Cloud Ribbon 步骤
* 引入 spring-cloud-starter-eureka 和 spring-cloud-starter-ribbon 依赖，注意 ribbon 是根据 eureka 来获取服务清单的，勿忘 eureka
* Spring Boot 启动类上加 @EnableDiscoveryClient 注解激活 Eureka 中的 DiscoveryClient 实现
* Spring Boot 启动类中加被 @LoadBalanced（开启客户端负载均衡） 注解修饰过的 RestTemplate 对象来实现面向服务的接口调用
* 在相关业务中通过 restTemplate 对象调用远程服务

## RestTemplate 详解
* getForEntity() 函数
* getForObject() 函数
* postForEntity() 函数
* postForObject() 函数
* postForLocation() 函数，以 POST 请求提交资源，并返回新资源的URL
* put() 函数
* delete() 函数

## 参数配置
* 全局配置
> 如配置连接超时时间：ribbon.ConnectTimeout=250
* 指定客户端的配置方式
> 如为客户端指定具体的实例清单(加入不用eureka)：hello-service.ribbon.listOfServers=localhost:8001,localhost:8002,localhost:8003
