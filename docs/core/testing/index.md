---
title: Testování částí ve standardu .NET Core a .NET Standard
description: Tento článek poskytuje stručný přehled testování částí pro projekty .NET Core a .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 1263bfe337b9d6609c0ca7df70aa299a61a7f1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78157398"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testování částí ve standardu .NET Core a .NET Standard

.NET Core usnadňuje vytváření testů částí. Tento článek zavádí testování částí a ukazuje, jak se liší od jiných typů testů. Propojené zdroje v dolní části stránky ukazují, jak přidat testovací projekt do vašeho řešení. Po nastavení testovacího projektu budete moci spustit testy částí pomocí příkazového řádku nebo sady Visual Studio.

Pokud testujete **projekt ASP.NET Core,** přečtěte si informace [o testech integrace v ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).

.NET Core 2.0 a novější podporuje [.NET Standard 2.0](../../standard/net-standard.md)a použijeme jeho knihovny k předvedení testů částí.

Můžete použít předdefinované šablony projektu .NET Core 2.0 a novější hospo- testování částí pro C#, F# a Visual Basic jako výchozí bod pro váš osobní projekt.

## <a name="what-are-unit-tests"></a>Co jsou testy částí?

S automatizovanými testy je skvělý způsob, jak zajistit, aby softwarová aplikace dělala to, co její autoři hodlají dělat. Existuje několik typů testů pro softwarové aplikace. Patří mezi ně integrační testy, webové testy, zátěžové testy a další. **Jednotkové testy** testují jednotlivé softwarové komponenty a metody. Testy částí by měly testovat pouze kód v rámci ovládacího prvku vývojáře. Neměly by testovat obavy týkající se infrastruktury. Mezi problémy infrastruktury patří databáze, systémy souborů a síťové prostředky.

Také mějte na paměti, že existují osvědčené postupy pro psaní testů. Například [Vývoj řízený testováním (TDD)](https://deviq.com/test-driven-development/) je při testování částí před kód, který je určen ke kontrole. TDD je jako vytvoření osnovy pro knihu, než ji napíšeme. Je určen k pomoci vývojářům psát jednodušší, čitelnější a efektivní kód.

> [!NOTE]
> Tým ASP.NET tyto [konvence](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) pomáhá vývojářům přijít s dobrými názvy pro testovací třídy a metody.

Snažte se nezavádět závislosti na infrastruktuře při psaní testů částí. Ty dělají testy pomalé a křehké a měly by být vyhrazeny pro integrační testy. Těmto závislostem v aplikaci se můžete vyhnout podle [zásadexplicitních závislostí](https://deviq.com/explicit-dependencies-principle/) a použitím [vkládání závislostí](/aspnet/core/fundamentals/dependency-injection). Můžete také zachovat testy částí v samostatném projektu z integračních testů. Tím zajistíte, že váš projekt testování částí nemá odkazy nebo závislosti na balíčcích infrastruktury.

## <a name="next-steps"></a>Další kroky

Další informace o testování částí v projektech .NET Core:

Testovací projekty jednotky .NET Core jsou podporovány pro:

- [C #](../../csharp/index.yml)
- [F #](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml)

Můžete si také vybrat mezi:

- [xJednotka](https://xunit.github.io)
- [NJednotka](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Další informace naleznete v následujících návodech:

- Vytvořte testy částí pomocí [ *xUnit* a *C#* pomocí rozhraní CLI jádra .NET](unit-testing-with-dotnet-test.md).
- Vytvořte testy částí pomocí [ *NUnit* a *C#* pomocí rozhraní CLI jádra .NET](unit-testing-with-nunit.md).
- Vytvořte testy částí pomocí [ *MSTest* a *C#* pomocí rozhraní CLI jádra .NET](unit-testing-with-mstest.md).
- Vytvořte testy částí pomocí [ *xUnit* a *F#* pomocí rozhraní CLI jádra .NET](unit-testing-fsharp-with-dotnet-test.md).
- Vytvořte testy částí pomocí [ *NUnit* a *F#* pomocí rozhraní CLI jádra .NET](unit-testing-fsharp-with-nunit.md).
- Vytvořte testy částí pomocí [ *MSTest* a *F#* pomocí rozhraní CLI jádra .NET](unit-testing-fsharp-with-mstest.md).
- Vytvořte testy částí pomocí [ *xUnit* a *Visual Basic* pomocí rozhraní PŘÍKAZU KONT jádra .NET](unit-testing-visual-basic-with-dotnet-test.md).
- Vytvořte testy částí pomocí [ *NUnit* a *Visual Basic* pomocí rozhraní PŘÍKAZU KONT jádra .NET](unit-testing-visual-basic-with-nunit.md).
- Vytvořte testy částí pomocí [ *mstest* a *visual basic* s rozhraním příkazového příkazu .NET Core CLI](unit-testing-visual-basic-with-mstest.md).

Další informace naleznete v následujících článcích:

- Visual Studio Enterprise nabízí skvělé testovací nástroje pro .NET Core. Další informace najdete v [živém testování částí](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu.](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)
- Další informace o spuštění testů selektivních částí naleznete v [tématu Spuštění testů selektivních částí](selective-unit-tests.md)nebo [zahrnutí a vyloučení testů pomocí sady Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [Použití jednotky xUnit s rozhraními .NET Core a visual studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
