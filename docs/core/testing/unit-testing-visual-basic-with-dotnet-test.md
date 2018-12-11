---
title: Testování částí pomocí jazyka Visual Basic v rozhraní .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek v .NET Core prostřednictvím vytváření ukázkové řešení jazyka Visual Basic podrobné interaktivní prostředí pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: eae5f0727d2d75044c072e8cc1d9a1c6faf53a9a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170532"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="e8ec2-103">Testování knihovny jazyka Visual Basic .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="e8ec2-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="e8ec2-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="e8ec2-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="e8ec2-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="e8ec2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="e8ec2-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="e8ec2-107">Creating the source project</span></span>

<span data-ttu-id="e8ec2-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-108">Open a shell window.</span></span> <span data-ttu-id="e8ec2-109">Vytvořte adresář s názvem *unit-testing-vb-using-dotnet-test* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="e8ec2-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="e8ec2-111">Tento postup usnadňuje správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="e8ec2-112">V adresáři řešení, vytvářet *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="e8ec2-113">Jaký máte následující strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="e8ec2-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="e8ec2-115">Přejmenovat *Class1.VB* k *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="e8ec2-116">Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="e8ec2-117">Vraťte do adresáře *unit-testing-vb-using-dotnet-test* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="e8ec2-118">Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="e8ec2-119">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="e8ec2-119">Creating the test project</span></span>

<span data-ttu-id="e8ec2-120">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="e8ec2-121">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="e8ec2-122">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="e8ec2-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="e8ec2-123">Tento příkaz vytvoří testovací projekt, který používá xUnit jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="e8ec2-124">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="e8ec2-125">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="e8ec2-126">`dotnet new` v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="e8ec2-127">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="e8ec2-128">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="e8ec2-129">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="e8ec2-130">Máte následující poslední složky rozložení:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-130">You have the following final folder layout:</span></span>

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

<span data-ttu-id="e8ec2-131">Spustit [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *unit-testing-vb-using-dotnet-test* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="e8ec2-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="e8ec2-132">Creating the first test</span></span>

<span data-ttu-id="e8ec2-133">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="e8ec2-134">Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="e8ec2-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="e8ec2-136">`<Fact>` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="e8ec2-137">Z *testování použití dotnet testování částí*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="e8ec2-138">Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="e8ec2-139">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="e8ec2-140">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-140">Your test fails.</span></span> <span data-ttu-id="e8ec2-141">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="e8ec2-142">Tento test provést napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="e8ec2-143">V *unit-testing-vb-using-dotnet-test* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="e8ec2-144">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="e8ec2-145">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="e8ec2-146">Předá.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="e8ec2-147">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="e8ec2-147">Adding more features</span></span>

<span data-ttu-id="e8ec2-148">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="e8ec2-149">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="e8ec2-150">Tyto případy můžete přidat jako nové testy s `<Fact>` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="e8ec2-151">Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="e8ec2-152">A `<Theory>` atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="e8ec2-153">Můžete použít `<InlineData>` atribut můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="e8ec2-154">Místo vytváření nové testy, platí tyto dva atributy k vytvoření jedné teorií.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="e8ec2-155">Teorie je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="e8ec2-156">Spustit `dotnet test`, a dvě z nich selhání testů.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="e8ec2-157">Chcete-li všechny průchodu testů, změňte `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="e8ec2-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="e8ec2-158">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="e8ec2-159">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="e8ec2-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="e8ec2-160">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="e8ec2-161">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="e8ec2-162">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8ec2-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
