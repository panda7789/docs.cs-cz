---
title: '&lt;Odebrat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e803561ef20bb17ed7c637eb487027466b65077
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-appsettings"></a>\<Odebrat > elementu pro \<appSettings >

Odebere vlastní nastavení aplikace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Odebrat >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atribut

|         | Popis |
| ------- | ----------- |
| **klíč** | Požadovaný atribut.<br><br>Určuje název klíč k odebrání. |

### <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
