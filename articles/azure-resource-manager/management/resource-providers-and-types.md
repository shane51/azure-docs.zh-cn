---
title: 资源提供程序和资源类型
description: 介绍支持 Azure 资源管理器的资源提供程序。 它介绍其架构、可用 API 版本，以及可以承载资源的区域。
ms.topic: conceptual
ms.date: 11/09/2020
ms.custom: devx-track-azurecli
ms.openlocfilehash: 702836e0dc98b06ccf6e0eeb0d0f373374c4e783
ms.sourcegitcommit: 0dcafc8436a0fe3ba12cb82384d6b69c9a6b9536
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94426453"
---
# <a name="azure-resource-providers-and-types"></a>Azure 资源提供程序和类型

部署资源时，经常需要检索有关资源提供程序和类型的信息。 例如，若要存储密钥和机密，请使用 Microsoft.KeyVault 资源提供程序。 此资源提供程序提供名为“保管库”的资源类型，用于创建密钥保管库。

资源类型的名称采用以下格式：{resource-provider}/{resource-type}  。 Key Vault 的资源类型为 **Microsoft.KeyVault/vaults** 。

在本文中，学习如何：

* 查看 Azure 中的所有资源提供程序
* 检查资源提供程序的注册状态
* 注册资源提供程序
* 查看资源提供程序的资源类型
* 查看资源类型的有效位置
* 查看资源类型的有效 API 版本

可以通过 Azure 门户、Azure PowerShell 或 Azure CLI 执行这些步骤。

有关将资源提供程序映射到 Azure 服务的列表，请参阅 [Azure 服务的资源提供程序](azure-services-resource-providers.md)。

## <a name="register-resource-provider"></a>注册资源提供程序

在使用资源提供程序之前，必须为资源提供程序注册你的 Azure 订阅。 注册会将你的订阅配置为使用资源提供程序。 某些资源提供程序在默认情况下已注册。 执行特定操作时，会自动注册其他资源提供程序。 例如，通过门户创建资源时，通常会注册资源提供程序。 对于其他方案，你可能需要手动注册资源提供程序。

本文介绍了如何检查资源提供程序的注册状态，并根据需要将其注册。 你必须具备为资源提供程序执行 `/register/action` 操作的权限。 此权限包含在“参与者”和“所有者”角色中。

你的应用程序代码不应阻止为处于“正在注册”状态的资源提供程序创建资源的操作。 注册资源提供程序时，将针对每个受支持的区域单独执行该操作。 若要在某个区域中创建资源，只需在该区域中完成注册即可。 如果不阻止处于正在注册状态的资源提供程序，则你的应用程序可以以快得多的速度继续执行，不需要等待所有区域完成。

当订阅中仍有某个资源提供程序的资源类型时，不能注销该资源提供程序。

## <a name="azure-portal"></a>Azure 门户

查看所有资源提供程序和订阅的注册状态：

