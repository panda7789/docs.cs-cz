---
title: Začínáme s .NET Core v macOS
description: Tento dokument obsahuje kroky a pracovní postup k vytvoření řešení .NET Core používat Visual Studio Code.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e5ac6fa04a2a5001146936de56acafeec7dd895d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647006"
---
# <a name="get-started-with-net-core-on-macos"></a><span data-ttu-id="ebb2b-103">Začínáme s .NET Core v macOS</span><span class="sxs-lookup"><span data-stu-id="ebb2b-103">Get started with .NET Core on macOS</span></span>

<span data-ttu-id="ebb2b-104">Tento dokument obsahuje kroky a pracovní postup pro vytvoření řešení .NET Core pro macOS.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="ebb2b-105">Zjistěte, jak vytvářet projekty testování částí, použijte ladicí nástroje a začlenit knihovny třetích stran přes [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="ebb2b-106">Tento článek používá [Visual Studio Code](https://code.visualstudio.com) v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ebb2b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebb2b-107">Prerequisites</span></span>

<span data-ttu-id="ebb2b-108">Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="ebb2b-109">.NET Core SDK obsahuje nejnovější verzi rozhraní .NET Core framework a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="ebb2b-110">Nainstalujte [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="ebb2b-111">V průběhu tohoto článku můžete také nainstalovat rozšíření, které zlepšují .NET Core. vývojové prostředí Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="ebb2b-112">Instalace rozšíření Visual Studio kódu C# otevřete Visual Studio Code a stisknutím klávesy <kbd>F1</kbd> otevřete paletu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="ebb2b-113">Typ **ext, přípona instalace** zobrazíte seznam přípon.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="ebb2b-114">Vyberte rozšíření jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-114">Select the C# extension.</span></span> <span data-ttu-id="ebb2b-115">Restartujte Visual Studio Code k aktivaci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="ebb2b-116">Další informace najdete v tématu [dokumentaci kódu C# rozšíření sady Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="ebb2b-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="ebb2b-117">Get started</span></span>

<span data-ttu-id="ebb2b-118">V tomto kurzu vytvoříte tři projekty: projekt knihovny testů pro daný projekt knihovny a konzolové aplikace, která používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="ebb2b-119">Je možné [zobrazení nebo stažení zdroj](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) pro toto téma v úložišti dotnet/samples na Githubu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="ebb2b-120">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ebb2b-121">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-121">Start Visual Studio Code.</span></span> <span data-ttu-id="ebb2b-122">Stisknutím klávesy <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak třemi nebo prvními) nebo vyberte **zobrazení > integrovaný terminál** v nabídce otevřít vložený Terminál ve Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="ebb2b-123">Externí prostředí stále můžete otevřít pomocí Průzkumníka **otevřete příkazový řádek** příkazu (**spusťte v terminálu** v systému Mac nebo Linux) Pokud chcete raději pracovat mimo Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="ebb2b-124">Začněte vytvořením souboru řešení, která slouží jako kontejner pro jeden nebo více projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="ebb2b-125">V terminálu vytvořte *zlaté* složky a otevřete složku.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="ebb2b-126">Tato složka je kořenový adresář řešení.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-126">This folder is the root of your solution.</span></span> <span data-ttu-id="ebb2b-127">Spustit [ `dotnet new` ](../tools/dotnet-new.md) příkaz pro vytvoření nového řešení *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="ebb2b-128">Z *zlaté* složky, spusťte následující příkaz pro vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, v *knihovny* složky:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="ebb2b-129">Spustit [ `dotnet sln` ](../tools/dotnet-sln.md) příkaz pro přidání nově vytvořené *library.csproj* projektu do řešení:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="ebb2b-130">*Library.csproj* soubor obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ebb2b-131">Naše knihovna metody serializaci a deserializaci objektů ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="ebb2b-132">Pro podporu JSON serializace a deserializace, přidejte odkaz na `Newtonsoft.Json` balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="ebb2b-133">`dotnet add` Příkaz přidá nové položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="ebb2b-134">Chcete-li přidat odkaz na balíček NuGet, použijte [ `dotnet add package` ](../tools/dotnet-add-package.md) příkaz a zadejte název balíčku:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="ebb2b-135">Tento postup přidá `Newtonsoft.Json` a jeho závislosti do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="ebb2b-136">Případně ručně upravit *library.csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="ebb2b-137">Spustit [ `dotnet restore` ](../tools/dotnet-restore.md), ([viz Poznámka](#dotnet-restore-note)) která obnoví závislosti a vytvoří *obj* složky uvnitř *knihovny* s třemi soubory, včetně *project.assets.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="ebb2b-138">V *knihovny* složka, soubor přejmenujte *Class1.cs* k *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="ebb2b-139">Nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-139">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="ebb2b-140">`Thing` Třída obsahuje jednu veřejnou metodu `Get`, která vrací součet dvou čísel ale dosahuje tím, že součet převodu na řetězec a deserializovat ho do celé číslo.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="ebb2b-141">Toto využívá celou řadou moderní funkce C#, jako například [ `using static` direktivy](../../csharp/language-reference/keywords/using-static.md), [členové tvoření](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), a [interpolace](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="ebb2b-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="ebb2b-142">Vytvoření knihovny pomocí [ `dotnet build` ](../tools/dotnet-build.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="ebb2b-143">Tímto se vytvoří *library.dll* soubor *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="ebb2b-144">Vytvořte projekt testu</span><span class="sxs-lookup"><span data-stu-id="ebb2b-144">Create the test project</span></span>

<span data-ttu-id="ebb2b-145">Vytvoření testovacího projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-145">Build a test project for the library.</span></span> <span data-ttu-id="ebb2b-146">Z *zlaté* složku, vytvořte nový projekt testu:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="ebb2b-147">Přidejte projekt testu k řešení:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="ebb2b-148">Přidáte odkaz na projekt knihovna, kterou jste vytvořili v předchozí části tak, aby kompilátor můžete najít a používat projekt knihovny.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="ebb2b-149">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="ebb2b-150">Případně ručně upravit *testovací library.csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="ebb2b-151">Teď, když závislosti byla správně nakonfigurovaná, vytvořte testy pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="ebb2b-152">Otevřít *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="ebb2b-153">Mějte na paměti, vyhodnocení, hodnota 42 není roven 19 + 23 (nebo 42) při prvním vytvoření testu jednotek (`Assert.NotEqual`), který se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="ebb2b-154">Důležitým krokem při vytváření testů jednotek je pro vytvoření testu po prvním selhání potvrďte svou logikou.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="ebb2b-155">Z *zlaté* složky, spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="ebb2b-156">Tyto příkazy se rekurzivně hledat všechny projekty k obnovení závislostí, je vytvořit a aktivovat xUnit test runner pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="ebb2b-157">Jeden test selže, tak, jak očekáváte.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="ebb2b-158">Upravit *UnitTest1.cs* soubor a změňte kontrolního výrazu z `Assert.NotEqual` k `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="ebb2b-159">Spusťte následující příkaz z *zlaté* složku, kterou chcete znovu spustit test, které vyhovují této doby:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="ebb2b-160">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="ebb2b-160">Create the console app</span></span>

<span data-ttu-id="ebb2b-161">Konzolovou aplikaci, které vytvoříte prostřednictvím následujících kroků je závislá na projekt knihovny vytvořené dříve a volá metodu jeho knihovna při spuštění.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="ebb2b-162">Použití tohoto modelu vývoje, můžete zjistit, jak vytvářet opakovaně použitelné knihovny pro více projektů.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="ebb2b-163">Vytvořte novou konzolovou aplikaci z *zlaté* složky:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="ebb2b-164">Přidáte do řešení projekt konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="ebb2b-165">Vytvořte závislosti na knihovně spuštěním `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="ebb2b-166">Spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) Chcete-li obnovit závislosti tří projektů v řešení.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="ebb2b-167">Otevřít *Program.cs* a nahraďte obsah `Main` metoda tento řádek:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="ebb2b-168">Přidejte dva `using` direktivy k hornímu okraji *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="ebb2b-169">Spuštěním následujících `dotnet run` příkaz ke spuštění spustitelného souboru, kde `-p` umožňuje `dotnet run` určuje projekt, pro hlavní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="ebb2b-170">Aplikace vytvoří řetězec "odpověď je 42".</span><span class="sxs-lookup"><span data-stu-id="ebb2b-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="ebb2b-171">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="ebb2b-171">Debug the application</span></span>

<span data-ttu-id="ebb2b-172">Nastavit zarážku na `WriteLine` příkaz v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="ebb2b-173">To udělat buď stisknutím <kbd>F9</kbd> klávesy, když se ukazatel myši nachází `WriteLine` řádek nebo kliknutím myši na levý okraj řádku, ve které chcete nastavit zarážku.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="ebb2b-174">Na okraji vedle řádku kódu se zobrazí červený kruh.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="ebb2b-175">Při dosažení zarážky zastaví provádění kódu *před* provedením řádku zarážku.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="ebb2b-176">Výběrem ikony ladění na panelu nástrojů Visual Studio Code otevřete kartu ladicí program výběrem **zobrazení > ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="ebb2b-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Ladicí program sady Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="ebb2b-178">Kliknutím na tlačítko Přehrát a spusťte tak aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="ebb2b-179">Aplikace zahájí vykonávání a běží na zarážku, kde se zastaví.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="ebb2b-180">Krokovat s vnořením `Get` metoda a ujistěte se, že jste předali v správné argumenty.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="ebb2b-181">Potvrďte, že odpověď je 42.</span><span class="sxs-lookup"><span data-stu-id="ebb2b-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]