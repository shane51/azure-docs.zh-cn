---
title: 为 Azure AD 中的企业应用禁用用户登录
description: 如何禁用企业应用程序，防止用户在 Azure Active Directory 中登录该程序
services: active-directory
documentationcenter: ''
author: kenwith
manager: celestedg
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: how-to
ms.date: 04/12/2019
ms.author: kenwith
ms.reviewer: asteen
ms.custom: it-pro
ms.collection: M365-identity-device-management
ms.openlocfilehash: c208da657d30d4a0f5b6f171693c5c6abc2b358b
ms.sourcegitcommit: 8e7316bd4c4991de62ea485adca30065e5b86c67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94649171"
---
# <a name="disable-user-sign-ins-for-an-enterprise-app-in-azure-active-directory"></a>在 Azure Active Directory 中对企业应用禁用用户登录

可以轻松地禁用企业应用程序，防止用户在 Azure Active Directory (Azure AD) 中登录该程序。 你需要具有合适的权限才能管理企业应用。 而且，你必须是目录的全局管理员。

## <a name="how-do-i-disable-user-sign-ins"></a>如何禁用用户登录？

1. 使用目录全局管理员的帐户登录到 [Azure 门户](https://portal.azure.com)。
1. 选择“所有服务”  ，在文本框中输入 **Azure Active Directory**，并选择“Enter”  。
1. 在 " **Azure Active Directory**  -   **_directoryname_"*窗格上 (即，用于所管理目录的 Azure AD 窗格) ，请选择 "* 企业应用程序**"。
1. 在“企业应用程序 - 所有应用程序”  窗格上，你会看到你可以管理的应用的列表。 选择一个应用。
1. 在 " **_appname_"*窗格 (即，在标题) 中包含所选应用的名称的窗格中，选择 "_* 属性**"。
1. 在 " **_appname_"*-_*"属性**" 窗格中，选择 "**否**" 以使 **用户能够登录？**。
1. 选择“保存”  命令。

## <a name="use-azure-ad-powershell-to-disable-an-unlisted-app"></a>使用 Azure AD PowerShell 禁用未列出的应用

如果你知道未出现在企业应用列表中的应用的 AppId（例如，因为你删除了该应用，或者由于该应用正在由 Microsoft 预授权而尚未创建服务主体），则可以手动创建该应用的服务主体，然后使用 [AzureAD PowerShell cmdlet](/powershell/module/azuread/New-AzureADServicePrincipal?view=azureadps-2.0) 将其禁用。

```PowerShell
# The AppId of the app to be disabled
$appId = "{AppId}"

# Check if a service principal already exists for the app
$servicePrincipal = Get-AzureADServicePrincipal -Filter "appId eq '$appId'"
if ($servicePrincipal) {
    # Service principal exists already, disable it
    Set-AzureADServicePrincipal -ObjectId $servicePrincipal.ObjectId -AccountEnabled $false
} else {
    # Service principal does not yet exist, create it and disable it at the same time
    $servicePrincipal = New-AzureADServicePrincipal -AppId $appId -AccountEnabled $false
}
```

## <a name="next-steps"></a>后续步骤

* [查看所有组](../fundamentals/active-directory-groups-view-azure-portal.md)
* [向企业应用分配用户或组](assign-user-or-group-access-portal.md)
* [删除企业应用的用户或组分配](./assign-user-or-group-access-portal.md)
* [更改企业应用的名称或徽标](./add-application-portal-configure.md)