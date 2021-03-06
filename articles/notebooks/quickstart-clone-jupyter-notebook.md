---
title: 使用 Azure Notebooks 预览版从 GitHub 克隆 Jupyter 笔记本
description: 快速克隆 GitHub 存储库中的 Jupyter 笔记本并在 Azure Notebooks 帐户中运行它。
ms.topic: quickstart
ms.date: 12/04/2018
ms.openlocfilehash: 267e79e7d4bf108ac3b2c72d64cee5a07ba638be
ms.sourcegitcommit: eb6bef1274b9e6390c7a77ff69bf6a3b94e827fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "87424471"
---
# <a name="quickstart-clone-a-notebook-in-azure-notebooks-preview"></a>快速入门：在 Azure Notebooks 预览版中克隆笔记本

[!INCLUDE [notebooks-status](../../includes/notebooks-status.md)]

在本快速入门中，你将 GitHub 中存储的一个 Jupyter 笔记本复制到 Azure Notebooks 帐户中。 

GitHub 存储库为 Jupyter 笔记本提供存储和版本控制。 协作者维护存储库的本地副本，并通过这些副本来运行笔记本。 将某个 Jupyter 笔记本从 GitHub 克隆到你的 Azure Notebooks 帐户将创建该笔记本的独立副本。 更改仅存储在 Azure Notebooks 帐户中，不会影响原始 GitHub 存储库。 

由于你的 Azure Notebooks 克隆位于云中，因此可以将它与其他协作者共享，这些协作者不需要创建任何本地复制，也不需要在其计算机上安装 Jupyter。 你还可以克隆某个笔记本来仅将其用作你自己的项目的起点，或者克隆它来获取数据文件。 

## <a name="prerequisites"></a>先决条件
无。

## <a name="clone-azure-cognitive-services-notebooks"></a>克隆 Azure 认知服务笔记本

1. 转到 [Azure Notebooks](https://notebooks.azure.com) 并登录。 有关详细信息，请参阅[快速入门 - 登录 Azure Notebooks](quickstart-sign-in-azure-notebooks.md)。

1. 在公用个人资料页面中，选择页面顶部的“我的项目”  ：

    ![浏览器窗口顶部的“我的项目”链接](media/quickstarts/my-projects-link.png)

1. 在“我的项目”页上，选择向上箭头按钮  （键盘快捷方式：U；当浏览器窗口够宽时，按钮显示为“上传 GitHub 存储库”）： 

    ![“我的项目”页面上的“上传 GitHub 存储库”命令](media/quickstarts/upload-github-repo-command.png)

1. 在出现的“上传 GitHub 存储库”中，输入或设置以下详细信息，然后选择“导入”   ：

   - **GitHub 存储库**：Microsoft/cognitive-services-notebooks（此名称在 [https://github.com/Microsoft/cognitive-services-notebooks](https://github.com/Microsoft/cognitive-services-notebooks) 上克隆适用于 Azure 认知服务的 Jupyter 笔记本）。
   - **以递归方式克隆**：（已清除）
   - 项目名称  ：认知服务克隆
   - **项目 ID**：cognitive-services-clone
   - **公共**：（已清除）

     ![“上传 GitHub 存储库”弹出窗口，用于收集存储库信息](media/quickstarts/upload-github-repo-popup.png)

1. 请耐心等待此过程完成；克隆一个存储库可能需要数分钟。

1. 克隆完成后，Azure Notebooks 会转到新项目，其中可以看到所有文件的副本。

    :::image type="content" source="media/quickstarts/completed-clone.png" alt-text="已完成克隆的视图。" lightbox="media/quickstarts/completed-clone.png":::

## <a name="share-a-notebook"></a>共享笔记本

1. 若要共享已克隆项目的副本，请使用“共享”控件，或者获取一个链接、获取包含该链接的**** HTML 或 Markdown 代码，或者创建包含该链接的电子邮件：

    ![项目共享命令](media/quickstarts/share-project-command.png)

1. 由于在克隆项目时已清除“公共”选项，因此克隆是专用的。 若要将副本公开，请选择“项目设置”，在弹出窗口中设置“公共项目”选项，然后选择“保存”。  

1. 在项目中选择一个笔记本来运行。 例如， Azure 认知服务存储库中的每个笔记本都是其自己的自包含快速入门。 下图显示在添加认知服务 API 订阅密钥并将搜索词“puppies”更改为“bunnies”后，使用 BingImageSearchAPI 笔记本的结果：

    ![运行从 GitHub 克隆的 Jupyter 笔记本](media/quickstarts/clone-notebook-result.png)

1. 运行完笔记本以后，请选择“文件” > “关闭并停止”，以便关闭笔记本及其浏览器窗口。

1. 若要共享项目中的单个笔记本，请右键单击该笔记本，然后选择“复制链接”（键盘快捷方式：y）：

    ![用于复制单个笔记本的链接的上下文菜单命令](media/quickstarts/copy-link-to-individual-notebook.png)

1. 若要编辑笔记本以外的文件，请右键单击该项目中的文件并选择“编辑文件”（键盘快捷方式：i）。 默认操作“运行”（键盘快捷方式：r）仅显示文件内容且不允许编辑。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [教程：创建并运行 Jupyter 笔记本以执行线性回归](tutorial-create-run-jupyter-notebook.md)
