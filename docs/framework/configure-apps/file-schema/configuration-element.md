---
title: <configuration> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921248"
---
# <a name="configuration-element"></a>\<configuration> – element

Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.

**\<configuration>**

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

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | Určuje zásadu vazby sestavení na úrovni konfigurace.|
| [**\<startup>** Schéma nastavení](./startup/index.md) | Všechny elementy ve schématu nastavení spouštění. |
| [**\<runtime>** Schéma nastavení](./runtime/index.md) | Všechny elementy ve schématu nastavení modulu runtime. |
| [**\<system.runtime.remoting>** Schéma nastavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Všechny elementy ve schématu nastavení vzdálené komunikace. |
| [**\<system.Net>** Schéma nastavení](./network/index.md) | Všechny elementy ve schématu nastavení sítě. |
| [**\<cryptographySettings>** Schéma nastavení](./cryptography/index.md) | Všechny elementy ve schématu nastavení kryptografie. |
| [**\<configuration>** Schéma oddílů](configuration-sections-schema.md) | Všechny elementy ve schématu nastavení konfiguračního oddílu. |
| [Trasování a ladění schématu nastavení](./trace-debug/index.md) | Všechny prvky ve schématu nastavení trasování a ladění. |
| [Schéma nastavení konfigurace ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Všechny prvky ve schématu konfigurace ASP.NET, které zahrnuje prvky pro konfiguraci webů a aplikací ASP.NET. Používá se v souborech *Web. config* . |
| [**\<webServices>** Schéma nastavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Všechny prvky ve schématu nastavení webových služeb. |
| [Schéma nastavení webu](./web/index.md) | Všechny prvky ve schématu nastavení webu, které obsahují prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je služba IIS. Používá se v souborech *ASPNET. config* . |

## <a name="remarks"></a>Poznámky

Každý konfigurační soubor musí obsahovat přesně jeden **\<configuration>** element.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
