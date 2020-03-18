---
title: Testování částí visual basicu v rozhraní .NET Core s dotnet testem a NUnit
description: Naučte koncepty testování částí v .NET Core prostřednictvím interaktivní prostředí vytváření ukázkové řešení jazyka krok za krokem pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240919"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="5e5e8-103">Testování částí knihoven Jazyka .NET Core pomocí dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="5e5e8-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="5e5e8-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5e5e8-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="5e5e8-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5e5e8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="5e5e8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e5e8-107">Prerequisites</span></span>

- <span data-ttu-id="5e5e8-108">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="5e5e8-109">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="5e5e8-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="5e5e8-110">Creating the source project</span></span>

<span data-ttu-id="5e5e8-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-111">Open a shell window.</span></span> <span data-ttu-id="5e5e8-112">Vytvořte adresář s názvem *unit-testing-vb-nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="5e5e8-113">V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="5e5e8-114">Dále vytvořte adresář *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="5e5e8-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="5e5e8-115">Následující osnova ukazuje strukturu souborů tak daleko:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="5e5e8-116">Vytvořte *primeservice* jako aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="5e5e8-117">Přejmenujte *třídu 1.VB* na *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="5e5e8-118">Můžete vytvořit selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="5e5e8-119">Změňte adresář zpět do adresáře *unit-testing-vb-using-mstest.*</span><span class="sxs-lookup"><span data-stu-id="5e5e8-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="5e5e8-120">Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="5e5e8-121">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="5e5e8-121">Creating the test project</span></span>

<span data-ttu-id="5e5e8-122">Dále vytvořte adresář *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="5e5e8-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5e5e8-123">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="5e5e8-124">Vytvořte adresář *PrimeService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="5e5e8-125">[Dotnet new](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako testovací knihovnu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="5e5e8-126">Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeServiceTests.vbproj:*</span><span class="sxs-lookup"><span data-stu-id="5e5e8-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="5e5e8-127">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5e5e8-128">`dotnet new`v předchozím kroku přidánn NUnit a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="5e5e8-129">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5e5e8-130">Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="5e5e8-131">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="5e5e8-132">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-132">You have the following final solution layout:</span></span>

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

<span data-ttu-id="5e5e8-133">V adresáři *unit-testing-vb-nunit proveďte* následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="5e5e8-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="5e5e8-134">Creating the first test</span></span>

<span data-ttu-id="5e5e8-135">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5e5e8-136">V adresáři *PrimeService.Tests* přejmenujte soubor *UnitTest1.vb* na *PrimeService_IsPrimeShould.VB* a nahraďte celý jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="5e5e8-137">Atribut `<TestFixture>` označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="5e5e8-138">Atribut `<Test>` označuje metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="5e5e8-139">Z *jednotky unit-testing-vb-nunit*spusťte [`dotnet test`](../tools/dotnet-test.md) k sestavení testů a knihovny tříd a spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5e5e8-140">Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5e5e8-141">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5e5e8-142">Váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-142">Your test fails.</span></span> <span data-ttu-id="5e5e8-143">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="5e5e8-144">Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="5e5e8-145">V adresáři *unit-testing-vb-nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5e5e8-146">Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5e5e8-147">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5e5e8-148">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5e5e8-149">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="5e5e8-149">Adding more features</span></span>

<span data-ttu-id="5e5e8-150">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5e5e8-151">Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5e5e8-152">Tyto případy můžete přidat jako `<Test>` nové testy s atributem, ale to se rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5e5e8-153">Existují další atributy xUnit, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="5e5e8-154">Atribut `<TestCase>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="5e5e8-155">`<TestCase>` Atribut můžete použít k určení hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="5e5e8-156">Namísto vytváření nových testů použijte tyto dva atributy k vytvoření řady testů, které testují několik hodnot menší než dvě, což je nejnižší prvočíslo:</span><span class="sxs-lookup"><span data-stu-id="5e5e8-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="5e5e8-157">Spustit `dotnet test`a dva z těchto testů nezdaří.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="5e5e8-158">Chcete-li provést všechny testy `if` projít, změňte `Main` klauzuli na začátku metody v *souboru PrimeServices.cs:*</span><span class="sxs-lookup"><span data-stu-id="5e5e8-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="5e5e8-159">Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5e5e8-160">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="5e5e8-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="5e5e8-161">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5e5e8-162">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5e5e8-163">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e5e8-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
