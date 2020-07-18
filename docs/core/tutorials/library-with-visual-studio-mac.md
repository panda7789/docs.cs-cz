---
title: Vytvoření .NET Standard knihovny tříd pomocí Visual Studio pro Mac
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí Visual Studio pro Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 8e1e4ca3bc1b12d889b847d80318f3d6cd1bbe46
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416006"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="cd305-103">Kurz: Vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="cd305-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="cd305-104">V tomto kurzu vytvoříte knihovnu tříd, která obsahuje jedinou metodu zpracování řetězce.</span><span class="sxs-lookup"><span data-stu-id="cd305-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span> <span data-ttu-id="cd305-105">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="cd305-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="cd305-106">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="cd305-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="cd305-107">Knihovna tříd, která cílí na .NET Standard 2,1, může být použita aplikací, která cílí na jakoukoli implementaci rozhraní .NET, která podporuje .NET Standard verze 2,1.</span><span class="sxs-lookup"><span data-stu-id="cd305-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="cd305-108">Po dokončení knihovny tříd ji můžete distribuovat jako součást třetí strany nebo jako součást balíčku s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="cd305-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="cd305-109">Vaše zpětná vazba je vysoce ohodnocená.</span><span class="sxs-lookup"><span data-stu-id="cd305-109">Your feedback is highly valued.</span></span> <span data-ttu-id="cd305-110">Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:</span><span class="sxs-lookup"><span data-stu-id="cd305-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="cd305-111">V Visual Studio pro Mac vyberte v nabídce **nápovědu**  >  **nahlásit problém** nebo **nahlásit problém** z úvodní obrazovky, která otevře okno pro podání zprávy o chybě.</span><span class="sxs-lookup"><span data-stu-id="cd305-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="cd305-112">Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).</span><span class="sxs-lookup"><span data-stu-id="cd305-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="cd305-113">Chcete-li vytvořit návrh, vyberte v nabídce **možnost**  >  **poskytnout návrh** nebo **Poskytněte návrh** z úvodní obrazovky, který vás přesměruje na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="cd305-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd305-114">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="cd305-114">Prerequisites</span></span>

