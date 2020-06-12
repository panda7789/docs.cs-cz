---
title: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.
ms.date: 05/22/2020
ms.openlocfilehash: 6d8f9adb2f77dbfd2d1cf54c80f1cdea582b1d96
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717507"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="3a5b8-103">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3a5b8-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="3a5b8-104">V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="3a5b8-105">Úkoly projektu, jako je vytváření, kompilování a spuštění projektu, jsou prováděny pomocí .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="3a5b8-106">Pokud chcete, můžete postupovat podle tohoto kurzu v jiném editoru kódu a v terminálu spustit příkazy.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a5b8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a5b8-107">Prerequisites</span></span>

1. <span data-ttu-id="3a5b8-108">[Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="3a5b8-109">Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="3a5b8-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="3a5b8-110">[.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="3a5b8-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="3a5b8-111">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="3a5b8-111">Create the app</span></span>

<span data-ttu-id="3a5b8-112">Vytvořte projekt konzolové aplikace .NET Core s názvem HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="3a5b8-113">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="3a5b8-114">V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** (**soubor**  >  **otevřít...** v MacOS).</span><span class="sxs-lookup"><span data-stu-id="3a5b8-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="3a5b8-115">V dialogovém okně **Otevřít složku** vytvořte složku *HelloWorld* a klikněte na **Vybrat složku** (**otevřít** v MacOS).</span><span class="sxs-lookup"><span data-stu-id="3a5b8-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="3a5b8-116">Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="3a5b8-117">Později do kurzu přidáte kód, který předpokládá, že je obor názvů projektu `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="3a5b8-118">Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="3a5b8-119">**Terminál** se otevře s příkazovým řádkem ve složce *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="3a5b8-120">V **terminálu**zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3a5b8-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="3a5b8-121">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="3a5b8-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="3a5b8-122">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3a5b8-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="3a5b8-123">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-123">in the console window.</span></span>

<span data-ttu-id="3a5b8-124">Kód šablony definuje třídu, `Program` , s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument:</span><span class="sxs-lookup"><span data-stu-id="3a5b8-124">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="3a5b8-125">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-125">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="3a5b8-126">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-126">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="3a5b8-127">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3a5b8-127">Run the app</span></span>

<span data-ttu-id="3a5b8-128">V **terminálu**spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3a5b8-128">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="3a5b8-129">Program zobrazí "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3a5b8-129">The program displays "Hello World!"</span></span> <span data-ttu-id="3a5b8-130">a končí.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-130">and ends.</span></span>

![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="3a5b8-132">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="3a5b8-132">Enhance the app</span></span>

<span data-ttu-id="3a5b8-133">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-133">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="3a5b8-134">Otevřete *program.cs* kliknutím na něj.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-134">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="3a5b8-135">Při prvním otevření souboru jazyka C# v Visual Studio Code se [OmniSharp](https://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-135">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="3a5b8-137">Pokud vás Visual Studio Code vyzve k přidání chybějících assetů k sestavení a ladění vaší aplikace, vyberte **Ano** .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-137">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="3a5b8-139">Nahraďte obsah `Main` metody v *program.cs*, což je řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="3a5b8-139">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   <span data-ttu-id="3a5b8-140">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="3a5b8-140">This code displays "What is your name?"</span></span> <span data-ttu-id="3a5b8-141">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-141">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="3a5b8-142">Tento řetězec je uložen v proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="3a5b8-143">Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` .</span><span class="sxs-lookup"><span data-stu-id="3a5b8-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="3a5b8-144">Nakonec tyto hodnoty zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-144">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="3a5b8-145">`\n`Představuje znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-145">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="3a5b8-146">Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-146">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="3a5b8-147">Hodnota výrazu je vložena do řetězce místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-147">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="3a5b8-148">Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="3a5b8-148">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="3a5b8-149">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-149">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="3a5b8-150">V Visual Studio Code musíte explicitně uložit změny.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-150">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="3a5b8-151">Na rozdíl od sady Visual Studio se změny souborů při sestavení a spuštění aplikace automaticky neuloží.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-151">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="3a5b8-152">Spusťte program znovu:</span><span class="sxs-lookup"><span data-stu-id="3a5b8-152">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="3a5b8-153">Zadáním názvu a stisknutím klávesy <kbd>ENTER</kbd> odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-153">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminálu s upraveným výstupem programu":::

1. <span data-ttu-id="3a5b8-155">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-155">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3a5b8-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3a5b8-156">Additional resources</span></span>

- [<span data-ttu-id="3a5b8-157">Nastavení Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3a5b8-157">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="3a5b8-158">Další kroky</span><span class="sxs-lookup"><span data-stu-id="3a5b8-158">Next steps</span></span>

<span data-ttu-id="3a5b8-159">V tomto kurzu jste vytvořili konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-159">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="3a5b8-160">V dalším kurzu ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-160">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a5b8-161">Ladění konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3a5b8-161">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
