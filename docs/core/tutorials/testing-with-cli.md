---
title: Uspořádání a testování projektů pomocí příkazového řádku .NET Core
description: Tento kurz vysvětluje, jak uspořádat a Testovací projekty .NET Core z příkazového řádku.
author: cartermp
ms.author: mairaw
ms.date: 09/10/2018
ms.openlocfilehash: 9984b4f43ca8c09cc0948cad7e6c176127384361
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49415221"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="d8315-103">Uspořádání a testování projektů pomocí příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8315-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="d8315-104">V tomto kurzu následuje [Začínáme s .NET Core ve Windows, Linux nebo macOS pomocí příkazového řádku](using-with-xplat-cli.md), přechod nad rámec vytváření jednoduchou konzolovou aplikaci pro vývoj pokročilých a dobře organizovaný aplikací.</span><span class="sxs-lookup"><span data-stu-id="d8315-104">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="d8315-105">Po ukazuje, jak na složky slouží k uspořádání kódu, tento kurz ukazuje, jak rozšířit aplikaci konzoly pomocí [xUnit](https://xunit.github.io/) testování.</span><span class="sxs-lookup"><span data-stu-id="d8315-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="d8315-106">Použití složek k uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="d8315-106">Using folders to organize code</span></span>

<span data-ttu-id="d8315-107">Pokud chcete zavést nové typy do konzolové aplikace, provedete to tak, že přidáte soubory, které obsahují typy pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8315-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="d8315-108">Například pokud přidáte soubory, které obsahují `AccountInformation` a `MonthlyReportRecords` typy do projektu, je struktura souboru projektu bez stromové struktury a usnadňuje přechod:</span><span class="sxs-lookup"><span data-stu-id="d8315-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="d8315-109">Ale toto funguje, pouze i když je poměrně malá velikost vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="d8315-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="d8315-110">Můžete si představit, co se stane, pokud je 20 typy přidat do projektu?</span><span class="sxs-lookup"><span data-stu-id="d8315-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="d8315-111">Projekt jednoznačně by se snadno procházet a udržovat s, který mnoho souborů littering kořenový adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="d8315-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="d8315-112">K uspořádání projekt, vytvořte novou složku s názvem *modely* pro uložení souborů typů.</span><span class="sxs-lookup"><span data-stu-id="d8315-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="d8315-113">Umístěte soubory typu do *modely* složky:</span><span class="sxs-lookup"><span data-stu-id="d8315-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="d8315-114">Projekty, které logicky skupiny soubory do složek, které jsou snadno procházet a udržovat.</span><span class="sxs-lookup"><span data-stu-id="d8315-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="d8315-115">V další části vytvořit složitější vzorek se složkami a testování částí.</span><span class="sxs-lookup"><span data-stu-id="d8315-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="d8315-116">Uspořádání a testování s využitím ukázkové NewTypes mazlíčků</span><span class="sxs-lookup"><span data-stu-id="d8315-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="d8315-117">Vytváření vzorku</span><span class="sxs-lookup"><span data-stu-id="d8315-117">Building the sample</span></span>

