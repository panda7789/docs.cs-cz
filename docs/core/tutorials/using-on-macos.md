---
title: "Začínáme s .NET Core v systému macOS"
description: "Tento dokument obsahuje kroky a pracovní postup pro vytvoření základní řešení .NET pomocí Visual Studio Code."
keywords: "Rozhraní .NET, .NET core, Mac, systému macOS, Visual Studio Code"
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.workload: dotnetcore
ms.openlocfilehash: 5a8f1fca7623763d43b977d0cc44396de249c62e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="54e1f-104">Začínáme s .NET Core v systému macOS</span><span class="sxs-lookup"><span data-stu-id="54e1f-104">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="54e1f-105">Tento dokument obsahuje kroky a pracovní postup k vytvoření řešení pro systému macOS .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54e1f-105">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="54e1f-106">Naučte se vytvářet projekty, testy částí, použijte ladicí nástroje a začlenění knihoven jiných výrobců přes [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="54e1f-106">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="54e1f-107">Tento článek používá [Visual Studio Code](http://code.visualstudio.com) v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="54e1f-107">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54e1f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54e1f-108">Prerequisites</span></span>

<span data-ttu-id="54e1f-109">Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="54e1f-109">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="54e1f-110">.NET Core SDK zahrnuje nejnovější verze jádra rozhraní .NET framework a prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="54e1f-110">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="54e1f-111">Nainstalujte [Visual Studio Code](http://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="54e1f-111">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="54e1f-112">Během postupu v tomto článku můžete také nainstalovat rozšíření, které vylepšují vývoj .NET Core prostředí Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="54e1f-112">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="54e1f-113">Nainstalovat rozšíření pro Visual Studio kódu C# otevřete Visual Studio Code a stisknutím klávesy <kbd>F1</kbd> otevřete Visual Studio Code paletu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-113">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="54e1f-114">Typ **ext nainstalovat** zobrazíte seznam přípon.</span><span class="sxs-lookup"><span data-stu-id="54e1f-114">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="54e1f-115">Vyberte požadované rozšíření C#.</span><span class="sxs-lookup"><span data-stu-id="54e1f-115">Select the C# extension.</span></span> <span data-ttu-id="54e1f-116">Restartujte Visual Studio Code aktivovat rozšíření.</span><span class="sxs-lookup"><span data-stu-id="54e1f-116">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="54e1f-117">Další informace najdete v tématu [kódu jazyka C# rozšíření sady Visual Studio dokumentaci](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="54e1f-117">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="54e1f-118">Začínáme</span><span class="sxs-lookup"><span data-stu-id="54e1f-118">Getting started</span></span>

<span data-ttu-id="54e1f-119">V tomto kurzu vytvoříte tří projektů: projekt knihovny testů pro tento projekt knihovny a Konzolová aplikace, která používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-119">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="54e1f-120">Můžete [zobrazit nebo stáhnout zdrojovou](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) pro toto téma na dotnet/docs úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-120">You can [view or download the source](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) for this topic at the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="54e1f-121">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="54e1f-121">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="54e1f-122">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="54e1f-122">Start Visual Studio Code.</span></span> <span data-ttu-id="54e1f-123">Stiskněte klávesu <kbd>Ctrl</kbd> + <kbd> \\` </kbd> (znak třemi nebo backtick) nebo vyberte **zobrazení > integrované Terminálové** v nabídce otevřete embedded terminálu ve Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="54e1f-123">Press <kbd>Ctrl</kbd>+<kbd>\\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="54e1f-124">Externí prostředí stále můžete otevřít pomocí Průzkumníka **otevřete v příkazovém řádku** příkazu (**otevřete v terminálu** na Mac nebo Linux) Pokud dáváte přednost práci mimo Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="54e1f-124">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="54e1f-125">Začněte vytvořením řešení souboru, který slouží jako kontejner pro jeden nebo více projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54e1f-125">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="54e1f-126">V terminálu, vytvořte *zlaté* složky a otevřete složku.</span><span class="sxs-lookup"><span data-stu-id="54e1f-126">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="54e1f-127">Tato složka je kořenový adresář řešení.</span><span class="sxs-lookup"><span data-stu-id="54e1f-127">This folder is the root of your solution.</span></span> <span data-ttu-id="54e1f-128">Spustit [ `dotnet new` ](../tools/dotnet-new.md) příkazu vytvořte nové řešení *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="54e1f-128">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="54e1f-129">Z *zlaté* složky, spusťte následující příkaz k vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, v *knihovny* složky:</span><span class="sxs-lookup"><span data-stu-id="54e1f-129">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="54e1f-130">Spuštění [ `dotnet sln` ](../tools/dotnet-sln.md) příkaz pro přidání nově vytvořený *library.csproj* projektu a řešení:</span><span class="sxs-lookup"><span data-stu-id="54e1f-130">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="54e1f-131">*Library.csproj* soubor obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="54e1f-131">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="54e1f-132">Naše knihovna metody serializaci a deserializaci objektů ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="54e1f-132">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="54e1f-133">Pro podporu JSON serializace a deserializace, přidejte odkaz na `Newtonsoft.Json` balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="54e1f-133">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="54e1f-134">`dotnet add` Příkaz přidá nové položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-134">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="54e1f-135">Chcete-li přidat odkaz na balíček NuGet, použijte [ `dotnet add package` ](../tools/dotnet-add-package.md) příkaz a zadejte název balíčku:</span><span class="sxs-lookup"><span data-stu-id="54e1f-135">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="54e1f-136">Tento postup přidá `Newtonsoft.Json` a jeho závislé součásti na projekt knihovny.</span><span class="sxs-lookup"><span data-stu-id="54e1f-136">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="54e1f-137">Případně ručně upravit *library.csproj* souboru a přidejte následující uzly:</span><span class="sxs-lookup"><span data-stu-id="54e1f-137">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="54e1f-138">Spuštění [ `dotnet restore` ](../tools/dotnet-restore.md), ([viz Poznámka](#dotnet-restore-note)), který obnoví závislosti a vytvoří *obj* složky uvnitř *knihovny* s třemi soubory v, včetně *project.assets.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="54e1f-138">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="54e1f-139">V *knihovny* složku, přejmenujte soubor *Class1.cs* k *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="54e1f-139">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="54e1f-140">Nahraďte kód tímto:</span><span class="sxs-lookup"><span data-stu-id="54e1f-140">Replace the code with the following:</span></span>

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

<span data-ttu-id="54e1f-141">`Thing` Třída obsahuje jeden veřejná metoda `Get`, která vrací součet dvou čísla, ale součet převádění na řetězce a pak ho deserializaci do celé číslo.</span><span class="sxs-lookup"><span data-stu-id="54e1f-141">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="54e1f-142">Toto využívá celou řadu moderní C# funkcí, jako například [ `using static` direktivy](../../csharp/language-reference/keywords/using-static.md), [výraz vozidlo členy](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), a [interpolované řetězce](../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="54e1f-142">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [interpolated strings](../../csharp/language-reference/keywords/interpolated-strings.md).</span></span>

<span data-ttu-id="54e1f-143">Sestavení knihovny s [ `dotnet build` ](../tools/dotnet-build.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="54e1f-143">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="54e1f-144">Tímto se vytvoří *library.dll* souboru pod *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="54e1f-144">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="54e1f-145">Vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="54e1f-145">Create the test project</span></span>

<span data-ttu-id="54e1f-146">Vytvoření testovacího projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="54e1f-146">Build a test project for the library.</span></span> <span data-ttu-id="54e1f-147">Z *zlaté* složky, vytvořte nový projekt testu:</span><span class="sxs-lookup"><span data-stu-id="54e1f-147">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="54e1f-148">Do řešení přidáte k testovacímu projektu:</span><span class="sxs-lookup"><span data-stu-id="54e1f-148">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="54e1f-149">Přidáte odkaz na projekt knihovna, kterou jste vytvořili v předchozí části, aby kompilátor můžete najít a použití projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="54e1f-149">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="54e1f-150">Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="54e1f-150">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="54e1f-151">Případně ručně upravit *test library.csproj* souboru a přidejte následující uzlu:</span><span class="sxs-lookup"><span data-stu-id="54e1f-151">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="54e1f-152">Teď, když jsou správně nakonfigurovány závislosti vytváření testů pro své knihovny.</span><span class="sxs-lookup"><span data-stu-id="54e1f-152">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="54e1f-153">Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="54e1f-153">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="54e1f-154">Všimněte si assert hodnota 42 není rovno 19 + 23 (nebo 42) při prvním vytvoření testování částí (`Assert.NotEqual`), který se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="54e1f-154">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="54e1f-155">Důležitým krokem při vytváření testů jednotek je vytvoření testu, aby v případě selhání jednou nejprve potvrdit svou logikou.</span><span class="sxs-lookup"><span data-stu-id="54e1f-155">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="54e1f-156">Z *zlaté* složky, spuštěním následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="54e1f-156">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="54e1f-157">Tyto příkazy bude rekurzivní hledání, že všechny projekty k obnovení závislosti, je sestavení a aktivaci xUnit test runner ke spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="54e1f-157">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="54e1f-158">Jeden test se nezdaří, podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="54e1f-158">The single test fails, as you expect.</span></span>

<span data-ttu-id="54e1f-159">Upravit *UnitTest1.cs* soubor a změňte assertion z `Assert.NotEqual` k `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="54e1f-159">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="54e1f-160">Spusťte následující příkaz z *zlaté* složku, kterou chcete znovu spustit test, který předává této doby:</span><span class="sxs-lookup"><span data-stu-id="54e1f-160">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="54e1f-161">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="54e1f-161">Create the console app</span></span>

<span data-ttu-id="54e1f-162">Konzolové aplikace, které vytvoříte prostřednictvím následujících kroků má závislost na projekt knihovny jste dříve vytvořili a volá metodu jeho knihovny, když je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="54e1f-162">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="54e1f-163">Pomocí tohoto vzoru vývoj, můžete zjistit, jak vytvořit opakovaně použitelné knihovny pro více projektů.</span><span class="sxs-lookup"><span data-stu-id="54e1f-163">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="54e1f-164">Vytvořte novou konzolovou aplikaci z *zlaté* složky:</span><span class="sxs-lookup"><span data-stu-id="54e1f-164">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="54e1f-165">Do řešení přidáte projekt konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="54e1f-165">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="54e1f-166">Vytvoření závislosti na knihovně spuštěním `dotnet add reference` příkaz:</span><span class="sxs-lookup"><span data-stu-id="54e1f-166">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="54e1f-167">Spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) Chcete-li obnovit závislosti tři projekty v řešení.</span><span class="sxs-lookup"><span data-stu-id="54e1f-167">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="54e1f-168">Otevřete *Program.cs* a nahraďte obsah `Main` metoda tento řádek:</span><span class="sxs-lookup"><span data-stu-id="54e1f-168">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="54e1f-169">Přidejte dva `using` direktivy do horní části *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="54e1f-169">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="54e1f-170">Spuštěním následujících `dotnet run` příkaz ke spuštění spustitelného souboru, kde `-p` možnost k `dotnet run` určuje projekt, který pro hlavní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="54e1f-170">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="54e1f-171">Aplikace vytvoří řetězec "odpověď je 42".</span><span class="sxs-lookup"><span data-stu-id="54e1f-171">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="54e1f-172">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="54e1f-172">Debug the application</span></span>

