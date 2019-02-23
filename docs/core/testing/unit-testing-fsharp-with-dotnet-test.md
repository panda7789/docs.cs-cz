---
title: Testování částí F# v .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek pro F# v .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 9765c463bb427f79dcd0308e7e4fc643fdc06968
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745943"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="ff3b1-103">Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="ff3b1-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="ff3b1-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ff3b1-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="ff3b1-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ff3b1-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ff3b1-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="ff3b1-107">Creating the source project</span></span>

<span data-ttu-id="ff3b1-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-108">Open a shell window.</span></span> <span data-ttu-id="ff3b1-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="ff3b1-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="ff3b1-111">Díky tomu usnadňují správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="ff3b1-112">V adresáři řešení, vytvářet *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="ff3b1-113">Struktura adresářů a souborů je dosavadním vidíte níže:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="ff3b1-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="ff3b1-115">Vytvoříte selhání provádění matematických služby:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="ff3b1-116">Vraťte do adresáře *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="ff3b1-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="ff3b1-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="ff3b1-118">Creating the test project</span></span>

<span data-ttu-id="ff3b1-119">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="ff3b1-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="ff3b1-121">Ujistěte se, *MathService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="ff3b1-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ff3b1-122">Tím se vytvoří projekt testů, který používá xUnit jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="ff3b1-123">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="ff3b1-124">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ff3b1-125">`dotnet new` v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="ff3b1-126">Teď přidejte `MathService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="ff3b1-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="ff3b1-128">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="ff3b1-129">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="ff3b1-130">Spustit [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="ff3b1-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="ff3b1-131">Creating the first test</span></span>

<span data-ttu-id="ff3b1-132">Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="ff3b1-133">Otevřít *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="ff3b1-134">`[<Fact>]` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="ff3b1-135">Z *jednotky – testování s fsharp*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ff3b1-136">Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ff3b1-137">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ff3b1-138">Tyto dva testy zobrazit naprosto základní předáním hodnoty a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="ff3b1-139">`My test` úspěšně proběhne, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="ff3b1-140">Teď vytvořte test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="ff3b1-141">`squaresOfOdds` Metoda vrátí sekvenci druhých mocnin hodnot liché celé číslo, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="ff3b1-142">Namísto pokusu o zápis všechny tyto funkce současně, můžete interaktivně vytvořit testy, které ověří funkčnost.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="ff3b1-143">Provedení každého testu předat znamená vytvoření potřebné funkce k metodě.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="ff3b1-144">Nejjednodušší nám můžete napsat test je volání `squaresOfOdds` s všechna sudá čísla, kde výsledkem by měl být k prázdné sekvenci celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="ff3b1-145">Tady je tento test:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="ff3b1-146">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-146">Your test fails.</span></span> <span data-ttu-id="ff3b1-147">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="ff3b1-148">Tento test provést napsáním kódu nejjednodušší v `MathService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="ff3b1-149">V *jednotky – testování s fsharp* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ff3b1-150">`dotnet test` Sestavení pro spuštění příkazu `MathService` projekt a potom `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="ff3b1-151">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ff3b1-152">Předá.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="ff3b1-153">Dokončuje požadavky</span><span class="sxs-lookup"><span data-stu-id="ff3b1-153">Completing the requirements</span></span>

<span data-ttu-id="ff3b1-154">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ff3b1-155">Další jednoduchý případ funguje s pořadím, jehož jen liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="ff3b1-156">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="ff3b1-157">Tady je další testu:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="ff3b1-158">Provádění `dotnet test` spouští testy a ukazuje, že nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="ff3b1-159">Teď, aktualizovat `squaresOfOdds` metodu ke zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="ff3b1-160">Filtrovat všechna sudá čísla mimo pořadí, aby tento test předat.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="ff3b1-161">Můžete to udělat tak, že funkce malé filtru zápisu a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="ff3b1-162">Existuje jeden další krok: čtvercové všech lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="ff3b1-163">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="ff3b1-164">Test můžete vyřešit přesměrujete filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý liché číslo:</span><span class="sxs-lookup"><span data-stu-id="ff3b1-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="ff3b1-165">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ff3b1-166">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ff3b1-167">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff3b1-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
