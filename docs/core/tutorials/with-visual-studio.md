---
title: Vytvoření aplikace Hello World pomocí .NET Core v aplikaci Visual Studio
description: Naučte se, jak vytvořit první konzolovou aplikaci .NET Core pomocí C# nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394830"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="e99bb-103">Kurz: Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e99bb-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="e99bb-104">Tento článek popisuje podrobný Úvod k vytvoření a spuštění Hello World konzolové aplikace .NET Core v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e99bb-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="e99bb-105">Aplikace Hello World se tradičně používá k zavedení začátečníků do nového programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="e99bb-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="e99bb-106">Tento program jednoduše zobrazí frázi "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e99bb-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="e99bb-107">.</span><span class="sxs-lookup"><span data-stu-id="e99bb-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e99bb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e99bb-108">Prerequisites</span></span>

- <span data-ttu-id="e99bb-109">[Visual Studio 2019 verze 16,4 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="e99bb-110">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="e99bb-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="e99bb-111">Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="e99bb-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="e99bb-112">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="e99bb-112">Create the app</span></span>

<span data-ttu-id="e99bb-113">V následujících pokynech je vytvořená jednoduchá Hello World Konzolová aplikace:</span><span class="sxs-lookup"><span data-stu-id="e99bb-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e99bb-114">C#</span><span class="sxs-lookup"><span data-stu-id="e99bb-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e99bb-115">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e99bb-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e99bb-116">Vytvořte nový projekt konzolové aplikace C# .NET Core s názvem HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="e99bb-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e99bb-117">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-117">On the start window, choose **Create a new project**.</span></span>

      ![Tlačítko vytvořit nový projekt vybráno v okně Start sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e99bb-119">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e99bb-120">Potom v seznamu jazyk vyberte **C#** a pak v seznamu platforma zvolte **všechny platformy** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e99bb-121">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Vytvoří nové okno projektu s vybranými filtry.](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e99bb-123">Pokud nevidíte šablony .NET Core, pravděpodobně nemáte nainstalovanou požadovanou úlohu.</span><span class="sxs-lookup"><span data-stu-id="e99bb-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e99bb-124">V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e99bb-125">Otevře se Instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e99bb-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e99bb-126">Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e99bb-127">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e99bb-128">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-128">Then, choose **Create**.</span></span>

      ![Konfigurovat nové okno projektu s názvem projektu, umístěním a poli s názvem řešení](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="e99bb-130">Šablona konzolové aplikace v jazyce C# pro .NET Core automaticky definuje třídu `Program` s jedinou metodou, `Main` která <xref:System.String> jako argument přijímá pole.</span><span class="sxs-lookup"><span data-stu-id="e99bb-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e99bb-131">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e99bb-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e99bb-132">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .</span><span class="sxs-lookup"><span data-stu-id="e99bb-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio a nový HelloWorld projekt](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="e99bb-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e99bb-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e99bb-135">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e99bb-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e99bb-136">Vytvořte nový Visual Basic projekt konzolové aplikace .NET Core s názvem "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e99bb-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e99bb-137">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-137">On the start window, choose **Create a new project**.</span></span>

      ![Tlačítko vytvořit nový projekt vybráno v okně Start sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e99bb-139">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e99bb-140">Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **všechny platformy** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e99bb-141">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Zvolit šablonu Visual Basic pro konzolovou aplikaci (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e99bb-143">Pokud nevidíte šablony .NET Core, pravděpodobně nemáte nainstalovanou požadovanou úlohu.</span><span class="sxs-lookup"><span data-stu-id="e99bb-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e99bb-144">V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e99bb-145">Otevře se Instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e99bb-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e99bb-146">Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e99bb-147">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** .</span><span class="sxs-lookup"><span data-stu-id="e99bb-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e99bb-148">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="e99bb-149">Šablona konzolové aplikace pro .NET Core automaticky definuje třídu `Program` s jedinou metodou, `Main` která <xref:System.String> jako argument přijímá pole.</span><span class="sxs-lookup"><span data-stu-id="e99bb-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e99bb-150">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e99bb-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e99bb-151">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v `args` parametru.</span><span class="sxs-lookup"><span data-stu-id="e99bb-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio a nový HelloWorld projekt](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="e99bb-153">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e99bb-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="e99bb-154">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e99bb-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="e99bb-155">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="e99bb-156">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e99bb-156">Run the app</span></span>

1. <span data-ttu-id="e99bb-157">Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybraným tlačítkem spustit v HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="e99bb-159">Otevře se okno konzoly s textem "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="e99bb-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="e99bb-160">vytištěno na obrazovce a některé informace o ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e99bb-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="e99bb-162">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="e99bb-163">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="e99bb-163">Enhance the app</span></span>

<span data-ttu-id="e99bb-164">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="e99bb-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="e99bb-165">Následující pokyny upravují a spouštějí aplikaci znovu:</span><span class="sxs-lookup"><span data-stu-id="e99bb-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="e99bb-166">C#</span><span class="sxs-lookup"><span data-stu-id="e99bb-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e99bb-167">Nahraďte obsah `Main` metody, která je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e99bb-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   <span data-ttu-id="e99bb-168">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="e99bb-168">This code displays "What is your name?"</span></span> <span data-ttu-id="e99bb-169">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER.</span><span class="sxs-lookup"><span data-stu-id="e99bb-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e99bb-170">Tento řetězec je uložen do proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="e99bb-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e99bb-171">Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` .</span><span class="sxs-lookup"><span data-stu-id="e99bb-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e99bb-172">Nakonec používá [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e99bb-173">Zkompilujte program tím, že kliknete na **sestavit**sestavení  >  **řešení**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e99bb-174">Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e99bb-175">Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="e99bb-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e99bb-177">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="e99bb-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e99bb-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e99bb-179">Nahraďte obsah `Main` metody, která je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e99bb-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="e99bb-180">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="e99bb-180">This code displays "What is your name?"</span></span> <span data-ttu-id="e99bb-181">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER.</span><span class="sxs-lookup"><span data-stu-id="e99bb-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e99bb-182">Tento řetězec je uložen do proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="e99bb-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e99bb-183">Načítá také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` .</span><span class="sxs-lookup"><span data-stu-id="e99bb-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e99bb-184">Nakonec používá [interpolované řetězce](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) k zobrazení těchto hodnot v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e99bb-185">Zkompilujte program tím, že kliknete na **sestavit**sestavení  >  **řešení**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e99bb-186">Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="e99bb-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e99bb-187">Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="e99bb-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e99bb-189">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="e99bb-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="e99bb-190">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e99bb-190">Next steps</span></span>

<span data-ttu-id="e99bb-191">V tomto článku jste vytvořili a spustili svou první aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e99bb-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="e99bb-192">V dalším kroku budete ladit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e99bb-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e99bb-193">Ladění aplikace Hello World .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e99bb-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
