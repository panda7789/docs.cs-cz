---
title: Další nástroje .NET core
description: Přehled další nástroje, které podporují a rozšiřovat funkce .NET Core.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: a842224a76962a9d6db820149a75f1255204e9b7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728560"
---
# <a name="net-core-additional-tools"></a>Další nástroje .NET core

Tato část zkompiluje o seznam nástrojů, které podporují a rozšířit funkci .NET Core kromě [.NET Core rozhraní příkazového řádku (CLI)](..\tools\index.md) nástroje.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Odkaz na službu WCF webové nástroje](wcf-web-service-reference-guide.md)

Odkaz webové služby WCF (Windows Communication Foundation) je poskytovatel připojené služby Visual Studio, který provedené v jeho debut [Visual Studio 2017 verze 15,5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). Tento nástroj získává metadata z webové služby v aktuálním řešení v umístění v síti, nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídu proxy WCF pomocí metody, které můžete použít pro přístup k operace webové služby.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Nástroj dotnet svcutil WCF](dotnet-svcutil-guide.md)

Nástroj dotnet svcutil WCF (Windows Communication Foundation) je nástroj .NET Core rozhraní příkazového řádku, který získává metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídu proxy WCF pomocí metody používané pro přístup k operace webové služby. **Dotnet svcutil** nástroj je alternativní možnost [ **odkaz na službu WCF Web** ](/dotnet/core/additional-tools/wcf-web-service-reference-guide) Visual Studio připojené poskytovatele služeb, které první dodaný pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj pro .NET Core rozhraní příkazového řádku, je k dispozici platformy Linux, systému macOS a systému Windows.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je řešení pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou součástí sestavení, které chcete zvýšit výkon při spuštění serializace XML při serializaci nebo zrušte serializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.