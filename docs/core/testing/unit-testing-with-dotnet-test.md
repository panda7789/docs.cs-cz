---
title: Testování jednotek kódu C# v .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: f84792e5d973f2b2d8bcf418f68e7038fd7a81f5
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747846"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="0142b-103">Testování jednotek C# v .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="0142b-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="0142b-104">Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="0142b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="0142b-105">Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) předtím, než začnete.</span><span class="sxs-lookup"><span data-stu-id="0142b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="0142b-106">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0142b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="0142b-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="0142b-107">Creating the source project</span></span>

<span data-ttu-id="0142b-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="0142b-108">Open a shell window.</span></span> <span data-ttu-id="0142b-109">Vytvořte adresář s názvem *testování použití dotnet testování částí* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="0142b-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="0142b-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení.</span><span class="sxs-lookup"><span data-stu-id="0142b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="0142b-111">Řešení usnadňuje správu knihovny tříd a projekt testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="0142b-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="0142b-112">V adresáři řešení, vytvářet *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="0142b-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="0142b-113">Strukturu adresáře a souboru doposud by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="0142b-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="0142b-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="0142b-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="0142b-115">Přejmenovat *Class1.cs* k *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="0142b-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="0142b-116">Nejprve vytvoříte selhání provádění `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="0142b-116">You first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="0142b-117">Vraťte do adresáře *testování použití dotnet testování částí* adresáře.</span><span class="sxs-lookup"><span data-stu-id="0142b-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="0142b-118">Spustit [dotnet sln](../tools/dotnet-sln.md) příkaz pro přidání do řešení projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="0142b-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="0142b-119">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="0142b-119">Creating the test project</span></span>

<span data-ttu-id="0142b-120">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="0142b-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="0142b-121">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="0142b-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="0142b-122">Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="0142b-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="0142b-123">Tento příkaz vytvoří testovací projekt, který používá [xUnit](https://xunit.github.io/) jako knihovna testu.</span><span class="sxs-lookup"><span data-stu-id="0142b-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="0142b-124">Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.csproj* souboru podobně jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="0142b-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="0142b-125">Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="0142b-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="0142b-126">`dotnet new` v předchozím kroku přidat xUnit a xUnit runner.</span><span class="sxs-lookup"><span data-stu-id="0142b-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="0142b-127">Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="0142b-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="0142b-128">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="0142b-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="0142b-129">Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="0142b-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="0142b-130">Následující obrázek znázorňuje rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="0142b-130">The following shows the final solution layout:</span></span>

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

<span data-ttu-id="0142b-131">Chcete-li přidat testovací projekt do řešení, spusťte [dotnet sln](../tools/dotnet-sln.md) v *testování použití dotnet testování částí* adresáře:</span><span class="sxs-lookup"><span data-stu-id="0142b-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="0142b-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="0142b-132">Creating the first test</span></span>

<span data-ttu-id="0142b-133">Jeden zápis služeb při selhání testu, nastavte ji pass a postup se opakuje.</span><span class="sxs-lookup"><span data-stu-id="0142b-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="0142b-134">Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový C# soubor s názvem *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="0142b-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="0142b-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0142b-135">Add the following code:</span></span>

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

<span data-ttu-id="0142b-136">`[Fact]` Určuje atribut testovací metody, která se spouští pomocí nástroje test runner.</span><span class="sxs-lookup"><span data-stu-id="0142b-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="0142b-137">Z *PrimeService.Tests* složce spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="0142b-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="0142b-138">Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů.</span><span class="sxs-lookup"><span data-stu-id="0142b-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="0142b-139">`dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="0142b-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="0142b-140">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="0142b-140">Your test fails.</span></span> <span data-ttu-id="0142b-141">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="0142b-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="0142b-142">Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje.</span><span class="sxs-lookup"><span data-stu-id="0142b-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="0142b-143">Nahraďte existující `IsPrime` implementace metody s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0142b-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="0142b-144">V *PrimeService.Tests* adresáře, spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="0142b-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="0142b-145">`dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="0142b-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="0142b-146">Po vytvoření oba projekty, poběží tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="0142b-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="0142b-147">Předá.</span><span class="sxs-lookup"><span data-stu-id="0142b-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="0142b-148">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="0142b-148">Adding more features</span></span>

<span data-ttu-id="0142b-149">Teď, když jste provedli, předejte jeden test, je čas zápisu informace.</span><span class="sxs-lookup"><span data-stu-id="0142b-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="0142b-150">Existuje několik dalších jednoduché případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="0142b-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="0142b-151">Tyto případy můžete přidat jako nové testy s `[Fact]` atribut, ale rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="0142b-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="0142b-152">Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování:</span><span class="sxs-lookup"><span data-stu-id="0142b-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="0142b-153">`[Theory]` představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="0142b-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="0142b-154">`[InlineData]` atribut určuje hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="0142b-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="0142b-155">Místo vytváření nové testy, platí tyto dva atributy `[Theory]` a `[InlineData]`, k vytvoření jedné teorie v *PrimeService_IsPrimeShould.cs* souboru.</span><span class="sxs-lookup"><span data-stu-id="0142b-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="0142b-156">Teorie je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:</span><span class="sxs-lookup"><span data-stu-id="0142b-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="0142b-157">Spustit `dotnet test` znovu, a dvě z těchto testů by selhat.</span><span class="sxs-lookup"><span data-stu-id="0142b-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="0142b-158">Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `IsPrime` metoda ve *PrimeService.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="0142b-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="0142b-159">Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny.</span><span class="sxs-lookup"><span data-stu-id="0142b-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="0142b-160">Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="0142b-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0142b-161">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0142b-161">Additional resources</span></span>

- [<span data-ttu-id="0142b-162">xUnit.net oficiální web</span><span class="sxs-lookup"><span data-stu-id="0142b-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="0142b-163">Testování logice kontroleru v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0142b-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
