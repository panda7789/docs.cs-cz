---
title: Nástroje pro přenos do .NET Core
description: Přečtěte si o některých nástrojích, které můžete použít k portům pro .NET Core.
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795583"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Nástroje pro pomoc s přenosem aplikací do .NET Core

Můžete najít nástroje uvedené v tomto článku, které jsou užitečné při přenosu:

- [Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) – sada nástrojů, který může generovat sestavu způsobu, jakým je váš kód mezi .NET Framework a .NET Core.
  - Jako [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Rozhraní .NET API Analyzer](../../standard/analyzers/api-analyzer.md) – analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro rozhraní API jazyka C# na různých platformách a detekuje volání zastaralých rozhraní API.
- [Try-Convert](https://www.nuget.org/packages/try-convert/) -globální nástroj .NET Core, který může převést projekt nebo celé řešení na sadu .NET SDK, včetně přesunu desktopových aplikací do .NET Core. Nedoporučuje se, pokud máte navázánější sestavení (například vlastní úkoly, cíle nebo importy) a odmítáte mnoho typů projektů, které nejsou kompatibilní s .NET Core.
