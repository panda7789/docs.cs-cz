---
title: "&lt;konfigurace&gt; – element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 3874a613879d099ede4968b5bce349aefa015a38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-element"></a>\<Konfigurace > elementu

Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.

**\<Konfigurace >**

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

Žádné

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<assemblybinding – >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Určuje sestavení vazby zásady na úrovni konfigurace.|
| [**\<spuštění >** schéma nastavení](~/docs/framework/configure-apps/file-schema/startup/index.md) | Všechny elementy ve schématu nastavení spuštění. |
| [**\<modul runtime >** schéma nastavení](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Všechny elementy ve schématu nastavení modulu runtime. |
| [**\<System.Runtime.Remoting >** schéma nastavení](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | Všechny elementy ve schématu nastavení vzdálené komunikace. |
| [**\<system.Net >** schéma nastavení](~/docs/framework/configure-apps/file-schema/network/index.md) | Všechny elementy ve schématu nastavení sítě. |
| [**\<cryptographySettings – >** schéma nastavení](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Všechny elementy ve schématu kryptografických nastavení. |
| [**\<Konfigurace >** schéma oddílů](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Všechny elementy ve schématu oddílu nastavení konfigurace. |
| [Trasování a ladění schématu nastavení](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | Všechny elementy ve schématu nastavení trasování a ladění. |
| [Schéma nastavení konfigurace technologie ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | Všechny elementy ve schématu konfigurace ASP.NET, který obsahuje prvky konfigurace ASP.NET – webové servery a aplikace. Použít v *Web.config* soubory. |
| [**\<webovým službám >** schéma nastavení](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Všechny elementy ve schématu nastavení webových služeb. |
| [Schéma nastavení webu](~/docs/framework/configure-apps/file-schema/web/index.md) | Všechny elementy ve schéma nastavení webu, který obsahuje prvky pro konfiguraci, jak funguje technologie ASP.NET s hostitelskou aplikaci, například služby IIS. Použít v *soubor aspnet.config* soubory. |

## <a name="remarks"></a>Poznámky

Každý konfigurační soubor musí obsahovat přesně jeden  **\<konfigurace >** element.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
