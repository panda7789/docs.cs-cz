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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665672"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="a803c-103">Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="a803c-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="a803c-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="a803c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="a803c-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="a803c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="a803c-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a803c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="a803c-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="a803c-107">Creating the source project</span></span>

<span data-ttu-id="a803c-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="a803c-108">Open a shell window.</span></span> <span data-ttu-id="a803c-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="a803c-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="a803c-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="a803c-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="a803c-111">Díky tomu usnadňují správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="a803c-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="a803c-112">V adresáři řešení, vytvářet *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="a803c-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="a803c-113">Struktura adresářů a souborů je dosavadním vidíte níže:</span><span class="sxs-lookup"><span data-stu-id="a803c-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="a803c-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="a803c-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="a803c-115">Vytvoříte selhání provádění matematických služby:</span><span class="sxs-lookup"><span data-stu-id="a803c-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="a803c-116">Vraťte do adresáře *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="a803c-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="a803c-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="a803c-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="a803c-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="a803c-118">Creating the test project</span></span>

<span data-ttu-id="a803c-119">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="a803c-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="a803c-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="a803c-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="a803c-121">Ujistěte se, *MathService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="a803c-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="a803c-122">Tím se vytvoří projekt testů, který se používá jako testovací rozhraní MSTest.</span><span class="sxs-lookup"><span data-stu-id="a803c-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="a803c-123">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="a803c-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="a803c-124">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="a803c-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="a803c-125">`dotnet new` v předchozím kroku přidat MSTest a MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="a803c-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="a803c-126">Teď přidejte `MathService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="a803c-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="a803c-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="a803c-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="a803c-128">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="a803c-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="a803c-129">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="a803c-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="a803c-130">Spustit [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="a803c-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="a803c-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="a803c-131">Creating the first test</span></span>

<span data-ttu-id="a803c-132">Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje.</span><span class="sxs-lookup"><span data-stu-id="a803c-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="a803c-133">Otevřít *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="a803c-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="a803c-134">`[<TestClass>]` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="a803c-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="a803c-135">`[<TestMethod>]` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="a803c-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="a803c-136">Z *jednotky – testování s fsharp* adresáře, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="a803c-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="a803c-137">Nástroj test runner MSTest obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="a803c-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="a803c-138">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a803c-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="a803c-139">Tyto dva testy zobrazit naprosto základní předáním hodnoty a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="a803c-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="a803c-140">`My test` úspěšně proběhne, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="a803c-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="a803c-141">Teď vytvořte test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="a803c-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="a803c-142">`squaresOfOdds` Metoda vrátí seznam hodnot druhých mocnin hodnot liché celé číslo, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="a803c-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="a803c-143">Namísto pokusu o zápis všechny tyto funkce současně, můžete interaktivně vytvořit testy, které ověří funkčnost.</span><span class="sxs-lookup"><span data-stu-id="a803c-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="a803c-144">Provedení každého testu předat znamená vytvoření potřebné funkce k metodě.</span><span class="sxs-lookup"><span data-stu-id="a803c-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="a803c-145">Nejjednodušší nám můžete napsat test je volání `squaresOfOdds` s všechna sudá čísla, kde výsledkem by měl být k prázdné sekvenci celých čísel.</span><span class="sxs-lookup"><span data-stu-id="a803c-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="a803c-146">Tady je tento test:</span><span class="sxs-lookup"><span data-stu-id="a803c-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="a803c-147">Všimněte si, že `expected` pořadí byl převeden do seznamu.</span><span class="sxs-lookup"><span data-stu-id="a803c-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="a803c-148">Knihovna MSTest spoléhá na mnoho standardních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="a803c-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="a803c-149">Že závislostí znamená, že vaše veřejné rozhraní a očekávané výsledky podporu <xref:System.Collections.ICollection> spíše než <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="a803c-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="a803c-150">Při spuštění testu se zobrazí, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a803c-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="a803c-151">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="a803c-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="a803c-152">Tento test provést napsáním kódu nejjednodušší v `Mathservice` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="a803c-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="a803c-153">V *jednotky – testování s fsharp* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="a803c-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="a803c-154">`dotnet test` Sestavení pro spuštění příkazu `MathService` projekt a potom `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="a803c-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="a803c-155">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="a803c-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="a803c-156">Předá.</span><span class="sxs-lookup"><span data-stu-id="a803c-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="a803c-157">Dokončuje požadavky</span><span class="sxs-lookup"><span data-stu-id="a803c-157">Completing the requirements</span></span>

<span data-ttu-id="a803c-158">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="a803c-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="a803c-159">Další jednoduchý případ funguje s pořadím, jehož jen liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="a803c-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="a803c-160">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="a803c-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="a803c-161">Tady je další testu:</span><span class="sxs-lookup"><span data-stu-id="a803c-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="a803c-162">Provádění `dotnet test` nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a803c-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="a803c-163">Je nutné aktualizovat `squaresOfOdds` metodu ke zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="a803c-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="a803c-164">Všechna sudá čísla mimo pořadí, aby tento test předat musí filtrovat.</span><span class="sxs-lookup"><span data-stu-id="a803c-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="a803c-165">Můžete to udělat tak, že funkce malé filtru zápisu a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="a803c-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="a803c-166">Všimněte si, že volání `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="a803c-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="a803c-167">Který vytváří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a803c-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="a803c-168">Existuje jeden další krok: čtvercové všech lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="a803c-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="a803c-169">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="a803c-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="a803c-170">Test můžete vyřešit přesměrujete filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý liché číslo:</span><span class="sxs-lookup"><span data-stu-id="a803c-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="a803c-171">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="a803c-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="a803c-172">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a803c-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="a803c-173">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="a803c-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
