---
title: 'Testování částí F # v .NET Core pomocí příkazu dotnet test a NUnit'
description: 'Seznamte se s koncepty testování částí jazyka F # v .NET Core prostřednictvím interaktivního prostředí vytvářejícího ukázkové řešení pomocí příkazu dotnet test a NUnit.'
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 9a1b4bb7e5e705cf1c71cd44827d4a2e0a3f8cf6
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656472"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="32ce2-103">Testování částí knihoven F # v .NET Core pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="32ce2-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="32ce2-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="32ce2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="32ce2-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="32ce2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="32ce2-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="32ce2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="32ce2-107">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="32ce2-107">Prerequisites</span></span>

- <span data-ttu-id="32ce2-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="32ce2-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="32ce2-109">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="32ce2-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="32ce2-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="32ce2-110">Creating the source project</span></span>

<span data-ttu-id="32ce2-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="32ce2-111">Open a shell window.</span></span> <span data-ttu-id="32ce2-112">Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="32ce2-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="32ce2-113">V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="32ce2-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="32ce2-114">Potom vytvořte adresář *MathService* .</span><span class="sxs-lookup"><span data-stu-id="32ce2-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="32ce2-115">Následující osnova ukazuje strukturu adresářů a souborů, které jsou tak daleko:</span><span class="sxs-lookup"><span data-stu-id="32ce2-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="32ce2-116">Vytvořte *MathService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="32ce2-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="32ce2-117">Vytvoříte nefunkční implementaci služby Math Service:</span><span class="sxs-lookup"><span data-stu-id="32ce2-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="32ce2-118">Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp.</span><span class="sxs-lookup"><span data-stu-id="32ce2-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="32ce2-119">Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:</span><span class="sxs-lookup"><span data-stu-id="32ce2-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="32ce2-120">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="32ce2-120">Creating the test project</span></span>

<span data-ttu-id="32ce2-121">Dále vytvořte adresář *MathService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="32ce2-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="32ce2-122">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="32ce2-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="32ce2-123">Vytvořte adresář *MathService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="32ce2-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="32ce2-124">Tím se vytvoří testovací projekt, který jako testovací rozhraní používá NUnit.</span><span class="sxs-lookup"><span data-stu-id="32ce2-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="32ce2-125">Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:</span><span class="sxs-lookup"><span data-stu-id="32ce2-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="32ce2-126">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="32ce2-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="32ce2-127">`dotnet new` v předchozím kroku jste přidali NUnit a testovací adaptér NUnit.</span><span class="sxs-lookup"><span data-stu-id="32ce2-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="32ce2-128">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="32ce2-129">Použijte `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="32ce2-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="32ce2-130">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="32ce2-131">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="32ce2-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="32ce2-132">Spusťte následující příkaz v adresáři *Unit-Testing-with-FSharp* :</span><span class="sxs-lookup"><span data-stu-id="32ce2-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="32ce2-133">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="32ce2-133">Creating the first test</span></span>

<span data-ttu-id="32ce2-134">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="32ce2-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="32ce2-135">Otevřete *UnitTest1. FS* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="32ce2-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="32ce2-136">`[<TestFixture>]`Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="32ce2-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="32ce2-137">`[<Test>]`Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="32ce2-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="32ce2-138">Z adresáře *Unit-Testing-with-FSharp* spusťte příkaz `dotnet test` pro sestavení testů a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="32ce2-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="32ce2-139">NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="32ce2-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="32ce2-140">`dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="32ce2-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="32ce2-141">Tyto dva testy znázorňují základní a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="32ce2-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="32ce2-142">`My test` projde a `Fail every time` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="32ce2-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="32ce2-143">Nyní vytvořte test pro `squaresOfOdds` metodu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="32ce2-144">`squaresOfOdds`Metoda vrací sekvenci čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="32ce2-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="32ce2-145">Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost.</span><span class="sxs-lookup"><span data-stu-id="32ce2-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="32ce2-146">Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="32ce2-147">Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.</span><span class="sxs-lookup"><span data-stu-id="32ce2-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="32ce2-148">Zde je tento test:</span><span class="sxs-lookup"><span data-stu-id="32ce2-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="32ce2-149">Všimněte si, že se `expected` sekvence převedla na seznam.</span><span class="sxs-lookup"><span data-stu-id="32ce2-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="32ce2-150">NUnit Framework spoléhá na mnoho standardních typů .NET.</span><span class="sxs-lookup"><span data-stu-id="32ce2-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="32ce2-151">Tato závislost znamená, že vaše veřejné rozhraní a očekávané výsledky podporují <xref:System.Collections.ICollection> spíše než <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="32ce2-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="32ce2-152">Když spustíte test, uvidíte, že test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="32ce2-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="32ce2-153">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="32ce2-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="32ce2-154">Proveďte tento test průchodu tak, že napíšete nejjednodušší kód v *knihovně Library. FS* v projektu MathService, který funguje:</span><span class="sxs-lookup"><span data-stu-id="32ce2-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="32ce2-155">V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="32ce2-156">`dotnet test`Příkaz spustí sestavení pro `MathService` projekt a potom pro `MathService.Tests` projekt.</span><span class="sxs-lookup"><span data-stu-id="32ce2-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="32ce2-157">Po sestavení obou projektů spustí vaše testy.</span><span class="sxs-lookup"><span data-stu-id="32ce2-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="32ce2-158">Dva testy proběhnou nyní.</span><span class="sxs-lookup"><span data-stu-id="32ce2-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="32ce2-159">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="32ce2-159">Completing the requirements</span></span>

<span data-ttu-id="32ce2-160">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="32ce2-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="32ce2-161">Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo je `1` .</span><span class="sxs-lookup"><span data-stu-id="32ce2-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="32ce2-162">Číslo 1 je snazší, protože čtvercem 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="32ce2-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="32ce2-163">Následující test:</span><span class="sxs-lookup"><span data-stu-id="32ce2-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="32ce2-164">Spuštění `dotnet test` selhalo v novém testu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="32ce2-165">Je nutné aktualizovat `squaresOfOdds` metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="32ce2-166">Chcete-li provést tento test, je nutné vyfiltrovat všechna sudá čísla mimo sekvenci.</span><span class="sxs-lookup"><span data-stu-id="32ce2-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="32ce2-167">Můžete to udělat tak, že napíšete malou funkci filtru a použijete `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="32ce2-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="32ce2-168">Všimněte si volání `Seq.toList` .</span><span class="sxs-lookup"><span data-stu-id="32ce2-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="32ce2-169">Tím se vytvoří seznam, který implementuje <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="32ce2-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="32ce2-170">K dispozici je ještě ještě jeden krok: čtverce každé liché číslice.</span><span class="sxs-lookup"><span data-stu-id="32ce2-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="32ce2-171">Začněte zápisem nového testu:</span><span class="sxs-lookup"><span data-stu-id="32ce2-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="32ce2-172">Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="32ce2-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="32ce2-173">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="32ce2-174">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="32ce2-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="32ce2-175">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="32ce2-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ce2-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32ce2-176">See also</span></span>

- [<span data-ttu-id="32ce2-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="32ce2-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="32ce2-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="32ce2-178">dotnet test</span></span>](../tools/dotnet-test.md)
