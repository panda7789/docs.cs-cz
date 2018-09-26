---
title: Další nástroje .NET core
description: Přehled další nástroje, které podporují a rozšíření funkcí .NET Core.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: c64dddbe36b789a695c2603e78b29b38d8718f95
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208380"
---
# <a name="net-core-additional-tools"></a>Další nástroje .NET core

Tato část sestaví seznam nástrojů, které podporují a rozšíření funkcí .NET Core, kromě [rozhraní příkazového řádku .NET Core (CLI)](../tools/index.md) nástroje.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Nástroj WCF Web Service Reference](wcf-web-service-reference-guide.md)

Odkaz na webovou službu WCF (Windows Communication Foundation) je poskytovatel připojených služeb sady Visual Studio, který k jeho debutem v [Visual Studio 2017 verze 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools). Tento nástroj načte metadata z webové služby v aktuálním řešení, na umístění v síti, nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídy proxy WCF s metodami, které můžete použít pro přístup k operací webové služby.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Nástroj dotnet svcutil WCF](dotnet-svcutil-guide.md)

Nástroj dotnet svcutil WCF (Windows Communication Foundation) je nástroj rozhraní příkazového řádku .NET Core, který načte metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje zdrojový soubor, který je kompatibilní s .NET Core, definování třídy proxy WCF s metodami můžete použít pro přístup k operací webové služby. **Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) poskytovatele služeb, které první dodaný připojená sady Visual Studio pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je řešení pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou obsaženy v sestavení, které chcete zlepšit výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.