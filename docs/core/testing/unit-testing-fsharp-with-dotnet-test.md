---
title: Testování F# částí v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty F# testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 8ef4489fffa8a0876f7f8dcfd1463965c177646a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253944"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testování F# částí knihoven v .NET Core pomocí příkazu dotnet test a xUnit

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.
V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení. To usnadňuje správu knihovny tříd i projektu testu jednotek.
V adresáři řešení vytvořte adresář *MathService* . Struktura adresářů a souborů je tedy uvedena níže:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Vytvořte *MathService* aktuální adresář a spusťte příkaz [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) k vytvoření zdrojového projektu.  Vytvoříte nefunkční implementaci služby Math Service:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp. Spusťte [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) , chcete-li přidat projekt knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *MathService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Nastavte adresář *MathService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new xunit -lang F#`](../tools/dotnet-new.md). Tím se vytvoří testovací projekt, který jako knihovnu testů používá xUnit. Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new`v předchozím kroku jsme přidali xUnit a xUnit Runner. Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:

```console
dotnet add reference ../MathService/MathService.fsproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.

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

Spusťte [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-with-FSharp* . 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Otevřete *Tests. FS* a přidejte následující kód:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner. Z rutiny *testování částí-with-FSharp*spusťte [`dotnet test`](../tools/dotnet-test.md) pro sestavení testů a knihovny tříd a potom spusťte testy. XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Tyto dva testy znázorňují základní a neúspěšné testy. `My test`projde a `Fail every time` dojde k chybě. Nyní vytvořte test pro `squaresOfOdds` metodu. `squaresOfOdds` Metoda vrací sekvenci čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence. Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost. Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.

Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.  Zde je tento test:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu vytvořením nejjednoduššího kódu `MathService` ve třídě, která funguje:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu. Příkaz spustí sestavení `MathService` pro`MathService.Tests` projekt a potom pro projekt. `dotnet test` Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="completing-the-requirements"></a>Splnění požadavků

Teď, když jste udělali jeden test Pass, je čas zapsat další. Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo `1`je. Číslo 1 je snazší, protože čtvercem 1 je 1. Následující test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Spuštění `dotnet test` spustí testy a ukáže vás, že nový test se nezdařil. Nyní aktualizujte `squaresOfOdds` metodu pro zpracování tohoto nového testu. Vyfiltrujete všechna sudá čísla mimo sekvenci k provedení tohoto testu. Můžete to udělat tak, že napíšete malou funkci filtru `Seq.filter`a použijete:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

K dispozici je ještě ještě jeden krok: čtverce každé liché číslice. Začněte zápisem nového testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.
