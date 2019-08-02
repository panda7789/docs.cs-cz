---
title: Testování C# částí pomocí nunit a .NET Core
description: Seznamte se s koncepty C# testování částí v a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a nunit.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 927facd271d6590cac2b0ce10790a16c88482020
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733418"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="f7dfc-103">Testování C# částí pomocí nunit a .NET Core</span><span class="sxs-lookup"><span data-stu-id="f7dfc-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="f7dfc-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="f7dfc-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="f7dfc-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f7dfc-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7dfc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7dfc-107">Prerequisites</span></span>

- <span data-ttu-id="f7dfc-108">[.NET Core 2,1 SDK](https://www.microsoft.com/net/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="f7dfc-109">Textový editor nebo Editor kódu dle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="f7dfc-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="f7dfc-110">Creating the source project</span></span>

<span data-ttu-id="f7dfc-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-111">Open a shell window.</span></span> <span data-ttu-id="f7dfc-112">Vytvořte adresář s názvem *Unit-Testing-using-nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="f7dfc-113">V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="f7dfc-114">Potom vytvořte adresář *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="f7dfc-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="f7dfc-115">Následující osnova ukazuje strukturu adresářů a souborů, které jsou tak daleko:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="f7dfc-116">Vytvořte *PrimeService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="f7dfc-117">Přejmenujte *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="f7dfc-118">Vytvoříte selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-118">You create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="f7dfc-119">Změňte adresář zpátky na adresář s *testováním jednotek pomocí-nunit* .</span><span class="sxs-lookup"><span data-stu-id="f7dfc-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="f7dfc-120">Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="f7dfc-121">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="f7dfc-121">Creating the test project</span></span>

<span data-ttu-id="f7dfc-122">Dále vytvořte adresář *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="f7dfc-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="f7dfc-123">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="f7dfc-124">Vytvořte adresář *PrimeService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="f7dfc-125">Příkaz [dotnet New](../tools/dotnet-new.md) vytvoří testovací projekt, který jako knihovnu testů používá nunit.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="f7dfc-126">Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeService. Tests. csproj* :</span><span class="sxs-lookup"><span data-stu-id="f7dfc-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="f7dfc-127">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="f7dfc-128">`dotnet new`v předchozím kroku jsme přidali Microsoft Test SDK, NUnit test Framework a adaptér NUnit test Adapter.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="f7dfc-129">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="f7dfc-130">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="f7dfc-131">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="f7dfc-132">Následující osnova znázorňuje konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-132">The following outline shows the final solution layout:</span></span>

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

<span data-ttu-id="f7dfc-133">Spusťte následující příkaz v adresáři *Unit-Test-Using-nunit* :</span><span class="sxs-lookup"><span data-stu-id="f7dfc-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="f7dfc-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="f7dfc-134">Creating the first test</span></span>

<span data-ttu-id="f7dfc-135">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="f7dfc-136">V adresáři *PrimeService. Tests* přejmenujte soubor *UnitTest1.cs* na *PrimeService_IsPrimeShould. cs* a nahraďte jeho celý obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        [Test]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            PrimeService primeService = CreatePrimeService();
            var result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
        
        /*
        More tests
        */
        
        private PrimeService CreatePrimeService()
        {
             return new PrimeService();
        }
    }
}
```

<span data-ttu-id="f7dfc-137">`[TestFixture]` Atribut označuje třídu, která obsahuje testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="f7dfc-138">`[Test]` Atribut označuje metodu testu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="f7dfc-139">Uložte tento soubor a spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz pro sestavení testů a knihovny tříd a potom spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="f7dfc-140">NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="f7dfc-141">`dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="f7dfc-142">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-142">Your test fails.</span></span> <span data-ttu-id="f7dfc-143">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="f7dfc-144">Proveďte tento test průchodu vytvořením nejjednoduššího kódu `PrimeService` ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="f7dfc-145">V adresáři *Unit-Testing-using-nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="f7dfc-146">Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="f7dfc-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="f7dfc-147">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="f7dfc-148">Předá.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="f7dfc-149">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="f7dfc-149">Adding more features</span></span>

<span data-ttu-id="f7dfc-150">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="f7dfc-151">Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="f7dfc-152">Můžete přidat nové testy s `[Test]` atributem, ale to se rychle bude zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="f7dfc-153">Existují další atributy NUnit, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="f7dfc-154">`[TestCase]` Atribut slouží k vytvoření sady testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="f7dfc-155">`[TestCase]` Atribut můžete použít k zadání hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="f7dfc-156">Místo vytváření nových testů použijte tento atribut k vytvoření jednoho testu řízeného daty.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="f7dfc-157">Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:</span><span class="sxs-lookup"><span data-stu-id="f7dfc-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="f7dfc-158">Spuštění `dotnet test`a dva z těchto testů selžou.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="f7dfc-159">Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku `Main` metody v souboru *PrimeService.cs* :</span><span class="sxs-lookup"><span data-stu-id="f7dfc-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="f7dfc-160">Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="f7dfc-161">Máte hotovou [verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="f7dfc-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="f7dfc-162">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="f7dfc-163">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="f7dfc-164">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7dfc-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
