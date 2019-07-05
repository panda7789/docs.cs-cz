---
title: Port kód z rozhraní .NET Framework do .NET Core
description: Vysvětlení procesu přenosem a zjišťování nástroje, které vám můžou pomoct při přenášení do rozhraní .NET Framework projektu .NET Core.
author: cartermp
ms.date: 07/03/2019
ms.custom: seodec18
ms.openlocfilehash: 4206907bcee7ff5c71c9898fee4cb6cad02f1696
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569483"
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

Následující seznam obsahuje nástroje že mohou být užitečné používat během procesu přenosem:

* .NET portability Analyzeru - [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), nástroj, který může vygenerovat sestavu je váš kód jak přenosné mezi rozhraní .NET Framework a cílovou platformu .NET Core. Tato sestava obsahuje rozpis sestavení podle typu a rozhraní API chybí na cílové platformě .NET Core. Další informace najdete v tématu [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md). Se doporučuje spustit nástroj .NET Portability Analyzeru, než začnete, přenos, jak vám pomůže identifikovat všechny mezery v chybějící rozhraní API.
* Analyzátor rozhraní API .NET – Roslyn analyzátor, který zjistí standardní rozhraní API .NET, který vyvolá <xref:System.PlatformNotSupportedException> na některých platformách zjistí volání rozhraní API nepoužívané a zjistí, několik dalších potenciální rizika kompatibility pro C# rozhraní API na různých platformách. Další informace najdete v tématu [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md). Tento analyzátor je užitečné, poté, co jste už vytvořili projektu .NET Core k identifikaci rozdíly v chování modulu runtime na různých platformách. 
* Reverzního vyhledávání balíčků – A [užitečné webová služba](https://packagesearch.azurewebsites.net) , který umožňuje hledat typ a vyhledat balíčky obsahující tohoto typu.

Kromě toho se můžete pokusit port menší řešení nebo na formát souboru projektu .NET Core s jednotlivými projekty [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) nástroj.

> [!WARNING] 
> CsprojToVs2017 je nástroj třetí strany. Neexistuje žádná záruka, že bude fungovat pro všemi svými projekty a může to způsobit drobné změny v chování, které nejvíc potřebujete. CsprojToVs2017 by měla sloužit jako _počáteční bod_ , který automatizuje základní akce, které je možné automatizovat. Není zaručené řešení migrace formáty souborů projektu.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)

