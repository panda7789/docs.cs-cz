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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921248"
---
# <a name="configuration-element"></a>\<element > Konfigurace

Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.

**\<> Konfigurace**

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
| [ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md) | Určuje zásadu vazby sestavení na úrovni konfigurace.|
| [schéma nastavení **> po spuštění \<** ](./startup/index.md) | Všechny elementy ve schématu nastavení spouštění. |
| [schéma nastavení **> modulu runtime \<** ](./runtime/index.md) | Všechny elementy ve schématu nastavení modulu runtime. |
| [**System. Runtime. Vzdálená > Nastavení schématu \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Všechny elementy ve schématu nastavení vzdálené komunikace. |
| [schéma nastavení **> systému .NET \<** ](./network/index.md) | Všechny elementy ve schématu nastavení sítě. |
| [schéma nastavení > cryptographySettings  **\<** ](./cryptography/index.md) | Všechny elementy ve schématu nastavení kryptografie. |
| [schéma oddílů > Konfigurace  **\<** ](configuration-sections-schema.md) | Všechny elementy ve schématu nastavení konfiguračního oddílu. |
| [Trasování a ladění schématu nastavení](./trace-debug/index.md) | Všechny prvky ve schématu nastavení trasování a ladění. |
| [Schéma nastavení konfigurace ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Všechny prvky ve schématu konfigurace ASP.NET, které zahrnuje prvky pro konfiguraci webů a aplikací ASP.NET. Používá se v souborech *Web. config* . |
| [schéma nastavení > služeb pro WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Všechny prvky ve schématu nastavení webových služeb. |
| [Schéma nastavení webu](./web/index.md) | Všechny prvky ve schématu nastavení webu, které obsahují prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je služba IIS. Používá se v souborech *ASPNET. config* . |

## <a name="remarks"></a>Poznámky

Každý konfigurační soubor musí obsahovat právě jeden  **\<element konfigurace >** .

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
