---
title: Testování C# s MSTest a .NET Core
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: efeb12eb43539b0a85168b1162e0f8b94ad67e90
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257419"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="8de0c-103">Testování C# s MSTest a .NET Core</span><span class="sxs-lookup"><span data-stu-id="8de0c-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="8de0c-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="8de0c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="8de0c-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="8de0c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="8de0c-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8de0c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="8de0c-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="8de0c-107">Creating the source project</span></span>

<span data-ttu-id="8de0c-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="8de0c-108">Open a shell window.</span></span> <span data-ttu-id="8de0c-109">Vytvořte adresář s názvem *jednotky – testování použití mstest* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="8de0c-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="8de0c-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) vytvořte nový soubor řešení pro knihovny tříd a testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="8de0c-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="8de0c-111">Dále vytvořte *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="8de0c-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="8de0c-112">Následující osnovy doposud znázorňuje strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="8de0c-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="8de0c-113">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="8de0c-114">Přejmenovat *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="8de0c-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="8de0c-115">Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="8de0c-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="8de0c-116">Vraťte do adresáře *jednotky – testování použití mstest* adresáře.</span><span class="sxs-lookup"><span data-stu-id="8de0c-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="8de0c-117">Spustit [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="8de0c-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="8de0c-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="8de0c-118">Creating the test project</span></span>

<span data-ttu-id="8de0c-119">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="8de0c-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="8de0c-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="8de0c-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="8de0c-121">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="8de0c-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="8de0c-122">Nový příkaz dotnet vytvoří projekt testů, který používá MStest jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="8de0c-123">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="8de0c-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="8de0c-124">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="8de0c-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="8de0c-125">`dotnet new` v předchozím kroku přidat testovací sady SDK MSTest, MSTest rozhraní framework a MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="8de0c-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="8de0c-126">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="8de0c-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="8de0c-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="8de0c-128">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="8de0c-129">Následující osnovy ukazuje rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="8de0c-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="8de0c-130">Spustit [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování použití dotnet testování částí* adresáře.</span><span class="sxs-lookup"><span data-stu-id="8de0c-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="8de0c-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="8de0c-131">Creating the first test</span></span>

<span data-ttu-id="8de0c-132">Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="8de0c-133">Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresář a vytvořit nový soubor jazyka C# s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="8de0c-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="8de0c-134">`[TestClass]` Atribut označuje třídu, která obsahuje testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="8de0c-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="8de0c-135">`[TestMethod]` Atribut označuje, že metoda je testovací metodu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="8de0c-136">Tento soubor uložte a spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="8de0c-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="8de0c-137">Nástroj test runner MSTest obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="8de0c-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="8de0c-138">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="8de0c-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="8de0c-139">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8de0c-139">Your test fails.</span></span> <span data-ttu-id="8de0c-140">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="8de0c-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="8de0c-141">Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="8de0c-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="8de0c-142">V *jednotky – testování použití mstest* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="8de0c-143">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="8de0c-144">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="8de0c-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="8de0c-145">Předá.</span><span class="sxs-lookup"><span data-stu-id="8de0c-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="8de0c-146">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="8de0c-146">Adding more features</span></span>

<span data-ttu-id="8de0c-147">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="8de0c-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="8de0c-148">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="8de0c-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="8de0c-149">Můžete přidat nové testy s `[TestMethod]` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="8de0c-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="8de0c-150">Existují jiné atributy MSTest, které umožňují také napsat sady podobné testování.</span><span class="sxs-lookup"><span data-stu-id="8de0c-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="8de0c-151">A `[DataTestMethod]`atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="8de0c-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="8de0c-152">Můžete použít `[DataRow]` atribut můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="8de0c-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="8de0c-153">Místo vytváření nové testy, platí tyto dva atributy pro vytvoření testu jedné řízené daty.</span><span class="sxs-lookup"><span data-stu-id="8de0c-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="8de0c-154">Test na základě dat je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="8de0c-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="8de0c-155">Spustit `dotnet test`, a dvě z nich selhání testů.</span><span class="sxs-lookup"><span data-stu-id="8de0c-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="8de0c-156">Chcete-li všechny průchodu testů, změňte `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="8de0c-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="8de0c-157">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="8de0c-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="8de0c-158">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="8de0c-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="8de0c-159">Začlenění malé knihovny a sadu testů jednotek pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="8de0c-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="8de0c-160">Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8de0c-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="8de0c-161">Jste koncentrované většinu času a úsilí na řešení cíle aplikace.</span><span class="sxs-lookup"><span data-stu-id="8de0c-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
