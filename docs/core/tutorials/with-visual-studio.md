---
title: Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio
description: Naučte se, jak vytvořit konzolovou aplikaci .NET Core pomocí jazyka C# nebo Visual Basic pomocí sady Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: fbe0b3491260e787c08b98b320b19408f2c897eb
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795382"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="22784-103">Kurz: Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="22784-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="22784-104">V tomto kurzu se dozvíte, jak vytvořit a spustit konzolovou aplikaci .NET Core v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="22784-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22784-105">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="22784-105">Prerequisites</span></span>

- <span data-ttu-id="22784-106">[Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="22784-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="22784-107">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="22784-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="22784-108">Další informace najdete v tématu [instalace .NET Core SDK se sadou Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="22784-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="22784-109">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="22784-109">Create the app</span></span>

<span data-ttu-id="22784-110">Vytvořte projekt konzolové aplikace .NET Core s názvem HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="22784-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="22784-111">Spusťte Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="22784-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="22784-112">Na úvodní stránce vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="22784-112">On the start page, choose **Create a new project**.</span></span>

   ![Tlačítko vytvořit nový projekt vybráno na úvodní stránce sady Visual Studio](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="22784-114">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="22784-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="22784-115">Dále v seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="22784-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="22784-116">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="22784-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![Vytvoří nové okno projektu s vybranými filtry.](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="22784-118">Pokud nevidíte šablony .NET Core, pravděpodobně nebudete mít k dispozici požadované úlohy.</span><span class="sxs-lookup"><span data-stu-id="22784-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="22784-119">V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** .</span><span class="sxs-lookup"><span data-stu-id="22784-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="22784-120">Otevře se Instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22784-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="22784-121">Ujistěte se, že máte nainstalovanou úlohu **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="22784-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="22784-122">V dialogovém okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** .</span><span class="sxs-lookup"><span data-stu-id="22784-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="22784-123">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="22784-123">Then choose **Create**.</span></span>

   ![Konfigurovat nové okno projektu s názvem projektu, umístěním a poli s názvem řešení](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="22784-125">Šablona vytvoří jednoduchou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="22784-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="22784-126">Volá <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodu pro zobrazení "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="22784-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="22784-127">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="22784-127">in the console window.</span></span>

<span data-ttu-id="22784-128">Kód šablony definuje třídu, `Program` , s jedinou metodou, `Main` která přijímá <xref:System.String> pole jako argument:</span><span class="sxs-lookup"><span data-stu-id="22784-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="22784-129">`Main`je vstupním bodem aplikace, metodou, která je automaticky volána modulem runtime při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="22784-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="22784-130">Jakékoli argumenty příkazového řádku, které jsou zadány při spuštění aplikace, jsou k dispozici v poli *args* .</span><span class="sxs-lookup"><span data-stu-id="22784-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="22784-131">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="22784-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="22784-132">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="22784-132">Run the app</span></span>

1. <span data-ttu-id="22784-133">Stisknutím klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> spusťte program bez ladění.</span><span class="sxs-lookup"><span data-stu-id="22784-133">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="22784-134">Otevře se okno konzoly s textem "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="22784-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="22784-135">vytištěno na obrazovce a některé informace o ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22784-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konzoly zobrazující Hello World pro pokračování stiskněte libovolnou klávesu](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="22784-137">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="22784-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="22784-138">Vylepšení aplikace</span><span class="sxs-lookup"><span data-stu-id="22784-138">Enhance the app</span></span>

<span data-ttu-id="22784-139">Vylepšete aplikaci, aby se uživateli zobrazila výzva k zadání názvu a zobrazila se spolu s datem a časem.</span><span class="sxs-lookup"><span data-stu-id="22784-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="22784-140">V *program.cs* nebo *program. vb*nahraďte obsah `Main` metody, což je řádek, který volá `Console.WriteLine` , s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="22784-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="22784-141">Tento kód zobrazí "" Jaké je vaše jméno? "</span><span class="sxs-lookup"><span data-stu-id="22784-141">This code displays "What is your name?"</span></span> <span data-ttu-id="22784-142">v okně konzoly a počkejte, dokud uživatel nezadá řetězec následovaný klávesou <kbd>ENTER</kbd> .</span><span class="sxs-lookup"><span data-stu-id="22784-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="22784-143">Tento řetězec je uložen v proměnné s názvem `name` .</span><span class="sxs-lookup"><span data-stu-id="22784-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="22784-144">Načte také hodnotu <xref:System.DateTime.Now?displayProperty=nameWithType> vlastnosti, která obsahuje aktuální místní čas a přiřadí ji k proměnné s názvem `date` ( `currentDate` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="22784-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="22784-145">Nakonec tyto hodnoty zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="22784-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="22784-146">`\n`( `vbCrLf` V Visual Basic) představuje znak nového řádku.</span><span class="sxs-lookup"><span data-stu-id="22784-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="22784-147">Znak dolaru ( `$` ) před řetězcem umožňuje do složených závorek v řetězci vkládat výrazy, jako jsou názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="22784-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="22784-148">Hodnota výrazu je vložena do řetězce místo výrazu.</span><span class="sxs-lookup"><span data-stu-id="22784-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="22784-149">Tato syntaxe je označována jako [interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="22784-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="22784-150">Stisknutím klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> spusťte program bez ladění.</span><span class="sxs-lookup"><span data-stu-id="22784-150">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="22784-151">Zadáním názvu a stisknutím klávesy <kbd>ENTER</kbd> odpovězte na výzvu.</span><span class="sxs-lookup"><span data-stu-id="22784-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![Okno konzoly s upraveným výstupem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="22784-153">Stisknutím libovolné klávesy zavřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="22784-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="22784-154">Další kroky</span><span class="sxs-lookup"><span data-stu-id="22784-154">Next steps</span></span>

<span data-ttu-id="22784-155">V tomto kurzu jste vytvořili konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22784-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="22784-156">V dalším kurzu ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="22784-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22784-157">Ladění konzolové aplikace .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="22784-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
