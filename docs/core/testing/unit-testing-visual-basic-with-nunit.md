---
title: Testování jazyka Visual Basic v .NET Core pomocí testovacích dotnet a NUnit částí
description: Další koncepty test jednotky v .NET Core prostřednictvím interaktivní prostředí vytváření ukázkové řešení Visual Basic podrobné pomocí NUnit.
author: rprouse
ms.date: 12/01/2017
dev_langs:
- vb
ms.openlocfilehash: 552b60dd3937abc413c1b4410213948f3b509526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217773"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="23731-103">Knihovny jazyka Visual Basic .NET Core pomocí testovacích dotnet a NUnit testování částí</span><span class="sxs-lookup"><span data-stu-id="23731-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="23731-104">Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="23731-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="23731-105">Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) před zahájením.</span><span class="sxs-lookup"><span data-stu-id="23731-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="23731-106">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="23731-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="23731-107">Vytvoření projektu zdroje</span><span class="sxs-lookup"><span data-stu-id="23731-107">Creating the source project</span></span>

<span data-ttu-id="23731-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="23731-108">Open a shell window.</span></span> <span data-ttu-id="23731-109">Vytvořte adresář s názvem *jednotky – testování vb-nunit* pro uložení řešení.</span><span class="sxs-lookup"><span data-stu-id="23731-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="23731-110">Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení.</span><span class="sxs-lookup"><span data-stu-id="23731-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="23731-111">Tento postup je snazší správa knihovny tříd a projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="23731-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="23731-112">V adresáři řešení vytvořit *PrimeService* adresáře.</span><span class="sxs-lookup"><span data-stu-id="23731-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="23731-113">Proto pokud máte následující strukturu adresáře a souboru:</span><span class="sxs-lookup"><span data-stu-id="23731-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="23731-114">Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje.</span><span class="sxs-lookup"><span data-stu-id="23731-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="23731-115">Přejmenování *Class1.VB* k *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="23731-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="23731-116">Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="23731-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="23731-117">Změna adresáře zpět do *jednotky – testování vb – pomocí stest* adresáře.</span><span class="sxs-lookup"><span data-stu-id="23731-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="23731-118">Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="23731-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="23731-119">Šablona projektu NUnit instalace</span><span class="sxs-lookup"><span data-stu-id="23731-119">Install the NUnit project template</span></span>

<span data-ttu-id="23731-120">NUnit testování projektu, který je potřeba nainstalovat před vytvořením testovacího projektu šablony.</span><span class="sxs-lookup"><span data-stu-id="23731-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="23731-121">To jenom je nutné provést jednou na každém počítači vývojáře, kde vytvoříte nové projekty NUnit.</span><span class="sxs-lookup"><span data-stu-id="23731-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="23731-122">Spustit [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) instalovat NUnit šablony.</span><span class="sxs-lookup"><span data-stu-id="23731-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="23731-123">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="23731-123">Creating the test project</span></span>

<span data-ttu-id="23731-124">Dále vytvořte *PrimeService.Tests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="23731-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="23731-125">Zobrazí následující osnova adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="23731-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="23731-126">Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new nunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="23731-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="23731-127">Tento příkaz vytvoří testovací projekt, který používá NUnit jako knihovně testu.</span><span class="sxs-lookup"><span data-stu-id="23731-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="23731-128">Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="23731-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="23731-129">K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí.</span><span class="sxs-lookup"><span data-stu-id="23731-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="23731-130">`dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptéru.</span><span class="sxs-lookup"><span data-stu-id="23731-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="23731-131">Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="23731-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="23731-132">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="23731-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="23731-133">Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.</span><span class="sxs-lookup"><span data-stu-id="23731-133">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="23731-134">Máte následující rozložení konečné řešení:</span><span class="sxs-lookup"><span data-stu-id="23731-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="23731-135">Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *jednotky – testování vb-nunit* adresáře.</span><span class="sxs-lookup"><span data-stu-id="23731-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="23731-136">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="23731-136">Creating the first test</span></span>

<span data-ttu-id="23731-137">Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu.</span><span class="sxs-lookup"><span data-stu-id="23731-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="23731-138">Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="23731-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="23731-139">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="23731-139">Add the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="23731-140">`<TestFixture>` Atribut určuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="23731-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="23731-141">`<Test>` Atribut označuje metodu, která spustí nástroj test runner.</span><span class="sxs-lookup"><span data-stu-id="23731-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="23731-142">Z *jednotky – testování vb-nunit*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="23731-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="23731-143">Nástroj test runner NUnit obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="23731-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="23731-144">`dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="23731-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="23731-145">Test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="23731-145">Your test fails.</span></span> <span data-ttu-id="23731-146">Nevytvořili jste ještě implementace.</span><span class="sxs-lookup"><span data-stu-id="23731-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="23731-147">Psaní kódu nejjednodušší v, aby tento test `PrimeService` třídu, která funguje:</span><span class="sxs-lookup"><span data-stu-id="23731-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="23731-148">V *jednotky – testování vb-nunit* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="23731-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="23731-149">`dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="23731-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="23731-150">Po sestavení obou projektů, spustí se tento jeden test.</span><span class="sxs-lookup"><span data-stu-id="23731-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="23731-151">Pak předá.</span><span class="sxs-lookup"><span data-stu-id="23731-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="23731-152">Přidání další funkce</span><span class="sxs-lookup"><span data-stu-id="23731-152">Adding more features</span></span>

<span data-ttu-id="23731-153">Teď, když jste udělali jeden testovací předání, je čas zapsat informace.</span><span class="sxs-lookup"><span data-stu-id="23731-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="23731-154">Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="23731-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="23731-155">Můžete přidat jako nový testování pomocí těchto případech `<Test>` atribut, ale které rychle stane zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="23731-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="23731-156">Existují další xUnit atributy, které vám umožní zápisu sada testů, podobně jako.</span><span class="sxs-lookup"><span data-stu-id="23731-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="23731-157">A `<TestCase>` atribut představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="23731-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="23731-158">Můžete použít `<TestCase>` atribut zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="23731-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="23731-159">Místo vytváření nové testů, platí tyto dva atributy vytvoření řady testů, které testovací několik hodnoty menší než dva, což je s nejnižším číslem prime:</span><span class="sxs-lookup"><span data-stu-id="23731-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="23731-160">Spustit `dotnet test`, a dvě z nich testy nezdaří.</span><span class="sxs-lookup"><span data-stu-id="23731-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="23731-161">Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="23731-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="23731-162">Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní.</span><span class="sxs-lookup"><span data-stu-id="23731-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="23731-163">Máte [dokončení verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [dokončení implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="23731-163">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="23731-164">Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="23731-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="23731-165">Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="23731-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="23731-166">Jste soustředí většinu čas a úsilí na řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="23731-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
