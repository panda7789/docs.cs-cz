---
title: Testování C# s použitím NUnit a .NET Core
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 253e07c16740a39566cf37ee5742a32342c78c49
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746741"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="b28f8-103">Testování C# s použitím NUnit a .NET Core</span><span class="sxs-lookup"><span data-stu-id="b28f8-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="b28f8-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="b28f8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="b28f8-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="b28f8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="b28f8-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b28f8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b28f8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b28f8-107">Prerequisites</span></span>

- <span data-ttu-id="b28f8-108">[.NET core SDK 2.1 (vs. 2.1.400)](https://www.microsoft.com/net/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="b28f8-108">[.NET Core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="b28f8-109">Textového editoru nebo editoru kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="b28f8-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="b28f8-110">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="b28f8-110">Creating the source project</span></span>

<span data-ttu-id="b28f8-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="b28f8-111">Open a shell window.</span></span> <span data-ttu-id="b28f8-112">Vytvořte adresář s názvem *jednotky – testování použití nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="b28f8-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="b28f8-113">Uvnitř tohoto nového adresáře spuštěním následujícího příkazu vytvořte nový soubor řešení pro knihovny tříd a testovacího projektu:</span><span class="sxs-lookup"><span data-stu-id="b28f8-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="b28f8-114">Dále vytvořte *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="b28f8-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="b28f8-115">Následující osnovy zatím znázorňuje strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="b28f8-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="b28f8-116">Ujistěte se, *PrimeService* aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="b28f8-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="b28f8-117">Přejmenovat *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="b28f8-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="b28f8-118">Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="b28f8-118">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

<span data-ttu-id="b28f8-119">Vraťte do adresáře *jednotky – testování použití nunit* adresáře.</span><span class="sxs-lookup"><span data-stu-id="b28f8-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="b28f8-120">Spusťte následující příkaz pro přidání do řešení projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="b28f8-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="b28f8-121">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="b28f8-121">Creating the test project</span></span>

<span data-ttu-id="b28f8-122">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="b28f8-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="b28f8-123">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="b28f8-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="b28f8-124">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="b28f8-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="b28f8-125">[Dotnet nové](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="b28f8-126">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeService.Tests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="b28f8-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="b28f8-127">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="b28f8-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="b28f8-128">`dotnet new` v předchozím kroku přidat Microsoft test sady SDK, testovací rozhraní NUnit a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="b28f8-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="b28f8-129">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="b28f8-130">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="b28f8-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="b28f8-131">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="b28f8-132">Následující osnovy ukazuje rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="b28f8-132">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="b28f8-133">Spusťte následující příkaz v *testování použití dotnet testování částí* adresáře:</span><span class="sxs-lookup"><span data-stu-id="b28f8-133">Execute the following command in the *unit-testing-using-dotnet-test* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="b28f8-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="b28f8-134">Creating the first test</span></span>

<span data-ttu-id="b28f8-135">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-135">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="b28f8-136">V *PrimeService.Tests* adresáře, přejmenovat *UnitTest1.cs* do souboru *PrimeService_IsPrimeShould.cs* a jeho celý obsah nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b28f8-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="b28f8-137">`[TestFixture]` Atribut označuje třídu, která obsahuje testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="b28f8-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="b28f8-138">`[Test]` Atribut označuje, že metoda je testovací metodu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="b28f8-139">Tento soubor uložte a spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="b28f8-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="b28f8-140">Nástroj test runner NUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="b28f8-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="b28f8-141">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="b28f8-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="b28f8-142">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b28f8-142">Your test fails.</span></span> <span data-ttu-id="b28f8-143">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="b28f8-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="b28f8-144">Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="b28f8-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="b28f8-145">V *jednotky – testování použití nunit* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="b28f8-146">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="b28f8-147">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="b28f8-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="b28f8-148">Předá.</span><span class="sxs-lookup"><span data-stu-id="b28f8-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="b28f8-149">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="b28f8-149">Adding more features</span></span>

<span data-ttu-id="b28f8-150">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="b28f8-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="b28f8-151">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="b28f8-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="b28f8-152">Můžete přidat nové testy s `[Test]` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="b28f8-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="b28f8-153">Existují jiné NUnit atributy, které umožňují také napsat sady podobné testování.</span><span class="sxs-lookup"><span data-stu-id="b28f8-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="b28f8-154">A `[TestCase]` atribut se používá k vytvoření sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="b28f8-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="b28f8-155">Můžete použít `[TestCase]` atribut můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="b28f8-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="b28f8-156">Místo vytváření nové testy, Použíjte tento atribut pro vytvoření testu jedné řízené daty.</span><span class="sxs-lookup"><span data-stu-id="b28f8-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="b28f8-157">Test na základě dat je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="b28f8-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="b28f8-158">Spustit `dotnet test`, a dvě z nich selhání testů.</span><span class="sxs-lookup"><span data-stu-id="b28f8-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="b28f8-159">Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `Main` metoda ve *PrimeService.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="b28f8-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="b28f8-160">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="b28f8-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="b28f8-161">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="b28f8-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="b28f8-162">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="b28f8-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="b28f8-163">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b28f8-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="b28f8-164">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="b28f8-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
