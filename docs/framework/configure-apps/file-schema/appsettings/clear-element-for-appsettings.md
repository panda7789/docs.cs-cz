---
title: <clear> – element pro element <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0b6a48d1fdab3cbccf40aaa77731a658f533eeba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278575"
---
# <a name="clear-element-for-appsettings"></a>\<Vymazat > – element pro \<appSettings >

Vymaže nastavení vlastní aplikace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Vymazat >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Atributy

Žádná

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací konfigurace vlastní aplikace. |

## <a name="child-elements"></a>Podřízené prvky

Žádná

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
