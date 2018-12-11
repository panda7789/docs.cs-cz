---
title: Testování částí F# v .NET Core pomocí příkazu dotnet test a NUnit
description: Další koncepty testů jednotek pro F# v .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: e919da8910129be027ff7e2dbed8c4564738e023
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241759"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="ae352-103">Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="ae352-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="ae352-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="ae352-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ae352-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="ae352-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="ae352-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ae352-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae352-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae352-107">Prerequisites</span></span>

- <span data-ttu-id="ae352-108">[Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="ae352-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="ae352-109">Textového editoru nebo editoru kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="ae352-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ae352-110">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="ae352-110">Creating the source project</span></span>

<span data-ttu-id="ae352-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="ae352-111">Open a shell window.</span></span> <span data-ttu-id="ae352-112">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="ae352-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="ae352-113">Uvnitř tohoto nového adresáře spuštěním následujícího příkazu vytvořte nový soubor řešení pro knihovny tříd a testovacího projektu:</span><span class="sxs-lookup"><span data-stu-id="ae352-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="ae352-114">Dále vytvořte *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ae352-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="ae352-115">Následující osnovy zatím znázorňuje strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="ae352-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="ae352-116">Ujistěte se, *MathService* aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="ae352-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang F#
```

<span data-ttu-id="ae352-117">Použít vývoj řízený testováním (TDD), vytvořte implementaci selhání matematické služby:</span><span class="sxs-lookup"><span data-stu-id="ae352-117">To use test-driven development (TDD), you create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="ae352-118">Vraťte do adresáře *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ae352-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="ae352-119">Spusťte následující příkaz pro přidání do řešení projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="ae352-119">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="ae352-120">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="ae352-120">Creating the test project</span></span>

<span data-ttu-id="ae352-121">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ae352-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="ae352-122">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="ae352-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="ae352-123">Ujistěte se, *MathService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="ae352-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang F#
```

<span data-ttu-id="ae352-124">Tím se vytvoří projekt testů, který se používá jako testovací rozhraní NUnit.</span><span class="sxs-lookup"><span data-stu-id="ae352-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="ae352-125">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="ae352-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="ae352-126">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="ae352-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ae352-127">`dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="ae352-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="ae352-128">Teď přidejte `MathService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="ae352-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="ae352-129">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="ae352-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="ae352-130">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="ae352-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="ae352-131">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="ae352-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="ae352-132">Spusťte následující příkaz v *jednotky – testování s fsharp* adresáře:</span><span class="sxs-lookup"><span data-stu-id="ae352-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="ae352-133">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="ae352-133">Creating the first test</span></span>

<span data-ttu-id="ae352-134">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="ae352-134">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="ae352-135">Otevřít *UnitTest1.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ae352-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="ae352-136">`[<TestFixture>]` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="ae352-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="ae352-137">`[<Test>]` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="ae352-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="ae352-138">Z *jednotky – testování s fsharp* adresáře, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ae352-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ae352-139">Nástroj test runner NUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="ae352-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ae352-140">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="ae352-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ae352-141">Tyto dva testy zobrazit naprosto základní předáním hodnoty a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="ae352-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="ae352-142">`My test` úspěšně proběhne, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="ae352-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="ae352-143">Teď vytvořte test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="ae352-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="ae352-144">`squaresOfOdds` Metoda vrátí sekvenci druhých mocnin hodnot liché celé číslo, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="ae352-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="ae352-145">Namísto pokusu o zápis všechny tyto funkce současně, můžete interaktivně vytvořit testy, které ověří funkčnost.</span><span class="sxs-lookup"><span data-stu-id="ae352-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="ae352-146">Provedení každého testu předat znamená vytvoření potřebné funkce k metodě.</span><span class="sxs-lookup"><span data-stu-id="ae352-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="ae352-147">Nejjednodušší nám můžete napsat test je volání `squaresOfOdds` s všechna sudá čísla, kde výsledkem by měl být k prázdné sekvenci celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ae352-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="ae352-148">Tady je tento test:</span><span class="sxs-lookup"><span data-stu-id="ae352-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ae352-149">Všimněte si, že `expected` pořadí byl převeden do seznamu.</span><span class="sxs-lookup"><span data-stu-id="ae352-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="ae352-150">Rozhraní NUnit spoléhá na mnoho standardních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="ae352-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="ae352-151">Že závislostí znamená, že vaše veřejné rozhraní a očekávané výsledky podporu <xref:System.Collections.ICollection> spíše než <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="ae352-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="ae352-152">Při spuštění testu se zobrazí, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ae352-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="ae352-153">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="ae352-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="ae352-154">Ujistěte se, tento test předat napsáním kódu nejjednodušší v *Library.fs* třídu v projektu MathService, která funguje:</span><span class="sxs-lookup"><span data-stu-id="ae352-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="ae352-155">V *jednotky – testování s fsharp* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="ae352-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ae352-156">`dotnet test` Sestavení pro spuštění příkazu `MathService` projekt a potom `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="ae352-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="ae352-157">Po vytvoření oba projekty, spouští testy.</span><span class="sxs-lookup"><span data-stu-id="ae352-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="ae352-158">Dva testy jsou nyní úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ae352-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="ae352-159">Dokončuje požadavky</span><span class="sxs-lookup"><span data-stu-id="ae352-159">Completing the requirements</span></span>

<span data-ttu-id="ae352-160">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="ae352-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ae352-161">Další jednoduchý případ funguje s pořadím, jehož jen liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="ae352-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="ae352-162">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="ae352-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="ae352-163">Tady je další testu:</span><span class="sxs-lookup"><span data-stu-id="ae352-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ae352-164">Provádění `dotnet test` nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ae352-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="ae352-165">Je nutné aktualizovat `squaresOfOdds` metodu ke zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="ae352-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="ae352-166">Všechna sudá čísla mimo pořadí, aby tento test předat musí filtrovat.</span><span class="sxs-lookup"><span data-stu-id="ae352-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="ae352-167">Můžete to udělat tak, že funkce malé filtru zápisu a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="ae352-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="ae352-168">Všimněte si, že volání `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="ae352-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="ae352-169">Který vytváří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae352-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="ae352-170">Existuje jeden další krok: čtvercové všech lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="ae352-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="ae352-171">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="ae352-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="ae352-172">Test můžete vyřešit přesměrujete filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý liché číslo:</span><span class="sxs-lookup"><span data-stu-id="ae352-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="ae352-173">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="ae352-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ae352-174">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ae352-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ae352-175">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae352-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>