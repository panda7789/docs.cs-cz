---
title: Testování jednotek u kódu v jazyce C# s použitím NUnit a .NET Core
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivní ho dání prostřednictvím vytváření ukázkového řešení krok za krokem pomocí dotnet test a NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240880"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="81fa0-103">Testování jednotek u kódu v jazyce C# s použitím NUnit a .NET Core</span><span class="sxs-lookup"><span data-stu-id="81fa0-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="81fa0-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="81fa0-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="81fa0-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="81fa0-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="81fa0-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="81fa0-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="81fa0-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81fa0-107">Prerequisites</span></span>

- <span data-ttu-id="81fa0-108">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="81fa0-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="81fa0-109">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="81fa0-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="81fa0-110">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="81fa0-110">Creating the source project</span></span>

<span data-ttu-id="81fa0-111">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="81fa0-111">Open a shell window.</span></span> <span data-ttu-id="81fa0-112">Vytvořte adresář s názvem *unit-testing-using-nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="81fa0-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="81fa0-113">V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="81fa0-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="81fa0-114">Dále vytvořte adresář *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="81fa0-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="81fa0-115">Následující osnova ukazuje adresář a strukturu souborů tak daleko:</span><span class="sxs-lookup"><span data-stu-id="81fa0-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="81fa0-116">Vytvořte *primeservice* jako aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:</span><span class="sxs-lookup"><span data-stu-id="81fa0-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib
```

<span data-ttu-id="81fa0-117">Přejmenujte *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="81fa0-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="81fa0-118">Můžete vytvořit selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="81fa0-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="81fa0-119">Změňte adresář zpět do adresáře *unit-testing-using-nunit.*</span><span class="sxs-lookup"><span data-stu-id="81fa0-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="81fa0-120">Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="81fa0-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="81fa0-121">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="81fa0-121">Creating the test project</span></span>

<span data-ttu-id="81fa0-122">Dále vytvořte adresář *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="81fa0-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="81fa0-123">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="81fa0-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="81fa0-124">Vytvořte adresář *PrimeService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="81fa0-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit
```

<span data-ttu-id="81fa0-125">[Dotnet new](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako testovací knihovnu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="81fa0-126">Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeService.Tests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="81fa0-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="81fa0-127">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="81fa0-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="81fa0-128">`dotnet new`V předchozím kroku přidánmicrosoft test SDK, NUnit testovací rámec a NUnit testovací adaptér.</span><span class="sxs-lookup"><span data-stu-id="81fa0-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="81fa0-129">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="81fa0-130">Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="81fa0-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="81fa0-131">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="81fa0-132">Následující osnova ukazuje konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="81fa0-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="81fa0-133">V adresáři *jednotky testování nunit proveďte* následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="81fa0-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="81fa0-134">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="81fa0-134">Creating the first test</span></span>

<span data-ttu-id="81fa0-135">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="81fa0-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="81fa0-136">V adresáři *PrimeService.Tests* přejmenujte soubor *UnitTest1.cs* na *soubor PrimeService_IsPrimeShould.cs* a nahraďte celý jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="81fa0-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

<span data-ttu-id="81fa0-137">Atribut `[TestFixture]` označuje třídu, která obsahuje testy částí.</span><span class="sxs-lookup"><span data-stu-id="81fa0-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="81fa0-138">Atribut `[Test]` označuje, že metoda je zkušební metoda.</span><span class="sxs-lookup"><span data-stu-id="81fa0-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="81fa0-139">Uložte tento [`dotnet test`](../tools/dotnet-test.md) soubor a spusťte k sestavení testů a knihovny tříd a pak spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="81fa0-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="81fa0-140">Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="81fa0-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="81fa0-141">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="81fa0-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="81fa0-142">Váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="81fa0-142">Your test fails.</span></span> <span data-ttu-id="81fa0-143">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="81fa0-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="81fa0-144">Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="81fa0-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="81fa0-145">V adresáři *unit-testing-using-nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="81fa0-146">Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="81fa0-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="81fa0-147">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="81fa0-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="81fa0-148">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="81fa0-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="81fa0-149">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="81fa0-149">Adding more features</span></span>

<span data-ttu-id="81fa0-150">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="81fa0-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="81fa0-151">Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="81fa0-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="81fa0-152">Můžete přidat nové testy `[Test]` s atributem, ale to se rychle stává únavné.</span><span class="sxs-lookup"><span data-stu-id="81fa0-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="81fa0-153">Existují další Atributy NUnit, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="81fa0-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="81fa0-154">Atribut `[TestCase]` se používá k vytvoření sady testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="81fa0-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="81fa0-155">`[TestCase]` Atribut můžete použít k určení hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="81fa0-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="81fa0-156">Namísto vytváření nových testů použijte tento atribut k vytvoření jednoho testu řízeného daty.</span><span class="sxs-lookup"><span data-stu-id="81fa0-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="81fa0-157">Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:</span><span class="sxs-lookup"><span data-stu-id="81fa0-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="81fa0-158">Spustit `dotnet test`a dva z těchto testů nezdaří.</span><span class="sxs-lookup"><span data-stu-id="81fa0-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="81fa0-159">Chcete-li provést všechny testy `if` projít, změňte `Main` klauzuli na začátku metody v *souboru PrimeService.cs:*</span><span class="sxs-lookup"><span data-stu-id="81fa0-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="81fa0-160">Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="81fa0-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="81fa0-161">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="81fa0-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="81fa0-162">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="81fa0-163">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="81fa0-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="81fa0-164">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="81fa0-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
