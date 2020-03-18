---
title: Další nástroje
description: Přehled dalších nástrojů, které můžete nainstalovat, které podporují a rozšířit .NET Základní funkce.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451522"
---
# <a name="net-core-additional-tools-overview"></a>Přehled dalších nástrojů .NET Core

Tato část zkompiluje seznam nástrojů, které podporují a rozšiřují funkce .NET Core, kromě rozhraní .NET Core CLI.

## <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj .NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umožňuje vyčistit sady .NET Core SDK a runtimes v systému tak, aby zůstaly pouze zadané verze. K dispozici je kolekce možností, které určují, které verze jsou odinstalovány.

## <a name="net-core-diagnostic-tools"></a>Základní diagnostické nástroje .NET

[čítače dotnet](../diagnostics/dotnet-counters.md) je nástroj pro sledování výkonu pro monitorování stavu první úrovně a sledování výkonu.

[dotnet-dump](../diagnostics/dotnet-dump.md) poskytuje způsob, jak shromažďovat a analyzovat windows a linuxové základní výpisy bez nativníladný ladicí program.

[dotnet-trace](../diagnostics/dotnet-trace.md) shromažďuje data profilování z vaší aplikace, která můžou pomoct ve scénářích, kde potřebujete zjistit, co způsobuje pomalé spouštění aplikace.

## <a name="wcf-web-service-reference-tool"></a>Referenční nástroj webové služby WCF

[WCF](wcf-web-service-reference-guide.md) (Windows Communication Foundation) Web Service Reference tool je poskytovatel služeb připojených k sadě Visual Studio, který debutoval ve [visual studiu 2017 verze 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL. Generuje zdrojový soubor kompatibilní s rozhraním .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet-svcutil nástroj

Nástroj WCF [dotnet-svcutil](dotnet-svcutil-guide.md) je nástroj .NET, který načítá metadata z webové služby v síťovém umístění nebo ze souboru WSDL. Generuje zdrojový soubor kompatibilní s rozhraním .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

Nástroj **dotnet-svcutil** je alternativou k poskytovateli připojených služeb [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio, který byl poprvé dodán s Visual Studio 2017 verze 15.5. Nástroj **dotnet-svcutil** jako nástroj .NET je k dispozici v systémech Linux, macOS a Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil.xmlserializer nástroj

V rozhraní .NET Framework můžete předem vygenerovat sestavení serializace pomocí nástroje svcutil. Nástroj WCF [dotnet-svcutil.xmlserializer](dotnet-svcutil.xmlserializer-guide.md) poskytuje podobné funkce v rozhraní .NET Core. Předem generuje kód serializace jazyka C# pro typy v klientské aplikaci, které jsou používány <xref:System.Xml.Serialization.XmlSerializer>wcf service contract a které mohou být serializovány . To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="xml-serializer-generator"></a>XML Serializer Generator

Podobně jako [generátor serializátorů XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework je [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) řešením pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení ke zlepšení výkonu při spuštění serializace XML při <xref:System.Xml.Serialization.XmlSerializer>serializaci nebo deserializaci objektů těchto typů pomocí .
