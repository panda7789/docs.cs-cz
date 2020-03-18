---
title: Testování částí kódu Jazyka C# v rozhraní .NET Core pomocí dotnet test a xUnit
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240893"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="c37aa-103">Testování částí C# v .NET Core pomocí dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="c37aa-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="c37aa-104">Tento kurz ukazuje, jak vytvořit řešení obsahující projekt testování částí a projekt zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="c37aa-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="c37aa-105">Chcete-li postupovat podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="c37aa-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="c37aa-106">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c37aa-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="c37aa-107">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="c37aa-107">Create the solution</span></span>

<span data-ttu-id="c37aa-108">V této části je vytvořeno řešení, které obsahuje zdroj ové a testovací projekty.</span><span class="sxs-lookup"><span data-stu-id="c37aa-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="c37aa-109">Dokončené řešení má následující adresářovou strukturu:</span><span class="sxs-lookup"><span data-stu-id="c37aa-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="c37aa-110">Následující pokyny poskytují kroky k vytvoření testovacího řešení.</span><span class="sxs-lookup"><span data-stu-id="c37aa-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="c37aa-111">Pokyny k vytvoření testovacího řešení v jednom kroku naleznete v [tématu Příkazy k vytvoření testovacího řešení.](#create-test-cmd)</span><span class="sxs-lookup"><span data-stu-id="c37aa-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="c37aa-112">Otevřete okno prostředí.</span><span class="sxs-lookup"><span data-stu-id="c37aa-112">Open a shell window.</span></span>
* <span data-ttu-id="c37aa-113">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c37aa-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="c37aa-114">Příkaz [`dotnet new sln`](../tools/dotnet-new.md) vytvoří nové řešení v adresáři *testování jednotky using-dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="c37aa-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="c37aa-115">Změňte adresář na složku *testování jednotky pomocí dotnet-test.*</span><span class="sxs-lookup"><span data-stu-id="c37aa-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="c37aa-116">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c37aa-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="c37aa-117">Příkaz [`dotnet new classlib`](../tools/dotnet-new.md) vytvoří nový projekt knihovny tříd ve složce *PrimeService.*</span><span class="sxs-lookup"><span data-stu-id="c37aa-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="c37aa-118">Nová knihovna tříd bude obsahovat kód, který má být testován.</span><span class="sxs-lookup"><span data-stu-id="c37aa-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="c37aa-119">Přejmenujte *Class1.cs* na *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="c37aa-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="c37aa-120">Nahraďte kód v *PrimeService.cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c37aa-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* <span data-ttu-id="c37aa-121">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="c37aa-121">The preceding code:</span></span>
  * <span data-ttu-id="c37aa-122">Vyvolá <xref:System.NotImplementedException> se zprávou označující, že není implementována.</span><span class="sxs-lookup"><span data-stu-id="c37aa-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="c37aa-123">Je aktualizován později v kurzu.</span><span class="sxs-lookup"><span data-stu-id="c37aa-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="c37aa-124">V adresáři *testování jednotky using-dotnet-test* přidejte do řešení následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c37aa-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="c37aa-125">Vytvořte projekt *PrimeService.Tests* spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="c37aa-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="c37aa-126">Předchozí příkaz:</span><span class="sxs-lookup"><span data-stu-id="c37aa-126">The preceding command:</span></span>
  * <span data-ttu-id="c37aa-127">Vytvoří projekt *PrimeService.Tests* v adresáři *PrimeService.Tests.*</span><span class="sxs-lookup"><span data-stu-id="c37aa-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="c37aa-128">Testovací projekt používá [xUnit](https://xunit.github.io/) jako testovací knihovnu.</span><span class="sxs-lookup"><span data-stu-id="c37aa-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="c37aa-129">Nakonfiguruje testovacího `<PackageReference />`běžce přidáním následujících prvků do souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="c37aa-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="c37aa-130">"Microsoft.NET.Test.Sdk"</span><span class="sxs-lookup"><span data-stu-id="c37aa-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="c37aa-131">"xunit"</span><span class="sxs-lookup"><span data-stu-id="c37aa-131">"xunit"</span></span>
    * <span data-ttu-id="c37aa-132">"xunit.runner.visualstudio"</span><span class="sxs-lookup"><span data-stu-id="c37aa-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="c37aa-133">Přidejte testovací projekt do souboru řešení spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="c37aa-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="c37aa-134">Přidejte `PrimeService` knihovnu tříd jako závislost do projektu *PrimeService.Tests:*</span><span class="sxs-lookup"><span data-stu-id="c37aa-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="c37aa-135">Příkazy k vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="c37aa-135">Commands to create the solution</span></span>

<span data-ttu-id="c37aa-136">Tato část shrnuje všechny příkazy v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="c37aa-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="c37aa-137">Pokud jste dokončili kroky v předchozí části, tuto část přeskočte.</span><span class="sxs-lookup"><span data-stu-id="c37aa-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="c37aa-138">Následující příkazy vytvořit testovací řešení v počítači se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="c37aa-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="c37aa-139">V případě macOS a `ren` Unixu aktualizujte `ren` příkaz na verzi operačního systému a přejmenujte soubor:</span><span class="sxs-lookup"><span data-stu-id="c37aa-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="c37aa-140">Postupujte podle pokynů pro "Nahradit kód v *PrimeService.cs* s následujícím kódem" v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="c37aa-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="c37aa-141">Vytvoření testu</span><span class="sxs-lookup"><span data-stu-id="c37aa-141">Create a test</span></span>

