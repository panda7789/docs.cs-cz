---
title: Testování jednotek v .NET Core a .NET Standard
description: Tento článek poskytuje stručný přehled o testování jednotek pro projekty .NET Core a .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 3fdacd5beb2c6cbfc631d58e99a8741f7a6b233c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243972"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testování jednotek v .NET Core a .NET Standard

.NET core umožňuje snadno vytvořit testy jednotek. Tento článek představuje testování částí a ukazuje, jak se liší od jiných typů testů. Propojené prostředky v dolní části stránky ukazují, jak přidat do svého řešení projekt testu. Po nastavení projektu testu bude moct spustit testování částí pomocí příkazového řádku nebo Visual Studio.

.NET core 2.0 a novějších verzích podporuje [.NET Standard 2.0](../../standard/net-standard.md), a budeme používat jeho knihovny k předvedení testování částí.

Budete moct používat integrované .NET Core 2.0 a novější šablony projektů testů jednotek pro C#, F# a Visual Basic jako výchozí bod pro váš osobní projekt.

## <a name="what-are-unit-tests"></a>Co jsou testy jednotek?

Automatizované testy je skvělý způsob, jak Ujistěte se, že softwarové aplikace dělá, co autorů, že má udělat. Existují různé druhy testů pro softwarové aplikace. Patří mezi ně integrační testy, testy webu, zátěžových testů a dalších. **Testy jednotek** testování jednotlivých softwarových komponent a metody. Testy jednotek by měl pouze testování kódu v rámci ovládacího prvku pro vývojáře. Testují by neměl starostí o infrastrukturu. Starostí o infrastrukturu zahrnují databáze, systémy souborů a síťové prostředky. 

Mějte na paměti, že jsou také osvědčené postupy pro psaní testů. Například [testování řízeného vývoje (TDD)](https://deviq.com/test-driven-development/) je při testování částí zápisu před kódem je určená ke kontrole. TDD je stejná jako předtím, než jsme napsali vytvoření přehledu pro knihy. Smyslem je pomoci vývojářům při psaní kódu jednodušší, lépe čitelný a efektivní. 

> [!NOTE]
> Pomocí následujícího team ASP.NET [Tato konvence](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) , což vývojářům umožňuje najít správné názvy pro testovací třídy a metody.

Pokuste se zavedení závislostí na infrastruktuře při psaní testů jednotek. Tyto proveďte testy pomalé a křehký a by měl být vyhrazen pro testy integrace. Tyto závislosti ve své aplikaci můžete vyhnout podle [explicitní závislosti Princip](https://deviq.com/explicit-dependencies-principle/) a pomocí [injektáž závislostí](/aspnet/core/fundamentals/dependency-injection). Testování částí lze také zachovat v samostatném projektu z testů integrace. Tím se zajistí, že projektu jednotkového testu nemá odkazy nebo závislosti na balíčky infrastruktury.

## <a name="next-steps"></a>Další kroky

Další informace o testování jednotek v projektech .NET Core:

Projekty testů jednotek .NET core jsou podporované pro:
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

Můžete také zvolit mezi:
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/vstest-docs)

Další informace najdete v následujících návodech:

* Vytvoření testování částí pomocí [ *xUnit* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-mstest.md).
* Vytvoření testování částí pomocí [ *xUnit* a *F#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *F#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *F#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-mstest.md).
* Vytvoření testování částí pomocí [ *xUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-mstest.md).

Další informace najdete v následujících článcích:

* Visual Studio Enterprise nabízí skvělé testovací nástroje pro .NET Core. Podívejte se na [Live Unit Testing](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Další informace.
* Další informace o tom, jak spouštění selektivních testů jednotek, naleznete v tématu [spouštění selektivních testů jednotek](selective-unit-tests.md), nebo [zahrnutí a vyloučení testy pomocí sady Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* [Jak pomocí .NET Core a Visual Studio xUnit](https://xunit.github.io/docs/getting-started-dotnet-core.html).
