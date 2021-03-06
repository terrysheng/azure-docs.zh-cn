---
title: "使用 Azure Resource Manager 和 Azure 门户创建具有站点到站点 VPN 连接的虚拟网络 | Microsoft Docs"
description: "如何使用 Resource Manager 部署模型创建 VNet 并使用 S2S VPN 网关连接将其连接到你的本地网络。"
services: vpn-gateway
documentationcenter: na
author: cherylmc
manager: carmonm
editor: 
tags: azure-resource-manager
ms.assetid: 827a4db7-7fa5-4eaf-b7e1-e1518c51c815
ms.service: vpn-gateway
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 10/14/2016
ms.author: cherylmc
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 95268d0197f9c79b1650165056cbf4b3e79f12ec


---
# <a name="create-a-vnet-with-a-sitetosite-connection-using-the-azure-portal"></a>使用 Azure 门户创建具有站点到站点连接的 VNet
> [!div class="op_single_selector"]
> * [Resource Manager - Azure 门户](vpn-gateway-howto-site-to-site-resource-manager-portal.md)
> * [Resource Manager - PowerShell](vpn-gateway-create-site-to-site-rm-powershell.md)
> * [经典 - 经典门户](vpn-gateway-site-to-site-create.md)
> 
> 

本文逐步讲解如何使用 Azure Resource Manager 部署模型和 Azure 门户创建一个虚拟网络和一个连接到本地网络的站点到站点 VPN 网关连接。 站点到站点连接可以用于跨界和混合配置。

![图表](./media/vpn-gateway-howto-site-to-site-resource-manager-portal/s2srmportal.png)

### <a name="deployment-models-and-methods-for-sitetosite-connections"></a>用于站点到站点连接的部署模型和方法
[!INCLUDE [deployment models](../../includes/vpn-gateway-deployment-models-include.md)]

下表显示了站点到站点配置当前可用的部署模型和方法。 当有配置步骤相关的文章发布时，我们会直接从此表格链接到该文章。

[!INCLUDE [site-to-site table](../../includes/vpn-gateway-table-site-to-site-include.md)]

#### <a name="additional-configurations"></a>其他配置
如果你想要将多个 VNet 连接到一起，但又不想创建连接到本地位置的连接，则请参阅 [配置 VNet 到 VNet 连接](vpn-gateway-vnet-vnet-rm-ps.md)。 如果想要向已具有连接的 VNet 添加站点到站点连接，请参阅[使用现有 VPN 网关连接将 S2S 连接添加到 VNet](vpn-gateway-howto-multi-site-to-site-resource-manager-portal.md)。

## <a name="before-you-begin"></a>开始之前
在开始配置之前，请确认你具有以下各项：