<span data-ttu-id="54e1f-173">Nastavte zarážky v `WriteLine` příkaz v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="54e1f-173">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="54e1f-174">To provedete buď stiskněte <kbd>F9</kbd> klíče, pokud se ukazatel myši `WriteLine` řádku nebo pomocí myši na levém okraji na řádek, na kterém chcete nastavit bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="54e1f-174">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="54e1f-175">Červené kolečko se zobrazí u okraje řádku řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-175">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="54e1f-176">Když je dosaženo zarážkou, provádění kódu zastaví *před* řádek zarážek spustí.</span><span class="sxs-lookup"><span data-stu-id="54e1f-176">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="54e1f-177">Otevřete kartu ladicí program výběrem ikony ladění na panelu nástrojů Visual Studio Code výběr **zobrazení > ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd> + <kbd> POSUNUTÍ</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="54e1f-177">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Ladicí program Visual Studio Code](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="54e1f-179">Kliknutím na tlačítko Přehrát a spusťte aplikaci v části ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="54e1f-179">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="54e1f-180">Aplikace zahájí spuštění a běží na zarážku, kde se zastaví.</span><span class="sxs-lookup"><span data-stu-id="54e1f-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="54e1f-181">Krokovat s vnořením `Get` metoda a ujistěte se, že předané ve správné argumenty.</span><span class="sxs-lookup"><span data-stu-id="54e1f-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="54e1f-182">Potvrďte, že odpověď 42.</span><span class="sxs-lookup"><span data-stu-id="54e1f-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]