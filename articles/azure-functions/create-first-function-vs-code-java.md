---
title: 使用 Visual Studio Code 创建 Java 函数 - Azure Functions
description: 了解如何创建 Java 函数，然后使用 Visual Studio Code 中的 Azure Functions 扩展将本地项目发布到 Azure Functions 中托管的无服务器实例。
ms.topic: quickstart
ms.date: 11/03/2020
ms.openlocfilehash: daaa578b2842a6314706b3578f4c9e44d46aa6ce
ms.sourcegitcommit: 7cc10b9c3c12c97a2903d01293e42e442f8ac751
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2020
ms.locfileid: "93424594"
---
# <a name="quickstart-create-a-java-function-in-azure-using-visual-studio-code"></a>快速入门：在 Azure 中使用 Visual Studio Code 创建 Java 函数

[!INCLUDE [functions-language-selector-quickstart-vs-code](../../includes/functions-language-selector-quickstart-vs-code.md)]

在本文中，我们使用 Visual Studio Code 来创建一个响应 HTTP 请求的 Java 函数。 在本地测试代码后，将代码部署到 Azure Functions 的无服务器环境。

完成本快速入门会从你的 Azure 帐户中扣取最多几美分的费用。

> [!NOTE]
> 如果 Visual Studio Code 不是首选开发工具，请查看面向使用 [Maven](create-first-function-cli-java.md)、[Gradle](./functions-create-first-java-gradle.md) 和 [IntelliJ IDEA](/azure/developer/java/toolkit-for-intellij/quickstart-functions) 的 Java 开发人员的类似教程。

## <a name="configure-your-environment"></a>配置环境

在开始之前，请确保已满足下列要求：

+ 具有活动订阅的 Azure 帐户。 [免费创建帐户](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio)。

+ [Java 开发人员工具包](/azure/developer/java/fundamentals/java-jdk-long-term-support)版本 8 或 11。

+ [Apache Maven](https://maven.apache.org) 3.0 或更高版本。

+ 安装在某个[受支持的平台](https://code.visualstudio.com/docs/supporting/requirements#_platforms)上的 [Visual Studio Code](https://code.visualstudio.com/)。

+ [Java 扩展包](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)  

+ Visual Studio Code 的 [Azure Functions 扩展](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)。 

## <a name="create-your-local-project"></a><a name="create-an-azure-functions-project"></a>创建本地项目

本部分将使用 Visual Studio Code 在 Java 中创建一个本地 Azure Functions 项目。 稍后在本文中，你要将函数代码发布到 Azure。 

1. 在活动栏中选择“Azure”图标，然后在“Azure:函数”区域中选择“创建新项目...”图标。

    ![选择“创建新项目”](./media/functions-create-first-function-vs-code/create-new-project.png)

1. 为项目工作区选择目录位置，然后选择“选择”  。

    > [!NOTE]
    > 这些步骤已设计为在工作区之外完成。 在这种情况下，请不要选择属于工作区内的项目文件夹。

1. 根据提示提供以下信息：

    + **选择函数项目的语言**：选择`Java`。

    + **选择 Java 的版本**：选择在 Azure 中运行函数的 Java 版本 `Java 8` 或 `Java 11`。 选择已在本地验证的 Java 版本。

    + **提供组 ID**：选择`com.function`。

    + **提供项目 ID**：选择`myFunction`。

    + **提供版本**：选择`1.0-SNAPSHOT`。

    + **提供包名称**：选择`com.function`。

    + **提供应用名称**：选择`myFunction-12345`。

    + **授权级别**：选择 `Anonymous`，这使任何人都可以调用你的函数终结点。 若要了解授权级别，请参阅[授权密钥](functions-bindings-http-webhook-trigger.md#authorization-keys)。

    + **选择打开项目的方式**：选择`Add to workspace`。

1. Visual Studio Code 将使用此信息生成一个包含 HTTP 触发器的 Azure Functions 项目。 可以在资源管理器中查看本地项目文件。 若要详细了解所创建的文件，请参阅[生成的项目文件](functions-develop-vs-code.md#generated-project-files)。 

[!INCLUDE [functions-run-function-test-local-vs-code](../../includes/functions-run-function-test-local-vs-code.md)]

确认该函数可以在本地计算机上正确运行以后，可以使用 Visual Studio Code 将项目直接发布到 Azure。

[!INCLUDE [functions-sign-in-vs-code](../../includes/functions-sign-in-vs-code.md)]

[!INCLUDE [functions-publish-project-vscode](../../includes/functions-publish-project-vscode.md)]

[!INCLUDE [functions-vs-code-run-remote](../../includes/functions-vs-code-run-remote.md)]

[!INCLUDE [functions-cleanup-resources-vs-code.md](../../includes/functions-cleanup-resources-vs-code.md)]

## <a name="next-steps"></a>后续步骤

你已使用 Visual Studio Code 通过简单的 HTTP 触发函数创建了函数应用。 在下一篇文章中，将通过添加输出绑定来扩展该函数。 此绑定将 HTTP 请求中的字符串写入 Azure 队列存储队列中的消息。 

> [!div class="nextstepaction"]
> [连接到 Azure 存储队列](functions-add-output-binding-storage-queue-vs-code.md?pivots=programming-language-java)

[Azure Functions Core Tools]: functions-run-local.md
[Azure Functions extension for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions
