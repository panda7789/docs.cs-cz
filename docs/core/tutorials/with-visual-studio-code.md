---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit svou první aplikaci .NET Core v jazyce C# pomocí Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506879"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="cf56c-103">Začínáme s jazykem C# a nástrojem Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cf56c-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="cf56c-104">.NET Core poskytuje rychlou a modulární platformu pro vytváření aplikací, které běží na systémech Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="cf56c-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="cf56c-105">Použijte Visual Studio Code s rozšířením C# k získání výkonného prostředí pro úpravy s plnou podporou pro C# IntelliSense (inteligentní dokončování kódu) a ladění.</span><span class="sxs-lookup"><span data-stu-id="cf56c-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf56c-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf56c-106">Prerequisites</span></span>

1. <span data-ttu-id="cf56c-107">Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="cf56c-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="cf56c-108">Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="cf56c-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="cf56c-109">Nainstalujte [rozšíření C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pro Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cf56c-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="cf56c-110">Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="cf56c-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="cf56c-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="cf56c-111">Hello World</span></span>

<span data-ttu-id="cf56c-112">Začínáme s jednoduchým programem "Hello World" v .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cf56c-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="cf56c-113">Otevřete projekt:</span><span class="sxs-lookup"><span data-stu-id="cf56c-113">Open a project:</span></span>

    - <span data-ttu-id="cf56c-114">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cf56c-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="cf56c-115">V hlavní nabídce vyberte **soubor** > **Otevřít složku** .</span><span class="sxs-lookup"><span data-stu-id="cf56c-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="cf56c-116">Vytvořte složku s názvem *HelloWorld*a klikněte na **Vybrat složku**.</span><span class="sxs-lookup"><span data-stu-id="cf56c-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="cf56c-117">Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cf56c-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="cf56c-118">Později do kurzu přidáte kód, který předpokládá, že je `HelloWorld`obor názvů projektu.</span><span class="sxs-lookup"><span data-stu-id="cf56c-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="cf56c-119">Inicializovat projekt C#:</span><span class="sxs-lookup"><span data-stu-id="cf56c-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="cf56c-120">Otevření terminálu z Visual Studio Code výběrem možnosti **Zobrazit** > **terminál** v hlavní nabídce.</span><span class="sxs-lookup"><span data-stu-id="cf56c-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="cf56c-121">V okně terminálu zadejte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="cf56c-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="cf56c-122">Tento příkaz vytvoří soubor *program.cs* ve složce s jednoduchým již zapsaným programem "Hello World" společně se souborem projektu C# s názvem *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="cf56c-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Příkaz dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="cf56c-124">Spusťte program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="cf56c-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="cf56c-125">V okně terminálu zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="cf56c-125">In the terminal window, enter `dotnet run`.</span></span>

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="cf56c-127">Ladit</span><span class="sxs-lookup"><span data-stu-id="cf56c-127">Debug</span></span>

1. <span data-ttu-id="cf56c-128">Otevřete *program.cs* kliknutím na něj.</span><span class="sxs-lookup"><span data-stu-id="cf56c-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="cf56c-129">Při prvním otevření souboru jazyka C# v Visual Studio Code se [OmniSharp](https://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="cf56c-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="cf56c-131">Visual Studio Code vás vyzve k přidání chybějících assetů pro sestavení a ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf56c-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="cf56c-132">Vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="cf56c-132">Select **Yes**.</span></span>

    ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="cf56c-134">Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="cf56c-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otevřete kartu ladění v Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="cf56c-136">Vyhledejte zelenou šipku v horní části podokna.</span><span class="sxs-lookup"><span data-stu-id="cf56c-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="cf56c-137">Zajistěte, aby v rozevíracím seznamu vedle něho byla vybrána možnost **spuštění rozhraní .NET Core (konzola)** .</span><span class="sxs-lookup"><span data-stu-id="cf56c-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Výběr .NET Core v Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="cf56c-139">Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísel řádků v editoru, vedle řádku 9 nebo přesuňte kurzor myši na řádek 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="cf56c-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="cf56c-141">Chcete-li spustit ladění, stiskněte klávesu <kbd>F5</kbd> nebo vyberte zelenou šipku.</span><span class="sxs-lookup"><span data-stu-id="cf56c-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="cf56c-142">Ladicí program zastaví provádění programu při dosažení zarážky, kterou jste nastavili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="cf56c-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="cf56c-143">Během ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu ladění.</span><span class="sxs-lookup"><span data-stu-id="cf56c-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="cf56c-144">Vyberte modrou šipku v horní části a pokračujte v ladění, nebo vyberte červené čtverce v horní části a zastavte.</span><span class="sxs-lookup"><span data-stu-id="cf56c-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Spuštění a ladění v Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="cf56c-146">Další informace a tipy pro řešení potíží s laděním .NET Core pomocí OmniSharp v Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="cf56c-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="cf56c-147">Přidání třídy</span><span class="sxs-lookup"><span data-stu-id="cf56c-147">Add a class</span></span>

1. <span data-ttu-id="cf56c-148">Chcete-li přidat novou třídu, klikněte pravým tlačítkem myši v Průzkumníkovi VSCode pod *program.cs* a vyberte možnost **nový soubor**.</span><span class="sxs-lookup"><span data-stu-id="cf56c-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="cf56c-149">Tím se přidá nový soubor do složky, kterou jste otevřeli v VSCode.</span><span class="sxs-lookup"><span data-stu-id="cf56c-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="cf56c-150">Pojmenujte soubor *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="cf56c-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="cf56c-151">Je nutné jej uložit s `.cs` příponou na konci, aby jej bylo možné rozpoznat jako CSharp soubor.</span><span class="sxs-lookup"><span data-stu-id="cf56c-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="cf56c-152">Přidejte následující kód k vytvoření první třídy.</span><span class="sxs-lookup"><span data-stu-id="cf56c-152">Add the following code to create your first class.</span></span>

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

1. <span data-ttu-id="cf56c-153">Zavolejte svou novou třídu z `Main` metody tak, že nahradíte kód v *program.cs* pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="cf56c-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

1. <span data-ttu-id="cf56c-154">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="cf56c-154">Save your changes.</span></span>

1. <span data-ttu-id="cf56c-155">Spusťte program znovu.</span><span class="sxs-lookup"><span data-stu-id="cf56c-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="cf56c-156">Nová zpráva se zobrazí spolu s připojovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="cf56c-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="cf56c-157">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="cf56c-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="cf56c-158">Chybí požadované prostředky pro sestavení a ladění C# v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cf56c-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="cf56c-159">Můj ladicí program říká "žádnou konfiguraci".</span><span class="sxs-lookup"><span data-stu-id="cf56c-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="cf56c-160">Rozšíření Visual Studio Code C# může generovat assety pro sestavení a ladění.</span><span class="sxs-lookup"><span data-stu-id="cf56c-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="cf56c-161">Visual Studio Code se zobrazí výzva, abyste tyto prostředky vygenerovali při prvním otevření projektu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cf56c-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="cf56c-162">Pokud jste nevytvořili prostředky, můžete přesto spustit tento příkaz otevřením palety příkazů (**zobrazení palety příkazů zobrazit >**) a zadáním "> .NET: generovat prostředky pro sestavení a ladění".</span><span class="sxs-lookup"><span data-stu-id="cf56c-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="cf56c-163">Výběrem této možnosti se vytvoří konfigurační soubory *. VSCode*, *Launch. JSON*a *Tasks. JSON* , které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="cf56c-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf56c-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf56c-164">See also</span></span>

- [<span data-ttu-id="cf56c-165">Nastavení Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cf56c-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="cf56c-166">Ladění v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cf56c-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
