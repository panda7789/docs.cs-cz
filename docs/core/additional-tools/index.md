---
title: Další nástroje .NET core
description: Přehled další nástroje, které podporují a rozšiřovat funkce .NET Core.
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: 2e33cdbcbe9c81e6c3af84f8f2795ee3dc6e28ae
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-additional-tools"></a>Další nástroje .NET core

Tato část zkompiluje o seznam nástrojů, které podporují a rozšířit funkci .NET Core kromě [.NET Core rozhraní příkazového řádku (CLI)](..\tools\index.md) nástroje.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Nástroj odkaz na službu WCF webu](wcf-web-service-reference-guide.md)

Odkaz na službu WCF Web je poskytovatel připojené služby Visual Studio, který provedené v jeho debut [Visual Studio 2017 verze 15,5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). Tento nástroj získává metadata z webové služby v aktuálním řešení v umístění v síti, nebo ze souboru WSDL a vytvoří soubor kompatibilní zdroj .NET Core obsahující kód proxy serveru klienta Windows Communication Foundation (WCF), který můžete použít pro přístup k webu Služba.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serializer Generator](xml-serializer-generator.md)

Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je řešení pro knihovny .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou součástí sestavení, které chcete zvýšit výkon při spuštění serializace XML při serializaci nebo zrušte serializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.