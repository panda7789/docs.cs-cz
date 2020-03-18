---
title: Testování částí F# v rozhraní .NET Core s dotnet testem a xUnit
description: Naučte koncepty testování částí pro F# v .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5fe4a8faddd87334439513368f24d808abc58e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157307"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="f2d4c-103">Testování částí knihoven F# v rozhraní .NET Core pomocí dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="f2d4c-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="f2d4c-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="f2d4c-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="f2d4c-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f2d4c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="f2d4c-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="f2d4c-107">Creating the source project</span></span>

<span data-ttu-id="f2d4c-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-108">Open a shell window.</span></span> <span data-ttu-id="f2d4c-109">Vytvořte adresář s názvem *testování jednotky s fsharp* držet řešení.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="f2d4c-110">V tomto novém `dotnet new sln` adresáři spusťte a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="f2d4c-111">To usnadňuje správu knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="f2d4c-112">V adresáři řešení vytvořte adresář *MathService.*</span><span class="sxs-lookup"><span data-stu-id="f2d4c-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="f2d4c-113">Adresář a struktura souborů je zatím uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="f2d4c-114">Nastavení *mathservice* jako aktuálního `dotnet new classlib -lang "F#"` adresáře a spuštěním vytvořte zdrojový projekt.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="f2d4c-115">Vytvoříte selhávající implementaci matematické služby:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="f2d4c-116">Změňte adresář zpět do adresáře *testování jednotek s fsharp.*</span><span class="sxs-lookup"><span data-stu-id="f2d4c-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="f2d4c-117">Spuštěním `dotnet sln add .\MathService\MathService.fsproj` přidáte projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="f2d4c-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="f2d4c-118">Creating the test project</span></span>

<span data-ttu-id="f2d4c-119">Dále vytvořte adresář *MathService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="f2d4c-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="f2d4c-120">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="f2d4c-121">Vytvořte adresář *MathService.Tests* jako aktuální adresář `dotnet new xunit -lang "F#"`a vytvořte nový projekt pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="f2d4c-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="f2d4c-122">Tím se vytvoří testovací projekt, který používá xUnit jako testovací knihovnu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="f2d4c-123">Vygenerovaná šablona konfiguruje testovacího běžce v *mathservicetests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="f2d4c-124">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="f2d4c-125">`dotnet new`v předchozím kroku přidánxUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="f2d4c-126">Nyní přidejte `MathService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="f2d4c-127">Použijte `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="f2d4c-128">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="f2d4c-129">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="f2d4c-130">Spusťte `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` v adresáři *testování jednotky s fsharp.*</span><span class="sxs-lookup"><span data-stu-id="f2d4c-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="f2d4c-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="f2d4c-131">Creating the first test</span></span>

<span data-ttu-id="f2d4c-132">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="f2d4c-133">Otevřete *soubor Tests.fs* a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="f2d4c-134">Atribut `[<Fact>]` označuje testovací metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="f2d4c-135">Z *jednotky testování s fsharp*, `dotnet test` spusťte k sestavení testů a knihovny tříd a pak spustit testy.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="f2d4c-136">XUnit test runner obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="f2d4c-137">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="f2d4c-138">Tyto dva testy ukazují nejzákladnější absolvování a selhání testů.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="f2d4c-139">`My test`projde a `Fail every time` selže.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="f2d4c-140">Nyní vytvořte test `squaresOfOdds` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="f2d4c-141">Metoda `squaresOfOdds` vrátí posloupnost čtverců všech lichých celočíselných hodnot, které jsou součástí vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="f2d4c-142">Spíše než se snaží zapsat všechny tyto funkce najednou, můžete iterativně vytvořit testy, které ověřují funkce.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="f2d4c-143">Provedení každého průchodu test znamená vytvoření potřebné funkce pro metodu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="f2d4c-144">Nejjednodušší test, který můžeme napsat, je volat `squaresOfOdds` se všemi sudými čísly, kde by výsledkem měla být prázdná posloupnost celých čísel.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="f2d4c-145">Tady je ten test:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="f2d4c-146">Váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-146">Your test fails.</span></span> <span data-ttu-id="f2d4c-147">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="f2d4c-148">Proveďte tento test projít napsáním `MathService` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="f2d4c-149">V adresáři *testování jednotek s fsharp* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="f2d4c-150">Příkaz `dotnet test` spustí sestavení pro `MathService` projekt a `MathService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="f2d4c-151">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="f2d4c-152">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="f2d4c-153">Splnění požadavků</span><span class="sxs-lookup"><span data-stu-id="f2d4c-153">Completing the requirements</span></span>

<span data-ttu-id="f2d4c-154">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="f2d4c-155">Další jednoduchý případ pracuje s sekvencí, jejíž jediné liché číslo je `1`.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="f2d4c-156">Číslo 1 je jednodušší, protože čtverec 1 je 1.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="f2d4c-157">Zde je další test:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="f2d4c-158">Spuštění `dotnet test` spustí testy a ukáže, že nový test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="f2d4c-159">Nyní aktualizujte `squaresOfOdds` metodu pro zpracování tohoto nového testu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="f2d4c-160">Můžete filtrovat všechna sudá čísla z pořadí, aby tento test projít.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="f2d4c-161">Můžete to udělat tak, že napíšete malou funkci filtru a použijete: `Seq.filter`</span><span class="sxs-lookup"><span data-stu-id="f2d4c-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="f2d4c-162">Je před ním ještě jeden krok: srovnat každé z lichých čísel.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="f2d4c-163">Začněte napsáním nového testu:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="f2d4c-164">Test můžete opravit potrubím filtrované sekvence pomocí operace mapy pro výpočet čtverce každého lichého čísla:</span><span class="sxs-lookup"><span data-stu-id="f2d4c-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="f2d4c-165">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="f2d4c-166">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="f2d4c-167">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2d4c-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2d4c-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2d4c-168">See also</span></span>

- [<span data-ttu-id="f2d4c-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f2d4c-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="f2d4c-170">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f2d4c-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="f2d4c-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="f2d4c-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="f2d4c-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f2d4c-172">dotnet test</span></span>](../tools/dotnet-test.md)
