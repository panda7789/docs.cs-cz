---
title: 'Testování částí F # v .NET Core pomocí příkazu dotnet test a MSTest'
description: 'Seznamte se s koncepty testování částí jazyka F # v .NET Core prostřednictvím interaktivního prostředí vytvářejícího ukázkové řešení pomocí příkazu dotnet test a MSTest.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 08aa0b4a36f399d4439a0f3b34e88a1b51e98215
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656537"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Testování částí knihoven F # v .NET Core pomocí příkazu dotnet test a MSTest

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.
V tomto novém adresáři spusťte příkaz `dotnet new sln` a vytvořte nové řešení. To usnadňuje správu knihovny tříd i projektu testu jednotek.
V adresáři řešení vytvořte adresář *MathService* . Struktura adresářů a souborů je tedy uvedena níže:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Vytvořte *MathService* aktuální adresář a spusťte příkaz `dotnet new classlib -lang "F#"` k vytvoření zdrojového projektu.  Vytvoříte nefunkční implementaci služby Math Service:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp. Spusťte `dotnet sln add .\MathService\MathService.fsproj` , chcete-li přidat projekt knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *MathService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Nastavte adresář *MathService. Tests* na aktuální adresář a vytvořte nový projekt pomocí `dotnet new mstest -lang "F#"` . Tím se vytvoří testovací projekt, který jako testovací rozhraní používá MSTest. Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new` v předchozím kroku jsme přidali MSTest a MSTest Runner. Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu. Použijte `dotnet add reference` příkaz:

```dotnetcli
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

Spusťte `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` v adresáři *Unit-Testing-with-FSharp* .

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Otevřete *Tests. FS* a přidejte následující kód:

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

`[<TestClass>]`Atribut označuje třídu, která obsahuje testy. `[<TestMethod>]`Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner. Z adresáře *Unit-Testing-with-FSharp* spusťte příkaz `dotnet test` pro sestavení testů a knihovny tříd a poté spusťte testy. MSTest Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Tyto dva testy znázorňují základní a neúspěšné testy. `My test` projde a `Fail every time` dojde k chybě. Nyní vytvořte test pro `squaresOfOdds` metodu. `squaresOfOdds`Metoda vrátí seznam čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence. Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost. Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.

Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.  Zde je tento test:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Všimněte si, že se `expected` sekvence převedla na seznam. Knihovna MSTest spoléhá na mnoho standardních typů .NET. Tato závislost znamená, že vaše veřejné rozhraní a očekávané výsledky podporují <xref:System.Collections.ICollection> spíše než <xref:System.Collections.IEnumerable> .

Když spustíte test, uvidíte, že test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu vytvořením nejjednoduššího kódu ve `Mathservice` třídě, která funguje:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu. `dotnet test`Příkaz spustí sestavení pro `MathService` projekt a potom pro `MathService.Tests` projekt. Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="completing-the-requirements"></a>Splnění požadavků

Teď, když jste udělali jeden test Pass, je čas zapsat další. Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo je `1` . Číslo 1 je snazší, protože čtvercem 1 je 1. Následující test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Spuštění `dotnet test` selhalo v novém testu. Je nutné aktualizovat `squaresOfOdds` metodu pro zpracování tohoto nového testu. Chcete-li provést tento test, je nutné vyfiltrovat všechna sudá čísla mimo sekvenci. Můžete to udělat tak, že napíšete malou funkci filtru a použijete `Seq.filter` :

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Všimněte si volání `Seq.toList` . Tím se vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.

K dispozici je ještě ještě jeden krok: čtverce každé liché číslice. Začněte zápisem nového testu:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.

## <a name="see-also"></a>Viz také:

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-sln.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
