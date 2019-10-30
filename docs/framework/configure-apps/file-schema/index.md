---
title: Schéma konfiguračního souboru pro .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039163"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma konfiguračního souboru pro .NET Framework

Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavení zásad pro aplikace. Schéma konfigurace .NET Framework se skládá z prvků, které lze použít v konfiguračních souborech pro řízení chování aplikací. Obsah této části odráží hierarchii schématu pro spuštění, modul runtime, síť a další typy nastavení konfigurace.

Informace o typech, formátech a umístění konfiguračních souborů najdete v tématu [Konfigurace aplikací](../index.md). Pokud chcete upravit konfigurační soubory přímo, Seznamte se s XML.

> [!IMPORTANT]
> Značky a atributy XML v konfiguračních souborech rozlišují velká a malá písmena.

## <a name="in-this-section"></a>V tomto oddílu

[ **\<> elementu konfigurace** ](configuration-element.md)\
Element nejvyšší úrovně pro všechny konfigurační soubory.

[ **\<element > assemblyBinding** ](assemblybinding-element-for-configuration.md)\
Určuje zásadu vazby sestavení na úrovni konfigurace.

[ **\<element > linkedConfiguration** ](linkedconfiguration-element.md)\
Určuje konfigurační soubor, který se má zahrnout.

\ [schématu nastavení spuštění](./startup/index.md)
Prvky, které určují, která verze modulu CLR (Common Language Runtime) se má použít.

\ [schématu nastavení modulu runtime](./runtime/index.md)
Prvky, které konfigurují vazby sestavení a běhové chování.

\ [schématu nastavení sítě](./network/index.md)
Prvky, které určují, jak se .NET Framework připojí k Internetu.

[Nastavení kryptografie\ schématu](./cryptography/index.md)
Prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.

\ [schématu konfiguračních oddílů](configuration-sections-schema.md)
Prvky, které slouží k vytváření a používání konfiguračních oddílů pro vlastní nastavení.

\ [schématu nastavení trasování a ladění](./trace-debug/index.md)
Prvky, které určují přepínače trasování a naslouchací procesy.

\ [schématu nastavení kompilátoru a poskytovatele jazyka](./compiler/index.md)
Prvky, které určují konfiguraci kompilátoru pro poskytovatele dostupných jazyků.

\ [schématu nastavení aplikace](application-settings-schema.md)
Prvky, které umožňují model Windows Forms nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a uživatelem.

\ [schématu nastavení aplikace](./appsettings/index.md)
Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.

\ [schématu webového nastavení](./web/index.md)
Prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je IIS. Používá se v souborech *ASPNET. config* .

\ [schématu konfigurace model Windows Forms](winforms/index.md)
Všechny prvky v části Konfigurace aplikace model Windows Forms, které zahrnují přizpůsobení, jako je například podpora více monitorů a vysokého rozlišení DPI.

\ [schématu konfigurace WCF](./wcf/index.md)
Všechny prvky, které umožňují konfigurovat službu WCF a klientské aplikace.

\ [syntaxe direktiv WCF](./wcf-directive/index.md)
Popisuje direktivu `@ServiceHost`, která definuje atributy specifické pro stránku používané kompilátorem. svc.

\ [schématu konfigurace WIF](windows-identity-foundation/index.md)
Všechny prvky schématu konfigurace Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Související oddíly

[Nastavení vzdálené komunikace\ schématu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))
Popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálenou komunikaci.

\ [schématu nastavení ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))
Popisuje prvky, které řídí chování webových aplikací ASP.NET.

\ [schématu nastavení webových služeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))
Popisuje prvky, které řídí chování webových služeb ASP.NET a jejich klientů.

[Konfigurace aplikací .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
Popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v .NET Framework.
