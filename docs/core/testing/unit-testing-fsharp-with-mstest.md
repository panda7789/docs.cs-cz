---
title: Testování F# částí v .NET Core pomocí příkazu dotnet test a MSTest
description: Seznamte se s koncepty F# testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: d402d6a8e4d9285f7107d0cacaea9f00e1e9344b
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374182"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="4a5dc-103">Testování F# částí knihoven v .NET Core pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="4a5dc-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="4a5dc-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="4a5dc-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="4a5dc-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4a5dc-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="4a5dc-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="4a5dc-107">Creating the source project</span></span>

<span data-ttu-id="4a5dc-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-108">Open a shell window.</span></span> <span data-ttu-id="4a5dc-109">Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="4a5dc-110">V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="4a5dc-111">To usnadňuje správu knihovny tříd i projektu testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="4a5dc-112">V adresáři řešení vytvořte adresář *MathService* .</span><span class="sxs-lookup"><span data-stu-id="4a5dc-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="4a5dc-113">Struktura adresářů a souborů je tedy uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="4a5dc-114">Vytvořte *MathService* aktuální adresář a spusťte příkaz [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="4a5dc-115">Vytvoříte nefunkční implementaci služby Math Service:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="4a5dc-116">Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="4a5dc-117">Spusťte [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) , chcete-li přidat projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="4a5dc-118">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="4a5dc-118">Creating the test project</span></span>

<span data-ttu-id="4a5dc-119">Dále vytvořte adresář *MathService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="4a5dc-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="4a5dc-120">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="4a5dc-121">Nastavte adresář *MathService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="4a5dc-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="4a5dc-122">Tím se vytvoří testovací projekt, který jako testovací rozhraní používá MSTest.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="4a5dc-123">Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="4a5dc-124">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="4a5dc-125">`dotnet new`v předchozím kroku jsme přidali MSTest a MSTest Runner.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="4a5dc-126">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="4a5dc-127">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="4a5dc-128">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="4a5dc-129">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="4a5dc-130">Spusťte [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-with-FSharp* .</span><span class="sxs-lookup"><span data-stu-id="4a5dc-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="4a5dc-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="4a5dc-131">Creating the first test</span></span>

<span data-ttu-id="4a5dc-132">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="4a5dc-133">Otevřete *Tests. FS* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="4a5dc-134">`[<TestClass>]` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="4a5dc-135">`[<TestMethod>]` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="4a5dc-136">Z adresáře *Unit-Testing-with-FSharp* spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz pro sestavení testů a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="4a5dc-137">MSTest Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="4a5dc-138">`dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="4a5dc-139">Tyto dva testy znázorňují základní a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="4a5dc-140">`My test`projde a `Fail every time` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="4a5dc-141">Nyní vytvořte test pro `squaresOfOdds` metodu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="4a5dc-142">`squaresOfOdds` Metoda vrátí seznam čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="4a5dc-143">Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="4a5dc-144">Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="4a5dc-145">Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="4a5dc-146">Zde je tento test:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="4a5dc-147">Všimněte si, `expected` že se sekvence převedla na seznam.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="4a5dc-148">Knihovna MSTest spoléhá na mnoho standardních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="4a5dc-149">Tato závislost znamená, že vaše veřejné rozhraní a očekávané výsledky <xref:System.Collections.ICollection> podporují spíše <xref:System.Collections.IEnumerable>než.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="4a5dc-150">Když spustíte test, uvidíte, že test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="4a5dc-151">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="4a5dc-152">Proveďte tento test průchodu vytvořením nejjednoduššího kódu `Mathservice` ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="4a5dc-153">V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="4a5dc-154">Příkaz spustí sestavení `MathService` pro`MathService.Tests` projekt a potom pro projekt. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="4a5dc-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="4a5dc-155">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="4a5dc-156">Předá.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="4a5dc-157">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="4a5dc-157">Completing the requirements</span></span>

<span data-ttu-id="4a5dc-158">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="4a5dc-159">Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo `1`je.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="4a5dc-160">Číslo 1 je snazší, protože čtvercem 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="4a5dc-161">Následující test:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="4a5dc-162">Spuštění `dotnet test` selhalo v novém testu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="4a5dc-163">Je nutné aktualizovat `squaresOfOdds` metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="4a5dc-164">Chcete-li provést tento test, je nutné vyfiltrovat všechna sudá čísla mimo sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="4a5dc-165">Můžete to udělat tak, že napíšete malou funkci filtru `Seq.filter`a použijete:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="4a5dc-166">Všimněte si volání `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="4a5dc-167">Tím se vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="4a5dc-168">K dispozici je ještě ještě jeden krok: čtverce každé liché číslice.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="4a5dc-169">Začněte zápisem nového testu:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="4a5dc-170">Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="4a5dc-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="4a5dc-171">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="4a5dc-172">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="4a5dc-173">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a5dc-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