* 一台兼容的 VPN 设备和能够对其进行配置的人员。 请参阅 [关于 VPN 设备](vpn-gateway-about-vpn-devices.md)。 如果不熟悉 VPN 设备的配置，或者不熟悉本地网络配置中的 IP 地址范围，则需咨询能够为你提供此类详细信息的人员。
* 一个用于 VPN 设备的面向外部的公共 IP 地址。 此 IP 地址不得位于 NAT 之后。
* Azure 订阅。 如果你还没有 Azure 订阅，可以激活 [MSDN 订户权益](http://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)或注册获取[免费帐户](http://azure.microsoft.com/pricing/free-trial/)。

### <a name="a-namevaluesasample-configuration-values-for-this-exercise"></a><a name="values"></a>此练习的示例配置值
练习这些步骤时，可以使用示例配置值：

* **VNet 名称：**TestVNet1
* **地址空间：**10.11.0.0/16 和 10.12.0.0/16
* **子网：**
  * FrontEnd：10.11.0.0/24
  * BackEnd：10.12.0.0/24
  * GatewaySubnet：10.12.255.0/27
* **资源组：**TestRG1
* **位置：**美国东部
* **DNS 服务器：**8.8.8.8
* **网关名称：**VNet1GW
* **公共 IP：**VNet1GWIP
* **VPN 类型：**基于路由
* **连接类型：**站点到站点 (IPsec)
* **网关类型：**VPN
* **局域网网关名称：**Site2
* **连接名称：**VNet1toSite2

## <a name="a-namecreatvneta1-create-a-virtual-network"></a><a name="CreatVNet"></a>1.创建虚拟网络
如果已有一个 VNet，请检查其设置是否与 VPN 网关设计兼容。 请特别注意任何可能与其他网络重叠的子网。 如果有重叠子网，连接将无法正常工作。 如果 VNet 配置了正确的设置，则可以开始执行 [指定 DNS 服务器](#dns) 部分中的步骤。

### <a name="to-create-a-virtual-network"></a>创建虚拟网络
[!INCLUDE [vpn-gateway-basic-vnet-rm-portal](../../includes/vpn-gateway-basic-vnet-rm-portal-include.md)]

## <a name="a-namesubnetsa2-add-additional-address-space-and-subnets"></a><a name="subnets"></a>2.添加其他地址空间和子网
可以将其他地址空间和子网添加到已创建的 VNet。

[!INCLUDE [vpn-gateway-additional-address-space](../../includes/vpn-gateway-additional-address-space-include.md)]

## <a name="a-namednsa3-specify-a-dns-server"></a><a name="dns"></a>3.指定 DNS 服务器
### <a name="to-specify-a-dns-server"></a>指定 DNS 服务器
[!INCLUDE [vpn-gateway-add-dns-rm-portal](../../includes/vpn-gateway-add-dns-rm-portal-include.md)]

## <a name="a-namegatewaysubneta4-create-a-gateway-subnet"></a><a name="gatewaysubnet"></a>4.创建网关子网
将虚拟网络连接到网关之前，必须先创建要连接的虚拟网络的网关子网。 在可能的情况下，最好是使用 CIDR 块 /28 或 /27 创建网关子网，以便提供足够的 IP 地址，满足将来的其他配置要求。

如果你在练习创建此配置，请在创建网关子网时引用这些 [值](#values) 。

### <a name="to-create-a-gateway-subnet"></a>创建网关子网
[!INCLUDE [vpn-gateway-add-gwsubnet-rm-portal](../../includes/vpn-gateway-add-gwsubnet-rm-portal-include.md)]

## <a name="a-namevnetgatewaya5-create-a-virtual-network-gateway"></a><a name="VNetGateway"></a>5.创建虚拟网络网关
如果正在练习创建此配置，可以参考[示例配置值](#values)。

### <a name="to-create-a-virtual-network-gateway"></a>创建虚拟网络网关
[!INCLUDE [vpn-gateway-add-gw-rm-portal](../../includes/vpn-gateway-add-gw-rm-portal-include.md)]

## <a name="a-namelocalnetworkgatewaya6-create-a-local-network-gateway"></a><a name="LocalNetworkGateway"></a>6.创建本地网络网关
“本地网络网关”是指本地位置。 为本地网络网关命名，Azure 可通过该名称引用该网关。 

如果正在练习创建此配置，可以参考[示例配置值](#values)。

### <a name="to-create-a-local-network-gateway"></a>创建局域网网关
[!INCLUDE [vpn-gateway-add-lng-rm-portal](../../includes/vpn-gateway-add-lng-rm-portal-include.md)]

## <a name="a-namevpndevicea7-configure-your-vpn-device"></a><a name="VPNDevice"></a>7.配置 VPN 设备
[!INCLUDE [vpn-gateway-configure-vpn-device-rm](../../includes/vpn-gateway-configure-vpn-device-rm-include.md)]

## <a name="a-namecreateconnectiona8-create-a-sitetosite-vpn-connection"></a><a name="CreateConnection"></a>8.创建站点到站点 VPN 连接
在虚拟网络网关和 VPN 设备之间创建站点到站点 VPN 连接。 请务必替换为你自己的值。 共享密钥必须与你用于 VPN 设备配置的值匹配。 

在开始本部分之前，请确认虚拟网络网关与局域网网关已完成创建。 如果你在练习创建此配置，请在创建连接时引用这些 [值](#values) 。

### <a name="to-create-the-vpn-connection"></a>创建 VPN 连接
[!INCLUDE [vpn-gateway-add-site-to-site-connection-rm-portal](../../includes/vpn-gateway-add-site-to-site-connection-rm-portal-include.md)]

## <a name="a-nameverifyconnectiona9-verify-the-vpn-connection"></a><a name="VerifyConnection"></a>9.验证 VPN 连接
你可以在门户中或使用 PowerShell 验证 VPN 连接。

[!INCLUDE [vpn-gateway-verify-connection-rm](../../includes/vpn-gateway-verify-connection-rm-include.md)]

## <a name="next-steps"></a>后续步骤
* 连接完成后，即可将虚拟机添加到虚拟网络。 有关详细信息，请参阅虚拟机 [学习路径](https://azure.microsoft.com/documentation/learning-paths/virtual-machines) 。
* 有关 BGP 的信息，请参阅 [BGP 概述](vpn-gateway-bgp-overview.md)和[如何配置 BGP](vpn-gateway-bgp-resource-manager-ps.md)。




<!--HONumber=Nov16_HO2-->


