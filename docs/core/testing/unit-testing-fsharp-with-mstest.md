---
title: 'Jednotka knihovny F # testování v .NET Core pomocí testovacích dotnet a Mstestu'
description: 'Další koncepty testů jednotek pro F # v .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a Mstestu.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.openlocfilehash: 14e1ac54cb966e0e38c962e92cceb764fd8e9b42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218855"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="575b0-103">Jednotka knihovny F # testování v .NET Core pomocí testovacích dotnet a Mstestu</span><span class="sxs-lookup"><span data-stu-id="575b0-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="575b0-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="575b0-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="575b0-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="575b0-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="575b0-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="575b0-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="575b0-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="575b0-107">Creating the source project</span></span>

<span data-ttu-id="575b0-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="575b0-108">Open a shell window.</span></span> <span data-ttu-id="575b0-109">Vytvořte adresář s názvem *jednotky – testování s fsharp* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="575b0-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="575b0-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení.</span><span class="sxs-lookup"><span data-stu-id="575b0-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="575b0-111">Díky tomu je snazší správa knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="575b0-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="575b0-112">V adresáři řešení vytvořit *MathService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="575b0-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="575b0-113">Strukturu adresáře a souboru proto mnohem je zobrazena níže:</span><span class="sxs-lookup"><span data-stu-id="575b0-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="575b0-114">Ujistěte se, *MathService* aktuální adresář a spusťte [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="575b0-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="575b0-115">Pokud chcete používat testy řízený vývoj (TDD), vytvoříte selhání implementace matematické služby:</span><span class="sxs-lookup"><span data-stu-id="575b0-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="575b0-116">Změna adresáře zpět do *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="575b0-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="575b0-117">Spustit [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="575b0-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="575b0-118">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="575b0-118">Creating the test project</span></span>

<span data-ttu-id="575b0-119">Dále vytvořte *MathService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="575b0-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="575b0-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="575b0-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="575b0-121">Ujistěte se, *MathService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="575b0-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="575b0-122">Tím se vytvoří testovací projekt, který používá Mstestu jako rozhraní test.</span><span class="sxs-lookup"><span data-stu-id="575b0-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="575b0-123">Nástroj test runner v nakonfiguruje vygenerované šablony *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="575b0-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="575b0-124">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="575b0-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="575b0-125">`dotnet new` v předchozím kroku přidat Mstestu a Mstestu runner.</span><span class="sxs-lookup"><span data-stu-id="575b0-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="575b0-126">Nyní přidejte `MathService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="575b0-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="575b0-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="575b0-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="575b0-128">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="575b0-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="575b0-129">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="575b0-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="575b0-130">Spuštění [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) v *jednotky – testování s fsharp* adresáře.</span><span class="sxs-lookup"><span data-stu-id="575b0-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="575b0-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="575b0-131">Creating the first test</span></span>

<span data-ttu-id="575b0-132">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="575b0-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="575b0-133">Otevřete *Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="575b0-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="575b0-134">`[<TestClass>]` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="575b0-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="575b0-135">`[<TestMethod>]` Atribut označuje testovací metodu, která spustí nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="575b0-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="575b0-136">Z *jednotky – testování s fsharp* adresáře, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="575b0-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="575b0-137">Nástroj test runner Mstestu obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="575b0-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="575b0-138">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="575b0-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="575b0-139">Tyto dva testy zobrazit nejzákladnější, předávání a selhání testy.</span><span class="sxs-lookup"><span data-stu-id="575b0-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="575b0-140">`My test` úspěšně projde, a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="575b0-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="575b0-141">Teď vytvořte testu pro `squaresOfOdds` metoda.</span><span class="sxs-lookup"><span data-stu-id="575b0-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="575b0-142">`squaresOfOdds` Metoda vrátí seznam kvadratických hodnot liché celé číslo, které jsou součástí vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="575b0-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="575b0-143">Místo došlo k pokusu o zápis všechny tyto funkce najednou, můžete vytvořit interaktivně testy, které ověřit funkčnost.</span><span class="sxs-lookup"><span data-stu-id="575b0-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="575b0-144">Provedení každého testu předat znamená vytváření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="575b0-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="575b0-145">Nejjednodušší testu jsme může zapisovat je volání `squaresOfOdds` s všechna čísla sudé, kde výsledkem by měl být prázdnou sekvencí celých čísel.</span><span class="sxs-lookup"><span data-stu-id="575b0-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="575b0-146">Tady je testu:</span><span class="sxs-lookup"><span data-stu-id="575b0-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="575b0-147">Všimněte si, že `expected` pořadí byl převeden na seznamu.</span><span class="sxs-lookup"><span data-stu-id="575b0-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="575b0-148">Knihovna Mstestu spoléhá na mnoho standardní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="575b0-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="575b0-149">Aby závislost znamená, že veřejné rozhraní a očekávaných výsledků podporu <xref:System.Collections.ICollection> místo <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="575b0-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="575b0-150">Při spuštění testu, uvidíte, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="575b0-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="575b0-151">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="575b0-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="575b0-152">Psaní kódu nejjednodušší v, aby tento test `Mathservice` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="575b0-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="575b0-153">V *jednotky – testování s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="575b0-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="575b0-154">`dotnet test` Příkaz spustí sestavení pro `MathService` projektu a pak `MathService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="575b0-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="575b0-155">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="575b0-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="575b0-156">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="575b0-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="575b0-157">Požadavky na dokončení</span><span class="sxs-lookup"><span data-stu-id="575b0-157">Completing the requirements</span></span>

<span data-ttu-id="575b0-158">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="575b0-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="575b0-159">Další jednoduché případ funguje s pořadím, jejichž pouze liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="575b0-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="575b0-160">Číslo 1 je jednodušší, protože druhou mocninu 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="575b0-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="575b0-161">Zde je další testu:</span><span class="sxs-lookup"><span data-stu-id="575b0-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="575b0-162">Provádění `dotnet test` nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="575b0-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="575b0-163">Je nutné aktualizovat `squaresOfOdds` metodu ke zpracování tento nový test.</span><span class="sxs-lookup"><span data-stu-id="575b0-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="575b0-164">Musí filtrovat všechna čísla sudé mimo pořadí, aby tento test předat.</span><span class="sxs-lookup"><span data-stu-id="575b0-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="575b0-165">Můžete to udělat tak, že zápis funkce malé filtru a pomocí `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="575b0-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="575b0-166">Všimněte si volání `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="575b0-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="575b0-167">Který vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="575b0-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="575b0-168">Neexistuje jeden krok přejdete: Čtvereček každý liché čísel.</span><span class="sxs-lookup"><span data-stu-id="575b0-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="575b0-169">Začněte vytvořením nového testu:</span><span class="sxs-lookup"><span data-stu-id="575b0-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="575b0-170">Můžete je vyřešit test tím filtrované pořadí prostřednictvím operace mapy vypočítat druhou mocninu každý lichý počet:</span><span class="sxs-lookup"><span data-stu-id="575b0-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="575b0-171">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="575b0-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="575b0-172">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="575b0-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="575b0-173">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="575b0-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
