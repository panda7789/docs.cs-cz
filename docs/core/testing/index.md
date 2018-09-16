---
title: Testování jednotek v .NET Core
description: Testování částí nebylo nikdy jednodušší. Najdete informace o použití testování jednotek v projektech .NET Core a .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 4a1d880da796aac40da93ca2513b6163200ca3c1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676451"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testování jednotek v .NET Core a .NET Standard

.NET core s testovatelností na paměti, byly navržené tak, aby vytváření testů jednotek pro vaše aplikace je jednodušší než kdy dřív. Tento článek stručně představuje jednotky testů (a jak se liší od jiných typů testů). Propojené prostředky ukazují, jak přidat do svého řešení projekt testu a pak spusťte testování částí pomocí příkazového řádku nebo Visual Studio.

.NET core 2.0 podporuje [.NET Standard 2.0](../../standard/net-standard.md). Knihovny použité k předvedení testování jednotek v této části využívají .NET Standard a bude fungovat v i ostatní typy projektů.

Od verze rozhraní .NET Core 2.0, existují šablony projektů testů jednotek pro C#, F # a Visual Basic.

## <a name="getting-started-with-testing"></a>Začínáme s testováním

S sada automatických testů je jedním z nejlepších způsobů Ujistěte se, že softwarové aplikace dělá, co autorů určené na práci. Existují různé druhy testů pro softwarové aplikace, včetně testů integrace, webové testy, testy zatížení a dalších. Testy jednotek, které testují jednotlivé softwarové komponenty nebo metody jsou nejnižší úrovni testy. Testy jednotek by měl pouze testování kódu v rámci ovládacího prvku pro vývojáře a by neměl testu starostí o infrastrukturu, jako jsou databáze, systémy souborů nebo síťovým prostředkům. Testy jednotek jde zapsat pomocí [testu řízeného vývoje (TDD)](http://deviq.com/test-driven-development/), nebo je možné je přidat k existujícímu kódu k potvrzení jeho správnost. V obou případech se musí být malé, dobře pojmenované a rychlé, protože v ideálním případě ale chcete být schopni spustit stovky je před odesláním změn do úložiště projektu sdíleného kódu.

> [!NOTE]
> Vývojáři se často potýkají s naráželi s dobrým názvy pro jejich testovací třídy a metody. Jako výchozí bod, produktový tým ASP.NET následuje [Tato konvence](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Při psaní testů jednotek, dbejte na to, že nezpůsobíte omylem závislosti na infrastruktuře. Tyto jsou obvykle provádět testy pomalejší a větší křehká a proto by se mělo vyhradit pro testy integrace. Vyhnete tyto skryté závislosti v kódu aplikace pomocí následujících [explicitní závislosti Princip](http://deviq.com/explicit-dependencies-principle/) a pomocí [injektáž závislostí](/aspnet/core/fundamentals/dependency-injection) k vyžádání závislosti z rozhraní framework. Můžete také ponechat testování částí v samostatném projektu z testů integrace a ujistěte se, že projektu jednotkového testu nemá odkazy nebo závislosti na balíčky infrastruktury.

Další informace o testování jednotek v projektech .NET Core:

Projekty testů jednotek pro .NET Core podporují [jazyka C#](../../csharp/index.md), [F #](../../fsharp/index.md) a [jazyka Visual Basic](../../visual-basic/index.md). Můžete také zvolit [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) a [MSTest](https://github.com/Microsoft/vstest-docs).

Informace o najdete v těchto kurzech tyto kombinace:

* Vytvoření testování částí pomocí [ *xUnit* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *jazyka C#* pomocí rozhraní příkazového řádku .NET Core](unit-testing-with-mstest.md).
* Vytvoření testování částí pomocí [ *xUnit* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *F #* pomocí rozhraní příkazového řádku .NET Core](unit-testing-fsharp-with-mstest.md).
* Vytvoření testování částí pomocí [ *xUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Vytvoření testování částí pomocí [ *NUnit* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-nunit.md).
* Vytvoření testování částí pomocí [ *MSTest* a *jazyka Visual Basic* pomocí rozhraní příkazového řádku .NET Core](unit-testing-visual-basic-with-mstest.md).

Můžete použít různé jazyky pro knihovny tříd a jednotky testování knihovny. Dozvíte se, jak kombinace a porovnávání návody odkazuje výše.

* Visual Studio Enterprise nabízí skvělé testovací nástroje pro .NET Core. Podívejte se na [Live Unit Testing](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) Další informace.
* Další informace a příklady, jak používat filtrování testů selektivní jednotky najdete v tématu [spouštění selektivních testů jednotek](selective-unit-tests.md), nebo [zahrnutí a vyloučení testy pomocí sady Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* Tým xUnit zapsala kurz, který ukazuje [použití xUnit s .NET Core a Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).
