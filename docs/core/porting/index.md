---
title: Port kód z rozhraní .NET Framework do .NET Core
description: Vysvětlení procesu přenosem a zjišťování nástroje, které vám můžou pomoct při přenášení do rozhraní .NET Framework projektu .NET Core.
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: 5c7cd8b01672e71b0db7255dad23d994a95ce532
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170038"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Přeneste kód z rozhraní .NET Framework do .NET Core

Pokud máte kód, který běží na rozhraní .NET Framework, může zajímat příliš spouštění kódu v rozhraní .NET Core. Tady je přehled procesu přenosem a seznam nástroje vám můžou pomoct při přenesení kódu až po .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenos

To je proces, doporučujeme že je provést při přenášení projektu .NET Core. Každý krok procesu se budeme věnovat jednotlivě podrobněji v dalších článcích.

1. Identifikujte a účtu pro vašeho závislostí třetích stran.

   Tento krok zahrnuje pochopení, co závislostí třetích stran se, jak jsou závislé na nich, jak a zkontrolujte, zda také spustit na .NET Core a kroky můžete provést v případě, že ne. Také popisuje, jak můžete migrovat vaše závislosti přes [PackageReference](/nuget/consume-packages/package-references-in-project-files) formátu, který se používá v .NET Core.

2. Přesměrovat všechny projekty, které chcete port pro cílové rozhraní .NET Framework 4.7.2 nebo vyšší.

   Tento krok zajistí, že když .NET Core nepodporuje dané rozhraní API, můžete použít rozhraní API alternativy cílů specifické pro rozhraní .NET Framework.

3. Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) analyzovat vaše sestavení a vývoj plánu na port na základě jejích výsledků.

   Nástroj Analyzátor přenositelnosti rozhraní API analyzuje zkompilovaným sestavením a generuje sestavu, která zobrazuje souhrn vyšší úrovně přenositelnost a přehled každé rozhraní API používáte, není k dispozici v rozhraní .NET Core. Můžete použít tuto sestavu spolu s analýzu vašeho základu kódu pro jak budete přeneste kód přes při vytváření plánu.

4. Přeneste kód testy.

   Přenos aplikací .NET Core je takto významná změna do vašeho základu kódu, se důrazně doporučujeme zobrazíte testy přenést, tak, aby jako přeneste kód prostřednictvím je možné spustit testy. MSTest, xUnit a NUnit podporovat .NET Core.

5. Spuštění vašeho plánu pro přenos!

## <a name="tools-to-help"></a>Nástroje, které pomáhají

Následující seznam obsahuje nástroje že mohou být užitečné používat během procesu přenosem:

* .NET portability Analyzeru - [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), sada nástrojů, který může vygenerovat sestavu jak přenosného kódu je mezi rozhraní .NET Framework a .NET Core pomocí Rozpis sestavení podle problémů. Další informace najdete v tématu [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md).
* Analyzátor rozhraní API .NET – A Roslyn analyzátor, který hledá potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání rozhraní API nepoužívané. Další informace najdete v tématu [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md).
* Reverzního vyhledávání balíčků – A [užitečné webová služba](https://packagesearch.azurewebsites.net) , který umožňuje hledat typ a vyhledat balíčky obsahující tohoto typu.

Kromě toho se můžete pokusit port menší řešení nebo na formát souboru projektu .NET Core s jednotlivými projekty [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) nástroj.

> [!WARNING] 
> CsprojToVs2017 je nástroj třetí strany. Neexistuje žádná záruka, že bude fungovat pro všemi svými projekty a může to způsobit drobné změny v chování, které nejvíc potřebujete. CsprojToVs2017 by měla sloužit jako _počáteční bod_ , který automatizuje základní akce, které je možné automatizovat. Není zaručené řešení migrace formáty souborů projektu.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
