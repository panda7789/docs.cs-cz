---
title: Testování v .NET Core jednotky
description: Testování částí se nikdy nebyl snazší. V tématu Jak používat v .NET Core a .NET Standard projektů testování částí.
keywords: Rozhraní .NET, testování částí .NET core, .NET Standard
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.workload:
- dotnetcore
ms.openlocfilehash: cb78a66a3a6a7158a86a76d62e5230c75b51a416
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>V .NET Core a .NET Standard testování částí

.NET core má byly navrženy s testovatelnosti na paměti, aby testů jednotek pro vaše aplikace je jednodušší než kdy dřív. Tento článek představuje stručně jednotka testy (a jak se liší od jiných druhů testů). Propojené prostředky ukazují, jak přidat projekt testu do řešení a potom spusťte testy jednotek pomocí příkazového řádku nebo Visual Studio.

Podporuje rozhraní .NET 2.0 základní [standardní rozhraní .NET 2.0](../../standard/net-standard.md). Závisí na .NET Standard a bude fungovat v typy projektu knihovny použitá k předvedení jednotky testování v této části.

Od verze rozhraní .NET 2.0 jádra, existují šablony projektů testů jednotek pro Visual Basic a F # a také C#.

## <a name="getting-started-with-testing"></a>Začínáme s testování

Sada automatizovaných testů s je jedním z nejlepší způsobů, jak zajistit, že softwarová aplikace nemá co jeho autoři určené na práci. Existují různé druhy testů pro softwarové aplikace, včetně integrace testy, webové testy, zátěžových testů a dalších. Testy jednotek, které testování jednotlivých softwarové součásti nebo metody jsou nejnižší úrovni testy. Testování částí měli jenom otestovat kód v rámci ovládacího prvku pro vývojáře a neměli testování aspekty infrastruktury, jako jsou databáze, systémy souborů nebo síťovým prostředkům. Testování částí lze zapisovat pomocí [testovací řízené vývoj (TDD)](http://deviq.com/test-driven-development/), nebo mohou být přidány do stávajícího kódu pro potvrzení jeho správnost. V obou případech se musí být malé, dobře s názvem a rychlé, vzhledem k tomu, že v ideálním případě chcete být schopni spustit stovky je před odesláním změn do úložiště sdíleného kódu projektu.

> [!NOTE]
> Vývojáři často potýkat s tím zajistily se objevuje s funkčním názvy pro své testovací třídy a metody. Jako počáteční bod, následuje produktový tým ASP.NET [tyto konvence](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Pokud zápis testů částí, dávejte pozor, nejsou omylem zavést závislosti na infrastruktuře. Tyto mívají aby testy pomalejší a více křehká a proto by se mělo vyhradit pro integraci testy. Tyto závislosti skrytá můžete vyhnout v kódu aplikace pomocí následujících [explicitní závislosti Princip](http://deviq.com/explicit-dependencies-principle/) a pomocí [vkládání závislostí](/aspnet/core/fundamentals/dependency-injection) k vyžádání závislostmi z rozhraní. Také můžete zabránit testů jednotek v samostatných projektu testů integrace a ujistěte se, že vaše projektu testování částí nemá odkazy na nebo závislosti na infrastruktuře balíčky.

Další informace o testování v projektech .NET Core jednotky:

Projektů testování částí pro rozhraní .NET Core jsou podporovány pro [C#](../../csharp/index.md), [F #](../../fsharp/index.md) a [jazyka Visual Basic](../../visual-basic/index.md). Můžete také zvolit [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) a [Mstestu](https://github.com/Microsoft/vstest-docs).

Další informace o těchto kombinace v těchto kurzů:

* Vytváření testů jednotek pomocí [ *XUnit* a *C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-dotnet-test.md).
* Vytváření testů jednotek pomocí [ *NUnit* a *C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-nunit.md).
* Vytváření testů jednotek pomocí [ *Mstestu* a *C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-mstest.md).
* Vytváření testů jednotek pomocí [ *XUnit* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Vytváření testů jednotek pomocí [ *NUnit* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-nunit.md).
* Vytváření testů jednotek pomocí [ *Mstestu* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-mstest.md).
* Vytváření testů jednotek pomocí [ *XUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Vytváření testů jednotek pomocí [ *NUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-nunit.md).
* Vytváření testů jednotek pomocí [ *Mstestu* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-mstest.md).

Můžete vybrat různé jazyky pro vaše knihovny tříd a vaše jednotkové testování knihovny. Dozvíte, jak pomocí kombinace a porovnávání názorné postupy odkazuje výše.

* Visual Studio Enterprise nabízí skvělý testování nástroje pro .NET Core. Podívejte se na [Live testování částí](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Další informace.
* Další příklady a další informace o tom, jak pomocí filtrování testovací selektivní jednotky, najdete v části [spouštění testů jednotek selektivní](selective-unit-tests.md), nebo [zahrnutí a vyloučení testů pomocí sady Visual Studio](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods).
* Týmem XUnit zápisem kurz, který ukazuje [použití xUnit s .NET Core a Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).
