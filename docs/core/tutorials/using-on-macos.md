---
title: 'Kurz: Vytvoření řešení .NET Core v macOS pomocí kódu Visual Studia'
description: Tento dokument poskytuje kroky a pracovní postup k vytvoření .NET Core řešení pomocí kódu sady Visual Studio.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156592"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="49303-103">Kurz: Vytvoření řešení .NET Core v macOS pomocí kódu Visual Studia</span><span class="sxs-lookup"><span data-stu-id="49303-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="49303-104">Tento dokument obsahuje postup a pracovní postup k vytvoření řešení .NET Core pro macOS.</span><span class="sxs-lookup"><span data-stu-id="49303-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="49303-105">Naučte se vytvářet projekty, testování částí, používat ladicí nástroje a začlenit knihovny třetích stran prostřednictvím [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="49303-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="49303-106">Tento článek používá [Visual Studio Kód](https://code.visualstudio.com) na macOS.</span><span class="sxs-lookup"><span data-stu-id="49303-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49303-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49303-107">Prerequisites</span></span>

<span data-ttu-id="49303-108">Nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="49303-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="49303-109">Sada .NET Core SDK obsahuje nejnovější verzi rozhraní .NET Core framework a runtime.</span><span class="sxs-lookup"><span data-stu-id="49303-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="49303-110">Nainstalujte [kód sady Visual Studio](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="49303-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="49303-111">Během tohoto článku také nainstalovat rozšíření kódu sady Visual Studio, které zlepšují vývojové prostředí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49303-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="49303-112">Nainstalujte rozšíření Visual Studio Code C# otevřením kódu Sady Visual Studio a stisknutím <kbd>klávesy Fn</kbd>+<kbd>F1</kbd> otevřete paletu kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49303-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>Fn</kbd>+<kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="49303-113">Zadejte **ext install** zobrazíte seznam rozšíření.</span><span class="sxs-lookup"><span data-stu-id="49303-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="49303-114">Vyberte rozšíření C#.</span><span class="sxs-lookup"><span data-stu-id="49303-114">Select the C# extension.</span></span> <span data-ttu-id="49303-115">Restartujte visual studio kód pro aktivaci rozšíření.</span><span class="sxs-lookup"><span data-stu-id="49303-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="49303-116">Další informace naleznete v [dokumentaci k rozšíření aplikace Visual Studio Code C# Extension](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="49303-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="49303-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="49303-117">Get started</span></span>

<span data-ttu-id="49303-118">V tomto kurzu vytvoříte tři projekty: projekt knihovny, testy pro tento projekt knihovny a konzolovou aplikaci, která využívá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="49303-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="49303-119">Zdroj tohoto článku můžete [zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) v úložišti dotnet/samples na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="49303-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this article at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="49303-120">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="49303-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="49303-121">Spusťte kód sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49303-121">Start Visual Studio Code.</span></span> <span data-ttu-id="49303-122">Stisknutím <kbd>klávesy Ctrl</kbd> <kbd>\`</kbd> (znak backquote nebo backtick) nebo vyberte **zobrazit** > **terminál** z nabídky a otevřete vložený terminál v kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49303-122">Press <kbd>Ctrl</kbd><kbd>\`</kbd> (the backquote or backtick character) or select **View** > **Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="49303-123">Stále můžete otevřít externí prostředí s příkazem Otevřít explorer **v příkazovém řádku** **(Otevřít v terminálu** na macOS nebo Linux), pokud dáváte přednost práci mimo Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="49303-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on macOS or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="49303-124">Začněte vytvořením souboru řešení, který slouží jako kontejner pro jeden nebo více projektů .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49303-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="49303-125">V terminálu spusťte [`dotnet new`](../tools/dotnet-new.md) příkaz a vytvořte nové řešení *golden.sln* uvnitř nové složky s názvem *golden*:</span><span class="sxs-lookup"><span data-stu-id="49303-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="49303-126">Přejděte do nové *zlaté* složky a spusťte následující příkaz k vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, ve složce *knihovny:*</span><span class="sxs-lookup"><span data-stu-id="49303-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="49303-127">Spusťte [`dotnet sln`](../tools/dotnet-sln.md) příkaz a přidejte do řešení nově vytvořený projekt *library.csproj:*</span><span class="sxs-lookup"><span data-stu-id="49303-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="49303-128">Soubor *library.csproj* obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="49303-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="49303-129">Naše metody knihovny serializují a rekonstruují objekty ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="49303-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="49303-130">Chcete-li podporovat serializaci a deserializaci JSON, přidejte odkaz na balíček `Newtonsoft.Json` NuGet.</span><span class="sxs-lookup"><span data-stu-id="49303-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="49303-131">Příkaz `dotnet add` přidá do projektu nové položky.</span><span class="sxs-lookup"><span data-stu-id="49303-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="49303-132">Chcete-li přidat odkaz na balíček [`dotnet add package`](../tools/dotnet-add-package.md) NuGet, použijte příkaz a zadejte název balíčku:</span><span class="sxs-lookup"><span data-stu-id="49303-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="49303-133">To `Newtonsoft.Json` přidá a jeho závislosti do projektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="49303-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="49303-134">Případně ručně upravte soubor *library.csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="49303-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="49303-135">Spustit [`dotnet restore`](../tools/dotnet-restore.md), ([viz poznámka),](#dotnet-restore-note)která obnoví závislosti a vytvoří složku *obj* uvnitř *knihovny* se třemi soubory, včetně souboru *project.assets.json:*</span><span class="sxs-lookup"><span data-stu-id="49303-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="49303-136">Ve složce *knihovny* přejmenujte *Class1.cs* souborů na *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="49303-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="49303-137">Nahraďte kód následujícím:</span><span class="sxs-lookup"><span data-stu-id="49303-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="49303-138">Třída `Thing` obsahuje jednu `Get`veřejnou metodu , která vrací součet dvou čísel, ale činí tak převedením součtu na řetězec a následným deserializací na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="49303-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="49303-139">To využívá řadu moderních funkcí jazyka C#, jako [ `using static` jsou direktivy](../../csharp/language-reference/keywords/using-static.md), [členy s výrazovým tělem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)a [interpolace řetězců](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="49303-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="49303-140">Vytvořte knihovnu [`dotnet build`](../tools/dotnet-build.md) pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="49303-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="49303-141">Tím se vytvoří soubor *library.dll* pod *položkou golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="49303-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="49303-142">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="49303-142">Create the test project</span></span>

<span data-ttu-id="49303-143">Vytvořte testovací projekt pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="49303-143">Build a test project for the library.</span></span> <span data-ttu-id="49303-144">Ze *zlaté* složky vytvořte nový testovací projekt:</span><span class="sxs-lookup"><span data-stu-id="49303-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="49303-145">Přidejte testovací projekt do řešení:</span><span class="sxs-lookup"><span data-stu-id="49303-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="49303-146">Přidejte odkaz na projekt knihovnu, kterou jste vytvořili v předchozí části, aby kompilátor mohl najít a použít projekt knihovny.</span><span class="sxs-lookup"><span data-stu-id="49303-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="49303-147">Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="49303-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="49303-148">Případně ručně upravte soubor *test-library.csproj* a přidejte následující uzel:</span><span class="sxs-lookup"><span data-stu-id="49303-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="49303-149">Nyní, když byly správně nakonfigurovány závislosti, vytvořte testy pro vaši knihovnu.</span><span class="sxs-lookup"><span data-stu-id="49303-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="49303-150">Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="49303-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="49303-151">Všimněte si, že tvrdíte, že hodnota 42 se nerovná 19 +23`Assert.NotEqual`(nebo 42) při prvním vytvoření testování částí ( ), které se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="49303-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="49303-152">Důležitým krokem při vytváření testů částí je vytvořit test nezdaří jednou první potvrdit jeho logiku.</span><span class="sxs-lookup"><span data-stu-id="49303-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="49303-153">Ze *zlaté* složky proveďte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="49303-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="49303-154">Tyto příkazy budou rekurzivně najít všechny projekty obnovit závislosti, jejich sestavení a aktivovat xUnit test runner spustit testy.</span><span class="sxs-lookup"><span data-stu-id="49303-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="49303-155">Jeden test se nezdaří, jak očekáváte.</span><span class="sxs-lookup"><span data-stu-id="49303-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="49303-156">Upravte soubor *UnitTest1.cs* a `Assert.NotEqual` změňte kontrolní výraz z na `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="49303-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="49303-157">Proveďte následující příkaz ze *zlaté* složky a znovu spusťte test, který tentokrát projde:</span><span class="sxs-lookup"><span data-stu-id="49303-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="49303-158">Vytvoření konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="49303-158">Create the console app</span></span>

<span data-ttu-id="49303-159">Konzolová aplikace, kterou vytvoříte v následujících krocích, bude závislá na projektu knihovny, který jste vytvořili dříve, a při spuštění zavolá metodu knihovny.</span><span class="sxs-lookup"><span data-stu-id="49303-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="49303-160">Pomocí tohoto vzoru vývoje uvidíte, jak vytvořit opakovaně použitelné knihovny pro více projektů.</span><span class="sxs-lookup"><span data-stu-id="49303-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="49303-161">Vytvořte novou konzolovou aplikaci ze *zlaté* složky:</span><span class="sxs-lookup"><span data-stu-id="49303-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="49303-162">Přidejte projekt konzolové aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="49303-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="49303-163">Vytvořte závislost na knihovně `dotnet add reference` spuštěním příkazu:</span><span class="sxs-lookup"><span data-stu-id="49303-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="49303-164">Spustit `dotnet restore` ([viz poznámka)](#dotnet-restore-note)obnovit závislosti tří projektů v řešení.</span><span class="sxs-lookup"><span data-stu-id="49303-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="49303-165">Otevřete *Program.cs* a nahraďte obsah `Main` metody následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="49303-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="49303-166">Do `using` horní části *Program.cs* souboru přidejte dvě direktivy:</span><span class="sxs-lookup"><span data-stu-id="49303-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="49303-167">Proveďte `dotnet run` následující příkaz pro spuštění spustitelného souboru, `-p` kde možnost `dotnet run` určuje projekt pro hlavní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="49303-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="49303-168">Aplikace vytvoří řetězec "Odpověď je 42".</span><span class="sxs-lookup"><span data-stu-id="49303-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="49303-169">Ladění aplikace</span><span class="sxs-lookup"><span data-stu-id="49303-169">Debug the application</span></span>

<span data-ttu-id="49303-170">Nastavte zarážku `WriteLine` na `Main` příkaz v metodě.</span><span class="sxs-lookup"><span data-stu-id="49303-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="49303-171">To buď stisknutím klávesy <kbd>Fn</kbd>+<kbd>F9,</kbd> když `WriteLine` je kurzor nad čárou, nebo kliknutím myši na levém okraji na řádku, kde chcete nastavit zarážku.</span><span class="sxs-lookup"><span data-stu-id="49303-171">Do this by either pressing the <kbd>Fn</kbd>+<kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="49303-172">Červený kruh se zobrazí na okraji vedle řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="49303-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="49303-173">Po dosažení zarážky spuštění kódu se zastaví *před* spuštěním řádku zarážky.</span><span class="sxs-lookup"><span data-stu-id="49303-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="49303-174">Otevřete kartu ladicího programu tak, že vyberete ikonu Ladění na panelu nástrojů Kód sady Visual Studio, vyberete **možnost Zobrazit** > **ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="49303-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View** > **Debug** from the menu bar, or using the keyboard shortcut <kbd>&#8679;</kbd><kbd>&#8984;</kbd><kbd>D</kbd>:</span></span>

![Ladicí program kódu sady Visual Studio](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="49303-176">Stisknutím tlačítka Přehrát spusťte aplikaci pod ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="49303-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="49303-177">Vytvořili jste testovací projekt i aplikaci v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="49303-177">You've created both a test project and an application in this project.</span></span> <span data-ttu-id="49303-178">Ladicí program se zeptá, který projekt chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="49303-178">The debugger asks which project you want to start.</span></span> <span data-ttu-id="49303-179">Vyberte projekt "aplikace".</span><span class="sxs-lookup"><span data-stu-id="49303-179">Select the "app" project.</span></span> <span data-ttu-id="49303-180">Aplikace začne spouštění a spustí se na zarážku, kde se zastaví.</span><span class="sxs-lookup"><span data-stu-id="49303-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="49303-181">Krok do `Get` metody a ujistěte se, že jste prošli ve správných argumentech.</span><span class="sxs-lookup"><span data-stu-id="49303-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="49303-182">Potvrďte, že odpověď je 42.</span><span class="sxs-lookup"><span data-stu-id="49303-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
