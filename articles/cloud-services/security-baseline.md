---
title: Azure 云服务的 azure 安全基线
description: Azure 云服务安全基线为实现 Azure 安全基准中指定的安全建议提供过程指南和资源。
author: msmbaldwin
ms.service: cloud-services
ms.topic: conceptual
ms.date: 11/02/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 2c088bce3bc763bf813298ef91b4e07f0b20c50c
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2020
ms.locfileid: "93328672"
---
# <a name="azure-security-baseline-for-azure-cloud-services"></a>Azure 云服务的 azure 安全基线

此安全基线将 [Azure 安全基准版本 1.0](../security/benchmarks/overview-v1.md) 中的指南应用到 Microsoft Azure 云服务。 Azure 安全基准提供有关如何在 Azure 上保护云解决方案的建议。
内容由 Azure 安全基准定义的 **安全控制** 和适用于云服务的相关指南进行分组。 排除了不适用于云服务的 **控件** 。

 
若要查看云服务如何完全映射到 Azure 安全基准，请参阅 [完整的云服务安全基线映射文件](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)。

## <a name="network-security"></a>网络安全性

[有关详细信息，请参阅 *Azure 安全基线：* 网络安全](../security/benchmarks/security-control-network-security.md)。

### <a name="11-protect-azure-resources-within-virtual-networks"></a>1.1：保护虚拟网络中的 Azure 资源

**指南** ：创建包含独立公共子网和专用子网的经典 Azure 虚拟网络，根据受信任端口和 IP 范围强制隔离。 这些虚拟网络和子网必须是经典虚拟网络 (经典部署) 基于的资源，而不是当前的 Azure 资源管理器资源。  

使用网络安全组允许或拒绝流量，其中包含基于流量方向、协议、源地址和端口以及目标地址和端口的访问控制规则。 网络安全组的规则随时可以更改，更改将应用于所有关联的实例。

Microsoft Azure 云服务 (经典) 不能放置在 Azure 资源管理器虚拟网络中。 但是，基于资源管理器的虚拟网络和基于部署的经典虚拟网络可以通过对等互连进行连接。 

- [网络安全组概述](../virtual-network/network-security-groups-overview.md)

