---
title: Testování C# s použitím NUnit a .NET Core jednotky
description: Další koncepty test jednotky v C# a .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a NUnit.
keywords: NUnit, .NET, .NET Core
author: rprouse
ms.date: 12/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.openlocfilehash: b29912a58511305202a18e8da4ae57700605867a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="e220a-104">Testování C# s použitím NUnit a .NET Core jednotky</span><span class="sxs-lookup"><span data-stu-id="e220a-104">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="e220a-105">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="e220a-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="e220a-106">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="e220a-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="e220a-107">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="e220a-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="e220a-108">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="e220a-108">Creating the source project</span></span>

<span data-ttu-id="e220a-109">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="e220a-109">Open a shell window.</span></span> <span data-ttu-id="e220a-110">Vytvořte adresář s názvem *jednotky – testování pomocí nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="e220a-110">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="e220a-111">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) vytvořit nový soubor řešení pro knihovny tříd a k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="e220a-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="e220a-112">Dále vytvořte *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e220a-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="e220a-113">Následující obrys doposud ukazuje strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="e220a-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="e220a-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="e220a-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="e220a-115">Přejmenování *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="e220a-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="e220a-116">Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="e220a-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="e220a-117">Změna adresáře zpět do *jednotky – testování pomocí nunit* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e220a-117">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="e220a-118">Spustit [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="e220a-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="e220a-119">Šablona projektu NUnit instalace</span><span class="sxs-lookup"><span data-stu-id="e220a-119">Install the NUnit project template</span></span>

<span data-ttu-id="e220a-120">NUnit testování projektu, který je potřeba nainstalovat před vytvořením testovacího projektu šablony.</span><span class="sxs-lookup"><span data-stu-id="e220a-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="e220a-121">To jenom je nutné provést jednou na každém počítači vývojáře, kde vytvoříte nové projekty NUnit.</span><span class="sxs-lookup"><span data-stu-id="e220a-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="e220a-122">Spustit [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) instalovat NUnit šablony.</span><span class="sxs-lookup"><span data-stu-id="e220a-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="e220a-123">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="e220a-123">Creating the test project</span></span>

<span data-ttu-id="e220a-124">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e220a-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="e220a-125">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="e220a-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="e220a-126">Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new nunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="e220a-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="e220a-127">Nový příkaz dotnet vytvoří testovací projekt, který používá NUnit jako knihovně testu.</span><span class="sxs-lookup"><span data-stu-id="e220a-127">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="e220a-128">Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="e220a-128">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="e220a-129">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="e220a-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="e220a-130">`dotnet new` v předchozím kroku přidat Microsoft test SDK, rozhraní test NUnit a adaptér testovací NUnit.</span><span class="sxs-lookup"><span data-stu-id="e220a-130">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="e220a-131">Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="e220a-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="e220a-132">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="e220a-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="e220a-133">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="e220a-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="e220a-134">Zobrazí následující osnova rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="e220a-134">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="e220a-135">Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování pomocí dotnet – testování* adresáře.</span><span class="sxs-lookup"><span data-stu-id="e220a-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="e220a-136">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="e220a-136">Creating the first test</span></span>

<span data-ttu-id="e220a-137">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="e220a-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="e220a-138">Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový soubor C# s s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="e220a-138">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

<span data-ttu-id="e220a-139">`[TestFixture]` Atribut označuje třídu, která obsahuje testování částí.</span><span class="sxs-lookup"><span data-stu-id="e220a-139">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="e220a-140">`[Test]` Atribut uvádí, že je metoda metodou test.</span><span class="sxs-lookup"><span data-stu-id="e220a-140">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="e220a-141">Uložte tento soubor a spusťte [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="e220a-141">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="e220a-142">Nástroj test runner NUnit obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="e220a-142">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="e220a-143">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="e220a-143">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="e220a-144">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e220a-144">Your test fails.</span></span> <span data-ttu-id="e220a-145">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="e220a-145">You haven't created the implementation yet.</span></span> <span data-ttu-id="e220a-146">Ujistěte se, tento test předat napsáním kód nejjednodušší `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="e220a-146">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="e220a-147">V *jednotky – testování pomocí nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="e220a-147">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="e220a-148">`dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="e220a-148">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="e220a-149">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="e220a-149">After building both projects, it runs this single test.</span></span> <span data-ttu-id="e220a-150">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="e220a-150">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="e220a-151">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="e220a-151">Adding more features</span></span>

<span data-ttu-id="e220a-152">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="e220a-152">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="e220a-153">Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="e220a-153">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="e220a-154">Můžete přidat nové testování pomocí `[Test]` atribut, ale které rychle stane zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="e220a-154">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="e220a-155">Existují další NUnit atributy, které vám umožní zápisu sada testů, podobně jako.</span><span class="sxs-lookup"><span data-stu-id="e220a-155">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="e220a-156">A `[TestCase]` atribut se používá k vytvoření sada testů, které provést stejný kód, ale mají jinou vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="e220a-156">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="e220a-157">Můžete použít `[TestCase]` atribut zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="e220a-157">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="e220a-158">Místo vytváření nové testů, Použíjte tento atribut k vytvoření testu jedné řízených daty.</span><span class="sxs-lookup"><span data-stu-id="e220a-158">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="e220a-159">Řízených testovací daty je metoda, která porovná několik méně než dvě hodnoty, což je s nejnižším číslem prime:</span><span class="sxs-lookup"><span data-stu-id="e220a-159">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="e220a-160">Spustit `dotnet test`, a dvě z nich testy nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e220a-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="e220a-161">Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="e220a-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="e220a-162">Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní.</span><span class="sxs-lookup"><span data-stu-id="e220a-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="e220a-163">Máte [dokončení verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [dokončení implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="e220a-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="e220a-164">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="e220a-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="e220a-165">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="e220a-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="e220a-166">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="e220a-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
