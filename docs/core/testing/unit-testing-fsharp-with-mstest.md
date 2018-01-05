---
title: "Jednotka knihovny F # testování v .NET Core pomocí testovacích dotnet a Mstestu"
description: "Další koncepty testů jednotek pro F # v .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a Mstestu."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 6dc5388f8e5645530cdd12986a9e1e53e4115c9a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Jednotka knihovny F # testování v .NET Core pomocí testovacích dotnet a Mstestu

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení. Díky tomu je snazší správa knihovny tříd a projektu testování částí.
V adresáři řešení vytvořit *MathService* adresáře. Strukturu adresáře a souboru proto mnohem je zobrazena níže:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.  Pokud chcete používat testy řízený vývoj (TDD), vytvoříte selhání implementace matematické služby:

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změna adresáře zpět do *jednotky – testování s fsharp* adresáře. Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytvoření projektu testů

Dále vytvořte *MathService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Ujistěte se, *MathService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md). Tím se vytvoří testovací projekt, který používá Mstestu jako rozhraní test. Nástroj test runner v nakonfiguruje vygenerované šablony *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new`v předchozím kroku přidat Mstestu a Mstestu runner. Nyní přidejte `MathService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../MathService/MathService.fsproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.

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

Spuštění [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu. Otevřete *Tests.fs* a přidejte následující kód:

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

`[<TestClass>]` Atribut označuje třídu, která obsahuje testy. `[<TestMethod>]` Atribut označuje testovací metodu, která spustí nástroj test runner. Z *jednotky – testování s fsharp* adresáře, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner Mstestu obsahuje vstupní bod programu ke spuštění testů. `dotnet test`Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Tyto dva testy zobrazit nejzákladnější, předávání a selhání testy. `My test`úspěšně projde, a `Fail every time` selže. Teď vytvořte testu pro `sumOfSquares` metoda. `sumOfSquares` Metoda vrátí součet kvadratických hodnot liché celé číslo, které jsou součástí vstupní pořadí. Místo došlo k pokusu o zápis všechny tyto funkce najednou, můžete vytvořit interaktivně testy, které ověřit funkčnost. Provedení každého testu předat znamená vytváření potřebné funkce pro metodu.

Nejjednodušší testu jsme může zapisovat je volání `sumOfSquares` s všechna čísla sudé, kde výsledkem by měl být prázdnou sekvencí celých čísel.  Tady je testu:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Všimněte si, že `expected` pořadí byl převeden na seznamu. Knihovna Mstestu spoléhá na mnoho standardní typy .NET. Aby závislost znamená, že veřejné rozhraní a očekávaných výsledků podporu <xref:System.Collections.ICollection> místo <xref:System.Collections.IEnumerable>.

Při spuštění testu, uvidíte, že váš test se nezdaří. Nevytvořili jste ještě implementace. Psaní kódu nejjednodušší v, aby tento test `Mathservice` třídu, která funguje:

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

V *jednotky – testování s fsharp* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `MathService` projektu a pak `MathService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="completing-the-requirements"></a>Požadavky na dokončení

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Další jednoduché případ funguje s pořadím, jejichž pouze liché číslo je `1`. Číslo 1 je jednodušší, protože druhou mocninu 1 je 1. Zde je další testu:

```fsharp
[<TestMethod>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Provádění `dotnet test` nový test se nezdaří. Je nutné aktualizovat `sumOfSquares` metodu ke zpracování tento nový test. Musí filtrovat všechna čísla sudé mimo pořadí, aby tento test předat. Můžete to udělat tak, že zápis funkce malé filtru a pomocí `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Všimněte si volání `Seq.toList`. Který vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.

Neexistuje jeden krok přejdete: Čtvereček každý liché čísel. Začněte vytvořením nového testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Můžete je vyřešit test tím filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý lichý počet:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu. Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu. Jste soustředí většinu čas a úsilí na řešení cílů aplikace.
