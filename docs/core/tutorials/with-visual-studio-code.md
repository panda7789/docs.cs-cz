---
title: Začínáme s C# a Visual Studio Code - průvodce v C#
description: Naučte se vytvářet a ladit první aplikaci .NET Core v C# s použitím Visual Studio Code.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 8958c39ba16cadbfab95e35fa36e8e85ce0a4ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213613"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="edd85-103">Začínáme s C# a Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="edd85-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="edd85-104">.NET core poskytuje rychlou modulární platformu pro vytváření aplikací, které běží na systému Windows, Linux a systému macOS.</span><span class="sxs-lookup"><span data-stu-id="edd85-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="edd85-105">Použijte Visual Studio Code s příponou C# získání výkonné možnosti s plnou podporu pro C# IntelliSense (doplňování kódu pro inteligentní) úprav a ladění.</span><span class="sxs-lookup"><span data-stu-id="edd85-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edd85-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edd85-106">Prerequisites</span></span>

1. <span data-ttu-id="edd85-107">Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="edd85-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="edd85-108">Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="edd85-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="edd85-109">Nainstalujte [C# rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="edd85-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="edd85-110">Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code najdete v tématu [VS kód rozšíření Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="edd85-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="edd85-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="edd85-111">Hello World</span></span>

<span data-ttu-id="edd85-112">Můžeme začít pracovat s jednoduchý program "Hello World" na .NET Core:</span><span class="sxs-lookup"><span data-stu-id="edd85-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="edd85-113">Otevřete projekt:</span><span class="sxs-lookup"><span data-stu-id="edd85-113">Open a project:</span></span>

    * <span data-ttu-id="edd85-114">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="edd85-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="edd85-115">Klikněte na ikonu Explorer v levé nabídce a potom klikněte na **otevřít složku**.</span><span class="sxs-lookup"><span data-stu-id="edd85-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="edd85-116">Vyberte **soubor** > **otevřete složku** z hlavní nabídky otevření složky chcete projektu C# je v a klikněte na tlačítko **vyberte složku**.</span><span class="sxs-lookup"><span data-stu-id="edd85-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="edd85-117">Pro náš příklad vytváříme složku pro naše projektu s názvem *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="edd85-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="edd85-119">Inicializace projektu C#:</span><span class="sxs-lookup"><span data-stu-id="edd85-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="edd85-120">Otevřete integrované terminál z Visual Studio Code výběrem **zobrazení** > **integrované Terminálové** z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="edd85-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="edd85-121">V okně terminálu zadejte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="edd85-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="edd85-122">Tento příkaz vytvoří `Program.cs` soubor ve složce s jednoduché "Hello, World" program již vytvořený, společně s C# projektu soubor s názvem `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="edd85-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Nový příkaz dotnet.](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="edd85-124">Vyřešte prostředky sestavení:</span><span class="sxs-lookup"><span data-stu-id="edd85-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="edd85-125">Pro **.NET Core 1.x**, typ `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="edd85-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="edd85-126">Spuštění `dotnet restore` dává vám přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="edd85-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Příkaz restore dotnet.](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="edd85-128">Spusťte program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="edd85-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="edd85-129">Typ `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="edd85-129">Type `dotnet run`.</span></span> 

      ![Dotnet, spusťte příkaz](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="edd85-131">Můžete také shlédnout krátké video kurz pro další pomoc instalační program na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [systému macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="edd85-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="edd85-132">Ladit</span><span class="sxs-lookup"><span data-stu-id="edd85-132">Debug</span></span>

1. <span data-ttu-id="edd85-133">Otevřete *Program.cs* kliknutím na.</span><span class="sxs-lookup"><span data-stu-id="edd85-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="edd85-134">Při prvním otevření souboru C# v sadě Visual Studio Code [OmniSharp](http://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="edd85-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otevřete soubor Program.cs](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="edd85-136">Visual Studio Code by se zobrazit výzva k přidání chybějící prostředky pro sestavení a ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="edd85-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="edd85-137">Vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="edd85-137">Select **Yes**.</span></span> 

    ![Výzva k zadání chybějící prostředky](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="edd85-139">Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v levé nabídce.</span><span class="sxs-lookup"><span data-stu-id="edd85-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otevřete kartu ladění](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="edd85-141">Vyhledejte na zelenou šipku v horní části podokna.</span><span class="sxs-lookup"><span data-stu-id="edd85-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="edd85-142">Ověřte, zda má rozevíracího seznamu vedle `.NET Core Launch (console)` vybrané.</span><span class="sxs-lookup"><span data-stu-id="edd85-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Výběr .NET Core](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="edd85-144">Do projektu přidejte zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísla řádků v editoru vedle řádku 9.</span><span class="sxs-lookup"><span data-stu-id="edd85-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![Nastavení boru přerušení](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="edd85-146">Chcete-li začít, ladění, vyberte <kbd>F5</kbd> nebo zelenou šipku.</span><span class="sxs-lookup"><span data-stu-id="edd85-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="edd85-147">Ladicí program zastaví programu, když dorazí do zarážek, které jste nastavili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="edd85-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="edd85-148">Při ladění, můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="edd85-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Spuštění a ladění](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="edd85-150">Vyberte zelenou šipku v horní části, chcete-li pokračovat, ladění, nebo červený čtvereček v horní části zastavit.</span><span class="sxs-lookup"><span data-stu-id="edd85-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="edd85-151">Další informace a tipy na .NET Core ladění pomocí OmniSharp v kódu Visual Studio pro odstraňování potíží naleznete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="edd85-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edd85-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="edd85-152">See also</span></span>
<span data-ttu-id="edd85-153">[Nastavení kódu v jazyce Visual Studio](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="edd85-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="edd85-154">Ladění v sadě Visual Studio kódu</span><span class="sxs-lookup"><span data-stu-id="edd85-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
