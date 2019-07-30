---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a MSTest
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: 6081e7b6b52d85615cfde701e364eb87d69f42bf
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626427"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="03aae-103">Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="03aae-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="03aae-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="03aae-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="03aae-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="03aae-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="03aae-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="03aae-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="03aae-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="03aae-107">Creating the source project</span></span>

<span data-ttu-id="03aae-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="03aae-108">Open a shell window.</span></span> <span data-ttu-id="03aae-109">Vytvořte adresář s názvem *Unit-Testing-VB-MSTest* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="03aae-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="03aae-110">V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="03aae-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="03aae-111">Tento postup usnadňuje správu knihovny tříd i projektu testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="03aae-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="03aae-112">V adresáři řešení vytvořte adresář *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="03aae-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="03aae-113">Máte zatím následující strukturu adresářů a souborů:</span><span class="sxs-lookup"><span data-stu-id="03aae-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="03aae-114">Vytvořte *PrimeService* aktuální adresář a spusťte příkaz [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) k vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="03aae-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="03aae-115">Přejmenujte *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="03aae-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="03aae-116">Vytvoříte selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="03aae-116">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="03aae-117">Změňte adresář zpátky na adresář *testování částí-VB-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="03aae-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="03aae-118">Spusťte [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) , chcete-li přidat projekt knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="03aae-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="03aae-119">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="03aae-119">Creating the test project</span></span>

<span data-ttu-id="03aae-120">Dále vytvořte adresář *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="03aae-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="03aae-121">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="03aae-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="03aae-122">Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="03aae-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="03aae-123">Tento příkaz vytvoří testovací projekt, který jako knihovnu testů používá MSTest.</span><span class="sxs-lookup"><span data-stu-id="03aae-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="03aae-124">Vygenerovaná šablona konfiguruje Test Runner v *PrimeServiceTests. vbproj*:</span><span class="sxs-lookup"><span data-stu-id="03aae-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="03aae-125">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="03aae-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="03aae-126">`dotnet new`v předchozím kroku jsme přidali MSTest a MSTest Runner.</span><span class="sxs-lookup"><span data-stu-id="03aae-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="03aae-127">Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="03aae-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="03aae-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="03aae-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="03aae-129">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="03aae-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="03aae-130">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="03aae-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="03aae-131">Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-VB-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="03aae-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="03aae-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="03aae-132">Creating the first test</span></span>

<span data-ttu-id="03aae-133">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="03aae-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="03aae-134">Z adresáře *PrimeService. Tests* odeberte *UnitTest1. vb* a vytvořte nový soubor Visual Basic s názvem *PrimeService_IsPrimeShould. vb*.</span><span class="sxs-lookup"><span data-stu-id="03aae-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="03aae-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="03aae-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="03aae-136">`<TestClass>` Atribut označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="03aae-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="03aae-137">`<TestMethod>` Atribut označuje metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="03aae-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="03aae-138">Z rutiny *testování částí-VB-MSTest*spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz pro sestavení testů a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="03aae-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="03aae-139">MSTest Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="03aae-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="03aae-140">`dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="03aae-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="03aae-141">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="03aae-141">Your test fails.</span></span> <span data-ttu-id="03aae-142">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="03aae-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="03aae-143">Proveďte tento test průchodu vytvořením nejjednoduššího kódu `PrimeService` ve třídě, která funguje:</span><span class="sxs-lookup"><span data-stu-id="03aae-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="03aae-144">V adresáři *Unit-Testing-VB-MSTest* spusťte `dotnet test` znovu.</span><span class="sxs-lookup"><span data-stu-id="03aae-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="03aae-145">Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="03aae-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="03aae-146">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="03aae-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="03aae-147">Předá.</span><span class="sxs-lookup"><span data-stu-id="03aae-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="03aae-148">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="03aae-148">Adding more features</span></span>

<span data-ttu-id="03aae-149">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="03aae-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="03aae-150">Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="03aae-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="03aae-151">Tyto případy můžete přidat jako nové testy s `<TestMethod>` atributem, ale to se rychle bude zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="03aae-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="03aae-152">Existují další atributy MSTest, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="03aae-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="03aae-153">`<DataTestMethod>` Atribut představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="03aae-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="03aae-154">`<DataRow>` Atribut můžete použít k zadání hodnot pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="03aae-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="03aae-155">Místo vytváření nových testů použijte tyto dva atributy pro vytvoření jedné teorie.</span><span class="sxs-lookup"><span data-stu-id="03aae-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="03aae-156">Teoretická je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:</span><span class="sxs-lookup"><span data-stu-id="03aae-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="03aae-157">Spuštění `dotnet test`a dva z těchto testů selžou.</span><span class="sxs-lookup"><span data-stu-id="03aae-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="03aae-158">Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="03aae-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="03aae-159">Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="03aae-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="03aae-160">Máte hotovou [verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="03aae-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="03aae-161">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="03aae-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="03aae-162">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="03aae-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="03aae-163">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="03aae-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
