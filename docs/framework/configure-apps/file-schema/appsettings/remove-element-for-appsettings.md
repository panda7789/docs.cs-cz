---
title: <remove> – element pro element <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: cf9a34e47b70aaff12b29b9c5cf944d5bb15fee9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258718"
---
# <a name="remove-element-for-appsettings"></a>\<Odebrat > – element pro \<appSettings >

Odebere vlastní nastavení aplikace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atribut

|         | Popis |
| ------- | ----------- |
| **key** | Požadovaný atribut.<br><br>Určuje název klíč k odebrání. |

### <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci. |

## <a name="child-elements"></a>Podřízené prvky

Žádná

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
