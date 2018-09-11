---
title: Začínáme s C# a Visual Studio Code – průvodce v C#
description: Zjistěte, jak vytvářet a ladit vaši první aplikaci .NET Core v jazyce C# pomocí nástroje Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 321edcebdea141b7290fa57b47c8d9fc91d3521c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360671"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="349a8-103">Začínáme s C# a Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349a8-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="349a8-104">.NET core nabízí rychlou modulární platformu pro vytváření aplikací, které běží ve Windows, Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="349a8-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="349a8-105">Získání výkonné prostředí s plnou podporu pro C# IntelliSense (inteligentního dokončování kódu) pro úpravy a ladění pomocí Visual Studio Code s rozšířením C#.</span><span class="sxs-lookup"><span data-stu-id="349a8-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="349a8-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="349a8-106">Prerequisites</span></span>

1. <span data-ttu-id="349a8-107">Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="349a8-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="349a8-108">Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="349a8-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="349a8-109">Nainstalujte [rozšíření jazyka C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349a8-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="349a8-110">Další informace o tom, jak rozšíření nainstalovat Visual Studio Code najdete v tématu [VS Code příponou Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="349a8-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="349a8-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="349a8-111">Hello World</span></span>

<span data-ttu-id="349a8-112">Pusťme se do práce s jednoduchý program "Hello World" v rozhraní .NET Core:</span><span class="sxs-lookup"><span data-stu-id="349a8-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="349a8-113">Otevřete projekt:</span><span class="sxs-lookup"><span data-stu-id="349a8-113">Open a project:</span></span>

    * <span data-ttu-id="349a8-114">Otevřít Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349a8-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="349a8-115">Klikněte na ikonu Průzkumníka v nabídce vlevo a pak klikněte na tlačítko **otevřít složku**.</span><span class="sxs-lookup"><span data-stu-id="349a8-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="349a8-116">Vyberte **souboru** > **otevřít složku** v hlavní nabídce otevřete složku projektu C# v a klikněte na tlačítko chcete **vybrat složku**.</span><span class="sxs-lookup"><span data-stu-id="349a8-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="349a8-117">V našem příkladu vytváříme složku pro náš projekt s názvem *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="349a8-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="349a8-119">Inicializace projektu v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="349a8-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="349a8-120">Otevřít integrovaný terminál z Visual Studio Code tak, že vyberete **zobrazení** > **integrovaný terminál** z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="349a8-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="349a8-121">V okně terminálu zadejte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="349a8-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="349a8-122">Tento příkaz vytvoří `Program.cs` souboru ve složce s jednoduchou "Hello World" program již vytvořený, spolu s C# soubor projektu s názvem `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="349a8-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Nový příkaz dotnet](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="349a8-124">Vyřešte prostředky sestavení:</span><span class="sxs-lookup"><span data-stu-id="349a8-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="349a8-125">Pro **.NET Core 1.x**, typ `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="349a8-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="349a8-126">Spuštění `dotnet restore` dává vám přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="349a8-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="349a8-128">Spusťte program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="349a8-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="349a8-129">Typ `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="349a8-129">Type `dotnet run`.</span></span>

      ![Spusťte příkaz dotnet](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="349a8-131">Můžete také zhlédnout krátké Výukové video o další pomoc instalační program na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="349a8-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="349a8-132">Ladit</span><span class="sxs-lookup"><span data-stu-id="349a8-132">Debug</span></span>

1. <span data-ttu-id="349a8-133">Otevřít *Program.cs* kliknutím na ni.</span><span class="sxs-lookup"><span data-stu-id="349a8-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="349a8-134">Při prvním otevření souboru C# v sadě Visual Studio Code [OmniSharp](http://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="349a8-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otevřete soubor Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="349a8-136">Visual Studio Code by se zobrazit výzva k přidání chybějící prostředky pro sestavení a ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="349a8-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="349a8-137">Vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="349a8-137">Select **Yes**.</span></span>

    ![Výzva k zadání chybějících prostředků](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="349a8-139">Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="349a8-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otevřete kartu ladění](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="349a8-141">Vyhledejte na zelenou šipku v horní části podokna.</span><span class="sxs-lookup"><span data-stu-id="349a8-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="349a8-142">Ujistěte se, že má rozevíracího seznamu vedle něj `.NET Core Launch (console)` vybrané.</span><span class="sxs-lookup"><span data-stu-id="349a8-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Výběr .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="349a8-144">Přidejte zarážku do svého projektu kliknutím na **okraj editoru**, což je místo na levé straně čísla řádků v editoru vedle řádku 9, nebo textový kurzor na řádku 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="349a8-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Nastavením zarážky](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="349a8-146">Chcete-li spustit ladění, vyberte <kbd>F5</kbd> nebo zelenou šipku.</span><span class="sxs-lookup"><span data-stu-id="349a8-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="349a8-147">Ladicí program se zastaví provádění programu při dosažení zarážky, které jste nastavili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="349a8-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="349a8-148">Při ladění, můžete zobrazit místní proměnné v horním levém podokně nebo použít konzolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="349a8-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Spuštění a ladění](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="349a8-150">Vyberte zelenou šipku v horní části stránky pro pokračování v ladění, nebo vyberte červený čtvereček v horní části zastavit.</span><span class="sxs-lookup"><span data-stu-id="349a8-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP]
> <span data-ttu-id="349a8-151">Další informace a řešení potíží s tipy k ladění rozhraní .NET Core s OmniSharp ve Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="349a8-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="faq"></a><span data-ttu-id="349a8-152">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="349a8-152">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="349a8-153">Chybí požadované prostředky pro sestavení a ladění jazyka C# ve Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349a8-153">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="349a8-154">Moje ladicí program říká "Žádná konfigurace."</span><span class="sxs-lookup"><span data-stu-id="349a8-154">My debugger says "No Configuration."</span></span>

<span data-ttu-id="349a8-155">Rozšíření Visual Studio kódu C# může generovat prostředky pro sestavení a ladění za vás.</span><span class="sxs-lookup"><span data-stu-id="349a8-155">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="349a8-156">Visual Studio Code zobrazí výzvu ke generování těchto prostředků, při prvním otevření projektu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="349a8-156">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="349a8-157">Pokud nebyl vygenerujte prostředky, a spustíte tento příkaz můžete stále tak, že otevřete paletu příkazů (**zobrazení > paletu příkazů**) a zadejte text "> .NET: generovat prostředky pro sestavování a ladění".</span><span class="sxs-lookup"><span data-stu-id="349a8-157">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="349a8-158">Tento výběr generuje .vscode launch.json a tasks.json konfigurační soubory, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="349a8-158">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="349a8-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="349a8-159">See also</span></span>

* [<span data-ttu-id="349a8-160">Nastavení aplikace Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349a8-160">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
* [<span data-ttu-id="349a8-161">Ladění ve Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349a8-161">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
