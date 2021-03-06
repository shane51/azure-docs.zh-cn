---
title: 教程：Azure Active Directory 与 Questetra BPM Suite 集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 和 Questetra BPM Suite 之间配置单一登录。
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 03/27/2019
ms.author: jeedes
ms.openlocfilehash: 13f05005529d3983e042398f5274fd7f981b8c8c
ms.sourcegitcommit: 59f506857abb1ed3328fda34d37800b55159c91d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92516580"
---
# <a name="tutorial-azure-active-directory-integration-with-questetra-bpm-suite"></a>教程：Azure Active Directory 与 Questetra BPM Suite 集成

在本教程中，了解如何将 Questetra BPM Suite 与 Azure Active Directory (Azure AD) 集成。
将 Questetra BPM Suite 与 Azure AD 集成提供以下优势：

* 可以在 Azure AD 中控制谁有权访问 Questetra BPM Suite。
* 可让用户使用其 Azure AD 帐户自动登录到 Questetra BPM Suite（单一登录）。
* 可在中心位置（即 Azure 门户）管理帐户。

如果要了解有关 SaaS 应用与 Azure AD 集成的更多详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](../manage-apps/what-is-single-sign-on.md)。
如果还没有 Azure 订阅，可以在开始前[创建一个免费帐户](https://azure.microsoft.com/free/)。

## <a name="prerequisites"></a>必备条件

若要配置 Azure AD 与 Questetra BPM Suite 的集成，需备齐以下项目：

* 一个 Azure AD 订阅。 如果你没有 Azure AD 环境，可以在[此处](https://azure.microsoft.com/pricing/free-trial/)获取一个月的试用版。
* 已启用 Questetra BPM Suite 单一登录的订阅

## <a name="scenario-description"></a>方案描述

本教程会在测试环境中配置和测试 Azure AD 单一登录。

* Questetra BPM Suite 支持 **SP** 发起的 SSO

## <a name="adding-questetra-bpm-suite-from-the-gallery"></a>从库中添加 Questetra BPM Suite

要配置 Questetra BPM Suite 与 Azure AD 的集成，需要从库中将 Questetra BPM Suite 添加到托管 SaaS 应用列表。

**若要从库中添加 Questetra BPM Suite，请执行以下步骤：**

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”  图标。

    ![“Azure Active Directory”按钮](common/select-azuread.png)

2. 转到“企业应用”，并选择“所有应用”选项   。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

3. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”  按钮。

    ![“新增应用程序”按钮](common/add-new-app.png)

4. 在搜索框中键入 **Questetra BPM Suite** ，在结果面板中选择“Questetra BPM Suite”，然后单击“添加”按钮添加该应用程序。  

     ![结果列表中的“Questetra BPM Suite”](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录

在本部分，我们基于名为 **Britta Simon** 的测试用户来配置并测试 Questetra BPM Suite 的 Azure AD 单一登录。
若要正常使用单一登录，需要在 Azure AD 用户与 Questetra BPM Suite 相关用户之间建立链接关系。

若要配置和测试 Questetra BPM Suite 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configure-azure-ad-single-sign-on)** - 使用户能够使用此功能。
2. **[配置 Questetra BPM Suite 单一登录](#configure-questetra-bpm-suite-single-sign-on)** - 在应用程序端配置单一登录设置。
3. **[创建 Azure AD 测试用户](#create-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
4. **[分配 Azure AD 测试用户](#assign-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
5. **[创建 Questetra BPM Suite 测试用户](#create-questetra-bpm-suite-test-user)** - 在 Questetra BPM Suite 中创建 Britta Simon 的对应用户，并将其关联到其在 Azure AD 中的表示形式。
6. **[测试单一登录](#test-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将在 Azure 门户中启用 Azure AD 单一登录。

若要配置 Questetra BPM Suite 的 Azure AD 单一登录，请执行以下步骤：

1. 在 [Azure 门户](https://portal.azure.com/)中的“Questetra BPM Suite”应用程序集成页上，选择“单一登录”。  

    ![配置单一登录链接](common/select-sso.png)

2. 在 **选择单一登录方法** 对话框中，选择 **SAML/WS-Fed** 模式以启用单一登录。

    ![单一登录选择模式](common/select-saml-option.png)

3. 在“使用 SAML 设置单一登录”页上，单击“编辑”图标以打开“基本 SAML 配置”对话框    。

    ![编辑基本 SAML 配置](common/edit-urls.png)

4. 在“基本 SAML 配置”  部分中，按照以下步骤操作：

    ![Questetra BPM Suite 域和 URL 单一登录信息](common/sp-identifier.png)

    a. 在“登录 URL”文本框中，使用以下模式键入 URL：`https://<subdomain>.questetra.net/saml/SSO/alias/bpm`

    b. 在“标识符(实体 ID)”文本框中，使用以下模式键入 URL：`https://<subdomain>.questetra.net/`

    > [!NOTE]
    > 这些不是实际值。 必须使用实际登录 URL 和标识符更新这些值。 可以从 **Questetra BPM Suite** 公司站点的“SP 信息”部分获取这些值（在本教程中的后面部分进行说明），或者联系 [Questetra BPM Suite 客户端支持团队](https://www.questetra.com/contact/)来获取。 还可以参考 Azure 门户中的“基本 SAML 配置”  部分中显示的模式。

5. 在“使用 SAML 设置单一登录”  页上，在“SAML 签名证书”  部分中，单击“下载”  以根据要求从给定的选项下载 **证书(Base64)** 并将其保存在计算机上。

    ![证书下载链接](common/certificatebase64.png)

6. 在“设置 Questetra BPM Suite”部分，根据要求复制相应的 URL。 

    ![复制配置 URL](common/copy-configuration-urls.png)

    a. 登录 URL

    b. Azure AD 标识符

    c. 注销 URL

### <a name="configure-questetra-bpm-suite-single-sign-on"></a>配置 Questetra BPM Suite 单一登录

1. 在其他 Web 浏览器窗口中，以管理员身份登录到 **Questetra BPM Suite** 公司站点。

2. 在顶部菜单中，单击“系统设置”  。 
   
    ![显示从 Questetra BPM Suite 公司站点选择了“系统设置”的屏幕截图。][10]

3. 若要打开“SingleSignOnSAML”  页，请单击“SSO (SAML)”  。 
   
    ![显示选择了“SSO (SAML)”的屏幕截图。][11]

4. 在 **Questetra BPM Suite** 公司站点的“SP 信息”  部分中，执行以下步骤：

    a. 复制“ACS URL”，然后将其粘贴到 Azure 门户上“基本 SAML 配置”部分的“登录 URL”文本框中。   
    
    b. 复制“实体 ID”，然后将其粘贴到 Azure 门户上“基本 SAML 配置”部分的“标识符”文本框中。   

5. 在 **Questetra BPM Suite** 公司站点上，执行以下步骤： 
   
    ![配置单一登录][15]
   
    a. 选择“启用单一登录”  。
   
    b. 在“实体 ID”文本框中，粘贴从 Azure 门户复制的“Azure AD 标识符”值   。
    
    c. 在“登录 URL”文本框中，粘贴从 Azure 门户复制的“登录 URL”值   。
    
    d. 在“注销 URL”文本框中，粘贴从 Azure 门户复制的“注销 URL”值   。
    
    e. 在“NameID 格式”  文本框中，键入 `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`。

    f. 在记事本中打开从 Azure 门户下载的 Base-64 编码证书，将其内容复制到剪贴板，然后再粘贴到“验证证书”文本框中   。 

    g. 单击“保存”  。

### <a name="create-an-azure-ad-test-user"></a>创建 Azure AD 测试用户 

本部分的目的是在 Azure 门户中创建名为 Britta Simon 的测试用户。

1. 在 Azure 门户的左侧窗格中，依次选择“Azure Active Directory”  、“用户”  和“所有用户”  。

    ![“用户和组”以及“所有用户”链接](common/users.png)

2. 选择屏幕顶部的“新建用户”  。

    ![“新建用户”按钮](common/new-user.png)

3. 在“用户属性”中，按照以下步骤操作。

    ![“用户”对话框](common/user-properties.png)

    a. 在“名称”  字段中，输入 BrittaSimon  。
  
    b. 在“用户名”字段中键入 brittasimon@yourcompanydomain.extension。 例如： BrittaSimon@contoso.com

    c. 选中“显示密码”复选框，然后记下“密码”框中显示的值  。

    d. 单击“创建”。 

### <a name="assign-the-azure-ad-test-user"></a>分配 Azure AD 测试用户

在本部分中，通过授予 Britta Simon 访问 Questetra BPM Suite 的权限，允许她使用 Azure 单一登录。

1. 在 Azure 门户中，依次选择“企业应用程序”、“所有应用程序”、“Questetra BPM Suite”。   

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

2. 在应用程序列表中，选择“Questetra BPM Suite”  。

    ![“应用程序”列表中的“Questetra BPM Suite”链接](common/all-applications.png)

3. 在左侧菜单中，选择“用户和组”  。

    ![“用户和组”链接](common/users-groups-blade.png)

4. 单击“添加用户”按钮，然后在“添加分配”对话框中选择“用户和组”。

    ![“添加分配”窗格](common/add-assign-user.png)

5. 在“用户和组”  对话框中，选择“用户”列表中的 Britta Simon  ，然后单击屏幕底部的“选择”  按钮。

6. 如果你在 SAML 断言中需要任何角色值，请在“选择角色”  对话框中从列表中为用户选择合适的角色，然后单击屏幕底部的“选择”按钮。 

7. 在“添加分配”对话框中，单击“分配”按钮。  

### <a name="create-questetra-bpm-suite-test-user"></a>创建 Questetra BPM Suite 测试用户

本部分的目的是在 Questetra BPM Suite 中创建名为“Britta Simon”的用户。

**若要在 Questetra BPM Suite 中创建名为“Britta Simon”的用户，请执行以下步骤：**

1. 以管理员身份登录到 Questetra BPM Suite 公司站点。

2. 转到“系统设置”>“用户列表”>“新建用户”  。
 
3. 在“新建用户”对话框中，执行以下步骤： 
   
    ![创建测试用户][300] 
   
    a. 在“名称”文本框中，键入用户的 **名称**britta.simon@contoso.com。
   
    b. 在“电子邮件”文本框中，键入用户的 **电子邮件地址**britta.simon@contoso.com。
   
    c. 在“密码”文本框中，键入用户的密码   。
    
    d. 单击“添加新用户”  。

### <a name="test-single-sign-on"></a>测试单一登录 

在本部分中，使用访问面板测试 Azure AD 单一登录配置。

在访问面板中单击“Questetra BPM Suite”磁贴时，应会自动登录到设置了 SSO 的 Questetra BPM Suite。 有关访问面板的详细信息，请参阅 [Introduction to the Access Panel](../user-help/my-apps-portal-end-user-access.md)（访问面板简介）。

## <a name="additional-resources"></a>其他资源

- [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](./tutorial-list.md)

- [Azure Active Directory 的应用程序访问与单一登录是什么？](../manage-apps/what-is-single-sign-on.md)

- [什么是 Azure Active Directory 中的条件访问？](../conditional-access/overview.md)

<!--Image references-->

[10]: ./media/questetra-bpm-suite-tutorial/questera_bpm_suite_03.png
[11]: ./media/questetra-bpm-suite-tutorial/questera_bpm_suite_04.png
[15]: ./media/questetra-bpm-suite-tutorial/questera_bpm_suite_08.png
[300]: ./media/questetra-bpm-suite-tutorial/questera_bpm_suite_11.png