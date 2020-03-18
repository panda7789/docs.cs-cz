---
title: Testování částí visual basicu v rozhraní .NET Core s dotnet testem a xUnit
description: Naučte koncepty testování částí v .NET Core prostřednictvím interaktivní hochu, který bude krok za krokem vytvářet ukázkové řešení jazyka Visual Basic pomocí dotnet Test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240945"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="9cc5d-103">Testování částí knihoven Jazyka .NET Core pomocí dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="9cc5d-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="9cc5d-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9cc5d-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) než začnete.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="9cc5d-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9cc5d-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="9cc5d-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="9cc5d-107">Creating the source project</span></span>

<span data-ttu-id="9cc5d-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-108">Open a shell window.</span></span> <span data-ttu-id="9cc5d-109">Vytvořte adresář s názvem *unit-testing-vb-using-dotnet-test* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="9cc5d-110">V tomto novém [`dotnet new sln`](../tools/dotnet-new.md) adresáři spusťte a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="9cc5d-111">Tento postup usnadňuje správu knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="9cc5d-112">V adresáři řešení vytvořte adresář *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="9cc5d-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="9cc5d-113">Zatím máte následující adresářovou a souborovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="9cc5d-114">Vytvořte *PrimeService* aktuální [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) adresář a spustit k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="9cc5d-115">Přejmenujte *třídu 1.VB* na *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="9cc5d-116">Můžete vytvořit selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="9cc5d-117">Změňte adresář zpět do adresáře *testování jednotky vb-using-dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="9cc5d-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="9cc5d-118">Spuštěním [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) přidáte projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="9cc5d-119">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="9cc5d-119">Creating the test project</span></span>

<span data-ttu-id="9cc5d-120">Dále vytvořte adresář *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="9cc5d-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="9cc5d-121">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="9cc5d-122">Vytvořte adresář *PrimeService.Tests* jako aktuální adresář [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)a vytvořte nový projekt pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="9cc5d-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9cc5d-123">Tento příkaz vytvoří testovací projekt, který používá xUnit jako testovací knihovnu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="9cc5d-124">Vygenerovaná šablona konfiguruje testovacího běžce v *souboru PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="9cc5d-125">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9cc5d-126">`dotnet new`v předchozím kroku přidánxUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="9cc5d-127">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="9cc5d-128">Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="9cc5d-129">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="9cc5d-130">Máte následující rozložení konečné složky:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-130">You have the following final folder layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="9cc5d-131">Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) v adresáři testování jednotky *vb-using-dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="9cc5d-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="9cc5d-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="9cc5d-132">Creating the first test</span></span>

<span data-ttu-id="9cc5d-133">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="9cc5d-134">Odeberte *soubor UnitTest1.vb* z adresáře *PrimeService.Tests* a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="9cc5d-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="9cc5d-136">Atribut `<Fact>` označuje testovací metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="9cc5d-137">Z *jednotky testování-using-dotnet-test*, [`dotnet test`](../tools/dotnet-test.md) provést k sestavení testů a knihovny tříd a potom spustit testy.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9cc5d-138">XUnit test runner obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9cc5d-139">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9cc5d-140">Váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-140">Your test fails.</span></span> <span data-ttu-id="9cc5d-141">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="9cc5d-142">Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="9cc5d-143">V adresáři *testování jednotky vb-using-dotnet-test* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9cc5d-144">Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="9cc5d-145">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9cc5d-146">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="9cc5d-147">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="9cc5d-147">Adding more features</span></span>

<span data-ttu-id="9cc5d-148">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9cc5d-149">Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="9cc5d-150">Tyto případy můžete přidat jako `<Fact>` nové testy s atributem, ale to se rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="9cc5d-151">Existují další atributy xUnit, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="9cc5d-152">Atribut `<Theory>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="9cc5d-153">`<InlineData>` Atribut můžete použít k určení hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="9cc5d-154">Namísto vytváření nových testů použijte tyto dva atributy k vytvoření jedné teorie.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="9cc5d-155">Teorie je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="9cc5d-156">Spustit `dotnet test`a dva z těchto testů nezdaří.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="9cc5d-157">Chcete-li provést všechny testy `if` projít, změňte klauzuli na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="9cc5d-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="9cc5d-158">Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="9cc5d-159">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="9cc5d-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="9cc5d-160">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9cc5d-161">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9cc5d-162">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="9cc5d-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