<span data-ttu-id="c37aa-142">Populární přístup ve vývoji řízený testováním (TDD) je napsat test před implementací cílového kódu.</span><span class="sxs-lookup"><span data-stu-id="c37aa-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="c37aa-143">Tento kurz používá přístup TDD.</span><span class="sxs-lookup"><span data-stu-id="c37aa-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="c37aa-144">Metoda `IsPrime` je volatelná, ale není implementována.</span><span class="sxs-lookup"><span data-stu-id="c37aa-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="c37aa-145">Testovací volání `IsPrime` se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="c37aa-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="c37aa-146">S TDD je napsán test, o kterých je známo, že se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="c37aa-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="c37aa-147">Cílový kód je aktualizován tak, aby test projít.</span><span class="sxs-lookup"><span data-stu-id="c37aa-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="c37aa-148">Budete pokračovat v opakování tohoto přístupu, psaní selhání testu a pak aktualizace cílového kódu předat.</span><span class="sxs-lookup"><span data-stu-id="c37aa-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="c37aa-149">Aktualizace projektu *PrimeService.Tests:*</span><span class="sxs-lookup"><span data-stu-id="c37aa-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="c37aa-150">Odstranit *PrimeService.Tests/UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="c37aa-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="c37aa-151">Vytvořte soubor *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*</span><span class="sxs-lookup"><span data-stu-id="c37aa-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="c37aa-152">Nahraďte kód v *PrimeService_IsPrimeShould.cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c37aa-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

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

<span data-ttu-id="c37aa-153">Atribut `[Fact]` deklaruje testovací metodu, která je spuštěna testovacím běžcem.</span><span class="sxs-lookup"><span data-stu-id="c37aa-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="c37aa-154">Ze složky *PrimeService.Tests* spusťte `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="c37aa-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="c37aa-155">[Dotnet test](../tools/dotnet-test.md) příkaz vytvoří oba projekty a spustí testy.</span><span class="sxs-lookup"><span data-stu-id="c37aa-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="c37aa-156">XUnit test runner obsahuje vstupní bod programu ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="c37aa-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="c37aa-157">`dotnet test`spustí testovací běh pomocí projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="c37aa-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="c37aa-158">Test se `IsPrime` nezdaří, protože nebyl implementován.</span><span class="sxs-lookup"><span data-stu-id="c37aa-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="c37aa-159">Pomocí přístupu TDD, napište pouze dostatek kódu, aby tento test projde.</span><span class="sxs-lookup"><span data-stu-id="c37aa-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="c37aa-160">Aktualizace `IsPrime` s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c37aa-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="c37aa-161">Spusťte `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="c37aa-161">Run `dotnet test`.</span></span> <span data-ttu-id="c37aa-162">Test projde.</span><span class="sxs-lookup"><span data-stu-id="c37aa-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="c37aa-163">Přidání dalších testů</span><span class="sxs-lookup"><span data-stu-id="c37aa-163">Add more tests</span></span>

<span data-ttu-id="c37aa-164">Přidejte testy prvočísel pro 0 a -1.</span><span class="sxs-lookup"><span data-stu-id="c37aa-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="c37aa-165">Můžete zkopírovat předchozí test a změnit následující kód pro použití 0 a -1:</span><span class="sxs-lookup"><span data-stu-id="c37aa-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="c37aa-166">Kopírování testovacího kódu při změně pouze parametru má za následek duplikaci kódu a testovací nadýmání.</span><span class="sxs-lookup"><span data-stu-id="c37aa-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="c37aa-167">Následující atributy xUnit umožňují zápis sady podobných testů:</span><span class="sxs-lookup"><span data-stu-id="c37aa-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="c37aa-168">`[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="c37aa-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="c37aa-169">`[InlineData]`atribut určuje hodnoty pro tyto vstupy.</span><span class="sxs-lookup"><span data-stu-id="c37aa-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="c37aa-170">Spíše než vytvářet nové testy, použijte předchozí xUnit atributy k vytvoření jedné teorie.</span><span class="sxs-lookup"><span data-stu-id="c37aa-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="c37aa-171">Nahraďte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c37aa-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="c37aa-172">s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c37aa-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="c37aa-173">V předchozím kódu `[Theory]` a `[InlineData]` povolit testování několik hodnot menší než dvě.</span><span class="sxs-lookup"><span data-stu-id="c37aa-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="c37aa-174">Dvojka je nejmenší prvočíslo.</span><span class="sxs-lookup"><span data-stu-id="c37aa-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="c37aa-175">Spuštění `dotnet test`, dva testy se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="c37aa-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="c37aa-176">Chcete-li provést všechny testy `IsPrime` projít, aktualizujte metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="c37aa-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="c37aa-177">Podle přístupu TDD přidejte další testy selhání a aktualizujte cílový kód.</span><span class="sxs-lookup"><span data-stu-id="c37aa-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="c37aa-178">Podívejte se na [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="c37aa-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="c37aa-179">Dokončená `IsPrime` metoda není efektivní algoritmus pro testování primality.</span><span class="sxs-lookup"><span data-stu-id="c37aa-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c37aa-180">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c37aa-180">Additional resources</span></span>

- [<span data-ttu-id="c37aa-181">xUnit.net oficiální stránky</span><span class="sxs-lookup"><span data-stu-id="c37aa-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="c37aa-182">Logika testovacího řadiče v ASP.NET core</span><span class="sxs-lookup"><span data-stu-id="c37aa-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
