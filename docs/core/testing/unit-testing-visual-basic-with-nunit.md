---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a NUnit
description: Další koncepty testů jednotek v .NET Core prostřednictvím vytváření ukázkové řešení jazyka Visual Basic podrobné interaktivní prostředí pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: cf8a81241c93a6eeecf04052aba57750774aa050
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397509"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="08c86-103">Testování pomocí příkazu dotnet test a NUnit knihovny jazyka Visual Basic .NET Core</span><span class="sxs-lookup"><span data-stu-id="08c86-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="08c86-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="08c86-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="08c86-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="08c86-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="08c86-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="08c86-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08c86-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08c86-107">Prerequisites</span></span>

- <span data-ttu-id="08c86-108">[Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="08c86-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="08c86-109">Textového editoru nebo editoru kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="08c86-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="08c86-110">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="08c86-110">Creating the source project</span></span>

<span data-ttu-id="08c86-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="08c86-111">Open a shell window.</span></span> <span data-ttu-id="08c86-112">Vytvořte adresář s názvem *jednotky – testování – vb-nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="08c86-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="08c86-113">Uvnitř tohoto nového adresáře spuštěním následujícího příkazu vytvořte nový soubor řešení pro knihovny tříd a testovacího projektu:</span><span class="sxs-lookup"><span data-stu-id="08c86-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="08c86-114">Dále vytvořte *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="08c86-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="08c86-115">Následující osnovy zatím znázorňuje strukturu souboru:</span><span class="sxs-lookup"><span data-stu-id="08c86-115">The following outline shows the file structure so far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="08c86-116">Ujistěte se, *PrimeService* aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="08c86-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="08c86-117">Přejmenovat *Class1.VB* k *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="08c86-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="08c86-118">Vytvoření selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="08c86-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="08c86-119">Vraťte do adresáře *jednotky – testování – vb použití mstest* adresáře.</span><span class="sxs-lookup"><span data-stu-id="08c86-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="08c86-120">Spusťte následující příkaz pro přidání do řešení projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="08c86-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="08c86-121">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="08c86-121">Creating the test project</span></span>

<span data-ttu-id="08c86-122">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="08c86-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="08c86-123">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="08c86-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="08c86-124">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="08c86-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="08c86-125">[Dotnet nové](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="08c86-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="08c86-126">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.vbproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="08c86-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="08c86-127">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="08c86-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="08c86-128">`dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="08c86-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="08c86-129">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="08c86-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="08c86-130">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="08c86-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="08c86-131">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="08c86-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="08c86-132">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="08c86-132">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="08c86-133">Spusťte následující příkaz v *jednotky – testování – vb-nunit* adresáře:</span><span class="sxs-lookup"><span data-stu-id="08c86-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="08c86-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="08c86-134">Creating the first test</span></span>

<span data-ttu-id="08c86-135">Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje.</span><span class="sxs-lookup"><span data-stu-id="08c86-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="08c86-136">V *PrimeService.Tests* adresáře, přejmenovat *UnitTest1.vb* do souboru *PrimeService_IsPrimeShould.VB* a jeho celý obsah nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="08c86-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="08c86-137">`<TestFixture>` Atribut určuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="08c86-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="08c86-138">`<Test>` Atribut označuje metodu, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="08c86-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="08c86-139">Z *jednotky – testování – vb-nunit*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="08c86-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="08c86-140">Nástroj test runner NUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="08c86-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="08c86-141">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="08c86-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="08c86-142">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="08c86-142">Your test fails.</span></span> <span data-ttu-id="08c86-143">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="08c86-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="08c86-144">Tento test provést napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="08c86-144">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="08c86-145">V *jednotky – testování – vb-nunit* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="08c86-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="08c86-146">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="08c86-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="08c86-147">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="08c86-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="08c86-148">Předá.</span><span class="sxs-lookup"><span data-stu-id="08c86-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="08c86-149">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="08c86-149">Adding more features</span></span>

<span data-ttu-id="08c86-150">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="08c86-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="08c86-151">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="08c86-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="08c86-152">Tyto případy můžete přidat jako nové testy s `<Test>` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="08c86-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="08c86-153">Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování.</span><span class="sxs-lookup"><span data-stu-id="08c86-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="08c86-154">A `<TestCase>` atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="08c86-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="08c86-155">Můžete použít `<TestCase>` atribut můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="08c86-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="08c86-156">Místo vytváření nové testy, platí tyto dva atributy k vytvoření série testů, které testují několik hodnot, které jsou kratší než dvě, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="08c86-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="08c86-157">Spustit `dotnet test`, a dvě z nich selhání testů.</span><span class="sxs-lookup"><span data-stu-id="08c86-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="08c86-158">Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `Main` metoda ve *PrimeServices.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="08c86-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="08c86-159">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="08c86-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="08c86-160">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="08c86-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="08c86-161">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="08c86-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="08c86-162">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="08c86-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="08c86-163">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="08c86-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
