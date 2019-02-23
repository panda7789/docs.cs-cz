---
title: Testování částí F# v .NET Core pomocí příkazu dotnet test a MSTest
description: Další koncepty testů jednotek pro F# v .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1765c16cb55857b83a8206ae97327d0fd2809019
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747489"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a MSTest

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení. Díky tomu usnadňují správu knihovny tříd a projekt testu jednotek.
V adresáři řešení, vytvářet *MathService* adresáře. Struktura adresářů a souborů je dosavadním vidíte níže:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.  Vytvoříte selhání provádění matematických služby:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Vraťte do adresáře *jednotky – testování s fsharp* adresáře. Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *MathService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Ujistěte se, *MathService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md). Tím se vytvoří projekt testů, který se používá jako testovací rozhraní MSTest. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat MSTest a MSTest runner. Teď přidejte `MathService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../MathService/MathService.fsproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.

Máte následující rozložení konečné řešení:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

Spustit [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje. Otevřít *Tests.fs* a přidejte následující kód:

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

`[<TestClass>]` Atribut označuje třídu, která obsahuje testy. `[<TestMethod>]` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner. Z *jednotky – testování s fsharp* adresáře, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner MSTest obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Tyto dva testy zobrazit naprosto základní předáním hodnoty a neúspěšné testy. `My test` úspěšně proběhne, a `Fail every time` selže. Teď vytvořte test `squaresOfOdds` metody. `squaresOfOdds` Metoda vrátí seznam hodnot druhých mocnin hodnot liché celé číslo, které jsou součástí vstupní sekvence. Namísto pokusu o zápis všechny tyto funkce současně, můžete interaktivně vytvořit testy, které ověří funkčnost. Provedení každého testu předat znamená vytvoření potřebné funkce k metodě.

Nejjednodušší nám můžete napsat test je volání `squaresOfOdds` s všechna sudá čísla, kde výsledkem by měl být k prázdné sekvenci celých čísel.  Tady je tento test:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Všimněte si, že `expected` pořadí byl převeden do seznamu. Knihovna MSTest spoléhá na mnoho standardních typů .NET. Že závislostí znamená, že vaše veřejné rozhraní a očekávané výsledky podporu <xref:System.Collections.ICollection> spíše než <xref:System.Collections.IEnumerable>.

Při spuštění testu se zobrazí, že váš test se nezdaří. Nevytvořili jste ještě implementace. Tento test provést napsáním kódu nejjednodušší v `Mathservice` třídu, která funguje:

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

V *jednotky – testování s fsharp* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `MathService` projekt a potom `MathService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="completing-the-requirements"></a>Dokončuje požadavky

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Další jednoduchý případ funguje s pořadím, jehož jen liché číslo je `1`. Číslo 1 je jednodušší, protože druhou mocninu 1 je 1. Tady je další testu:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Provádění `dotnet test` nový test se nezdaří. Je nutné aktualizovat `squaresOfOdds` metodu ke zpracování tohoto nového testu. Všechna sudá čísla mimo pořadí, aby tento test předat musí filtrovat. Můžete to udělat tak, že funkce malé filtru zápisu a pomocí `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Všimněte si, že volání `Seq.toList`. Který vytváří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.

Existuje jeden další krok: čtvercové všech lichých čísel. Začněte vytvořením nového testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Test můžete vyřešit přesměrujete filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý liché číslo:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Začlenění malé knihovny a sadu testů jednotek pro knihovny. Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu. Jste koncentrované většinu času a úsilí na řešení cíle aplikace.
