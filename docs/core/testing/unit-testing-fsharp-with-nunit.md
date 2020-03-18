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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="3de13-103">Testování částí knihoven F# v rozhraní .NET Core pomocí dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="3de13-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="3de13-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="3de13-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3de13-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="3de13-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="3de13-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="3de13-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="3de13-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3de13-107">Prerequisites</span></span>

- <span data-ttu-id="3de13-108">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="3de13-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="3de13-109">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="3de13-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3de13-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="3de13-110">Creating the source project</span></span>

<span data-ttu-id="3de13-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="3de13-111">Open a shell window.</span></span> <span data-ttu-id="3de13-112">Vytvořte adresář s názvem *testování jednotky s fsharp* držet řešení.</span><span class="sxs-lookup"><span data-stu-id="3de13-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="3de13-113">V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="3de13-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="3de13-114">Dále vytvořte adresář *MathService.*</span><span class="sxs-lookup"><span data-stu-id="3de13-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="3de13-115">Následující osnova ukazuje adresář a strukturu souborů tak daleko:</span><span class="sxs-lookup"><span data-stu-id="3de13-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="3de13-116">Vytvořte *mathservice* jako aktuální adresář a vytvořte zdrojový projekt následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="3de13-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="3de13-117">Vytvoření selhání implementace matematické služby:</span><span class="sxs-lookup"><span data-stu-id="3de13-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="3de13-118">Změňte adresář zpět do adresáře *testování jednotek s fsharp.*</span><span class="sxs-lookup"><span data-stu-id="3de13-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="3de13-119">Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3de13-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="3de13-120">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="3de13-120">Creating the test project</span></span>

<span data-ttu-id="3de13-121">Dále vytvořte adresář *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="3de13-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="3de13-122">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="3de13-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="3de13-123">Vytvořte adresář *MathService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="3de13-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="3de13-124">Tím se vytvoří testovací projekt, který používá NUnit jako testovací rámec.</span><span class="sxs-lookup"><span data-stu-id="3de13-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="3de13-125">Vygenerovaná šablona konfiguruje testovacího běžce v *mathservicetests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="3de13-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="3de13-126">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="3de13-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3de13-127">`dotnet new`v předchozím kroku přidánn NUnit a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="3de13-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="3de13-128">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="3de13-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="3de13-129">Použijte `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="3de13-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="3de13-130">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="3de13-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="3de13-131">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="3de13-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="3de13-132">V adresáři *testování jednotky s fsharp* proveďte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3de13-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="3de13-133">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="3de13-133">Creating the first test</span></span>

<span data-ttu-id="3de13-134">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="3de13-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="3de13-135">Otevřete *unittest1.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="3de13-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="3de13-136">Atribut `[<TestFixture>]` označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="3de13-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="3de13-137">Atribut `[<Test>]` označuje testovací metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="3de13-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="3de13-138">Z adresáře *testování jednotky s fsharp* spusťte `dotnet test` k sestavení testů a knihovny tříd a spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="3de13-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3de13-139">Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="3de13-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3de13-140">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="3de13-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3de13-141">Tyto dva testy ukazují nejzákladnější absolvování a selhání testů.</span><span class="sxs-lookup"><span data-stu-id="3de13-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="3de13-142">`My test`projde a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="3de13-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="3de13-143">Nyní vytvořte test `squaresOfOdds` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="3de13-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="3de13-144">Metoda `squaresOfOdds` vrátí posloupnost čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="3de13-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="3de13-145">Spíše než se snaží zapsat všechny tyto funkce najednou, můžete iterativně vytvořit testy, které ověřují funkce.</span><span class="sxs-lookup"><span data-stu-id="3de13-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="3de13-146">Provedení každého průchodu test znamená vytvoření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="3de13-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="3de13-147">Nejjednodušší test, který můžeme napsat, je volat `squaresOfOdds` se všemi sudými čísly, kde by výsledkem měla být prázdná posloupnost celých čísel.</span><span class="sxs-lookup"><span data-stu-id="3de13-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="3de13-148">Tady je ten test:</span><span class="sxs-lookup"><span data-stu-id="3de13-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3de13-149">Všimněte `expected` si, že sekvence byla převedena na seznam.</span><span class="sxs-lookup"><span data-stu-id="3de13-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="3de13-150">NUnit framework spoléhá na mnoho standardních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="3de13-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="3de13-151">Tato závislost znamená, že vaše veřejné <xref:System.Collections.ICollection> rozhraní <xref:System.Collections.IEnumerable>a očekávané výsledky podporují spíše než .</span><span class="sxs-lookup"><span data-stu-id="3de13-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="3de13-152">Při spuštění testu uvidíte, že váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3de13-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="3de13-153">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="3de13-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="3de13-154">Proveďte tento test projít napsáním nejjednodušší kód ve třídě *Library.fs* v projektu MathService, který funguje:</span><span class="sxs-lookup"><span data-stu-id="3de13-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="3de13-155">V adresáři *testování jednotek s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="3de13-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3de13-156">Příkaz `dotnet test` spustí sestavení pro `MathService` projekt a `MathService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="3de13-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="3de13-157">Po sestavení obou projektů spustí testy.</span><span class="sxs-lookup"><span data-stu-id="3de13-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="3de13-158">Dva testy teď jsou pryč.</span><span class="sxs-lookup"><span data-stu-id="3de13-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="3de13-159">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="3de13-159">Completing the requirements</span></span>

<span data-ttu-id="3de13-160">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="3de13-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3de13-161">Další jednoduchý případ pracuje s sekvencí, jejíž jediné liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="3de13-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="3de13-162">Číslo 1 je jednodušší, protože čtverec 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="3de13-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="3de13-163">Zde je další test:</span><span class="sxs-lookup"><span data-stu-id="3de13-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3de13-164">Spuštění `dotnet test` se nezdaří nový test.</span><span class="sxs-lookup"><span data-stu-id="3de13-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="3de13-165">Je nutné `squaresOfOdds` aktualizovat metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="3de13-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="3de13-166">Je nutné filtrovat všechna sudá čísla z pořadí, aby tento test prošel.</span><span class="sxs-lookup"><span data-stu-id="3de13-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="3de13-167">Můžete to udělat tak, že napíšete malou funkci filtru a použijete: `Seq.filter`</span><span class="sxs-lookup"><span data-stu-id="3de13-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="3de13-168">Všimněte si `Seq.toList`volání .</span><span class="sxs-lookup"><span data-stu-id="3de13-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="3de13-169">Tím se vytvoří seznam, <xref:System.Collections.ICollection> který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3de13-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="3de13-170">Je před ním ještě jeden krok: srovnat každé z lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="3de13-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="3de13-171">Začněte napsáním nového testu:</span><span class="sxs-lookup"><span data-stu-id="3de13-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="3de13-172">Test můžete opravit potrubím filtrované sekvence pomocí operace mapy pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="3de13-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="3de13-173">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="3de13-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3de13-174">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3de13-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3de13-175">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="3de13-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="3de13-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="3de13-176">See also</span></span>

- [<span data-ttu-id="3de13-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3de13-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="3de13-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3de13-178">dotnet test</span></span>](../tools/dotnet-test.md)
