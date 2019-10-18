---
title: Testování částí v .NET Core a .NET Standard
description: Tento článek poskytuje stručný přehled testování částí pro projekty .NET Core a .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 006ccf0370f8014e5021275c4d38cc50bf1c076f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522908"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testování částí v .NET Core a .NET Standard

Rozhraní .NET Core usnadňuje vytváření testů jednotek. Tento článek zavádí testy jednotek a ukazuje, jak se liší od jiných druhů testů. Propojené prostředky v dolní části stránky ukazují, jak přidat testovací projekt do vašeho řešení. Po nastavení testovacího projektu budete moci spouštět testy jednotek pomocí příkazového řádku nebo sady Visual Studio.

Pokud testujete projekt **ASP.NET Core** , přečtěte si téma [testy integrace v ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).

.NET Core 2,0 a novější podporuje [.NET Standard 2,0](../../standard/net-standard.md)a my použijeme své knihovny k předvedení testů jednotek.

Můžete použít integrované šablony projektu .NET Core 2,0 a novější pro C# F# a Visual Basic jako výchozí bod pro svůj osobní projekt.

## <a name="what-are-unit-tests"></a>Co jsou testy jednotek?

Automatizované testy jsou skvělým způsobem, jak zajistit, aby softwarová aplikace měla své záměry dělat. Pro softwarové aplikace existuje několik typů testů. Patří mezi ně integrační testy, webové testy, zátěžové testy a další. **Testování částí testuje jednotlivé** softwarové komponenty a metody. Testy jednotek by měly testovat pouze kód v rámci ovládacího prvku vývojáře. Neměly by se týkat testovací infrastruktury. Mezi aspekty infrastruktury patří databáze, souborové systémy a síťové prostředky. 

Pamatujte také na to, že jsou osvědčené postupy pro psaní testů. Například [Vývoj řízený testováním (TDD)](https://deviq.com/test-driven-development/) je při zápisu jednotkového testu před kódem, který je určen ke kontrole. TDD je jako vytvoření osnovy pro knihu předtím, než ji napíšeme. Je určena k tomu, aby vývojářům usnadnil psaní jednodušších, čitelnějších a efektivních kódu. 

> [!NOTE]
> Tým ASP.NET řídí [tyto konvence](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) , které vývojářům pomůžou pocházet s dobrými názvy testovacích tříd a metod.

Při zápisu testů jednotek se nepovedlo zavést závislosti na infrastruktuře. Tyto testy jsou pomaleji a poměrně křehký a měly by být rezervovány pro integrační testy. Pomocí [principu explicitní závislosti](https://deviq.com/explicit-dependencies-principle/) a [vložení závislostí](/aspnet/core/fundamentals/dependency-injection)se můžete vyhnout těmto závislostem ve vaší aplikaci. Testy jednotek můžete také zachovat v samostatném projektu z testů Integration. Tím zajistíte, že projekt testů jednotek nebude mít odkazy na balíčky infrastruktury ani závislosti.

## <a name="next-steps"></a>Další kroky

Další informace o testování částí v projektech .NET Core:

Projekty testů jednotek .NET Core jsou podporované pro:

- [C#](../../csharp/index.md)
- [F#](../../fsharp/index.md)
- [Visual Basic](../../visual-basic/index.md) 

Můžete si také vybrat:

- [xUnit](https://xunit.github.io) 
- [NUnit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Další informace najdete v následujících návodech:

- Vytvářejte testy jednotek pomocí [ *xUnit* a *C#* .NET Core CLI](unit-testing-with-dotnet-test.md).
- Vytvářejte testy jednotek pomocí [ *NUnit* a *C#* .NET Core CLI](unit-testing-with-nunit.md).
- Vytvářejte testy jednotek pomocí [ *MSTest* a *C#* .NET Core CLI](unit-testing-with-mstest.md).
- Vytvářejte testy jednotek pomocí [ *xUnit* a *F#* .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).
- Vytvářejte testy jednotek pomocí [ *NUnit* a *F#* .NET Core CLI](unit-testing-fsharp-with-nunit.md).
- Vytvářejte testy jednotek pomocí [ *MSTest* a *F#* .NET Core CLI](unit-testing-fsharp-with-mstest.md).
- Vytvářejte testy jednotek pomocí [ *xUnit* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).
- Vytvářejte testy jednotek pomocí [ *NUnit* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-nunit.md).
- Vytvářejte testy jednotek pomocí [ *MSTest* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-mstest.md).

Další informace najdete v následujících článcích:

- Visual Studio Enterprise nabízí skvělé testovací nástroje pro .NET Core. Další informace najdete [Live Unit Testing](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) .
- Další informace o tom, jak spustit selektivní testy jednotek, najdete v tématu [spuštění selektivních testů jednotek](selective-unit-tests.md)nebo [zahrnutí a vyloučení testů v aplikaci Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [Jak používat xUnit s .NET Core a sadou Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
