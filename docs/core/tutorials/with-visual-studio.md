---
title: Vytvoření konzolové aplikace pomocí .NET Core v aplikaci Visual Studio
description: Naučte se, jak vytvořit konzolovou aplikaci .NET Core pomocí jazyka C# nebo Visual Basic pomocí sady Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201589"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="4672e-103">Kurz: Vytvoření konzolové aplikace .NET Core v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4672e-103">Tutorial: Create a .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="4672e-104">V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="4672e-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4672e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4672e-105">Prerequisites</span></span>

- <span data-ttu-id="4672e-106">[Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="4672e-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="4672e-107">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="4672e-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="4672e-108">Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="4672e-108">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4672e-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="4672e-109">Create the app</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="4672e-110">Otevřete Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="4672e-110">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="4672e-111">Vytvořte nový projekt konzolové aplikace .NET Core s názvem HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="4672e-111">Create a new .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="4672e-112">Na úvodní stránce vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="4672e-112">On the start page, choose **Create a new project**.</span></span>

      ![Tlačítko vytvořit nový projekt vybráno na úvodní stránce sady Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="4672e-114">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="4672e-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="4672e-115">Dále v seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="4672e-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="4672e-116">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="4672e-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Vytvoří nové okno projektu s vybranými filtry.](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="4672e-118">Pokud nevidíte šablony .NET Core, pravděpodobně nebudete mít k dispozici požadované úlohy.</span><span class="sxs-lookup"><span data-stu-id="4672e-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="4672e-119">V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .</span><span class="sxs-lookup"><span data-stu-id="4672e-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="4672e-120">Otevře se Instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4672e-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="4672e-121">Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="4672e-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="4672e-122">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** .</span><span class="sxs-lookup"><span data-stu-id="4672e-122">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="4672e-123">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="4672e-123">Then choose **Create**.</span></span>

      ![Konfigurovat nové okno projektu s názvem projektu, umístěním a poli s názvem řešení](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="4672e-125">Šablona konzolové aplikace pro .NET Core definuje třídu `Program` s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument.</span><span class="sxs-lookup"><span data-stu-id="4672e-125">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="4672e-126">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4672e-126">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4672e-127">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .</span><span class="sxs-lookup"><span data-stu-id="4672e-127">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   <span data-ttu-id="4672e-128">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="4672e-128">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   <span data-ttu-id="4672e-129">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="4672e-129">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="4672e-130">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4672e-130">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="4672e-131">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4672e-131">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4672e-132">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4672e-132">Run the app</span></span>

1. <span data-ttu-id="4672e-133">Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="4672e-133">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybraným tlačítkem spustit v HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="4672e-135">Otevře se okno konzoly s textem "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="4672e-135">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="4672e-136">vytištěno na obrazovce a některé informace o ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4672e-136">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="4672e-138">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4672e-138">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="4672e-139">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="4672e-139">Enhance the app</span></span>

<span data-ttu-id="4672e-140">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="4672e-140">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="4672e-141">Následující pokyny upraví aplikaci a znovu ji spusťte:</span><span class="sxs-lookup"><span data-stu-id="4672e-141">The following instructions modify the app and run it again:</span></span>

1. <span data-ttu-id="4672e-142">Nahraďte obsah `Main` metody, která je aktuálně pouze řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4672e-142">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   <span data-ttu-id="4672e-143">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="4672e-143">This code displays "What is your name?"</span></span> <span data-ttu-id="4672e-144">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou ENTER.</span><span class="sxs-lookup"><span data-stu-id="4672e-144">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="4672e-145">Tento řetězec je uložen v proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="4672e-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4672e-146">Načte také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` ( `currentDate` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4672e-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="4672e-147">Nakonec tyto hodnoty zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4672e-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="4672e-148">`\n`( `vbCrLf` V Visual Basic) představuje znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="4672e-148">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="4672e-149">Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="4672e-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4672e-150">Hodnota výrazu je vložena do řetězce místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="4672e-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4672e-151">Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4672e-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4672e-152">Chcete-li spustit program, zvolte **HelloWorld** na panelu nástrojů nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="4672e-152">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="4672e-153">Zadáním názvu a stisknutím klávesy **ENTER** odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="4672e-153">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="4672e-155">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4672e-155">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4672e-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4672e-156">Next steps</span></span>

<span data-ttu-id="4672e-157">V tomto kurzu jste vytvořili aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4672e-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="4672e-158">V dalším kurzu ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4672e-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4672e-159">Ladění konzolové aplikace .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4672e-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
