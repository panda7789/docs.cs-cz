---
title: 'Testování částí F # v .NET Core pomocí příkazu dotnet test a xUnit'
description: 'Seznamte se s koncepty testování částí jazyka F # v .NET Core prostřednictvím interaktivního prostředí vytvářejícího ukázkové řešení pomocí příkazu dotnet test a xUnit.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: e0f2b6f88a650f412148f51cc0236fa46ed8c618
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656550"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="73b48-103">Testování částí knihoven F # v .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="73b48-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="73b48-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="73b48-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="73b48-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="73b48-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="73b48-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="73b48-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="73b48-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="73b48-107">Creating the source project</span></span>

<span data-ttu-id="73b48-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="73b48-108">Open a shell window.</span></span> <span data-ttu-id="73b48-109">Vytvořte adresář s názvem *Unit-Testing-with-FSharp* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="73b48-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="73b48-110">V tomto novém adresáři spusťte příkaz `dotnet new sln` a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="73b48-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="73b48-111">To usnadňuje správu knihovny tříd i projektu testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="73b48-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="73b48-112">V adresáři řešení vytvořte adresář *MathService* .</span><span class="sxs-lookup"><span data-stu-id="73b48-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="73b48-113">Struktura adresářů a souborů je tedy uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="73b48-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="73b48-114">Nastavte *MathService* na aktuální adresář a spusťte příkaz `dotnet new classlib -lang "F#"` k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="73b48-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="73b48-115">Vytvoříte nefunkční implementaci služby Math Service:</span><span class="sxs-lookup"><span data-stu-id="73b48-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="73b48-116">Změňte adresář zpátky na adresář *testování částí s* adresářem-FSharp.</span><span class="sxs-lookup"><span data-stu-id="73b48-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="73b48-117">Spusťte `dotnet sln add .\MathService\MathService.fsproj` , chcete-li přidat projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="73b48-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="73b48-118">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="73b48-118">Creating the test project</span></span>

<span data-ttu-id="73b48-119">Dále vytvořte adresář *MathService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="73b48-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="73b48-120">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="73b48-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="73b48-121">Nastavte adresář *MathService. Tests* na aktuální adresář a vytvořte nový projekt pomocí `dotnet new xunit -lang "F#"` .</span><span class="sxs-lookup"><span data-stu-id="73b48-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="73b48-122">Tím se vytvoří testovací projekt, který jako knihovnu testů používá xUnit.</span><span class="sxs-lookup"><span data-stu-id="73b48-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="73b48-123">Vygenerovaná šablona konfiguruje Test Runner v *MathServiceTests. fsproj*:</span><span class="sxs-lookup"><span data-stu-id="73b48-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="73b48-124">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="73b48-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="73b48-125">`dotnet new` v předchozím kroku jsme přidali xUnit a xUnit Runner.</span><span class="sxs-lookup"><span data-stu-id="73b48-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="73b48-126">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="73b48-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="73b48-127">Použijte `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="73b48-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="73b48-128">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="73b48-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="73b48-129">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="73b48-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="73b48-130">Spusťte `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` v adresáři *Unit-Testing-with-FSharp* .</span><span class="sxs-lookup"><span data-stu-id="73b48-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="73b48-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="73b48-131">Creating the first test</span></span>

<span data-ttu-id="73b48-132">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="73b48-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="73b48-133">Otevřete *Tests. FS* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="73b48-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="73b48-134">`[<Fact>]`Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="73b48-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="73b48-135">Z rutiny *testování částí-with-FSharp*spusťte `dotnet test` pro sestavení testů a knihovny tříd a potom spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="73b48-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="73b48-136">XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="73b48-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="73b48-137">`dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="73b48-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="73b48-138">Tyto dva testy znázorňují základní a neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="73b48-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="73b48-139">`My test` projde a `Fail every time` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="73b48-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="73b48-140">Nyní vytvořte test pro `squaresOfOdds` metodu.</span><span class="sxs-lookup"><span data-stu-id="73b48-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="73b48-141">`squaresOfOdds`Metoda vrací sekvenci čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="73b48-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="73b48-142">Místo toho, abyste se pokusili zapsat všechny tyto funkce najednou, můžete iteračním vytvořit testy, které ověřují funkčnost.</span><span class="sxs-lookup"><span data-stu-id="73b48-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="73b48-143">Provedení každého testovacího průchodu znamená vytvoření nezbytné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="73b48-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="73b48-144">Nejjednodušší test, který můžeme napsat, je zavolat `squaresOfOdds` se všemi sudými čísly, kde výsledek by měl být prázdná sekvence celých čísel.</span><span class="sxs-lookup"><span data-stu-id="73b48-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="73b48-145">Zde je tento test:</span><span class="sxs-lookup"><span data-stu-id="73b48-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="73b48-146">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="73b48-146">Your test fails.</span></span> <span data-ttu-id="73b48-147">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="73b48-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="73b48-148">Proveďte tento test průchodu vytvořením nejjednoduššího kódu ve `MathService` třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="73b48-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="73b48-149">V adresáři *Unit-Testing-with-FSharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="73b48-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="73b48-150">`dotnet test`Příkaz spustí sestavení pro `MathService` projekt a potom pro `MathService.Tests` projekt.</span><span class="sxs-lookup"><span data-stu-id="73b48-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="73b48-151">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="73b48-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="73b48-152">Předá.</span><span class="sxs-lookup"><span data-stu-id="73b48-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="73b48-153">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="73b48-153">Completing the requirements</span></span>

<span data-ttu-id="73b48-154">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="73b48-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="73b48-155">Následující jednoduchý případ funguje s posloupností, jejíž pouze liché číslo je `1` .</span><span class="sxs-lookup"><span data-stu-id="73b48-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="73b48-156">Číslo 1 je snazší, protože čtvercem 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="73b48-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="73b48-157">Následující test:</span><span class="sxs-lookup"><span data-stu-id="73b48-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="73b48-158">Spuštění `dotnet test` spustí testy a ukáže vás, že nový test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="73b48-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="73b48-159">Nyní aktualizujte `squaresOfOdds` metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="73b48-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="73b48-160">Vyfiltrujete všechna sudá čísla mimo sekvenci k provedení tohoto testu.</span><span class="sxs-lookup"><span data-stu-id="73b48-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="73b48-161">Můžete to udělat tak, že napíšete malou funkci filtru a použijete `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="73b48-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="73b48-162">K dispozici je ještě ještě jeden krok: čtverce každé liché číslice.</span><span class="sxs-lookup"><span data-stu-id="73b48-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="73b48-163">Začněte zápisem nového testu:</span><span class="sxs-lookup"><span data-stu-id="73b48-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="73b48-164">Test můžete vyřešit tak, že provedete vyfiltrování filtrované sekvence pomocí operace mapování pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="73b48-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="73b48-165">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="73b48-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="73b48-166">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="73b48-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="73b48-167">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="73b48-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="73b48-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73b48-168">See also</span></span>

- [<span data-ttu-id="73b48-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="73b48-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="73b48-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="73b48-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="73b48-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="73b48-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="73b48-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="73b48-172">dotnet test</span></span>](../tools/dotnet-test.md)
