# Walrus服务实例部署文档

> **免责声明：**
>
> 本服务由第三方提供，我们尽力确保其安全性、准确性和可靠性，但无法保证其完全免于故障、中断、错误或攻击。因此，本公司在此声明：对于本服务的内容、准确性、完整性、可靠性、适用性以及及时性不作任何陈述、保证或承诺，不对您使用本服务所产生的任何直接或间接的损失或损害承担任何责任；对于您通过本服务访问的第三方网站、应用程序、产品和服务，不对其内容、准确性、完整性、可靠性、适用性以及及时性承担任何责任，您应自行承担使用后果产生的风险和责任；对于因您使用本服务而产生的任何损失、损害，包括但不限于直接损失、间接损失、利润损失、商誉损失、数据损失或其他经济损失，不承担任何责任，即使本公司事先已被告知可能存在此类损失或损害的可能性；我们保留不时修改本声明的权利，因此请您在使用本服务前定期检查本声明。如果您对本声明或本服务存在任何问题或疑问，请联系我们。

## 概述
Walrus应用管理平台是一个用于管理和部署应用程序的平台。它提供了一个集中化的管理界面，使用户能够轻松地管理应用的生命周期，包括创建、配置、部署、监控和维护应用。Walrus还提供了一些高级功能，如应用版本控制、自动化部署和弹性扩展，以帮助用户更好地管理和运行他们的应用。

本文向您介绍如何开通计算巢上的Walrus，以及部署流程和使用说明。

## 计费说明

Walrus在计算巢上的费用主要涉及：

- 所选 vCPU 与内存规格
- 系统盘类型及容量
- 公网带宽

## 部署架构

![](arch.png)

## RAM账号所需权限

Walrus服务需要对ECS、VPC等资源进行访问和创建操作，若您使用RAM用户创建服务实例，需要在创建服务实例前，对使用的RAM用户的账号添加相应资源的权限。添加RAM权限的详细操作，请参见 [RAM 用户授权](https://help.aliyun.com/document_detail/121945.html)
。所需权限如下表所示。

| 权限策略名称                    | 备注                                      |
| ------------------------------- | ----------------------------------------- |
| AliyunECSFullAccess             | 管理云服务器服务（ECS）的权限             |
| AliyunVPCReadOnlyAccess         | 只读访问专有网络（VPC）的权限             |
| AliyunROSFullAccess             | 管理资源编排服务（ROS）的权限             |
| AliyunComputeNestUserFullAccess | 管理计算巢服务（ComputeNest）的用户侧权限 |

## 部署流程

### 部署步骤

单击[部署链接](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-ff8fc794c05042968b39)，进入服务实例部署界面，根据界面提示，填写参数完成部署。

![](params.png)

### 部署参数说明

您在创建服务实例的过程中，需要配置服务实例信息。下文介绍Walrus服务实例输入参数的详细信息。

| 参数组      | 参数项        | 示例                   | 说明                           |
|----------|------------|----------------------|------------------------------|
| 服务实例名称   |            | walrus-test          | 实例的名称                        |
| 地域       |            | cn-hangzhou          | 选中服务实例的地域，建议就近选中，以获取更好的网络延时。 |
| ECS 实例配置 | 实例类型       | ecs.g6.large         | ECS实例规格，可以根据实际需求选择。          |
| 可用区配置    | 可用区        | cn-hangzhou-j        | 地域下的不同可用区域。                  |
| 网络配置     | 是否新建VPC    | true                 |                              |
| 网络配置    | 专有网络IPv4网段 | 192.168.0.0/16       |                              |
| 网络配置    | 交换机子网网段    | 192.168.1.0/24       |                              |
| 网络配置    | VPC实例ID    | vpc-\*\*\*\*\*\*\*\* |                              |
| 网络配置    | 交换机实例ID    | vsw-\*\*\*\*\*\*\*\* | |                            

### 验证结果

1. 查看服务实例。服务实例创建成功后，部署时间大约需要5分钟。部署完成后，页面上可以看到对应的服务实例。

![](r1.png)
2. 通过服务实例访问Walrus。进入到对应的服务实例后，可以在页面获取到Walrus登录页面的地址，以及admin账号的初始密码。

![](r2.png)

![](r3.png)
3. 登录成功后，进行Walrus的配置和使用。![](r4.png)

## 帮助文档

请访问[Walrus用户指南](https://github.com/seal-io/walrus)了解如何使用。