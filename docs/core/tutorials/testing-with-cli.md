---
title: Organizování a testování projektů pomocí .NET Core CLI
description: V tomto kurzu se dozvíte, jak organizovat a testovat projekty .NET Core z příkazového řádku.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 58c78c0f11ab1b275e4e4d05bf1da32562333c91
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84325942"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="1c67b-103">Organizování a testování projektů pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="1c67b-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="1c67b-104">Tento kurz následuje [kurz: Vytvoření konzolové aplikace pomocí .NET Core s využitím Visual Studio Code](with-visual-studio-code.md), který vám přesáhne vytvoření jednoduché konzolové aplikace pro vývoj aplikací pro pokročilé a dobře uspořádané aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c67b-104">This tutorial follows [Tutorial: Create a console application with .NET Core using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="1c67b-105">Po zobrazení, jak používat složky k uspořádání kódu, se v tomto kurzu dozvíte, jak roztáhnout konzolovou aplikaci pomocí testovacího rozhraní [xUnit](https://xunit.github.io/) .</span><span class="sxs-lookup"><span data-stu-id="1c67b-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="1c67b-106">Použití složek k uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="1c67b-106">Using folders to organize code</span></span>

<span data-ttu-id="1c67b-107">Pokud chcete zavést nové typy do konzolové aplikace, můžete to udělat tak, že přidáte soubory, které obsahují typy do aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c67b-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="1c67b-108">Například pokud přidáte soubory obsahující `AccountInformation` a `MonthlyReportRecords` typy do projektu, struktura souboru projektu je plochá a Snadná navigace:</span><span class="sxs-lookup"><span data-stu-id="1c67b-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="1c67b-109">To však funguje i v případě, že velikost projektu je poměrně malá.</span><span class="sxs-lookup"><span data-stu-id="1c67b-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="1c67b-110">Můžete si představit, co se stane, když do projektu přidáte 20 typů?</span><span class="sxs-lookup"><span data-stu-id="1c67b-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="1c67b-111">Projekt nebude možné snadno procházet a udržovat s tím, že mnoho souborů zachovává kořenový adresář projektu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="1c67b-112">Chcete-li uspořádat projekt, vytvořte novou složku a pojmenujte *modely* IT tak, aby obsahovaly soubory typu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="1c67b-113">Do složky *modely* umístěte soubory typu:</span><span class="sxs-lookup"><span data-stu-id="1c67b-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="1c67b-114">Projekty, které logicky seskupují soubory do složek, lze snadno procházet a udržovat.</span><span class="sxs-lookup"><span data-stu-id="1c67b-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="1c67b-115">V další části vytvoříte složitější vzorek pomocí složek a testování částí.</span><span class="sxs-lookup"><span data-stu-id="1c67b-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="1c67b-116">Uspořádání a testování pomocí ukázky NewTypes pro domácí zvířata</span><span class="sxs-lookup"><span data-stu-id="1c67b-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="1c67b-117">Vytvoření ukázky</span><span class="sxs-lookup"><span data-stu-id="1c67b-117">Building the sample</span></span>

<span data-ttu-id="1c67b-118">V následujících krocích můžete postupovat podle toho, jak se používá [Ukázka NewTypes pro domácí](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) prostředí, nebo můžete vytvořit vlastní soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="1c67b-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="1c67b-119">Typy jsou logicky uspořádány do struktury složek, která umožňuje přidání dalších typů později a testy jsou také logicky umístěny do složky umožňující přidání dalších testů později.</span><span class="sxs-lookup"><span data-stu-id="1c67b-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="1c67b-120">Ukázka obsahuje dva typy a a `Dog` `Cat` má k implementaci společné rozhraní `IPet` .</span><span class="sxs-lookup"><span data-stu-id="1c67b-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="1c67b-121">Pro `NewTypes` projekt je vaším cílem organizovat do *domácí složky domácí* typy, které souvisejí s PET.</span><span class="sxs-lookup"><span data-stu-id="1c67b-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="1c67b-122">Pokud se později přidá další sada typů, *WildAnimals* se například umístí do složky *NewTypes* vedle složky *domácí* .</span><span class="sxs-lookup"><span data-stu-id="1c67b-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="1c67b-123">Složka *WildAnimals* může obsahovat typy pro zvířata, která nejsou domácí, například `Squirrel` a `Rabbit` typy.</span><span class="sxs-lookup"><span data-stu-id="1c67b-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="1c67b-124">Tímto způsobem, že se přidávají typy, projekt zůstane dobře uspořádaný.</span><span class="sxs-lookup"><span data-stu-id="1c67b-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="1c67b-125">Vytvořte následující strukturu složek se zvýrazněným obsahem souboru:</span><span class="sxs-lookup"><span data-stu-id="1c67b-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="1c67b-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="1c67b-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="1c67b-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="1c67b-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="1c67b-130">*NewTypes. csproj*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="1c67b-131">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1c67b-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="1c67b-132">Získejte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1c67b-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="1c67b-133">Volitelné cvičení: rozšířením tohoto projektu můžete přidat nový typ PET, například `Bird` ,.</span><span class="sxs-lookup"><span data-stu-id="1c67b-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="1c67b-134">Nastavit metodu ptáku `TalkToOwner` jako `Tweet!` vlastníka.</span><span class="sxs-lookup"><span data-stu-id="1c67b-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="1c67b-135">Spusťte aplikaci znovu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-135">Run the app again.</span></span> <span data-ttu-id="1c67b-136">Výstup bude obsahovat`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="1c67b-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="1c67b-137">Testování ukázky</span><span class="sxs-lookup"><span data-stu-id="1c67b-137">Testing the sample</span></span>

