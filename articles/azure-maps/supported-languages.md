---
title: 本地化支持 | Microsoft Azure Maps
description: 查看哪些区域 Azure Maps 支持地图、搜索、路由、天气和流量事件等服务。 了解如何设置 View 参数。
author: anastasia-ms
ms.author: v-stharr
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: azure-maps
services: azure-maps
manager: philmea
ms.openlocfilehash: a6664b5a2c0c6b4de2435ee5c8bb29f63560c342
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "88037688"
---
# <a name="localization-support-in-azure-maps"></a>Azure Maps 中的本地化支持

Azure Maps 支持多种语言和视图，具体取决于国家/地区。 本文提供了受支持的语言和视图来帮助指导你实现 Azure Maps。


## <a name="azure-maps-supported-languages"></a>Azure Maps 支持的语言

Azure Maps 已采用多种语言对其服务进行了本地化。 下表提供了每项服务支持的语言代码。  
  

| ID         | 名称                   |  地图 | 搜索 | 路由 | 天气 | 交通事故 | JS 地图控件 |
|------------|------------------------|:-----:|:------:|:-------:|:--------:|:-----------------:|:--------------:|
| af-ZA      | 南非荷兰语              |       |    ✓   |    ✓    |         |                   |                |
| ar-SA      | 阿拉伯语                 |   ✓   |    ✓   |    ✓    |    ✓      |         ✓         |        ✓       |
| bn-BD      | 孟加拉语（孟加拉国）    |       |       |         |     ✓    |                   |                |
| bn-IN      | 孟加拉语（印度）         |       |       |         |     ✓    |                   |                |
| bs-BA      | 波斯尼亚语                 |       |       |         |     ✓    |                   |                |
| eu-ES      | 巴斯克语                 |       |    ✓   |         |         |                   |                |
| bg-BG      | 保加利亚语              |   ✓   |    ✓   |    ✓    |     ✓     |                   |        ✓       |
| ca-ES      | 加泰罗尼亚语                |       |    ✓   |         |    ✓      |                   |                |
| zh-HanS    | 中文(简体)   |       |  zh-CN |         |     zh-CN   |                   |                |
| zh-HanT    | 中文(香港特别行政区)  |  |   |    |    zh-HK   |                   |           |
| zh-HanT    | 中文（台湾）  | zh-TW |  zh-TW |  zh-TW  |    zh-TW   |                   |      zh-TW     |
| hr-HR      | 克罗地亚语               |       |    ✓   |         |    ✓      |                   |                |
| cs-CZ      | 捷克语                  |   ✓   |    ✓   |    ✓    |    ✓      |         ✓         |        ✓       |
| da-DK      | 丹麦语                 |   ✓   |    ✓   |    ✓    |     ✓     |         ✓         |        ✓       |
| nl-BE      | 荷兰语（比利时）        |       |    ✓   |         |      ✓    |                   |                |
| nl-NL      | 荷兰语（荷兰）    |   ✓   |    ✓   |    ✓    |     ✓     |         ✓         |        ✓       |
| en-AU      | 英语（澳大利亚）    |   ✓   |    ✓   |    ✓    |     ✓     |         ✓         |        ✓       |
| en-NZ      | 英语（新西兰）  |   ✓   |    ✓   |    ✓    |     ✓     |         ✓         |        ✓       |
| en-GB      | 英语（英国） |   ✓   |    ✓   |    ✓    |     ✓     |         ✓         |        ✓       |
| zh-CN      | 英语（美国）          |   ✓   |    ✓   |    ✓    |      ✓    |         ✓         |        ✓       |
| et-EE      | 爱沙尼亚语               |       |    ✓   |         |      ✓    |         ✓         |                |
| fil-PH     | 菲律宾语               |       |       |         |     ✓    |                   |                |
| fi-FI      | 芬兰语                |   ✓   |    ✓   |    ✓    |      ✓    |         ✓         |        ✓       |
| fr-FR      | 法语                 |   ✓   |    ✓   |    ✓    |      ✓    |         ✓         |        ✓       |
| fr-CA      | 法语（加拿大）      |       |    ✓   |         |     ✓     |                   |                |
| gl-ES      | 加利西亚语               |       |    ✓   |         |         |                   |                |
| de-DE      | 德语                 |   ✓   |    ✓   |    ✓    |   ✓      |         ✓         |        ✓       |
| el-GR      | 希腊语                  |   ✓   |    ✓   |    ✓    |    ✓     |         ✓         |        ✓       |
| gu-IN      | 古吉拉特语                |       |       |         |     ✓    |                   |                |
| he-IL      | 希伯来语                 |       |    ✓   |         |     ✓    |         ✓         |                |
| hi-IN      | Hindi                  |       |        |         |     ✓    |                   |                |
| hu-HU      | 匈牙利语              |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| is-IS      | 冰岛语              |       |       |         |     ✓    |                   |                |
| id-ID      | 印度尼西亚语             |   ✓   |    ✓    |    ✓    |     ✓    |         ✓         |        ✓       |
| it-IT      | 意大利语                |   ✓   |    ✓   |    ✓    |      ✓   |         ✓         |        ✓       |
| ja-JP      | 日语               |       |        |         |     ✓    |                   |                |
| kn-IN      | 卡纳达语                |       |       |         |     ✓    |                   |                |
| kk-KZ      | 哈萨克语                 |       |    ✓   |         |     ✓    |                   |                |
| ko-KR      | 韩语                 |   ✓   |        |    ✓    |     ✓    |                   |        ✓       |
| es-419     | 拉丁美洲西班牙语 |       |    ✓   |         |         |                   |                |
| lv-LV      | 拉脱维亚语                |       |    ✓   |         |     ✓    |         ✓         |                |
| lt-LT      | 立陶宛语             |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| mk-MK      | 马其顿语             |       |       |         |     ✓    |                   |                |
| ms-MY      | 马来语(拉丁语系)          |   ✓   |    ✓   |    ✓    |    ✓   |                   |        ✓       |
| mr-IN      | 马拉地语                 |       |       |         |     ✓    |                   |                |
| nb-NO      | 书面挪威语       |   ✓   |    ✓   |    ✓    |      ✓   |         ✓         |        ✓       |
| NGT        | 非特定真实语言 - 本地脚本中所有区域的官方语言（如果可用） |   ✓     |        |         |       |        |      ✓          |
| NGT-Latn   | 非特定真实语言 - 拉丁语外来语。 将使用拉丁语脚本（如果可用） |   ✓     |        |         |         |                |        ✓         |
| pl-PL      | 波兰语                 |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| pt-BR      | 葡萄牙语（巴西）    |   ✓   |    ✓   |    ✓    |      ✓   |                   |        ✓       |
| pt-PT      | 葡萄牙语(葡萄牙)  |   ✓   |    ✓   |    ✓    |      ✓   |         ✓         |        ✓       |
| pa-IN      | 旁遮普语                 |       |       |         |     ✓    |                   |                |
| ro-RO      | 罗马尼亚语               |       |    ✓    |         |     ✓    |         ✓         |                |
| ru-RU      | 俄语                |   ✓   |    ✓   |    ✓    |      ✓   |         ✓         |        ✓       |
| sr-Cyrl-RS | 塞尔维亚语（西里尔）     |       |   sr-RS  |         |    sr-RS     |                   |                |
| sr-Latn-RS | 塞尔维亚语（拉丁）        |       |       |         |     sr-latn    |                   |                |
| sk-SK      | 斯洛伐克语             |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| sl-SL      | 斯洛文尼亚语              |   ✓   |    ✓   |    ✓    |     ✓    |                   |        ✓       |
| es-ES      | 西班牙语                |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| es-MX      | 西班牙语（墨西哥）       |   ✓   |        |    ✓    |     ✓    |                   |        ✓       |
| sv-SE      | 瑞典语                |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| ta-IN      | 泰米尔语（印度）                 |       |       |         |     ✓    |                   |                |
| te-IN      | 泰卢固语（印度）                 |       |       |         |     ✓    |                   |                |
| th-TH      | 泰语                   |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| tr-TR      | 土耳其语                |   ✓   |    ✓   |    ✓    |     ✓    |         ✓         |        ✓       |
| uk-UA      | 乌克兰语               |       |    ✓   |         |     ✓    |                   |                |
| ur-PK      | 乌尔都语                 |       |       |         |     ✓    |                   |                |
| uz-Latn-UZ | 乌兹别克语                 |       |       |         |     ✓    |                   |                |
| vi-VN      | 越南语             |       |    ✓   |         |      ✓    |                  |                |


