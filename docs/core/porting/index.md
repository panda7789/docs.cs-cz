---
title: Portování do .NET Core z rozhraní .NET Framework
description: Princip přenosem a zjistit nástroje, které vás může být užitečná při portování rozhraní .NET Framework projektu na .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f943caff23ddbfcd5c845c9f517d24aea089850
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="porting-to-net-core-from-net-framework"></a>Portování do .NET Core z rozhraní .NET Framework

Pokud máte k dispozici kód spuštěný na rozhraní .NET Framework, může zajímat spuštěním kódu v .NET Core 1.0.  Tento článek obsahuje přehled procesu přenosem a seznam nástroje, které vás může být užitečná při portování do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenosem

Doporučený postup pro přenos zahrnuje následující sérii kroků.  Každou z těchto součástí procesu jsou popsané v podrobněji další články.

1. Identifikovat a účet pro svoje závislosti třetích stran.

   To bude zahrnovat vysvětlení, co vaše třetích stran závislosti jsou, jak jsou závislé na je, jak a zjistěte, zda také běží na .NET Core a postup můžete provést v případě ne.
   
2. Změňte cíl všechny projekty, které chcete port na cílové rozhraní .NET Framework 4.6.2.

   Zajistíte, že můžete použít rozhraní API alternativy pro specifické pro rozhraní .NET Framework cíle v případech, kde .NET Core nepodporuje dané rozhraní API.
   
3. Použití [nástroj Analyzátor přenositelnost rozhraní API](https://github.com/Microsoft/dotnet-apiport/) analyzovat vaše sestavení a vytvořte plán na port, na základě jeho výsledků.

   Nástroj Analyzátor přenositelnost API analyzovat zkompilovaná sestavení a generovat sestavy, která se zobrazují souhrnné informace vysoké úrovně přenositelnost a rozpis každé rozhraní API používáte, není k dispozici na .NET Core.  Můžete použít tuto sestavu spolu s analýzu vašeho základu kódu při vytváření plánu o tom, jak budete prostřednictvím portu vašeho kódu.
   
4. Port testy kódu.

   Portování do .NET Core je velkou změnu do vaší codebase, a proto se důrazně doporučujeme získat testy přesně tak, aby testy můžete spustit jako portu kód přes.  Mstestu, xUnit a NUnit podporovat dnes .NET Core 1.0.
   
6. Spuštění plánu pro přenos!

## <a name="tools-to-help"></a>Nástrojů, které pomůžou

Tady je seznam krátké nástroje, které najdete užitečné:

* NuGet - [klienta Nuget](https://dist.nuget.org/index.html) nebo [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Správce balíčků společnosti Microsoft pro implementace rozhraní .NET.
* Přenositelnost Analyzer API - [nástroj pro příkazový řádek](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), nástrojů, který můžete vygenerovat sestavu, jak přenosné kódu je mezi rozhraní .NET Framework a .NET Core pomocí sestavení podle rozpis těchto problémů.  V tématu [nástrojů můžete v procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Další informace.
* Reverse balíček vyhledávání - A [užitečné webové služby](https://packagesearch.azurewebsites.net) , které umožňuje hledat typ a vyhledejte balíčky, které obsahují typu.

## <a name="next-steps"></a>Další kroky

[Analýza závislostmi třetích stran.](third-party-deps.md)
   
