---
title: Vytvoření konzolové aplikace pomocí .NET Core pomocí Visual Studio Code
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201709"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="828af-103">Kurz: Vytvoření konzolové aplikace pomocí .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="828af-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="828af-104">V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio Code a .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="828af-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="828af-105">Úkoly projektu, jako je vytváření, kompilování a spuštění projektu, jsou prováděny pomocí rozhraní příkazového řádku, takže můžete postupovat podle tohoto kurzu v jiném editoru kódu a v případě potřeby spustit příkazy v terminálu.</span><span class="sxs-lookup"><span data-stu-id="828af-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="828af-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="828af-106">Prerequisites</span></span>

1. <span data-ttu-id="828af-107">[Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="828af-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="828af-108">Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="828af-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="828af-109">[.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="828af-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="828af-110">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="828af-110">Create the app</span></span>

1. <span data-ttu-id="828af-111">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="828af-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="828af-112">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="828af-112">Create a project.</span></span>

   1. <span data-ttu-id="828af-113">V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** / **otevřít...** , vytvořte složku *HelloWorld* a klikněte na **Vybrat složku** / **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="828af-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="828af-114">Název složky se ve výchozím nastavení zobrazí jako název projektu a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="828af-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="828af-115">Později do kurzu přidáte kód, který předpokládá, že je obor názvů projektu `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="828af-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="828af-116">Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="828af-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="828af-117">**Terminál** se otevře s příkazovým řádkem ve složce *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="828af-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="828af-118">V **terminálu**zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="828af-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="828af-119">Šablona konzolové aplikace pro .NET Core definuje třídu `Program` s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="828af-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="828af-120">Soubor *program.cs* má následující kód:</span><span class="sxs-lookup"><span data-stu-id="828af-120">The *Program.cs* file has the following code:</span></span>

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

<span data-ttu-id="828af-121">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="828af-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="828af-122">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .</span><span class="sxs-lookup"><span data-stu-id="828af-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="828af-123">Šablona vytvoří jednoduchou aplikaci, která volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="828af-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="828af-124">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="828af-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="828af-125">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="828af-125">Run the app</span></span>

<span data-ttu-id="828af-126">V **terminálu**spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="828af-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="828af-127">Program zobrazí "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="828af-127">The program displays "Hello World!"</span></span> <span data-ttu-id="828af-128">a končí.</span><span class="sxs-lookup"><span data-stu-id="828af-128">and ends.</span></span>

![Příkaz dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="828af-130">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="828af-130">Enhance the app</span></span>

<span data-ttu-id="828af-131">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="828af-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="828af-132">Otevřete *program.cs* kliknutím na něj.</span><span class="sxs-lookup"><span data-stu-id="828af-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="828af-133">Při prvním otevření souboru jazyka C# v Visual Studio Code se [OmniSharp](https://www.omnisharp.net/) načte v editoru.</span><span class="sxs-lookup"><span data-stu-id="828af-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Otevřít soubor Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="828af-135">Pokud vás Visual Studio Code vyzve k přidání chybějících assetů k sestavení a ladění vaší aplikace, vyberte **Ano** .</span><span class="sxs-lookup"><span data-stu-id="828af-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Vyzvat k chybějícím prostředkům](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="828af-137">Nahraďte obsah `Main` metody v *program.cs*, což je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="828af-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="828af-138">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="828af-138">This code displays "What is your name?"</span></span> <span data-ttu-id="828af-139">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou **ENTER** .</span><span class="sxs-lookup"><span data-stu-id="828af-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="828af-140">Tento řetězec je uložen v proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="828af-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="828af-141">Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` .</span><span class="sxs-lookup"><span data-stu-id="828af-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="828af-142">Nakonec tyto hodnoty zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="828af-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="828af-143">`\n`Představuje znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="828af-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="828af-144">Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="828af-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="828af-145">Hodnota výrazu je vložena do řetězce místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="828af-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="828af-146">Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="828af-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="828af-147">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="828af-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="828af-148">V Visual Studio Code musíte explicitně uložit změny.</span><span class="sxs-lookup"><span data-stu-id="828af-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="828af-149">Na rozdíl od sady Visual Studio se změny souborů při sestavení a spuštění aplikace automaticky neuloží.</span><span class="sxs-lookup"><span data-stu-id="828af-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="828af-150">Spusťte program znovu:</span><span class="sxs-lookup"><span data-stu-id="828af-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="828af-151">Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="828af-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminálu s upraveným výstupem programu":::

1. <span data-ttu-id="828af-153">Ukončete program stisknutím libovolné klávesy.</span><span class="sxs-lookup"><span data-stu-id="828af-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="828af-154">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="828af-154">Additional resources</span></span>

- [<span data-ttu-id="828af-155">Nastavení Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="828af-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="828af-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="828af-156">Next steps</span></span>

<span data-ttu-id="828af-157">V tomto kurzu jste vytvořili aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="828af-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="828af-158">V dalším kurzu ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="828af-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="828af-159">Ladění konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="828af-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
