---
title: 'Testování knihovny F # v .NET Core pomocí testovacích dotnet a NUnit částí'
description: 'Další koncepty testů jednotek pro F # v .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a NUnit.'
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs:
- fsharp
ms.prod: .net-core
ms.openlocfilehash: c38be75ff39fae3afd371a5a3a9332ee5ac96022
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="6940f-103">Testování knihovny F # v .NET Core pomocí testovacích dotnet a NUnit částí</span><span class="sxs-lookup"><span data-stu-id="6940f-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="6940f-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="6940f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="6940f-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="6940f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="6940f-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6940f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="6940f-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="6940f-107">Creating the source project</span></span>

<span data-ttu-id="6940f-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="6940f-108">Open a shell window.</span></span> <span data-ttu-id="6940f-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="6940f-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="6940f-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení.</span><span class="sxs-lookup"><span data-stu-id="6940f-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="6940f-111">Díky tomu je snazší správa knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="6940f-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="6940f-112">V adresáři řešení vytvořit *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="6940f-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="6940f-113">Strukturu adresáře a souboru proto mnohem je zobrazena níže:</span><span class="sxs-lookup"><span data-stu-id="6940f-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="6940f-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="6940f-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="6940f-115">Pokud chcete používat testy řízený vývoj (TDD), vytvoříte selhání implementace matematické služby:</span><span class="sxs-lookup"><span data-stu-id="6940f-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="6940f-116">Změna adresáře zpět do *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="6940f-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="6940f-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="6940f-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="6940f-118">Šablona projektu NUnit instalace</span><span class="sxs-lookup"><span data-stu-id="6940f-118">Install the NUnit project template</span></span>

<span data-ttu-id="6940f-119">NUnit testování projektu, který je potřeba nainstalovat před vytvořením testovacího projektu šablony.</span><span class="sxs-lookup"><span data-stu-id="6940f-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="6940f-120">To jenom je nutné provést jednou na každém počítači vývojáře, kde vytvoříte nové projekty NUnit.</span><span class="sxs-lookup"><span data-stu-id="6940f-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="6940f-121">Spustit [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) instalovat NUnit šablony.</span><span class="sxs-lookup"><span data-stu-id="6940f-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="6940f-122">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="6940f-122">Creating the test project</span></span>

<span data-ttu-id="6940f-123">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="6940f-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="6940f-124">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="6940f-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="6940f-125">Ujistěte se, *MathService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new nunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="6940f-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="6940f-126">Tím se vytvoří testovací projekt, který používá NUnit jako rozhraní test.</span><span class="sxs-lookup"><span data-stu-id="6940f-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="6940f-127">Nástroj test runner v nakonfiguruje vygenerované šablony *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="6940f-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="6940f-128">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="6940f-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="6940f-129">`dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptéru.</span><span class="sxs-lookup"><span data-stu-id="6940f-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="6940f-130">Nyní přidejte `MathService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="6940f-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="6940f-131">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="6940f-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="6940f-132">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="6940f-132">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="6940f-133">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="6940f-133">You have the following final solution layout:</span></span>

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

<span data-ttu-id="6940f-134">Spuštění [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="6940f-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="6940f-135">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="6940f-135">Creating the first test</span></span>

<span data-ttu-id="6940f-136">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="6940f-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="6940f-137">Otevřete *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6940f-137">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="6940f-138">`[<TestFixture>]` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="6940f-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="6940f-139">`[<Test>]` Atribut označuje testovací metodu, která spustí nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="6940f-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="6940f-140">Z *jednotky – testování s fsharp* adresáře, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="6940f-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="6940f-141">Nástroj test runner NUnit obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="6940f-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="6940f-142">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="6940f-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="6940f-143">Tyto dva testy zobrazit nejzákladnější, předávání a selhání testy.</span><span class="sxs-lookup"><span data-stu-id="6940f-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="6940f-144">`My test` úspěšně projde, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="6940f-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="6940f-145">Teď vytvořte testu pro `squaresOfOdds` metoda.</span><span class="sxs-lookup"><span data-stu-id="6940f-145">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="6940f-146">`squaresOfOdds` Metoda vrátí pořadí kvadratických hodnot liché celé číslo, které jsou součástí vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="6940f-146">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="6940f-147">Místo došlo k pokusu o zápis všechny tyto funkce najednou, můžete vytvořit interaktivně testy, které ověřit funkčnost.</span><span class="sxs-lookup"><span data-stu-id="6940f-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="6940f-148">Provedení každého testu předat znamená vytváření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="6940f-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="6940f-149">Nejjednodušší testu jsme může zapisovat je volání `squaresOfOdds` s všechna čísla sudé, kde výsledkem by měl být prázdnou sekvencí celých čísel.</span><span class="sxs-lookup"><span data-stu-id="6940f-149">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="6940f-150">Tady je testu:</span><span class="sxs-lookup"><span data-stu-id="6940f-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="6940f-151">Všimněte si, že `expected` pořadí byl převeden na seznamu.</span><span class="sxs-lookup"><span data-stu-id="6940f-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="6940f-152">Rozhraní framework NUnit spoléhá na mnoho standardní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="6940f-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="6940f-153">Aby závislost znamená, že veřejné rozhraní a očekávaných výsledků podporu <xref:System.Collections.ICollection> místo <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="6940f-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="6940f-154">Při spuštění testu, uvidíte, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="6940f-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="6940f-155">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="6940f-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="6940f-156">Psaní kódu nejjednodušší v, aby tento test `Mathservice` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="6940f-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="6940f-157">V *jednotky – testování s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="6940f-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="6940f-158">`dotnet test` Příkaz spustí sestavení pro `MathService` projektu a pak `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="6940f-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="6940f-159">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="6940f-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="6940f-160">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="6940f-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="6940f-161">Požadavky na dokončení</span><span class="sxs-lookup"><span data-stu-id="6940f-161">Completing the requirements</span></span>

<span data-ttu-id="6940f-162">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="6940f-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="6940f-163">Další jednoduché případ funguje s pořadím, jejichž pouze liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="6940f-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="6940f-164">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="6940f-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="6940f-165">Zde je další testu:</span><span class="sxs-lookup"><span data-stu-id="6940f-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="6940f-166">Provádění `dotnet test` nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="6940f-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="6940f-167">Je nutné aktualizovat `squaresOfOdds` metodu ke zpracování tento nový test.</span><span class="sxs-lookup"><span data-stu-id="6940f-167">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="6940f-168">Musí filtrovat všechna čísla sudé mimo pořadí, aby tento test předat.</span><span class="sxs-lookup"><span data-stu-id="6940f-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="6940f-169">Můžete to udělat tak, že zápis funkce malé filtru a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="6940f-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="6940f-170">Všimněte si volání `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="6940f-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="6940f-171">Který vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6940f-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="6940f-172">Neexistuje jeden krok přejdete: Čtvereček každý liché čísel.</span><span class="sxs-lookup"><span data-stu-id="6940f-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="6940f-173">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="6940f-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="6940f-174">Můžete je vyřešit test tím filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý lichý počet:</span><span class="sxs-lookup"><span data-stu-id="6940f-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="6940f-175">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="6940f-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="6940f-176">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="6940f-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="6940f-177">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="6940f-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
