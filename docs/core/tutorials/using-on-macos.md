---
title: 'Kurz: Vytvoření řešení .NET Core v macOS pomocí Visual Studio Code'
description: Tento dokument popisuje kroky a pracovní postup pro vytvoření řešení .NET Core pomocí Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 022afd99c6d36d7a60ac40f3f27ba073c5470bd2
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082814"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="48d3f-103">Kurz: Vytvoření řešení .NET Core v macOS pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="48d3f-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="48d3f-104">Tento dokument popisuje kroky a pracovní postup pro vytvoření řešení .NET Core pro macOS.</span><span class="sxs-lookup"><span data-stu-id="48d3f-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="48d3f-105">Naučte se vytvářet projekty, testy jednotek, používat ladicí nástroje a začlenit knihovny třetích stran přes [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="48d3f-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="48d3f-106">Tento článek používá [Visual Studio Code](https://code.visualstudio.com) v MacOS.</span><span class="sxs-lookup"><span data-stu-id="48d3f-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48d3f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48d3f-107">Prerequisites</span></span>

<span data-ttu-id="48d3f-108">Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="48d3f-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="48d3f-109">.NET Core SDK zahrnuje nejnovější verzi rozhraní .NET Core Framework a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="48d3f-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="48d3f-110">Nainstalujte [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="48d3f-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="48d3f-111">V průběhu tohoto článku nainstalujete také rozšíření Visual Studio Code, která zlepšují vývojové prostředí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48d3f-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="48d3f-112">Visual Studio Code C# rozšíření můžete nainstalovat otevřením Visual Studio Code a stisknutím <kbd>klávesy F1</kbd> otevřete paletu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="48d3f-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="48d3f-113">Zadáním **EXT Install** zobrazíte seznam rozšíření.</span><span class="sxs-lookup"><span data-stu-id="48d3f-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="48d3f-114">Vyberte C# rozšíření.</span><span class="sxs-lookup"><span data-stu-id="48d3f-114">Select the C# extension.</span></span> <span data-ttu-id="48d3f-115">Pro aktivaci rozšíření restartujte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="48d3f-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="48d3f-116">Další informace najdete v dokumentaci k [rozšíření C# Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="48d3f-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="48d3f-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="48d3f-117">Get started</span></span>

<span data-ttu-id="48d3f-118">V tomto kurzu vytvoříte tři projekty: projekt knihovny, testy pro daný projekt knihovny a konzolovou aplikaci, která využívá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="48d3f-119">Zdroj pro toto téma můžete [Zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) v úložišti dotnet/Samples na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="48d3f-120">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="48d3f-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="48d3f-121">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="48d3f-121">Start Visual Studio Code.</span></span> <span data-ttu-id="48d3f-122">Stiskněte klávesu <kbd>CTRL</kbd> + <kbd>\`</kbd> (znaková uvozovka nebo znak zaškrtnutí) nebo vyberte **Zobrazit > integrovaného terminálu** z nabídky pro otevření vloženého terminálu v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="48d3f-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="48d3f-123">Můžete otevřít externí prostředí pomocí Průzkumníka **otevřít v příkazu příkazového řádku** (**otevřít v terminálu** na Macu nebo Linux), pokud dáváte přednost práci mimo Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="48d3f-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="48d3f-124">Začněte vytvořením souboru řešení, který slouží jako kontejner pro jeden nebo více projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48d3f-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="48d3f-125">V terminálu spusťte [`dotnet new`](../tools/dotnet-new.md) příkaz pro vytvoření nového řešení *zlatý. sln* uvnitř nové složky s názvem *zlatá*:</span><span class="sxs-lookup"><span data-stu-id="48d3f-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```console
dotnet new sln -o golden
```

<span data-ttu-id="48d3f-126">Přejděte do nové *zlaté* složky a spusťte následující příkaz pro vytvoření projektu knihovny, který ve složce *knihovny* vytvoří dva soubory,*Library. csproj* a *Class1.cs*:</span><span class="sxs-lookup"><span data-stu-id="48d3f-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="48d3f-127">Spusťte příkaz pro přidání nově vytvořeného projektu *Library. csproj* do řešení: [`dotnet sln`](../tools/dotnet-sln.md)</span><span class="sxs-lookup"><span data-stu-id="48d3f-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="48d3f-128">Soubor *Library. csproj* obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="48d3f-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="48d3f-129">Naše metody knihovny serializovat a deserializovat objekty ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="48d3f-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="48d3f-130">Pro podporu serializace a deserializace JSON přidejte odkaz na `Newtonsoft.Json` balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="48d3f-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="48d3f-131">`dotnet add` Příkaz přidá nové položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="48d3f-132">Chcete-li přidat odkaz na balíček NuGet, použijte [`dotnet add package`](../tools/dotnet-add-package.md) příkaz a zadejte název balíčku:</span><span class="sxs-lookup"><span data-stu-id="48d3f-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="48d3f-133">Tím se `Newtonsoft.Json` přidá a jeho závislosti do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="48d3f-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="48d3f-134">Případně ručně upravte soubor *Library. csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="48d3f-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="48d3f-135">Execute [`dotnet restore`](../tools/dotnet-restore.md)([Viz poznámku](#dotnet-restore-note)), která obnoví závislosti a vytvoří složku *obj* v *knihovně* se třemi soubory, včetně souboru *Project. assets. JSON* :</span><span class="sxs-lookup"><span data-stu-id="48d3f-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="48d3f-136">Ve složce *Library (knihovna* ), přejmenujte soubor *Class1.cs* na *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="48d3f-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="48d3f-137">Nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="48d3f-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="48d3f-138">Třída obsahuje jednu veřejnou `Get`metodu, která vrací součet dvou čísel, ale provede převod součtu na řetězec a jeho deserializaci na celé číslo. `Thing`</span><span class="sxs-lookup"><span data-stu-id="48d3f-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="48d3f-139">To C# využívá řadu moderních funkcí, [ `using static` ](../../csharp/language-reference/keywords/using-static.md)jako jsou například direktivy, [členy Expression-těle](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)a [interpolace řetězců](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="48d3f-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="48d3f-140">Sestavte knihovnu pomocí [`dotnet build`](../tools/dotnet-build.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="48d3f-141">Tím se vytvoří soubor *Library. dll* v rámci *zlaté/knihovny/přihrádky/ladění/netstandard 1.4*:</span><span class="sxs-lookup"><span data-stu-id="48d3f-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="48d3f-142">Vytvořte projekt testu</span><span class="sxs-lookup"><span data-stu-id="48d3f-142">Create the test project</span></span>

<span data-ttu-id="48d3f-143">Sestavte projekt testů pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-143">Build a test project for the library.</span></span> <span data-ttu-id="48d3f-144">Ze *zlaté* složky vytvořte nový testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="48d3f-144">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="48d3f-145">Přidejte testovací projekt do řešení:</span><span class="sxs-lookup"><span data-stu-id="48d3f-145">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="48d3f-146">Přidejte projekt odkaz na knihovnu, kterou jste vytvořili v předchozí části, aby kompilátor mohl najít a použít projekt knihovny.</span><span class="sxs-lookup"><span data-stu-id="48d3f-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="48d3f-147">[`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="48d3f-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="48d3f-148">Případně ručně upravte soubor *test-Library. csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="48d3f-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="48d3f-149">Teď, když jsou závislosti správně nakonfigurované, vytvořte testy pro vaši knihovnu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="48d3f-150">Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="48d3f-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="48d3f-151">Všimněte si, že hodnota 42 se nerovná 19 + 23 (nebo 42) při prvním vytvoření testu jednotek (`Assert.NotEqual`), což selže.</span><span class="sxs-lookup"><span data-stu-id="48d3f-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="48d3f-152">Důležitým krokem při sestavování testů jednotek je vytvoření testu pro jeho první selhání a potvrzení jeho logiky.</span><span class="sxs-lookup"><span data-stu-id="48d3f-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="48d3f-153">Ze *zlaté* složky spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="48d3f-153">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="48d3f-154">Tyto příkazy rekurzivně vyhledají všechny projekty pro obnovení závislostí, sestavují je a aktivují xUnit Test Runner pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="48d3f-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="48d3f-155">Jeden test se nezdařil, jak očekáváte.</span><span class="sxs-lookup"><span data-stu-id="48d3f-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="48d3f-156">Upravte soubor *UnitTest1.cs* a změňte kontrolní výraz z `Assert.NotEqual` na. `Assert.Equal`</span><span class="sxs-lookup"><span data-stu-id="48d3f-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="48d3f-157">Spusťte následující příkaz ze *zlaté* složky a spusťte test znovu, který projde tímto časem:</span><span class="sxs-lookup"><span data-stu-id="48d3f-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="48d3f-158">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="48d3f-158">Create the console app</span></span>

<span data-ttu-id="48d3f-159">Aplikace konzoly, kterou vytvoříte pomocí následujících kroků, provede závislost na projektu knihovny, který jste vytvořili dříve, a volá jeho metodu Library při spuštění.</span><span class="sxs-lookup"><span data-stu-id="48d3f-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="48d3f-160">Pomocí tohoto modelu vývoje vidíte, jak vytvořit opakovaně použitelné knihovny pro více projektů.</span><span class="sxs-lookup"><span data-stu-id="48d3f-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="48d3f-161">Vytvořit novou konzolovou aplikaci ze *zlaté* složky:</span><span class="sxs-lookup"><span data-stu-id="48d3f-161">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="48d3f-162">Přidejte projekt konzolové aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="48d3f-162">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="48d3f-163">Vytvořte závislost na knihovně spuštěním `dotnet add reference` příkazu:</span><span class="sxs-lookup"><span data-stu-id="48d3f-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="48d3f-164">Spusťte `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) a obnovte závislosti tří projektů v řešení.</span><span class="sxs-lookup"><span data-stu-id="48d3f-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="48d3f-165">Otevřete *program.cs* a nahraďte obsah `Main` metody následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="48d3f-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="48d3f-166">Do horní `using` části souboru *program.cs* přidejte dvě direktivy:</span><span class="sxs-lookup"><span data-stu-id="48d3f-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="48d3f-167">Spuštěním následujícího `dotnet run` příkazu spusťte spustitelný soubor, `-p` kde možnost `dotnet run` určuje projekt pro hlavní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="48d3f-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="48d3f-168">Aplikace vytvoří řetězec "odpověď je 42".</span><span class="sxs-lookup"><span data-stu-id="48d3f-168">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="48d3f-169">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="48d3f-169">Debug the application</span></span>

<span data-ttu-id="48d3f-170">Nastavte zarážku na `WriteLine` příkaz `Main` v metodě.</span><span class="sxs-lookup"><span data-stu-id="48d3f-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="48d3f-171">Provedete to tak, že stisknete klávesu <kbd>F9</kbd> , když se `WriteLine` ukazatel myši nachází na řádku, nebo kliknete myší na levém okraji na řádku, kde chcete nastavit zarážku.</span><span class="sxs-lookup"><span data-stu-id="48d3f-171">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="48d3f-172">Na okraji vedle řádku kódu se zobrazí červené kolečko.</span><span class="sxs-lookup"><span data-stu-id="48d3f-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="48d3f-173">Při dosažení zarážky se spuštění kódu zastaví *před* provedením řádku zarážky.</span><span class="sxs-lookup"><span data-stu-id="48d3f-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="48d3f-174">Otevřete kartu ladicí program výběrem ikony ladění na panelu nástrojů Visual Studio Code a výběrem možnosti **Zobrazit > ladění** na panelu nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="48d3f-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Ladicí program Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="48d3f-176">Stisknutím tlačítka Přehrát spusťte aplikaci v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="48d3f-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="48d3f-177">Aplikace se spustí a spustí se na zarážku, kde se zastaví.</span><span class="sxs-lookup"><span data-stu-id="48d3f-177">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="48d3f-178">Zajistěte `Get` krok do metody a ujistěte se, že jste předali správné argumenty.</span><span class="sxs-lookup"><span data-stu-id="48d3f-178">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="48d3f-179">Potvrďte, že odpověď je 42.</span><span class="sxs-lookup"><span data-stu-id="48d3f-179">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
