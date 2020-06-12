---
title: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Naučte se vytvořit konzolovou aplikaci .NET Core pomocí Visual Studio pro Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 57f16e510270b7256b285493b1f978101fc11804
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717520"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="e02fd-103">Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="e02fd-103">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="e02fd-104">V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core pomocí Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="e02fd-104">This tutorial shows how to create and run a .NET Core console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="e02fd-105">Vaše zpětná vazba je vysoce ohodnocená.</span><span class="sxs-lookup"><span data-stu-id="e02fd-105">Your feedback is highly valued.</span></span> <span data-ttu-id="e02fd-106">Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="e02fd-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="e02fd-107">V Visual Studio pro Mac vyberte v nabídce **nápovědu**  >  **nahlásit problém** nebo **nahlásit problém** z úvodní obrazovky. tím otevřete okno pro podání zprávy o chybě.</span><span class="sxs-lookup"><span data-stu-id="e02fd-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="e02fd-108">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="e02fd-108">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="e02fd-109">Chcete-li vytvořit návrh, **vyberte v**  >  nabídce možnost**poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás převezme na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="e02fd-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e02fd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e02fd-110">Prerequisites</span></span>

* <span data-ttu-id="e02fd-111">[Visual Studio pro Mac verze 8,6 nebo novější](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="e02fd-111">[Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="e02fd-112">Vyberte možnost instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e02fd-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="e02fd-113">Instalace Xamarin je volitelná pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e02fd-113">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="e02fd-114">Další informace najdete v následujících materiálech:</span><span class="sxs-lookup"><span data-stu-id="e02fd-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="e02fd-115">[Kurz: instalace Visual Studio pro Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="e02fd-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="e02fd-116">[Podporované verze MacOS](../install/dependencies.md?pivots=os-macos)</span><span class="sxs-lookup"><span data-stu-id="e02fd-116">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="e02fd-117">[Verze .NET Core podporované nástrojem Visual Studio pro Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="e02fd-117">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="e02fd-118">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="e02fd-118">Create the app</span></span>

<span data-ttu-id="e02fd-119">Vytvořte projekt konzolové aplikace .NET Core s názvem HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="e02fd-119">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="e02fd-120">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="e02fd-120">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="e02fd-121">V úvodním okně vyberte **Nový** .</span><span class="sxs-lookup"><span data-stu-id="e02fd-121">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Tlačítko Nový na úvodní obrazovce Visual Studio pro Mac":::

1. <span data-ttu-id="e02fd-123">V dialogovém okně **Nový projekt** vyberte **aplikace** v uzlu **web a konzola** .</span><span class="sxs-lookup"><span data-stu-id="e02fd-123">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="e02fd-124">Vyberte šablonu **Konzolová aplikace** a vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="e02fd-124">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Seznam nových šablon projektů":::

1. <span data-ttu-id="e02fd-126">V rozevíracím seznamu **Cílová architektura** v dialogovém okně **Konfigurovat novou konzolovou aplikaci** vyberte **.NET Core 3,1**a vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="e02fd-126">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET Core 3.1**, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Vybrat cílové rozhraní .NET Framework":::

1. <span data-ttu-id="e02fd-128">Zadejte "HelloWorld" pro **název projektu**a vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e02fd-128">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Dialogové okno Konfigurovat novou konzolovou aplikaci":::

<span data-ttu-id="e02fd-130">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e02fd-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="e02fd-131">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e02fd-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="e02fd-132">v okně terminálu.</span><span class="sxs-lookup"><span data-stu-id="e02fd-132">in the terminal window.</span></span>

<span data-ttu-id="e02fd-133">Kód šablony definuje třídu, `Program` , s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument:</span><span class="sxs-lookup"><span data-stu-id="e02fd-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="e02fd-134">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e02fd-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e02fd-135">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v `args` poli.</span><span class="sxs-lookup"><span data-stu-id="e02fd-135">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="e02fd-136">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e02fd-136">Run the app</span></span>

1. <span data-ttu-id="e02fd-137">Stiskněte <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>), aby se aplikace spouštěla bez ladění.</span><span class="sxs-lookup"><span data-stu-id="e02fd-137">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="V terminálu se zobrazí Hello World!":::

1. <span data-ttu-id="e02fd-139">Zavřete okno **terminálu** .</span><span class="sxs-lookup"><span data-stu-id="e02fd-139">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="e02fd-140">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="e02fd-140">Enhance the app</span></span>

<span data-ttu-id="e02fd-141">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="e02fd-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="e02fd-142">V *program.cs*nahraďte obsah `Main` metody, což je řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e02fd-142">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   <span data-ttu-id="e02fd-143">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="e02fd-143">This code displays "What is your name?"</span></span> <span data-ttu-id="e02fd-144">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="e02fd-144">in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="e02fd-145">Tento řetězec je uložen v proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="e02fd-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="e02fd-146">Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` .</span><span class="sxs-lookup"><span data-stu-id="e02fd-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e02fd-147">Nakonec tyto hodnoty zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e02fd-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="e02fd-148">`\n`Představuje znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="e02fd-148">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="e02fd-149">Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="e02fd-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="e02fd-150">Hodnota výrazu je vložena do řetězce místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="e02fd-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="e02fd-151">Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="e02fd-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="e02fd-152">Spusťte aplikaci stisknutím <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>ENTER</kbd>).</span><span class="sxs-lookup"><span data-stu-id="e02fd-152">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="e02fd-153">Zadáním názvu a stisknutím klávesy <kbd>ENTER</kbd>odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="e02fd-153">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminál zobrazuje upravený výstup programu":::

1. <span data-ttu-id="e02fd-155">Zavřete terminál.</span><span class="sxs-lookup"><span data-stu-id="e02fd-155">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e02fd-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e02fd-156">Next steps</span></span>

<span data-ttu-id="e02fd-157">V tomto kurzu jste vytvořili konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e02fd-157">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="e02fd-158">V dalším kurzu ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e02fd-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e02fd-159">Ladění konzolové aplikace .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e02fd-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio-mac.md)
