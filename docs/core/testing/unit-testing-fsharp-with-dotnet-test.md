---
title: Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek pro F# v .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 5f76f1b3117737616d94b3d6c9a2f397c3f66567
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170571"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="3c61b-103">Testování částí F# knihoven v .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="3c61b-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="3c61b-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="3c61b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3c61b-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="3c61b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="3c61b-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="3c61b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3c61b-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="3c61b-107">Creating the source project</span></span>

<span data-ttu-id="3c61b-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="3c61b-108">Open a shell window.</span></span> <span data-ttu-id="3c61b-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="3c61b-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="3c61b-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="3c61b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3c61b-111">Díky tomu usnadňují správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="3c61b-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="3c61b-112">V adresáři řešení, vytvářet *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="3c61b-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="3c61b-113">Struktura adresářů a souborů je dosavadním vidíte níže:</span><span class="sxs-lookup"><span data-stu-id="3c61b-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="3c61b-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="3c61b-115">Použití vývoj řízený testováním (TDD), vytvoříte selhání provádění matematických služby:</span><span class="sxs-lookup"><span data-stu-id="3c61b-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="3c61b-116">Vraťte do adresáře *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="3c61b-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="3c61b-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="3c61b-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="3c61b-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="3c61b-118">Creating the test project</span></span>

<span data-ttu-id="3c61b-119">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="3c61b-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="3c61b-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="3c61b-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="3c61b-121">Ujistěte se, *MathService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="3c61b-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3c61b-122">Tím se vytvoří projekt testů, který používá xUnit jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="3c61b-123">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="3c61b-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="3c61b-124">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="3c61b-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3c61b-125">`dotnet new` v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="3c61b-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="3c61b-126">Teď přidejte `MathService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="3c61b-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="3c61b-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="3c61b-128">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="3c61b-129">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="3c61b-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="3c61b-130">Spustit [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="3c61b-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="3c61b-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="3c61b-131">Creating the first test</span></span>

<span data-ttu-id="3c61b-132">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="3c61b-133">Otevřít *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="3c61b-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="3c61b-134">`[<Fact>]` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="3c61b-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="3c61b-135">Z *jednotky – testování s fsharp*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="3c61b-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3c61b-136">Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="3c61b-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3c61b-137">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="3c61b-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3c61b-138">Tyto dva testy zobrazit naprosto základní předáním hodnoty a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="3c61b-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="3c61b-139">`My test` úspěšně proběhne, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="3c61b-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="3c61b-140">Teď vytvořte test `squaresOfOdds` metody.</span><span class="sxs-lookup"><span data-stu-id="3c61b-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="3c61b-141">`squaresOfOdds` Metoda vrátí sekvenci druhých mocnin hodnot liché celé číslo, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="3c61b-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="3c61b-142">Namísto pokusu o zápis všechny tyto funkce současně, můžete interaktivně vytvořit testy, které ověří funkčnost.</span><span class="sxs-lookup"><span data-stu-id="3c61b-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="3c61b-143">Provedení každého testu předat znamená vytvoření potřebné funkce k metodě.</span><span class="sxs-lookup"><span data-stu-id="3c61b-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="3c61b-144">Nejjednodušší nám můžete napsat test je volání `squaresOfOdds` s všechna sudá čísla, kde výsledkem by měl být k prázdné sekvenci celých čísel.</span><span class="sxs-lookup"><span data-stu-id="3c61b-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="3c61b-145">Tady je tento test:</span><span class="sxs-lookup"><span data-stu-id="3c61b-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="3c61b-146">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3c61b-146">Your test fails.</span></span> <span data-ttu-id="3c61b-147">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="3c61b-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="3c61b-148">Tento test provést napsáním kódu nejjednodušší v `MathService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="3c61b-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="3c61b-149">V *jednotky – testování s fsharp* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3c61b-150">`dotnet test` Sestavení pro spuštění příkazu `MathService` projekt a potom `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="3c61b-151">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="3c61b-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3c61b-152">Předá.</span><span class="sxs-lookup"><span data-stu-id="3c61b-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="3c61b-153">Dokončuje požadavky</span><span class="sxs-lookup"><span data-stu-id="3c61b-153">Completing the requirements</span></span>

<span data-ttu-id="3c61b-154">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="3c61b-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3c61b-155">Další jednoduchý případ funguje s pořadím, jehož jen liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="3c61b-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="3c61b-156">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="3c61b-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="3c61b-157">Tady je další testu:</span><span class="sxs-lookup"><span data-stu-id="3c61b-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="3c61b-158">Provádění `dotnet test` spouští testy a ukazuje, že nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3c61b-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="3c61b-159">Teď, aktualizovat `squaresOfOdds` metodu ke zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="3c61b-160">Filtrovat všechna sudá čísla mimo pořadí, aby tento test předat.</span><span class="sxs-lookup"><span data-stu-id="3c61b-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="3c61b-161">Můžete to udělat tak, že funkce malé filtru zápisu a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="3c61b-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="3c61b-162">Existuje jeden další krok: čtvercové všech lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="3c61b-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="3c61b-163">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="3c61b-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="3c61b-164">Test můžete vyřešit přesměrujete filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý liché číslo:</span><span class="sxs-lookup"><span data-stu-id="3c61b-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="3c61b-165">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="3c61b-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3c61b-166">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3c61b-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3c61b-167">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c61b-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
