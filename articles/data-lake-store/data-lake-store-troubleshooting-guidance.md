---
title: "Azure Data Lake Store 常见问题 | Microsoft 文档"
description: "有关排查或缓解 Azure Data Lake Store 问题的指导"
services: data-lake-store
documentationcenter: 
author: nitinme
manager: jhubbard
editor: cgronlun
ms.assetid: bf7fd555-3e30-43ce-b28c-c3ad0a241fdb
ms.service: data-lake-store
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: big-data
ms.date: 11/02/2016
ms.author: nitinme
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: 84d644e07036f511e685b0fd020cdf8c310fd969


---
# <a name="frequently-asked-questions-for-azure-data-lake-store"></a>Azure Data Lake Store 常见问题
本文提供有关 Azure Data Lake Store 的常见问题。

## <a name="how-do-i-handle-disaster-recovery-and-data-corruption-for-my-azure-data-lake-store-account"></a>如何处理 Azure Data Lake Store 帐户的灾难恢复和数据损坏？
Azure Data Lake Store 帐户中的数据可通过自动化副本，弹性应对区域中的暂时性硬件故障。 这可以确保持久性和高可用性，满足 Azure Data Lake Store SLA。 下面是有关如何进一步保护数据，防范极其少见的全区域服务中断或意外删除行为的一些指导。

### <a name="disaster-recovery-guidance"></a>灾难恢复指南
每个客户都应准备好自己的灾难恢复计划，这很重要。 制定灾难恢复计划时，请参阅以下 Azure 文档。 下面是可以帮助自行创建计划的一些资源。

* [Azure 应用程序的灾难恢复和高可用性](../resiliency/resiliency-disaster-recovery-high-availability-azure-applications.md)
* [Azure 复原技术指南](../resiliency/resiliency-technical-guidance.md)

#### <a name="best-practices"></a>最佳实践
我们建议按照与灾难恢复计划需求相符的频率，将关键数据复制到另一个区域中的另一个 Data Lake Store 帐户。 可以使用多种方法复制数据，包括 [ADLCopy](data-lake-store-copy-data-azure-storage-blob.md)、[Azure PowerShell](data-lake-store-get-started-powershell.md) 或 [Azure 数据工厂](../data-factory/data-factory-azure-datalake-connector.md)。 Azure 数据工厂是一个非常有用的服务，可以周期性地创建和部署数据移动管道。

如果发生区域性的服务中断，你可以在数据所复制到的区域中访问数据。可以监视 [Azure 服务运行状况仪表板](https://azure.microsoft.com/status/)，确定全球范围内的 Azure 服务状态。

### <a name="data-corruption-or-accidental-deletion-recovery-guidance"></a>数据损坏或意外删除恢复指导
尽管 Azure Data Lake Store 通过自动化副本提供数据复原能力，但这不能避免应用程序（或开发人员/用户）损坏数据或意外删除数据。

#### <a name="best-practices"></a>最佳实践
若要防止意外删除，我们建议首先使用 [Data Lake Store 安全功能](data-lake-store-security-overview.md)为 Data Lake Store 帐户设置适当的访问策略。 此外，我们建议在另一个 Data Lake Store 帐户、文件夹或 Azure 订阅中，定期使用 [ADLCopy](data-lake-store-copy-data-azure-storage-blob.md)、[Azure PowerShell](data-lake-store-get-started-powershell.md) 或 [Azure 数据工厂](../data-factory/data-factory-azure-datalake-connector.md)创建关键数据的副本。  发生数据损坏或删除事件时，可以使用这些副本来恢复数据。 Azure 数据工厂是一个非常有用的服务，可以周期性地创建和部署数据移动管道。

组织还可针对 Azure Data Lake Store 帐户启用[诊断日志记录](data-lake-store-diagnostic-logs.md)来收集数据访问审核跟踪，提供有关谁删除或更新了文件的信息。

## <a name="next-steps"></a>后续步骤
* [Azure Data Lake Store 入门](data-lake-store-get-started-portal.md)
* [保护 Data Lake Store 中的数据](data-lake-store-secure-data.md)




<!--HONumber=Nov16_HO2-->