<span data-ttu-id="d8315-118">Následující postup, můžete buď absolvovat pomocí [NewTypes domácí zvířata ukázka](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="d8315-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="d8315-119">Typy jsou logicky uspořádány do struktury složek, který umožňuje přidání dalších typů později, a testy jsou také logicky umístěny ve složkách umožňující přidání další testy později.</span><span class="sxs-lookup"><span data-stu-id="d8315-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="d8315-120">Ukázka obsahuje dva typy `Dog` a `Cat`a je jim implementovat obecné rozhraní `IPet`.</span><span class="sxs-lookup"><span data-stu-id="d8315-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="d8315-121">Pro `NewTypes` projektu, vaším cílem je uspořádat domácí mazlíček souvisejících typů do *Mazlíčci* složky.</span><span class="sxs-lookup"><span data-stu-id="d8315-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="d8315-122">Pokud se později přidá jinou sadu typů *WildAnimals* například přejdou na *NewTypes* složce společně s *Mazlíčci* složky.</span><span class="sxs-lookup"><span data-stu-id="d8315-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="d8315-123">*WildAnimals* složka může obsahovat typy pro zvířata, které nejsou mazlíčků, jako například `Squirrel` a `Rabbit` typy.</span><span class="sxs-lookup"><span data-stu-id="d8315-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="d8315-124">Tímto způsobem přidávání typů projektu zůstane dobře uspořádané.</span><span class="sxs-lookup"><span data-stu-id="d8315-124">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="d8315-125">Vytvořte následující strukturu složek s obsahem souboru uvedené:</span><span class="sxs-lookup"><span data-stu-id="d8315-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="d8315-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="d8315-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="d8315-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="d8315-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="d8315-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="d8315-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="d8315-129">*Soubor program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d8315-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="d8315-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="d8315-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="d8315-131">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d8315-131">Execute the following command:</span></span>

```console
dotnet run
```

<span data-ttu-id="d8315-132">Získáte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8315-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="d8315-133">Volitelné cvičení: můžete přidat nový domácí mazlíčky typ, například `Bird`, rozšířením tento projekt.</span><span class="sxs-lookup"><span data-stu-id="d8315-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="d8315-134">Ujistěte se, zobrazení z ptačí perspektivy `TalkToOwner` Poskytněte metodu `Tweet!` na vlastníka.</span><span class="sxs-lookup"><span data-stu-id="d8315-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="d8315-135">Znovu spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d8315-135">Run the app again.</span></span> <span data-ttu-id="d8315-136">Výstup bude zahrnovat `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="d8315-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="d8315-137">Testování ukázky</span><span class="sxs-lookup"><span data-stu-id="d8315-137">Testing the sample</span></span>

<span data-ttu-id="d8315-138">`NewTypes` Projekt je na místě a uspořádán udržováním mazlíčci související typy ve složce.</span><span class="sxs-lookup"><span data-stu-id="d8315-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="d8315-139">V dalším kroku vytvoření testovacího projektu a začít psát testy s [xUnit](https://xunit.github.io/) rozhraní pro testování.</span><span class="sxs-lookup"><span data-stu-id="d8315-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="d8315-140">Testování částí umožňuje automaticky zjišťovat chování domácí mazlíčky typů potvrďte, že funguje správně.</span><span class="sxs-lookup"><span data-stu-id="d8315-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="d8315-141">Vytvoření *testování* složka s *NewTypesTests* složky v něm.</span><span class="sxs-lookup"><span data-stu-id="d8315-141">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="d8315-142">Na příkazovém řádku z *NewTypesTests* složce spusťte `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="d8315-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="d8315-143">Tímto se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="d8315-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="d8315-144">Projekt testů nelze aktuálně typy v testu `NewTypes` a vyžaduje odkaz na projekt `NewTypes` projektu.</span><span class="sxs-lookup"><span data-stu-id="d8315-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="d8315-145">Chcete-li přidat odkaz na projekt, použijte [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="d8315-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="d8315-146">Máte také možnost ručně přidáte odkaz na projekt tak, že přidáte `<ItemGroup>` uzlu *NewTypesTests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="d8315-146">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="d8315-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="d8315-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="d8315-148">*NewTypesTests.csproj* soubor obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="d8315-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="d8315-149">Odkaz na balíček `Microsoft.NET.Test.Sdk`, .NET testování infrastruktury</span><span class="sxs-lookup"><span data-stu-id="d8315-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="d8315-150">Odkaz na balíček `xunit`, xUnit testování</span><span class="sxs-lookup"><span data-stu-id="d8315-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="d8315-151">Odkaz na balíček `xunit.runner.visualstudio`, nástroj test runner</span><span class="sxs-lookup"><span data-stu-id="d8315-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="d8315-152">Odkaz na projekt `NewTypes`, kód pro testování</span><span class="sxs-lookup"><span data-stu-id="d8315-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="d8315-153">Změňte název *UnitTest1.cs* k *PetTests.cs* a nahraďte kód v souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d8315-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="d8315-154">Volitelné cvičení: Pokud jste přidali `Bird` dříve typ, který provede `Tweet!` vlastníkovi, přidejte testovací metody pro *PetTests.cs* souboru, `BirdTalkToOwnerReturnsTweet`, zkontroluje, jestli `TalkToOwner` metoda se dá použít správně `Bird` typu.</span><span class="sxs-lookup"><span data-stu-id="d8315-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="d8315-155">I když můžete očekávat, že `expected` a `actual` jsou hodnoty stejné, počáteční kontrolní výraz se `Assert.NotEqual` kontroly Určuje, že tyto hodnoty jsou *nerovná*.</span><span class="sxs-lookup"><span data-stu-id="d8315-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="d8315-156">Vždy nejprve vytvořte test selhání za účelem ověření logiky testu.</span><span class="sxs-lookup"><span data-stu-id="d8315-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="d8315-157">Jakmile potvrdíte, že se test nezdaří, upravte kontrolní výraz, aby test proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="d8315-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="d8315-158">Následuje ukázka struktury dokončený projekt:</span><span class="sxs-lookup"><span data-stu-id="d8315-158">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="d8315-159">Spustit v *test/NewTypesTests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="d8315-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="d8315-160">Obnovit testovací projekt s [ `dotnet restore` ](../tools/dotnet-restore.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="d8315-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="d8315-161">Spustit testy pomocí [ `dotnet test` ](../tools/dotnet-test.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="d8315-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="d8315-162">Tento příkaz spustí nástroj test runner zadané v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d8315-162">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="d8315-163">Podle očekávání, testování selže a konzoly se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8315-163">As expected, testing fails, and the console displays the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="d8315-164">Změnit kontrolní výrazy testy z `Assert.NotEqual` k `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="d8315-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="d8315-165">Znovu spusťte testy s `dotnet test` příkazů a získat následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8315-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="d8315-166">Testuje se předá.</span><span class="sxs-lookup"><span data-stu-id="d8315-166">Testing passes.</span></span> <span data-ttu-id="d8315-167">Domácí mazlíčky typy metody vrací správné hodnoty, když mluvíme vlastníkovi.</span><span class="sxs-lookup"><span data-stu-id="d8315-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="d8315-168">Když jste se naučili techniky k uspořádání a testování projektů s použitím xUnit.</span><span class="sxs-lookup"><span data-stu-id="d8315-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="d8315-169">Pomocí následujících postupů jejich použití ve vašich vlastních projektů přejdete vpřed.</span><span class="sxs-lookup"><span data-stu-id="d8315-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="d8315-170">*Šťastné kódování!*</span><span class="sxs-lookup"><span data-stu-id="d8315-170">*Happy coding!*</span></span>

