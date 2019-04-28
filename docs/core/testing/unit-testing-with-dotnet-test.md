---
title: Testování jednotek kódu C# v .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 97cf42c78154375ce06639d4a3029ed87b993ced
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665439"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testování jednotek C# v .NET Core pomocí příkazu dotnet test a xUnit

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *testování použití dotnet testování částí* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení. Řešení usnadňuje správu knihovny tříd a projekt testu jednotek.
V adresáři řešení, vytvářet *PrimeService* adresáře. Strukturu adresáře a souboru doposud by měl vypadat takto:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) vytvoření zdrojového projektu. Přejmenovat *Class1.cs* k *PrimeService.cs*. Nejprve vytvoříte selhání provádění `PrimeService` třídy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

Vraťte do adresáře *testování použití dotnet testování částí* adresáře.

Spustit [dotnet sln](../tools/dotnet-sln.md) příkaz pro přidání do řešení projekt knihovny tříd:

```
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit` ](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který používá [xUnit](https://xunit.github.io/) jako knihovna testu. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.csproj* souboru podobně jako následující kód:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat xUnit a xUnit runner. Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.

Následující obrázek znázorňuje rozložení konečné řešení:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Chcete-li přidat testovací projekt do řešení, spusťte [dotnet sln](../tools/dotnet-sln.md) v *testování použití dotnet testování částí* adresáře:

```
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje. Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový C# soubor s názvem *PrimeService_IsPrimeShould.cs*. Přidejte následující kód:

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` Určuje atribut testovací metody, která se spouští pomocí nástroje test runner. Z *PrimeService.Tests* složce spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje. Nahraďte existující `IsPrime` implementace metody s následujícím kódem:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

V *PrimeService.Tests* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Existuje několik dalších jednoduché případů pro prvočísel: 0, -1. Tyto případy můžete přidat jako nové testy s `[Fact]` atribut, ale rychle stane únavné. Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování:

- `[Theory]` představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.

- `[InlineData]` atribut určuje hodnoty pro tyto vstupy.

Místo vytváření nové testy, platí tyto dva atributy `[Theory]` a `[InlineData]`, k vytvoření jedné teorie v *PrimeService_IsPrimeShould.cs* souboru. Teorie je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test` znovu, a dvě z těchto testů by selhat. Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `IsPrime` metoda ve *PrimeService.cs* souboru:

```csharp
if (candidate < 2)
```

Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny. Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Další zdroje

- [xUnit.net oficiální web](https://xunit.github.io)
- [Testování logice kontroleru v ASP.NET Core](/aspnet/core/mvc/controllers/testing)
