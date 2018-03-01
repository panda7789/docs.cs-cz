---
title: "&lt;Přidat&gt; element pro &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d080a7c63ddda0577e66d2e7ddd433c7fd5fdbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-appsettings"></a>\<Přidat > elementu pro \<appSettings >

Přidá vlastní nastavení aplikace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Přidat >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Atributy

|           | Popis |
| --------- | ----------- |
| **klíč**   | Požadovaný atribut.<br><br>Určuje název klíč k přidání. |
| **value** | Požadovaný atribut.<br><br>Určuje hodnotu klíč k přidání. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat vlastní konfigurace nastavení pro název aplikace:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
