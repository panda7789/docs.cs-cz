---
title: Vytvoření aplikace Hello World s rozhraním .NET Core v sadě Visual Studio
description: Zjistěte, jak vytvořit první aplikaci konzoly .NET Core pomocí jazyka C# nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714002"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="e5475-103">Kurz: Vytvoření první aplikace konzoly .NET Core ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="e5475-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="e5475-104">Tento článek obsahuje podrobný úvod k vytvoření a spuštění aplikace konzoly Hello World .NET Core v sadě Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e5475-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="e5475-105">Aplikace Hello World se tradičně používá k zavedení začátečníků do nového programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="e5475-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="e5475-106">Tento program jednoduše zobrazuje frázi "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e5475-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="e5475-107">.</span><span class="sxs-lookup"><span data-stu-id="e5475-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5475-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5475-108">Prerequisites</span></span>

- <span data-ttu-id="e5475-109">[Visual Studio 2019 verze 16.4 nebo novější verze](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou **úlohou pro vývoj napříč platformami .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e5475-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="e5475-110">Sada .NET Core 3.1 SDK se automaticky nainstaluje, když vyberete tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="e5475-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="e5475-111">Další informace naleznete v části [Instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku Instalace [jádra .NET SDK.](../install/sdk.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="e5475-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="e5475-112">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="e5475-112">Create the app</span></span>

<span data-ttu-id="e5475-113">Následující pokyny vytvořit jednoduchou aplikaci Hello World konzoly:</span><span class="sxs-lookup"><span data-stu-id="e5475-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e5475-114">C #</span><span class="sxs-lookup"><span data-stu-id="e5475-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e5475-115">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e5475-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e5475-116">Vytvořte nový projekt konzoly C# .NET Core s názvem "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e5475-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e5475-117">V počátečním okně zvolte **Vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e5475-117">On the start window, choose **Create a new project**.</span></span>

      ![Vytvoření nového tlačítka projektu vybraného v počátečním okně sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e5475-119">Na stránce **Vytvořit nový projekt** zadejte **konzolu** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="e5475-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e5475-120">Dále zvolte **C#** ze seznamu jazyk a pak zvolte **všechny platformy** ze seznamu Platform.</span><span class="sxs-lookup"><span data-stu-id="e5475-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e5475-121">Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="e5475-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Vytvoření nového okna projektu s vybranými filtry](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e5475-123">Pokud nevidíte šablony .NET Core, pravděpodobně vám chybí nainstalované požadované zatížení.</span><span class="sxs-lookup"><span data-stu-id="e5475-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e5475-124">V části **Install more tools and features** **Nenajít to, co hledáte?**</span><span class="sxs-lookup"><span data-stu-id="e5475-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e5475-125">Otevře se instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5475-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e5475-126">Ujistěte se, že máte nainstalovanou **úlohu pro vývoj napříč platformami .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e5475-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e5475-127">Na stránce **Konfigurace nového projektu** zadejte **HelloWorld** do pole **Název projektu.**</span><span class="sxs-lookup"><span data-stu-id="e5475-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e5475-128">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e5475-128">Then, choose **Create**.</span></span>

      ![Konfigurace nového okna projektu s poli Název projektu, umístění a název řešení](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="e5475-130">Šablona aplikace konzoly Jazyka C# pro .NET Core automaticky definuje třídu , `Program`s jedinou metodou , `Main`která bere <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="e5475-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e5475-131">`Main`je vstupní bod aplikace, metoda, která je volána automaticky runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5475-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e5475-132">Všechny argumenty příkazového řádku zadané při spuštění aplikace jsou k dispozici v poli *args.*</span><span class="sxs-lookup"><span data-stu-id="e5475-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="e5475-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5475-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e5475-135">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e5475-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e5475-136">Vytvořte nový projekt konzoly Jazyka .NET Core s názvem "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e5475-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e5475-137">V počátečním okně zvolte **Vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e5475-137">On the start window, choose **Create a new project**.</span></span>

      ![Vytvoření nového tlačítka projektu vybraného v počátečním okně sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e5475-139">Na stránce **Vytvořit nový projekt** zadejte **konzolu** do vyhledávacího pole.</span><span class="sxs-lookup"><span data-stu-id="e5475-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e5475-140">Dále zvolte **Visual Basic** ze seznamu Jazyk a pak ze seznamu Platforma zvolte **Všechny platformy.**</span><span class="sxs-lookup"><span data-stu-id="e5475-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e5475-141">Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="e5475-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Volba šablony jazyka Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e5475-143">Pokud nevidíte šablony .NET Core, pravděpodobně vám chybí nainstalované požadované zatížení.</span><span class="sxs-lookup"><span data-stu-id="e5475-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e5475-144">V části **Install more tools and features** **Nenajít to, co hledáte?**</span><span class="sxs-lookup"><span data-stu-id="e5475-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e5475-145">Otevře se instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5475-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e5475-146">Ujistěte se, že máte nainstalovanou **úlohu pro vývoj napříč platformami .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e5475-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e5475-147">Na stránce **Konfigurace nového projektu** zadejte **HelloWorld** do pole **Název projektu.**</span><span class="sxs-lookup"><span data-stu-id="e5475-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e5475-148">Potom zvolte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e5475-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="e5475-149">Šablona konzolové aplikace pro rozhraní .NET `Program`Core automaticky definuje `Main`třídu <xref:System.String> , pomocí jediné metody , která bere pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="e5475-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e5475-150">`Main`je vstupní bod aplikace, metoda, která je volána automaticky runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5475-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e5475-151">Všechny argumenty příkazového řádku zadané při spuštění `args` aplikace jsou k dispozici v parametru.</span><span class="sxs-lookup"><span data-stu-id="e5475-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio a nový projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="e5475-153">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e5475-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="e5475-154">Volá metodu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pro zobrazení literálu řetězec "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e5475-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="e5475-155">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="e5475-156">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e5475-156">Run the app</span></span>

1. <span data-ttu-id="e5475-157">Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="e5475-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Panel nástrojů Sady Visual Studio s vybraným tlačítkem Spustit HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="e5475-159">Otevře se okno konzoly s textem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e5475-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="e5475-160">vytištěny na obrazovce a některé informace o ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5475-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konzoly zobrazující Hello World Stisknutím libovolné klávesy pokračujte](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="e5475-162">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="e5475-163">Vylepšete aplikaci</span><span class="sxs-lookup"><span data-stu-id="e5475-163">Enhance the app</span></span>

<span data-ttu-id="e5475-164">Vylepšete svou aplikaci tak, aby se uživateli vyzývala k zadání jeho jména a zobrazila ji spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="e5475-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="e5475-165">Následující pokyny upravte a spusťte aplikaci znovu:</span><span class="sxs-lookup"><span data-stu-id="e5475-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="e5475-166">C #</span><span class="sxs-lookup"><span data-stu-id="e5475-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e5475-167">Nahraďte obsah `Main` metody, která je aktuálně pouze `Console.WriteLine`řádek, který volá , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e5475-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="e5475-168">Tento kód zobrazuje "Jaké je vaše jméno?"</span><span class="sxs-lookup"><span data-stu-id="e5475-168">This code displays "What is your name?"</span></span> <span data-ttu-id="e5475-169">v okně konzoly a čeká, až uživatel zadá řetězec následovaný klávesou Enter.</span><span class="sxs-lookup"><span data-stu-id="e5475-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e5475-170">Ukládá tento řetězec do `name`proměnné s názvem .</span><span class="sxs-lookup"><span data-stu-id="e5475-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e5475-171">Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji proměnné s názvem `date`.</span><span class="sxs-lookup"><span data-stu-id="e5475-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e5475-172">Nakonec používá [interpolovaný řetězec](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e5475-173">Zkompilujte program výběrem **možnosti Sestavení** > **sestavení řešení**.</span><span class="sxs-lookup"><span data-stu-id="e5475-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e5475-174">Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="e5475-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e5475-175">Na výzvu odpovíte zadáním názvu a stisknutím klávesy **Enter.**</span><span class="sxs-lookup"><span data-stu-id="e5475-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e5475-177">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="e5475-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5475-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e5475-179">Nahraďte obsah `Main` metody, která je aktuálně pouze `Console.WriteLine`řádek, který volá , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e5475-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="e5475-180">Tento kód zobrazuje "Jaké je vaše jméno?"</span><span class="sxs-lookup"><span data-stu-id="e5475-180">This code displays "What is your name?"</span></span> <span data-ttu-id="e5475-181">v okně konzoly a čeká, až uživatel zadá řetězec následovaný klávesou Enter.</span><span class="sxs-lookup"><span data-stu-id="e5475-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e5475-182">Ukládá tento řetězec do `name`proměnné s názvem .</span><span class="sxs-lookup"><span data-stu-id="e5475-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e5475-183">Také načte hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji proměnné s názvem `date`.</span><span class="sxs-lookup"><span data-stu-id="e5475-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e5475-184">Nakonec používá [interpolovaný řetězec](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e5475-185">Zkompilujte program výběrem **možnosti Sestavení** > **sestavení řešení**.</span><span class="sxs-lookup"><span data-stu-id="e5475-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e5475-186">Chcete-li program spustit, zvolte **helloworld** na panelu nástrojů nebo stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="e5475-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e5475-187">Na výzvu odpovíte zadáním názvu a stisknutím klávesy **Enter.**</span><span class="sxs-lookup"><span data-stu-id="e5475-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e5475-189">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e5475-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="e5475-190">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e5475-190">Next steps</span></span>

<span data-ttu-id="e5475-191">V tomto článku jste vytvořili a spusťte první aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5475-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="e5475-192">V dalším kroku ladíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5475-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e5475-193">Ladění aplikace .NET Core Hello World v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5475-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
