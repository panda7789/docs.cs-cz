---
title: Začínáme s jazykem C# a nástrojem Visual Studio Code
description: Naučte se, jak vytvořit a ladit první aplikaci .NET Core v jazyce C# pomocí kódu sady Visual Studio.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 8eaf1ba2314dcab96db615a8691afed82c5011a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398879"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="916b9-103">Začínáme s jazykem C# a nástrojem Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="916b9-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="916b9-104">.NET Core nabízí rychlou a modulární platformu pro vytváření aplikací, které běží na Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="916b9-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="916b9-105">Použijte Visual Studio Kód s rozšířením C# získat výkonné prostředí pro úpravy s plnou podporou pro C# IntelliSense (inteligentní dokončení kódu) a ladění.</span><span class="sxs-lookup"><span data-stu-id="916b9-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="916b9-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="916b9-106">Prerequisites</span></span>

1. <span data-ttu-id="916b9-107">Nainstalujte [kód sady Visual Studio](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="916b9-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="916b9-108">Nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="916b9-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="916b9-109">Nainstalujte [rozšíření C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pro kód sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="916b9-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="916b9-110">Další informace o instalaci rozšíření v kódu sady Visual Studio naleznete v [tématu VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="916b9-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="916b9-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="916b9-111">Hello World</span></span>

<span data-ttu-id="916b9-112">Začněme s jednoduchým programem "Hello World" na .NET Core:</span><span class="sxs-lookup"><span data-stu-id="916b9-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="916b9-113">Otevření projektu:</span><span class="sxs-lookup"><span data-stu-id="916b9-113">Open a project:</span></span>

    - <span data-ttu-id="916b9-114">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="916b9-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="916b9-115">Klikněte na ikonu Průzkumníka v levé nabídce a potom klikněte na **Otevřít složku**.</span><span class="sxs-lookup"><span data-stu-id="916b9-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="916b9-116">Vyberte Otevřít složku **souboru** > **Open Folder** z hlavní nabídky, chcete-li otevřít složku, ve které má být projekt C#, a klepněte na tlačítko **Vybrat složku**.</span><span class="sxs-lookup"><span data-stu-id="916b9-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="916b9-117">Pro náš příklad vytváříme složku pro náš projekt s názvem *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="916b9-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Otevřená složka kódu Visual Studia](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="916b9-119">Inicializovat projekt Jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="916b9-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="916b9-120">Otevřete integrovaný terminál z visual studio kódu výběrem **zobrazit** > **integrovaný terminál** z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="916b9-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="916b9-121">Do okna terminálu `dotnet new console`zadejte příkaz .</span><span class="sxs-lookup"><span data-stu-id="916b9-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="916b9-122">Tento příkaz vytvoří *Program.cs* soubor ve složce s jednoduchým programem "Hello World", který je již napsán, spolu s souborem projektu C# s názvem *HelloWorld.csproj*.</span><span class="sxs-lookup"><span data-stu-id="916b9-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Dotnet new příkaz](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="916b9-124">Vyřešte datové zdroje sestavení:</span><span class="sxs-lookup"><span data-stu-id="916b9-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="916b9-125">Pro **rozhraní .NET Core 1.x**zadejte `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="916b9-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="916b9-126">Spuštění `dotnet restore` umožňuje přístup k požadované balíčky .NET Core, které jsou potřebné k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="916b9-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Příkaz dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="916b9-128">Spusťte program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="916b9-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="916b9-129">Zadejte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="916b9-129">Type `dotnet run`.</span></span>

      ![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="916b9-131">Můžete také sledovat krátké instruktážní video pro další nastavení nápovědy pro [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)nebo [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="916b9-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="916b9-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="916b9-132">Debug</span></span>

1. <span data-ttu-id="916b9-133">Otevřete *Program.cs* kliknutím na něj.</span><span class="sxs-lookup"><span data-stu-id="916b9-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="916b9-134">Při prvním otevření souboru C# v kódu sady Visual Studio [omnisharp](https://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="916b9-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otevření souboru Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="916b9-136">Visual Studio Code by vás měl vyzvat k přidání chybějících prostředků pro sestavení a ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="916b9-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="916b9-137">Vyberte **ano**.</span><span class="sxs-lookup"><span data-stu-id="916b9-137">Select **Yes**.</span></span>

    ![Dotázat se na chybějící datové zdroje](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="916b9-139">Chcete-li otevřít zobrazení ladění, klikněte na ikonu ladění v nabídce na levé straně.</span><span class="sxs-lookup"><span data-stu-id="916b9-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otevření karty Ladění v kódu Sady Visual Studio](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="916b9-141">Vyhledejte zelenou šipku v horní části podokna.</span><span class="sxs-lookup"><span data-stu-id="916b9-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="916b9-142">Ujistěte se, že rozbalovací rozbalovací soubor vedle něj má **vybranou .NET Core Launch (konzolu).**</span><span class="sxs-lookup"><span data-stu-id="916b9-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Výběr jádra rozhraní .NET v kódu sady Visual Studio](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="916b9-144">Přidejte do projektu zarážku kliknutím na **okraj editoru**, což je mezera vlevo od čísel řádků v editoru vedle řádku 9, nebo přesuňte textový kurzor na řádek 9 v editoru a stiskněte <kbd>klávesu F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="916b9-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Nastavení zarážky](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="916b9-146">Chcete-li zahájit ladění, stiskněte <kbd>klávesu F5</kbd> nebo vyberte zelenou šipku.</span><span class="sxs-lookup"><span data-stu-id="916b9-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="916b9-147">Ladicí program zastaví provádění programu, když dosáhne zarážky, kterou nastavíte v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="916b9-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="916b9-148">Při ladění můžete zobrazit místní proměnné v levém horním podokně nebo použít ladicí konzolu.</span><span class="sxs-lookup"><span data-stu-id="916b9-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="916b9-149">Chcete-li pokračovat v ladění, vyberte modrou šipku nahoře, nebo vyberte červený čtverec v horní části, který chcete zastavit.</span><span class="sxs-lookup"><span data-stu-id="916b9-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Spustit a ladit v kódu sady Visual Studio](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="916b9-151">Další informace a tipy pro řešení potíží s laděním jádra .NET pomocí omnisharpu v kódu visual studia naleznete v [pokynech k nastavení ladicího programu .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="916b9-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="916b9-152">Přidání třídy</span><span class="sxs-lookup"><span data-stu-id="916b9-152">Add a class</span></span>

1. <span data-ttu-id="916b9-153">Chcete-li přidat novou třídu, klepněte pravým tlačítkem myši do průzkumníka VSCode exploreru a vyberte **nový soubor**.</span><span class="sxs-lookup"><span data-stu-id="916b9-153">To add a new class, right click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="916b9-154">Tím přidáte nový soubor do složky, kterou máte otevřenou ve VSCode.</span><span class="sxs-lookup"><span data-stu-id="916b9-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="916b9-155">Pojmenujte soubor *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="916b9-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="916b9-156">Musíte jej uložit `.cs` s příponou na konci, aby byl rozpoznán jako soubor csharp.</span><span class="sxs-lookup"><span data-stu-id="916b9-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="916b9-157">Přidejte níže uvedený kód a vytvořte si první třídu.</span><span class="sxs-lookup"><span data-stu-id="916b9-157">Add the code below to create your first class.</span></span> <span data-ttu-id="916b9-158">Nezapomeňte zahrnout správný obor názvů, abyste na něj mohli odkazovat ze *Program.cs* souboru:</span><span class="sxs-lookup"><span data-stu-id="916b9-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

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

4. <span data-ttu-id="916b9-159">Zavolejte do své nové třídy z hlavní metody v *Program.cs* přidáním níže uvedeného kódu:</span><span class="sxs-lookup"><span data-stu-id="916b9-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

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

5. <span data-ttu-id="916b9-160">Uložte změny a znovu spusťte program.</span><span class="sxs-lookup"><span data-stu-id="916b9-160">Save your changes and run your program again.</span></span> <span data-ttu-id="916b9-161">Nová zpráva by se měla zobrazit s připojeným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="916b9-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="916b9-162">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="916b9-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="916b9-163">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="916b9-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="916b9-164">Chybí mi požadované prostředky k sestavení a ladění jazyka C# v kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="916b9-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="916b9-165">V ladicím programu je uvedeno "Žádná konfigurace".</span><span class="sxs-lookup"><span data-stu-id="916b9-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="916b9-166">Rozšíření visual studio kód C# můžete generovat prostředky pro sestavení a ladění pro vás.</span><span class="sxs-lookup"><span data-stu-id="916b9-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="916b9-167">Visual Studio Code vás vyzve ke generování těchto prostředků při prvním otevření projektu Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="916b9-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="916b9-168">Pokud jste negenerovali datové zdroje, můžete tento příkaz spustit otevřením palety příkazů **(Zobrazit paletu příkazů >)** a zadáním příkazu ">.NET: Generovat datové zdroje pro sestavení a ladění".</span><span class="sxs-lookup"><span data-stu-id="916b9-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="916b9-169">Výběrem této možnosti se vygenerují konfigurační soubory *.vscode*, *launch.json*a *tasks.json,* které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="916b9-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="916b9-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="916b9-170">See also</span></span>

- [<span data-ttu-id="916b9-171">Nastavení kódu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="916b9-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="916b9-172">Ladění v kódu sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="916b9-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
