---
title: Portování do .NET Core v rozhraní .NET Framework
description: Vysvětlení procesu přenosem a zjišťování nástroje, které vám můžou pomoct při přenášení do rozhraní .NET Framework projektu .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: d273b3abe46de59aa55b5b9a531d3c572a065124
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835389"
---
# <a name="porting-to-net-core-from-net-framework"></a>Portování do .NET Core v rozhraní .NET Framework

Pokud máte kód spuštěný na rozhraní .NET Framework, může zajímat spouštění kódu v .NET Core 1.0.  Tento článek obsahuje přehled procesu přenosem a seznam nástrojů, které vám můžou pomoct při přenášení do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenos

Doporučený postup pro přenesení následuje následující sérii kroků.  Každá z těchto částí procesu se budeme věnovat jednotlivě podrobněji v dalších článcích.

1. Identifikujte a účtu pro vašeho závislostí třetích stran.

   To bude zahrnovat porozumění jaké závislostí třetích stran se, jak jsou závislé na nich, jak a zjistěte, jestli jsou také běží na .NET Core a kroky můžete provést v případě ne.
   
2. Přesměrovat všechny projekty, které chcete port pro cílové rozhraní .NET Framework 4.6.2.

   Tím se zajistí, že můžete použít alternativy rozhraní API pro .NET Framework specifické cíle v případech, kdy .NET Core nemůže zajišťovat podporu pro dané rozhraní API.
   
3. Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) analyzovat vaše sestavení a vývoj plánu na port na základě jejích výsledků.

   Nástroj Analyzátor přenositelnosti rozhraní API analyzuje zkompilovaným sestavením a generovat sestavy, která zobrazuje souhrn vyšší úrovně přenositelnost a přehled každé rozhraní API používáte, není k dispozici v rozhraní .NET Core.  Můžete použít tuto sestavu spolu s analýzu vašeho základu kódu pro jak budete přeneste kód přes při vytváření plánu.
   
4. Přeneste kód testy.

   Přenos aplikací .NET Core je velkou změnu do vašeho základu kódu, se důrazně doporučujeme zobrazíte testy přenáší tak, aby jako port kód prostřednictvím je možné spustit testy.  MSTest, xUnit a NUnit podpora .NET Core 1.0 ještě dnes.
   
6. Spuštění vašeho plánu pro přenos!

## <a name="tools-to-help"></a>Nástroje, které pomáhají

Tady je krátký seznam nástrojů, které najdete užitečné:

* NuGet – [pro klienta Nuget](https://dist.nuget.org/index.html) nebo [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Správce balíčků od Microsoftu pro implementace .NET.
* Rozhraní API Portability Analyzeru - [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), sada nástrojů, který může vygenerovat sestavu jak přenosného kódu je mezi rozhraní .NET Framework a .NET Core s Rozpis sestavení podle problémů.  Zobrazit [nástroje, které vám pomohou v procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Další informace.
* Reverzního vyhledávání balíčků – A [užitečné webová služba](https://packagesearch.azurewebsites.net) , který umožňuje hledat typ a vyhledat balíčky obsahující tohoto typu.

## <a name="next-steps"></a>Další kroky

[Analýza závislostí třetích stran.](third-party-deps.md)
   
