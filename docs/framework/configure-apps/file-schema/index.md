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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039163"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma konfiguračního souboru pro .NET Framework

Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavení zásad pro aplikace. Schéma konfigurace .NET Framework se skládá z prvků, které lze použít v konfiguračních souborech pro řízení chování aplikací. Obsah této části odráží hierarchii schématu pro spuštění, modul runtime, síť a další typy nastavení konfigurace.

Informace o typech, formátech a umístění konfiguračních souborů najdete v tématu [Konfigurace aplikací](../index.md). Pokud chcete upravit konfigurační soubory přímo, Seznamte se s XML.

> [!IMPORTANT]
> Značky a atributy XML v konfiguračních souborech rozlišují velká a malá písmena.

## <a name="in-this-section"></a>V této části

[**\<configuration>** Objekt](configuration-element.md)\
Element nejvyšší úrovně pro všechny konfigurační soubory.

[**\<assemblyBinding>** Objekt](assemblybinding-element-for-configuration.md)\
Určuje zásadu vazby sestavení na úrovni konfigurace.

[**\<linkedConfiguration>** Objekt](linkedconfiguration-element.md)\
Určuje konfigurační soubor, který se má zahrnout.

[Schéma nastavení spouštění](./startup/index.md)\
Prvky, které určují, která verze modulu CLR (Common Language Runtime) se má použít.

[Schéma nastavení modulu runtime](./runtime/index.md)\
Prvky, které konfigurují vazby sestavení a běhové chování.

[Schéma nastavení sítě](./network/index.md)\
Prvky, které určují, jak se .NET Framework připojí k Internetu.

[Schéma nastavení kryptografie](./cryptography/index.md)\
Prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.

[Schéma konfiguračních oddílů](configuration-sections-schema.md)\
Prvky, které slouží k vytváření a používání konfiguračních oddílů pro vlastní nastavení.

[Nastavení trasování a ladění – schéma](./trace-debug/index.md)\
Prvky, které určují přepínače trasování a naslouchací procesy.

[Schéma nastavení kompilátoru a poskytovatele jazyka](./compiler/index.md)\
Prvky, které určují konfiguraci kompilátoru pro poskytovatele dostupných jazyků.

[Schéma nastavení aplikace](application-settings-schema.md)\
Prvky, které umožňují model Windows Forms nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a uživatelem.

[Schéma nastavení aplikace](./appsettings/index.md)\
Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.

[Schéma nastavení webu](./web/index.md)\
Prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je IIS. Používá se v souborech *ASPNET. config* .

[Schéma konfigurace model Windows Forms](winforms/index.md)\
Všechny prvky v části Konfigurace aplikace model Windows Forms, které zahrnují přizpůsobení, jako je například podpora více monitorů a vysokého rozlišení DPI.

[Schéma konfigurace WCF](./wcf/index.md)\
Všechny prvky, které umožňují konfigurovat službu WCF a klientské aplikace.

[Syntaxe direktivy WCF](./wcf-directive/index.md)\
Popisuje `@ServiceHost` direktivu, která definuje atributy specifické pro stránku používané kompilátorem. svc.

[Schéma konfigurace WIF](windows-identity-foundation/index.md)\
Všechny prvky schématu konfigurace Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Související oddíly

[Schéma nastavení vzdálené komunikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\
Popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálenou komunikaci.

[Schéma nastavení ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\
Popisuje prvky, které řídí chování webových aplikací ASP.NET.

[Schéma nastavení webových služeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\
Popisuje prvky, které řídí chování webových služeb ASP.NET a jejich klientů.

[Konfigurace aplikací .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
Popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v .NET Framework.