1. 登录 [Azure 门户](https://portal.azure.com)。
2. 在 Azure 门户菜单上，选择“所有服务”。

    ![选择“订阅”](./media/resource-providers-and-types/select-all-services.png)

3. 在“所有服务”  框中，输入“订阅”  ，然后选择“订阅”  。
4. 从订阅列表中选择订阅进行查看。
5. 选择“资源提供程序”  并查看可用资源提供程序的列表。

    ![显示资源提供程序](./media/resource-providers-and-types/show-resource-providers.png)

6. 若要注册资源提供程序，请选择“注册”  。 在上面的屏幕截图中，对于“Microsoft.Blueprint”突出显示了“注册”链接。

查看特定资源提供程序的信息：

1. 登录 [Azure 门户](https://portal.azure.com)。
2. 在 Azure 门户菜单中，选择“所有服务”  。
3. 在“所有服务”  框中，输入“资源浏览器”  ，然后选择“资源浏览器”  。

    ![选择“所有服务”](./media/resource-providers-and-types/select-resource-explorer.png)

4. 通过选择向右箭头来展开“提供程序”  。

    ![选择“提供程序”](./media/resource-providers-and-types/select-providers.png)

5. 展开要查看的资源提供程序和资源类型。

    ![选择资源类型](./media/resource-providers-and-types/select-resource-type.png)

6. 所有区域都支持 Resource Manager，但部署的资源可能无法在所有区域中受到支持。 此外，订阅可能存在一些限制，以防止用户使用某些支持该资源的区域。 资源浏览器显示资源类型的有效位置。

    ![显示位置](./media/resource-providers-and-types/show-locations.png)

7. API 版本对应于资源提供程序发布的 REST API 操作版本。 资源提供程序启用新功能时，会发布 REST API 的新版本。 资源浏览器显示资源类型的有效 API 版本。

    ![显示 API 版本](./media/resource-providers-and-types/show-api-versions.png)

## <a name="azure-powershell"></a>Azure PowerShell

若要查看 Azure 中的所有资源提供程序和订阅的注册状态，请使用：

```azurepowershell-interactive
Get-AzResourceProvider -ListAvailable | Select-Object ProviderNamespace, RegistrationState
```

这会返回类似于以下的结果：

```output
ProviderNamespace                RegistrationState
-------------------------------- ------------------
Microsoft.ClassicCompute         Registered
Microsoft.ClassicNetwork         Registered
Microsoft.ClassicStorage         Registered
Microsoft.CognitiveServices      Registered
...
```

若要查看订阅的所有已注册资源提供程序，请使用：

```azurepowershell-interactive
 Get-AzResourceProvider -ListAvailable | Where-Object RegistrationState -eq "Registered" | Select-Object ProviderNamespace, RegistrationState | Sort-Object ProviderNamespace
```

若要注册资源提供程序，请使用：

```azurepowershell-interactive
Register-AzResourceProvider -ProviderNamespace Microsoft.Batch
```

这会返回类似于以下的结果：

```output
ProviderNamespace : Microsoft.Batch
RegistrationState : Registering
ResourceTypes     : {batchAccounts, operations, locations, locations/quotas}
Locations         : {West Europe, East US, East US 2, West US...}
```

若要查看特定资源提供程序的信息，请使用：

```azurepowershell-interactive
Get-AzResourceProvider -ProviderNamespace Microsoft.Batch
```

这会返回类似于以下的结果：

```output
{ProviderNamespace : Microsoft.Batch
RegistrationState : Registered
ResourceTypes     : {batchAccounts}
Locations         : {West Europe, East US, East US 2, West US...}

...
```

若要查看资源提供程序的资源类型，请使用：

```azurepowershell-interactive
(Get-AzResourceProvider -ProviderNamespace Microsoft.Batch).ResourceTypes.ResourceTypeName
```

将返回：

```output
batchAccounts
operations
locations
locations/quotas
```

API 版本对应于资源提供程序发布的 REST API 操作版本。 资源提供程序启用新功能时，会发布 REST API 的新版本。

若要获取资源类型可用的 API 版本，请使用：

```azurepowershell-interactive
((Get-AzResourceProvider -ProviderNamespace Microsoft.Batch).ResourceTypes | Where-Object ResourceTypeName -eq batchAccounts).ApiVersions
```

将返回：

```output
2017-05-01
2017-01-01
2015-12-01
2015-09-01
2015-07-01
```

所有区域都支持 Resource Manager，但部署的资源可能无法在所有区域中受到支持。 此外，订阅可能存在一些限制，以防止用户使用某些支持该资源的区域。

若要获取某一资源类型的受支持位置，请使用。

```azurepowershell-interactive
((Get-AzResourceProvider -ProviderNamespace Microsoft.Batch).ResourceTypes | Where-Object ResourceTypeName -eq batchAccounts).Locations
```

将返回：

```output
West Europe
East US
East US 2
West US
...
```

## <a name="azure-cli"></a>Azure CLI

若要查看 Azure 中的所有资源提供程序和订阅的注册状态，请使用：

```azurecli-interactive
az provider list --query "[].{Provider:namespace, Status:registrationState}" --out table
```

这会返回类似于以下的结果：

```output
Provider                         Status
-------------------------------- ----------------
Microsoft.ClassicCompute         Registered
Microsoft.ClassicNetwork         Registered
Microsoft.ClassicStorage         Registered
Microsoft.CognitiveServices      Registered
...
```

若要查看订阅的所有已注册资源提供程序，请使用：

```azurecli-interactive
az provider list --query "sort_by([?registrationState=='Registered'].{Provider:namespace, Status:registrationState}, &Provider)" --out table
```

若要注册资源提供程序，请使用：

```azurecli-interactive
az provider register --namespace Microsoft.Batch
```

这将返回“注册正在进行中”的信息。

若要查看特定资源提供程序的信息，请使用：

```azurecli-interactive
az provider show --namespace Microsoft.Batch
```

这会返回类似于以下的结果：

```output
{
    "id": "/subscriptions/####-####/providers/Microsoft.Batch",
    "namespace": "Microsoft.Batch",
    "registrationsState": "Registering",
    "resourceTypes:" [
        ...
    ]
}
```

若要查看资源提供程序的资源类型，请使用：

```azurecli-interactive
az provider show --namespace Microsoft.Batch --query "resourceTypes[*].resourceType" --out table
```

将返回：

```output
Result
---------------
batchAccounts
operations
locations
locations/quotas
```

API 版本对应于资源提供程序发布的 REST API 操作版本。 资源提供程序启用新功能时，会发布 REST API 的新版本。

若要获取资源类型可用的 API 版本，请使用：

```azurecli-interactive
az provider show --namespace Microsoft.Batch --query "resourceTypes[?resourceType=='batchAccounts'].apiVersions | [0]" --out table
```

将返回：

```output
Result
---------------
2017-05-01
2017-01-01
2015-12-01
2015-09-01
2015-07-01
```

所有区域都支持 Resource Manager，但部署的资源可能无法在所有区域中受到支持。 此外，订阅可能存在一些限制，以防止用户使用某些支持该资源的区域。

若要获取某一资源类型的受支持位置，请使用。

```azurecli-interactive
az provider show --namespace Microsoft.Batch --query "resourceTypes[?resourceType=='batchAccounts'].locations | [0]" --out table
```

将返回：

```output
Result
---------------
West Europe
East US
East US 2
West US
...
```

## <a name="next-steps"></a>后续步骤

* 若要了解如何创建资源管理器模板，请参阅[创作 Azure 资源管理器模板](../templates/template-syntax.md)。 
* 若要查看资源提供程序模板架构，请参阅[模板引用](/azure/templates/)。
* 有关将资源提供程序映射到 Azure 服务的列表，请参阅 [Azure 服务的资源提供程序](azure-services-resource-providers.md)。
* 若要查看资源提供程序的操作，请参阅 [Azure REST API](/rest/api/)。
