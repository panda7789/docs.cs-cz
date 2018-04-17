---
title: 'Testování knihovny F # v .NET Core pomocí testovacích dotnet a xUnit částí'
description: 'Další koncepty testů jednotek pro F # v .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a xUnit.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- fsharp
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 8485b1a64992c7a632d22d9dc492ee4d83592208
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Testování knihovny F # v .NET Core pomocí testovacích dotnet a xUnit částí

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

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
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
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

Ujistěte se, *MathService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md). Tím se vytvoří testovací projekt, který používá xUnit jako knihovně testu. Nástroj test runner v nakonfiguruje vygenerované šablony *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat xUnit a xUnit runner. Nyní přidejte `MathService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../MathService/MathService.fsproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.

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
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Atribut označuje testovací metodu, která spustí nástroj test runner. Z *jednotky – testování s fsharp*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner xUnit obsahuje vstupní bod programu ke spuštění testů. `dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Tyto dva testy zobrazit nejzákladnější, předávání a selhání testy. `My test` úspěšně projde, a `Fail every time` selže. Teď vytvořte testu pro `squaresOfOdds` metoda. `squaresOfOdds` Metoda vrátí pořadí kvadratických hodnot liché celé číslo, které jsou součástí vstupní pořadí. Místo došlo k pokusu o zápis všechny tyto funkce najednou, můžete vytvořit interaktivně testy, které ověřit funkčnost. Provedení každého testu předat znamená vytváření potřebné funkce pro metodu.

Nejjednodušší testu jsme může zapisovat je volání `squaresOfOdds` s všechna čísla sudé, kde výsledkem by měl být prázdnou sekvencí celých čísel.  Tady je testu:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test se nezdaří. Nevytvořili jste ještě implementace. Psaní kódu nejjednodušší v, aby tento test `MathService` třídu, která funguje:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

V *jednotky – testování s fsharp* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `MathService` projektu a pak `MathService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="completing-the-requirements"></a>Požadavky na dokončení

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Další jednoduché případ funguje s pořadím, jejichž pouze liché číslo je `1`. Číslo 1 je jednodušší, protože druhou mocninu 1 je 1. Zde je další testu:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Provádění `dotnet test` spustí testy a ukazuje, že nový test se nezdaří. Nyní, aktualizovat `squaresOfOdds` metodu ke zpracování tento nový test. Filtrovat všechna čísla sudé mimo pořadí, aby tento test předat. Můžete to udělat tak, že zápis funkce malé filtru a pomocí `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Neexistuje jeden krok přejdete: Čtvereček každý liché čísel. Začněte vytvořením nového testu:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Můžete je vyřešit test tím filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý lichý počet:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu. Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu. Jste soustředí většinu čas a úsilí na řešení cílů aplikace.
