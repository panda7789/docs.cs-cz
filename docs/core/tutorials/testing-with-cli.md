---
title: "Uspořádání a testování projektů pomocí příkazového řádku .NET Core"
description: "Tento kurz vysvětluje, jak uspořádat a testování .NET Core projekty z příkazového řádku."
keywords: "Testování, .NET Core CLI, xUnit .NET, .NET core jednotky"
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
ms.openlocfilehash: 62c81bf070a435f6105c313ae95340a5504233df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="b8b49-104">Uspořádání a testování projektů pomocí příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="b8b49-104">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="b8b49-105">V tomto kurzu následuje [Začínáme s .NET Core v systému Windows nebo Linux/macOS pomocí příkazového řádku](using-with-xplat-cli.md), přesměrujeme vás nad rámec vytvoření jednoduché konzolové aplikace pro vývoj aplikací pokročilé a dobře uspořádány.</span><span class="sxs-lookup"><span data-stu-id="b8b49-105">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="b8b49-106">Po ukazuje, jak používat složky organizace kódu, tento kurz ukazuje, jak rozšířit konzolovou aplikaci pomocí [xUnit](https://xunit.github.io/) testování framework.</span><span class="sxs-lookup"><span data-stu-id="b8b49-106">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="b8b49-107">Použití složek k uspořádání kódu</span><span class="sxs-lookup"><span data-stu-id="b8b49-107">Using folders to organize code</span></span>

<span data-ttu-id="b8b49-108">Pokud chcete zavést nové typy do konzoly aplikace, můžete tak učinit přidáním soubory obsahující typy, které mají aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8b49-108">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="b8b49-109">Například pokud přidáte soubory obsahující `AccountInformation` a `MonthlyReportRecords` typy do projektu strukturu souborů projektu je plochý a usnadňují přejděte:</span><span class="sxs-lookup"><span data-stu-id="b8b49-109">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="b8b49-110">Však to jenom funguje i při velikost vašeho projektu je poměrně malý.</span><span class="sxs-lookup"><span data-stu-id="b8b49-110">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="b8b49-111">Můžete si, co se stane Pokud přidáte do projektu 20 typy?</span><span class="sxs-lookup"><span data-stu-id="b8b49-111">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="b8b49-112">Projekt výborný nebude snadno přejděte a udržovat s třídou mnoho soubory littering kořenového adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-112">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="b8b49-113">K uspořádání projektu, vytvořte novou složku a pojmenujte ji *modely* pro soubory typu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-113">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="b8b49-114">Pro soubory typu do *modely* složky:</span><span class="sxs-lookup"><span data-stu-id="b8b49-114">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="b8b49-115">Projekty, které logicky skupiny souborů do složek, které se dají snadno přejděte a údržbu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-115">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="b8b49-116">V další části je vytvořit složitější ukázku se složkami a testování částí.</span><span class="sxs-lookup"><span data-stu-id="b8b49-116">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="b8b49-117">Uspořádání a testování pomocí ukázkových mazlíčků NewTypes</span><span class="sxs-lookup"><span data-stu-id="b8b49-117">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="b8b49-118">Vytváření vzorku</span><span class="sxs-lookup"><span data-stu-id="b8b49-118">Building the sample</span></span>

<span data-ttu-id="b8b49-119">Následující postup, můžete buď absolvovat pomocí [NewTypes mazlíčků ukázkové](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="b8b49-119">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="b8b49-120">Typy jsou logicky uspořádány do strukturu složek, která umožňuje přidání další typy později a testy jsou také logicky umístit do složky umožňující přidání další testy později.</span><span class="sxs-lookup"><span data-stu-id="b8b49-120">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="b8b49-121">Ukázka obsahuje dva typy `Dog` a `Cat`a je implementovat společné rozhraní a má `IPet`.</span><span class="sxs-lookup"><span data-stu-id="b8b49-121">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="b8b49-122">Pro `NewTypes` projektu vaším cílem je uspořádat typy související s pet do *mazlíčků* složky.</span><span class="sxs-lookup"><span data-stu-id="b8b49-122">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="b8b49-123">Pokud později, přidáte další sadu typy *WildAnimals* například se umístit do *NewTypes* složky spolu s *mazlíčků* složky.</span><span class="sxs-lookup"><span data-stu-id="b8b49-123">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="b8b49-124">*WildAnimals* složka může obsahovat typy pro zvířat, které nejsou mazlíčků, jako například `Squirrel` a `Rabbit` typy.</span><span class="sxs-lookup"><span data-stu-id="b8b49-124">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="b8b49-125">Tímto způsobem jako typy jsou přidány, projekt zůstává i uspořádány.</span><span class="sxs-lookup"><span data-stu-id="b8b49-125">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="b8b49-126">Vytvořte následující strukturu složek s uvedené obsah souboru:</span><span class="sxs-lookup"><span data-stu-id="b8b49-126">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="b8b49-127">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-127">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="b8b49-128">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-128">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="b8b49-129">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-129">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="b8b49-130">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-130">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="b8b49-131">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-131">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="b8b49-132">Spuštěním následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="b8b49-132">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="b8b49-133">Získejte následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b8b49-133">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="b8b49-134">Volitelné cvičení: můžete přidat nové domácí typu, například `Bird`, tím, že rozšíří tento projekt.</span><span class="sxs-lookup"><span data-stu-id="b8b49-134">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="b8b49-135">Ujistěte se, ptačí perspektivy na `TalkToOwner` metoda udělení `Tweet!` vlastníkovi.</span><span class="sxs-lookup"><span data-stu-id="b8b49-135">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="b8b49-136">Spusťte aplikaci znovu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-136">Run the app again.</span></span> <span data-ttu-id="b8b49-137">Výstup bude obsahovat`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="b8b49-137">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="b8b49-138">Testování vzorku</span><span class="sxs-lookup"><span data-stu-id="b8b49-138">Testing the sample</span></span>

<span data-ttu-id="b8b49-139">`NewTypes` Projektu je na místě a uspořádán udržováním typy související s mazlíčků ve složce.</span><span class="sxs-lookup"><span data-stu-id="b8b49-139">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="b8b49-140">V dalším kroku vytvořte projekt testu a zahájit zápis testování pomocí [xUnit](https://xunit.github.io/) test framework.</span><span class="sxs-lookup"><span data-stu-id="b8b49-140">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="b8b49-141">Testování částí umožňuje automaticky zkontrolujte bevahior vaše domácí typů potvrďte, že jste operační správně.</span><span class="sxs-lookup"><span data-stu-id="b8b49-141">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="b8b49-142">Vytvoření *testování* složku s *NewTypesTests* v její složce.</span><span class="sxs-lookup"><span data-stu-id="b8b49-142">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="b8b49-143">Na příkazovém řádku z *NewTypesTests* složky, provést `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="b8b49-143">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="b8b49-144">Tímto se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="b8b49-144">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="b8b49-145">K testovacímu projektu nemůže otestovat aktuálně typy v `NewTypes` a vyžaduje odkaz na projekt `NewTypes` projektu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-145">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="b8b49-146">Chcete-li přidat odkaz na projekt, použijte [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="b8b49-146">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="b8b49-147">Máte také možnost ručně přidejte odkaz na projekt tak, že přidáte `<ItemGroup>` uzlu *NewTypesTests.csproj* souboru:</span><span class="sxs-lookup"><span data-stu-id="b8b49-147">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="b8b49-148">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="b8b49-148">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="b8b49-149">*NewTypesTests.csproj* soubor obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="b8b49-149">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="b8b49-150">Odkaz na balíček `Microsoft.NET.Test.Sdk`, .NET testování infrastruktury</span><span class="sxs-lookup"><span data-stu-id="b8b49-150">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="b8b49-151">Odkaz na balíček `xunit`, xUnit testování framework</span><span class="sxs-lookup"><span data-stu-id="b8b49-151">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="b8b49-152">Odkaz na balíček `xunit.runner.visualstudio`, nástroj test runner</span><span class="sxs-lookup"><span data-stu-id="b8b49-152">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="b8b49-153">Odkaz na projekt `NewTypes`, kód pro testování</span><span class="sxs-lookup"><span data-stu-id="b8b49-153">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="b8b49-154">Změna názvu *UnitTest1.cs* k *PetTests.cs* a nahraďte kód v souboru následující:</span><span class="sxs-lookup"><span data-stu-id="b8b49-154">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="b8b49-155">Volitelné cvičení: Pokud jste přidali `Bird` dříve typ, který poskytne `Tweet!` vlastníkovi, přidejte metodu testu do *PetTests.cs* souboru, `BirdTalkToOwnerReturnsTweet`, zkontroluje, jestli `TalkToOwner` metoda funguje správně pro `Bird` typu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-155">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="b8b49-156">I když můžete očekávat, který `expected` a `actual` jsou hodnoty stejné, počáteční kontrolní výrazy s `Assert.NotEqual` kontroly určit, že jsou *nerovná*.</span><span class="sxs-lookup"><span data-stu-id="b8b49-156">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="b8b49-157">Vždy nejprve vytvořte testy selhání jednou pro ověření logiku testů.</span><span class="sxs-lookup"><span data-stu-id="b8b49-157">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="b8b49-158">Toto je důležitým krokem při metodika návrhu řízeného testováním (TDD).</span><span class="sxs-lookup"><span data-stu-id="b8b49-158">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="b8b49-159">Jakmile potvrdíte, že testy nezdaří, můžete upravit kontrolní výrazy a povolení jejich předávání.</span><span class="sxs-lookup"><span data-stu-id="b8b49-159">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="b8b49-160">Na obrázku je dokončený projekt strukturu:</span><span class="sxs-lookup"><span data-stu-id="b8b49-160">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="b8b49-161">Spusťte v *test/NewTypesTests* adresáře.</span><span class="sxs-lookup"><span data-stu-id="b8b49-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="b8b49-162">Obnovit k testovacímu projektu s [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="b8b49-162">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="b8b49-163">Spouštění testů pomocí [ `dotnet test` ](../tools/dotnet-test.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="b8b49-163">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="b8b49-164">Tento příkaz spustí nástroj test runner zadaný v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b8b49-164">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="b8b49-165">Podle očekávání, testování selže a konzole zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b8b49-165">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="b8b49-166">Změnit tvrzení testů z `Assert.NotEqual` k `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="b8b49-166">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="b8b49-167">Znovu spusťte testy s `dotnet test` příkazů a získat následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b8b49-167">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="b8b49-168">Testování předává.</span><span class="sxs-lookup"><span data-stu-id="b8b49-168">Testing passes.</span></span> <span data-ttu-id="b8b49-169">Domácí typy metody vrací správné hodnoty při posuzování vlastníkovi.</span><span class="sxs-lookup"><span data-stu-id="b8b49-169">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="b8b49-170">Když jste se naučili techniky k uspořádání a testování projektů pomocí xUnit.</span><span class="sxs-lookup"><span data-stu-id="b8b49-170">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="b8b49-171">Pokračovat v těchto postupů je použití ve vašich vlastních projektů.</span><span class="sxs-lookup"><span data-stu-id="b8b49-171">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="b8b49-172">*Kódování radostí!*</span><span class="sxs-lookup"><span data-stu-id="b8b49-172">*Happy coding!*</span></span>

