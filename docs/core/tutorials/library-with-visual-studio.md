---
title: Vytvoření knihovny tříd .NET Standard v aplikaci Visual Studio
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí sady Visual Studio.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005234"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="30983-103">Kurz: Vytvoření knihovny .NET Standard v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30983-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="30983-104">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="30983-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="30983-105">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30983-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="30983-106">Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako součást třetí strany, nebo zda ji chcete zahrnout jako součást sady s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="30983-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="30983-107">Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="30983-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="30983-108">V tomto kurzu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="30983-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="30983-109">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="30983-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30983-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30983-110">Prerequisites</span></span>

- <span data-ttu-id="30983-111">[Visual Studio 2019 verze 16,6 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** .</span><span class="sxs-lookup"><span data-stu-id="30983-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="30983-112">Sada .NET Core 3,1 SDK se automaticky nainstaluje při výběru této úlohy.</span><span class="sxs-lookup"><span data-stu-id="30983-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="30983-113">Další informace najdete v části [instalace pomocí sady Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) v článku [instalace .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="30983-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="30983-114">Vytvoření řešení pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30983-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="30983-115">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="30983-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="30983-116">Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="30983-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="30983-117">Do stejného řešení přidáte další související projekty.</span><span class="sxs-lookup"><span data-stu-id="30983-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="30983-118">Vytvoření prázdného řešení:</span><span class="sxs-lookup"><span data-stu-id="30983-118">To create the blank solution:</span></span>

1. <span data-ttu-id="30983-119">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30983-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="30983-120">V okně Start vyberte možnost **vytvořit nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="30983-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="30983-121">Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .</span><span class="sxs-lookup"><span data-stu-id="30983-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="30983-122">Zvolte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="30983-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Prázdná šablona řešení v aplikaci Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="30983-124">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **ClassLibraryProjects** .</span><span class="sxs-lookup"><span data-stu-id="30983-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="30983-125">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="30983-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="30983-126">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="30983-126">Create a class library project</span></span>

1. <span data-ttu-id="30983-127">Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="30983-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="30983-128">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="30983-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="30983-129">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** .</span><span class="sxs-lookup"><span data-stu-id="30983-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="30983-130">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="30983-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="30983-131">Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="30983-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="30983-132">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="30983-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="30983-133">Pak zvolte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="30983-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="30983-134">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30983-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="30983-135">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="30983-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="30983-136">Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="30983-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="30983-138">Pokud používáte Visual Basic, vymažte text v textovém poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="30983-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="30983-140">Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="30983-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="30983-141">V tomto kurzu definujete obor názvů nejvyšší úrovně pomocí [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) klíčového slova v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="30983-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="30983-142">Nahraďte kód v okně Code pro *Class1.cs* nebo *Class1. vb* následujícím kódem a uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="30983-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="30983-143">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="30983-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="30983-144">Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="30983-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="30983-145">Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="30983-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="30983-146">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="30983-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="30983-147"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="30983-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="30983-148">Na panelu nabídek vyberte **sestavit**  >  **sestavení řešení** a ověřte, že se projekt zkompiluje bez chyby.</span><span class="sxs-lookup"><span data-stu-id="30983-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="30983-149">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="30983-149">Add a console app to the solution</span></span>

<span data-ttu-id="30983-150">Použijte knihovnu tříd v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznamuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="30983-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="30983-151">Do řešení přidejte novou konzolovou aplikaci .NET Core s názvem prezentující.</span><span class="sxs-lookup"><span data-stu-id="30983-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="30983-152">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="30983-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="30983-153">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Console** .</span><span class="sxs-lookup"><span data-stu-id="30983-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="30983-154">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="30983-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="30983-155">Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="30983-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="30983-156">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **prezentující** .</span><span class="sxs-lookup"><span data-stu-id="30983-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="30983-157">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="30983-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="30983-158">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="30983-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="30983-160">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="30983-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="30983-161">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="30983-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="30983-162">V **Průzkumník řešení**klikněte pravým tlačítkem myši na `ShowCase` uzel **závislosti** projektu a vyberte možnost **Přidat odkaz na projekt**.</span><span class="sxs-lookup"><span data-stu-id="30983-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Přidat kontextovou nabídku odkazu v aplikaci Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="30983-164">V dialogovém okně **Správce odkazů** vyberte projekt **StringLibrary** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="30983-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Dialog Správce odkazů s vybraným StringLibrary](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="30983-166">V okně kódu pro soubor *program.cs* nebo *program. vb* nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="30983-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="30983-167">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="30983-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="30983-168">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="30983-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="30983-169">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="30983-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="30983-170">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="30983-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="30983-171">Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="30983-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="30983-172">V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="30983-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="30983-173">Zkompilujte a spusťte program tak, že vyberete zelenou šipku na **tlačítku pro** sestavování.</span><span class="sxs-lookup"><span data-stu-id="30983-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="30983-175">Vyzkoušejte program zadáním řetězců a stisknutím klávesy **ENTER**a stisknutím klávesy **ENTER** ukončete.</span><span class="sxs-lookup"><span data-stu-id="30983-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konzoly s předvedením":::

## <a name="next-steps"></a><span data-ttu-id="30983-177">Další kroky</span><span class="sxs-lookup"><span data-stu-id="30983-177">Next steps</span></span>

<span data-ttu-id="30983-178">V tomto kurzu jste vytvořili řešení, přidali projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="30983-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="30983-179">V dalším kurzu přidáte do řešení projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="30983-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30983-180">Testování knihovny .NET Standard pomocí .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30983-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
