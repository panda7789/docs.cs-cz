---
title: Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET
description: Tento kurz vysvětluje, jak uspořádat a otestovat projekty .NET Core z příkazového řádku.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239908"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="868be-103">Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="868be-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="868be-104">Tento kurz následuje [Začínáme s rozhraním .NET Core ve Windows/Linux/macOS pomocí příkazového řádku](cli-create-console-app.md), který vás přenese nad rámec vytvoření jednoduché konzolové aplikace pro vývoj pokročilých a dobře organizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="868be-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="868be-105">Poté, co ukazuje, jak používat složky k uspořádání kódu, tento kurz ukazuje, jak rozšířit konzolové aplikace s [xUnit](https://xunit.github.io/) testování rámce.</span><span class="sxs-lookup"><span data-stu-id="868be-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="868be-106">Uspořádání kódu pomocí složek</span><span class="sxs-lookup"><span data-stu-id="868be-106">Using folders to organize code</span></span>

<span data-ttu-id="868be-107">Pokud chcete do konzolové aplikace zavést nové typy, můžete tak učinit přidáním souborů obsahujících typy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="868be-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="868be-108">Pokud například přidáte do `AccountInformation` `MonthlyReportRecords` projektu soubory obsahující a typy, struktura souborů projektu je plochá a snadno se naviguje:</span><span class="sxs-lookup"><span data-stu-id="868be-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="868be-109">To však funguje dobře pouze v případě, že velikost projektu je relativně malá.</span><span class="sxs-lookup"><span data-stu-id="868be-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="868be-110">Dokážete si představit, co se stane, když do projektu přidáte 20 typů?</span><span class="sxs-lookup"><span data-stu-id="868be-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="868be-111">Projekt rozhodně nebude snadné se orientovat a udržovat s tím, že mnoho souborů odhazování kořenového adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="868be-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="868be-112">Chcete-li projekt uspořádat, vytvořte novou složku a pojmenujte ji *Modely* pro uložení textových souborů.</span><span class="sxs-lookup"><span data-stu-id="868be-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="868be-113">Umístěte textové soubory do složky *Modely:*</span><span class="sxs-lookup"><span data-stu-id="868be-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="868be-114">Projekty, které logicky seskupují soubory do složek, lze snadno procházet a udržovat.</span><span class="sxs-lookup"><span data-stu-id="868be-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="868be-115">V další části vytvoříte složitější ukázku se složkami a testováním částí.</span><span class="sxs-lookup"><span data-stu-id="868be-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="868be-116">Uspořádání a testování pomocí newtypes domácí chránič ukázky</span><span class="sxs-lookup"><span data-stu-id="868be-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="868be-117">Vytvoření vzorku</span><span class="sxs-lookup"><span data-stu-id="868be-117">Building the sample</span></span>

