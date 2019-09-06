---
title: Testování C# částí kódu v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty C# testování částí v a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 1a6c8ed515e62bed921290a54e3d9687bb889a4d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374155"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="5aa7a-103">Testování C# částí v .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="5aa7a-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="5aa7a-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5aa7a-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="5aa7a-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5aa7a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="5aa7a-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="5aa7a-107">Creating the source project</span></span>

<span data-ttu-id="5aa7a-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-108">Open a shell window.</span></span> <span data-ttu-id="5aa7a-109">Vytvořte adresář s názvem *Unit-Testing-using-dotnet-test* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="5aa7a-110">V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="5aa7a-111">Díky řešení je snazší spravovat jak knihovnu tříd, tak projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="5aa7a-112">V adresáři řešení vytvořte adresář *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="5aa7a-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="5aa7a-113">Struktura adresáře a souborů by měla být takto:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-113">The directory and file structure thus far should be as follows:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="5aa7a-114">Vytvořte *PrimeService* aktuální adresář a spusťte příkaz [`dotnet new classlib`](../tools/dotnet-new.md) k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="5aa7a-115">Přejmenujte *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="5aa7a-116">Nejprve vytvoříte selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-116">You first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="5aa7a-117">Změňte adresář zpátky na adresář *-Test-Using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="5aa7a-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="5aa7a-118">Spusťte příkaz [dotnet sln](../tools/dotnet-sln.md) a přidejte do řešení projekt knihovny tříd:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```console
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="5aa7a-119">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="5aa7a-119">Creating the test project</span></span>

<span data-ttu-id="5aa7a-120">Dále vytvořte adresář *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="5aa7a-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5aa7a-121">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="5aa7a-122">Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new xunit`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="5aa7a-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="5aa7a-123">Tento příkaz vytvoří testovací projekt, který jako knihovnu testů používá [xUnit](https://xunit.github.io/) .</span><span class="sxs-lookup"><span data-stu-id="5aa7a-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="5aa7a-124">Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeServiceTests. csproj* podobně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="5aa7a-125">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5aa7a-126">`dotnet new`v předchozím kroku jsme přidali xUnit a xUnit Runner.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="5aa7a-127">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5aa7a-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="5aa7a-129">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="5aa7a-130">Následující příklad ukazuje konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-130">The following shows the final solution layout:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="5aa7a-131">Chcete-li přidat testovací projekt do řešení, spusťte příkaz [dotnet sln](../tools/dotnet-sln.md) v adresáři *Unit-Testing-using-dotnet-test* :</span><span class="sxs-lookup"><span data-stu-id="5aa7a-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="5aa7a-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="5aa7a-132">Creating the first test</span></span>

<span data-ttu-id="5aa7a-133">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5aa7a-134">Odeberte *UnitTest1.cs* z adresáře *PrimeService. Tests* a vytvořte nový C# soubor s názvem *PrimeService_IsPrimeShould. cs*.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="5aa7a-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-135">Add the following code:</span></span>

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="5aa7a-136">`[Fact]` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="5aa7a-137">Ze složky *PrimeService. Tests* spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz a sestavte testy a knihovnu tříd a potom spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5aa7a-138">XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5aa7a-139">`dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5aa7a-140">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-140">Your test fails.</span></span> <span data-ttu-id="5aa7a-141">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="5aa7a-142">Proveďte tento test průchodu tak, že napíšete `PrimeService` nejjednodušší kód ve třídě, která funguje.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="5aa7a-143">Nahraďte stávající `IsPrime` implementaci metody následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="5aa7a-144">V adresáři *PrimeService. Tests* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5aa7a-145">Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="5aa7a-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5aa7a-146">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5aa7a-147">Předá.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5aa7a-148">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="5aa7a-148">Adding more features</span></span>

<span data-ttu-id="5aa7a-149">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5aa7a-150">Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5aa7a-151">Tyto případy můžete přidat jako nové testy s `[Fact]` atributem, ale to se rychle bude zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5aa7a-152">Existují další atributy xUnit, které umožňují napsat sadu podobných testů:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="5aa7a-153">`[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="5aa7a-154">`[InlineData]`atribut určuje hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="5aa7a-155">Namísto vytváření nových testů, použijte tyto dva atributy, `[Theory]` a `[InlineData]`vytvořte jednu teorie v souboru *PrimeService_IsPrimeShould. cs* .</span><span class="sxs-lookup"><span data-stu-id="5aa7a-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="5aa7a-156">Teoretická je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:</span><span class="sxs-lookup"><span data-stu-id="5aa7a-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="5aa7a-157">Spusťte `dotnet test` znovu a dva z těchto testů by měly selhat.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="5aa7a-158">Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku `IsPrime` metody v souboru *PrimeService.cs* :</span><span class="sxs-lookup"><span data-stu-id="5aa7a-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="5aa7a-159">Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="5aa7a-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5aa7a-160">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="5aa7a-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5aa7a-161">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5aa7a-161">Additional resources</span></span>

- [<span data-ttu-id="5aa7a-162">Oficiální web xUnit.net</span><span class="sxs-lookup"><span data-stu-id="5aa7a-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="5aa7a-163">Testování logiky kontroleru v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5aa7a-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