<span data-ttu-id="1c67b-138">`NewTypes`Projekt je na místě a organizujete ho tím, že ve složce zachováte typy související s dalšími místy.</span><span class="sxs-lookup"><span data-stu-id="1c67b-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="1c67b-139">Dále vytvořte testovací projekt a začněte psát testy pomocí testovacího rozhraní [xUnit](https://xunit.github.io/) .</span><span class="sxs-lookup"><span data-stu-id="1c67b-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="1c67b-140">Testování částí vám umožní automaticky kontrolovat chování typů PET a ověřit tak, že fungují správně.</span><span class="sxs-lookup"><span data-stu-id="1c67b-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="1c67b-141">Přejděte zpět do složky *Src* a vytvořte *testovací* složku se složkou *NewTypesTests* v ní.</span><span class="sxs-lookup"><span data-stu-id="1c67b-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="1c67b-142">Na příkazovém řádku ze složky *NewTypesTests* spusťte `dotnet new xunit` .</span><span class="sxs-lookup"><span data-stu-id="1c67b-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="1c67b-143">Tím se vytvoří dva soubory: *NewTypesTests. csproj* a *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="1c67b-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="1c67b-144">Testovací projekt aktuálně nemůže testovat typy v `NewTypes` a vyžaduje odkaz na projekt `NewTypes` .</span><span class="sxs-lookup"><span data-stu-id="1c67b-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="1c67b-145">Chcete-li přidat odkaz na projekt, použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="1c67b-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="1c67b-146">Nebo máte také možnost ručně přidat odkaz na projekt přidáním `<ItemGroup>` uzlu do souboru *NewTypesTests. csproj* :</span><span class="sxs-lookup"><span data-stu-id="1c67b-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="1c67b-147">*NewTypesTests. csproj*:</span><span class="sxs-lookup"><span data-stu-id="1c67b-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="1c67b-148">Soubor *NewTypesTests. csproj* obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="1c67b-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="1c67b-149">Odkaz na balíček `Microsoft.NET.Test.Sdk` , na který je infrastruktura testování .NET</span><span class="sxs-lookup"><span data-stu-id="1c67b-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="1c67b-150">Odkaz na balíček `xunit` , na rozhraní xUnit Testing</span><span class="sxs-lookup"><span data-stu-id="1c67b-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="1c67b-151">Odkaz na balíček `xunit.runner.visualstudio` , na, Test Runner</span><span class="sxs-lookup"><span data-stu-id="1c67b-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="1c67b-152">Odkaz na projekt na `NewTypes` , kód k otestování</span><span class="sxs-lookup"><span data-stu-id="1c67b-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="1c67b-153">Změňte název *UnitTest1.cs* na *PetTests.cs* a nahraďte kód v souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1c67b-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="1c67b-154">Volitelné cvičení: Pokud jste přidali `Bird` typ dříve, který `Tweet!` vydává vlastníkovi, přidejte testovací metodu do souboru *PetTests.cs* , `BirdTalkToOwnerReturnsTweet` abyste zkontrolovali, že `TalkToOwner` metoda pro daný typ funguje správně `Bird` .</span><span class="sxs-lookup"><span data-stu-id="1c67b-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="1c67b-155">I když očekáváte, `expected` že `actual` hodnoty a jsou stejné, počáteční kontrolní výraz s `Assert.NotEqual` touto kontrolou určí, že tyto hodnoty nejsou *stejné*.</span><span class="sxs-lookup"><span data-stu-id="1c67b-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="1c67b-156">Před prvním vytvořením testu, který se nezdařil, je zkontrolovat logiku testu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="1c67b-157">Po potvrzení, že se test nezdařil, upravte kontrolní výraz, aby bylo možné test předat.</span><span class="sxs-lookup"><span data-stu-id="1c67b-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="1c67b-158">Následuje ukázka kompletní struktury projektu:</span><span class="sxs-lookup"><span data-stu-id="1c67b-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="1c67b-159">Začněte v adresáři *test/NewTypesTests* .</span><span class="sxs-lookup"><span data-stu-id="1c67b-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="1c67b-160">Obnovte testovací projekt pomocí [`dotnet restore`](../tools/dotnet-restore.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="1c67b-161">Spusťte testy pomocí [`dotnet test`](../tools/dotnet-test.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="1c67b-162">Tento příkaz spustí Test Runner zadaný v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="1c67b-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1c67b-163">Jak bylo očekáváno, testování se nezdařilo a konzola zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1c67b-163">As expected, testing fails, and the console displays the following output:</span></span>

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

<span data-ttu-id="1c67b-164">Změňte kontrolní výrazy testů z `Assert.NotEqual` na `Assert.Equal` :</span><span class="sxs-lookup"><span data-stu-id="1c67b-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="1c67b-165">Znovu spusťte testy pomocí `dotnet test` příkazu a získejte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1c67b-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="1c67b-166">Testy proběhly úspěšně.</span><span class="sxs-lookup"><span data-stu-id="1c67b-166">Testing passes.</span></span> <span data-ttu-id="1c67b-167">Metody typu PET vrací správné hodnoty při komunikaci s vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="1c67b-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="1c67b-168">Naučili jste se techniky pro organizování a testování projektů pomocí xUnit.</span><span class="sxs-lookup"><span data-stu-id="1c67b-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="1c67b-169">Pokud je chcete použít ve svých vlastních projektech, přečtěte si tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="1c67b-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="1c67b-170">*Šťastné kódování!*</span><span class="sxs-lookup"><span data-stu-id="1c67b-170">*Happy coding!*</span></span>
