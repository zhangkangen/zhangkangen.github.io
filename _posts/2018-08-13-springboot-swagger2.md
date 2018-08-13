---
layout: post
title: springboot 开发项目中集成 swagger2
date: 2018-08-13 19:33:20
categories:
- springboot
tags:
- java
- springboot
description: springboot 开发项目中集成 swagger2
---
#springboot 开发项目中集成 swagger2
##集成
pom.xml 中引入以下库
```
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger2</artifactId>
        <version>2.7.0</version>
    </dependency>
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger-ui</artifactId>
        <version>2.7.0</version>
    </dependency>
```
springboot 项目启动类加上 **@EnableSwagger2** 注解.

##常用的注解
1. @ApiIgnore
2. @Api
3. @ApiOperation
4. 

##注意
- springboot 中如果使用了自定义拦截器,这需要在拦截器中排出一下链接: "/swagger-resources/**"
- springboot 集成 shiro 框架时,需要放行以下链接
```
    filterChainDefainitionMap.put("/swagger-ui.html", "anon");
    filterChainDefainitionMap.put("/swagger-resources", "anon");
    filterChainDefainitionMap.put("/v2/api-docs", "anon");
    filterChainDefainitionMap.put("/webjars/springfox-swagger-ui/**", "anon");
```
- 集成 swagger2 会导致项目启动变慢, springboot 多分支开发时, 线上分支可以选择停用, 来减少项目发布时间.

