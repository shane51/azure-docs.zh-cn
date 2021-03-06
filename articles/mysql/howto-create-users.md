---
title: 创建数据库和用户 - Azure Database for MySQL
description: 本文介绍如何创建新的用户帐户，以与 Azure Database for MySQL 服务器进行交互。
author: savjani
ms.author: pariks
ms.service: mysql
ms.topic: how-to
ms.date: 10/1/2020
ms.openlocfilehash: 2e934ede193d6efb9cc795c6b63cb485b88f792e
ms.sourcegitcommit: 6ab718e1be2767db2605eeebe974ee9e2c07022b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2020
ms.locfileid: "94541413"
---
# <a name="create-databases-and-users-in-azure-database-for-mysql"></a>在 Azure Database for MySQL 中创建数据库和用户

[!INCLUDE[applies-to-single-flexible-server](includes/applies-to-single-flexible-server.md)]

本文介绍如何在 Azure Database for MySQL 中创建用户。

> [!NOTE]
> **无偏差通信**
>
> Microsoft 支持多样化的包容性环境。 本文包含对单词 slave 的引用。 Microsoft 的[无偏差通信风格指南](https://github.com/MicrosoftDocs/microsoft-style-guide/blob/master/styleguide/bias-free-communication.md)将其视为排他性单词。 本文中使用的词是为了保持一致，因为它是当前显示在软件中的单词。 如果软件更新后删除了该单词，则本文也将更新以保持一致。
>

首次创建 Azure Database for MySQL 服务器时，需要提供服务器管理员用户名和密码。 有关详细信息，请参阅此[快速入门](quickstart-create-mysql-server-database-using-azure-portal.md)。 你可以在 Azure 门户中确定你的服务器管理员用户名。

服务器管理员用户具有以下权限： 

   选择、插入、更新、删除、创建、放置、重载、处理、引用、索引、更改、显示数据库、创建临时表、锁定表、执行、复制从属、复制客户端、创建视图、显示视图、创建例程、更改例程、创建用户、事件、触发器


创建 Azure Database for MySQL 服务器后，你可以使用第一个服务器管理员帐户来创建其他用户，并授予这些用户管理员访问权限。 你还可以使用服务器管理员帐户来创建只能访问各个数据库架构的权限较低的用户。

> [!NOTE]
> 不支持 SUPER 权限和 DBA 角色。 请在“限制”一文中查看[权限](concepts-limits.md#privileges--data-manipulation-support)，以了解服务中不支持的权限。
>
> 服务器不支持 `validate_password` 和 `caching_sha2_password` 等密码插件。


## <a name="to-create-a-database-with-a-non-admin-user-in-azure-database-for-mysql"></a>若要在 Azure Database for MySQL 中使用非管理员用户创建数据库

1. 获取连接信息和管理员用户名。
   若要连接到数据库服务器，需提供完整的服务器名称和管理员登录凭据。 可以在 Azure 门户的服务器“概览”页或“属性”页中轻松地找到服务器名称和登录信息 。

2. 使用管理员帐户和密码连接到你的数据库服务器。 使用你的首选客户端工具，如 MySQL Workbench、mysql.exe 或 HeidiSQL。
   
   如果你不确定如何连接，请参阅 [连接和查询单一服务器的数据](./connect-workbench.md) 或 [连接和查询数据以用于灵活的服务器](./flexible-server/connect-workbench.md)。

3. 编辑并运行下面的 SQL 代码。 将占位符 `db_user` 替换为所需的新用户名。 将占位符 `testdb` 替换为数据库名称。

   此 SQL 代码创建名为 testdb 的新数据库。 然后，它在 MySQL 服务中创建新用户，并将所有权限授予该用户的新数据库架构 (testdb.\*)。

   ```sql
   CREATE DATABASE testdb;

   CREATE USER 'db_user'@'%' IDENTIFIED BY 'StrongPassword!';

   GRANT ALL PRIVILEGES ON testdb . * TO 'db_user'@'%';

   FLUSH PRIVILEGES;
   ```

4. 验证数据库中的授予：

   ```sql
   USE testdb;

   SHOW GRANTS FOR 'db_user'@'%';
   ```

5. 登录到服务器，指定选定的数据库并使用新用户名和密码。 此示例显示了 mysql 命令行。 使用此命令时，系统会提示你输入用户的密码。 使用你自己的服务器名称、数据库名称和用户名。

   # <a name="single-server"></a>[单一服务器](#tab/single-server)

   ```azurecli-interactive
   mysql --host mydemoserver.mysql.database.azure.com --database testdb --user db_user@mydemoserver -p
   ```
   # <a name="flexible-server"></a>[灵活服务器](#tab/flexible-server)

   ```azurecli-interactive
   mysql --host mydemoserver.mysql.database.azure.com --database testdb --user db_user -p
   ```
 ---

## <a name="to-create-additional-admin-users-in-azure-database-for-mysql"></a>若要在 Azure Database for MySQL 中创建其他管理员用户

1. 获取连接信息和管理员用户名。
   若要连接到数据库服务器，需提供完整的服务器名称和管理员登录凭据。 可以在 Azure 门户的服务器“概览”页或“属性”页中轻松地找到服务器名称和登录信息 。

2. 使用管理员帐户和密码连接到你的数据库服务器。 使用你的首选客户端工具，如 MySQL Workbench、mysql.exe 或 HeidiSQL。
   
   如果你不确定如何连接，请参阅[使用 MySQL Workbench 连接和查询数据](./connect-workbench.md)。

3. 编辑并运行下面的 SQL 代码。 将占位符 `new_master_user` 替换为新用户名。 此语法会将所有数据库架构 ( *.* ) 上列出的权限授予该用户名（本示例中的 `new_master_user`）。

   ```sql
   CREATE USER 'new_master_user'@'%' IDENTIFIED BY 'StrongPassword!';

   GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, PROCESS, REFERENCES, INDEX, ALTER, SHOW DATABASES, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, REPLICATION SLAVE, REPLICATION CLIENT, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, CREATE USER, EVENT, TRIGGER ON *.* TO 'new_master_user'@'%' WITH GRANT OPTION;

   FLUSH PRIVILEGES;
   ```

4. 验证授予：

   ```sql
   USE sys;

   SHOW GRANTS FOR 'new_master_user'@'%';
   ```

## <a name="azure_superuser"></a>azure_superuser

所有 Azure Database for MySQL 服务器都是使用名为“azure_superuser”的用户创建的。 这是由 Microsoft 创建的系统帐户，用于管理服务器以执行监视、备份和其他定期维护。 待命工程师还可以使用此帐户在发生证书身份验证事件期间访问服务器，并且必须使用实时 (JIT) 进程请求访问。

## <a name="next-steps"></a>后续步骤

针对新用户计算机的 IP 地址打开防火墙，使其能够连接：
- [在单一服务器上创建和管理防火墙规则](howto-manage-firewall-using-portal.md) 
- [ 在灵活的服务器上创建和管理防火墙规则](flexible-server/how-to-connect-tls-ssl.md)

有关用户帐户管理的详细信息，请参阅 MySQL 产品文档，了解[用户帐户管理](https://dev.mysql.com/doc/refman/5.7/en/access-control.html)、[GRANT 语法](https://dev.mysql.com/doc/refman/5.7/en/grant.html)和[权限](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html)。
