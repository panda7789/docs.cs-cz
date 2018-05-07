---
title: '&lt;Vymazat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 525818309ddc142fdb3ad65ce841ea58c1d635a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clear-element-for-appsettings"></a>\<Clear > elementu pro \<appSettings >

Vymaže vlastní nastavení aplikace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo jakékoli jiné informace o konfiguraci vlastní aplikace. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
