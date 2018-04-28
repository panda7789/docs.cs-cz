---
title: Testování C# s použitím Mstestu a .NET Core jednotky
description: Další koncepty test jednotky v C# a .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a Mstestu.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: fcc64bbbe00231442927023beff7dda670a3c567
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="fa8ea-103">Testování C# s použitím Mstestu a .NET Core jednotky</span><span class="sxs-lookup"><span data-stu-id="fa8ea-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="fa8ea-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="fa8ea-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="fa8ea-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="fa8ea-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="fa8ea-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="fa8ea-107">Creating the source project</span></span>

<span data-ttu-id="fa8ea-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-108">Open a shell window.</span></span> <span data-ttu-id="fa8ea-109">Vytvořte adresář s názvem *testování pomocí dotnet – testování* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="fa8ea-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) vytvořit nový soubor řešení pro knihovny tříd a k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="fa8ea-111">Dále vytvořte *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="fa8ea-112">Následující obrys doposud ukazuje strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="fa8ea-113">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="fa8ea-114">Přejmenování *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="fa8ea-115">Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="fa8ea-116">Změna adresáře zpět do *jednotky – testování pomocí mstestu* adresáře.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="fa8ea-117">Spustit [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="fa8ea-118">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="fa8ea-118">Creating the test project</span></span>

<span data-ttu-id="fa8ea-119">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="fa8ea-120">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="fa8ea-121">Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="fa8ea-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="fa8ea-122">Nový příkaz dotnet vytvoří testovací projekt, který používá Mstestu jako knihovně testu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="fa8ea-123">Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="fa8ea-124">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="fa8ea-125">`dotnet new` v předchozím kroku přidat testovat Mstestu SDK, Mstestu framework a runner Mstestu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="fa8ea-126">Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="fa8ea-127">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="fa8ea-128">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="fa8ea-129">Zobrazí následující osnova rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-129">The following outline shows the final solution layout:</span></span>

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

<span data-ttu-id="fa8ea-130">Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování pomocí dotnet – testování* adresáře.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="fa8ea-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="fa8ea-131">Creating the first test</span></span>

<span data-ttu-id="fa8ea-132">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="fa8ea-133">Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový soubor C# s s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

<span data-ttu-id="fa8ea-134">`[TestClass]` Atribut označuje třídu, která obsahuje testování částí.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="fa8ea-135">`[TestMethod]` Atribut uvádí, že je metoda metodou test.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="fa8ea-136">Uložte tento soubor a spusťte [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="fa8ea-137">Nástroj test runner Mstestu obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="fa8ea-138">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="fa8ea-139">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-139">Your test fails.</span></span> <span data-ttu-id="fa8ea-140">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="fa8ea-141">Ujistěte se, tento test předat napsáním kód nejjednodušší `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="fa8ea-142">V *jednotky – testování pomocí mstestu* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="fa8ea-143">`dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="fa8ea-144">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="fa8ea-145">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="fa8ea-146">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="fa8ea-146">Adding more features</span></span>

<span data-ttu-id="fa8ea-147">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="fa8ea-148">Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="fa8ea-149">Můžete přidat nové testování pomocí `[TestMethod]` atribut, ale které rychle stane zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="fa8ea-150">Existují další Mstestu atributy, které vám umožní zápisu sada testů, podobně jako.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="fa8ea-151">A `[DataTestMethod]`atribut představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="fa8ea-152">Můžete použít `[DataRow]` atribut zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="fa8ea-153">Místo vytváření nové testů, platí tyto dva atributy pro vytvoření testu jedné řízených daty.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="fa8ea-154">Test řízených daty je metoda, která porovná několik hodnoty menší než dva, což je s nejnižším číslem prime::</span><span class="sxs-lookup"><span data-stu-id="fa8ea-154">The data driven test is a method that tests several values less than two, which is the lowest prime number: :</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="fa8ea-155">Spustit `dotnet test`, a dvě z nich testy nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="fa8ea-156">Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="fa8ea-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="fa8ea-157">Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="fa8ea-158">Máte [dokončení verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [dokončení implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="fa8ea-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="fa8ea-159">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="fa8ea-160">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="fa8ea-161">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="fa8ea-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
