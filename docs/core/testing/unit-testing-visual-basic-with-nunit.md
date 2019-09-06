---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a NUnit
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
ms.custom: seodec18
ms.openlocfilehash: c48b2777b451598a0f3ccbb383d702d0069ff6ff
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373821"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="ecf7d-103">Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="ecf7d-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="ecf7d-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ecf7d-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="ecf7d-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ecf7d-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="ecf7d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecf7d-107">Prerequisites</span></span>

- <span data-ttu-id="ecf7d-108">[.NET Core 2,1 SDK](https://www.microsoft.com/net/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="ecf7d-109">Textový editor nebo Editor kódu dle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="ecf7d-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="ecf7d-110">Creating the source project</span></span>

<span data-ttu-id="ecf7d-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-111">Open a shell window.</span></span> <span data-ttu-id="ecf7d-112">Vytvořte adresář s názvem *Unit-Testing-VB-nunit* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="ecf7d-113">V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="ecf7d-114">Potom vytvořte adresář *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="ecf7d-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="ecf7d-115">Následující osnova znázorňuje strukturu souborů tak daleko:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="ecf7d-116">Vytvořte *PrimeService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="ecf7d-117">Přejmenujte *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="ecf7d-118">Vytvoříte selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="ecf7d-119">Změňte adresář zpátky na adresář *testování částí-VB-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="ecf7d-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="ecf7d-120">Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="ecf7d-121">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="ecf7d-121">Creating the test project</span></span>

<span data-ttu-id="ecf7d-122">Dále vytvořte adresář *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="ecf7d-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="ecf7d-123">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="ecf7d-124">Vytvořte adresář *PrimeService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="ecf7d-125">Příkaz [dotnet New](../tools/dotnet-new.md) vytvoří testovací projekt, který jako knihovnu testů používá nunit.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="ecf7d-126">Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeServiceTests. vbproj* :</span><span class="sxs-lookup"><span data-stu-id="ecf7d-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="ecf7d-127">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ecf7d-128">`dotnet new`v předchozím kroku jste přidali NUnit a testovací adaptér NUnit.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="ecf7d-129">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="ecf7d-130">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="ecf7d-131">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="ecf7d-132">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="ecf7d-133">Spusťte následující příkaz v adresáři *Unit-Testing-VB-nunit* :</span><span class="sxs-lookup"><span data-stu-id="ecf7d-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="ecf7d-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="ecf7d-134">Creating the first test</span></span>

<span data-ttu-id="ecf7d-135">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="ecf7d-136">V adresáři *PrimeService. Tests* přejmenujte soubor *UnitTest1. vb* na *PrimeService_IsPrimeShould. vb* a nahraďte jeho celý obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="ecf7d-137">`<TestFixture>` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="ecf7d-138">`<Test>` Atribut označuje metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="ecf7d-139">Z rutiny *testování částí-VB-nunit*spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz pro sestavení testů a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ecf7d-140">NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ecf7d-141">`dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ecf7d-142">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-142">Your test fails.</span></span> <span data-ttu-id="ecf7d-143">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="ecf7d-144">Proveďte tento test průchodu vytvořením nejjednoduššího kódu `PrimeService` ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="ecf7d-145">V adresáři *Unit-Testing-VB-nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ecf7d-146">Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="ecf7d-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="ecf7d-147">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ecf7d-148">Předá.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="ecf7d-149">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="ecf7d-149">Adding more features</span></span>

<span data-ttu-id="ecf7d-150">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ecf7d-151">Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="ecf7d-152">Tyto případy můžete přidat jako nové testy s `<Test>` atributem, ale to se rychle bude zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="ecf7d-153">Existují další atributy xUnit, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="ecf7d-154">`<TestCase>` Atribut představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="ecf7d-155">`<TestCase>` Atribut můžete použít k zadání hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="ecf7d-156">Namísto vytváření nových testů, použijte tyto dva atributy k vytvoření řady testů, které testují několik hodnot menší než dvě, což je nejnižší číslo základny:</span><span class="sxs-lookup"><span data-stu-id="ecf7d-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="ecf7d-157">Spuštění `dotnet test`a dva z těchto testů selžou.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="ecf7d-158">Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku `Main` metody v souboru *PrimeServices.cs* :</span><span class="sxs-lookup"><span data-stu-id="ecf7d-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="ecf7d-159">Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="ecf7d-160">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="ecf7d-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="ecf7d-161">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ecf7d-162">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ecf7d-163">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecf7d-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