## <a name="azure-maps-supported-views"></a>Azure Maps 支持的视图

> [!Note]
> 我们于 2019 年 8 月 1 日在下列国家/地区发布了 Azure Maps：
>  * 阿根廷
>  * 印度
>  * 摩洛哥
>  * 巴基斯坦
>
> 2019 年 8 月 1 日之后，“视图”参数将定义上述新的国家/地区返回的地图内容。 Azure Maps 的“视图”参数（也称为“用户区域参数”）是一个两字母组成的 ISO-3166 国家/地区代码，它将显示该国家/地区的正确地图，其中指定了通过 Azure Maps 服务返回哪组地理位置存在争议的内容，包括地图上显示的边界和标签。 

对于你的服务正在使用的 REST API 和 SDK，请确保根据需要设置“视图”参数。
  

### <a name="rest-apis"></a>Rest Api
  
确保已根据需要设置“视图”参数。 “视图”参数指定了通过 Azure Maps 服务返回哪组地理位置存在争议的内容。 

受影响 Azure Maps REST 服务：
    
 * 获取地图图块
 * 获取地图图像 
 * 获取模糊搜索
 * 获取 POI 搜索
 * 获取 POI 类别搜索
 * 获取附近搜索
 * 获取地址搜索
 * 获取结构化搜索地址
 * 获取反向地址搜索
 * 获取交叉路口反向地址搜索
 * 发布在几何图形中的搜索
 * 发布地址搜索批量预览
 * 发布反向地址搜索批量预览
 * 发布沿路线搜索
 * 发布模糊搜索批量预览

 
