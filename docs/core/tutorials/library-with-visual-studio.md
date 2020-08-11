---
title: Vytvoření .NET Standard knihovny tříd pomocí sady Visual Studio
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí sady Visual Studio.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: contperfq1
ms.openlocfilehash: 5bd853c62a44d2160bd222d76adcd2dc34d42efc
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88075485"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="76cdf-103">Kurz: Vytvoření knihovny .NET Standard pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76cdf-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="76cdf-104">V tomto kurzu vytvoříte jednoduchou knihovnu tříd, která obsahuje jedinou metodu zpracování řetězce.</span><span class="sxs-lookup"><span data-stu-id="76cdf-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="76cdf-105">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="76cdf-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="76cdf-106">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="76cdf-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="76cdf-107">Po dokončení knihovny tříd ji můžete distribuovat jako balíček NuGet nebo jako součást, která je součástí aplikace, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="76cdf-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76cdf-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76cdf-108">Prerequisites</span></span>

- <span data-ttu-id="76cdf-109">[Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="76cdf-110">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="76cdf-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="76cdf-111">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="76cdf-111">Create a solution</span></span>

<span data-ttu-id="76cdf-112">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="76cdf-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="76cdf-113">Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="76cdf-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="76cdf-114">Do stejného řešení přidáte další související projekty.</span><span class="sxs-lookup"><span data-stu-id="76cdf-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="76cdf-115">Vytvoření prázdného řešení:</span><span class="sxs-lookup"><span data-stu-id="76cdf-115">To create the blank solution:</span></span>

1. <span data-ttu-id="76cdf-116">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76cdf-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="76cdf-117">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="76cdf-118">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="76cdf-119">Zvolte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Prázdná šablona řešení v aplikaci Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="76cdf-121">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **ClassLibraryProjects** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="76cdf-122">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="76cdf-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="76cdf-123">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="76cdf-123">Create a class library project</span></span>

1. <span data-ttu-id="76cdf-124">Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="76cdf-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="76cdf-125">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="76cdf-126">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="76cdf-127">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="76cdf-128">Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="76cdf-129">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="76cdf-130">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="76cdf-131">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="76cdf-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="76cdf-132">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="76cdf-133">Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="76cdf-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="76cdf-135">Pokud používáte Visual Basic, vymažte text v textovém poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="76cdf-137">Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="76cdf-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="76cdf-138">V tomto kurzu definujete obor názvů nejvyšší úrovně pomocí [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) klíčového slova v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="76cdf-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="76cdf-139">Nahraďte kód v okně Code pro *Class1.cs* nebo *Class1. vb* následujícím kódem a uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="76cdf-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="76cdf-140">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="76cdf-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="76cdf-141">Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="76cdf-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="76cdf-142">Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="76cdf-143">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="76cdf-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="76cdf-144"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="76cdf-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="76cdf-145">`StartsWithUpper`je implementován jako [metoda rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete volat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="76cdf-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="76cdf-146">Na panelu nabídek vyberte **sestavit**  >  **sestavení řešení** a ověřte, že se projekt zkompiluje bez chyby.</span><span class="sxs-lookup"><span data-stu-id="76cdf-146">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="76cdf-147">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="76cdf-147">Add a console app to the solution</span></span>

<span data-ttu-id="76cdf-148">Přidejte konzolovou aplikaci, která používá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="76cdf-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="76cdf-149">Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="76cdf-150">Do řešení přidejte novou konzolovou aplikaci .NET Core s názvem prezentující.</span><span class="sxs-lookup"><span data-stu-id="76cdf-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="76cdf-151">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="76cdf-152">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="76cdf-153">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="76cdf-154">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="76cdf-155">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **prezentující** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="76cdf-156">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="76cdf-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="76cdf-157">V okně kódu pro soubor *program.cs* nebo *program. vb* nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="76cdf-158">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="76cdf-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="76cdf-159">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="76cdf-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="76cdf-160">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="76cdf-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="76cdf-161">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="76cdf-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="76cdf-162">Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="76cdf-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="76cdf-163">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="76cdf-163">Add a project reference</span></span>

<span data-ttu-id="76cdf-164">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="76cdf-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="76cdf-165">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="76cdf-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="76cdf-166">V **Průzkumník řešení**klikněte pravým tlačítkem myši na `ShowCase` uzel **závislosti** projektu a vyberte možnost **Přidat odkaz na projekt**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Přidat kontextovou nabídku odkazu v aplikaci Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="76cdf-168">V dialogovém okně **Správce odkazů** vyberte projekt **StringLibrary** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="76cdf-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Dialog Správce odkazů s vybraným StringLibrary](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="76cdf-170">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="76cdf-170">Run the app</span></span>

1. <span data-ttu-id="76cdf-171">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="76cdf-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="76cdf-173">Stisknutím klávesy <kbd>CTRL</kbd> + <kbd>F5</kbd> zkompilujete a spustíte program bez ladění.</span><span class="sxs-lookup"><span data-stu-id="76cdf-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="76cdf-175">Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.</span><span class="sxs-lookup"><span data-stu-id="76cdf-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konzoly s předvedením":::

## <a name="additional-resources"></a><span data-ttu-id="76cdf-177">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="76cdf-177">Additional resources</span></span>

* [<span data-ttu-id="76cdf-178">Vývoj knihoven pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="76cdf-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="76cdf-179">[.NET Standard verze a podporované platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="76cdf-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="76cdf-180">Další kroky</span><span class="sxs-lookup"><span data-stu-id="76cdf-180">Next steps</span></span>

<span data-ttu-id="76cdf-181">V tomto kurzu jste vytvořili knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="76cdf-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="76cdf-182">V dalším kurzu se dozvíte, jak jednotkové testování knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="76cdf-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76cdf-183">Testování částí .NET Standard knihovny pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76cdf-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="76cdf-184">Nebo můžete přeskočit automatizované testování částí a zjistit, jak knihovnu nasdílet vytvořením balíčku NuGet:</span><span class="sxs-lookup"><span data-stu-id="76cdf-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76cdf-185">Vytvoření a publikování balíčku pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76cdf-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="76cdf-186">Nebo se dozvíte, jak publikovat konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="76cdf-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="76cdf-187">Pokud publikujete konzolovou aplikaci z řešení, které jste vytvořili v tomto kurzu, do knihovny tříd přejdete jako soubor *. dll* .</span><span class="sxs-lookup"><span data-stu-id="76cdf-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76cdf-188">Publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76cdf-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
