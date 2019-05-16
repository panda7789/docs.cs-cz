---
title: Další nástroje rozhraní příkazového řádku .NET core
description: Přehled další nástroje, které můžete nainstalovat, které podporují a rozšíření funkcí .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 75c74c16367bacf66fa2fb56d7666a07f7274aff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631961"
---
# <a name="net-core-additional-tools-overview"></a>Přehled dalších nástrojů pro .NET core

Tato část sestaví seznam nástrojů, které podporují a rozšíření funkcí .NET Core, kromě [rozhraní příkazového řádku .NET Core (CLI)](../tools/index.md) nástroje.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Nástroj WCF Web Service Reference](wcf-web-service-reference-guide.md)

Odkaz na webovou službu WCF (Windows Communication Foundation) je poskytovatel připojených služeb sady Visual Studio, který k jeho debutem v [Visual Studio 2017 verze 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, na umístění v síti, nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídy proxy WCF s metodami, které můžete použít pro přístup k operací webové služby.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Nástroj dotnet svcutil WCF](dotnet-svcutil-guide.md)

Nástroj dotnet svcutil WCF (Windows Communication Foundation) je nástroj rozhraní příkazového řádku .NET Core, který načte metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídy proxy WCF s metodami můžete použít pro přístup k operací webové služby.
**Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) poskytovatele služeb, které první dodaný připojená sady Visual Studio pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[Nástroj pro dotnet svcutil.xmlserializer WCF](dotnet-svcutil.xmlserializer-guide.md)

Na rozhraní .NET Framework můžete předběžně generovat sestavení serializace pomocí nástroje svcutil. Balíček NuGet dotnet svcutil.xmlserializer poskytuje podobné funkce v rozhraní .NET Core. Předem vygeneruje C# Serializační kód pro typy v klientské aplikaci, které jsou používány kontraktu služby WCF a, který lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je řešení pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou obsaženy v sestavení, které chcete zlepšit výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.
