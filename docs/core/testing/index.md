---
title: Testování částí v .NET Core a .NET Standard
description: Tento článek poskytuje stručný přehled testování částí pro projekty .NET Core a .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703101"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Testování částí v .NET Core a .NET Standard

Rozhraní .NET Core usnadňuje vytváření testů jednotek. Tento článek zavádí testy jednotek a ukazuje, jak se liší od jiných druhů testů. Propojené prostředky v dolní části stránky ukazují, jak přidat testovací projekt do vašeho řešení. Po nastavení testovacího projektu budete moci spouštět testy jednotek pomocí příkazového řádku nebo sady Visual Studio.

Pokud testujete projekt **ASP.NET Core** , přečtěte si téma [testy integrace v ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).

.NET Core 2,0 a novější podporuje [.NET Standard 2,0](../../standard/net-standard.md)a my použijeme své knihovny k předvedení testů jednotek.

Můžete použít integrované šablony projektu .NET Core 2,0 a novějších testů jednotek pro C#, F # a Visual Basic jako výchozí bod pro váš osobní projekt.

## <a name="what-are-unit-tests"></a>Co jsou testy jednotek?

Automatizované testy jsou skvělým způsobem, jak zajistit, aby softwarová aplikace měla své záměry dělat. Pro softwarové aplikace existuje několik typů testů. Patří mezi ně integrační testy, webové testy, zátěžové testy a další. **Testování částí testuje jednotlivé** softwarové komponenty a metody. Testy jednotek by měly testovat pouze kód v rámci ovládacího prvku vývojáře. Neměly by se týkat testovací infrastruktury. Mezi aspekty infrastruktury patří databáze, souborové systémy a síťové prostředky.

Pamatujte také na to, že jsou osvědčené postupy pro psaní testů. Například [Vývoj řízený testováním (TDD)](https://deviq.com/test-driven-development/) je při zápisu jednotkového testu před kódem, který je určen ke kontrole. TDD je jako vytvoření osnovy pro knihu předtím, než ji napíšeme. Je určena k tomu, aby vývojářům usnadnil psaní jednodušších, čitelnějších a efektivních kódu.

> [!NOTE]
> Tým ASP.NET řídí [tyto konvence](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) , které vývojářům pomůžou pocházet s dobrými názvy testovacích tříd a metod.

Při zápisu testů jednotek se nepovedlo zavést závislosti na infrastruktuře. Tyto testy jsou pomaleji a poměrně křehký a měly by být rezervovány pro integrační testy. Pomocí [principu explicitní závislosti](https://deviq.com/explicit-dependencies-principle/) a [vložení závislostí](/aspnet/core/fundamentals/dependency-injection)se můžete vyhnout těmto závislostem ve vaší aplikaci. Testy jednotek můžete také zachovat v samostatném projektu z testů Integration. Tím zajistíte, že projekt testů jednotek nebude mít odkazy na balíčky infrastruktury ani závislosti.

## <a name="next-steps"></a>Další kroky

Další informace o testování částí v projektech .NET Core:

Projekty testů jednotek .NET Core jsou podporované pro:

- [C#](../../csharp/index.yml)
- [F#](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml)

Můžete si také vybrat mezi několika rozhraními pro testování částí:

- [xUnit](https://xunit.net/)
- [NUnit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Další informace najdete v následujících návodech:

:::zone pivot="mstest"

- Vytvářejte testy jednotek pomocí [ *MSTest* a *C#* s .NET Core CLI](unit-testing-with-mstest.md).
- Vytvářejte testy jednotek pomocí [ *MSTest* a *F #* s .NET Core CLI](unit-testing-fsharp-with-mstest.md).
- Vytvářejte testy jednotek pomocí [ *MSTest* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-mstest.md).

:::zone-end
:::zone pivot="xunit"

- Vytvářejte testy jednotek pomocí [ *xUnit* a *C#* s .NET Core CLI](unit-testing-with-dotnet-test.md).
- Vytvářejte testy jednotek pomocí [ *XUnit* a *F #* s .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).
- Vytvářejte testy jednotek pomocí [ *xUnit* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).

:::zone-end
:::zone pivot="nunit"

- Vytvářejte testy jednotek pomocí [ *nunit* a *C#* s .NET Core CLI](unit-testing-with-nunit.md).
- Vytvářejte testy jednotek pomocí [ *nunit* a *F #* s .NET Core CLI](unit-testing-fsharp-with-nunit.md).
- Vytvářejte testy jednotek pomocí [ *NUnit* a *Visual Basic* s .NET Core CLI](unit-testing-visual-basic-with-nunit.md).

:::zone-end

Další informace najdete v následujících článcích:

- Visual Studio Enterprise nabízí skvělé testovací nástroje pro .NET Core. Další informace najdete [Live Unit Testing](/visualstudio/test/live-unit-testing) nebo [pokrytí kódu](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) .
- Další informace o tom, jak spustit selektivní testy jednotek, najdete v tématu [spuštění selektivních testů jednotek](selective-unit-tests.md)nebo [zahrnutí a vyloučení testů v aplikaci Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [Jak používat xUnit s .NET Core a sadou Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
