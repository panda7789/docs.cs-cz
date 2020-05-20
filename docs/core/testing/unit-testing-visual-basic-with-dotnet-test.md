---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: ed1291a980f9a39284525877bab8d0a93389fbd0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702955"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="5dc18-103">Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="5dc18-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="5dc18-104">V tomto kurzu se dozvíte, jak vytvořit řešení obsahující projekt testování částí a projekt knihovny.</span><span class="sxs-lookup"><span data-stu-id="5dc18-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="5dc18-105">Pokud chcete postupovat podle kurzu s použitím předem připraveného řešení, [Zobrazte si ukázkový kód nebo si ho stáhněte](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="5dc18-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="5dc18-106">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5dc18-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="5dc18-107">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="5dc18-107">Create the solution</span></span>

<span data-ttu-id="5dc18-108">V této části se vytvoří řešení, které obsahuje zdrojové a testovací projekty.</span><span class="sxs-lookup"><span data-stu-id="5dc18-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="5dc18-109">Dokončené řešení má následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="5dc18-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="5dc18-110">Následující pokyny popisují postup vytvoření testovacího řešení.</span><span class="sxs-lookup"><span data-stu-id="5dc18-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="5dc18-111">Pokyny k vytvoření testovacího řešení v jednom kroku naleznete v tématu [příkazy k vytvoření testovacího řešení](#create-test-cmd) .</span><span class="sxs-lookup"><span data-stu-id="5dc18-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="5dc18-112">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="5dc18-112">Open a shell window.</span></span>
* <span data-ttu-id="5dc18-113">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5dc18-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="5dc18-114">[`dotnet new sln`](../tools/dotnet-new.md)Příkaz vytvoří nové řešení v adresáři *Unit-Testing-using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="5dc18-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="5dc18-115">Změňte adresář na složku- *Test-Using-dotnet-test* .</span><span class="sxs-lookup"><span data-stu-id="5dc18-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="5dc18-116">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5dc18-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="5dc18-117">[`dotnet new classlib`](../tools/dotnet-new.md)Příkaz vytvoří nový projekt knihovny tříd ve složce *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="5dc18-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="5dc18-118">Nová knihovna tříd bude obsahovat kód, který chcete testovat.</span><span class="sxs-lookup"><span data-stu-id="5dc18-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="5dc18-119">Přejmenujte *Class1. vb* na *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="5dc18-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="5dc18-120">Nahraďte kód v *PrimeService. vb* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5dc18-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="5dc18-121">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="5dc18-121">The preceding code:</span></span>
  * <span data-ttu-id="5dc18-122">Vyvolá <xref:System.NotImplementedException> zprávu oznamující, že není implementována.</span><span class="sxs-lookup"><span data-stu-id="5dc18-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="5dc18-123">Se aktualizuje později v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="5dc18-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="5dc18-124">V adresáři *testování částí-using-dotnet-test* spusťte následující příkaz pro přidání projektu knihovny tříd do řešení:</span><span class="sxs-lookup"><span data-stu-id="5dc18-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="5dc18-125">Vytvořte projekt *PrimeService. Tests* spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5dc18-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="5dc18-126">Předchozí příkaz:</span><span class="sxs-lookup"><span data-stu-id="5dc18-126">The preceding command:</span></span>
  * <span data-ttu-id="5dc18-127">Vytvoří projekt *PrimeService. Tests* v adresáři *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="5dc18-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5dc18-128">Testovací projekt používá [xUnit](https://xunit.net/) jako knihovnu testů.</span><span class="sxs-lookup"><span data-stu-id="5dc18-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="5dc18-129">Konfiguruje Test Runner přidáním následujících `<PackageReference />` prvků do souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="5dc18-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="5dc18-130">Microsoft. NET. test. SDK</span><span class="sxs-lookup"><span data-stu-id="5dc18-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="5dc18-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="5dc18-131">"xunit"</span></span>
    * <span data-ttu-id="5dc18-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="5dc18-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="5dc18-133">Přidejte testovací projekt do souboru řešení spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5dc18-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="5dc18-134">Přidejte `PrimeService` knihovnu tříd jako závislost do projektu *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="5dc18-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="5dc18-135">Příkazy k vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="5dc18-135">Commands to create the solution</span></span>

<span data-ttu-id="5dc18-136">Tato část shrnuje všechny příkazy v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5dc18-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="5dc18-137">Pokud jste dokončili kroky v předchozí části, přeskočte tuto část.</span><span class="sxs-lookup"><span data-stu-id="5dc18-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="5dc18-138">Následující příkazy vytvoří testovací řešení na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="5dc18-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="5dc18-139">Pro macOS a UNIX aktualizujte `ren` příkaz na verzi operačního systému `ren` pro přejmenování souboru:</span><span class="sxs-lookup"><span data-stu-id="5dc18-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="5dc18-140">Postupujte podle pokynů v části "nahrazení kódu v *PrimeService. vb* následujícím kódem" v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5dc18-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="5dc18-141">Vytvořit test</span><span class="sxs-lookup"><span data-stu-id="5dc18-141">Create a test</span></span>

<span data-ttu-id="5dc18-142">Oblíbeným přístupem v rámci vývoje řízených testů (TDD) je napsat test před implementací cílového kódu.</span><span class="sxs-lookup"><span data-stu-id="5dc18-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="5dc18-143">V tomto kurzu se používá přístup TDD.</span><span class="sxs-lookup"><span data-stu-id="5dc18-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="5dc18-144">`IsPrime`Metoda je volat, ale není implementovaná.</span><span class="sxs-lookup"><span data-stu-id="5dc18-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="5dc18-145">Testovací volání se `IsPrime` nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5dc18-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="5dc18-146">Pomocí TDD je napsán test, u kterého se říká selhání.</span><span class="sxs-lookup"><span data-stu-id="5dc18-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="5dc18-147">Cílový kód je aktualizován, aby provedl test Pass.</span><span class="sxs-lookup"><span data-stu-id="5dc18-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="5dc18-148">Tento přístup se opakuje, napíše se neúspěšný test a pak se aktualizuje cílový kód, který se má předat.</span><span class="sxs-lookup"><span data-stu-id="5dc18-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="5dc18-149">Aktualizujte projekt *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="5dc18-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="5dc18-150">Odstraňte *PrimeService. Tests/UnitTest1. vb*.</span><span class="sxs-lookup"><span data-stu-id="5dc18-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="5dc18-151">Vytvořte soubor *PrimeService. Tests/PrimeService_IsPrimeShould. vb* .</span><span class="sxs-lookup"><span data-stu-id="5dc18-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="5dc18-152">Kód v *jazyce PrimeService_IsPrimeShould. vb* nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5dc18-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="5dc18-153">`[Fact]`Atribut deklaruje testovací metodu, která je spuštěna nástrojem Test Runner.</span><span class="sxs-lookup"><span data-stu-id="5dc18-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="5dc18-154">Ze složky *PrimeService. Tests* spusťte `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="5dc18-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="5dc18-155">Příkaz [dotnet test](../tools/dotnet-test.md) vytvoří oba projekty a spustí testy.</span><span class="sxs-lookup"><span data-stu-id="5dc18-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="5dc18-156">XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="5dc18-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="5dc18-157">`dotnet test`spustí Test Runner pomocí projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="5dc18-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="5dc18-158">Test se nezdařil, protože `IsPrime` nebyl implementován.</span><span class="sxs-lookup"><span data-stu-id="5dc18-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="5dc18-159">Pomocí přístupu TDD zapište pouze dostatečný kód, aby tento test prošl.</span><span class="sxs-lookup"><span data-stu-id="5dc18-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="5dc18-160">Aktualizujte `IsPrime` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5dc18-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="5dc18-161">Spusťte `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="5dc18-161">Run `dotnet test`.</span></span> <span data-ttu-id="5dc18-162">Test byl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="5dc18-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="5dc18-163">Přidat další testy</span><span class="sxs-lookup"><span data-stu-id="5dc18-163">Add more tests</span></span>

<span data-ttu-id="5dc18-164">Přidejte testy hlavní číslo pro 0 a-1.</span><span class="sxs-lookup"><span data-stu-id="5dc18-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="5dc18-165">Předchozí test můžete zkopírovat a změnit následující kód na použití 0 a-1:</span><span class="sxs-lookup"><span data-stu-id="5dc18-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="5dc18-166">Kopírování testovacího kódu, pokud se změní pouze parametr, je výsledkem duplicity kódu a dispozici determinističtější testů.</span><span class="sxs-lookup"><span data-stu-id="5dc18-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="5dc18-167">Následující atributy xUnit umožňují zápis sady podobných testů:</span><span class="sxs-lookup"><span data-stu-id="5dc18-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="5dc18-168">`[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="5dc18-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="5dc18-169">`[InlineData]`atribut určuje hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="5dc18-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="5dc18-170">Místo vytváření nových testů použijte předchozí atributy xUnit a vytvořte jednu teorie.</span><span class="sxs-lookup"><span data-stu-id="5dc18-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="5dc18-171">Nahraďte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5dc18-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="5dc18-172">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5dc18-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="5dc18-173">V předchozím kódu `[Theory]` a `[InlineData]` Povolte testování více hodnot, které jsou menší než dvě.</span><span class="sxs-lookup"><span data-stu-id="5dc18-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="5dc18-174">Dva je nejmenší číslo prvočísla.</span><span class="sxs-lookup"><span data-stu-id="5dc18-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="5dc18-175">Spuštění `dotnet test` , dva z testů selžou.</span><span class="sxs-lookup"><span data-stu-id="5dc18-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="5dc18-176">Chcete-li provést všechny testy, aktualizujte `IsPrime` metodu následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5dc18-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="5dc18-177">Po přístupu ke službě TDD přidejte další neúspěšné testy a pak aktualizujte cílový kód.</span><span class="sxs-lookup"><span data-stu-id="5dc18-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="5dc18-178">Viz [Dokončená verze testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="5dc18-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="5dc18-179">Metoda Completed `IsPrime` není efektivní algoritmem pro testování primality.</span><span class="sxs-lookup"><span data-stu-id="5dc18-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5dc18-180">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5dc18-180">Additional resources</span></span>

- [<span data-ttu-id="5dc18-181">Oficiální web xUnit.net</span><span class="sxs-lookup"><span data-stu-id="5dc18-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="5dc18-182">Testování logiky kontroleru v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5dc18-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
