---
title: Další nástroje rozhraní příkazového řádku pro .NET Core
description: Přehled dalších nástrojů, které můžete nainstalovat a které podporují a zvyšují funkčnost .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: c885d6f6b0417a80dd6e26afe9572766738c5b4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771970"
---
# <a name="net-core-additional-tools-overview"></a>Přehled dalších nástrojů .NET Core

Tato část kompiluje seznam nástrojů, které podporují a rozšířily funkce .NET Core, kromě nástrojů [rozhraní příkazového řádku (CLI) .NET Core](../tools/index.md) .

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Referenční nástroj webové služby WCF](wcf-web-service-reference-guide.md)

Odkaz na webovou službu WCF (Windows Communication Foundation) je poskytovatel připojené služby sady Visual Studio, který provedl své debutem ve [Visual studiu 2017 verze 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL a vygeneruje zdrojový soubor kompatibilní s .NET Core a definuje třídu proxy WCF s metodami, které můžete použít pro přístup k operacím webové služby.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet – nástroj Svcutil](dotnet-svcutil-guide.md)

Nástroj pro WCF (Windows Communication Foundation) dotnet-Svcutil je .NET Core CLI nástroj, který načítá metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje zdrojový soubor kompatibilní s .NET Core, definování třídy proxy WCF pomocí metod. který můžete použít pro přístup k operacím webové služby.
Nástroj **dotnet-Svcutil** je alternativou k [**webové službě WCF reference**](wcf-web-service-reference-guide.md) k poskytovateli propojené služby sady Visual Studio, který se poprvé dodává se sadou visual Studio 2017 verze 15,5. Nástroj **dotnet-Svcutil** jako nástroj .NET Core CLI je k dispozici pro různé platformy v systémech Linux, MacOS a Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet – Svcutil. XmlSerializer – nástroj](dotnet-svcutil.xmlserializer-guide.md)

Na .NET Framework můžete předem vygenerovat sestavení serializace pomocí nástroje Svcutil. Balíček NuGet-Svcutil. XmlSerializer nabízí podobné funkce rozhraní .NET Core. Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován <xref:System.Xml.Serialization.XmlSerializer>. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátorů XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro .NET Framework je [balíček NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) řešením pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení pro zlepšení výkonu při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.