### <a name="sdks"></a>SDK

请确保已根据需要设置“视图”参数，并且你具有最新版本的 Web SDK 和 Android SDK。 受影响的 SDK：

 * Azure Maps Web SDK
 * Azure Maps Android SDK

默认情况下，“视图”参数设置为“统一”，即使你未在请求中定义它也是如此。 确定你的用户的位置。 然后，为该位置正确设置“视图”参数。 或者，可设置“View=Auto”，这将根据请求的 IP 地址返回地图数据。  Azure Maps 中的“视图”参数在使用时必须遵守适用法律，包括提供你有权通过 Azure Maps 访问的地图、图像和其他数据及第三方内容的国家/地区所规定的地图相关法律。


下表提供了受支持的视图。

| 视图         | 说明                            |  地图 | 搜索 | JS 地图控件 |
|--------------|----------------------------------------|:-----:|:------:|:--------------:|
| AE           | 阿拉伯联合酋长国（阿拉伯视图）    |   ✓   |        |     ✓          |
| AR           | 阿根廷（阿根廷视图）           |   ✓   |    ✓   |     ✓          |
| BH           | 巴林（阿拉伯视图）                 |   ✓   |        |     ✓          |
| IN           | 印度（印度视图）                    |   ✓   |   ✓     |     ✓          |
| IQ           | 伊拉克（阿拉伯视图）                    |   ✓   |        |     ✓          |
| JO           | 约旦（阿拉伯视图）                  |   ✓   |        |     ✓          |
| KW           | 科威特（阿拉伯视图）                  |   ✓   |        |     ✓          |
| LB           | 黎巴嫩（阿拉伯视图）                 |   ✓   |        |     ✓          |
| MA           | 摩洛哥（摩洛哥视图）                |   ✓   |   ✓     |     ✓          |
| OM           | 阿曼（阿拉伯视图）                    |   ✓   |        |     ✓          |
| PK           | 巴基斯坦（巴基斯坦视图）              |   ✓   |    ✓    |     ✓          |
| PS           | 巴勒斯坦权力机构（阿拉伯视图）    |   ✓   |        |     ✓          |
| QA           | 卡塔尔（阿拉伯视图）                   |   ✓   |        |     ✓          |
| SA           | 沙特阿拉伯（阿拉伯视图）            |   ✓   |        |     ✓          |
| SY           | 叙利亚（阿拉伯视图）                   |   ✓   |        |     ✓          |
| YE           | 也门（阿拉伯视图）                   |   ✓   |        |     ✓          |
| Auto         | 根据请求的 IP 地址返回地图数据。|   ✓   |    ✓   |     ✓          |
| 统一      | 统一视图（其他）                  |   ✓   |   ✓     |     ✓          |
