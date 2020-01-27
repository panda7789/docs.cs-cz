---
title: Další nástroje rozhraní příkazového řádku
description: Přehled dalších nástrojů, které můžete nainstalovat a které podporují a zvyšují funkčnost .NET Core.
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 853633f5ef159eee39ed1a8682372d4291a752f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740704"
---
# <a name="net-core-additional-tools-overview"></a>Přehled dalších nástrojů .NET Core

Tato část kompiluje seznam nástrojů, které podporují a rozšířily funkce .NET Core, kromě nástrojů [rozhraní příkazového řádku (CLI) .NET Core](../tools/index.md) .

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[Nástroj pro odinstalaci .NET Core](uninstall-tool.md)

[Nástroj pro odinstalaci .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umožňuje vyčistit sady .NET Core SDK a moduly runtime v systému tak, aby zůstaly jenom zadané verze. K dispozici je kolekce možností, pomocí kterých určíte, které verze se odinstalují.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Referenční nástroj webové služby WCF](wcf-web-service-reference-guide.md)

Odkaz na webovou službu WCF (Windows Communication Foundation) je poskytovatel připojené služby sady Visual Studio, který provedl své debutem ve [Visual studiu 2017 verze 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, do umístění v síti nebo ze souboru WSDL. Vygeneruje zdrojový soubor kompatibilní s .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet – nástroj Svcutil](dotnet-svcutil-guide.md)

Nástroj Svcutil WCF (Windows Communication Foundation) dotnet-je .NET Core CLI nástroj, který načítá metadata z webové služby v síťovém umístění nebo ze souboru WSDL. Vygeneruje zdrojový soubor kompatibilní s .NET Core a definuje třídu proxy WCF pomocí metod, které můžete použít pro přístup k operacím webové služby.

Nástroj **dotnet-Svcutil** je alternativou k [**webové službě WCF reference**](wcf-web-service-reference-guide.md) k poskytovateli propojené služby sady Visual Studio, který se poprvé dodává se sadou visual Studio 2017 verze 15,5. Nástroj **dotnet-Svcutil** , jako nástroj .NET Core CLI, je k dispozici pro různé platformy v systémech Linux, MacOS a Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet – Svcutil. XmlSerializer – nástroj](dotnet-svcutil.xmlserializer-guide.md)

Na .NET Framework můžete předem vygenerovat sestavení serializace pomocí nástroje Svcutil. Balíček NuGet-Svcutil. XmlSerializer nabízí podobné funkce rozhraní .NET Core. Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován <xref:System.Xml.Serialization.XmlSerializer>. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátorů XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro .NET Framework je [balíček NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) řešením pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení pro zlepšení výkonu při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.
