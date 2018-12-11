---
title: Testování C# s použitím NUnit a .NET Core
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a NUnit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 80c831a6d8ab9aa35435d0ff8f13334f7d169a3a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169025"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testování C# s použitím NUnit a .NET Core

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

- [Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější verze.
- Textového editoru nebo editoru kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování použití nunit* pro uložení řešení. Uvnitř tohoto nového adresáře spuštěním následujícího příkazu vytvořte nový soubor řešení pro knihovny tříd a testovacího projektu:

```console
dotnet new sln
```
 
Dále vytvořte *PrimeService* adresáře. Následující osnovy zatím znázorňuje strukturu adresáře a souboru:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:

```console
dotnet new classlib
```

Přejmenovat *Class1.cs* k *PrimeService.cs*. Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:

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

Vraťte do adresáře *jednotky – testování použití nunit* adresáře. Spusťte následující příkaz pro přidání do řešení projekt knihovny tříd:

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí následujícího příkazu:

```console
dotnet new nunit
```

[Dotnet nové](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako knihovna testu. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeService.Tests.csproj* souboru:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat Microsoft test sady SDK, testovací rozhraní NUnit a NUnit testovací adaptér. Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.

Následující osnovy ukazuje rozložení konečné řešení:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

Spusťte následující příkaz v *testování použití dotnet testování částí* adresáře:

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu. V *PrimeService.Tests* adresáře, přejmenovat *UnitTest1.cs* do souboru *PrimeService_IsPrimeShould.cs* a jeho celý obsah nahraďte následujícím kódem:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestFixture]` Atribut označuje třídu, která obsahuje testy jednotek. `[Test]` Atribut označuje, že metoda je testovací metodu.

Tento soubor uložte a spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner NUnit obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:

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

V *jednotky – testování použití nunit* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Existuje několik dalších jednoduché případů pro prvočísel: 0, -1. Můžete přidat nové testy s `[Test]` atribut, ale rychle stane únavné. Existují jiné NUnit atributy, které umožňují také napsat sady podobné testování.  A `[TestCase]` atribut se používá k vytvoření sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty. Můžete použít `[TestCase]` atribut můžete zadat hodnoty pro tyto vstupy.

Místo vytváření nové testy, Použíjte tento atribut pro vytvoření testu jedné řízené daty. Test na základě dat je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich selhání testů. Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `Main` metoda ve *PrimeService.cs* souboru:

```csharp
if (candidate < 2)
```

Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny. Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Začlenění malé knihovny a sadu testů jednotek pro knihovny. Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu. Jste koncentrované většinu času a úsilí na řešení cíle aplikace.
