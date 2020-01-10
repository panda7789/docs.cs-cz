---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a MSTest
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 14c145ffc227078378897feeb75db0df8da4be6f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714253"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="610d2-103">Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="610d2-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="610d2-104">Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí.</span><span class="sxs-lookup"><span data-stu-id="610d2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="610d2-105">Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) před jeho zahájením nebo si ho stáhněte.</span><span class="sxs-lookup"><span data-stu-id="610d2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="610d2-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="610d2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="610d2-107">Vytvoření zdrojového projektu</span><span class="sxs-lookup"><span data-stu-id="610d2-107">Creating the source project</span></span>

<span data-ttu-id="610d2-108">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="610d2-108">Open a shell window.</span></span> <span data-ttu-id="610d2-109">Vytvořte adresář s názvem *Unit-Testing-VB-MSTest* , který bude obsahovat řešení.</span><span class="sxs-lookup"><span data-stu-id="610d2-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="610d2-110">V tomto novém adresáři spusťte [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení.</span><span class="sxs-lookup"><span data-stu-id="610d2-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="610d2-111">Tento postup usnadňuje správu knihovny tříd i projektu testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="610d2-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="610d2-112">V adresáři řešení vytvořte adresář *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="610d2-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="610d2-113">Máte zatím následující strukturu adresářů a souborů:</span><span class="sxs-lookup"><span data-stu-id="610d2-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="610d2-114">Vytvořte *PrimeService* aktuální adresář a spusťte [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) pro vytvoření zdrojového projektu.</span><span class="sxs-lookup"><span data-stu-id="610d2-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="610d2-115">Přejmenujte *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="610d2-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="610d2-116">Vytvoříte selhání implementace `PrimeService` třídy:</span><span class="sxs-lookup"><span data-stu-id="610d2-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="610d2-117">Změňte adresář zpátky na adresář *testování částí-VB-using-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="610d2-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="610d2-118">Spusťte [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) pro přidání projektu knihovny tříd do řešení.</span><span class="sxs-lookup"><span data-stu-id="610d2-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="610d2-119">Vytváření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="610d2-119">Creating the test project</span></span>

<span data-ttu-id="610d2-120">Dále vytvořte adresář *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="610d2-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="610d2-121">Následující osnova znázorňuje adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="610d2-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="610d2-122">Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="610d2-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="610d2-123">Tento příkaz vytvoří testovací projekt, který jako knihovnu testů používá MSTest.</span><span class="sxs-lookup"><span data-stu-id="610d2-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="610d2-124">Vygenerovaná šablona konfiguruje Test Runner v *PrimeServiceTests. vbproj*:</span><span class="sxs-lookup"><span data-stu-id="610d2-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="610d2-125">Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky.</span><span class="sxs-lookup"><span data-stu-id="610d2-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="610d2-126">`dotnet new` v předchozím kroku jsme přidali MSTest a MSTest Runner.</span><span class="sxs-lookup"><span data-stu-id="610d2-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="610d2-127">Nyní přidejte knihovnu tříd `PrimeService` jako jinou závislost do projektu.</span><span class="sxs-lookup"><span data-stu-id="610d2-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="610d2-128">Použijte příkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) :</span><span class="sxs-lookup"><span data-stu-id="610d2-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="610d2-129">Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="610d2-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="610d2-130">Máte následující konečné rozložení řešení:</span><span class="sxs-lookup"><span data-stu-id="610d2-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="610d2-131">Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-VB-MSTest* .</span><span class="sxs-lookup"><span data-stu-id="610d2-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="610d2-132">Vytvoření prvního testu</span><span class="sxs-lookup"><span data-stu-id="610d2-132">Creating the first test</span></span>

<span data-ttu-id="610d2-133">Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte.</span><span class="sxs-lookup"><span data-stu-id="610d2-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="610d2-134">Z adresáře *PrimeService. Tests* odeberte *UnitTest1. vb* a vytvořte nový soubor Visual Basic s názvem *PrimeService_IsPrimeShould. vb*.</span><span class="sxs-lookup"><span data-stu-id="610d2-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="610d2-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="610d2-135">Add the following code:</span></span>

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

<span data-ttu-id="610d2-136">Atribut `<TestClass>` označuje třídu, která obsahuje testy.</span><span class="sxs-lookup"><span data-stu-id="610d2-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="610d2-137">Atribut `<TestMethod>` označuje metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="610d2-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="610d2-138">Z rutiny *testování částí-VB-MSTest*spusťte [`dotnet test`](../tools/dotnet-test.md) pro sestavení testů a knihovny tříd a poté spusťte testy.</span><span class="sxs-lookup"><span data-stu-id="610d2-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="610d2-139">MSTest Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="610d2-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="610d2-140">`dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="610d2-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="610d2-141">Test se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="610d2-141">Your test fails.</span></span> <span data-ttu-id="610d2-142">Ještě jste nevytvořili implementaci.</span><span class="sxs-lookup"><span data-stu-id="610d2-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="610d2-143">Proveďte tento test průchodu tak, že napíšete nejjednodušší kód ve třídě `PrimeService`, která funguje:</span><span class="sxs-lookup"><span data-stu-id="610d2-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="610d2-144">V adresáři *Unit-Testing-VB-MSTest* znovu spusťte `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="610d2-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="610d2-145">Příkaz `dotnet test` spustí sestavení pro projekt `PrimeService` a potom pro projekt `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="610d2-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="610d2-146">Po sestavení obou projektů spustí tento jediný test.</span><span class="sxs-lookup"><span data-stu-id="610d2-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="610d2-147">Předá.</span><span class="sxs-lookup"><span data-stu-id="610d2-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="610d2-148">Přidání dalších funkcí</span><span class="sxs-lookup"><span data-stu-id="610d2-148">Adding more features</span></span>

<span data-ttu-id="610d2-149">Teď, když jste udělali jeden test Pass, je čas zapsat další.</span><span class="sxs-lookup"><span data-stu-id="610d2-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="610d2-150">Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="610d2-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="610d2-151">Tyto případy můžete přidat jako nové testy s atributem `<TestMethod>`, ale to se rychle bude zdlouhavé.</span><span class="sxs-lookup"><span data-stu-id="610d2-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="610d2-152">Existují další atributy MSTest, které umožňují napsat sadu podobných testů.</span><span class="sxs-lookup"><span data-stu-id="610d2-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="610d2-153">Atribut `<DataTestMethod>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="610d2-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="610d2-154">Pomocí atributu `<DataRow>` můžete zadat hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="610d2-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="610d2-155">Místo vytváření nových testů použijte tyto dva atributy pro vytvoření jedné teorie.</span><span class="sxs-lookup"><span data-stu-id="610d2-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="610d2-156">Teoretická je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:</span><span class="sxs-lookup"><span data-stu-id="610d2-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="610d2-157">Spusťte `dotnet test`a dva z těchto testů selžou.</span><span class="sxs-lookup"><span data-stu-id="610d2-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="610d2-158">Chcete-li provést všechny testy Pass, změňte klauzuli `if` na začátku metody:</span><span class="sxs-lookup"><span data-stu-id="610d2-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="610d2-159">Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně.</span><span class="sxs-lookup"><span data-stu-id="610d2-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="610d2-160">Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="610d2-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="610d2-161">Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu.</span><span class="sxs-lookup"><span data-stu-id="610d2-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="610d2-162">Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="610d2-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="610d2-163">Vyrostli jste většinu času a úsilí při řešení cílů aplikace.</span><span class="sxs-lookup"><span data-stu-id="610d2-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
