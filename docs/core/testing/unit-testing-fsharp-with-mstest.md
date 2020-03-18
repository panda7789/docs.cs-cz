---
title: Testování částí F# v rozhraní .NET Core s dotnet testem a MSTest
description: Naučte koncepty testování částí pro F# v .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: a685ed8a56393fb6e1c1b9400f0ed4bcef15f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714281"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="bcccc-103">Testování částí knihoven F# v rozhraní .NET Core pomocí dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="bcccc-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="bcccc-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="bcccc-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="bcccc-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="bcccc-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="bcccc-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="bcccc-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="bcccc-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="bcccc-107">Creating the source project</span></span>

<span data-ttu-id="bcccc-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="bcccc-108">Open a shell window.</span></span> <span data-ttu-id="bcccc-109">Vytvořte adresář s názvem *testování jednotky s fsharp* držet řešení.</span><span class="sxs-lookup"><span data-stu-id="bcccc-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="bcccc-110">V tomto novém `dotnet new sln` adresáři spusťte a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="bcccc-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="bcccc-111">To usnadňuje správu knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="bcccc-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="bcccc-112">V adresáři řešení vytvořte adresář *MathService.*</span><span class="sxs-lookup"><span data-stu-id="bcccc-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="bcccc-113">Adresář a struktura souborů je zatím uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="bcccc-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="bcccc-114">Nastavení *mathservice* jako aktuálního adresáře a spuštění `dotnet new classlib -lang "F#"` pro vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-114">Make *MathService* the current directory and run `dotnet new classlib -lang "F#"` to create the source project.</span></span>  <span data-ttu-id="bcccc-115">Vytvoříte selhávající implementaci matematické služby:</span><span class="sxs-lookup"><span data-stu-id="bcccc-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="bcccc-116">Změňte adresář zpět do adresáře *testování jednotek s fsharp.*</span><span class="sxs-lookup"><span data-stu-id="bcccc-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="bcccc-117">Spuštěním `dotnet sln add .\MathService\MathService.fsproj` přidáte projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="bcccc-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="bcccc-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="bcccc-118">Creating the test project</span></span>

<span data-ttu-id="bcccc-119">Dále vytvořte adresář *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="bcccc-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="bcccc-120">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="bcccc-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="bcccc-121">Vytvořte adresář *MathService.Tests* jako aktuální adresář `dotnet new mstest -lang "F#"`a vytvořte nový projekt pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="bcccc-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new mstest -lang "F#"`.</span></span> <span data-ttu-id="bcccc-122">Tím se vytvoří testovací projekt, který používá MSTest jako testovací rámec.</span><span class="sxs-lookup"><span data-stu-id="bcccc-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="bcccc-123">Vygenerovaná šablona konfiguruje testovacího běžce v *mathservicetests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="bcccc-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="bcccc-124">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="bcccc-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="bcccc-125">`dotnet new`v předchozím kroku přidánm MSTest a MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="bcccc-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="bcccc-126">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="bcccc-127">Použijte `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="bcccc-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="bcccc-128">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="bcccc-129">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="bcccc-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="bcccc-130">Spusťte `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` v adresáři *testování jednotky s fsharp.*</span><span class="sxs-lookup"><span data-stu-id="bcccc-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="bcccc-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="bcccc-131">Creating the first test</span></span>

