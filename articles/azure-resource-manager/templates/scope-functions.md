---
title: 作用域内部署中的模板函数
description: 介绍如何在范围的部署中解析模板函数。 范围可以是租户、管理组、订阅和资源组。
ms.topic: conceptual
ms.date: 10/22/2020
ms.openlocfilehash: cb02a3dc808604a80fd9943138c1cd0d8648904e
ms.sourcegitcommit: 4cb89d880be26a2a4531fedcc59317471fe729cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681427"
---
# <a name="arm-template-functions-in-deployment-scopes"></a>部署范围内的 ARM 模板函数

借助 Azure 资源管理器模板 (ARM 模板) ，你可以部署到资源组、订阅、管理组或租户。 通常， [ARM 模板函数](template-functions.md) 对于所有作用域都是相同的。 本文介绍了某些函数存在的差异，具体取决于作用域。

## <a name="supported-functions"></a>支持的函数

部署到不同的作用域时，有一些重要的注意事项：

* 资源组部署 **支持** [ResourceGroup ( # B1](template-functions-resource.md#resourcegroup)函数。
* 资源组和订阅部署 **支持**[订阅 ( # B1](template-functions-resource.md#subscription)函数。
* 所有作用域都 **支持** [ ( # B1](template-functions-resource.md#reference)和 [list ( # B3](template-functions-resource.md#list)函数的引用。
* 使用 [resourceId ( # B1 ](template-functions-resource.md#resourceid) 获取在资源组中部署的资源的 ID。

  ```json
  "subnet": {
    "id": "[resourceId(parameters('virtualNetworkResourceGroup'), 'Microsoft.Network/virtualNetworks/subnets', parameters('virtualNetworkName'), parameters('subnet1Name'))]"
  }
  ```

* 使用 [subscriptionResourceId ( # B1 ](template-functions-resource.md#subscriptionresourceid) 函数获取在订阅上部署的资源的 ID。

  例如，若要获取部署到订阅的策略定义的资源 ID，请使用：

  ```json
  "roleDefinitionId": "[subscriptionResourceId('Microsoft.Authorization/roleDefinitions', 'acdd72a7-3385-48ef-bd42-f606fba81ae7')]"
  ```

* 对于实现为管理组扩展的资源，请使用 [extensionResourceId ( # B1 ](template-functions-resource.md#extensionresourceid) 函数。 部署到管理组的自定义策略定义是管理组的扩展。

  若要获取管理组级别的自定义策略定义的资源 ID，请使用：
  
  ```json
  "policyDefinitionId": "[extensionResourceId(variables('mgScope'), 'Microsoft.Authorization/policyDefinitions', parameters('policyDefinitionID'))]"
  ```

* 使用 [tenantResourceId](template-functions-resource.md#tenantresourceid) 函数获取租户中部署的资源的 ID。 内置策略定义是租户级别资源。 在管理组级别分配内置策略时，请使用 tenantResourceId 函数。

  若要获取内置策略定义的资源 ID，请使用：
  
  ```json
  "policyDefinitionId": "[tenantResourceId('Microsoft.Authorization/policyDefinitions', parameters('policyDefinitionID'))]"
  ```

## <a name="function-resolution-in-scopes"></a>作用域中的函数解析

当部署到多个范围时，根据指定模板的方式不同，[resourceGroup()](template-functions-resource.md#resourcegroup) 和 [subscription()](template-functions-resource.md#subscription) 函数解析的方式也有所不同。 链接到外部模板时，函数始终解析为该模板的作用域。 在父模板中嵌套模板时，请使用 `expressionEvaluationOptions` 属性指定函数是否解析为父模板或嵌套模板的资源组和订阅。 将属性设置为 `inner`，以便解析为嵌套模板的范围。 将属性设置为 `outer`，以便解析为父模板的范围。

下表显示了函数是解析为父资源组，还是解析为嵌入资源组和订阅。

| 模板类型 | 范围 | 解决方法 |
| ------------- | ----- | ---------- |
| 嵌套        | 外部（默认值） | 父资源组 |
| 嵌套        | 内部 | 子资源组 |
| 链接        | 空值   | 子资源组 |

以下[示例模板](https://github.com/Azure/azure-docs-json-samples/blob/master/azure-resource-manager/crossresourcegroupproperties.json)演示：

* 具有默认（外部）范围的嵌套模板
* 具有内部范围的嵌套模板
* 链接的模板

:::code language="json" source="~/resourcemanager-templates/azure-resource-manager/crossresourcegroupproperties.json":::

若要测试上述模板并查看结果，请使用 PowerShell 或 Azure CLI。

# <a name="powershell"></a>[PowerShell](#tab/azure-powershell)

```azurepowershell-interactive
New-AzResourceGroup -Name parentGroup -Location southcentralus
New-AzResourceGroup -Name inlineGroup -Location southcentralus
New-AzResourceGroup -Name linkedGroup -Location southcentralus

New-AzResourceGroupDeployment `
  -ResourceGroupName parentGroup `
  -TemplateUri https://raw.githubusercontent.com/Azure/azure-docs-json-samples/master/azure-resource-manager/crossresourcegroupproperties.json
```

前述示例的输出为：

```output
 Name             Type                       Value
 ===============  =========================  ==========
 parentRG         String                     Parent resource group is parentGroup
 defaultScopeRG   String                     Default scope resource group is parentGroup
 innerScopeRG     String                     Inner scope resource group is inlineGroup
 linkedRG         String                     Linked resource group is linkedgroup
```

# <a name="azure-cli"></a>[Azure CLI](#tab/azure-cli)

```azurecli-interactive
az group create --name parentGroup --location southcentralus
az group create --name inlineGroup --location southcentralus
az group create --name linkedGroup --location southcentralus

az deployment group create \
  --name ExampleDeployment \
  --resource-group parentGroup \
  --template-uri https://raw.githubusercontent.com/Azure/azure-docs-json-samples/master/azure-resource-manager/crossresourcegroupproperties.json
```

前述示例的输出为：

```output
"outputs": {
  "defaultScopeRG": {
    "type": "String",
    "value": "Default scope resource group is parentGroup"
  },
  "innerScopeRG": {
    "type": "String",
    "value": "Inner scope resource group is inlineGroup"
  },
  "linkedRG": {
    "type": "String",
    "value": "Linked resource group is linkedGroup"
  },
  "parentRG": {
    "type": "String",
    "value": "Parent resource group is parentGroup"
  }
},
```

---

## <a name="next-steps"></a>后续步骤

* 若要了解如何在模板中定义参数，请参阅[了解 Azure Resource Manager 模板的结构和语法](template-syntax.md)。
* 有关解决常见部署错误的提示，请参阅[排查使用 Azure Resource Manager 时的常见 Azure 部署错误](common-deployment-errors.md)。
* 有关部署需要 SAS 令牌的模板的信息，请参阅[使用 SAS 令牌部署专用模板](secure-template-with-sas-token.md)。