* <span data-ttu-id="cd305-115">[Nainstalujte Visual Studio pro Mac verze 8,6 nebo novější](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="cd305-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="cd305-116">Vyberte možnost instalace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd305-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="cd305-117">Instalace Xamarin je volitelná pro vývoj v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd305-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="cd305-118">Další informace naleznete v následujících zdrojích:</span><span class="sxs-lookup"><span data-stu-id="cd305-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="cd305-119">[Kurz: instalace Visual Studio pro Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="cd305-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="cd305-120">[Podporované verze MacOS](../install/dependencies.md?pivots=os-macos)</span><span class="sxs-lookup"><span data-stu-id="cd305-120">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="cd305-121">[Verze .NET Core podporované nástrojem Visual Studio pro Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="cd305-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="cd305-122">Vytvoření řešení pomocí projektu knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="cd305-122">Create a solution with a class library project</span></span>

<span data-ttu-id="cd305-123">Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="cd305-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="cd305-124">Vytvořte řešení a projekt knihovny tříd v řešení.</span><span class="sxs-lookup"><span data-stu-id="cd305-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="cd305-125">Další související projekty přidáte do stejného řešení později.</span><span class="sxs-lookup"><span data-stu-id="cd305-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="cd305-126">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="cd305-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="cd305-127">V okně Start vyberte **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="cd305-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="cd305-128">V dialogovém okně **Nový projekt** pod uzlem **více platforem** vyberte možnost **knihovna**, vyberte šablonu **knihovny .NET Standard** a vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="cd305-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Dialog Nový projekt":::

1. <span data-ttu-id="cd305-130">V dialogovém okně **Konfigurovat novou knihovnu .NET Standard** zvolte .NET Standard 2,1 a vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="cd305-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Vyberte .NET Standard 2,1":::

1. <span data-ttu-id="cd305-132">Pojmenujte projekt "StringLibrary" a řešení "ClassLibraryProjects".</span><span class="sxs-lookup"><span data-stu-id="cd305-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="cd305-133">Ponechte položku **vytvořit adresář projektu v rámci vybraného adresáře řešení** .</span><span class="sxs-lookup"><span data-stu-id="cd305-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="cd305-134">Vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="cd305-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio pro Mac možnosti dialogového okna Nový projekt":::

1. <span data-ttu-id="cd305-136">V hlavní nabídce vyberte možnost **Zobrazit**panel  >  **Pads**  >  **řešení**a vyberte ikonu ukotvit, aby se panel otevřel.</span><span class="sxs-lookup"><span data-stu-id="cd305-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Ikona ukotvení pro panel řešení":::

1. <span data-ttu-id="cd305-138">Na panelu **řešení** rozbalte uzel, aby se zobrazil `StringLibrary` soubor třídy poskytnutý šablonou, *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd305-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="cd305-139"><kbd>podržte klávesu CTRL</kbd>a klikněte na soubor, v místní nabídce vyberte **Přejmenovat** a přejmenujte soubor na *StringLibrary.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd305-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="cd305-140">Otevřete soubor a nahraďte jeho obsah následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="cd305-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="cd305-141">Uložte soubor stisknutím <kbd>⌘</kbd><kbd>S</kbd> (<kbd>Commands</kbd> + <kbd>S</kbd>).</span><span class="sxs-lookup"><span data-stu-id="cd305-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="cd305-142">V dolní části okna IDE vyberte **chyby** a otevřete panel **chyby** .</span><span class="sxs-lookup"><span data-stu-id="cd305-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="cd305-143">Vyberte tlačítko **výstup sestavení** .</span><span class="sxs-lookup"><span data-stu-id="cd305-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Spodní okraj integrovaného vývojového prostředí (IDE) sady Visual Studio zobrazující tlačítko chyby":::

1. <span data-ttu-id="cd305-145">V nabídce vyberte **sestavit**  >  **vše** .</span><span class="sxs-lookup"><span data-stu-id="cd305-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="cd305-146">Řešení vytvoří.</span><span class="sxs-lookup"><span data-stu-id="cd305-146">The solution builds.</span></span> <span data-ttu-id="cd305-147">Na panelu výstup sestavení se zobrazí, že sestavení proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="cd305-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Podokno výstupu sestavení Mac sady Visual Studio na panelu chyby se zprávou úspěšné sestavení":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="cd305-149">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="cd305-149">Add a console app to the solution</span></span>

<span data-ttu-id="cd305-150">Přidejte konzolovou aplikaci, která používá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="cd305-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="cd305-151">Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="cd305-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="cd305-152">Na panelu **řešení** <kbd>stiskněte klávesu CTRL</kbd>a klikněte na `ClassLibraryProjects` řešení.</span><span class="sxs-lookup"><span data-stu-id="cd305-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="cd305-153">Přidejte nový projekt **konzolové aplikace** tak, že vyberete šablonu z šablon **webové a konzolové**  >  **aplikace** a kliknete na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="cd305-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="cd305-154">Jako **cílovou architekturu** vyberte **.NET Core 3,1** a vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="cd305-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="cd305-155">Pojmenujte si **prezentující**projekt.</span><span class="sxs-lookup"><span data-stu-id="cd305-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="cd305-156">Vyberte **vytvořit** a vytvořte projekt v řešení.</span><span class="sxs-lookup"><span data-stu-id="cd305-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Přidat projekt prezentace":::

1. <span data-ttu-id="cd305-158">Otevřete soubor *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="cd305-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="cd305-159">Nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="cd305-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="cd305-160">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="cd305-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="cd305-161">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="cd305-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="cd305-162">Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="cd305-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="cd305-163">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="cd305-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="cd305-164">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="cd305-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="cd305-165">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="cd305-165">Add a project reference</span></span>

<span data-ttu-id="cd305-166">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="cd305-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="cd305-167">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="cd305-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="cd305-168">Na panelu **řešení** <kbd>stiskněte CTRL</kbd>a klikněte na uzel **závislosti** nového projektu **prezentace** .</span><span class="sxs-lookup"><span data-stu-id="cd305-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="cd305-169">V místní nabídce vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="cd305-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="cd305-170">V dialogovém okně **odkazy** vyberte **StringLibrary** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd305-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="cd305-171">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="cd305-171">Run the app</span></span>

1. <span data-ttu-id="cd305-172"><kbd>stiskněte klávesu CTRL</kbd>a klikněte na projekt prezentace a v místní nabídce vyberte **spustit projekt** .</span><span class="sxs-lookup"><span data-stu-id="cd305-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="cd305-173">Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.</span><span class="sxs-lookup"><span data-stu-id="cd305-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Okno konzoly Visual Studio pro Mac znázorňující spuštěnou aplikaci":::

## <a name="additional-resources"></a><span data-ttu-id="cd305-175">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cd305-175">Additional resources</span></span>

* [<span data-ttu-id="cd305-176">Vývoj knihoven pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="cd305-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="cd305-177">[.NET Standard verze a podporované platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="cd305-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="cd305-178">Zpráva k vydání verze pro Visual Studio 2019 pro Mac</span><span class="sxs-lookup"><span data-stu-id="cd305-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="cd305-179">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cd305-179">Next steps</span></span>

<span data-ttu-id="cd305-180">V tomto kurzu jste vytvořili řešení a projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="cd305-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="cd305-181">V dalším kurzu přidáte do řešení projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="cd305-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cd305-182">Testování knihovny .NET Standard pomocí .NET Core s využitím Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="cd305-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
