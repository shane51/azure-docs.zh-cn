---
title: 如何删除用户对 Azure Active Directory 中的应用程序的访问权限
description: 了解如何在 Azure Active Directory 中删除用户对应用程序的访问权限
services: active-directory
author: kenwith
manager: celestedg
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.topic: how-to
ms.date: 11/02/2020
ms.author: kenwith
ms.openlocfilehash: 28b31d98f283dc957927ab2a35f0ab95bf066473
ms.sourcegitcommit: 8e7316bd4c4991de62ea485adca30065e5b86c67
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94654110"
---
# <a name="how-to-remove-a-users-access-to-an-application"></a>如何删除用户对应用程序的访问权限

本文介绍如何删除用户对应用程序的访问权限。

## <a name="i-want-to-remove-a-specific-users-or-groups-assignment-to-an-application"></a>我要删除特定用户或组到应用程序的分配

若要删除用户或组对应用程序的分配，请按照[在 Azure Active Directory 中从企业应用删除用户或组分配](./assign-user-or-group-access-portal.md)一文中所列的步骤进行操作。

## <a name="i-want-to-disable-all-access-to-an-application-for-every-user"></a>我要禁用每个用户对应用程序的所有访问权限

若要禁用所有用户对应用程序的登录，请遵循[在 Azure Active Directory 中对企业应用禁用用户登录](./disable-user-sign-in-portal.md)一文中所列出的步骤。

## <a name="i-want-to-delete-an-application-entirely"></a>我要彻底删除应用程序

[有关应用程序管理的快速入门系列](delete-application-portal.md)包括从 Azure Active Directory 租户中删除应用程序的指南。

## <a name="i-want-to-disable-all-future-user-consent-operations-to-any-application"></a>我要禁用用户未来针对应用程序的所有同意操作

针对整个目录禁用用户同意操作，可防止最终用户同意任何应用程序。 管理员仍可以代表用户授予许可。 有关应用程序同意的详细信息，以及可能希望或可能不希望这样做的原因，请阅读[了解用户和管理员同意](../develop/howto-convert-app-to-be-multi-tenant.md#understand-user-and-admin-consent)。 此外，请参阅[权限和许可](../develop/v2-permissions-and-consent.md)。

若要 **禁用用户未来在整个目录中执行的所有同意操作**，请根据以下说明进行操作：

1.  打开 [**Azure 门户**](https://portal.azure.com/)，并以“全局管理员”身份登录。

2.  打开“Azure Active Directory 扩展” 

3.  单击导航菜单中的 " **企业应用程序** "。

5.  单击 " **用户设置**"。

6.  将“用户可以允许应用代表他们访问公司数据”切换为“否”并单击“保存”按钮。


## <a name="next-steps"></a>后续步骤

[管理对应用的访问](what-is-access-management.md)