<span data-ttu-id="bcccc-132">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="bcccc-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="bcccc-133">Otevřete *soubor Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bcccc-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="bcccc-134">Atribut `[<TestClass>]` označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="bcccc-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="bcccc-135">Atribut `[<TestMethod>]` označuje testovací metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="bcccc-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="bcccc-136">Z adresáře *testování jednotky s fsharp* spusťte `dotnet test` k sestavení testů a knihovny tříd a spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="bcccc-136">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="bcccc-137">Testovací běžec MSTest obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="bcccc-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="bcccc-138">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="bcccc-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="bcccc-139">Tyto dva testy ukazují nejzákladnější absolvování a selhání testů.</span><span class="sxs-lookup"><span data-stu-id="bcccc-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="bcccc-140">`My test`projde a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="bcccc-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="bcccc-141">Nyní vytvořte test `squaresOfOdds` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="bcccc-142">Metoda `squaresOfOdds` vrátí seznam čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="bcccc-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="bcccc-143">Spíše než se snaží zapsat všechny tyto funkce najednou, můžete iterativně vytvořit testy, které ověřují funkce.</span><span class="sxs-lookup"><span data-stu-id="bcccc-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="bcccc-144">Provedení každého průchodu test znamená vytvoření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="bcccc-145">Nejjednodušší test, který můžeme napsat, je volat `squaresOfOdds` se všemi sudými čísly, kde by výsledkem měla být prázdná posloupnost celých čísel.</span><span class="sxs-lookup"><span data-stu-id="bcccc-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="bcccc-146">Tady je ten test:</span><span class="sxs-lookup"><span data-stu-id="bcccc-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bcccc-147">Všimněte `expected` si, že sekvence byla převedena na seznam.</span><span class="sxs-lookup"><span data-stu-id="bcccc-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="bcccc-148">Knihovna MSTest závisí na mnoha standardních typech .NET.</span><span class="sxs-lookup"><span data-stu-id="bcccc-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="bcccc-149">Tato závislost znamená, že vaše veřejné <xref:System.Collections.ICollection> rozhraní <xref:System.Collections.IEnumerable>a očekávané výsledky podporují spíše než .</span><span class="sxs-lookup"><span data-stu-id="bcccc-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="bcccc-150">Při spuštění testu uvidíte, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bcccc-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="bcccc-151">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="bcccc-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="bcccc-152">Proveďte tento test projít napsáním `Mathservice` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="bcccc-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="bcccc-153">V adresáři *testování jednotek s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="bcccc-154">Příkaz `dotnet test` spustí sestavení pro `MathService` projekt a `MathService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="bcccc-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="bcccc-155">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="bcccc-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="bcccc-156">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="bcccc-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="bcccc-157">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="bcccc-157">Completing the requirements</span></span>

<span data-ttu-id="bcccc-158">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="bcccc-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="bcccc-159">Další jednoduchý případ pracuje s sekvencí, jejíž jediné liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="bcccc-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="bcccc-160">Číslo 1 je jednodušší, protože čtverec 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="bcccc-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="bcccc-161">Zde je další test:</span><span class="sxs-lookup"><span data-stu-id="bcccc-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bcccc-162">Spuštění `dotnet test` se nezdaří nový test.</span><span class="sxs-lookup"><span data-stu-id="bcccc-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="bcccc-163">Je nutné `squaresOfOdds` aktualizovat metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="bcccc-164">Je nutné filtrovat všechna sudá čísla z pořadí, aby tento test prošel.</span><span class="sxs-lookup"><span data-stu-id="bcccc-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="bcccc-165">Můžete to udělat tak, že napíšete malou funkci filtru a použijete: `Seq.filter`</span><span class="sxs-lookup"><span data-stu-id="bcccc-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="bcccc-166">Všimněte si `Seq.toList`volání .</span><span class="sxs-lookup"><span data-stu-id="bcccc-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="bcccc-167">Tím se vytvoří seznam, <xref:System.Collections.ICollection> který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bcccc-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="bcccc-168">Je před ním ještě jeden krok: srovnat každé z lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="bcccc-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="bcccc-169">Začněte napsáním nového testu:</span><span class="sxs-lookup"><span data-stu-id="bcccc-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bcccc-170">Test můžete opravit potrubím filtrované sekvence pomocí operace mapy pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="bcccc-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="bcccc-171">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="bcccc-172">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bcccc-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="bcccc-173">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="bcccc-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcccc-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcccc-174">See also</span></span>

- [<span data-ttu-id="bcccc-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bcccc-175">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="bcccc-176">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bcccc-176">dotnet sln</span></span>](../tools/dotnet-sln.md)
- [<span data-ttu-id="bcccc-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="bcccc-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="bcccc-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bcccc-178">dotnet test</span></span>](../tools/dotnet-test.md)
