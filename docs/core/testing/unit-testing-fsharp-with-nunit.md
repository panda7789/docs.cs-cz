---
title: Testování částí F# v rozhraní .NET Core s dotnet testem a Jednotkou NUnit
description: Naučte koncepty testování částí pro F# v .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715449"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Testování částí knihoven F# v rozhraní .NET Core pomocí dotnet test a NUnit

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *testování jednotky s fsharp* držet řešení.
V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```

Dále vytvořte adresář *MathService.* Následující osnova ukazuje adresář a strukturu souborů tak daleko:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Vytvořte *mathservice* jako aktuální adresář a vytvořte zdrojový projekt následujícím příkazem:

```dotnetcli
dotnet new classlib -lang "F#"
```

Vytvoření selhání implementace matematické služby:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Změňte adresář zpět do adresáře *testování jednotek s fsharp.* Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

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

Vytvořte adresář *MathService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit -lang "F#"
```

Tím se vytvoří testovací projekt, který používá NUnit jako testovací rámec. Vygenerovaná šablona konfiguruje testovacího běžce v *mathservicetests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`v předchozím kroku přidánn NUnit a NUnit testovací adaptér. Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu. Použijte `dotnet add reference` příkaz:

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
        MathService.Tests.fsproj
```

V adresáři *testování jednotky s fsharp* proveďte následující příkaz:

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. Otevřete *unittest1.fs* a přidejte následující kód:

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

Atribut `[<TestFixture>]` označuje třídu, která obsahuje testy. Atribut `[<Test>]` označuje testovací metodu, která je spuštěna testovacím běžcem. Z adresáře *testování jednotky s fsharp* spusťte `dotnet test` k sestavení testů a knihovny tříd a spusťte testy. Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

Tyto dva testy ukazují nejzákladnější absolvování a selhání testů. `My test`projde a `Fail every time` selže. Nyní vytvořte test `squaresOfOdds` pro metodu. Metoda `squaresOfOdds` vrátí posloupnost čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence. Spíše než se snaží zapsat všechny tyto funkce najednou, můžete iterativně vytvořit testy, které ověřují funkce. Provedení každého průchodu test znamená vytvoření potřebné funkce pro metodu.

Nejjednodušší test, který můžeme napsat, je volat `squaresOfOdds` se všemi sudými čísly, kde by výsledkem měla být prázdná posloupnost celých čísel.  Tady je ten test:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Všimněte `expected` si, že sekvence byla převedena na seznam. NUnit framework spoléhá na mnoho standardních typů .NET. Tato závislost znamená, že vaše veřejné <xref:System.Collections.ICollection> rozhraní <xref:System.Collections.IEnumerable>a očekávané výsledky podporují spíše než .

Při spuštění testu uvidíte, že váš test se nezdaří. Ještě jste nevytvořili implementaci. Proveďte tento test projít napsáním nejjednodušší kód ve třídě *Library.fs* v projektu MathService, který funguje:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

V adresáři *testování jednotek s fsharp* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `MathService` projekt a `MathService.Tests` potom pro projekt. Po sestavení obou projektů spustí testy. Dva testy teď jsou pryč.

## <a name="completing-the-requirements"></a>Splnění požadavků

Nyní, když jste provedli jeden test projít, je čas napsat více. Další jednoduchý případ pracuje s sekvencí, jejíž jediné liché číslo je `1`. Číslo 1 je jednodušší, protože čtverec 1 je 1. Zde je další test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Spuštění `dotnet test` se nezdaří nový test. Je nutné `squaresOfOdds` aktualizovat metodu pro zpracování tohoto nového testu. Je nutné filtrovat všechna sudá čísla z pořadí, aby tento test prošel. Můžete to udělat tak, že napíšete malou funkci filtru a použijete: `Seq.filter`

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Všimněte si `Seq.toList`volání . Tím se vytvoří seznam, <xref:System.Collections.ICollection> který implementuje rozhraní.

Je před ním ještě jeden krok: srovnat každé z lichých čísel. Začněte napsáním nového testu:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