<span data-ttu-id="868be-118">Následující kroky můžete sledovat pomocí [NewTypes Pets Ukázka](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="868be-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="868be-119">Typy jsou logicky uspořádány do struktury složek, která umožňuje přidání více typů později a testy jsou také logicky umístěny do složek, které umožňují přidání dalších testů později.</span><span class="sxs-lookup"><span data-stu-id="868be-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="868be-120">Ukázka obsahuje dva `Dog` `Cat`typy a , a má `IPet`je implementovat společné rozhraní , .</span><span class="sxs-lookup"><span data-stu-id="868be-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="868be-121">Pro `NewTypes` projekt, vaším cílem je uspořádat pet-související typy do složky *Domácí zvířata.*</span><span class="sxs-lookup"><span data-stu-id="868be-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="868be-122">Pokud další sadu typů je přidán později, *WildAnimals* například, jsou umístěny ve složce *NewTypes* vedle *pets* složky.</span><span class="sxs-lookup"><span data-stu-id="868be-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="868be-123">Složka *WildAnimals* může obsahovat typy pro zvířata, `Squirrel` `Rabbit` která nejsou domácími mazlíčky, například a typy.</span><span class="sxs-lookup"><span data-stu-id="868be-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="868be-124">Tímto způsobem, jak jsou přidány typy, projekt zůstává dobře organizovaný.</span><span class="sxs-lookup"><span data-stu-id="868be-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="868be-125">Vytvořte následující strukturu složek s indikovaným obsahem souboru:</span><span class="sxs-lookup"><span data-stu-id="868be-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="868be-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="868be-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="868be-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="868be-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="868be-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="868be-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="868be-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="868be-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="868be-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="868be-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="868be-131">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="868be-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="868be-132">Získejte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="868be-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="868be-133">Volitelné cvičení: Rozšířením tohoto projektu můžete `Bird`přidat nový typ domácího mazlíčka, například .</span><span class="sxs-lookup"><span data-stu-id="868be-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="868be-134">Aby ptačí `TalkToOwner` metoda dát `Tweet!` majiteli.</span><span class="sxs-lookup"><span data-stu-id="868be-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="868be-135">Spusťte aplikaci znovu.</span><span class="sxs-lookup"><span data-stu-id="868be-135">Run the app again.</span></span> <span data-ttu-id="868be-136">Výstup bude zahrnovat`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="868be-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="868be-137">Testování vzorku</span><span class="sxs-lookup"><span data-stu-id="868be-137">Testing the sample</span></span>

<span data-ttu-id="868be-138">Projekt `NewTypes` je na svém místě a vy jste ho uspořádali tak, že jste ve složce uchovávali typy související s domácími zvířaty.</span><span class="sxs-lookup"><span data-stu-id="868be-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="868be-139">Dále vytvořte testovací projekt a začněte psát testy pomocí rozhraní [xUnit](https://xunit.github.io/) test.</span><span class="sxs-lookup"><span data-stu-id="868be-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="868be-140">Testování částí umožňuje automaticky zkontrolovat chování vašeho domácího mazlíčka, abyste potvrdili, že fungují správně.</span><span class="sxs-lookup"><span data-stu-id="868be-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="868be-141">Přejděte zpět do složky *src* a vytvořte *testovací* složku se složkou *NewTypesTests* v ní.</span><span class="sxs-lookup"><span data-stu-id="868be-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="868be-142">Na příkazovém řádku ze složky `dotnet new xunit` *NewTypesTests* spusťte .</span><span class="sxs-lookup"><span data-stu-id="868be-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="868be-143">Tím se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="868be-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="868be-144">Testovací projekt nemůže aktuálně otestovat `NewTypes` typy v aplikaci `NewTypes` a vyžaduje odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="868be-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="868be-145">Chcete-li přidat odkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) na projekt, použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="868be-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="868be-146">Nebo máte také možnost ručně přidat odkaz na projekt `<ItemGroup>` přidáním uzlu do souboru *NewTypesTests.csproj:*</span><span class="sxs-lookup"><span data-stu-id="868be-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="868be-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="868be-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="868be-148">Soubor *NewTypesTests.csproj* obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="868be-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="868be-149">Odkaz na `Microsoft.NET.Test.Sdk`balíček , testovací infrastrukturu .NET</span><span class="sxs-lookup"><span data-stu-id="868be-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="868be-150">Odkaz na `xunit`balíček , rozhraní xUnit testing framework</span><span class="sxs-lookup"><span data-stu-id="868be-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="868be-151">Odkaz na `xunit.runner.visualstudio`balíček , zkušební běžec</span><span class="sxs-lookup"><span data-stu-id="868be-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="868be-152">Odkaz na `NewTypes`projekt , kód k testování</span><span class="sxs-lookup"><span data-stu-id="868be-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="868be-153">Změňte název *UnitTest1.cs,* *chcete-li PetTests.cs* a nahraďte kód v souboru následujícím:</span><span class="sxs-lookup"><span data-stu-id="868be-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="868be-154">Volitelné cvičení: Pokud `Bird` jste přidali typ `Tweet!` dříve, který dává a vlastníkovi, `BirdTalkToOwnerReturnsTweet`přidejte testovací `TalkToOwner` metodu do `Bird` souboru *PetTests.cs* , zkontrolujte, zda metoda funguje správně pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="868be-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="868be-155">I když `expected` očekáváte, že hodnoty a `actual` jsou `Assert.NotEqual` stejné, počáteční kontrolní výraz s kontrolou určuje, že tyto hodnoty *nejsou stejné*.</span><span class="sxs-lookup"><span data-stu-id="868be-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="868be-156">Vždy zpočátku vytvořit test nezdaří, aby bylo možné zkontrolovat logiku testu.</span><span class="sxs-lookup"><span data-stu-id="868be-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="868be-157">Po potvrzení, že test se nezdaří, upravte kontrolní výraz povolit test předat.</span><span class="sxs-lookup"><span data-stu-id="868be-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="868be-158">Následující ukazuje kompletní strukturu projektu:</span><span class="sxs-lookup"><span data-stu-id="868be-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="868be-159">Začněte v adresáři *test/NewTypesTests.*</span><span class="sxs-lookup"><span data-stu-id="868be-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="868be-160">Obnovte testovací projekt [`dotnet restore`](../tools/dotnet-restore.md) pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="868be-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="868be-161">Spusťte testy [`dotnet test`](../tools/dotnet-test.md) pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="868be-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="868be-162">Tento příkaz spustí testovací běh zadaný v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="868be-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="868be-163">Podle očekávání se testování nezdaří a konzola zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="868be-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
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

<span data-ttu-id="868be-164">Změna kontrolních výrazů `Assert.NotEqual` testů `Assert.Equal`z do :</span><span class="sxs-lookup"><span data-stu-id="868be-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="868be-165">Znovu spusťte testy `dotnet test` pomocí příkazu a získejte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="868be-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="868be-166">Testování projde.</span><span class="sxs-lookup"><span data-stu-id="868be-166">Testing passes.</span></span> <span data-ttu-id="868be-167">Metody typů zvířat vrátí správné hodnoty při rozhovoru s majitelem.</span><span class="sxs-lookup"><span data-stu-id="868be-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="868be-168">Naučili jste se techniky pro organizaci a testování projektů pomocí xUnit.</span><span class="sxs-lookup"><span data-stu-id="868be-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="868be-169">Pokračujte s těmito technikami jejich použití ve svých vlastních projektech.</span><span class="sxs-lookup"><span data-stu-id="868be-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="868be-170">*Happy kódování!*</span><span class="sxs-lookup"><span data-stu-id="868be-170">*Happy coding!*</span></span>
