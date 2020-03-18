---
title: Testování částí C# s MSTest a .NET Core
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240906"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="02490-103">Testování částí C# s MSTest a .NET Core</span><span class="sxs-lookup"><span data-stu-id="02490-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="02490-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="02490-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="02490-105">Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) než začnete.</span><span class="sxs-lookup"><span data-stu-id="02490-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="02490-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="02490-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="02490-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="02490-107">Create the source project</span></span>

<span data-ttu-id="02490-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="02490-108">Open a shell window.</span></span> <span data-ttu-id="02490-109">Vytvořte adresář s názvem *unit-testing-using-mstest* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="02490-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="02490-110">V tomto novém [`dotnet new sln`](../tools/dotnet-new.md) adresáři spusťte a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="02490-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="02490-111">Dále vytvořte adresář *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="02490-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="02490-112">Následující osnova ukazuje adresář a strukturu souborů tak daleko:</span><span class="sxs-lookup"><span data-stu-id="02490-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="02490-113">Vytvořte *PrimeService* aktuální [`dotnet new classlib`](../tools/dotnet-new.md) adresář a spustit k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="02490-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="02490-114">Přejmenujte *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="02490-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="02490-115">Můžete vytvořit selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="02490-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="02490-116">Změňte adresář zpět do adresáře *unit-testing-using-mstest.*</span><span class="sxs-lookup"><span data-stu-id="02490-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="02490-117">Spuštěním [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) přidáte projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="02490-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="02490-118">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="02490-118">Create the test project</span></span>

<span data-ttu-id="02490-119">Dále vytvořte adresář *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="02490-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="02490-120">Následující osnova ukazuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="02490-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="02490-121">Vytvořte adresář *PrimeService.Tests* jako aktuální adresář [`dotnet new mstest`](../tools/dotnet-new.md)a vytvořte nový projekt pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="02490-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="02490-122">Dotnet new příkaz vytvoří testovací projekt, který používá MSTest jako testovací knihovny.</span><span class="sxs-lookup"><span data-stu-id="02490-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="02490-123">Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeServiceTests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="02490-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="02490-124">Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí.</span><span class="sxs-lookup"><span data-stu-id="02490-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="02490-125">`dotnet new`v předchozím kroku přidánm MSTest SDK, MSTest testovací rámec a mstest runner.</span><span class="sxs-lookup"><span data-stu-id="02490-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="02490-126">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="02490-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="02490-127">Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="02490-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="02490-128">Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="02490-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="02490-129">Následující osnova ukazuje konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="02490-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="02490-130">Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) v adresáři *unit-testing-using-mstest.*</span><span class="sxs-lookup"><span data-stu-id="02490-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="02490-131">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="02490-131">Create the first test</span></span>

<span data-ttu-id="02490-132">Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces.</span><span class="sxs-lookup"><span data-stu-id="02490-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="02490-133">Odeberte *UnitTest1.cs* z adresáře *PrimeService.Tests* a vytvořte nový soubor Jazyka C# s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="02490-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="02490-134">TestClass [atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) označuje třídu, která obsahuje testy částí.</span><span class="sxs-lookup"><span data-stu-id="02490-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="02490-135">Atribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) označuje, že metoda je zkušební metoda.</span><span class="sxs-lookup"><span data-stu-id="02490-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="02490-136">Uložte tento [`dotnet test`](../tools/dotnet-test.md) soubor a spusťte k sestavení testů a knihovny tříd a pak spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="02490-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="02490-137">Testovací běžec MSTest obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="02490-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="02490-138">`dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="02490-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="02490-139">Váš test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="02490-139">Your test fails.</span></span> <span data-ttu-id="02490-140">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="02490-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="02490-141">Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="02490-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="02490-142">V adresáři *testování jednotky using-mstest* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="02490-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="02490-143">Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt.</span><span class="sxs-lookup"><span data-stu-id="02490-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="02490-144">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="02490-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="02490-145">Už to přejde.</span><span class="sxs-lookup"><span data-stu-id="02490-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="02490-146">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="02490-146">Add more features</span></span>

<span data-ttu-id="02490-147">Nyní, když jste provedli jeden test projít, je čas napsat více.</span><span class="sxs-lookup"><span data-stu-id="02490-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="02490-148">Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="02490-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="02490-149">Můžete přidat nové testy s [TestMethod atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale to se rychle stane únavné.</span><span class="sxs-lookup"><span data-stu-id="02490-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="02490-150">Existují další atributy MSTest, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="02490-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="02490-151">A [DataTestMethod atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="02490-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="02490-152">[Atribut DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) můžete použít k určení hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="02490-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="02490-153">Namísto vytváření nových testů použijte tyto dva atributy k vytvoření jednoho testu řízeného daty.</span><span class="sxs-lookup"><span data-stu-id="02490-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="02490-154">Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:</span><span class="sxs-lookup"><span data-stu-id="02490-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="02490-155">Spustit `dotnet test`a dva z těchto testů nezdaří.</span><span class="sxs-lookup"><span data-stu-id="02490-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="02490-156">Chcete-li provést všechny testy `if` projít, změňte klauzuli na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="02490-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="02490-157">Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="02490-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="02490-158">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="02490-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="02490-159">Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="02490-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="02490-160">Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="02490-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="02490-161">Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="02490-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="02490-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="02490-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="02490-163">Použití architektury MSTest v jednotkových testech</span><span class="sxs-lookup"><span data-stu-id="02490-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="02490-164">Dokumenty testovacího rámce MSTest V2</span><span class="sxs-lookup"><span data-stu-id="02490-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
