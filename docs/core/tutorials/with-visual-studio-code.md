---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit první aplikaci .NET Core C# pomocí Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: 4e283f631f463953185a37bf196a1a9b706eee2b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002318"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="4ea86-103">Začínáme s jazykem C# a nástrojem Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ea86-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="4ea86-104">.NET Core poskytuje rychlou a modulární platformu pro vytváření aplikací, které běží na systémech Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="4ea86-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="4ea86-105">Pomocí Visual Studio Code s C# rozšířením můžete získat výkonné prostředí pro C# úpravy s plnou podporou technologie IntelliSense (inteligentní dokončování kódu) a ladění.</span><span class="sxs-lookup"><span data-stu-id="4ea86-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ea86-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ea86-106">Prerequisites</span></span>

1. <span data-ttu-id="4ea86-107">Nainstalujte [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="4ea86-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="4ea86-108">Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="4ea86-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="4ea86-109">Nainstalujte [ C# rozšíření](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pro Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4ea86-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="4ea86-110">Další informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="4ea86-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="4ea86-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="4ea86-111">Hello World</span></span>

<span data-ttu-id="4ea86-112">Pojďme začít jednoduchý program Hello World v .NET Core:</span><span class="sxs-lookup"><span data-stu-id="4ea86-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="4ea86-113">Otevřete projekt:</span><span class="sxs-lookup"><span data-stu-id="4ea86-113">Open a project:</span></span>

    - <span data-ttu-id="4ea86-114">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4ea86-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="4ea86-115">V levé nabídce klikněte na ikonu Průzkumníka a pak klikněte na **Otevřít složku**.</span><span class="sxs-lookup"><span data-stu-id="4ea86-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="4ea86-116">Vyberte **soubor** > **Otevřít složku** z hlavní nabídky a otevřete složku, ve které chcete mít C# projekt, a klikněte na **Vybrat složku**.</span><span class="sxs-lookup"><span data-stu-id="4ea86-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="4ea86-117">V našem příkladu vytvoříme složku pro náš projekt s názvem *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="4ea86-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code otevření složky](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="4ea86-119">Inicializovat C# projekt:</span><span class="sxs-lookup"><span data-stu-id="4ea86-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="4ea86-120">Otevřete integrovaný terminál z Visual Studio Code výběrem možnosti **zobrazit** > **integrovaný terminál** z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4ea86-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="4ea86-121">V okně terminálu zadejte `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="4ea86-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="4ea86-122">Tento příkaz vytvoří soubor *program.cs* ve složce s jednoduchým již zapsaným programem "Hello World" společně se souborem C# projektu s názvem *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="4ea86-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Příkaz dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="4ea86-124">Vyřešte prostředky sestavení:</span><span class="sxs-lookup"><span data-stu-id="4ea86-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="4ea86-125">Pro **.NET Core 1. x**zadejte `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="4ea86-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="4ea86-126">Pokud používáte `dotnet restore`, získáte přístup k požadovaným balíčkům .NET Core, které jsou potřeba k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="4ea86-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="4ea86-128">Spusťte program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="4ea86-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="4ea86-129">Zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4ea86-129">Type `dotnet run`.</span></span>

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="4ea86-131">Můžete si také prohlédnout krátký video kurz pro další nápovědu k instalaci ve [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="4ea86-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="4ea86-132">Ladit</span><span class="sxs-lookup"><span data-stu-id="4ea86-132">Debug</span></span>

1. <span data-ttu-id="4ea86-133">Otevřete *program.cs* kliknutím na něj.</span><span class="sxs-lookup"><span data-stu-id="4ea86-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="4ea86-134">Při prvním otevření C# souboru v Visual Studio Code [OmniSharp](https://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="4ea86-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="4ea86-136">Visual Studio Code by se vám měla zobrazit výzva k přidání chybějících assetů pro sestavení a ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ea86-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="4ea86-137">Vyberte **Ano**.</span><span class="sxs-lookup"><span data-stu-id="4ea86-137">Select **Yes**.</span></span>

    ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="4ea86-139">Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="4ea86-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otevřete kartu ladění v Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="4ea86-141">Vyhledejte zelenou šipku v horní části podokna.</span><span class="sxs-lookup"><span data-stu-id="4ea86-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="4ea86-142">Zajistěte, aby v rozevíracím seznamu vedle něho byla vybrána možnost **spuštění rozhraní .NET Core (konzola)** .</span><span class="sxs-lookup"><span data-stu-id="4ea86-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Výběr .NET Core v Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="4ea86-144">Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je místo na levé straně čísel řádků v editoru, vedle řádku 9 nebo přesuňte kurzor myši na řádek 9 v editoru a stiskněte klávesu <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4ea86-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="4ea86-146">Chcete-li spustit ladění, stiskněte klávesu <kbd>F5</kbd> nebo vyberte zelenou šipku.</span><span class="sxs-lookup"><span data-stu-id="4ea86-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="4ea86-147">Ladicí program zastaví provádění programu při dosažení zarážky, kterou jste nastavili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="4ea86-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="4ea86-148">Během ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít konzolu ladění.</span><span class="sxs-lookup"><span data-stu-id="4ea86-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="4ea86-149">Vyberte modrou šipku v horní části a pokračujte v ladění, nebo vyberte červené čtverce v horní části a zastavte.</span><span class="sxs-lookup"><span data-stu-id="4ea86-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Spuštění a ladění v Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="4ea86-151">Další informace a tipy pro řešení potíží s laděním .NET Core pomocí OmniSharp v Visual Studio Code najdete v tématu [pokyny pro nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="4ea86-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="4ea86-152">Přidání třídy</span><span class="sxs-lookup"><span data-stu-id="4ea86-152">Add a class</span></span>

1. <span data-ttu-id="4ea86-153">Pokud chcete přidat novou třídu, klikněte pravým tlačítkem na VSCode Explorer a vyberte **nový soubor**.</span><span class="sxs-lookup"><span data-stu-id="4ea86-153">To add a new class, right click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="4ea86-154">Tím se přidá nový soubor do složky, kterou jste otevřeli v VSCode.</span><span class="sxs-lookup"><span data-stu-id="4ea86-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="4ea86-155">Pojmenujte soubor *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="4ea86-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="4ea86-156">Je nutné jej uložit s rozšířením `.cs` na konci, aby bylo rozpoznáno jako CSharp soubor.</span><span class="sxs-lookup"><span data-stu-id="4ea86-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="4ea86-157">Přidejte následující kód k vytvoření první třídy.</span><span class="sxs-lookup"><span data-stu-id="4ea86-157">Add the code below to create your first class.</span></span> <span data-ttu-id="4ea86-158">Ujistěte se, že jste zahrnuli správný obor názvů, abyste na něj mohli odkazovat ze souboru *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="4ea86-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

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

4. <span data-ttu-id="4ea86-159">Zavolejte svou novou třídu z metody Main v *program.cs* přidáním kódu níže:</span><span class="sxs-lookup"><span data-stu-id="4ea86-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

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

5. <span data-ttu-id="4ea86-160">Uložte změny a spusťte program znovu.</span><span class="sxs-lookup"><span data-stu-id="4ea86-160">Save your changes and run your program again.</span></span> <span data-ttu-id="4ea86-161">Nová zpráva by se měla zobrazit spolu s připojovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="4ea86-161">The new message should appear with the appended string.</span></span>

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="4ea86-162">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="4ea86-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="4ea86-163">Chybí požadované prostředky pro sestavení a ladění C# v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4ea86-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="4ea86-164">Můj ladicí program říká "žádnou konfiguraci".</span><span class="sxs-lookup"><span data-stu-id="4ea86-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="4ea86-165">Rozšíření Visual Studio Code C# může generovat assety pro sestavení a ladění.</span><span class="sxs-lookup"><span data-stu-id="4ea86-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="4ea86-166">Visual Studio Code vás vyzve k vygenerování těchto assetů při prvním otevření C# projektu.</span><span class="sxs-lookup"><span data-stu-id="4ea86-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="4ea86-167">Pokud jste nevytvořili prostředky, můžete přesto spustit tento příkaz otevřením palety příkazů (**zobrazení palety příkazů zobrazit >** ) a zadáním "> .NET: generovat prostředky pro sestavení a ladění".</span><span class="sxs-lookup"><span data-stu-id="4ea86-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="4ea86-168">Výběrem této možnosti se vytvoří konfigurační soubory *. VSCode*, *Launch. JSON*a *Tasks. JSON* , které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="4ea86-168">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ea86-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ea86-169">See also</span></span>

- [<span data-ttu-id="4ea86-170">Nastavení Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ea86-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="4ea86-171">Ladění v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ea86-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
