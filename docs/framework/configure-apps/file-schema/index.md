---
title: Schéma konfiguračního souboru pro rozhraní .NET Framework
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b227ba343db7996d38d5a485b54629a1f4ed28bd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744106"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma konfiguračního souboru pro rozhraní .NET Framework

Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavení zásad pro vaše aplikace. Konfigurační schéma rozhraní .NET Framework se skládá z prvky používané v konfiguračních souborech můžete řídit chování aplikací. Obsah pro tento oddíl odráží schéma hierarchie pro spouštění, modul runtime, sítě a další typy nastavení konfigurace.

Informace o typech, formát a umístění konfigurační soubory, najdete v článku [konfigurace aplikace](~/docs/framework/configure-apps/index.md). Pokud chcete upravit konfigurační soubory, které přímo, seznamte se se souborem XML.

> [!IMPORTANT]
> Značky XML a atributů v konfiguračních souborech jsou malá a velká písmena.

## <a name="in-this-section"></a>V tomto oddílu

[**\<Konfigurace >** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) popisuje `<configuration>` element, který je element nejvyšší úrovně pro všechny konfigurační soubory.

[**\<assemblybinding – >** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) určuje sestavení vazby zásady na úrovni konfigurace.

[**\<linkedconfiguration – >** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Určuje konfigurační soubor pro zahrnout.

[Schéma nastavení spouštění](~/docs/framework/configure-apps/file-schema/startup/index.md) popisuje elementy, které určují, kterou verzi modulu CLR používat.

[Schéma nastavení běhového prostředí](~/docs/framework/configure-apps/file-schema/runtime/index.md) popisuje elementy, které konfiguruje chování vazby a runtime sestavení.

[Schéma nastavení sítě](~/docs/framework/configure-apps/file-schema/network/index.md) popisuje elementy, které určují, jak rozhraní .NET Framework se připojuje k Internetu.

[Schéma nastavení šifrování](~/docs/framework/configure-apps/file-schema/cryptography/index.md) popisuje elementy, které mapování názvů popisný algoritmů na třídy, které implementují kryptografické algoritmy.

[Schéma konfigurace oddílů](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) popisuje elementy slouží k vytvoření a použití konfiguračních oddílů pro vlastní nastavení.

[Trasování a ladění schématu nastavení](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) popisuje elementy, které určují trasování – přepínače a naslouchací procesy.

[Schéma nastavení poskytovatele jazyka a kompilátor](~/docs/framework/configure-apps/file-schema/compiler/index.md) popisuje elementy, které určují kompilátoru konfigurace pro zprostředkovatele dostupný jazyk.

[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) popisuje elementy, které umožňují aplikacím Windows Forms nebo v technologii ASP.NET pro ukládání a načítání nastavení obor aplikace a nastavení uživatele.

[Schéma nastavení aplikace](~/docs/framework/configure-apps/file-schema/appsettings/index.md) obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.

[Webové nastavení schématu](~/docs/framework/configure-apps/file-schema/web/index.md) všechny elementy ve schéma nastavení webu, který obsahuje prvky pro konfiguraci, jak funguje technologie ASP.NET s hostitelskou aplikaci, například služby IIS. Použít v *soubor Aspnet.config* soubory.

[Windows Forms konfigurační schéma](winforms/index.md) všechny elementy v konfiguračním oddílu aplikace Windows Forms, včetně přizpůsobení například více monitorování a vysokou podporu DPI.

[Konfigurační schéma služby WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) všechny elementy, které vám umožní nakonfigurovat aplikace klienta a služby WCF.

[Syntaxe – direktiva WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) popisuje `@ServiceHost` – direktiva, který definuje používané kompilátoru .svc atributy specifické pro stránku.

[Schéma konfigurace WIF](windows-identity-foundation/index.md) všechny elementy schématu konfigurace Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Související oddíly

[Schéma nastavení vzdálené komunikace](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) popisuje elementy, které nakonfigurovat klientské a serverové aplikace, které implementují vzdálenou komunikaci.

[Schéma nastavení ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) popisuje prvky, které řídí chování webových aplikací ASP.NET.

[Webové služby schéma nastavení](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) popisuje elementy, které řídí chování webových služeb ASP.NET a svým klientům.

[Konfigurace aplikací rozhraní .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) popisuje postup konfigurace zabezpečení, sestavení – vazby a vzdálenou komunikaci v rozhraní .NET Framework.
