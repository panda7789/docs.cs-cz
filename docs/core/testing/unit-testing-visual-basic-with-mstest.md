---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a MSTest
description: Další koncepty testů jednotek v .NET Core prostřednictvím vytváření ukázkové řešení jazyka Visual Basic podrobné interaktivní prostředí pomocí nástroje MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: cc4f84551d28ad531713e31a27df723a78b338cb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242461"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="dd29e-103">Testování knihovny jazyka Visual Basic .NET Core pomocí příkazu dotnet test a MStest</span><span class="sxs-lookup"><span data-stu-id="dd29e-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="dd29e-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="dd29e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="dd29e-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="dd29e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="dd29e-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="dd29e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="dd29e-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="dd29e-107">Creating the source project</span></span>

<span data-ttu-id="dd29e-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="dd29e-108">Open a shell window.</span></span> <span data-ttu-id="dd29e-109">Vytvořte adresář s názvem *jednotky – testování – vb-mstest* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="dd29e-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="dd29e-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="dd29e-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="dd29e-111">Tento postup usnadňuje správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="dd29e-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="dd29e-112">V adresáři řešení, vytvářet *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="dd29e-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="dd29e-113">Jaký máte následující strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="dd29e-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="dd29e-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="dd29e-115">Přejmenovat *Class1.VB* k *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="dd29e-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="dd29e-116">Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="dd29e-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="dd29e-117">Vraťte do adresáře *jednotky – testování – vb použití stest* adresáře.</span><span class="sxs-lookup"><span data-stu-id="dd29e-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="dd29e-118">Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="dd29e-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="dd29e-119">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="dd29e-119">Creating the test project</span></span>

<span data-ttu-id="dd29e-120">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="dd29e-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="dd29e-121">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="dd29e-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="dd29e-122">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="dd29e-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="dd29e-123">Tento příkaz vytvoří testovací projekt, který používá MSTest jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="dd29e-124">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="dd29e-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="dd29e-125">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="dd29e-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="dd29e-126">`dotnet new` v předchozím kroku přidat MSTest a MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="dd29e-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="dd29e-127">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="dd29e-128">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="dd29e-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="dd29e-129">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="dd29e-130">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="dd29e-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="dd29e-131">Spustit [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *jednotky – testování – vb-mstest* adresáře.</span><span class="sxs-lookup"><span data-stu-id="dd29e-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="dd29e-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="dd29e-132">Creating the first test</span></span>

<span data-ttu-id="dd29e-133">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="dd29e-134">Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="dd29e-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="dd29e-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dd29e-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="dd29e-136">`<TestClass>` Atribut určuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="dd29e-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="dd29e-137">`<TestMethod>` Atribut označuje metodu, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="dd29e-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="dd29e-138">Z *jednotky – testování – vb-mstest*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="dd29e-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="dd29e-139">Nástroj test runner MSTest obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="dd29e-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="dd29e-140">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="dd29e-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="dd29e-141">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="dd29e-141">Your test fails.</span></span> <span data-ttu-id="dd29e-142">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="dd29e-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="dd29e-143">Tento test provést napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="dd29e-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="dd29e-144">V *jednotky – testování – vb-mstest* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="dd29e-145">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="dd29e-146">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="dd29e-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="dd29e-147">Předá.</span><span class="sxs-lookup"><span data-stu-id="dd29e-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="dd29e-148">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="dd29e-148">Adding more features</span></span>

<span data-ttu-id="dd29e-149">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="dd29e-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="dd29e-150">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="dd29e-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="dd29e-151">Tyto případy můžete přidat jako nové testy s `<TestMethod>` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="dd29e-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="dd29e-152">Existují jiné atributy MSTest, které umožňují také napsat sady podobné testování.</span><span class="sxs-lookup"><span data-stu-id="dd29e-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="dd29e-153">A `<DataTestMethod>` atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="dd29e-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="dd29e-154">Můžete použít `<DataRow>` atribut můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="dd29e-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="dd29e-155">Místo vytváření nové testy, platí tyto dva atributy k vytvoření jedné teorií.</span><span class="sxs-lookup"><span data-stu-id="dd29e-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="dd29e-156">Teorie je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="dd29e-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="dd29e-157">Spustit `dotnet test`, a dvě z nich selhání testů.</span><span class="sxs-lookup"><span data-stu-id="dd29e-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="dd29e-158">Chcete-li všechny průchodu testů, změňte `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="dd29e-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="dd29e-159">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="dd29e-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="dd29e-160">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="dd29e-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="dd29e-161">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="dd29e-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="dd29e-162">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="dd29e-163">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd29e-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
