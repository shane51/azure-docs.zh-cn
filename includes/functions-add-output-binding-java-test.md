---
author: ggailey777
ms.service: azure-functions
ms.topic: include
ms.date: 03/18/2020
ms.author: glenga
ms.openlocfilehash: eb54439f89cc2443eeed2d3b63dfbe7fedb4bf17
ms.sourcegitcommit: eb6bef1274b9e6390c7a77ff69bf6a3b94e827fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "80673437"
---
## <a name="update-the-tests"></a>更新测试

由于原型还创建一组测试，因此需更新这些测试，以便处理 `run` 方法签名中的新 `msg` 参数。  

浏览到测试代码在 _src/test/java_ 下的位置，打开 *Function.java* 项目文件，将 `//Invoke` 下的代码行替换为以下代码。

:::code language="java" source="~/functions-quickstart-java/functions-add-output-binding-storage-queue/src/test/java/com/function/FunctionTest.java" range="48-50":::
