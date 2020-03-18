---
title: Testování částí F# v rozhraní .NET Core s dotnet testem a xUnit
description: Naučte koncepty testování částí pro F# v .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5fe4a8faddd87334439513368f24d808abc58e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157307"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testování částí knihoven F# v rozhraní .NET Core pomocí dotnet test a xUnit

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *testování jednotky s fsharp* držet řešení.
V tomto novém `dotnet new sln` adresáři spusťte a vytvořte nové řešení. To usnadňuje správu knihovny tříd a projektu testování částí.
V adresáři řešení vytvořte adresář *MathService.* Adresář a struktura souborů je zatím uvedena níže:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Nastavení *mathservice* jako aktuálního `dotnet new classlib -lang "F#"` adresáře a spuštěním vytvořte zdrojový projekt. Vytvoříte selhávající implementaci matematické služby:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změňte adresář zpět do adresáře *testování jednotek s fsharp.* Spuštěním `dotnet sln add .\MathService\MathService.fsproj` přidáte projekt knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte adresář *MathService.Tests.* Následující osnova ukazuje adresářovou strukturu:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Vytvořte adresář *MathService.Tests* jako aktuální adresář `dotnet new xunit -lang "F#"`a vytvořte nový projekt pomocí aplikace . Tím se vytvoří testovací projekt, který používá xUnit jako testovací knihovnu. Vygenerovaná šablona konfiguruje testovacího běžce v *mathservicetests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`v předchozím kroku přidánxUnit a xUnit runner. Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu. Použijte `dotnet add reference` příkaz:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.

Máte následující konečné rozložení řešení:

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

Spusťte `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` v adresáři *testování jednotky s fsharp.*

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. Otevřete *soubor Tests.fs* a přidejte následující kód:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

Atribut `[<Fact>]` označuje testovací metodu, která je spuštěna testovacím běžcem. Z *jednotky testování s fsharp*, `dotnet test` spusťte k sestavení testů a knihovny tříd a pak spustit testy. XUnit test runner obsahuje vstupní bod programu ke spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

Tyto dva testy ukazují nejzákladnější absolvování a selhání testů. `My test`projde a `Fail every time` selže. Nyní vytvořte test `squaresOfOdds` pro metodu. Metoda `squaresOfOdds` vrátí posloupnost čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence. Spíše než se snaží zapsat všechny tyto funkce najednou, můžete iterativně vytvořit testy, které ověřují funkce. Provedení každého průchodu test znamená vytvoření potřebné funkce pro metodu.

Nejjednodušší test, který můžeme napsat, je volat `squaresOfOdds` se všemi sudými čísly, kde by výsledkem měla být prázdná posloupnost celých čísel.  Tady je ten test:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Váš test se nezdaří. Ještě jste nevytvořili implementaci. Proveďte tento test projít napsáním `MathService` nejjednodušší kód ve třídě, která funguje:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

V adresáři *testování jednotek s fsharp* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `MathService` projekt a `MathService.Tests` potom pro projekt. Po sestavení obou projektů spustí tento jediný test. Už to přejde.

## <a name="completing-the-requirements"></a>Splnění požadavků

Nyní, když jste provedli jeden test projít, je čas napsat více. Další jednoduchý případ pracuje s sekvencí, jejíž jediné liché číslo je `1`. Číslo 1 je jednodušší, protože čtverec 1 je 1. Zde je další test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Spuštění `dotnet test` spustí testy a ukáže, že nový test se nezdaří. Nyní aktualizujte `squaresOfOdds` metodu pro zpracování tohoto nového testu. Můžete filtrovat všechna sudá čísla z pořadí, aby tento test projít. Můžete to udělat tak, že napíšete malou funkci filtru a použijete: `Seq.filter`

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Je před ním ještě jeden krok: srovnat každé z lichých čísel. Začněte napsáním nového testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Test můžete opravit potrubím filtrované sekvence pomocí operace mapy pro výpočet čtverce každého lichého čísla:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu. Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu. Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.

## <a name="see-also"></a>Viz také

- [dotnet new](../tools/dotnet-new.md)
- [dotnet run](../tools/dotnet-new.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
