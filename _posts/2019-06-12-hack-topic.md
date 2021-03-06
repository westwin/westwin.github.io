---
layout: post
title: "Identity Hub"
permalink: /idp-hub/
categories: IDaaS
date: "2019-06-12 21:16:21 +0800"
---

* TOC
{:toc}
Identity Hub

## 介绍

Identity Hub是说, 把多种第三方认证源聚合到一起，形成一个**同时可以支持多个**认证源的超级认证源, 即Identity Hub

并且，用户在登录的时候可以自由选择使用哪个认证源来做登录.

Identity Hub作为一个承上启下的桥梁, 上可以对接多个认证源，下可以对接多个第三方SP. Identity Hub通过IDP的协议翻译和路由，从而达到
第三方SP可以同时使用不同的认证源单点登录的功能.

## 目标

从技术上讲，第三方认证源主要包括两种形式:

* 第三方认证源有自己的登录页面: 也就是说登录的时候需要跳转到第三方认证源的登录页面，登录成功之后再跳转回来(比如基于OAuth2协议的各种认证源)
* 第三方认证源没有自己的登录页面: 企业内的AD

这次hack大会，我们将会根据实际的开发进度，按照如下优先级来实现一些大目标，以及小目标, 每个小目标都是一个亮点功能.

有**两个大目标, 每个大目标又会有一些小目标(亮点功能)**. 如下:

1. 大目标: 用企业微信，通过扫码的方式来登录Yufu-Portal. 参见[集成文档](https://work.weixin.qq.com/api/doc#90000/90135/90988)
    * 亮点1: JIT, zhangsan用企业微信登录Yufu-Portal成功后, zhangsan的个人信息被存储(或更新)到Yufu-UD中
    * 亮点2: 权限映射, 企业微信的管理员->Yufu的管理员, 企业微信的普通用户->Yufu的普通用户
    * 亮点3： 给企业微信的登录额外加上Yufu-MFA(给没有MFA功能的认证源添加上Yufu-MFA功能)

2. 大目标: 用GitHub来登录Yufu-Portal, 参见[集成文档](https://developer.github.com/apps/building-oauth-apps/authorizing-oauth-apps/)
    * 亮点1: 第三方SP发起SP Initiated SSO可以指定使用GitHub来登录

另: 上面俩大目标都有一个共同的亮点目标: 给没有MFA功能的认证源添加上Yufu-MFA功能

如果时间允许的话，还可以再来一个大目标:

通过Agent用企业内的LDAP来登录Yufu-Portal(噱头:打通内网IDP和SaaS IDP), 这个的亮点在于，不同于现在已经实现的Agent以及STS认证源，新的Agent会更安全: 不需要在企业防火墙内开inbound端口

技术改造点:

1. 登录页面要能够展现多个登录认证源
    * 登录页面要集成企业微信的扫码登录的SDK
2. Admin页面要能够添加多个认证源，并做相应的配置
3. 服务端需要集成企业微信/GitHub的登录流程
4. MFA改造 ?

## 制度

1. 不建议熬夜，大家早点回去
   * 开发最好当天晚上完成所有开发任务
   * 第二天大家早上早点来, 9:30集合
2. 演示环境直接用开发本地的环境(前端+后端)
3. 第二天配合Demo的人，改进PPT以及给Demo的人讲解功能和使用细节

## 分工

1. 宣讲Demo的PPT准备: 要求界面美观，必须得体现团队协作
2. 前后端开发
3. 界面设计
4. 后勤
