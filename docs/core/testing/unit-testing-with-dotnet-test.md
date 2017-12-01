---
title: "Testování kódu C# v .NET Core pomocí testovacích dotnet a xUnit částí"
description: "Další koncepty test jednotky v C# a .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: a9e64fe37f05b7bbe05b1c5878e4b31084a1c8b6
ms.sourcegitcommit: 7296449e03f747528f9bc59954c74bf4e359cc1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="bcb89-103">Testování C# v .NET Core pomocí testovacích dotnet a xUnit částí</span><span class="sxs-lookup"><span data-stu-id="bcb89-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="bcb89-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="bcb89-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="bcb89-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="bcb89-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="bcb89-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="bcb89-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="bcb89-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="bcb89-107">Creating the source project</span></span>

<span data-ttu-id="bcb89-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="bcb89-108">Open a shell window.</span></span> <span data-ttu-id="bcb89-109">Vytvořte adresář s názvem *testování pomocí dotnet – testování* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="bcb89-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="bcb89-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení.</span><span class="sxs-lookup"><span data-stu-id="bcb89-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="bcb89-111">S řešením je snazší správa knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="bcb89-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="bcb89-112">V adresáři řešení vytvořit *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="bcb89-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="bcb89-113">Strukturu adresáře a souboru doposud by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="bcb89-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="bcb89-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="bcb89-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="bcb89-115">Přejmenování *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="bcb89-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="bcb89-116">Použití vývoje řízeného testováním (TDD), je nejprve vytvořit selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="bcb89-116">To use test-driven development (TDD), you first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="bcb89-117">Změnit adresář zpět do *testování pomocí dotnet – testování* adresáře.</span><span class="sxs-lookup"><span data-stu-id="bcb89-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="bcb89-118">Spustit [SLN – dotnet](../tools/dotnet-sln.md) příkaz pro přidání projektu knihovny tříd do řešení:</span><span class="sxs-lookup"><span data-stu-id="bcb89-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="bcb89-119">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="bcb89-119">Creating the test project</span></span>

<span data-ttu-id="bcb89-120">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="bcb89-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="bcb89-121">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="bcb89-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="bcb89-122">Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="bcb89-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="bcb89-123">Tento příkaz vytvoří testovací projekt, který používá xUnit jako knihovně testu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="bcb89-124">Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.csproj* souboru podobná následující kód:</span><span class="sxs-lookup"><span data-stu-id="bcb89-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="bcb89-125">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="bcb89-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="bcb89-126">`dotnet new`v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="bcb89-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="bcb89-127">Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="bcb89-128">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="bcb89-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="bcb89-129">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="bcb89-130">Na obrázku rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="bcb89-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="bcb89-131">K řešení přidat k testovacímu projektu, spusťte [SLN – dotnet](../tools/dotnet-sln.md) v *testování pomocí dotnet – testování* directory:</span><span class="sxs-lookup"><span data-stu-id="bcb89-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="bcb89-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="bcb89-132">Creating the first test</span></span>

<span data-ttu-id="bcb89-133">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="bcb89-134">Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový soubor C# s s názvem *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="bcb89-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="bcb89-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bcb89-135">Add the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="bcb89-136">`[Fact]` Atribut označuje testovací metodu, která spustí nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="bcb89-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="bcb89-137">Z *PrimeService.Tests* složky, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="bcb89-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="bcb89-138">Nástroj test runner xUnit obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="bcb89-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="bcb89-139">`dotnet test`Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="bcb89-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="bcb89-140">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bcb89-140">Your test fails.</span></span> <span data-ttu-id="bcb89-141">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="bcb89-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="bcb89-142">Psaní kódu nejjednodušší v, aby tento test `PrimeService` třídu, která funguje.</span><span class="sxs-lookup"><span data-stu-id="bcb89-142">Make this test by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="bcb89-143">Nahradit existující `IsPrime` implementace metod následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="bcb89-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="bcb89-144">V *PrimeService.Tests* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="bcb89-145">`dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="bcb89-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="bcb89-146">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="bcb89-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="bcb89-147">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="bcb89-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="bcb89-148">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="bcb89-148">Adding more features</span></span>

<span data-ttu-id="bcb89-149">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="bcb89-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="bcb89-150">Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="bcb89-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="bcb89-151">Můžete přidat jako nový testování pomocí těchto případech `[Fact]` atribut, ale které rychle stane zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="bcb89-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="bcb89-152">Existují další xUnit atributy, které vám umožní zápisu sada testů, podobně jako:</span><span class="sxs-lookup"><span data-stu-id="bcb89-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="bcb89-153">`[Theory]`představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="bcb89-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="bcb89-154">`[InlineData]`atribut určuje hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="bcb89-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="bcb89-155">Místo vytváření nové testů, platí tyto dva atributy `[Theory]` a `[InlineData]`, k vytvoření jedné teoreticky v *PrimeService_IsPrimeShould.cs* souboru.</span><span class="sxs-lookup"><span data-stu-id="bcb89-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="bcb89-156">Teorie je metoda, která porovná několik hodnoty menší než dva, což je nejnižší prime číslo:</span><span class="sxs-lookup"><span data-stu-id="bcb89-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="bcb89-157">Spustit `dotnet test` znovu, a obě tyto testy by měl nezdaří.</span><span class="sxs-lookup"><span data-stu-id="bcb89-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="bcb89-158">Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku `IsPrime` metoda v *PrimeService.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="bcb89-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="bcb89-159">Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní.</span><span class="sxs-lookup"><span data-stu-id="bcb89-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="bcb89-160">Máte [dokončení verzi testy](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [dokončení implementace knihovny](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="bcb89-160">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bcb89-161">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bcb89-161">Additional resources</span></span>

[<span data-ttu-id="bcb89-162">Testování řadiče logiku v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bcb89-162">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
