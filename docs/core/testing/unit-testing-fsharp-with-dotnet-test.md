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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="32b04-103">Testování knihovny F # v .NET Core pomocí testovacích dotnet a xUnit částí</span><span class="sxs-lookup"><span data-stu-id="32b04-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="32b04-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="32b04-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="32b04-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="32b04-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="32b04-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="32b04-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="32b04-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="32b04-107">Creating the source project</span></span>

<span data-ttu-id="32b04-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="32b04-108">Open a shell window.</span></span> <span data-ttu-id="32b04-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="32b04-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="32b04-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení.</span><span class="sxs-lookup"><span data-stu-id="32b04-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="32b04-111">Díky tomu je snazší správa knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="32b04-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="32b04-112">V adresáři řešení vytvořit *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="32b04-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="32b04-113">Strukturu adresáře a souboru proto mnohem je zobrazena níže:</span><span class="sxs-lookup"><span data-stu-id="32b04-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="32b04-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="32b04-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="32b04-115">Pokud chcete používat testy řízený vývoj (TDD), vytvoříte selhání implementace matematické služby:</span><span class="sxs-lookup"><span data-stu-id="32b04-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="32b04-116">Změna adresáře zpět do *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="32b04-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="32b04-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="32b04-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="32b04-118">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="32b04-118">Creating the test project</span></span>

<span data-ttu-id="32b04-119">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="32b04-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="32b04-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="32b04-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="32b04-121">Ujistěte se, *MathService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="32b04-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="32b04-122">Tím se vytvoří testovací projekt, který používá xUnit jako knihovně testu.</span><span class="sxs-lookup"><span data-stu-id="32b04-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="32b04-123">Nástroj test runner v nakonfiguruje vygenerované šablony *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="32b04-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="32b04-124">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="32b04-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="32b04-125">`dotnet new` v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="32b04-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="32b04-126">Nyní přidejte `MathService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="32b04-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="32b04-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="32b04-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="32b04-128">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="32b04-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="32b04-129">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="32b04-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="32b04-130">Spuštění [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="32b04-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="32b04-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="32b04-131">Creating the first test</span></span>

<span data-ttu-id="32b04-132">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="32b04-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="32b04-133">Otevřete *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="32b04-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="32b04-134">`[<Fact>]` Atribut označuje testovací metodu, která spustí nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="32b04-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="32b04-135">Z *jednotky – testování s fsharp*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="32b04-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="32b04-136">Nástroj test runner xUnit obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="32b04-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="32b04-137">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="32b04-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="32b04-138">Tyto dva testy zobrazit nejzákladnější, předávání a selhání testy.</span><span class="sxs-lookup"><span data-stu-id="32b04-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="32b04-139">`My test` úspěšně projde, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="32b04-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="32b04-140">Teď vytvořte testu pro `squaresOfOdds` metoda.</span><span class="sxs-lookup"><span data-stu-id="32b04-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="32b04-141">`squaresOfOdds` Metoda vrátí pořadí kvadratických hodnot liché celé číslo, které jsou součástí vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="32b04-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="32b04-142">Místo došlo k pokusu o zápis všechny tyto funkce najednou, můžete vytvořit interaktivně testy, které ověřit funkčnost.</span><span class="sxs-lookup"><span data-stu-id="32b04-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="32b04-143">Provedení každého testu předat znamená vytváření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="32b04-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="32b04-144">Nejjednodušší testu jsme může zapisovat je volání `squaresOfOdds` s všechna čísla sudé, kde výsledkem by měl být prázdnou sekvencí celých čísel.</span><span class="sxs-lookup"><span data-stu-id="32b04-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="32b04-145">Tady je testu:</span><span class="sxs-lookup"><span data-stu-id="32b04-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="32b04-146">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="32b04-146">Your test fails.</span></span> <span data-ttu-id="32b04-147">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="32b04-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="32b04-148">Psaní kódu nejjednodušší v, aby tento test `MathService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="32b04-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="32b04-149">V *jednotky – testování s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="32b04-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="32b04-150">`dotnet test` Příkaz spustí sestavení pro `MathService` projektu a pak `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="32b04-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="32b04-151">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="32b04-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="32b04-152">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="32b04-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="32b04-153">Požadavky na dokončení</span><span class="sxs-lookup"><span data-stu-id="32b04-153">Completing the requirements</span></span>

<span data-ttu-id="32b04-154">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="32b04-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="32b04-155">Další jednoduché případ funguje s pořadím, jejichž pouze liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="32b04-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="32b04-156">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="32b04-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="32b04-157">Zde je další testu:</span><span class="sxs-lookup"><span data-stu-id="32b04-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="32b04-158">Provádění `dotnet test` spustí testy a ukazuje, že nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="32b04-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="32b04-159">Nyní, aktualizovat `squaresOfOdds` metodu ke zpracování tento nový test.</span><span class="sxs-lookup"><span data-stu-id="32b04-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="32b04-160">Filtrovat všechna čísla sudé mimo pořadí, aby tento test předat.</span><span class="sxs-lookup"><span data-stu-id="32b04-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="32b04-161">Můžete to udělat tak, že zápis funkce malé filtru a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="32b04-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="32b04-162">Neexistuje jeden krok přejdete: Čtvereček každý liché čísel.</span><span class="sxs-lookup"><span data-stu-id="32b04-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="32b04-163">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="32b04-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="32b04-164">Můžete je vyřešit test tím filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý lichý počet:</span><span class="sxs-lookup"><span data-stu-id="32b04-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="32b04-165">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="32b04-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="32b04-166">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="32b04-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="32b04-167">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="32b04-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
