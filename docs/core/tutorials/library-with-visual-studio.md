---
title: Vytvoření .NET Standard knihovny tříd pomocí sady Visual Studio
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí sady Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701562"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="1d71c-103">Kurz: Vytvoření knihovny .NET Standard pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d71c-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="1d71c-104">V tomto kurzu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="1d71c-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="1d71c-105">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d71c-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="1d71c-106">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="1d71c-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="1d71c-107">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1d71c-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="1d71c-108">Po dokončení knihovny tříd ji můžete distribuovat jako součást třetí strany nebo jako součást balíčku s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="1d71c-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d71c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d71c-109">Prerequisites</span></span>

- <span data-ttu-id="1d71c-110">[Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="1d71c-111">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="1d71c-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="1d71c-112">Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="1d71c-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="1d71c-113">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="1d71c-113">Create a solution</span></span>

<span data-ttu-id="1d71c-114">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="1d71c-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="1d71c-115">Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="1d71c-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="1d71c-116">Do stejného řešení přidáte další související projekty.</span><span class="sxs-lookup"><span data-stu-id="1d71c-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="1d71c-117">Vytvoření prázdného řešení:</span><span class="sxs-lookup"><span data-stu-id="1d71c-117">To create the blank solution:</span></span>

1. <span data-ttu-id="1d71c-118">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d71c-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="1d71c-119">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="1d71c-120">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="1d71c-121">Zvolte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Prázdná šablona řešení v aplikaci Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="1d71c-123">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **ClassLibraryProjects** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="1d71c-124">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="1d71c-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="1d71c-125">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="1d71c-125">Create a class library project</span></span>

1. <span data-ttu-id="1d71c-126">Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="1d71c-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="1d71c-127">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="1d71c-128">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="1d71c-129">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="1d71c-130">Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="1d71c-131">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="1d71c-132">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="1d71c-133">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1d71c-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="1d71c-134">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="1d71c-135">Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="1d71c-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="1d71c-137">Pokud používáte Visual Basic, vymažte text v textovém poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="1d71c-139">Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="1d71c-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="1d71c-140">V tomto kurzu definujete obor názvů nejvyšší úrovně pomocí [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) klíčového slova v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="1d71c-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="1d71c-141">Nahraďte kód v okně Code pro *Class1.cs* nebo *Class1. vb* následujícím kódem a uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="1d71c-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="1d71c-142">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="1d71c-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="1d71c-143">Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="1d71c-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="1d71c-144">Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="1d71c-145">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="1d71c-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="1d71c-146"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="1d71c-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="1d71c-147">Na panelu nabídek vyberte **sestavit**  >  **sestavení řešení** a ověřte, že se projekt zkompiluje bez chyby.</span><span class="sxs-lookup"><span data-stu-id="1d71c-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="1d71c-148">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="1d71c-148">Add a console app to the solution</span></span>

<span data-ttu-id="1d71c-149">Přidejte konzolovou aplikaci, která používá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="1d71c-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="1d71c-150">Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="1d71c-151">Do řešení přidejte novou konzolovou aplikaci .NET Core s názvem prezentující.</span><span class="sxs-lookup"><span data-stu-id="1d71c-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="1d71c-152">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="1d71c-153">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="1d71c-154">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="1d71c-155">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="1d71c-156">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **prezentující** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="1d71c-157">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="1d71c-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="1d71c-158">V okně kódu pro soubor *program.cs* nebo *program. vb* nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="1d71c-159">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="1d71c-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="1d71c-160">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="1d71c-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="1d71c-161">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d71c-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="1d71c-162">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="1d71c-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="1d71c-163">Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="1d71c-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="1d71c-164">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="1d71c-164">Add a project reference</span></span>

<span data-ttu-id="1d71c-165">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="1d71c-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="1d71c-166">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="1d71c-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="1d71c-167">V **Průzkumník řešení**klikněte pravým tlačítkem myši na `ShowCase` uzel **závislosti** projektu a vyberte možnost **Přidat odkaz na projekt**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Přidat kontextovou nabídku odkazu v aplikaci Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="1d71c-169">V dialogovém okně **Správce odkazů** vyberte projekt **StringLibrary** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1d71c-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Dialog Správce odkazů s vybraným StringLibrary](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="1d71c-171">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="1d71c-171">Run the app</span></span>

1. <span data-ttu-id="1d71c-172">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="1d71c-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="1d71c-174">Stisknutím klávesy <kbd>SHIFT</kbd> + <kbd>F5</kbd> zkompilujete a spustíte program bez ladění.</span><span class="sxs-lookup"><span data-stu-id="1d71c-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="1d71c-176">Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.</span><span class="sxs-lookup"><span data-stu-id="1d71c-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konzoly s předvedením":::

## <a name="additional-resources"></a><span data-ttu-id="1d71c-178">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1d71c-178">Additional resources</span></span>

* [<span data-ttu-id="1d71c-179">Vývoj knihoven pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="1d71c-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="1d71c-180">[.NET Standard verze a podporované platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="1d71c-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1d71c-181">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1d71c-181">Next steps</span></span>

<span data-ttu-id="1d71c-182">V tomto kurzu jste vytvořili řešení, přidali projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="1d71c-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="1d71c-183">V dalším kurzu přidáte do řešení projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="1d71c-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d71c-184">Testování knihovny .NET Standard pomocí .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d71c-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
