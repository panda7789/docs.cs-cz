---
title: Testování C# částí kódu v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty C# testování částí v a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 1013e14690bb3cfc17e339bfd5045e6d10bc3d3e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168150"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testování C# částí v .NET Core pomocí příkazu dotnet test a xUnit

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-using-dotnet-test* pro uložení řešení.
V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení. Díky řešení je snazší spravovat jak knihovnu tříd, tak projekt testování částí.
V adresáři řešení vytvořte adresář *PrimeService* . Struktura adresáře a souborů by měla být takto:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální adresář a spusťte příkaz [`dotnet new classlib`](../tools/dotnet-new.md) k vytvoření zdrojového projektu. Přejmenujte *Class1.cs* na *PrimeService.cs*. Nejprve vytvoříte selhání implementace `PrimeService` třídy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

Změňte adresář zpátky na adresář *-Test-Using-dotnet-test* .

Spusťte příkaz [dotnet sln](../tools/dotnet-sln.md) a přidejte do řešení projekt knihovny tříd:

```console
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *PrimeService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new xunit`](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který jako knihovnu testů používá [xUnit](https://xunit.github.io/) . Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeServiceTests. csproj* podobně jako v následujícím kódu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new`v předchozím kroku jsme přidali xUnit a xUnit Runner. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.

Následující příklad ukazuje konečné rozložení řešení:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Chcete-li přidat testovací projekt do řešení, spusťte příkaz [dotnet sln](../tools/dotnet-sln.md) v adresáři *Unit-Testing-using-dotnet-test* :

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Odeberte *UnitTest1.cs* z adresáře *PrimeService. Tests* a vytvořte nový C# soubor s názvem *PrimeService_IsPrimeShould. cs*. Přidejte následující kód:

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner. Ze složky *PrimeService. Tests* spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz a sestavte testy a knihovnu tříd a potom spusťte testy. XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu tak, že napíšete `PrimeService` nejjednodušší kód ve třídě, která funguje. Nahraďte stávající `IsPrime` implementaci metody následujícím kódem:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

V adresáři *PrimeService. Tests* spusťte `dotnet test` znovu. Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test` Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Teď, když jste udělali jeden test Pass, je čas zapsat další. Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1. Tyto případy můžete přidat jako nové testy s `[Fact]` atributem, ale to se rychle bude zdlouhavé. Existují další atributy xUnit, které umožňují napsat sadu podobných testů:

- `[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.

- `[InlineData]`atribut určuje hodnoty pro tyto vstupy.

Namísto vytváření nových testů, použijte tyto dva atributy, `[Theory]` a `[InlineData]`vytvořte jednu teorie v souboru *PrimeService_IsPrimeShould. cs* . Teoretická je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spusťte `dotnet test` znovu a dva z těchto testů by měly selhat. Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku `IsPrime` metody v souboru *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně. Máte hotovou [verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Další zdroje

- [Oficiální web xUnit.net](https://xunit.github.io)
- [Testování logiky kontroleru v ASP.NET Core](/aspnet/core/mvc/controllers/testing)