- [虚拟网络对等互连](https://docs.microsoft.com/azure/cloud-services/cloud-services-connectivity-and-networking-faq?&amp;preserve-view=true#how-can-i-use-azure-resource-manager-virtual-networks-with-cloud-services)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="12-monitor-and-log-the-configuration-and-traffic-of-virtual-networks-subnets-and-nics"></a>1.2：监视和记录虚拟网络、子网和 NIC 的配置与流量

**指南** ：记录你的 Azure 云服务配置并监视其是否发生更改。 使用服务的配置文件来指定要为服务中的每个角色部署的角色实例数、任何配置设置的值以及与角色关联的任何证书的指纹。 

如果服务是虚拟网络的一部分，则必须在服务配置文件以及虚拟网络配置文件中提供网络的配置信息。 服务配置文件的默认扩展名为 .csdef。 请注意，不支持将 Azure 策略用于经典部署，因此无法进行配置。

在服务配置文件中设置云服务的配置值 ( .cscfg) ，并在服务定义 ( 的) 文件中定义定义。 使用服务定义文件定义应用程序的服务模型。 定义可用于云服务的角色，还可以指定服务终结点。 记录包含服务配置文件的 Azure 云服务的配置。 可以通过 ServiceConfig 文件进行任何重新配置。 

监视可选的 NetworkTrafficRules 元素服务定义，该定义将限制哪些角色可以与指定的内部终结点通信。 在服务定义文件中配置 NetworkTrafficRules 节点，该节点是一个可选元素，用于指定角色应如何相互通信。 限制哪些角色可以访问特定角色的内部终结点。  请注意，无法更改服务定义。 

启用网络安全组流日志，并将日志发送到 Azure 存储帐户进行审核。 将流日志发送到 Log Analytics 工作区，并使用流量分析来深入了解 Azure 租户中的流量模式。 流量分析的优势包括能够可视化网络活动、识别热点和安全威胁、了解通信流模式，以及查明网络不当配置。

- [Azure 资源管理器与经典部署-了解部署模型和资源状态](../azure-resource-manager/management/deployment-models.md)

- [云服务配置文件](schema-cscfg-file.md)

- [Azure 策略支持的服务列表](https://docs.microsoft.com/cli/azure/azure-services-the-azure-cli-can-manage?&amp;preserve-view=true)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="13-protect-critical-web-applications"></a>1.3：保护关键 Web 应用程序

**指南** ：在 Azure 云服务和客户之间传输数据时，Microsoft 使用 (TLS) 协议1.2 版的传输层安全性来保护数据。 Microsoft 的数据中心与连接到 Azure 服务的客户端系统协商建立 TLS 连接。 TLS 提供严格的身份验证，消息隐私性和完整性强（允许检测消息篡改、拦截和伪造），具有良好的互操作性，算法灵活，易于部署和使用。

- [加密基础知识](../security/fundamentals/encryption-overview.md)

- [配置 TLS/SSL 证书](cloud-services-configure-ssl-certificate-portal.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="14-deny-communications-with-known-malicious-ip-addresses"></a>1.4：拒绝与已知恶意的 IP 地址进行通信

**指南** ： Azure 云实现多层网络安全性，以保护其平台服务免受分布式拒绝服务 (DDoS) 攻击。 Azure DDoS 防护是 Azure 云持续监视过程的一部分，通过渗透测试不断改进。 此 DDoS 防护不仅可经受外部攻击，还能经受其他 Azure 租户的攻击。 

除了 Azure 云服务内的平台级保护之外，还有几种不同的方法可以阻止或拒绝通信。 其中包括： 

-  创建一个启动任务来选择性地阻止某些特定 IP 地址
-  通过修改 IIS web.config 文件，限制 Azure web 角色对一组指定的 IP 地址的访问权限

禁止将流量传入到你的云服务的默认 URL 或名称，例如， *cloudapp.net。将主机标头设置为自定义 DNS 名称，该名称位于云服务定义中的 "网站绑定配置" 下 (* ") 文件中。

将拒绝应用规则配置为经典订阅管理员分配。 默认情况下，在定义内部终结点后，通信可以从任意角色流动到角色的内部终结点，而不会受到任何限制。 若要限制通信，你必须将 NetworkTrafficRules 元素添加到服务定义文件中的 ServiceDefinition 元素。

- [如何阻止/禁用到云服务的默认 URL 的传入流量](https://docs.microsoft.com/azure/cloud-services/cloud-services-connectivity-and-networking-faq?&amp;preserve-view=true#how-can-i-blockdisable-incoming-traffic-to-the-default-url-of-my-cloud-service)

- [Azure DDOS 保护](https://docs.microsoft.com/azure/cloud-services/cloud-services-connectivity-and-networking-faq?&amp;preserve-view=true#how-do-i-prevent-receiving-thousands-of-hits-from-unknown-ip-addresses-that-might-indicate-a-malicious-attack-to-the-cloud-service)

- [阻止特定 IP 地址](cloud-services-startup-tasks-common.md#block-a-specific-ip-address)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="15-record-network-packets"></a>1.5：记录网络数据包

**指南** ：使用 Azure 网络观察程序、网络性能监视、诊断和分析服务（允许监视 Azure 网络）。 网络观察程序代理虚拟机扩展是在按需捕获网络流量和 Azure 虚拟机上的其他高级功能时所必需的。 安装网络观察程序代理虚拟机扩展，并打开网络安全组流日志。

配置网络安全组的流日志记录。 查看有关如何将网络观察程序虚拟机扩展部署到通过经典部署模型部署的现有虚拟机的详细信息。

- [配置网络安全组的流日志记录](../virtual-machines/extensions/network-watcher-linux.md)

- [有关配置流日志的详细信息，请访问](https://docs.microsoft.com/cli/azure/azure-services-the-azure-cli-can-manage?&amp;preserve-view=true)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="16-deploy-network-based-intrusion-detectionintrusion-prevention-systems-idsips"></a>1.6：部署基于网络的入侵检测/入侵防护系统 (IDS/IPS)

**指南** ： Azure 云服务没有内置 ID 或 ip 功能。 根据组织的要求，客户可以从 Azure Marketplace 中选择并部署基于网络的补充网络 ID 或 IPS 解决方案。 使用第三方解决方案时，请确保使用 Azure 云服务全面测试所选的 ID 或 IPS 解决方案，以确保正确的操作和功能。

- [Azure 市场](https://azuremarketplace.microsoft.com/marketplace/?term=Firewall) 

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="17-manage-traffic-to-web-applications"></a>1.7：管理发往 Web 应用程序的流量

**指南** ：连接到 Azure 云服务的服务证书可实现与服务之间的安全通信。 这些证书是在服务定义中定义的，会自动部署到运行 web 角色实例的虚拟机。 例如，对于 web 角色，可以使用可对公开的 HTTPS 终结点进行身份验证的服务证书。 

若要更新证书，只需上传新证书并更改服务配置文件中的指纹值。

使用 TLS 1.2 协议，最常用的方法是保护数据，提供保密性和完整性保护。 

通常，若要保护 web 应用程序并对其进行保护，使其免受 OWASP Top 10 等攻击，你可以部署支持防火墙的 Azure Azure 应用程序网关，以保护 web 应用程序。 

- [服务证书](cloud-services-certs-create.md)

- [为 Azure 中的应用程序配置 TLS](cloud-services-configure-ssl-certificate-portal.md)

- [如何部署应用程序网关](../application-gateway/quick-create-portal.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="19-maintain-standard-security-configurations-for-network-devices"></a>1.9：维护网络设备的标准安全配置

**指南** ：强化 Azure 云服务配置并监视其是否发生更改。 服务配置文件指定要为服务中每个角色部署的角色实例数、任何配置设置的值，以及与角色关联的任何证书的缩略图。 

如果服务是虚拟网络的一部分，则必须在服务配置文件以及虚拟网络配置文件中提供网络的配置信息。 服务配置文件的默认扩展名为 .csdef。

请注意，azure 云服务不支持 Azure 策略进行配置。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="110-document-traffic-configuration-rules"></a>1.10：阐述流量配置规则

**指南** ： azure 网络安全组可用于筛选进出 Azure 虚拟网络中的 azure 资源的网络流量。 网络安全组包含安全规则，这些规则可允许或拒绝来自多种类型的 Azure 资源的入站网络流量，或拒绝来自的出站网络流量。 可以为每项规则指定源和目标、端口以及协议。

使用 Azure 云服务中的单个网络安全组规则的 "描述" 字段，记录允许进出网络流量的规则。

- [如何使用网络安全组规则筛选网络流量](../virtual-network/tutorial-filter-network-traffic.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="111-use-automated-tools-to-monitor-network-resource-configurations-and-detect-changes"></a>1.11：使用自动化工具来监视网络资源配置和检测更改

**指南** ：使用 Azure 流量管理器的内置终结点监视和自动终结点故障转移功能。 它们有助于交付高可用性应用程序，这些应用程序可灵活应对终结点和 Azure 区域故障。 若要配置终结点监视，必须在流量管理器配置文件中指定某些设置。

将活动日志（Azure 中的平台日志）从活动日志中收集到订阅级事件。 它包括当修改资源或启动虚拟机时的信息。 在 Azure 门户中查看活动日志，或在 PowerShell 和 CLI 中检索条目。 

创建诊断设置以将活动日志发送到 Azure Monitor，将 Azure 事件中心转发到 Azure 外部，或发送到 Azure 存储以进行存档。 配置 Azure 云服务中的关键资源发生更改时，通知警报 Azure Monitor。 

- [Azure 活动日志](../azure-monitor/platform/activity-log.md)

- [使用 Azure Monitor 创建、查看和管理活动日志警报](../azure-monitor/platform/alerts-activity-log.md)

- [流量管理器监视](../traffic-manager/traffic-manager-monitoring.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="logging-and-monitoring"></a>日志记录和监视

[有关详细信息，请参阅 *Azure 安全基线：* 日志记录和监视](../security/benchmarks/security-control-logging-monitoring.md)。

### <a name="21-use-approved-time-synchronization-sources"></a>2.1：使用批准的时间同步源

**指南** ： Microsoft 维护 Azure 云服务的 azure 资源的时间源。 客户可能需要创建网络规则，以允许通过 UDP 协议通过端口123访问其环境中使用的时间服务器。

- [NTP 服务器访问](../firewall/protect-windows-virtual-desktop.md#additional-considerations)

**Azure 安全中心监视** ：是

**责任** ：共享

### <a name="22-configure-central-security-log-management"></a>2.2：配置中心安全日志管理

**指南** ：使用 Azure 事件中心以编程方式使用云服务流数据。 将所有这些数据集成并发送到 Azure Sentinel，以监视和查看日志，或使用第三方 SIEM。 对于中心安全日志管理，请将所选 Azure 安全中心数据的连续导出配置到 Azure 事件中心，并为 SIEM 设置相应的连接器。 下面是 Azure Sentinel 的一些选项，包括第三方工具：

- Azure Sentinel-使用本机安全中心警报数据连接器
- Splunk-使用 Splunk 的 Azure Monitor 外接程序
- IBM QRadar - 使用手动配置的日志源
- ArcSight –使用 SmartConnector

有关 Azure Sentinel 的可用连接器的其他详细信息，请参阅 Azure Sentinel 文档。 

- [连接数据源](../sentinel/connect-data-sources.md)

- [与 SIEM 集成](../security-center/continuous-export.md)

- [存储诊断数据](diagnostics-extension-to-storage.md)

- [通过 Azure 事件中心配置 SIEM 集成](../security-center/continuous-export.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="23-enable-audit-logging-for-azure-resources"></a>2.3：为 Azure 资源启用审核日志记录

**指南** ：配置 Visual Studio 以设置用于对 Azure 云服务进行故障排除的 Azure 诊断，这将捕获虚拟机上的系统和日志记录数据，包括运行 Azure 云服务的虚拟机实例。 诊断数据将传输到所选的存储帐户。 在 Azure 云服务项目中启用诊断，然后再进行部署。

 
查看 Azure Monitor 中的活动日志中的某些事件的更改历史记录。 审核事件时间段内发生的更改。 从活动日志中选择事件以进行更深入的检查，并使用更改历史记录 (预览 ") 选项卡。从 Visual Studio 发布 Azure 云服务时，请将诊断数据发送到 Application Insights。 在此时创建 Application Insights Azure 资源，或将数据发送到现有的 Azure 资源。 

可以通过 Application Insights 来监视 Azure 云服务的可用性、性能、故障和使用情况。 可将自定义图表添加到 Application Insights，以便查看最重要的数据。 可以使用 Azure 云服务项目中的 Application Insights SDK 收集角色实例数据。 

- [部署前在 Visual Studio 中启用诊断](https://docs.microsoft.com/visualstudio/azure/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines?&amp;preserve-view=true#to-turn-on-diagnostics-in-visual-studio-before-deployment)

- [查看更改历史记录](../azure-monitor/platform/activity-log.md#view-change-history)

- [适用于 Azure 云服务的 Application Insights (经典) ](../azure-monitor/app/cloudservices.md)

- [为 Azure 云服务 (经典) 和虚拟机设置诊断](https://docs.microsoft.com/visualstudio/azure/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines?toc=%2Fazure%2Fcloud-services%2Ftoc.json&amp;preserve-view=true)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="25-configure-security-log-storage-retention"></a>2.5：配置安全日志存储保留期

**指南** ：你可以使用 Azure 云服务的高级监视，以5分钟、1小时和12小时为单位采样和收集其他指标。 聚合数据存储在存储帐户的表中，并在10天后清除。 但是，使用的存储帐户是按角色配置的，你可以对不同的角色使用不同的存储帐户。 这种配置是使用 .csdef 和 .cscfg 文件中的连接字符串完成的。

请注意，高级监视涉及到使用 Azure 诊断扩展 (Application Insights SDK 在要监视的角色上是可选的) 。 该诊断扩展使用名为 diagnostics.wadcfgx 的配置文件（按角色）来配置所监视的诊断指标。 Azure 诊断扩展收集数据，并将数据存储在 Azure 存储帐户中。 在 .wadcfgx、.csdef 和 .cscfg 文件中配置这些设置。

- [云服务监视简介](cloud-services-how-to-monitor.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="26-monitor-and-review-logs"></a>2.6：监视和审查日志

**指南** ：适用于 Azure 云服务的基本或高级监视模式。 Azure 云服务会自动收集主机虚拟机中 (CPU 百分比、网络传入/传出和磁盘读/写) 的基本监视数据。 在 Azure 门户中的云服务的 "概述" 和 "指标" 页上查看收集的监视数据。 

使用 Azure 诊断扩展时，在 Azure 云服务中启用诊断，收集诊断数据（如应用程序日志、性能计数器等）。 使用 Set-AzureServiceDiagnosticsExtension cmdlet 在已运行的云服务上启用或更新诊断配置，或自动部署含诊断扩展的云服务。 （可选）安装 Application Insights SDK。 将性能计数器发送到 Azure Monitor。

Azure 诊断扩展收集数据，并将数据存储在 Azure 存储帐户中。 将诊断数据传输到 Microsoft Azure 存储模拟器或 Azure 存储空间，因为它不是永久存储。 一旦进入存储，就可以使用几种可用的工具之一进行查看，如 Visual Studio 中的服务器资源管理器，Microsoft Azure 存储资源管理器，Azure Management Studio。 使用配置文件配置要监视的诊断指标，该配置文件 (每个角色) 诊断扩展中名为 diagnostics.wadcfgx。 

- [云服务监视简介](cloud-services-how-to-monitor.md)

- [如何在辅助角色中启用诊断-与 SIEM 集成](../security-center/continuous-export.md)

- [使用 PowerShell 在 Azure 云服务中启用诊断](cloud-services-diagnostics-powershell.md)

- [在 Azure 存储中存储和查看诊断数据](diagnostics-extension-to-storage.md?&amp;preserve-view=true)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="27-enable-alerts-for-anomalous-activities"></a>2.7：针对异常活动启用警报

**指南** ：可以通过与 azure Sentinel 集成，或使用第三方 SIEM 来监视 Azure 云服务日志数据，为异常活动启用警报。

- [与 SIEM 集成](../security-center/continuous-export.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="28-centralize-anti-malware-logging"></a>2.8：集中管理反恶意软件日志记录

**指南** ：适用于 azure 的 Microsoft 反恶意软件可以保护 Azure 云服务和虚拟机。 此外，还可以选择部署第三方安全解决方案，例如 web 应用程序防火墙、网络防火墙、反恶意软件、入侵检测和防护系统 (ID 或 IPS) 等。

- [Azure 基本 IPS/IDS 和 DDOS 提供的特性和功能有哪些](https://docs.microsoft.com/azure/cloud-services/cloud-services-configuration-and-management-faq?&amp;preserve-view=true#what-are-the-features-and-capabilities-that-azure-basic-ipsids-and-ddos-provides)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="identity-and-access-control"></a>标识和访问控制

[有关详细信息，请参阅 *Azure 安全基线：* 标识和访问控制](../security/benchmarks/security-control-identity-access-control.md)。

### <a name="31-maintain-an-inventory-of-administrative-accounts"></a>3.1：维护管理帐户的清单

**指南** ： Microsoft 建议使用 azure RBAC)  (，使用 azure 基于角色的访问控制来管理对 azure 资源的访问权限。 但是，azure 云服务不支持 Azure RBAC 模型，因为它不是基于 Azure 资源管理器的服务，必须使用经典订阅

默认情况下，帐户管理员、服务管理员和 Co-Administrator 是 Azure 中的三种经典订阅管理员角色。 

经典订阅管理员对 Azure 订阅拥有完全访问权限。 他们可以使用 Azure 门户、Azure 资源管理器 API 和经典部署模型 API 来管理资源。 用于注册 Azure 的帐户会自动同时设置为帐户管理员和服务管理员。 稍后可以添加其他 Co-Administrators。 

服务管理员和 Co-Administrators 对已在订阅范围 (Azure 角色) 分配了 "所有者" 角色的用户具有等效的访问权限。 使用 Azure 门户上的 "经典管理员" 选项卡管理 Co-Administrators 或查看服务管理员。 

通过命令列出经典服务管理员和共同的角色分配：

Get-AzRoleAssignment-IncludeClassicAdministrators

查看经典订阅管理角色之间的差异。 

- [三个经典订阅管理角色之间的差异](../role-based-access-control/rbac-and-directory-admin-roles.md#classic-subscription-administrator-roles)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="33-use-dedicated-administrative-accounts"></a>3.3：使用专用管理帐户

**指南** ：建议根据可用角色以及操作和管理 Azure 云服务资源所需的权限，创建围绕专用管理帐户使用的标准操作过程。

- [经典订阅管理角色之间的差异](../role-based-access-control/rbac-and-directory-admin-roles.md#classic-subscription-administrator-roles)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="34-use-single-sign-on-sso-with-azure-active-directory"></a>3.4：将单一登录 (SSO) 与 Azure Active Directory 配合使用

**指南** ：避免为在 Azure 云服务上运行的应用程序管理单独的标识。 实现单一登录，以避免要求用户管理多个标识和凭据。

- [什么是 (SSO) 的单一登录 ](../active-directory/manage-apps/what-is-single-sign-on.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="36-use-dedicated-machines-privileged-access-workstations-for-all-administrative-tasks"></a>3.6：对所有管理任务使用专用计算机（特权访问工作站）

**指南** ：建议使用 Azure 托管的安全工作站 (也称为特权访问工作站) ，以执行需要提升权限的管理任务。

- [了解安全的 Azure 托管工作站](../active-directory/devices/concept-azure-managed-workstation.md)

- [如何启用 Azure AD MFA](../active-directory/authentication/howto-mfa-getstarted.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="data-protection"></a>数据保护

[有关详细信息，请参阅 *Azure 安全基线：* 数据保护](../security/benchmarks/security-control-data-protection.md)。

### <a name="41-maintain-an-inventory-of-sensitive-information"></a>4.1：维护敏感信息的清单

**指南** ：使用 Azure 云服务 REST Api 列出 Azure 云服务资源的清单，了解相关信息。 轮询部署的云服务资源以获取配置和 .pkg 资源。

 例如，下面列出了几个 Api：

- 获取部署-获取部署操作返回部署的配置信息、状态和系统属性。
- 获取包-获取包操作检索部署的云服务包，并将包文件存储在 Microsoft Azure Blob 存储中
- 获取云服务属性-"获取云服务属性" 操作检索指定云服务的属性

查看 Azure 云服务 REST Api 文档，并根据组织的要求，创建用于保护敏感信息的数据。

- [获取部署](/rest/api/compute/cloudservices/rest-get-deployment)

- [获取云服务属性](/rest/api/compute/cloudservices/rest-get-cloud-service-properties)

- [获取包](/rest/api/compute/cloudservices/rest-get-package)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="42-isolate-systems-storing-or-processing-sensitive-information"></a>4.2：隔离存储或处理敏感信息的系统

**指南** ：使用单独的订阅和管理组为 Azure 云服务的环境类型和数据敏感度级别实现隔离。

你还可以在 Azure 云服务的证书元素中编辑 "permissionLevel"，以指定赋予角色进程的访问权限。 如果只希望提升的进程能够访问私钥，请指定提升的权限。 limitedOrElevated 权限允许所有角色进程访问私钥。 可能的值为 limitedOrElevated 或升高。 默认值为 limitedOrElevated。

- [如何创建其他 Azure 订阅](/azure/billing/billing-create-subscription)

- [如何创建管理组](/azure/governance/management-groups/create)

- [WebRole 架构](schema-csdef-webrole.md#Certificate)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="43-monitor-and-block-unauthorized-transfer-of-sensitive-information"></a>4.3：监视和阻止未经授权的敏感信息传输

**指南** ：建议使用网络外围 Azure Marketplace 中的第三方解决方案来监视敏感信息的未授权传输，并在通知信息安全专业人员时阻止此类传输。

- [了解 Azure 中的客户数据保护](../security/fundamentals/protection-customer-data.md)

**Azure 安全中心监视** ：不适用

**责任** ：共享

### <a name="44-encrypt-all-sensitive-information-in-transit"></a>4.4：加密传输中的所有敏感信息

**指南** ：为 Azure 云服务配置 TLS v2。 使用 Azure 门户将证书添加到暂存的 Azure 云服务部署，并将证书信息添加到服务的已进行的文件和 .CSCFG 文件中。 重新打包应用程序，并更新过渡部署以使用新的包。 

使用 Azure 中的服务证书，这些证书连接到 Azure 云服务，以实现与服务之间的安全通信。 提供可对公开的 HTTPS 终结点进行身份验证的证书。 在云服务的服务定义中定义服务证书，并将其自动部署到运行角色实例的虚拟机。

通过管理 API) 管理证书进行身份验证，以便通过经典部署模型进行身份验证。 许多程序和工具（如 Visual Studio 或 Azure SDK）会使用这些证书来自动配置和部署各种 Azure 服务。 

为了进一步参考，Azure 服务管理 API 提供了对通过 Azure 门户提供的服务管理功能的编程访问。 用于 Python 的 azure SDK 可用于管理 Azure 云服务和 Azure 存储帐户。 用于 Python 的 Azure SDK 包装服务管理 API，这是一个 REST API。 所有 API 操作都通过 TLS 执行，并使用 X.509 v3 证书互相进行身份验证。 可以从在 Azure 中运行的服务内访问管理服务。 还可以直接通过 Internet 从可发送 HTTPS 请求和接收 HTTPS 响应的任意应用程序访问管理服务。

- [在 Azure 中为应用程序配置 TLS](cloud-services-configure-ssl-certificate-portal.md)

- [从 Python 使用服务管理](cloud-services-python-how-to-use-service-management.md)

**Azure 安全中心监视** ：不适用

**责任** ：共享

### <a name="45-use-an-active-discovery-tool-to-identify-sensitive-data"></a>4.5：使用有效的发现工具识别敏感数据

**指南** ：建议使用第三方活动发现工具来确定组织的技术系统（包括位于现场的或远程服务提供商）存储、处理或传输的所有敏感信息，然后更新组织的敏感信息清单。

- [了解 Azure 中的客户数据保护](../security/fundamentals/protection-customer-data.md)

**Azure 安全中心监视** ：不适用

**责任** ：共享

### <a name="47-use-host-based-data-loss-prevention-to-enforce-access-control"></a>4.7：使用基于主机的数据丢失防护来强制实施访问控制

**指南** ：不适用于云服务 (经典) 。 它不强制防止数据丢失。

建议实现第三方工具，例如基于主机的自动化数据丢失防护解决方案，即使在将数据复制到系统中时也可以对数据强制实施访问控制。

对于 Microsoft 管理的底层平台，Microsoft 会将所有客户内容视为敏感数据，并会全方位地防范客户数据丢失和遭到透露。 为了确保 Azure 中的客户数据保持安全，Microsoft 实现并维护一套可靠的数据保护控件和功能。

- [了解 Azure 中的客户数据保护](../security/fundamentals/protection-customer-data.md)

**Azure 安全中心监视** ：不适用

**责任** ：共享

### <a name="48-encrypt-sensitive-information-at-rest"></a>4.8：静态加密敏感信息

**指南** ： Azure 云服务不支持静态加密。 这是因为 Azure 云服务设计为无状态。 Azure 云服务支持外部存储，例如，默认情况下加密的 Azure 存储。  

存储在临时磁盘中的应用程序数据不会加密。 客户负责根据需要管理和加密这些数据。  

- [了解 Azure 中的静态加密](../security/fundamentals/encryption-atrest.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="49-log-and-alert-on-changes-to-critical-azure-resources"></a>4.9：记录对关键 Azure 资源的更改并对此类更改发出警报

**指南** ：你可以在 Azure Monitor 中使用经典指标警报，以便在将某个指标应用于关键资源时收到通知。 经典指标警报是一项较旧的功能，仅允许对非维度指标发出警报。 有一个称为“指标警报”的较新功能，它具有比经典指标警报改进的功能。 

此外，Application Insights 可以监视 Azure 云服务应用的可用性、性能、故障和使用情况。 这会将 Application Insights Sdk 中的合并数据与 Azure 云服务中的 Azure 诊断数据结合使用。

- [使用 Azure Monitor 创建、查看和管理经典指标警报](../azure-monitor/platform/alerts-classic-portal.md)

- [指标警报概述](../azure-monitor/platform/alerts-metric-overview.md) 

- [适用于 Azure 云服务的 Application Insights (经典) ](../azure-monitor/app/cloudservices.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="vulnerability-management"></a>漏洞管理

[有关详细信息，请参阅 *Azure 安全基线：* 漏洞管理](../security/benchmarks/security-control-vulnerability-management.md)。

### <a name="52-deploy-automated-operating-system-patch-management-solution"></a>5.2：部署自动操作系统修补管理解决方案

**指南** ：请注意，此信息与 Azure 云服务辅助角色的 azure 来宾操作系统以及平台即服务 (PaaS) 相关。 不过，它不会应用于具有基础结构即服务 (IaaS) 的虚拟机。

默认情况下，Azure 会定期将客户的来宾操作系统更新为操作系统系列中的最新支持的映像，这些映像在其服务配置 ( .cscfg) 中指定，例如 Windows Server 2016。

当客户为其 Azure 云服务部署选择特定的操作系统版本时，它将禁用自动操作系统更新，并对其责任进行修补。 客户必须确保其角色实例正在接收更新，或者他们可能会将其应用程序公开给安全漏洞。

- [Azure 来宾 OS](cloud-services-guestos-msrc-releases.md)

- [Azure 来宾 OS 可支持性和停用策略](cloud-services-guestos-retirement-policy.md)

- [如何配置云服务 (经典) ](cloud-services-how-to-configure-portal.md)

- [管理来宾 OS 版本](cloud-services-how-to-configure-portal.md#manage-guest-os-version)

**Azure 安全中心监视** ：不适用

**责任** ：共享

### <a name="53-deploy-an-automated-patch-management-solution-for-third-party-software-titles"></a>5.3：为第三方软件部署自动化补丁管理解决方案

**指南** ：使用第三方修补程序管理解决方案。 已在其环境中使用 Configuration Manager 的客户还可以使用 System Center Updates Publisher，以便将自定义更新发布到 Windows Server 更新服务中。 

这样更新管理就可以通过第三方软件来修补使用 Configuration Manager 作为其更新存储库的计算机。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="55-use-a-risk-rating-process-to-prioritize-the-remediation-of-discovered-vulnerabilities"></a>5.5：使用风险评级过程来确定已发现漏洞的修正措施的优先级

**指南** ：建议客户定期从 DDoS 攻击的风险范围中了解风险。 

建议在以下情况下考虑：

- 哪些新公开发布的 Azure 资源需要保护？
- 服务中是否存在单一故障点？
- 如何隔离服务，以限制某项攻击造成的影响，同时使服务仍可供合法客户使用？
- 是否有虚拟网络应启用标准 DDoS 防护，但却没有启用？
- 我的服务在跨多个区域故障转移后是否保持主动/主动状态？

支持性文档：

- [针对 Azure 资源的风险评估](../security/fundamentals/ddos-best-practices.md#risk-evaluation-of-your-azure-resources)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="inventory-and-asset-management"></a>库存和资产管理

[有关详细信息，请参阅 *Azure 安全基线：* 清单和资产管理](../security/benchmarks/security-control-inventory-asset-management.md)。

### <a name="61-use-automated-asset-discovery-solution"></a>6.1：使用自动化资产发现解决方案

**指南** ：不适用于 Azure 云服务。 此建议适用于 IaaS 计算资源。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="63-delete-unauthorized-azure-resources"></a>6.3：删除未经授权的 Azure 资源

**指南** ：建议定期协调清点，并确保从订阅中及时删除未经授权的资源。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="64-define-and-maintain-an-inventory-of-approved-azure-resources"></a>6.4：定义并维护已批准 Azure 资源的清单

**指南** ：客户应为计算资源定义已批准的 Azure 资源和批准的软件。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="65-monitor-for-unapproved-azure-resources"></a>6.5：监视未批准的 Azure 资源

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：
- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。
- 避免在环境中使用不需要的软件。
- 避免运行旧的不受支持的应用。
- 防止使用组织不允许的特定软件工具。
- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="66-monitor-for-unapproved-software-applications-within-compute-resources"></a>6.6：监视计算资源中未批准的软件应用程序

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：

- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。

- 避免在环境中使用不需要的软件。

- 避免运行旧的不受支持的应用。

- 防止使用组织不允许的特定软件工具。

- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="67-remove-unapproved-azure-resources-and-software-applications"></a>6.7：删除未批准的 Azure 资源和软件应用程序

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：

- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。

- 避免在环境中使用不需要的软件。

- 避免运行旧的不受支持的应用。

- 防止使用组织不允许的特定软件工具。

- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="68-use-only-approved-applications"></a>6.8：仅使用已批准的应用程序

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：

- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。

- 避免在环境中使用不需要的软件。

- 避免运行旧的不受支持的应用。

- 防止使用组织不允许的特定软件工具。

- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="610-maintain-an-inventory-of-approved-software-titles"></a>6.10：维护已获批软件的清单

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：
- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。
- 避免在环境中使用不需要的软件。
- 避免运行旧的不受支持的应用。
- 防止使用组织不允许的特定软件工具。
- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="612-limit-users-ability-to-execute-scripts-in-compute-resources"></a>6.12：限制用户在计算资源中执行脚本的能力

**指南** ：使用 Azure 安全中心提供的自适应应用程序控制功能。 它是来自安全中心的智能、自动化的端到端解决方案，可帮助你控制哪些应用程序可以在 Windows 和 Linux、Azure 和非 Azure 计算机上运行。 它还有助于强化计算机免受恶意软件的侵害。 

此功能适用于 Azure 和非 Azure Windows（所有版本，不管是经典部署模型还是 Azure 资源管理器部署模型）和 Linux 计算机。

安全中心使用机器学习来分析计算机上运行的应用程序，并根据此智能创建允许列表。 此功能大大简化了配置和维护应用程序允许列表策略的过程，让你可以：

- 阻止运行恶意应用程序的尝试（包括在其他情况下可能会被反恶意软件解决方案遗漏的尝试）或者向用户发出此方面的警报。

- 遵循组织要求只能使用许可软件的安全策略。

- 避免在环境中使用不需要的软件。

- 避免运行旧的不受支持的应用。

- 防止使用组织不允许的特定软件工具。

- 允许 IT 部门控制用户使用应用来访问敏感数据。

有关更多详细信息，请参阅引用的链接。

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="613-physically-or-logically-segregate-high-risk-applications"></a>6.13：以物理或逻辑方式隔离高风险应用程序

**指南** ：对于具有 Azure 云服务的敏感或高风险应用程序，请实现单独的订阅或管理组以提供隔离。

使用网络安全组、创建入站安全规则、选择一个服务（如 http），也可以选择一个自定义端口，并为其指定一个优先级和名称。 优先级影响规则的应用顺序，数值越小，就会应用规则。 需要将网络安全组关联到子网或特定网络接口，以根据业务需求隔离或分段网络流量。

有关更多详细信息，请参阅引用的链接。

- [教程-使用 Azure 门户的网络安全组筛选网络流量](../virtual-network/tutorial-filter-network-traffic.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="secure-configuration"></a>安全配置

[有关详细信息，请参阅 *Azure 安全基线：* 安全配置](../security/benchmarks/security-control-secure-configuration.md)。

### <a name="71-establish-secure-configurations-for-all-azure-resources"></a>7.1：为所有 Azure 资源建立安全配置

**指南** ：使用 Azure 安全中心提供的建议作为 Azure 云服务资源的安全配置基线。 

在 Azure 门户上，依次选择 "安全中心"、"计算 &amp; 应用" 和 "Azure 云服务"，查看适用于你的服务资源的建议。

- [安全建议 - 参考指南](../security-center/recommendations-reference.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="73-maintain-secure-azure-resource-configurations"></a>7.3：维护安全的 Azure 资源配置

**指南** ：不适用于 Azure 云服务。 它基于经典部署模型。 建议使用第三方解决方案来维护安全的 Azure 资源配置

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="75-securely-store-configuration-of-azure-resources"></a>7.5：安全存储 Azure 资源的配置

**指南** ： Azure 云服务的配置文件存储资源的操作属性。 可以将配置文件的副本存储到安全存储帐户。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="77-deploy-configuration-management-tools-for-azure-resources"></a>7.7：部署 Azure 资源的配置管理工具

**指南** ：不适用于 Azure 云服务。 它基于经典部署模型，无法由 Azure 资源管理器基于部署的配置工具进行管理。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="78-deploy-configuration-management-tools-for-operating-systems"></a>7.8：部署操作系统的配置管理工具

**指南** ：不适用于 Azure 云服务。 此建议适用于基于 (IaaS) 计算资源的基础结构即服务。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="79-implement-automated-configuration-monitoring-for-azure-resources"></a>7.9：为 Azure 资源实施自动配置监视

**指导** ：使用 Azure 安全中心对 Azure 资源执行基线扫描。  

- [如何在 Azure 安全中心修正建议](../security-center/security-center-remediate-recommendations.md)

**Azure 安全中心监视** ：是

**责任** ：客户

### <a name="710-implement-automated-configuration-monitoring-for-operating-systems"></a>7.10：为操作系统实施自动配置监视

**指南** ：在 Azure 安全中心中，选择 "计算 &amp; 应用" 功能，并根据虚拟机、服务器和容器的建议进行操作。

- [了解 Azure 安全中心容器建议](/azure/security-center/security-center-container-recommendations)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="711-manage-azure-secrets-securely"></a>7.11：安全管理 Azure 机密

**指南** ： Azure 云服务基于经典部署模型，不与 Azure Key Vault 集成。

你可以保护 Azure 云服务中使用的机密（如凭据），这样就不必每次都键入密码。 若要开始，请指定纯文本密码，并使用 Convertto-html-SecureString PowerShell 命令将其转换为安全字符串。 接下来，使用 Convertfrom-csv-SecureString 将此安全字符串转换为加密的标准字符串。  你现在可以使用集内容将此加密的标准字符串保存到文件。

此外，建议将 Azure 云服务中使用的证书的私钥存储到受保护的存储中。

- [从 PowerShell 配置远程桌面](cloud-services-role-enable-remote-desktop-powershell.md#configure-remote-desktop-from-powershell)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="713-eliminate-unintended-credential-exposure"></a>7.13：消除意外的凭据透露

**指南** ：保护 Azure 云服务中使用的机密（如凭据），这样就不必每次都键入密码。 
 

若要开始，请指定纯文本密码，使用 Convertto-html-SecureString PowerShell 命令将其更改为安全字符串。 接下来，使用 Convertfrom-csv-SecureString 将此安全字符串转换为加密的标准字符串。 现在使用 Set-Content 命令将此加密的标准字符串保存到文件。

将 Azure 云服务中使用的证书的私钥存储到受保护的存储位置。

- [从 PowerShell 配置远程桌面](cloud-services-role-enable-remote-desktop-powershell.md#configure-remote-desktop-from-powershell)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="malware-defense"></a>恶意软件防护

[有关详细信息，请参阅 *Azure 安全基线：* 恶意软件防护](../security/benchmarks/security-control-malware-defense.md)。

### <a name="81-use-centrally-managed-antimalware-software"></a>8.1：使用集中管理的反恶意软件

**指南** ：适用于 azure 的 Microsoft 反恶意软件适用于 Azure 云服务和虚拟机。 这是一个免费的实时保护，可帮助识别和删除病毒、间谍软件和其他恶意软件。 当已知恶意软件或不需要的软件试图在 Azure 系统上安装自己或运行时，该服务会生成警报。 

使用基于 PowerShell 的反恶意软件 cmdlet 来获取反恶意软件配置，使用 "Get-azureserviceantimalwareconfig"。

在 Azure 云服务的启动任务中使用 PowerShell 脚本启用反恶意软件扩展。

选择 Azure 安全中心的自适应应用程序控制功能，这是一个智能、自动化的端到端解决方案。 它可帮助强化计算机免受恶意软件的侵害，并使你能够阻止或通知运行恶意应用程序的尝试，包括那些可能会被反恶意软件解决方案丢失的应用程序。

- [如何以自动方式为 Azure 云服务添加反恶意软件扩展](https://docs.microsoft.com/azure/cloud-services/cloud-services-configuration-and-management-faq?&amp;preserve-view=true#how-can-i-add-an-antimalware-extension-for-my-cloud-services-in-an-automated-way)

- [反恶意软件部署方案](../security/fundamentals/antimalware.md#antimalware-deployment-scenarios)

- [自适应应用程序控制](../security-center/security-center-adaptive-application.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="incident-response"></a>事件响应

[有关详细信息，请参阅 *Azure 安全基线：* 事件响应](../security/benchmarks/security-control-incident-response.md)。

### <a name="101-create-an-incident-response-guide"></a>10.1：创建事件响应指导

**指南** ：为组织制定事件响应指南。 确保在书面的事件响应计划中定义人员职责，以及事件处理/管理从检测到事件后审查的各个阶段。

- [如何在 Azure 安全中心配置工作流自动化](../security-center/security-center-planning-and-operations-guide.md)

- [关于建立自己的安全事件响应流程的指南](https://msrc-blog.microsoft.com/2019/07/01/inside-the-msrc-building-your-own-security-incident-response-process)

- [Microsoft 安全响应中心事件分析](https://msrc-blog.microsoft.com/2019/07/01/inside-the-msrc-building-your-own-security-incident-response-process)

- [客户还可以利用 NIST 的“计算机安全事件处理指南”来制定他们自己的事件响应计划](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="102-create-an-incident-scoring-and-prioritization-procedure"></a>10.2：创建事件评分和优先级设定过程

**指导** ：Azure 安全中心为每条警报分配严重性，方便你根据优先级来确定应该最先调查的警报。 严重性取决于安全中心在发出警报时所依据的检测结果和分析结果的置信度，以及导致发出警报的活动的恶意企图的置信度。 

清楚地标记订阅（例如生产、非生产），并创建命名系统来对 Azure 资源进行明确标识和分类。

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="103-test-security-response-procedures"></a>10.3：测试安全响应过程

**指导** ：定期执行演练来测试系统的事件响应功能。 识别弱点和差距，并根据需要修改计划。 

- [请参阅 NIST 的刊物：Guide to Test, Training, and Exercise Programs for IT Plans and Capabilities](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-84.pdf)（IT 规划和功能的测试、培训与演练计划指南）

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="104-provide-security-incident-contact-details-and-configure-alert-notifications-for-security-incidents"></a>10.4：提供安全事件联系人详细信息，并针对安全事件配置警报通知

**指南** ：如果 Microsoft 安全响应中心 (MSRC) 发现非法或未经授权的某方访问了客户的数据，Microsoft 将使用安全事件联系人信息与你取得联系。 事后审查事件，确保问题得到解决。 

- [如何设置 Azure 安全中心安全联系人](../security-center/security-center-provide-security-contact-details.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="105-incorporate-security-alerts-into-your-incident-response-system"></a>10.5：将安全警报整合到事件响应系统中

**指导** ：使用连续导出功能导出 Azure 安全中心警报和建议。 使用连续导出可以手动导出或者持续导出警报和建议。 可以使用安全中心数据连接器将警报流式传输到 Azure Sentinel。 

- [如何配置连续导出](../security-center/continuous-export.md) 

- [如何将警报流式传输到 Azure Sentinel](../sentinel/connect-azure-security-center.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

### <a name="106-automate-the-response-to-security-alerts"></a>10.6：自动响应安全警报

**指导** ：使用 Azure 安全中心内的工作流自动化功能可以通过“逻辑应用”针对安全警报和建议自动触发响应。

- [如何配置工作流自动化和逻辑应用](../security-center/workflow-automation.md)

**Azure 安全中心监视** ：不适用

**责任** ：客户

## <a name="penetration-tests-and-red-team-exercises"></a>渗透测试和红队练习

[有关详细信息，请参阅 *Azure 安全基线：* 渗透测试和红队演练](../security/benchmarks/security-control-penetration-tests-red-team-exercises.md)。

### <a name="111-conduct-regular-penetration-testing-of-your-azure-resources-and-ensure-remediation-of-all-critical-security-findings"></a>11.1：定期对 Azure 资源执行渗透测试，确保修正所有发现的关键安全问题

指南：遵循 Microsoft Rules of Engagement 以确保渗透测试不违反 Microsoft 政策： https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1 

- [可在此处详细了解如何针对 Microsoft 托管云基础结构、服务和应用程序执行红队测试和实时站点渗透测试，以及 Microsoft 的相关策略](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure 安全中心监视** ：不适用

**责任** ：共享

## <a name="next-steps"></a>后续步骤

- 请参阅 [Azure 安全基准](/azure/security/benchmarks/overview)
- 详细了解 [Azure 安全基线](/azure/security/benchmarks/security-baselines-overview)
