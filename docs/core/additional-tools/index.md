---
title: Další nástroje
description: Přehled dalších nástrojů, které můžete nainstalovat a které podporují a zvyšují funkčnost .NET Core.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: f7bfa660f7521adf4950d5bbdd59628bb88cca4d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557929"
---
# <a name="net-core-additional-tools-overview"></a>Přehled dalších nástrojů .NET Core

Tato část kompiluje seznam nástrojů, které podporují a rozšířily funkce .NET Core, kromě .NET Core CLI.

## <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj pro odinstalaci .NET Core](https://github.com/dotnet/cli-lab/releases) ( `dotnet-core-uninstall` ) umožňuje vyčistit sady .NET Core SDK a moduly runtime v systému tak, aby zůstaly jenom zadané verze. K dispozici je kolekce možností, pomocí kterých určíte, které verze se odinstalují.

## <a name="net-core-diagnostic-tools"></a>Diagnostické nástroje .NET Core

[dotnet-Counters](../diagnostics/dotnet-counters.md) je nástroj pro monitorování výkonu, který slouží k monitorování stavu první úrovně a vyšetřování výkonu.

[dotnet-dump](../diagnostics/dotnet-dump.md) poskytuje způsob, jak shromažďovat a analyzovat základní výpisy paměti Windows a Linux bez nativního ladicího programu.

[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) poskytuje způsob, jak shromáždit výpisy paměti (GC) pro živé procesy .NET.

[dotnet – trasování](../diagnostics/dotnet-trace.md) shromažďuje data profilace z vaší aplikace, která vám pomůžou ve scénářích, kdy potřebujete zjistit, co způsobí, že aplikace běží pomalu.

## <a name="wcf-web-service-reference-tool"></a>Referenční nástroj webové služby WCF

[Referenční nástroj webové služby](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) je poskytovatel připojeného poskytovatele služby Visual Studio, který provedl své debutem ve [Visual studiu 2017 verze 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, do umístění v síti nebo ze souboru WSDL. Vygeneruje zdrojový soubor kompatibilní s .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet – nástroj Svcutil

Nástroj WCF [dotnet-Svcutil Tool](dotnet-svcutil-guide.md) je nástroj .NET, který načítá metadata z webové služby v síťovém umístění nebo ze souboru WSDL. Vygeneruje zdrojový soubor kompatibilní s .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

Nástroj **dotnet-Svcutil** je alternativou k [**webové službě WCF reference**](wcf-web-service-reference-guide.md) k poskytovateli propojené služby sady Visual Studio, který se poprvé dodává se sadou visual Studio 2017 verze 15,5. Nástroj **dotnet-Svcutil** , jako nástroj .NET, je k dispozici v systémech Linux, MacOS a Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>Nástroj WCF dotnet-svcutil.xmlserializátor

Na .NET Framework můžete předem vygenerovat sestavení serializace pomocí nástroje Svcutil. Nástroj WCF [dotnet-svcutil.xmlserializátor](dotnet-svcutil.xmlserializer-guide.md) nabízí podobné funkce rozhraní .NET Core. Předběžně generuje Serializační kód C# pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován pomocí <xref:System.Xml.Serialization.XmlSerializer> . To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="xml-serializer-generator"></a>XML Serializer Generator

Podobně jako [generátor serializátorů XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro .NET Framework je [ balíček NuGetMicrosoft.Xmlserializátor. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) řešení pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení pro zlepšení výkonu při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer> .
